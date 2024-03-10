\
[Return to Index](../index.md)
# Repl Tutorial Using Qiskit Template [WIP]
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

## Creating a Repl to Execute Qiskit Code
[Replit Home](https://replit.com/~)\
[Replit Tutorial Series](https://docs.replit.com/tutorials/overview)\
[FreeCodeCamp Replit Tutorial](https://www.freecodecamp.org/news/how-to-use-replit/)\
[Replit Desktop App](https://replit.com/desktop)

After creating an account and logging in, press the `Create Repl` button.
Select the `Python` template. It will automatically generate a title for you.
Replit's free tier only allows you to create public projects (so don't publish any secrets).
Press the `Create Repl` button again and you'll be taken to their IDE.

The central window is your editor. At the top, you''ll see the script file `main.py` is open, which stands for "main function". To the left are your file explorer and tools tabs.
To the right is your console and shell. You'll be printing your quantum circuits on the console.

The Replit AI tab can be opened either via the tools window or by clicking the AI button on the bottom left of the editor.
It will open as a tab on the right window. Alternatively, from the editor window you can use the `CTRL + I` keyboard shortcut to enter a prompt there.

Try pasting the following prompt into the Replit AI message box:
```
write a Qiskit code that demonstrates quantum teleportation and displays the circuit and the statistics of many trials
```

The code it generates for you will not run. For a bit of context, Qiskit is a Python module (or code library) which contains a set of functions we want to import so we can call them in our main function.

Here's the code it generated for me:
```
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram
from qiskit.extensions import Initialize

def create_bell_pair(qc, a, b):
    qc.h(a)
    qc.cx(a, b)

def alice_gates(qc, psi, a):
    qc.cx(psi, a)
    qc.h(psi)

def measure_and_send(qc, a, b):
    qc.barrier()
    qc.measure(a, 0)
    qc.measure(b, 1)

qc = QuantumCircuit(3, 2)

create_bell_pair(qc, 1, 2)
qc.barrier()

alice_gates(qc, 0, 1)
measure_and_send(qc, 0, 1)

simulator = Aer.get_backend('qasm_simulator')
result = execute(qc, simulator, shots=1024).result()
counts = result.get_counts(qc)

print(counts)
qc.draw()
```

When I run the script, I get a few errors which we'll investigate:

#### Error #1

```
The `qiskit` package is not installed, only `qiskit-terra` is installed. Starting in Qiskit 1.0.0 only the `qiskit` package will be published.
Migrate any requirements files still using `qiskit-terra` to use `qiskit` instead. See https://qisk.it/1-0-packaging-migration for more detail.
```

So this error is explaining that the Python template in Repl is not downloading the correct Qiskit package. Terra used to be the name for the compiler core of Qiskit up until they released version 1.0 (IBM has a naming scheme they call [The Qiskit Elements](https://qiskit.org/documentation/stable/0.24/the_elements.html)). Now that they've released version 1.0, they've renamed the core python package from `qiskit-terra` to just `qiskit`. Here is a note in the Qiskit changelog explaining this: https://github.com/Qiskit/qiskit/pull/11271. The guide for migrating from older Qiskit versions also explains the [old](https://docs.quantum.ibm.com/api/migration-guides/qiskit-1.0-installation#the-old-qiskit-structure) vs [new](https://docs.quantum.ibm.com/api/migration-guides/qiskit-1.0-installation#the-new-qiskit-structure) Qiskit structures.

#### Error #2

```
DeprecationWarning: The qiskit.extensions module is deprecated since Qiskit 0.46.0. It will be removed in the Qiskit 1.0 release.
```

If we take a look at the [version 1.0 release notes](https://docs.quantum.ibm.com/api/qiskit/release-notes/1.0#circuits-upgrade-notes) on the Qiskit documentation website, we'll find a note about this.

