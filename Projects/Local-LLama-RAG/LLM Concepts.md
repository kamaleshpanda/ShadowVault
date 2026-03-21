#### What is an LLM?
A **Large Language Model (LLM)** is a neural network trained on massive text data to:
- Generate text
- Answer questions
- Summarize documents
- Translate languages
- Write code

#### What is Llama?
LLama (Large Language Model Meta AI ) was developed by Meta AI.

##### Why Llama?
- Open-source weights
- Smaller sizes available
- Can run locally
- No API required

#### What is Ollama?
Its a local machine runtime which is used to run LLama.
It directly download llama models for us and run it for us.

Instead of manually configuring PyTorch + Transformers, we use:
```bash
ollama pull llama3.2
ollama run llama3.2
```
Ollama handles optimization and serving.

#### What is RAG
RAG = **Retrieval Augmented Generation**
Instead of letting the LLM guess, we:
1. Retrieve relevant data
2. Inject that data into prompt
3. Generate answer based on retrieved context

### What are Embeddings ?
Embeddings are numerical representations of text.
`Machine Learning" → [0.021, -0.88, 0.45, ...]
They allow us to:
- Compare semantic similarity
- Search documents
- Perform vector retrieval

### What is a Vector Database?
Vector Database is used to store embeddings.
We use **ChromaDB**.
It: 
- Stores embeddings
- Performs similarity search
- Returns most relevant chunks

### Flow of our app

PDF → Chunk → Embed → ChromaDB  

User Question → Embedding → Similarity Search → Retrieve → Llama 3.2 → Answer

### Why we use RAG ?
Without RAG:
- LLM may hallucinate
- LLM doesn’t know your PDF content
- Limited knowledge window

With RAG:
- Grounded answers
- Document-aware responses
- More accurate output

