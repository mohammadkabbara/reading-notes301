# What is functional programming?

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data 


# What is a pure function and how do we know if something is a pure function?

It returns the same result if given the same arguments

# What are the benefits of a pure function?

The code’s definitely easier to test. We don’t need to mock anything. So we can unit test pure functions with different contexts:

Given a parameter A → expect the function to return value B

Given a parameter C → expect the function to return value D

# What is immutability?

**Unchanging over time or unable to be changed.**

When data is immutable, its state cannot change after it’s created. If you want to change an immutable object, you can’t. Instead, you create a new object with the new value.

# What is Referential transparency?


n functional programming, referential transparency is generally defined as the fact that an expression, in a program, may be replaced by its value (or anything having the same value) without changing the result of the program. This implies that methods should always return the same value for a given argument, without having any other effect. This functional programming concept also applies to imperative programming, though, and can help you make your code clearer.

