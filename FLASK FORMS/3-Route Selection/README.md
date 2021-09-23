FLASK FORMS
Route Selection
As sites get larger and their file structure becomes more complex the paths of Flask routes may change. In this case paths that are hard coded into the navigation elements such as hyperlinks and forms may break.

Flask addresses the challenge of expanding file structures with url_for(). The function url_for() takes a route’s function name as an argument and returns the associated URL path. Given the following Flask route declaration:

@app.route('/')
def index:
These two hyperlinks below are identical.

<a href="/">Index Link</a>
 
<a href="{{ url_for('index') }}">Index Link</a>
Breaking down the second line of above code, we can see a few things:

url_for() is inside an expression delimiter
the argument for url_for() is inside single quotes
the entire statement is inside double quotes
Because of the last 2 points it is important to use one type of quotes for the whole statement and the other type of quotes for the url_for() argument.

To pass variables from the template to the app, keyword arguments can be added to url_for(). They will be sent as arguments attached to the URL. It can be accessed the same way as if it was added onto the path manually.

<a href="{{ url_for('my_page', id=1) }}">One</a>
This line creates a link that sends the value 1 to the route with the function name my_page. The route can access the variable through my_id.

@app.route("/my_path/<int:my_id>"), methods=["GET", "POST"])
def my_page(my_id):
    # Access flask_name in this function
    new_variable = my_id
    ...