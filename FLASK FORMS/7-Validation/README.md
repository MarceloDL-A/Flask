FLASK FORMS
Validation
In order to submit a form, it is common that certain required text fields must have data, date fields need to have a specific format, or a checkbox agreeing to certain terms needs to be checked.

Validation is when form fields must contain data or a certain format of data in order to move forward with submission. We enable validation in our form class using the validators parameter in the form field definitions.

Validators come from the wtform.validators module. Importing the DataRequired() validator is accomplished like this:

from wtforms.validators import DataRequired
The DataRequired() validator simply requires a field to have something in it before the form is submitted. Notifying the user that data is required is handled automatically.

my_textfield = StringField("TextLabel", validators=[DataRequired()])
The validators argument takes a list of validator instances.

The FlaskForm class also provides a method called validate_on_submit(), which we can used in our route to check for a valid form submission.

if my_form.validate_on_submit():
    # get form data
As we saw in second exercise pertaining to the request object, in order to avoid gathering data on first access to the route we had to put the data gathering code inside an if statement. The validate_on_submit() function does this exact task.

The validate_on_submit() function returns True when there is a POST request and all the associated form validators are satisfied. At this point the data can be gathered and processed. When the function returns False the route function can move onto other tasks such as rendering the template.

Instructions
1.
In app.py, the data handling section in the recipe route has been put inside an if True: block to mimic no validation. Run the code and hit refresh on the recipe page and notice what happens to the comments list.

Checkpoint 2 Passed
2.
Every time the page refreshes the string “None” is appended to the comments. This is because the data from the form is gathered every time the page renders. Even when the form is not submitted.

In app.py add a validate_on_submit() check. Be sure to include the data assignment logic but exclude the form instantiation.

Checkpoint 3 Passed

Hint
Create an if statement where the condition is the validate_on_submit method of comment_form. Use the following syntax.

if form_instance.validate_on_submit():
3.
To ensure that we get a comment every time the button is hit you need to put a validator on the string field. Note the wtforms.validators import statement.

Inside the CommentForm class add a validators list with the validator that requires data.

Run the code, refresh the page and try to submit an empty field. Note that the changes have taken effect

Checkpoint 4 Passed

Hint
Add validators=[DataRequired()] to the StringField call.