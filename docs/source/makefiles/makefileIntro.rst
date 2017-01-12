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

The commands **must** be tab indented to work.


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
