# VectorDB — C++ Vector Database

A C++ vector database with a web interface for vector similarity search, HNSW, KD-Tree, Brute Force search, document embeddings, and RAG using Ollama.

## Features

- HNSW, KD-Tree, and Brute Force search
- Cosine, Euclidean, and Manhattan distance metrics
- Demo vectors with PCA visualization
- Document embeddings using `nomic-embed-text`
- RAG pipeline using a local LLM
- REST API
- Web-based interface

## Technologies

- C++17
- HNSW
- KD-Tree
- Ollama
- HTML / CSS / JavaScript
- REST API

## How It Works

User Text
↓
Ollama Embedding Model
↓
Vector Embedding
↓
HNSW Index
↓
Similarity Search
↓
Relevant Document Chunks
↓
Local LLM
↓
Answer

## Requirements

- Windows
- C++17 compiler (MSYS2/MinGW)
- Git
- Ollama

## Installation

### 1. Install MSYS2

Download: https://www.msys2.org/

Open the MSYS2 UCRT64 terminal and run:

    pacman -Syu

If prompted to restart the terminal, do so and then run:

    pacman -S mingw-w64-ucrt-x86_64-gcc

Add this directory to your Windows PATH:

    C:\msys64\ucrt64\bin

Verify:

    g++ --version

### 2. Install Ollama

Download: https://ollama.com/

Pull the required models:

    ollama pull nomic-embed-text
    ollama pull llama3.2

Verify:

    ollama list

### 3. Clone the Repository

Replace the URL with your own GitHub repository:

    git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
    cd YOUR_REPOSITORY

### 4. Compile

    g++ -std=c++17 -O2 main.cpp -o db -lws2_32

### 5. Run

Start Ollama:

    ollama serve

In another terminal:

    .\db.exe

Open the application:

    http://localhost:8080

## Using the Application

### Vector Search

Choose:

- Algorithm: HNSW, KD-Tree, or Brute Force
- Metric: Cosine, Euclidean, or Manhattan

The application also provides a PCA-based visualization of the demo vectors.

### Documents

1. Enter a document title.
2. Paste the document text.
3. Click Embed & Insert.
4. The document is split into chunks.
5. Each chunk is converted into an embedding and stored for similarity search.

### Ask AI

After adding documents:

1. Enter a question.
2. Click Ask AI.
3. HNSW retrieves relevant document chunks.
4. The retrieved context is sent to the local LLM.
5. The LLM generates the answer.

## REST API

| Method | Endpoint | Description |
|---|---|---|
| GET | `/search` | Search vectors |
| POST | `/insert` | Insert a vector |
| DELETE | `/delete/:id` | Delete a vector |
| GET | `/items` | List vectors |
| GET | `/benchmark` | Compare search algorithms |
| GET | `/hnsw-info` | HNSW information |
| GET | `/stats` | Database statistics |
| POST | `/doc/insert` | Insert a document |
| GET | `/doc/list` | List documents |
| DELETE | `/doc/delete/:id` | Delete a document |
| POST | `/doc/ask` | RAG query |
| GET | `/status` | Ollama status |

## Project Structure

    VectorDB/
    ├── main.cpp
    ├── httplib.h
    ├── index.html
    ├── LICENSE
    └── README.md

## Algorithms

### HNSW

Hierarchical Navigable Small World is a graph-based approximate nearest-neighbor search algorithm that organizes vectors into multiple graph layers.

### KD-Tree

A KD-Tree partitions multidimensional space and reduces the number of points examined during a search.

### Brute Force

Brute Force compares the query vector with every stored vector and provides an exact search baseline.

## RAG Pipeline

Document
↓
Chunking
↓
Embedding
↓
Vector Storage
↓
Similarity Search
↓
Relevant Context
↓
Local LLM
↓
Generated Response

## Limitations

- Intended primarily for educational and experimental use
- Performance depends on hardware and dataset size
- KD-Tree becomes less efficient with high-dimensional vectors
- Local LLM inference can require significant system resources

## Acknowledgement

This repository is based on the open-source Your-OWN-AI project by Perry Vegehan.

Original repository:
https://github.com/perryvegehan/Your-OWN-AI

The original project is released under the MIT License.
