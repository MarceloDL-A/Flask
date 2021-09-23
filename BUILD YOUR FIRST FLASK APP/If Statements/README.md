FLASK TEMPLATES

If Statements

Including conditionals such as if and if/else statements in our templates allows us to control how data is handled.

Let’s say we have a string variable passed to our template. When the variable contains an empty string will you want to output it or will you want to output another string? Remember the default filter doesn’t work in this situation so an if statement is needed.

Using if statements in a template happens inside a statement delimiter block: {% %}.
````html
{% if condition %}
  <p>This text will output if condition is True</p> 
{% endif %}
````

Notice the {% endif %} delimiter is necessary to close the if statement.

The condition can include a variable that is tested using standard comparison operators, <, >, <=, >=, ==, !=.

````html
{% if template_variable == "Hello" %}
  <p>{{template_variable}}, World!</p> 
{% endif %}
````

While inside statement delimiters {% %} we can access variables without using the usual expression delimiter {{ }}.

Variables can also be tested on their own. A variable defined as None or False or equates to 0 or contains an empty sequence such as "" or [] will test as False.

The {% else %} and {% elif %} delimiters can be included to create multi-branch if statements.

Given the assignment template_number = 20.

````html
{% if template_number < 20 %}
  <p>{{ template_number }} is less than 20.</p> 
{% elif template_number > 20 %}
   <p>{{ template_number }} is greater than 20.</p> 
{% else %}
   <p>{{ template_number }} is equal to 20.</p> 
{% endif %}
````
 
OUTPUT
20 is equal to 20.
As expected the {% else %} branch is the one that is followed.