```python
from flask import Flask, render_template, request
```
- `Flask` → creates app
- `render_template` → loads HTML files
- `request` → gets data from user (form input)

```python
app = Flask(__name__)
```
- Initializes the Flask application

```python
@app.route('/')
def login():
    return render_template('form.html')
```
- `/` → homepage
- Shows `form.html`
- HTML file must be inside *templates folder*

```python
@app.route('/submit', methods=['POST'])
def submit():
```
- `/submit` → handles form data
- `POST` → used when sending data (secure)
```python

```