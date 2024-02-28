\
[Return to Index](index.md)
# Creating a Custom Repl to Run Qiskit [WIP]
Here I outline the steps I've taken to create a custom repl environment for running the latest version of Qiskit.
The existing [Repl Python template](https://replit.com/@replit/Python) has several issues, so we can't rely on it. For starters, it doesn't come with the latest version of Python.
Repl runs on a Linux distribution called NixOS, which uses the Nix package and configuration manager to enable reproducible environments we can run across different machines.

All Nix Repls have two configuration files: `replit.nix`, and `.replit`.\
To access these files, click the three dots on the file tree and select Show hidden files.\
![image](https://github.com/simonsavitt/CCNYIntroQC/assets/3525578/ea973cf1-c226-4ec2-8818-08ae55b46d56)

## Articles on Repl and Nix
[All New Repls are Powered By Nix](https://blog.replit.com/powered-by-nix)\
[Using Nix with Replit](https://docs.replit.com/programming-ide/nix-on-replit)\
