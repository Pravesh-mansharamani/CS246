## Command Line Arguments

```bash 
./program abs 123
```
To access these args,
Int main (int argc, char* argv[])
Int argc – the number of arguments given to the program (including the program name)
Argv – Array of char*s i.e – C sdstyle string
In this case, argv[0] = name of program, argv[1] = abc, argv[2] = 123
NOTE – argv[argc] = THE NULL POINTER

```c++ 
if (argv[1] == “abc”) {
} // THIS IS WRONG
```
This is comparing pointer locations rather than strings content.

Thus, we need to convert the args to std::String before use
```c++ 
Int main(int argc, char*argv[]) {
    for (int I = 0; I &lt; argc; i++) {
        string arg = argv[i];
        if (arg == “abc”) { } //THIS WORKS
    }
}
```

Example – Add all integers given as args on the command line 


```c++
Int main (int argc, char*argv[]) {
    int sum = 0;
    for (int i = 0; I &lt; argc; I++) {
        String arg = argv[i];
        int num;
        if (istringstream, iss{arg}, iss &gt;&gt; n) {
            sum += num;
        }
    }
cout &lt;&lt; sum &lt;&lt; endl;
}
```

# Defualt Function Parameters

```c++
void printSuiteFile (string fileName = "suite.txt") {
    ifstream file {fileName};
    string line;
    while (getline(file,line)) {
        cout << line << endl;
    }
}

PrintSuiteFile("abc.txt") -> read from abc.txt
PrintSuiteFile() -> read from suite.txt

Note - Optional Parameters must be last


void f (int x, String s = "hello")
int main () {
    f(5);
}
```
## The defualt function f doesnt know what will be passed in it cannot determine the difference between uninitialized memoryu and other strings. Caller of f must provide all arguments to f in advance

#### Default params are part of the declaration and not the definition

```c++
In C++:
int neg(int x) {return -x;}
bool neg(bool x) {return !x;}

Compiler chooses which overload of the function to use based on the # and types of arguments at compile time 
in this case, neg(5) -> -5, neg(true) -> false

```

# Structs

Structs exist in C++ just like they did in C :)

### Linked list node
```c++
IN C

struct Node{
    int data;
    Node* next;
};

int main () {
    struct Node node1{some_data, some_pointer}
    print node1.data
}

We have to use the word struct everywhere

IN C++, We can just omit the struct

int main () {
    Node node1{some_data, some_pointer}
}
```

# Structs

Structs exist in C++ just like they did in C :)

### Linked list node
```c++
IN C

struct Node{
    int data;
    Node* next;
};

int main () {
    struct Node node1{some_data, some_pointer}
    print node1.data
}

We have to use the word struct everywhere

IN C++, We can just omit the struct

int main () {
    Node node1{some_data, some_pointer}
}
```

# Constants

```c++
const int max_grade = 100;

Any attempt to modify this variable will not compile

const Node n {5, nullptr}
n's data cant be changed and n's next field cannot be changed

In C, The null pointer is indicated by NULL or 0
This is because there is a line imported via a library - #define NULL 0 which replaces all instances of NULL with 0
```
**DONT DO THIS IN C++**

```c++
void f(int x);
void f(Node* p);

f(NULL) - THIS WILL CALL THE int VERSION of f instead of the pointer version
nullptr is a special type that can be automatically converted to any other pointer type

thus, f(nullptr) will call the ptr version of f :) 
```

# Parameter Passing

```c++
void inc(int x ) { ++x; }
int main() {
    int x = 5;
    inc(x); //in this case we have not changed the value of x cause this is now how you do that 
    cout << x << endl; // This prints 5 and NOT 6
    //this is also known as pass by value semantics
}

void inc(int* p) {
    ++*p;
}
int main() {
    int x = 5;
    inc(&x);
    cout << x << endl; // This will print 6 

}

```

