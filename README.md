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

## Running the notebook

1. Use Python and Jupyter Notebook or JupyterLab to open `restaurant_rag_assistant.ipynb`.
2. Install dependencies using the notebook's first code cell.
3. Set your OpenAI API key in a local `.env` file (see `.env.example`). **Never commit your `.env` file.**
4. Add a text source named `eleven_madison_park_data.txt` beside the notebook. This data file is **not included** in this repository package.
5. Execute the notebook cells in order and open the Gradio link displayed by the final cell.

Example questions:

- What menu options are described?
- Who is the head chef?
- What information is available about the restaurant's dining experience?

**Note:** This notebook uses LangChain imports from its original implementation. LangChain APIs have changed across releases, so you may need to adapt imports and chain calls for your installed versions. Running the OpenAI embedding and language models requires API access and may incur charges.

## Known limitations

- The application depends on an external, pre-prepared text file; it does not crawl restaurant websites automatically.
- Source attribution is limited by the metadata present in that file and the LangChain chain's output.
- There is no formal evaluation suite, production deployment configuration, or automated data-refresh pipeline in this version.
- The content represents a snapshot of the source material; details such as menus and prices may change.

## Data sources

The notebook works with text derived from the public website of [Eleven Madison Park](https://www.elevenmadisonpark.com/). Website content belongs to its respective owner. Review applicable permissions before redistributing any collected text.
