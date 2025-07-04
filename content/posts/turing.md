+++
title = "The Code You Write is a Lie"
date = "2025-07-03"
updated = "2022-07-03"

[taxonomies]
tags=["computation","basics"]



[extra]
comment = true
+++






# **Introduction**

Imagine you're writing your first program ever probably the OG "Hello, World!" that we write in every language and use to test every compiler. Many people find it magical, but behind that single line lies an entire universe of complexity. It's not as simple as printing text deep inside the CPU, logic gates are flipping, 1s and 0s are shifting, and layers of computation are unfolding.

In this article, we'll explore the computation side of that "Hello, World!" moment. And by the end, you might just be surprised at how deep the things are.

# **How computation started**

The idea of computation began in the human mind as a way to solve complex problems by breaking them into step-by-step instructions that lead to a solution. Eventually, humans began writing these steps down, transforming raw thought into structured logic on paper. This became the earliest form of computational reasoning.

As we solved more problems, we started noticing patterns. Many solutions followed similar logical structures. This led to a powerful realization:
What if we could create reusable blocks of logic, like modules, and use them to solve different problems?

At the same time, another question emerged:

_What kinds of problems can even be broken down like this?_
_And can we build a model that captures all solvable problems using these logical building blocks?_

This is where early computation models came into play.

**DFA (Deterministic Finite Automata)** and **NFA (Non-deterministic Finite Automata)** fall under the category of Finite Automata. They were designed to follow simple logical flows, essentially acting as pattern recognizers. However, they have no memory, so they can’t handle tasks that require remembering past input.

Then came Pushdown Automata (PDA). To put it bluntly, it's like simulating prefix or postfix logic on paper. For example, evaluating expressions like `+ 3 4 or 3 4 +`. To do that, you need a temporary memory space, and that's where the stack comes in. PDAs can remember things using this limited memory, allowing them to handle more complex, nested structures like matching brackets or basic code blocks.

After many iterations of exploring such models, in 1936, Alan Turing proposed the **Turing Machine**, a theoretical model that could simulate any computation process. It wasn’t just a theory he mathematically proved that this machine could represent the logic behind any algorithmically solvable problem.


![Markdown Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/0/03/Turing_Machine_Model_Davey_2012.jpg/330px-Turing_Machine_Model_Davey_2012.jpg)


# **Turing Machine = Theoretical Blueprint of All Modern Computers**

Now we know the breif history of compuatation and lets see how **Turing machine** machine became a blueprint of all modern computers

Like you saw in the above image turing machine is made up of a control unit and a infinite tape, the tape is divided into cells and have 1s and 0s on them 

- The control unit which help to read the current tape symbol
- Writes a symbol on the tape
- Moves one position to the left or right
- Switches to the next state

![Markdown Logo](https://www.trccompsci.online/mediawiki/images/5/5f/Turingmachinetapehead.gif)

A Turing machine reads a long strip of paper called the tape. This tape contains symbols such as 1s, 0s, or blank spaces. The machine reads one symbol at a time and follows a set of rules that tell it what to do based on the current symbol and its current situation, known as a state. Each rule instructs the machine to change to a new state and then take an action. The action can either be writing a new symbol on the tape or moving one step to the left or right. The machine keeps repeating this process reading a symbol, deciding what to do, writing or moving, and then continuing. However, if it reaches a point where there is no rule that matches the current symbol and state, the machine simply stops. This is called halting.

So you might start to wonder, how does all of this actually make sense? Every programming language, at its core, runs on logic. And **logic is governed by strict rules**. When you write a set of steps or a defined procedure to solve a problem, you are applying those rules in a structured way. That set of steps is called an algorithm. It is not just a bunch of random instructions. It is a rule-based method that ensures the program behaves in a predictable and logical way.

so still how does turing machine still make sense as a machine? we can actually map the parts of turing machine to modern computers making it equivalent blueprint of modern computers 


| **Turing Machine Part**                        | **Modern Computer Equivalent**                   | **Explanation**                                                                                                                                               |
| ---------------------------------------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Tape (infinite in both directions)**         | **RAM or storage (finite memory)**               | The Turing Machine uses a tape to read and write data. Computers use memory (like RAM or hard drives) to store and update information.                        |
| **Head (reads and writes one cell at a time)** | **CPU read and write operations**                | The Turing Machine's head moves left or right, reading and writing one symbol at a time. The CPU reads and writes to memory in a similar step-by-step manner. |
| **Symbols on the tape**                        | **Bits, bytes, or instructions**                 | The Turing Machine works with simple symbols like 0, 1, or blank. Modern computers use binary, machine code, and characters to represent and process data.    |
| **States**                                     | **Program counter or execution state**           | The Turing Machine changes states based on input. Computers keep track of what to do next using a program counter and execution state.                        |
| **Transition function**                        | **Program logic (like if, while, or switch)**    | The Turing Machine uses rules that say what to do in each situation. In programming, this is like writing conditional logic to control program flow.          |
| **Halting**                                    | **Program termination**                          | When a Turing Machine halts, it stops working. This is like when a computer program finishes and exits.                                                       |
| **Input on tape**                              | **User input, command-line arguments, or files** | Turing Machines take input from the tape. Computers take input from keyboards, files, or other sources.                                                       |


# How it's all connected

As a exaple we discussed how a simple hello world program is actually having lot of things going behind now we know brief about computation lets see how it actually connected by stripping each layer of abstratction 

basically every programming langauges is based on one another many of know C++ is improved version of C but how does C exist in the first place ? its like pulling all layers of onion to the core of bulb and at core of bulb of every programmimg language is the OG **Assembly** and assembly is just simplifed version of machine code (which is just 1s and 0s) So, our beloved C language is forst written in assembly and then bootstraped by C itself thik it of like v1 of C is written in assembly and v2 is written with assembly and v1 C so in that way C is a bootstraped language and other languges like python and java are written in C and then bootstraped 
## How a programming language exist in first place ?
Now that we understand how programming languages came into existence, let’s take a closer look at what really happens when we write a simple program like printing "Hello, World". When you use a function like `printf()`, it may look simple on the surface, but behind the scenes, it follows a defined set of instructions written in a lower-level language like C. These instructions are eventually translated into assembly language, which is closer to how the computer actually works. From there, an assembler turns that into machine code, which the CPU executes directly. That entire chain of logic is what makes the words "Hello, World" appear on your screen. It all starts from your code but passes through multiple layers of logic before it reaches the hardware.


So let's zoom out a bit and connect above logic to Turing machine which inturns make the Hello world the Turing computable problem 

## How it's connected
- You write printf("Hello, World") in a high-level language like C
  - Input is placed on the Turing Machine tape

- The compiler reads this code and translates it into lower-level instructions
  -  The Turing Machine begins in a start state and starts scanning the tape

- These instructions are converted into assembly language
  - The machine moves through defined states based on symbols it reads

- The assembler takes the assembly code and produces machine code
  - The Turing Machine writes new symbols on the tape and changes states accordingly

- The CPU fetches and executes the machine code
  - The machine continues processing until no more rules apply

- When execution is done and "Hello, World" appears on screen
  - The Turing Machine halts after completing the computation

 ## Unsolvable 

Turing non-computable problems are problems for which no algorithm can solve all possible cases. A classic example is the Busy Beaver problem, which asks for the maximum number of steps a Turing machine of a given size can take before halting. Although some small cases have been solved through decades of effort, the general problem is uncomputable. This means no computer, no matter how powerful, can solve it for all inputs. In real-world terms, these problems resemble programs that loop forever with no predictable end, but not all infinite loops are uncomputable only those proven to have no general solution fall into this category.


# Conclusion
With every breakthrough in the field of computation, we see new limits of computation defined. Even the current AI is based on Turing principles. At the core, AI is just a big prediction machine, and everything we see is related to computation or feels like a simulation when you observe the world more deeply. The only things that aren’t based on Turing are living beings humans because we act upon emotions and are not governed strictly by a set of rules. When something like that is achieved by AI, it becomes what we call AGI.

And next time you write a piece of code, remember it is not magic, but the result of layers of abstraction hidden beneath all the way down to 1s and 0s, governed by rules.




