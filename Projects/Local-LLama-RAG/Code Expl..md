```python
def embedchain_bot(db_path):
    return App.from_config(
        config={
            "llm": {
                "provider": "ollama",
                "config": {
                    "model": "llama3.2:latest",
                    "base_url": "http://localhost:11434",
                },
            },
            "vectordb": {
                "provider": "chroma",
                "config": {"dir": db_path},
            },
            "embedder": {
                "provider": "ollama",
                "config": {
                    "model": "llama3.2:latest",
                    "base_url": "http://localhost:11434",
                },
            },
        }
    )
```

This function creates the **brain of your application**.
It connects LLM(Llama), Vector Database, Embedding Model, Local Ollama Server.
- The function `embedchain_bot(db_path)` creates and returns the complete RAG system for the app.
- It configures which LLM to use — **Llama 3.2** running through Ollama.
- The `base_url` (`http://localhost:11434`) tells the app where Ollama is running locally.
- The `"llm"` section is responsible for generating final answers.
- The `"embedder"` section converts text (PDF content and user questions) into numerical embeddings.
- The `"vectordb"` section uses ChromaDB to store those embeddings.
- `db_path` specifies the folder where the vector database will store document data.
- This configuration connects the LLM, embedding model, and vector database into one working RAG pipeline.
- Without this setup, the app would not know how to retrieve PDF content or generate context-based answers.

`def embedchain_bot(db_path):
    `return App.from_config( `
    > Create a function named `embedchain_bot` that takes one input called `db_path`.
    > We define a function that creates one Embedchain App. Inside this App, we configure the LLM, the embedding model, and the vector database. This configuration tells Embedchain how to perform Retrieval-Augmented Generation.

