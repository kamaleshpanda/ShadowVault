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
