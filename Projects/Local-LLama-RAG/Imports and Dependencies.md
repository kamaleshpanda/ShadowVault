### Checks
```bash
ollama --version
```
~ To check the version of Ollama and see whether its perfectly installed or not.

```bash
ollama pull llama3.2
```
~ This will download LLama 3.2 model.

```bash
ollama run llama3.2
```
~ If LLama responds, everything is correct.

### Install Python Dependencies
```bash
pip install streamlit embedchain chromadb streamlit-chat
```
~ `Streamlit` is used to create webapp, create button and UI etc.
~` Embedchain` does the RAG work, Instead of writing logic of chunking, embedding , retrieval; It handles all automatically.It also connects LLama and ChromaDB.
~ `ChromaDB` stores embeddings.Without a Vector DB, RAG is not possible.
~`Streamlit-chat` gives us bubble style UI, whatsapp like look : Otherwise messages will look plain.

### Imports
```python
import os
import tempfile
import streamlit as st
from embedchain import App
import base64
from streamlit_chat import message
```

`import os` is used for file handling and temp. file deletion.
`import tempfile` used for creating temp folder and temp pdf file.
```
We need this because when the user uploads a PDF, we store it temporarily.
```
`from embedchain import App` - this imports RAG Engine. `App` is the main class that connects LLM and vector DB.
`import base64` - it converts pdf into displayable format and show pdf inside webapp
`from streamlit_chat import message` - display chat messages in bubble format


