## BUILD YOUR FIRST FLASK APP

### Variable Rules

We’ve seen how the route() decorator can be used to bind one or more static URLs to a view function. But what if we want to handle a set of URLs that may be constantly changing? Let’s take a look at how we can use variable rules to allow for dynamic URLs.

When specifying the URL to bind to a view function, we have the option of making any section of the path between the slashes (/) variable by indicating \<variable_name>. These variable parts will then be passed to the view function as arguments. For example:

```python
@app.route('/orders/<user_name>/<int:order_id>')
def orders(user_name, order_id):
    return f'<p>Fetching order #{order_id} for {user_name}.</p>'
Now, URLs like '/orders/john/1' and '/orders/jane/8' can all be handled by the orders() function.
```

Note that we can also optionally enforce the type of the variable being accepted using the syntax: \<converter:variable_name>. The possible converter types are:


    string	accepts any text without a slash (default)
    int	    accepts positive integers
    float	accepts positive floating point values
    path	like string but also accepts slashes
    uuid	accepts UUID strings


## Review

Import the Flask class and create an application object

```python
from flask import Flask
app = Flask(__name__)
```

Define routes for handling requests sent from various URLs

```python
@app.route('/')
def home():
  return '<h1>Hello, World!</h1>'
```
Create variable rules to handle dynamic URLs

```python
@app.route('/orders/<user_name>/<int:order_id>')
def orders(user_name, order_id):
  return f'<p>Fetching order #{order_id} for {user_name}.</p>'
```