Intro to Makefiles
==================


What is Make?
-------------

From the man page:

  "The  make  utility will determine automatically which pieces of a large program need to be
   recompiled, and issue the commands to recompile them."

In plainer words, ``make`` is a utility to automate the building of programs, including handling
dependencies.

An example of this would be if you had 2 source code files ``a.inputfile`` and ``b.inputfile``,
and you need to compile ``b.inputfile`` before ``a.inputfile``. With a properly structured
makefile, Make will determine what dependencies need to be rebuilt during compilation. This is
extremely useful when working on large projects where you may only change one file, and Make can
then avoid recompiling large portions of the project and only recompile the edited version. 

The code for a makefile that does this might look something like this:

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

    output files: dependencies
        command to generate outputs from inputs

Dependencies are either files or other make rules.


A Warning
---------

The commands **must** be tab indented to work. Be careful when copying example code directly from
this page, as our documentation engine renders all tabs as spaces, which *will not work!* You will
have to change the spaces to tabs in the makefiles!


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


Uses for Makefiles
------------------

One very powerful use of makefiles is making it easy to switch between 'debug' and 'submittable'
versions of your code. You can combine c/c++ preprocessor define directives and makefile/g++
commands to toggle debug mode on your code. This way you don't have to constantly edit the file to
enable debugging to prevent debug stuff from leaking into your submitted code.

So, with the following c++ code in a file called ``potato.cpp``:

.. code-block:: cpp
  :linenos:

    #include <iostream>

    int main() {
      int x;

      std::cout << "plz give number: " << std::endl;
      std::cin >> x;

      #ifdef DEBUG
      std::cout << "Oh my goodness look at all the wonderful debug data here!" << std::endl;
      std::cout << "Best part is, this won't end up in your 'production' code!" << std::endl;
      #endif

      std::cout << x * 7 << std::endl;

      return 0;
    }

And with the following makefile:

.. code-block:: html
  :linenos:

  default: potato.cpp
        echo "This version will NOT have debug output..."
        g++ potato.cpp -o out.exe

  debug: potato.cpp
        echo "This version *will* have debug output..."
        g++ -DDEBUG potato.cpp -o debug.exe
