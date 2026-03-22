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
username = request.form.get('username')
password = request.form.get('password')
```
- Gets input from HTML form fields
```python
if username == 'admin' and password == '12345':
    return render_template('home.html', name=username)
else:
    return "Invalid login"
```
- Checks username & password
- If correct → open `home.html`
- If wrong → show error

*If you have more than 2 user name and password we can use Dictionary.*
For e.g. :-
```python
users = {
    "admin": "12345",
    "kamal": "pass123",
    "rahul": "rahul@123"
}
##modify the logic a little here
if username in users and users[username] == password:  
return render_template('home.html', name=username)
```
[[Rules#Rule 1|see the HTML and flask rules]]

-----------------------
## Jinja 2
- Jinja2 is used inside HTML to **add logic + dynamic data** (it allows HTML to use python data with variables, conditions and loops)
- It connects **Flask (Python)** with **HTML**

Means:
- Python sends data → HTML displays it using Jinja2

e.g. - Like if a school has 100 students so we cannot make 100 HTML page so therefore we will make one HTML page and from flask we will use a loop so that it will show their in that HTML page.

## ==Template Inheritance== :- 
- It allows you to create a **base template (layout)**
- Other pages **reuse it instead of rewriting HTML again**

