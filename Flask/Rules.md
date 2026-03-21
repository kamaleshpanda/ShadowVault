## Rule 1
### HTML (form.html)
```html
<form action="/submit" method="POST">  
<input type="text" name="username">  
<input type="password" name="password">  
<button type="submit">Login</button>  
</form>
```
### Flask (app.py)

``` python
@app.route('/submit', methods=['POST'])  
def submit():  
    username = request.form.get('username')  
    password = request.form.get('password')  
    return "Data received"
```
## Rules from this Example
1. **Action must match route**
    - `action="/submit"` → `@app.route('/submit')`
2. **Always use `/` in route**
    - `/submit`  (*correct way*)
3. **Method must match**
    - HTML: `POST` → Flask: `methods=['POST']`

