FLASK TEMPLATES

Variable Filters

Now that we can use variables in our templates, let’s look at different ways we can perform actions on them.

Filters are used by the template engine to act on template variables. To use them simply follow the variable with the filter name inside the delimiter and separate them with the | character.

    {{ variable | filter_name }}

The character | separating the variable and the filter is called a pipe or vertical bar.

The filter title acts on a string variable and capitalizes the first letter in every word. This is good for using as formatting on heading strings. Given the variable assignment template_heading = "my very interesting website".

    {{ template_heading |  title }}
 
OUTPUT

My Very Interesting Website
Notice that the first letter of every word is now capitalized.

Filters can also take arguments. The default filter will output the text in its argument when a variable isn’t passed to the template. Consider if no_template_variable is missing from the render_template() arguments.

    {{ no_template_variable | default("I am not from a variable.") }}
 
OUTPUT

I am not from a variable.
The default filter does not work on empty strings "" or None values. We will look at this scenario in the next exercise.

While filters perform more complex functions than simple operators, they are still small, focused actions. Here is a list of commonly applied filters and their descriptions. More information can be found in the Jinja2 documentation

    title: Capitalizes the first letter of each word in a string, known as titlecase

    capitalize: Capitalizes the first character of a string, such as in a sentence

    lower/uppercase: Makes all the characters in a string lowercase/uppercase

    int/float: Changes any number variable to an integer/float

    default: Defines a default string if the variable is not defined

    length: Calculates the length of a string, list or dictionary variable
    
    dictsort: Sorts a dictionary by its keys