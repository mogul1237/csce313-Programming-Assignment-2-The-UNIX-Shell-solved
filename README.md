# csce313-Programming-Assignment-2-The-UNIX-Shell-solved

Download Here: [csce313 Programming Assignment 2: The UNIX Shell solved](https://jarviscodinghub.com/assignment/programming-assignment-2-the-unix-shell-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

Introduction
Most useful interaction with a UNIX system occurs through the shell. Using a series of
easy to remember and simple commands, one can navigate the UNIX file system and issue
commands to perform a wide variety of tasks. Even though it may appear simple, the shell
encapsulates many significant components of the operating system.
Basic Shell Features
Environment
The shell maintains many variables which allow the user to maintain settings and easily
navigate the filesystem. Two of these that are particularly important are the current working
directory and the PATH. As its name implies, the current working directory variable keeps
track of the user’s current directory. The PATH variable consists of string of colon separated
pathnames. Whenever you type a name of a command, the kernel searches in the directories
specified by the PATH variable starting with the leftmost directory first. If the executable is
not found in any of the specified directories, then the shell returns with an error. One may
modify the PATH at any time to add and remove directories to search for executables.
Figure #1: Current Directory & PATH
Pipelining
UNIX provides a variety of useful programs for you to use (grep, ls, echo, to name a few).
Like instructions in C++, these programs tend to be quite effective at doing one specific
thing (Such as grep searching text, ls printing directories, and echo printing text to the
console). However, programmers/OS users would like to accomplish large tasks consisting of
many individual operations. Doing such requires using results from previous steps in order
to complete a larger problem. The UNIX shell supports this through the pipe operation
(represented by the character |). A pipe inbetween two commands causes the standard output
of one to be redirected into the standard input of another. An example of this is provided
below, using the pipe operation to search for all processes with the name ”bash”.
Figure #2: Piping Between Commands
1
CSCE 313 Fall 2018
Input/Output Redirection
Many times, the output of a program is not intended for immediate human consumption
(if at all). Even if someone isn’t intending to look at the output of your program, it is still
immensely helpful to have it print out status/logging messages during execution. If something
goes wrong, those messages can be reviewed to help pinpoint bugs. Since it is impractical to
have all messages from all system programs print out to a screen to be reviewed at a later
date, sending that data to a file as it is printed is desired.
Other times, a program might require an extensive list of input commands. It would be
an unnecessary waste of programmer time to have to sit and type them out individually.
Instead, pre-written text in a file can be redirected to serve as the input of the program as if
it were entered in the terminal window.
In short, the shell implements input redirection by redirecting the standard input of
a program to an file opened for reading. Similarly, output redirection is implemented by
changing the standard output (and sometimes also standard error) to point to a file opened
for writing.
Figure #3: Input/Output Redirection
Assignment
For this assignment, you are to design a simple shell which implements a subset of the
functionality of the Bourne Again Shell (Bash). The requirements for your shell are as follows:
• Continually prompt for textual user input on a command line.
• Parse user input according the provided grammar (see below)
• When a user enters a well formed command, execute it in the same way as a shell. You
must use the commands fork and exec to accomplish this. You may NOT use the C++
system() command.
• Allow users to pipe the standard output from one command to the input of another an
arbitrary number of times.
• Support input redirection from a file and output redirection to a file.
• Allow users to specify whether the process will run in the background or foreground
using an ’&’. Backgrounding processes should not result in the creation of zombie
processes. (Commands to run in the foreground do not have an ’&’, and commands
that run in the background do)
• Allow your program to take an option ”-t” which will run your shell the same way, just
without a prompt.
2
CSCE 313 Fall 2018
• (Bonus) Allow users to specify a custom prompt which supports printing the current
directory, username, current date, and current time.
Figure #4: Simple Shell Grammar
valid string = unix command || unix command REDIRECTION filename ||
unix command AMP || special command
unix command = command name ARGS || unix command PIPE unix command
special command = cd DIRECTORY || exit
command name = any valid executable/interpreted file name
AMP = &
ARG = string
ARGS = ARG ARGS || ARG
DIRECTORY = absolute path || relative path
PIPE = |
REDIRECTION = < || >
