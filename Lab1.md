\
[Return to Index](index.md)
# Quantum Computation Lab #1 - Quantum Teleportation [WIP]


For those of you doing the computer lab, replit is a good place to start.  Try typing "write a Qiskit code that demonstrates quantum teleportation and displays the circuit and the statistics of many trials" into the AI tool.  This is a ready supply of infinite Python examples.  You should be able modify the code yourself and understand what it’s doing (because you’ll need to explain it in the Lab Report), but you don't need to know how to create a program in Python, beginning-to-end, for this class.

There are many places to try to run quantum software, but asking replit to write code in qiskit is a good place to start.  Make your way to qiskit.com and Pennylane and create accounts.  I'll be pointing you there to play around with examples.

Your Lab Report should include what you're trying to demonstrate, how that’s being done by the computer/simulator, any data you gather, and your analysis of that data.  It needs to be long enough to demonstrate that you understand what you’re doing and what you’re seeing.  Please submit it in pdf.

For this first assignment: 1) create qubits, 2) change them, 3) measure them, and 4) gather statistics.

Create a circuit.
Initiate two qubits and two classical bits.
Apply Hadamard, X, Z, and controlled not operators, and measure the output for each.  Run the code several hundred times to gather statistics on your measurements and explain the results (Why is it 50/50?  Why is it 75/25?).

Normally, this will be due Friday, but late is fair this week.

Take a look at [this tutorial from qiskit](https://learning.quantum.ibm.com/course/basics-of-quantum-information/quantum-circuits) on the basics of a quantum circuit.  Lean on the AI tools heavily.  Ask ChatGPT to write your code, but not your lab report.  Please.

Simon Savitt has volunteered to answer any questions you may have.  He's cc'd on this email.  Please reach out to either/both of us if you have questions, are feeling lost, or having trouble.

I’m very interested in the pedagogy of what we’re attempting here for the first time.  So “this is terrible, I hate it” is valuable feedback.

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
