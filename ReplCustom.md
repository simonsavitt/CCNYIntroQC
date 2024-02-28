\
[Return to Index](index.md)
# Creating a Custom Repl to Run Qiskit [WIP]
Here I outline the steps I've taken to create a custom repl environment for running the latest version of Qiskit.

The existing [Repl Python template](https://replit.com/@replit/Python) has several issues, so we can't rely on it. 
For starters, it doesn't come with the latest version of Python.

Repl runs on a Linux distribution called NixOS, which uses the Nix package and configuration manager to enable reproducible environments we can run across different machines.

All Nix Repls have two configuration files: `replit.nix`, and `.replit`.\
To access these files, click the three dots on the file tree and select `Show hidden files`.

![image](https://github.com/simonsavitt/CCNYIntroQC/assets/3525578/ea973cf1-c226-4ec2-8818-08ae55b46d56)

The `.replit` file controls multiple aspects of your Repl's behavior including the run command, LSP ([Language Server Protocol](https://microsoft.github.io/language-server-protocol/)), and more. It follows the [toml configuration format](https://learnxinyminutes.com/docs/toml/).

The `replit.nix` file

### Learning Repl and Nix

#### Blog Posts
- [How we went from supporting 50 languages to all of them](https://blog.replit.com/nix)
- [All New Repls are Powered By Nix](https://blog.replit.com/powered-by-nix)
- [Will Nix Overtake Docker?](https://blog.replit.com/nix-vs-docker)
- [Super Colliding Nix Stores: Nix Flakes for Millions of Developers](https://blog.replit.com/super-colliding-nix-stores)

#### Written Guides
- [Replit & Nix](https://docs.replit.com/category/replit--nix) — Replit tutorial section on Replit & Nix
- [Getting started with Nix](https://docs.replit.com/programming-ide/nix-on-replit) — Replit & Nix getting started guide
- [Building with Nix on Replit](https://docs.replit.com/tutorials/python/build-with-nix) — Deploy a production web stack on Replit with Nix
- [Nix Pills](https://nixos.org/guides/nix-pills/) — Guided introduction to Nix
- [Nix Package Manager Guide](https://nixos.org/manual/nix/stable/) — A comprehensive guide of the Nix Package Manager
- [A tour of Nix](https://nixcloud.io/tour) — Learn the nix language itself
- [Configuring a Repl](https://docs.replit.com/programming-ide/configuring-repl) — How to configure the `.replit` file

#### Video Guides
- [Nixology](https://www.youtube.com/playlist?list=PLRGI9KQ3_HP_OFRG6R-p4iFgMSK1t5BHs) — A series of videos introducing Nix in a practical way
- [Taking the Nix pill](https://www.youtube.com/watch?v=QwLWIy2KleE) — An introduction to what Nix is, how it works, and a walkthrough of publishing several new languages to Replit within an hour.
- [Nix: A Deep Dive](https://www.youtube.com/watch?v=TsZte_9GfPE) — A deep dive on Nix: what Nix is, why you should use it, and how it works.
