pynix
=====

Welcome to pynix! This is a small project aimed at learning python
programming. It focuses on the implementation of a command line program
that implements some familiar Linux commands. The goal is to learn a
about the python ecosystem -- some important libraries, idioms and
patterns that frequently appear in the context of python programming
projects.

# Initial setup 

1. Clone this git repository
2. Create a branch to work in 
   `git switch -c <branchname>`
3. Create a new virtual environment for your project.
4. Install the requirements 
   `(venv) cd pynix && python -m pip install -r requirements.txt`
5. Install pynix in development mode 
   `(venv) python -m pip install -e .`

Once you've got this done, you should be able to run pynix:

```bash
(venv) pynix 
Hello from pynix!
```

The program currently has one specifically defined entrypoint `pynix`
that functions more or less like an alias to call the main routine of the
program, which is found in the `src/cli.py` module.


# Tasks 

The initial tasks focus on implementing a command line program from
which it is possible to run simplified versions of the well-known Unix
programs `cat` and `less`. Read up on the `argparse` library and figure
out the steps needed in order to implement the functionality described
below.

## Readings
+ [PEP 8](https://peps.python.org/pep-0008/) Style Guide for Python Code
+ Chapters 3 & 4, Programming Python by Mark Lutz
+ Manual pages for `cat` and `less`
+ Python docs for: argparse, os, sys, pathlib
+ Chapters 1, 2, 5, 6, Serious Python by Julien Danjou


## Implement cat 

The Linux man page for cat states that it is a program to "concatenate
files and print on the standard output". In order to replicate this
functionality your program will need to be able to read a variable
number of arguments from stdin. It should check that each of these
arguments can be converted to a valid pathlike object and then it should
open and read the file, writing its contents to stdout.

The usage for the cat command would be as follows: 
```bash
pynix --cat <file1> [<file2> <file3> ... <fileN>]
```

## Implement tail

Tail is another small utility program which comes from Unix. When called, it
outputs the last part of files passed as arguments. In this implementation, we
want to target the ability to specify how long the tail should be (how many
lines) and the file which should be read and printed to stdout.

```bash
pynix --tail <length (int)> <file>
```

## Implement some helpful error messages

If the program receives the wrong number of arguments as input, it
should be able to fail gracefully with a helpful error message for the
user. This tends to be handled by printing a usage statement to stdout
for the user.

```bash
pynix --cat 
usage: pynix --cat <file1> [<file2> <file3>]
```

## Change the name of the command line program 

Personalize the program so that it's possible to call it with another
name. For example, you could abbreviate the name to `pyx` in order to
lessen the amount of typing that you have to do at the command prompt in
order to run the program. The purpose of this exercise is to think a little bit
about how the python project is structured. Historically, the python ecosystem
for 

## Implement some tests to show that your program behaves as expected

Basically we want to use this opportunity to introduce `pytest` a very useful
testing library. You can focus on implementing two types of tests specifically:
unit tests and integration tests. You might have to do a little bit of research
to figure out what the different types do.

You can invoke pytest by running:
```bash
pytest tests/tests.py
```
