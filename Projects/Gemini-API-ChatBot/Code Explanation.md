**File Name: main.py**

  Step 1: Install python-dotenv
```bash  
pip install python-dotenv  
```
we created `.env` file to keep my API key safe because API key should not be seen by public users.
But How can python(main.py) access that `.env` file.
so we install the `python-dotenv` library in our system through terminal.

```python
from dotenv import load_dotenv  
import os 
```
This line imports the `load_dotenv` function from the dotenv library.

 The `.env` file stores the API key.  
 The `load_dotenv()` function loads the `.env` file into environment variables. The `os` module is used to access those environment variables in Python.

```python
load_dotenv()
api_key = os.getenv("GEMINI_API_KEY")

if api_key:
    print("API KEY ", api_key[0:4])  # always use , instead of because                                                    its conidered safer
else:
    print("API KEY not set")   
```
#commavsplus    Refer:[[Best Practices]]
we call the func `load_dotenv()`
Then Get Gemini API key from environment variables and store it in `api_key`
if `api_key` exists then print only 4 digits for security check otherwise not needed also. and if don't exist then print "API KEY not set".

<hr style="border:3px solid black">


```bash
pip install -q -U google-genai
```
This command installs the **google-genai** Python library, which is used to access Google's Gemini AI models in Python.
**-q**  
Means "quiet mode".  It reduces installation output and shows less messages.
**-U**  
Means "upgrade".  It upgrades the package to the latest version if already installed.

``` python
client = genai.Client()  
x = input("Ask Something :")  
response = client.models.generate_content(  
    model="gemini-3-flash-preview",  
    contents=x )  
print(response.text) 
```
**client = genai.Client()**
This line creates a client object to connect with Google Gemini AI.
It acts as a bridge between Python program and Gemini AI.
'x' takes input from user and 'response' line sends question to gemini ai and get the response.

<hr style="border:3px  solid green">

### Task 2 - Using LLamaIndex
###### Now our chatbot only works in texts , suppose we want to upload a document and ask question from that document.So we use LLamaIndex.

```bash
pip install --user llama-index pypdf sentence_transformers
```
--user not needed, that's optional.
`Llama-index` library connect LLMs with my data and build chatbots using my documents.(upload pdf & ask questions)
`pypdf` library used to read and extract text from PDF files.
`SentenceTransformer` convert text to embeddings(numerical vectors) , computer converts words/text to numbers.it makes it better for computer to understand.(Similar sentences = close embedding).
#### PDF Chatbot Architecture
```text
PDF file
  ↓
PyPDF → extracts text
  ↓
SentenceTransformer → converts text to embeddings
  ↓
LlamaIndex → stores and searches
  ↓
Gemini → generates final answer
```

**Important**
Llama Index was officially made for openAI by default but we are using Gemini API in this project so, we must change the default LLM settings in LlamaIndex.
```python
from llama_index.core import VectorStoreIndex,SimpleDirectoryReader, Settings
```
`VectorStoreIndex` → creates vector index from documents
`SimpleDirectoryReader` → loads PDF files from folder
`Settings` → used to configure LLM and embedding model

Here we are creating a folder and there we are storing a document.
```python
from dotenv import load_dotenv 
import os
```
```python
from llama_index.llms.google_genai import GoogleGenAI
```
This connects LlamaIndex to Gemini AI instead of OpenAI.

```python
from llama_index.embeddings.huggingface import HuggingFaceEmbedding  
from llama_index.core import Settings
```
This loads free embedding model from HuggingFace to do embeddings.
```python
load_dotenv()  
api_key = os.getenv("GEMINI_API_KEY")  
if api_key:  
    print("API KEY " , api_key[0:4]) 
else:  
    print("API KEY not set")
```
---
```python
Settings.llm = GoogleGenAI(model="gemini-3-flash-preview")
```
~ Very important as we are now changing settings.
```python
Settings.embed_model = HuggingFaceEmbedding(model_name="BAAI/bge-small-en")
```
Converts text into vector embeddings

---
```python
documents = SimpleDirectoryReader("pdf").load_data()
```
Loads all PDF files from "pdf" folder

```python
x = input("Ask something from the pdf :")  
index = VectorStoreIndex.from_documents(documents)  
```
>This converts PDF into vector database
```python
engine = index.as_query_engine()  
result = engine.query(x)  
print(result)
```
>Creates chatbot engine
>Search PDF
   Send relevant text to Gemini
	   Gemini generates answer and then it prints AI results.

As we run the code, the code takes too much time because it converts the file to text embedding and then it does search.
As we know we have to run the code many times, so better is ==if we run it once and our code saves the vector embedding/ indexes in a folder==.
We can save the index using:
```python
index.storage_context.persist("ml_index")
```
This creates a folder:
ml_index/
This folder contains:
- vector embeddings
- index data
- metadata