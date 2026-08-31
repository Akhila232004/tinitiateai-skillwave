# Courses

This folder is the course index for the Tinitiate education app.

## Goal

Provide one clean place where the app can discover:

- available subjects
- subject order
- subject metadata
- subject topic structure

## How This Folder Works

- `catalog.yaml` is the machine-readable manifest
- each subject folder contains a `README.md`
- each subject `README.md` defines the topic order for that subject

## Current Source Strategy

Most existing course material already exists in dedicated repositories.

Instead of rewriting all course material immediately, this folder imports the subject-level README structure into one central content repository. New subjects can also be authored directly in this repository with local markdown files. That gives the website a single catalog while continuing to reuse the current markdown source files where needed.

## Subject Folders

- `vue-js`
- `sql-server`
- `java`
- `next-js`
- `ai`

## How To Add A New Course

1. Create a new subject folder
2. Add `README.md` for that subject
3. Add the subject entry in `catalog.yaml`
4. Ensure all markdown links are valid and ordered correctly
