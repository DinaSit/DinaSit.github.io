---
title: Local code generation agent
date: 2026-04-15
links:
  - type: site
    url: https://github.com/DinaSit/cpp_local-code_agent
tags:
  - C++
  - LLM
  - llama.cpp
---

A code generation agent written in C++ that runs entirely locally, without
calling external APIs and without sending data anywhere.

<!--more-->

The agent is built on top of llama.cpp with the Qwen2.5-Coder model, with an
alternative path through Ollama.

Implemented:

- a pipeline for handling a request, generating code and validating the result;
- an iterative refinement loop;
- operation without network dependencies — all inference runs on the user's
  machine.

The project sits at the intersection of two areas: here a language model is not
a service reached over the network but a C++ library embedded into a program.
