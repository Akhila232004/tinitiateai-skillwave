# RAG and Vector Search

Retrieval-augmented generation, often called RAG, is a pattern where an AI system retrieves relevant information before generating an answer. RAG helps models answer using trusted documents instead of relying only on model memory.

## Why RAG Matters

RAG is useful when answers must depend on private, changing, or domain-specific information.

Examples:

- Company policies.
- Product documentation.
- Legal or compliance manuals.
- Support tickets.
- Engineering runbooks.
- Course content and knowledge bases.

## RAG Workflow

A basic RAG system has two phases.

Indexing phase:

1. Collect documents.
2. Split documents into chunks.
3. Convert chunks into embeddings.
4. Store embeddings and metadata in a vector database.

Answering phase:

1. Receive the user question.
2. Convert the question into an embedding.
3. Retrieve the most relevant chunks.
4. Send the chunks and question to the model.
5. Generate an answer with citations or references.

## Chunking

Chunking divides large documents into smaller pieces. Good chunks are small enough to fit into context but large enough to preserve meaning. Headings, sections, paragraphs, and metadata can improve retrieval quality.

## Vector Search

Vector search finds items with similar embeddings. Instead of matching only exact keywords, it can find content with similar meaning. Many RAG systems combine vector search with keyword search, filters, and reranking.

## RAG Quality Tips

- Store source titles, URLs, section names, and timestamps as metadata.
- Retrieve more candidates than needed, then rerank.
- Tell the model to answer only from retrieved context.
- Ask the model to say when the context is insufficient.
- Evaluate with real user questions and expected answers.

## Learning Goal

Learners should be able to explain and design a RAG pipeline that grounds AI answers in trusted information.

