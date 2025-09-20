# Why Machine Learning?
- Artificial Intelligence (AI) is opening fair access to advanced knowledge.
- AI is transforming the way we live and work (e.g., Driver Assistance Systems in cars, Robots in warehouses)
- Machine Learning is the central system behind AI
# What is Machine Learning?
## What is Learning?
Learning is a:
- change in mind/physical state.
- positive/useful change (**measured by a proper metric**) through repetitive trials, following instructions, and practices (via interaction with the outer world/experience).
- continual/non-linear/dynamic process.
- process of memorization and/or generalization.
Dictionary definition of learning: The alternation of behavior as a result of individual **experience**. When an organism can perceive and **change** its behavior, it is said to learn.
Another definition: Learning is making **useful changes** in he workings of our minds.
## Example of the Learning Process
### A Block-Arch Scenario
Suppose we do not know what an arch is, but someone told you “this is an arch.” You are going to form a set of mental descriptions of the concept of an arch (training data).
### A Block-Arch Scenario: Observation of “Hand Change”
An arch causes a strange phenomenon:
- Imagine you had a toy car and you tried to push it through an arch, you would fail because the arch would block your arm from moving, therefore stopping the car as well.
- In order to get through you need to release the car and reach around to the other side by switching hands as the car must be dragged through the arch.
- Now we have a new observation regarding arches and can better understand what arch is.
### Visualizing an Arch Given New Data
We know that an arch has 2 blocks with a horizontal block.
Visualization 1:
![[Visualization 1.png]]
There’s an issue with this visualization, this visualization fails to adhere to our hand-change observation.
Visualization 2: 2 blocks with a horizontal block **and** the blocks must not touch.
![[Visualization 2.png]]
This visualization has issues too, the hand-change rule is not followed and the blocks are not supporting the horizontal block. We need to be more specific.
Visualization 3: 2 **standing** blocks **supporting** a horizontal block **while** the blocks **do not** touch.
![[Visualization 3.png]]
This adheres to our hand-change and fits every other description. However our current description is too rigid, the supporting blocks need not just be blocks, they could be wedges too. Let’s try that.
Visualization 4: 2 **standing** blocks **or** wedges **supporting** a horizontal block **while** the blocks **do not** touch.
![[Visualization 4.png]]
As we can see, this accounts for far more arches.
**Right learning necessitates the right criteria that describes the original task fundamentally.**
**Key takeaways:**
- It is important to have the right learning metric.
- It is important to have enough examples (data).
## What is Machine Learning?
Machine learning is the way a machine learns to **perform** a task.
- Such as: **Classification**, **Object detection**, **Sentence generation**, and **Simulation of Human Intelligence**.
### A machine can learn in 2 ways:
- Heuristic Programming: Finding a practical solution rather than targeting the exact and theoretical frameworks. (**learning a function**)
- Automatic Learning: **Functional models** are to be **updated** based on **observations** (past data) and **performance metrics**.
- Note that it is **impossible** to program the process of human recognition. (**no** direct instructional programming)
### Machine Learning as a heuristic solution for classification:
- Different models give different classification results.
- Generalization is the **primary** challenge for Machine Learning.
- Note that the heuristic/simulating methods can be far better than human performance, ie. more accurate, faster, higher memory capacity.
## The Early Example of Machine Learning
### The MIT Learning Machine (1950)
A magnetized mouse named “Theseus” would **systematically** explore a maze until it found the cheese. If it were placed in the maze a second time, Theseus would go **straight** to the cheese. If you were to change the maze, Theseus would **“forget”** the old solution and start the **learning process** again.
### Theseus Operation: Maze Solving Machine
Theseus had:
- A **finger** to move East/West/North/South
- **Memory** for each square to remember the last direction in which Theseus left that sqaure.
- As Theseus comes to the square again the memory for the square is **updated counterclockwise** (e.g., east would be updated to north) in order to ensure that Theseus takes every possible route.
- Two modes of Machine Operations: **Exploration** and **Goal Strategy**.
### Why is Theseus a Learning Machine
Theseus is a learning machine because:
- Theseus finds a path in the maze by trial and error.
- Theseus memorizes the found path.
- It also **automatically** explores the new path when the maze is changed.
### Definition of Machine Learning
Textbook definition: A computer program that is said to **learn** from **experience E** with respect to some class of **tasks T**, and some **performance measure P**, if its performance at tasks in **T**, as measured by **P**, improves with experience **E**.
# Machine Learning Principles
Functions: model
Experience: data
Metric: loss
Change: training/updating parameters.
**Question:** Why is it not a good idea to just pursue a complex modeling? Why do we need to consider the number of data points we have?
# Machine Learning and AI
Many Machine Learning schemes **already existed** before Artificial Intelligence appeared. Like: Decision, Estimation Theory, and Optimization Theory. But they are reframed as Machine Learning in the context of Artificial Intelligence in order to emphasize its ability of automatic learning and their role in achieving the tasks related to human intelligence.
## Birth of AI in 1956
The study is to proceed on the basis of **conjecture** that **every aspect of learning** or any other feature of intelligence can in principle be **precisely described** such that **a machine can be made to simulate it**.
# Two Poles in AI: Heuristic vs. Symbolic Approach
### Connectionism (Heuristic Approach)
- Learns from data
- Focuses on end effect (Cares more about correct output, method may be unknown)
- **Inductive** (Uses trial and error)
### Symbolic AI (Rule Based)
- Uses logical rules as opposed to datasets
- Does not use data to derive an optimal function
- **Deductive** (Uses programmed logic)
