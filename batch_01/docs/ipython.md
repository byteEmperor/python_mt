# IPython and Jupyter Basics
The IPython shell can be launched with the command:
$ ipython

You can execute arbitrary Python statements by typing them in the shell.

## Object Introspection
Using a question mark (?) before or after a variable will display some general information about the object:
$ b = [1, 2, 3]
$ b?

This is referred to as object introspection. If the object is a function or instance method, the docstring, if defined,
will also be shown.

Using (??) will also show the function's source code if possible.

(?) has a final usage, which is for searching the IPython namespace in a manner similar to the standard Unix command 
line. A number of characters combined with the wildcard (*) will show all names matching the wildcard expression.
$ np.*load*?

## The %run Command
You can run any file as a Python program inside the environment of your IPython session using the %run command. 
For example:
$ %run ipython_script_test.py

The script is run in an empty namespace (with no imports or other variables defined) so that the behaviour should be 
identical to running the program on the command line. All of the variables (imports, functions, and globals) defined in 
the file will then be accessible in the IPython shell.

Should you wish to give a script access to variables already defined in the interactive IPython namespace, use the 
argument (-i) with the <$% run> command.

The related <$ %load> magic function imports a script into a cell code.

## Magic Commands
A magic command is any command prefixed by the percent symbol (%). For example, you can check the execution time of any
Python statement, such as a matrix multiplication, using the <%timeit> magic function.

Magic commands can be viewed as command-line programs to be run within the IPython system. Many of them have additional
"command-line" options, which can be viewed using <?>:
$ %debug?

Magic functions can be used by default without the percent sign, as long as no variable is defined with the same name
as the magic function in question. This feature is called automagic and can be enabled or disabled with <%automagic>.

Some magic functions behave like Python functions and their output can be assigned to a variable:
$ %pwd
$> '/home/...'
$ foo = %pwd

## Matplotlib Integration
One reason for IPython's popularity in analytical computing is that it integrates well with data visualisation and 
other user interface librearies like matplotlib. The <%matplotlib> magic function configures its integration with the
IPython shell or Jupyter notebook. This is important, as otherwise plots you create will either not appear (notebook)
or take control of the session until closed (shell).

In the IPython shell, running <%matplotlib> sets up the integration so you can create multiple plot windows without
interfering with the console session. In Jupyter, the command is a little different:
$ %matplotlib inline