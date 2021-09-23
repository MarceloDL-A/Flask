FLASK FORMS

FlaskForm Class

Flask provides an alternative to web forms by creating a form class in the application, implementing the fields in the template and handling the data back in the application.

A Flask form class inherits from the class FlaskForm and includes attributes for every field:


````html
class MyForm(FlaskForm):
    my_textfield = StringField("TextLabel")
    my_submit = SubmitField("SubmitName")
````

This simple class will enable the creation of a form with a text field and a submit button.

The class inherits from the class FlaskForm which allows it to implement the form as template variables and then collect the data once submitted. FlaskForm is a part of FlaskWTF.

Access to the fields of this form class is done through the attributes, my_textfield and my_submit. The StringField and SubmitField classes are the same as <input type=text... and <input type=submit... respectively and are part of the WTForms library.

Below is a simple Flask app with the form class.


```html
from flask import Flask, render_template
from flask_wtf import FlaskForm
from wtforms import StringField, SubmitField
 
app = Flask(__name__)
app.config["SECRET_KEY"] = "my_secret"
 
class MyForm(FlaskForm):
    my_textfield = StringField("TextLabel")
    my_submit = SubmitField("SubmitName")
 
@app.route("/")
def my_route():
    flask_form = MyForm()
    return render_template("my_template", template_form=flask_form)
```

First note the new import statements. FlaskForm is imported from the flask_wtf module and both form fields import from wtforms.

The next new line is:

```html
app.config["SECRET_KEY"] = "my_secret"
```

This line is a way to protect against CSRF or Cross-Site Request Forgery. Without going into too much detail, CSRF is an attack that used to gain control of a web application.

Next is the MyForm class definition. It inherits from FlaskForm and has attributes for the text and submit fields. For each field the label is passed as the only argument.

Lastly, in order to use this form in our template, we must create an instance of it and pass it to the template using render_template(). We will look at applying the form in the template in the next exercise.