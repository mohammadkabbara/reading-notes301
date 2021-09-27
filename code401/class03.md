# Primitives vs. Objects

object contains a single value of the corresponding primitive type.

primitive type variables have the following impact on the memory:

boolean – 1 bit

byte – 8 bits

short, char – 16 bits

int, float – 32 bits

long, double – 64 bits

referance types like:

Boolean – 128 bits

Byte – 128 bits

Short, Character – 128 bits

Integer, Float – 128 bits

Long, Double – 192 bits

# Exceptions

What Is an Exception?

An exception is an event that occurs during the execution of a program that disrupts the normal flow of instructions.

How to Throw Exceptions

This section covers the throw statement and the Throwable class and its subclasses.

Unchecked Exceptions — The Controversy

This section explains the correct and incorrect use of the unchecked exceptions indicated by subclasses of RuntimeException.

Advantages of Exceptions

The use of exceptions to manage errors has some advantages over traditional error-management techniques. You'll learn more in this section.

# Scanning

Objects of type Scanner are useful for breaking down formatted input into tokens and translating individual tokens according to their data type.

**Breaking Input into Tokens**
By default, a scanner uses white space to separate tokens. (White space characters include blanks, tabs, and line terminators. For the full list, refer to the documentation for Character.isWhitespace.) To see how scanning works, let's look at ScanXan, a program that reads the individual words in xanadu.txt and prints them out, one per line.

```import java.io.*;
import java.util.Scanner;

public class ScanXan {
    public static void main(String[] args) throws IOException {

        Scanner s = null;

        try {
            s = new Scanner(new BufferedReader(new FileReader("xanadu.txt")));

            while (s.hasNext()) {
                System.out.println(s.next());
            }
        } finally {
            if (s != null) {
                s.close();
            }
        }
    }
}
```
