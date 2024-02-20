\
[Return to Index](index.md)
# Creating a Repl to Execute Qiskit Code [WIP]
***
[Replit Home](https://replit.com/~)\
[Replit Tutorial Series](https://docs.replit.com/tutorials/overview)\
[FreeCodeCamp Replit Tutorial](https://www.freecodecamp.org/news/how-to-use-replit/)\
[Replit Desktop App](https://replit.com/desktop)

After creating an account and logging in, press the `Create Repl` button.
Select the `Python` template. It will automatically generate a title for you.
Replit's free tier only allows you to create public projects (so don't publish any secrets).
Press the `Create Repl` button again and you'll be taken to their IDE.

The central window is your editor. At the t op, you''ll see the script file `main.py` is open, which stands for "main function". To the left are your file explorer and tools tabs.
To the right is your console and shell. You'll be printing your quantum circuits on the console.

The Replit AI tab can be opened either via the tools window or by clicking the AI button on the bottom left of the editor.
It will open as a tab on the right window. Alternatively, from the editor window you can use the `CTRL + I` keyboard shortcut to enter a prompt there.

At this point, main.py will contain a script for a "Hello World!" program using a web application Python module named Flask, which we'll erase.
On the tools tab to the bottom left, scroll to `Packages` and click on it. It will open another tab on the right.
Flask is the only package currently installed. We could remove it as we won't be using it, but it's fine to leave it there.


Now we'll search for and install the packages we need to run Qiskit code. These are the packages we need:
qiskit
numpy
matplotlib
pylatexenc
pycparser (C parser in Python required for installing Qiskit)

The version of Qiskit shown in search will be qiskit@1.0.0
The version we DON'T want is qiskit-terra@0.46.0
Take a look at the console tab. It will say `poetry add '<package ==version>'`
