# Restaurant RAG Chatbot

A document-grounded question-answering application that uses **Retrieval-Augmented Generation (RAG)** to answer questions about Eleven Madison Park restaurant information. Built with **LangChain**, **OpenAI**, **ChromaDB**, and **Gradio**.

## Overview

The application loads a text-based knowledge source, splits it into overlapping chunks, generates vector embeddings, and indexes them in ChromaDB. User questions are matched to relevant passages using semantic search. The retrieved context is then passed to an OpenAI language model to generate an answer, with source information displayed when available.

## Features

- Document loading and preprocessing using LangChain
- Recursive text chunking with configurable size and overlap
- OpenAI embeddings and vector storage in ChromaDB
- Semantic similarity search and top-k retrieval
- Retrieval-based question answering using LangChain
- A Gradio interface for submitting questions and viewing answers and sources

## Architecture

```text
Restaurant data (.txt)
        |
    TextLoader
        |
 RecursiveCharacterTextSplitter
        |
  OpenAIEmbeddings
        |
     ChromaDB
        |
 Similarity retriever (top-k)
        |
   OpenAI LLM / QA chain
        |
 Gradio question-answer interface
```
