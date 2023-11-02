## Lesson 1
In this course we will discuss the paradigm of OOP from 3 perspectives
    - The programmers perspective
    - The compilers perspective
    - The designers perspective

### Intro to C++
- C version of printing Hello World
```C
    #include<stdio.h>
    int main() {
        print("Hello World!\n")
        return 0;
    }
```
- Below is the respective C++ version for printing Hello World
```C++
    import <iostream>;
    using namespace std;
    int main() {
        cout << " Hello World!" << endl;
        return 0;
    }
```
- Note that main MUST return an int
    - void main() is illegal
- Return statement: returns status code to OS ($?)
- stdio, printf still available to C++
- referred C++ I/O header <iostream>
```c++
    std::cout << ... << ... << ... (... = data)
    std::endl = end of line + flush out buffer
```
- A buffer is a region of memory in which data is held while it is being moved from one place to another, once the output has enough characters, the program will output the buffered characters all at once
- stderrors are unbuffered (as when you have an error you want to know immediately), on the other hand stdout is buffered
- The act of outputing all buffered characters into a file is known as 'flushing'
- using namespace std lets you omit the std:: prefix
- I/O Operators 
    - << "put to" (output), >> "get from" (input)
    - cerr << x
    - cin >> x

Add 2 #'s
```C++
    import <iostream>
    using namespace std;
    int main() {
        int x, y:
        cin >> x >> y;
        cout << x + y << endl;
    }
```
- By default, cin skips leading whitespace (space, tab, newline)
- What an error occurs, e.g
    - input doesn't comntain an integer next
    - input too large/small to fit in a variable
    - out of input (EOF)
- Then the statement will fail
- If the read failed, cin.fail() will be true
- If EOF, cin.fail() and cin.eof() will both be true
- This whill only happen until the attempted read fails
- There is an implicit conversion from cin's type (istream) to bool
- Allows you to use cin as a condition (e.g whether or not an error has occured)
- cin converts to true, unless the stream has had a failure
- The following example below reads all ints from stdin + echo them, one per line, stdout, stop on bad input or eof
```c++
    int main() {
        int r;
        while (true) {
            cin >> r;
            if (cin.fail()) break;
            cout << r << endl;
        }
    }
```
- Note: >> is C's (and C++'s) right bitshift operator
- If a and b are ints, a >> b shifts a's bits to the right by 6 spots


# Intro to C++

```c++
// This is what you would do in C
#include <stdio.h>
void main() {
    printf("Hello world \n");
}

// This is what you do in C++
#include <iostream> // In C++20, we can also use import instead of include 
using namespace std;

int main () { // In C++, main must always return an int
    cout << "Hello World" << endl; // We can also do cout << "Hello world \n" ; (note the diff between endl and \n)
    return 0; // Note - IF WE DONT RETURN ANY INT, 0 IS ASSUMED
}

```
##### import iostream - Access to printing like cout, cin, endl
##### using namespace std - Allows us to write cout and endl instead of std::cout and std::endl
##### Cout - Prints to stdout (Standard output)
##### Endl - Endline

#### Compilation 
1. g++20h iostream - Compiles system headers
2. g++20m main.cc -o program_name (default is a.out for some reason)
Now you can do ./a.out and this will print hello world :D 

If we Do not want to use C++20 modules, we can run "g++20i main.cc -o program_name". We dont need to compile headers

# Input Output

3 streams - stdout, stdin, stderr (standard output, input, error)
stdin for reading input, err for printing error, out for output
```c++
#include <iostream> // In C++20, we can also use import instead of include 
using namespace std;

int main () { 
    int x, y;
    cout << "Give me 2 numbers " << endl; 
    cin >> x >> y; // Notice how cout has << and cin has >>
    cout << x << y << endl;
}

```
Bits that are used by cin - fail bit and eof (end of file) bit. When a read fails, fail bit is set to true. This is accessible
by calling **cin.fail()** which returns true if fail bit is true. If a read fails due to eof, **fail bit and eof bit are BOTH** set to true, the eof bit is accessible via - **cin.eof()**

```c++
#include <iostream>
using namespace std;
int main () {
    while (true) {
        int x; // Note that we can reinitialize the variable inside the loop :) 
        cin >> x; 
        if (cin.fail()) { // Checks for both eof and invalid input 
            break;
        }
        cout << x << endl;
    }
}
```

**NOTE - if (cin) is the same as if (!cin.fail()) ==> if (!cin) is the same as if (cin.fail())**

Random Info :-
>> operator is C's bitshift operator 
x >> 3 - shifts x's bits to the right by 3