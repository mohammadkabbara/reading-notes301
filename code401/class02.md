# Packages

Package = directory. Java classes can be grouped together in packages. A package name is the same as the directory (folder) name which contains the .java files. You declare packages when you define your Java program, and you name the packages you want to use from other libraries in an import statement

# Common imports
There are 166 packages containing 3279 classes and interfaces in Java 5. However, only a few packages are used in most programming. GUI programs typically use at least the first three imports.

import java.awt.*;	Common GUI elements.

import java.awt.event.*;	The most common GUI event listeners.

import javax.swing.*;	More common GUI elements. Note "javax".

import java.util.*;	Data structures (Collections), time, Scanner, etc classes.

import java.io.*;	Input-output classes.

import java.text.*;	Some formatting classes.

import java.util.regex.*;	Regular expression classes.

**NetBeans will create your imports** If you forgot to write import statements, or don't remember which package a class is in, no problem. Just right click on the source file and choose Fix Imports. It will add all necessary import statements.

# loops

In programming languages, looping is a feature which facilitates the execution of a set of instructions until the controlling Boolean-expression evaluates to false.

Java provides different types of loops to fit any programming need. Each loop has its own purpose and a suitable use case to serve.

Here are the types of loops that we can find in Java:

1-**Simple for loop** A for loop is a control structure that allows us to repeat certain operations by incrementing and evaluating a loop counter.

**2-Enhanced for-each loop** 

**3-While loop** The while loop is Java's most fundamental loop statement. It repeats a statement or a block of statements while its controlling Boolean-expression is true.

For a detailed example, have a look at the dedicated post: Java While Loop.

**4-Do-While loop** The do-while loop works just like the while loop except for the fact that the first condition evaluation happens after the first iteration of the loop.