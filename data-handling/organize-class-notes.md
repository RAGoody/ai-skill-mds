---
name: organize-class-notes
description: generates a PDF of the given document, extracting content from captured images/slides and organizing them with your own notes.
---

## When to Use

- When you have a document that is a mixed collection of screen captures (as if from a Webinar) plus your own notes from the voice over
- Use this to combine the content w/in the captured images and slides with your own notes into an organized format.


## Input Variables

Prompt or inspect for:

- **`topic`**: Root directory name (e.g., `ai-skills-building`).

## Structured Prompt Template

```text
Using the uploaded file, review the text notes and images, generating a comprehensive, organized output of the topics covered. Make sure to include:
> table of contents
> each chapter is a specific topic, sequentially numbered
> extraction of embedded text in images included with the original source images
> show me in your output how you have organized the contents and the table of contents
> output into a .pdf file of [topic] name.

Variables:
[topic]=ai-skills-building