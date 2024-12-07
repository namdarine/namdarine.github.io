---
layout: post

title: Dynamic Table

date: 2022-01-12 18:00:00

description: Concepts and understanding of Interface

tags: WIL

categories: JAVA

toc:
  sidebar: left
---

Could say the interface is the ‘guide line’ of the code. Using an interface reduces code modification and increases maintenance.

Java interface is similar to Java class.

- can include variable declarations
- can include methods

However, variables must be constants. Methods must be abstract. and the Java interface cannot be instantiated. We can use an interface to formally specify the logical level of an ADT. It provides a template for classes to fill.

Classes **implement** interfaces, but **cannot** extend interfaces\*. Cannot define constructors for a Java interface.

\*Class that implements an interface must implement all the methods declared in the interface. The method must have the same signature (name + parameters) declared in the interface. The class doesn’t need to implement the variables of an interface.

- All variables in an interface are public, static, and final + abstract, methods.
- Java interface can contain constants.

- Java Class

l Java Abstract class

l Java Nested class can implement the interface.

l Java Enum

- Java Dynamic proxy

Java interface **cannot** declare any variables.

→ Because inheriting from a class (extend), and implementing an interface (implements) are two different concepts. Therefore, they use different keywords.

All the methods defined in an interface should be implemented by another class (overridden). But, cannot override constructors.

Interfaces are compiled like classes and applications. Each of the interfaces is kept in a separate file.

Interfaces are a versatile and powerful programming construct.

### Benefits of using Interface

- Can **check the syntax of our specification**. The compiler uncovers any syntactical errors in the method interface definitions when compiling the interface.
- Can **verify that the interface contract is met by the implementation**. When compiling the implementation, the compiler ensures that the method names, parameters, and return types match what was defined in the interface.
- Can provide a consistent interface to applications from among alternate implementations of the ADT.

### Reason to use Interface

1. To achieve total abstraction.
2. Since Java doesn’t support multiple inheritance in case of class, but by using interface it can achieve multiple inheritance.
3. To achieve loose coupling
