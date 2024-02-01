---

layout: post

title: Discrete Math & Proposition and Logical operation 1

date: 2023-01-18 18:00:00

description: Concepts and understanding of Discrete Math

tags: WIL

categories: Discrete_Structure

toc:
  sidebar: left

---

# What is 'Discrete Math'?
> Discrete mathematics is the study of mathematical structures that can be considered "discrete" (in a way analogous to discrete variables, having a bijection with the set of natural numbers) rather than "continuous" (analogously to continuous functions). Objects studied in discrete mathematics include integers, graphs, and statements in logic. In this study, topics in "continuous mathematics", real numbers, calculus, or Euclidean, are not taken care of.

# Then Why does CS Major study discrete math?
First, develop mathematical maturity, which is understanding and creating mathematical aguments. Programmers are a dime a dozem. Software engineeers with strong math backgrounds are balued.
Pattern recognition or machine learning includes automatic typing correction on your smartphone, face detection in its camera, and speech recognition when you call an automated telephone service.
Computational tasks in fields ranging from biology to finance require a good knowledge of optimization.

Concepts and notations from discrete mathematics are useful in studying and describing objects and problems in branches of computer science, such as computer algorithms, programming languages, cryptography, automated theorem proving, and software development. Computer implementations are significant in applying ideas from discrete mathematics to real-world problems.
Simply saying, it provides an essential foundation for virtually every area of computer science, and its applications are correspondingly vast.

# Why is Logic a meaningful topic for a CS major to learn?
Logic' is the language used for most formal specification languages and is fundamental for understanding much of the literature in verification and programming language foundations and design. Program verification and formal methods are seeing increasing adoption in the industry, and are being used in tandem with traditional testing techniques to increase the confidence that software behaves as it is supposed to.
Also, Logic is the basis of all mathematical reasoning, and of all automated reasoning. It has practical applications to the design of computing machines (hardware), to the specification of systems, to artificial intelligence, computer programming, to programming languages, and to other areas of computer science, as well as to many other fields of study.
FOL and higher-order logics are applied a lot in databases. Many query language have logical foundations. For example, Datalog (essentially a restricted version of Prolog for querying data) is logic programming language whose semantic is defined based on models for FOL formulas. Integrity constraints are expressed in sublanguages of FOL.

**Logic**: the study of formal or valid reasoning. Logically allows precision for technical specifications, contracts, medical protocols, computer hardware and software, mathematics, etc.

# Propositions and Logical Operations
* The raw material for logic is the proposition - a declarative statement that is either true or false.
- Every proposition has a truth value: exactly one of the **values** true, or false.
* A propositional variable, typically _p_, _q_, _r_, or similar letter, is often used to represent a proposition, perhaps with an unknown truth value.
- In most cases, we readily and empirically recognize a proposition because (a) it is clearly true, (b) it is clearly false, and (c) it has a truth value even though we don't know it.
* Logical operators create new propositions from the old. Logical **and** and **or** create a (compound) proposition from two original propositions. Logical negation ($$\neg$$) creates a new proposition by flipping the truth value of a single proposition.
* Search engines use logic, typically the logical and, to return web pages that have both (or all) of a list of search terms.

## Proposition
>'Proposition' is a declarative sentence that is either true or false. Propositions (statements) that are either true or false are the raw material of the mathematical industry.

Propositions plus connectives $\rightarrow$ new propositions

|Connective|prop. _p_: "It is ranning."<br> prop. _q_: "I am at home."|prop. variable form|
|:---:|:---:|:---:|
| Negation | It is not raining | $\neg$_p_ |
| Conjunction | It is raining and I am at home | _p_ $$\wedge$$ _q_ |
| Disjunction | It is raning or I am at home | _p_ $$\vee$$ _q_ |
| Exclusive or | It is raining or I am at home, but not both | _p_ &oplus; _q_|
| Conditional | If it is raining then I am at home | _p_ $$\rightarrow$$ _q_|
| Biconditional| It is raining if and only if I am at home | _p_ $$\leftrightarrow$$ _q_|

<br>

### Example
The following statements are propositions whether it is Ture or not.
* There is an integer that is both even and odd.
* Mies van der Rohe's buildings have ornate embellishments.
* IIT was founded in 1940.

Following statements are **NOT** propositions whether it is True or not.
* What game includes "Go directly to jail, and do not pass 'GO'?"
   - Because the question is not a proposition statement.
* Log on to website with your card credentials.

With the propositions <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;_p_: It is below freezing.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; _q_: It is snowing.
<br>
Represent the following propositions using _p_, _q_, and logical connectives. 

(a) **It is below freezing and snowing**: _p_ $$\wedge$$ _q_

(b) **It is below freezing but not snowing**: _p_ $$\wedge$$ _$$\neg$$q_

(c) **It is not below freezing and it is not snowing**: _$$\neg$$p_ $$\wedge$$ _$$\neg$$q_

(d) **It is either snowing or below freezing (or both)**: _p_ $$\vee$$ _q_
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$$\rightarrow$$ because of "or both", the logical connective of this statement is **inclusive or**, NOT exclusive or.

#### Truth Table
##### Negation

|_p_|_$$\neg$$p_|
|:---:|:---:|
|T|F|
|F|T|

##### Conjunction

|_p_|_q_|_p_ $$\wedge$$ _q_|
|:---:|:---:|:---:|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|F|

##### Disjunction

|_p_|_q_|_p_ $$\vee$$ _q_|
|:---:|:---:|:---:|
|T|T|T|
|T|F|T|
|F|T|T|
|F|F|F|

##### Exclusive or

|_p_|_q_|_p_ &oplus; _q_|
|:---:|:---:|:---:|
|T|T|F|
|T|F|T|
|F|T|T|
|F|F|F|

## Evaluating Compound Propositions
- Propositions can be joined together by the logical operators $$\wedge$$, $$\vee$$. Negation ($$\neg$$) only acts on one proposition and cannot join two together.
- Compound propositions can be joined together $$\wedge$$, $$\vee$$.
- The operator precedence is 1. $$\neg$$ 2. $$\vee$$ 3. $$\wedge$$ 4. $$\rightarrow$$ 5. $$\leftrightarrow$$. In the absence of clarifying parentheses, the operator leftmost in this order is evaluated first.

### Example
1. **_p $$\wedge$$ q $$\vee$$ r_**: _((p $$\wedge$$ q) $$\vee$$ r_
2. **_p $$\vee$$ $$\neg$$q $$\wedge$$ p $$\vee$$ r_**: _(p $$\vee$$ (($$\neg$$q) $$\wedge$$p) $$\vee$$ r)
3. **_$$\neg$$p $$\wedge$$ $$\neg$$ q $$\vee$$ r_**: _(($$\neg$$p) $$\wedge$$ ($$\neg$$q)) $$\vee$$ r

**Translate the following English sentence into a compound proposition**
Either I won't stay home from school today or there will be a blizzard or my car will not start.

- _p_: stay home
- _q_: blizzard
- _r_: car no start
$$\Rightarrow$$ _($$\neg$$p) &oplus; q &oplus; r_

The reason why it is not disjunction ($$\vee$$) is the sentence starts with 'Either'. Therefore, use 'exclusive or (&oplus;).

## Conditional Statements
The conditional statement captures the logical meaning of "hypothesis implies conclusion." A conditional statement _p $$\rightarrow$$ q_ can be thought of as a one-way contract. When are you happy with the contract? Certainly when _q_ is true, regardless of _p_. Would be unhappy if _p_ is true, but _q_ is false. For example, "_p_: you pay the price; _q_: you get the item." When you pay the price and get the item, you are happy, but when you pay the price and do not get the item, you are not happy. In the other situation, do not pay the price and get the item, you are a happy, a free item. And do not get the item without paying, you are also happy.
There are many ways of posing a conditional statement in English. Some of them are intuitive, but most have to be gotten used to or memorized. The conditional statement **has closely related, important, relatives that are also conditional statements: the converse, the contrapositive, and the inverse, all based on the original conditional but with other switched or with negation**.
The biconditional statement, _p $$\leftrightarrow$$ q_, can be thought of as a **two-way contract**, in which **both parties make sure they don't give away anything for free**.

#### Truth Table
##### Conditional statement

|_p_|_q_|_p $$\rightarrow$$ q_|
|:---:|:---:|:---:|
|T|T|T|
|T|F|F|
|F|T|T|
|F|F|T|
	
##### Biconditional statement

|_p_|_q_|_p $$\leftrightarrow$$ q_|
|:---:|:---:|:---:|
|T|T|T|
|T|F|F|
|F|T|F|
|F|F|T|

#### Expressing the conditional
_p $$\rightarrow$$ q_ can be expressed in many ways.

- if _p_ then _q_
- _p_ implies _q_
- _p_ is sufficient for _q_
- _q_ whenever _p_
- _q_ is necessary for _p_
- _p_ only if _q_
- _q_ if _p_
- _q_ follows from _p_

#### Example
_p_: "I put money in the drink machine," and _q_: "I get a cock;" what truth values of _p_ and _q_ make you happy about the whole coke-buying situation? Does your answer correspond to a truth table?

- _p $$\rightarrow$$ q_

|_p_|_q_|_p $$\rightarrow$$ q_|
|:---:|:---:|:---:|
|**T**|**T**|**T**|
|T|F|F|
|**F**|**T**|**T**|
|**F**|**F**|**T**|

**NOTE**: Whatever the result of the right-hand side, _q_, if the left-hand side, _p_, is False, then the conditional statement is True.

# Reference
- Illinois Institue of Technology, Discrete Structure, CS 330 Spring 2023, prof. Matthew Bauer