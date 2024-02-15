\
[Return to Index](../Phys31415/)
# Computer Lab #1 Walkthrough
***
## Creating a Repl to Execute Qiskit Code
[Replit Home](https://replit.com/~)\
[Replit Tutorial Series](https://docs.replit.com/tutorials/overview)\
[FreeCodeCamp Replit Tutorial](https://www.freecodecamp.org/news/how-to-use-replit/)

After creating an account and logging in, press the `Create Repl` button.
Select the `Python` template. It will automatically generate a title for you.
Replit's free tier only allows you to create public projects (so don't publish any secrets).
Press the `Create Repl` button again and you'll be taken to their online IDE.

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

When I run the script, I get errors that


