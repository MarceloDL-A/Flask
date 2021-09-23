FLASK FORMS

Template Form Variables

Creating a form in the template is done by accessing attributes of the form passed to the template.

Let’s use the following form as we work toward implementing it in a template:

```python
class MyForm(FlaskForm):
    my_textfield = StringField("TextLabel")
    my_submit = SubmitField("SubmitName")
```

In our application route we must instantiate the form and assign that instance to a template variable.


```python
my_form = MyForm()
 
return render_template(template_form=my_form)
```

Moving to the template, creating a form we simply use the form class attributes as expressions.

```html
<form action="/" method="post">
    {{ template_form.hidden_tag() }}
    {{ template_form.my_textfield.label }}
    {{ template_form.my_textfield() }}
    {{ template_form.my_submit() }}
</form>
```

Inside the standard <form> are all the FlaskForm objects accessed through template_form.

The first line {{ template_form.hidden_tag() }} is the other end of the CSRF protection. While not visible in the form, this field handles the necessary tasks to protect from CSRF.

The next two lines are for the text box. The first accesses the label of the field, which we specified as an argument when we created the field. The second my_textfield line is the input field itself.

The last line of the form is the submit button. Just like the HTML version, this will initiate sending the form data back to the server.

The HTML created from this form implementation is as follows:

```html
<form action="/" method="post">
    <input id="csrf_token" name="csrf_token" type="hidden" value="ImI1YzIxZjUwZWMxNDg0ZDFiODAyZTY5M2U5MGU3MTg2OThkMTJkZjQi.XupI5Q.9HOwqyn3g2pveEHtJMijTu955NU">
    <label for="my_textfield">TextLabel</label>
    <input id="my_textfield" name="my_textfield" type="text" value="">
    <input id="my_submit" name="my_submit" type="submit" value="SubmitName">
</form>
```