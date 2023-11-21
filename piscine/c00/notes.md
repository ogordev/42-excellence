# function
In C, a function is a set of statements that perform a specific task. It is the basic building block of a C program, providing modularity and code reusability. Functions in C have the following key aspects:
Declaration: In a function declaration, the function name, its return type, and the number and type of its parameters are specified.
Definition: A function definition provides the actual body of the function.
Calling: Functions can be called multiple times, reducing the repetition of the same statements in a program and making the code more readable

Functions in C can be predefined, such as printf() and scanf(), or user-defined, created by the developer to increase the scope and functionality of the program. When defining a function, the general form in C programming language is:

return_type function_name(parameter list) {
    // body of the function
}

function
}

Functions in C are essential for enabling reusability, reducing redundancy, making code modular, providing abstraction functionality, and breaking an extensive program into smaller and simpler pieces

# calling a function

To call a function in C, you use the function name followed by the argument list in parentheses. Here's a simple example:

#include <stdio.h>

// Function that takes two parameters a and b as inputs and returns their sum
int sum(int a, int b) {
    return a + b;
}

// Driver code
int main() {
    // Calling sum function and storing its value in add variable
    int add = sum(10, 30);
    printf("Sum is: %d", add);
    return 0;
}

In this example, the sum function is called with the arguments 10 and 30. The function returns the sum of the two numbers, which is then printed in the main function
3
.
Functions in C are essential for dividing bigger problems into smaller, more manageable chunks of code, making it simpler to create and run programs. They enable reusability, reduce redundancy, make code modular, provide abstraction functionality, and break an extensive program into smaller and simpler pieces


# parameters 
In C, a parameter refers to a variable in a function declaration or definition, while an argument is the actual value passed to the function when it is called. Parameters act as placeholders to receive 
the arguments passed during a function call, and they are also known as formal parameters. On the other hand, arguments are the actual values supplied during the function call 
and are also called actual parameters. For example, in the function Mult(int a, int b), a and b are parameters, and when the function is called with Mult(num1, num2), num1 and num2 are the arguments

When a method is called, the data passed into the method's parameters are referred to as arguments. Therefore, a parameter is a variable in a method definition, while the arguments are the actual data passed into the method's parameters

In summary, a parameter is a variable in a function declaration or definition, while an argument is the actual value passed to the function when it is called.

