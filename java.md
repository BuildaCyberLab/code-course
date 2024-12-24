### **Java**

#### **Objective**:  
Master Java for application development, object-oriented programming, and building robust, scalable applications.

---

### **Step 1: Installation**

1. **Install the Java Development Kit (JDK)**:  
   - Download the latest JDK from [oracle.com](https://www.oracle.com/java/technologies/javase-downloads.html) or use OpenJDK ([openjdk.org](https://openjdk.org)).  
   - Install and ensure the `java` and `javac` commands are added to your system PATH.  

2. **Verify Installation**:  
   - Open a terminal or command prompt:  
     ```bash
     java --version
     javac --version
     ```

---

### **Step 2: Setup**

1. **Editor/IDE**:  
   - Recommended IDEs:  
     - **IntelliJ IDEA** (Best for Java).  
     - **Eclipse**.  
     - **VS Code** (with Java extensions).

2. **File Structure**:  
   - Organize Java files in directories matching the package names:  
     ```
     project_name/
       ├── src/
       │   └── com/
       │       └── example/
       │           └── Main.java
       ├── bin/ (compiled files)
       └── README.md
     ```

3. **Compile and Run**:  
   - Compile a `.java` file:  
     ```bash
     javac Main.java
     ```  
   - Run the compiled program:  
     ```bash
     java Main
     ```

---

### **Step 3: Java Basics**

#### 1. **Core Syntax**:  
- **Hello World**:  
   ```java
   public class Main {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }
   ```

- **Variables**:  
   ```java
   int age = 25;
   double pi = 3.14;
   String name = "Commander";
   boolean isAdmin = true;
   ```

---

#### 2. **Conditionals**:  
   ```java
   int age = 18;
   if (age >= 18) {
       System.out.println("You are an adult.");
   } else {
       System.out.println("You are a minor.");
   }
   ```

---

#### 3. **Loops**:  
   ```java
   // For loop
   for (int i = 0; i < 5; i++) {
       System.out.println("Count: " + i);
   }

   // While loop
   int count = 0;
   while (count < 5) {
       System.out.println("Count: " + count);
       count++;
   }
   ```

---

#### 4. **Methods (Functions)**:  
   ```java
   public class Main {
       public static int add(int a, int b) {
           return a + b;
       }

       public static void main(String[] args) {
           int result = add(3, 5);
           System.out.println("Sum: " + result);
       }
   }
   ```

---

#### 5. **Object-Oriented Programming (OOP)**:

1. **Classes and Objects**:  
   ```java
   public class Person {
       String name;
       int age;

       public Person(String name, int age) {
           this.name = name;
           this.age = age;
       }

       public void introduce() {
           System.out.println("Name: " + name + ", Age: " + age);
       }
   }

   public class Main {
       public static void main(String[] args) {
           Person p1 = new Person("Commander", 30);
           p1.introduce();
       }
   }
   ```

2. **Inheritance**:  
   ```java
   class Animal {
       public void speak() {
           System.out.println("I am an animal.");
       }
   }

   class Dog extends Animal {
       public void speak() {
           System.out.println("Woof!");
       }
   }

   public class Main {
       public static void main(String[] args) {
           Dog dog = new Dog();
           dog.speak();
       }
   }
   ```

---

#### 6. **File I/O**:  
   ```java
   import java.io.*;

   public class Main {
       public static void main(String[] args) {
           try {
               // Write to a file
               FileWriter writer = new FileWriter("example.txt");
               writer.write("Hello, File!");
               writer.close();

               // Read from a file
               BufferedReader reader = new BufferedReader(new FileReader("example.txt"));
               String line;
               while ((line = reader.readLine()) != null) {
                   System.out.println(line);
               }
               reader.close();
           } catch (IOException e) {
               e.printStackTrace();
           }
       }
   }
   ```

---

### **Step 4: Projects (Beginner to Intermediate)**

#### **Project 1: Basic Calculator**  
**Purpose**: Perform basic math operations.  
**Code**:  
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter first number:");
        double num1 = scanner.nextDouble();

        System.out.println("Enter operator (+, -, *, /):");
        char operator = scanner.next().charAt(0);

        System.out.println("Enter second number:");
        double num2 = scanner.nextDouble();

        double result;
        switch (operator) {
            case '+': result = num1 + num2; break;
            case '-': result = num1 - num2; break;
            case '*': result = num1 * num2; break;
            case '/': result = num1 / num2; break;
            default: result = 0; System.out.println("Invalid operator!"); break;
        }

        System.out.println("Result: " + result);
    }
}
```

---

#### **Project 2: Student Management System**  
**Purpose**: Add, view, and manage student records.  
**Code**:  
```java
import java.util.ArrayList;

class Student {
    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void display() {
        System.out.println("Name: " + name + ", Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        ArrayList<Student> students = new ArrayList<>();

        students.add(new Student("John", 20));
        students.add(new Student("Jane", 22));

        for (Student s : students) {
            s.display();
        }
    }
}
```

---

#### **Project 3: File Encryption Tool**  
**Purpose**: Encrypt and decrypt text files.  
**Code**:  
```java
import java.io.*;

public class Main {
    public static void main(String[] args) throws IOException {
        String key = "mysecretkey";

        // Encrypt
        String text = "Hello, File!";
        String encrypted = encrypt(text, key);
        FileWriter writer = new FileWriter("encrypted.txt");
        writer.write(encrypted);
        writer.close();

        // Decrypt
        BufferedReader reader = new BufferedReader(new FileReader("encrypted.txt"));
        String encryptedText = reader.readLine();
        String decrypted = decrypt(encryptedText, key);
        System.out.println("Decrypted: " + decrypted);
    }

    public static String encrypt(String text, String key) {
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < text.length(); i++) {
            result.append((char) (text.charAt(i) + key.length()));
        }
        return result.toString();
    }

    public static String decrypt(String text, String key) {
        StringBuilder result = new StringBuilder();
        for (int i = 0; i < text.length(); i++) {
            result.append((char) (text.charAt(i) - key.length()));
        }
        return result.toString();
    }
}
```

---

#### **Project 4: Bank Account Manager**  
**Purpose**: Manage deposits, withdrawals, and balances.  
**Code**:  
```java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: $" + amount);
    }

    public void withdraw(double amount) {
        if (amount > balance) {
            System.out.println("Insufficient funds.");
        } else {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount);
        }
    }

    public void displayBalance() {
        System.out.println("Balance: $" + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        account.deposit(500);
        account.withdraw(200);
        account.displayBalance();
    }
}
```

---

#### **Project 5: Weather App (API Integration)**  
**Purpose**: Fetch weather data from an API.  
**Steps**: Use libraries like `HttpURLConnection` or a third-party library like **OkHttp**.  

---

### **Step 5: Advanced Concepts**

1. **Collections Framework**: Master `ArrayList`, `HashMap`, `Set`, etc.  
   ```java
   ArrayList<String> names = new ArrayList<>();
   names.add("John");
   System.out.println(names.get(0));
   ```

2. **Multithreading**: Learn how to create threads for concurrent tasks.  
   ```java
   class MyThread extends Thread {
       public void run() {
           System.out.println("Thread is running.");
       }
   }

   public class Main {
       public static void main(String[] args) {
           MyThread t = new MyThread();
           t.start();
       }
   }
   ```

3. **Java Frameworks**: Dive into **Spring Boot** for web applications or **Hibernate** for database management.  

---

### **Final Notes**

1. Master Java for its versatility in web, mobile, and enterprise applications.  
2. Focus on OOP principles and practice with real-world projects.  
3. Expand into advanced concepts like **data structures**, **concurrency**, and **frameworks**
