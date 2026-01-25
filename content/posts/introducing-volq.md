---
title: "Introducing Volq: A programming language for simulating quantum computation"
date: 2026-01-25
draft: false
tags:
  - volq
  - quantum-computing
---
![Volq](/images/volq/volq_banner.png)

Today, I want to introduce a project I've been working on for a while. 

Volq is an interpreted Domain Specific Language (DSL) that enables you to simulate quantum computing algorithms on your classical computer. You can play around with existing algorithms to better understand how they solve problems, or write your own from scratch using the easy-to-learn <abbr title="Domain Specific Language">DSL</abbr> based on the quantum circuit model.
<!--more-->
I originally started this project to create a framework for simulating the quantum circuit model. But as time and development went on, I realised more and more that I am actually just writing a compiler for quantum computing software, or in other words, _a linear algebra compiler for generating matrices_. That's when I decided to pivot to writing a programming language!

The backend and frontend of Volq is written 100% in Python and uses the libraries NumPy and UnitTest. The banner was created in the fabulous Google Slides (yes, seriously), because Canva wanted to charge me money to create an oval shape with dotted lines, so I thought I'd improvise.
# Why?
During my third year at university, I took a module called CS3600 Quantum Computation. In this module, I learned all the mathematics behind quantum computing and about different quantum algorithms that exist, such as Deutsch-Jozsa, Bernstein Vazirani, Grover's Algorithm and Shor's Algorithm. 

I won't lie, I struggled with the mathematics a fair bit and I always wished I could experiment with a quantum computer, so I could better understand the outputs of different quantum algorithms given different inputs. Some solutions do exist, but in my own personal opinion, I found Python libraries like IBM Qiskit or Google Cirq somewhat unintuitive without sinking a significant amount of time into them. IBM does allow you to run your own circuits on a real quantum computer for free up to 5 qubits, but this is quite a limited number of qubits such that there's more advantages to just simulating it, and this also requires you to register an account for another service.

After completing the exam for this module, I wanted to continue to learn more about quantum computing beyond the material of the CS3600 module and also to create this project to fill in this gap. I wanted to make applying gates on a basis state vector intuitive to the quantum circuit model itself, similar to slices of gates in a circuit. That way, you can spend less time learning and pick up the language very quickly.
# Can I see some code in Volq?
Sure! Here is the circuit diagram of the Deutsch-Jozsa algorithm, courtesy of Wikipedia:
![Deutsch-Jozsa Circuit Diagram](/images/volq/deutsch-jozsa-circuit-diagram.png)
And here's the corresponding Volq code, using a balanced function in the oracle:
```
QUBITS 9
RUNS 1000
INIT

APPLY X8
APPLY H0 H1 H2 H3 H4 H5 H6 H7 H8
APPLY CNOT8,0
APPLY CNOT8,1
APPLY CNOT8,2
APPLY CNOT8,3
APPLY CNOT8,4
APPLY CNOT8,5
APPLY CNOT8,6
APPLY CNOT8,7
APPLY H0 H1 H2 H3 H4 H5 H6 H7
MEASURE ALL
```
As you can see, the programming language is intuitive by sticking closely to the circuit diagram. Rather than learning how to create distinct circuit objects with code, this is all handled under the hood for the user, along with the number of shots and measurement.

This isn't perfect though, and I'm looking forward to making improvements in the future to make it even more intuitive. This includes a sub-DSL for oracles (e.g. `ALL 0 EXCEPT 0110`) so that the option for running them in one line is there, and creating shorthands for applying the same operator on many qubits at once (e.g. `H@` for a uniform superposition across the whole circuit, or `X[0,3]` for applying Pauli X across the first 4 qubits!).
# How long do you plan to work on it for?
It would be ideal to reach a v1.0.0 release within the next 12 months, but I work in cyber security and have a lot of other things happening on the side too, so I'm expecting it to realistically take a maximum of up to 24 months. I'll likely be working on the project on and off, and also I will be doing a lot of independent research into how compilers and parsers work under the hood, which will take a lot of time and won't be visible in the Git commit history.

At the time of writing, Volq is currently in alpha status. The focus during the alpha is adding most of the core features of the quantum circuit model to the <abbr title="Domain Specific Language">DSL</abbr> and following the mathematics by the book; inefficient, but perfectly correct. My intentions for beta development include polishing everything up to a high standard and focusing on optimisation of operator generation to accelerate circuit execution, which would ultimately allow for larger quantum circuits.
# How can I look at the source code and try it out?
First of all, thanks for scrolling down to the bottom of the page, or perhaps even reading to the end. Also the word "quantum" was mentioned 15 times in this article, I'm sorry.

The repository for Volq is on my GitHub, which I've linked below.

### [Link to Volq on GitHub](https://github.com/michaelchips/volq-quantum)
