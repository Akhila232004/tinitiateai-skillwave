# AWS S3
## S3 Core Storage
### Key Points
* Object storage — not a file system; access is by key via HTTP/HTTPS API, not file path
* Bucket names must be globally unique across all AWS accounts
* Multi-AZ durability is 11 nines (99.999999999%) — built-in, no configuration needed
* Max object size is 5 TB; single PUT is limited to 5 GB — use multipart for anything larger
* Request rate limits are per prefix: spread data across prefixes to increase aggregate throughput
* S3 has strong read-after-write consistency for all operations since December 2020


---

## S3 Storage Classes
### Key Points
* Standard is default — multi-AZ, low latency, no retrieval fees; best for frequently accessed data
* Intelligent-Tiering auto-moves objects between access tiers; no retrieval fees but has small per-object monitoring fee
* Standard-IA and One Zone-IA both charge retrieval fees; 30-day minimum storage duration applies
* One Zone-IA stores in a single AZ — only for data that can be recreated; never for backups
* Glacier Instant gives millisecond retrieval; Flexible is minutes to hours; Deep Archive is 12–48 hours
* Minimum storage durations: IA=30d, Glacier Instant/Flexible=90d, Deep Archive=180d — early deletion still charged
* Lifecycle policies automate transitions between storage classes based on age rules



---

## S3 Versioning
### Key Points
* Versioning must be explicitly enabled; once enabled it can only be suspended, never fully disabled
* Every PUT creates a new version with a unique version ID; GET without version ID returns the current version
* DELETE without version ID adds a delete marker — the object appears deleted but all versions still exist in S3
* DELETE with a specific version ID permanently removes that version — this is the only true permanent delete
* MFA Delete requires MFA authentication to permanently delete versions or change versioning state — extra compliance protection
* Versioning is a prerequisite for Cross-Region Replication and Object Lock
* All versions count toward storage billing; use lifecycle noncurrent-version expiration rules to control cost


---

## S3 Lifecycle Policies
### Key Points
* Lifecycle rules have two action types: transition (move to cheaper class) and expiration (delete objects)
* Minimum storage durations still apply during transitions: IA=30d, Glacier=90d, Deep Archive=180d
* Scope rules to entire bucket or filter by prefix, object tag, or object size range
* Always add a rule to abort incomplete multipart uploads — they accumulate silently and are billed
* Expire noncurrent versions with a noncurrent-version expiration rule to control versioning storage cost
* Delete expired delete markers automatically to keep bucket metadata clean


---

## S3 Security and Encryption
### Key Points
* SSE-S3: AWS manages the key; no extra cost; simplest to enable; good default for most workloads
* SSE-KMS: customer controls the key via KMS; adds per-request audit trail in CloudTrail; KMS API costs apply at scale
* SSE-C: customer provides the key on every request; AWS never stores the key; highest customer control
* Use a bucket policy `Deny` on `aws:SecureTransport: false` to enforce HTTPS on all requests
* Block Public Access should be on at account level; only disable per bucket when explicitly hosting public content
* Access Points give each team or application its own named endpoint with its own access policy scoped to a prefix


---

## S3 Replication
### Key Points
* CRR replicates to a different region for DR or compliance; SRR replicates within the same region for aggregation or dev/test
* Versioning must be enabled on both source and destination buckets before replication can start
* Replication is asynchronous and only applies to new objects written after replication is configured
* Pre-existing objects require a separate S3 Batch Replication job — replication rules do not backfill automatically
* Delete markers are not replicated by default — configure explicitly if downstream bucket must mirror deletes
* Permanent deletes (DELETE with version ID) are never replicated — important for compliance separation
* Replication Time Control (RTC) provides a 15-minute SLA with CloudWatch metrics for SLA evidence

---

## S3 as Data Lake
* Pattern: Raw zone (S3) → Curated zone (Parquet/Iceberg) → Consumption zone (Athena, Redshift)
* Always use columnar formats (Parquet/ORC) in curated layers — critical for Athena scan cost and query speed
* Partition by date or common filter columns so query engines prune scan scope and skip irrelevant files
* Small file problem: millions of tiny files increase metadata overhead and slow query planning — compact regularly
* Use Iceberg or Hudi on curated tables when ACID, upserts, deletes, or time travel are required
* Lake Formation adds fine-grained column-level and row-level access governance on top of S3 and Glue Catalog

**S3 Tables (Iceberg)**
* Lakehouse-style tabular datasets in Apache Iceberg format — fully managed
* Managed compaction and snapshot maintenance — no manual file management needed
* Glue Catalog integration — Athena, Redshift, and Spark can discover and query tables
* Use S3 Tables for curated analytical Iceberg tables; plain S3 prefixes for raw landing zones

---

## S3 and EventBridge
* Enable EventBridge on a bucket to send all S3 events to the default event bus
* EventBridge offers richer filtering (prefix, suffix, object metadata conditions) compared to native S3 notifications
* One S3 event can route to multiple EventBridge rules targeting different services simultaneously
* Archive and replay: EventBridge archives S3 events so you can replay them for debugging or reprocessing
* Use EventBridge over native S3 notifications when you need multiple targets, cross-account routing, or event archiving
* Common pattern: new file in S3 → EventBridge rule → Lambda triggers Glue job or Step Functions execution

## S3 Event Notifications
* Event Notifications - Native Destinations
* The three native S3 notification destinations — SQS, SNS, Lambda — plus the EventBridge option
* Native S3 notifications support SQS, SNS, and Lambda; enable EventBridge for richer routing
* Filtering is limited to object key prefix and suffix — no metadata, tag, or size-based filtering
* Each event configuration rule can point to only one destination — use EventBridge for fan-out
* At-least-once delivery means Lambda handlers and consumers must be idempotent to handle duplicate events
* Common pattern: S3 → SQS → Lambda polling — decouples traffic spikes and adds retry with DLQ support
* For richer filtering, multiple targets, or event replay, enable EventBridge at the bucket level
---

## S3 Performance and Optimization
* S3 scales automatically but per-prefix limits apply: 5500 GET / 3500 PUT per prefix per second
* Spread key prefixes to avoid hot spots — avoid all objects under a single date-stamped prefix at scale
* Use multipart upload for objects larger than 100 MB — improves reliability and allows parallel part uploads
* S3 Transfer Acceleration routes uploads through CloudFront edge nodes — useful for users far from the bucket region
* S3 Select lets query engines filter data inside S3 before returning it, reducing transferred bytes and compute cost
* For analytics workloads, use Parquet/ORC with snappy compression and file sizes of 128 MB–1 GB



---

## S3 Limitations
* S3 is object storage — no partial in-place updates; PUT replaces the entire object every time
* No atomic multi-object transactions — you cannot update multiple objects as a single atomic operation
* Renaming a prefix requires copying all objects then deleting originals — very expensive at scale with millions of objects
* S3 now has strong read-after-write consistency for all operations — the historic eventual consistency concern no longer applies
* Billing traps: all versions count, incomplete multipart uploads accumulate silently, Glacier retrieval fees apply
* Egress costs: data transferred out to internet or cross-region is charged; within the same region is generally free
* Bucket names and regions cannot be changed after creation



---

## S3 Real-time and Batch Processing
* Real-time: S3 event or EventBridge triggers Lambda or Step Functions for per-file processing within seconds of upload
* Near real-time: Kinesis Firehose buffers streaming records and writes batched files to S3 in configurable intervals
* Batch: Glue, EMR, Athena, and Airflow orchestrate scheduled jobs reading large S3 datasets on a schedule
* S3 Batch Operations runs a Lambda function across every object in a bucket or manifest — good for bulk tagging, copying, or transformations
* Hudi Merge-on-Read enables near-real-time table updates in S3 without full partition rewrites
* Compaction is always needed after streaming writes to merge many small files into efficient analytical file sizes



---

## S3 Advanced Use Cases
* S3 Object Lambda intercepts GET requests and runs a Lambda to transform the object before returning to caller — useful for PII redaction, format conversion, image resizing without storing multiple copies
* S3 Select pushes down filtering into S3 so only matching rows are returned — reduces compute and transfer cost for Athena and Glue pipelines
* S3 Inventory generates scheduled reports of all objects with metadata — use as input to Batch Operations or for usage auditing
* S3 Tables: fully managed Iceberg lakehouse tables with automated compaction and built-in Glue Catalog integration
* Object Lock compliance mode prevents deletion even by root account for the full retention period — required for SEC/FINRA compliance
* Presigned URLs grant temporary scoped access (GET or PUT) to a specific object without exposing credentials



