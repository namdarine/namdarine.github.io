---

layout: post

title: Algorithm & Time Complexity

date: 2023-01-20 18:00:00

description: Concepts and understanding of Algorithm and Time complexity

tags: WIL

categories: Algorithm

toc:
  sidebar: left

---

An algorithm is a finite sequence of precise instructions for performing a computation or for solving a problem.
Also, the algorithm is any well-defined computational procedure that takes some values, or set of values, as input and produces some value, or set of values, as output. Thus, a sequence of computational steps transforms the input into the output.

# Properties of Algorithms
- **Input**: An algorithm has input values from a specified set.
- **Output**: From each set of input values an algorithm produces output values from a specified set. The output values are the solution to the problem.
- **Definiteness**: The steps of an algorithm must be defined precisely.
- **Correctness**: An algorithm should produce the correct output values for each set of input values.
- **Finiteness**: An algorithm should produce the desired output after a finite (but perhaps large) number of steps for any input in the set.
- **Effectiveness**: It must be possible to perform each step of an algorithm exactly and in a finite amount of time.
- **Generality**: The procedure should be applicable for all problems of the desired form, not just for a particular set of input values.

# What is meant by Algorithm Analysis?
Algorithm analysis is an important part of computational complexity theory, which provides theoretical estimation for the required resources of an algorithm to solve a specific computational problem.
So, the analysis of algorithms determines the amount of time and space resources required to execute the algorithm.

## Why Analysis of Algorithms is IMPORTANT?
- To predict the behavior of an algorithm without implementing it on a specific computer.
- It is much more convenient to have simple measures for the efficiency of an algorithm than to implement the algorithm and test the efficiency every time a certain parameter in the underlying computer system changes.
- It is impossible to predict the exact behavior of an algorithm. There are too many influencing factors.
- The analysis is thus only an approximation; it is not perfect.
- More importantly, by analyzing different algorithms, we can compare them to determine the best one for our purpose.

# Complexity of Algorithm
To analyze the efficacy of an algorithm, usually consider two measurements: **time** and **memory needed**.
An analysis of the time required to solve a problem of a particular size involves the **time complexity** of the algorithm. An analysis of the computer memory required involves the **space complexity** of the algorithm.

## Time Complexity
> The amount of time taken by an algorithm to run, as a function of the length of the input. It measures the time taken to execute each statement of code in an algorithm.

The time complexity of an algorithm can be expressed in terms of the number of operations used by the algorithm when the input has a particular size.

### Time complexity is significant
An algorithm is a finite sequence of well-defined instructions, typically executed in a computer, to solve a class of problems or to perform a common task. We also indicated the algorithm to be performed in a computer, which leads to the next variation, in terms of the operating system, processor, hardware, etc. that are used which can also influence the way an algorithm can be performed.

# Reference
- CS 430, Introduction to Algorithms, Spring 2023, prof. Xiaolang Wang, Illinois Institute of Technology

- Design and analysis of algorithms (2022) GeeksforGeeks. GeeksforGeeks. Available at: <a href="https://www.geeksforgeeks.org/design-and-analysis-of-algorithms/">geeksforgeeks</a> (Accessed: January 19, 2023). 
 
- Dineshpathak, A. (2022) Algorithmic complexity, Devopedia. Devopedia Foundation. Available at: <a href="https://devopedia.org/algorithmic-complexity#:~:text=Algorithmic">devopedia</a> complexity is a measure,asymptotically as n approaches infinity. (Accessed: January 19, 2023). 