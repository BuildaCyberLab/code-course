### **C++**

#### **Objective**:  
Master C++ for system-level programming, performance-critical applications, and learning core programming concepts.

---

### **Step 1: Installation**

1. **Install a Compiler**:  
   - **Windows**:  
     - Install **MinGW** from [mingw-w64.org](https://mingw-w64.org). Ensure `g++` is added to the system PATH.  
     - Verify:  
       ```bash
       g++ --version
       ```

   - **Linux**:  
     - Install GCC (includes g++):  
       ```bash
       sudo apt-get install build-essential
       ```

   - **macOS**:  
     - Install Xcode Command Line Tools:  
       ```bash
       xcode-select --install
       ```

2. **Use an IDE**:  
   - Recommended IDEs:  
     - **Visual Studio Code** (with C++ extension).  
     - **CLion** (JetBrains).  
     - **Code::Blocks**.  

---

### **Step 2: Setup**

1. **Create a C++ File**:  
   - Save code in `.cpp` files. Example: `main.cpp`.

2. **Compile and Run**:  
   - Compile:  
     ```bash
     g++ main.cpp -o program
     ```  
   - Run:  
     ```bash
     ./program
     ```

3. **File Structure**:  
   - Use a structured project layout:  
     ```
     project_name/
       ├── src/
       │   └── main.cpp
       ├── include/
       ├── build/
       └── README.md
     ```

---

### **Step 3: C++ Basics**

#### 1. **Core Syntax**:  
- **Hello World**:  
   ```cpp
   #include <iostream>
   using namespace std;

   int main() {
       cout << "Hello, World!" << endl;
       return 0;
   }
   ```

- **Variables**:  
   ```cpp
   int age = 25;
   double pi = 3.14;
   string name = "Commander";
   ```

---

#### 2. **Conditionals**:  
   ```cpp
   int age = 18;
   if (age >= 18) {
       cout << "You are an adult." << endl;
   } else {
       cout << "You are a minor." << endl;
   }
   ```

---

#### 3. **Loops**:  
   ```cpp
   // For loop
   for (int i = 0; i < 5; i++) {
       cout << "Count: " << i << endl;
   }

   // While loop
   int count = 0;
   while (count < 5) {
       cout << "Count: " << count << endl;
       count++;
   }
   ```

---

#### 4. **Functions**:  
   ```cpp
   int add(int a, int b) {
       return a + b;
   }

   int main() {
       int result = add(3, 5);
       cout << "Sum: " << result << endl;
       return 0;
   }
   ```

---

#### 5. **Pointers**:  
   ```cpp
   int num = 10;
   int* ptr = &num;

   cout << "Value: " << num << endl;
   cout << "Address: " << ptr << endl;
   cout << "Value via Pointer: " << *ptr << endl;
   ```

---

#### 6. **Object-Oriented Programming (OOP)**:  

1. **Classes and Objects**:  
   ```cpp
   class Person {
   public:
       string name;
       int age;

       void introduce() {
           cout << "Name: " << name << ", Age: " << age << endl;
       }
   };

   int main() {
       Person p1;
       p1.name = "Commander";
       p1.age = 30;
       p1.introduce();
       return 0;
   }
   ```

2. **Constructors**:  
   ```cpp
   class Person {
   public:
       string name;
       int age;

       Person(string n, int a) {
           name = n;
           age = a;
       }

       void introduce() {
           cout << "Name: " << name << ", Age: " << age << endl;
       }
   };

   int main() {
       Person p1("Commander", 30);
       p1.introduce();
       return 0;
   }
   ```

---

#### 7. **File I/O**:  
   ```cpp
   #include <fstream>
   using namespace std;

   int main() {
       ofstream outFile("example.txt");
       outFile << "Hello, File!" << endl;
       outFile.close();

       ifstream inFile("example.txt");
       string line;
       while (getline(inFile, line)) {
           cout << line << endl;
       }
       inFile.close();
       return 0;
   }
   ```

---

### **Step 4: Projects (Beginner to Intermediate)**

#### **Project 1: Simple Calculator**  
**Purpose**: Perform basic math operations.  
**Code**:  
```cpp
#include <iostream>
using namespace std;

int main() {
    char op;
    double num1, num2;

    cout << "Enter operator (+, -, *, /): ";
    cin >> op;
    cout << "Enter two numbers: ";
    cin >> num1 >> num2;

    switch (op) {
        case '+': cout << "Result: " << num1 + num2 << endl; break;
        case '-': cout << "Result: " << num1 - num2 << endl; break;
        case '*': cout << "Result: " << num1 * num2 << endl; break;
        case '/': cout << "Result: " << num1 / num2 << endl; break;
        default: cout << "Invalid operator!" << endl;
    }
    return 0;
}
```

---

#### **Project 2: Bank Account Manager**  
**Purpose**: Simulate a simple bank account system.  
**Code**:  
```cpp
#include <iostream>
using namespace std;

class BankAccount {
private:
    double balance;

public:
    BankAccount() {
        balance = 0;
    }

    void deposit(double amount) {
        balance += amount;
        cout << "Deposited: " << amount << endl;
    }

    void withdraw(double amount) {
        if (amount > balance) {
            cout << "Insufficient balance!" << endl;
        } else {
            balance -= amount;
            cout << "Withdrawn: " << amount << endl;
        }
    }

    void checkBalance() {
        cout << "Balance: " << balance << endl;
    }
};

int main() {
    BankAccount account;
    account.deposit(500);
    account.withdraw(200);
    account.checkBalance();
    return 0;
}
```

---

#### **Project 3: Tic-Tac-Toe Game**  
**Purpose**: Play a simple 2-player game.  
**Steps**: Write a grid, validate moves, and determine a winner.  
**Code**: Build it step-by-step (too large to paste here in full).

---

#### **Project 4: File Encryption Tool**  
**Purpose**: Encrypt and decrypt text files using basic substitution.  
**Code**:  
```cpp
#include <iostream>
#include <fstream>
using namespace std;

void encrypt(string inputFile, string outputFile) {
    ifstream in(inputFile);
    ofstream out(outputFile);

    char ch;
    while (in.get(ch)) {
        out.put(ch + 3); // Caesar cipher encryption
    }

    in.close();
    out.close();
    cout << "File encrypted!" << endl;
}

void decrypt(string inputFile, string outputFile) {
    ifstream in(inputFile);
    ofstream out(outputFile);

    char ch;
    while (in.get(ch)) {
        out.put(ch - 3); // Reverse Caesar cipher
    }

    in.close();
    out.close();
    cout << "File decrypted!" << endl;
}

int main() {
    encrypt("plain.txt", "encrypted.txt");
    decrypt("encrypted.txt", "decrypted.txt");
    return 0;
}
```

---

#### **Project 5: Student Management System**  
**Purpose**: Add, display, and manage student records.  
**Code**:  
```cpp
#include <iostream>
#include <vector>
using namespace std;

class Student {
public:
    string name;
    int age;
    double grade;

    Student(string n, int a, double g) : name(n), age(a), grade(g) {}
};

int main() {
    vector<Student> students;

    students.push_back(Student("John", 20, 3.5));
    students.push_back(Student("Jane", 22, 3.8));

    for (auto &student : students) {
        cout << "Name: " << student.name << ", Age: " << student.age << ", Grade: " << student.grade << endl;
    }
    return 0;
}
```

---

### **Final Notes**

1. **Focus on Mastery**: Learn debugging, memory management (pointers), and advanced concepts (STL, templates).  
2. **Expand Skills**: Dive into file handling, multithreading, and networking.  
3. **Practice Projects**: Build games, simulations, and command-line tools.  

C++ is **high-performance**, versatile, and essential for system-level programming. Master the basics, then tackle larger projects. 
