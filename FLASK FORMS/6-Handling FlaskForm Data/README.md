FLASK FORMS
Handling FlaskForm Data
Once a form is submitted, the data is sent back to the server through a POST request. Previously we covered accessing this data through the request object provided by Flask.

Using our FlaskForm class, data is now accessible through the form instance in the Flask app. The data can be directly accessed by using the data attribute associated with each field in the class.

form_data = flask_form.my_textfield.data
Keeping all the information and functionality attached to the form object has streamlined the form creation and data gathering process.

Remember that when a route handles a form it is necessary to add the POST method to the route decorator.

methods=["GET", "POST"]
Instructions
1.
The data from the web form can now be accessed through the comment_form instance within the recipe route. In that route in app.py assign the comment field data to a variable called new_comment.

Checkpoint 2 Passed

Hint
Assign comment_form.comment.data to new_comment using this syntax.

some_var = some_instance.some_field.data
2.
Now add the submitted comment to the specified recipe comment list by appending new_comment to comments[id].

When you’re done, give the form a try by adding some comments to the recipe page. Head on to the next exercise when ready.

Checkpoint 3 Passed

Hint
Using .append() add new_comment to the comments[id] list using this syntax.

some_list.append(some_var)