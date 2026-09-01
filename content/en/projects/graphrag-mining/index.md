---
title: Question answering system over a corpus of scientific documents
date: 2026-08-02
links:
  - type: site
    url: https://github.com/DinaSit/graphrag-mining
tags:
  - Python
  - FastAPI
  - Neo4j
  - pgvector
  - LLM
---

The system answers questions over a corpus of reports, papers and
presentations, and supports every answer with references to specific fragments
of the source files.

<!--more-->

Expert knowledge in a research department is scattered across hundreds of
documents, and finding a particular result comes down to searching by hand.
The system addresses traceable access to such a corpus.

How it works:

- a document is split into addressable fragments — a page, a slide, a table
  row; scanned pages are rendered as images for visual extraction;
- a language model extracts structured facts from the fragments, and every
  fact is required to reference its source;
- facts are validated against numbers and units of measurement; those failing
  validation are routed to an expert rather than discarded;
- approved facts are projected into a Neo4j knowledge graph;
- fragments are encoded with the bge-m3 model and stored in pgvector.

Retrieval is hybrid: direct facts, the vector index and graph traversal. The
query is routed to a fast or a full pipeline depending on whether it contains
numbers or comparison conditions.

The key property is that footnotes in an answer resolve mechanically to
fragment identifiers, so the model cannot invent a source.

Developed during the Nornickel AI Science Hack.
