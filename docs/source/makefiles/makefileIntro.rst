Intro to Makefiles
==================

What is Make?
-------------

``make`` is a tool that is used to manage dependencies when compiling a program. 

An example of this would be if you had 2 source code files ``a.inputfile`` and ``b.inputfile``,
and you need to compile ``b.inputfile`` before ``a.inputfile``. The code for a makefile that
does this might look something like this:

.. code-block:: html
    :linenos:

    a.output: a.inputfile b.output
        commands to generate a.output from a.inputfile and b.output
    
    b.output: b.inputfile
        commands to generate b.output from b.inputfile


If you wanted to build ``a.output`` all you would need to do is run the command ``make a.output``.

Makefile Structure
------------------

Makefiles consist of definitions and rules. 

A definition would look something like this:

``VAR=value``

When referencing a definition like ``VAR``, surround it with ``$(VAR)``.

A rule would look something like this:

.. code-block:: html
    :linenos:

    output files: input files
        command to generate outputs from inputs

Makefile Variables
------------------
As shown above vairables look like ``VAR=value``. To use those Variables, you need to use a dollar sign and wrap the name in parenthesis like so:
``$(VAR)``

You could also manipulate variable. For example, you could add or remove flags based on your action like this:

``CFLAGS += $(DEBUG)``

or call functions on variables, likethis: 

``$(patsubst %.cpp, $(OBJDIR)/%.o, $(SOURCES))``

Makefile Functions
------------------

You can declare functions in make files and use them just like anyother programming language. There are also quite a few built in functions (like ``patsubst`` in the example above).

To build a function you start with define, the function name and an '=' sign and close the function with endef. This is an example of a function definition:

.. code-block:: html
    :linenos:
    
    define run-yacc =
    yacc $(firstword $^)
    mv y.tab.c $@
    endef
    
To call a function you call it like you would a variable that is like this: 

``$(run-yacc . . . )``

Makefile Rules
--------------

As stated above, make files have rules in order to tell ``make`` how to build your project. Rules take on serveral forms. You can have empty rules, rules that use other rules, rules that run commands, etc. . . 

The most basic rule looks like this:
``Rule name: Rule dependency``

In our MSU CSE curicullum, most of the time, the rule name will be a target or output, and the rule dependency will be the input files. But they in no way need to be like that. Lets take the simple Makefile below. looking at line 

Simple Example Makefile for C
-----------------------------

.. code-block:: html
    :linenos:

    CC=gcc

    bar: bar.c foo.h foo.o
        $(CC) -o bar bar.c foo.o

    foo.o: foo.c foo.h
        $(CC) -c foo.c

To run this make file, one would simply run the command ``make bar``.
