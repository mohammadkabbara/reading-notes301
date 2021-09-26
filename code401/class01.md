
# Variables

**The Java programming language defines the following kinds of variables:**

*Instance Variables (Non-Static Fields)* objects store their individual states in "non-static fields", that is, fields declared without the static keyword. Non-static fields are also known as instance variables because their values are unique to each instance of a class

*Class Variables (Static Fields)* A class variable is any field declared with the static modifier; this tells the compiler that there is exactly one copy of this variable in existence

*Local Variables* Similar to how an object stores its state in fields, a method will often store its temporary state in local variables.

*Parameters* Recall that the signature for the main method is public static void main(String[] args). Here, the args variable is the parameter to this method. The important thing to remember is that parameters are always classified as "variables" not "fields". This applies to other parameter-accepting constructs as well (such as constructors and exception handlers) that you'll learn about later in the tutorial. Example: main method.

# Naming

Every programming language has its own set of rules and conventions for the kinds of names that you're allowed to use, and the Java programming language is no different. The rules and conventions for naming your variables can be summarized as follows:

1-Variable names are case-sensitive. A variable's name can be any legal identifier — an unlimited-length sequence of Unicode letters and digits, beginning with a letter, the dollar sign "$", or the underscore character "_".

2-Subsequent characters may be letters, digits, dollar signs, or underscore characters. Conventions (and common sense) apply to this rule as well. When choosing a name for your variables, use full words instead of cryptic abbreviations. Doing so will make your code easier to read and understand.

3-If the name you choose consists of only one word, spell that word in all lowercase letters. If it consists of more than one word, capitalize the first letter of each subsequent word

# Operators

 Operators are special symbols that perform specific operations on one, two, or three operands, and then return a result.

 *The operators in the following table are listed according to precedence order. The closer to the top of the table an operator appears, the higher its precedence. Operators with higher precedence are evaluated before operators with relatively lower precedence. Operators on the same line have equal precedence. When operators of equal precedence appear in the same expression, a rule must govern which is evaluated first. All binary operators except for the assignment operators are evaluated from left to right; assignment operators are evaluated right to left.*

 | Operators |  Precedence |  
----------  | ------|
| postfix    |	expr++ expr--|
| unary    | ++expr --expr +expr -expr ~ !    |
| multiplicative  |* / %   |
| additive   |+ -|
| shift|<< >> >>>|
|  relational  |< > <= >= instanceof    |
| equality     | == !=     |
| bitwise AND   |&   |
| bitwise exclusive OR   |^      |
|  bitwise inclusive OR   |  ||  |
| logical AND |&&|
| logical OR   |||    |
| ternary   | ? :  |
| assignment|= += -= *= /= %= &= ^= |= <<= >>= >>>=  |

# Expressions, Statements, and Blocks

**Expressions**
An expression is a construct made up of variables, operators, and method invocations, which are constructed according to the syntax of the language, that evaluates to a single value. You've already seen examples of expressions, illustrated in bold below:

```int cadence = 0;
anArray[0] = 100;
System.out.println("Element 1 at index 0: " + anArray[0]);

int result = 1 + 2; // result is now 3
if (value1 == value2) 
    System.out.println("value1 == value2");
```

**Statements**
Statements are roughly equivalent to sentences in natural languages. A statement forms a complete unit of execution. The following types of expressions can be made into a statement by terminating the expression with a semicolon (;).

Assignment expressions

Any use of ++ or --

Method invocations

Object creation expressions

Such statements are called expression statements. Here are some examples of expression statements.

```// assignment statement
aValue = 8933.234;
// increment statement
aValue++;
// method invocation statement
System.out.println("Hello World!");
// object creation statement
Bicycle myBike = new Bicycle();
```

# Blocks

A block is a group of zero or more statements between balanced braces and can be used anywhere a single statement is allowed. The following example, BlockDemo, illustrates the use of blocks:

```class BlockDemo {
     public static void main(String[] args) {
          boolean condition = true;
          if (condition) { // begin block 1
               System.out.println("Condition is true.");
          } // end block one
          else { // begin block 2
               System.out.println("Condition is false.");
          } // end block 2
     }
}
```

# Control Flow Statements

The statements inside your source files are generally executed from top to bottom, in the order that they appear. Control flow statements, however, break up the flow of execution by employing decision making, looping, and branching, enabling your program to conditionally execute particular blocks of code. This section describes the decision-making statements (if-then, if-then-else, switch), the looping statements (for, while, do-while), and the branching statements (break, continue, return) supported by the Java programming language.
