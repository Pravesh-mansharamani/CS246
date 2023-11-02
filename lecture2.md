# More I/O stuff

We can also 
```c++
int i;
while (cin >> i) {
    cout << i << endl; 
}
```

Note - C++ allows multiple functions with the same name but different in the number and types of parameters (but doesnt care about return types - multiple functions of the same name could have the same return types)

```c++
// IO OVERLOADING :-
while (true) {
    if (!(cin >> i)) {
        break;
    }
    cout << i << endl; 
}

// EOF error :-
while (true) {
    if (!(cin >> i)) {
        if (cin.eof()) {
            break;
        }
        cin.clear(); // Clears the error flags and thus cin.fail() is set back to false
        cin.ignore(); // Removes the input contents that caused the read failure
    } else {
        cout << i << endl; 
    }
}

```

# Formatting

```c++
#include <iomanip> // Lets you format output - setw (set width), setfill, hex, dex, etc. (See cppreference.com)
```

eg - cout << hex << 95; // prints "5f" 

Note - State change via hex and dec affect global state. The change persists till you set it back
General rule - Undo changes to global state when done :) 

# Strings

In C, strings are FUCKING CANCER
In C++, you can use strings like you would in C... but dont do that... ever

```c++
#include <string>

using namespace std;

int main () {
    string string1; // strings are implemented as character arrays but memory management is handled for us (phew)
}

Ways to initialize strings :-
string s1;
string s2 = "Hello World";
string s3 {"Hello"};
s1 = s2 + s3;
s2[0] = 'a';
s1 += "cat";

string line;
while (getline(cin, line)) {
    // Do something
}

```

# File Streams

```c++
#include <fstream>

// std::ifstream (input file stream), stf::ofstream (output file stream) => Work like istream and ostream respectively

int main () {
    ifstream in {"input.txt"}; // opens input.txt in read mode
    string word;
    while (in >> word) {
        // Do something with the word
    }
} // in is destroyed and closes the file

```
There is also a stream which is a combo of string and io stream  - import <sstream> std::ostringstream