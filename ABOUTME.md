### **1. Scripting and Automation**
- **Install**: Use Bash (Linux/macOS) or Batch files (Windows). Pre-installed on most systems.  
- **Setup**: No extra setup needed; open terminal (Linux/macOS) or Command Prompt (Windows).  
- **Navigation Basics**:  
  - `ls` (list files), `cd` (change directory), `touch` (create file), `mkdir` (create folder).  
  - Windows equivalent: `dir`, `cd`, `type nul > file.txt`, `md`.  

**Projects**:  
1. Automate file renaming in a directory.  
2. Create a script to back up specific files to another folder.  
3. Write a script to schedule a system shutdown.  
4. Build a script to fetch and display system stats (CPU/memory).  
5. Create a multi-step task runner (e.g., install software, update packages).  

---

### **2. Python**
- **Install**: Download Python from [python.org](https://python.org). Add to PATH during install.  
- **Setup**: IDE (e.g., VS Code, PyCharm), or use a simple text editor + terminal.  
- **Basics**:  
  - Syntax: `print("Hello, World!")`, Variables: `x = 10`.  
  - Libraries: `pip install <library>`.  

**Projects**:  
1. Basic calculator.  
2. Weather app using an API (e.g., OpenWeather).  
3. To-do list app (CRUD operations).  
4. Data visualization with Matplotlib (simple charts).  
5. File encryption tool.  

---

### **3. JavaScript**
- **Install**: Pre-installed in browsers. For backend (Node.js): Download from [nodejs.org](https://nodejs.org).  
- **Setup**: Use a text editor (e.g., VS Code). Test in browser console or Node.js.  
- **Basics**:  
  - Syntax: `console.log("Hello, World!");`, Functions: `function add(a, b) { return a + b; }`.  
  - DOM Manipulation: `document.querySelector("#id").textContent = "Updated!"`.  

**Projects**:  
1. Countdown timer.  
2. Interactive to-do list.  
3. Weather dashboard (fetch API data).  
4. Create a quiz app.  
5. Build a basic web-based calculator.  

---

### **4. SQL**
- **Install**: MySQL/MariaDB (for beginners). Install from [mysql.com](https://mysql.com).  
- **Setup**: Use a GUI like MySQL Workbench or a terminal.  
- **Basics**:  
  - `CREATE DATABASE db_name;`, `CREATE TABLE table_name (...);`.  
  - `SELECT`, `INSERT`, `UPDATE`, `DELETE`.  

**Projects**:  
1. Create a user database (CRUD operations).  
2. Inventory management system.  
3. Library catalog search.  
4. Build an employee attendance tracker.  
5. Write a reporting dashboard (SQL + Python).  

---

### **5. PowerShell**
- **Install**: Pre-installed on Windows. For macOS/Linux, download [PowerShell](https://github.com/PowerShell/PowerShell).  
- **Setup**: Use PowerShell ISE or terminal.  
- **Basics**:  
  - `Get-Command`, `Get-Help`, `Write-Output "Hello, World!"`.  
  - Scripts: Save as `.ps1` file and execute using `.\script.ps1`.  

**Projects**:  
1. Automate folder creation and file sorting.  
2. Build a script to monitor system logs.  
3. Fetch installed software list.  
4. Script for scheduled backups.  
5. Automated email sender (SMTP setup).  

---

### **6. C++**
- **Install**: Install GCC (Linux), MinGW (Windows), or use IDEs like Visual Studio or CLion.  
- **Setup**: Configure compiler path (if using MinGW/terminal).  
- **Basics**:  
  - Syntax: `#include <iostream> int main() { std::cout << "Hello, World!"; return 0; }`.  
  - Compile and run: `g++ file.cpp -o output && ./output`.  

**Projects**:  
1. Simple calculator program.  
2. Bank account management system.  
3. Tic-Tac-Toe game.  
4. Text-based adventure game.  
5. File handling project (read/write files).  

---

### **7. Ruby**
- **Install**: Download from [ruby-lang.org](https://www.ruby-lang.org). Use `rbenv` or `rvm` for version management.  
- **Setup**: Run scripts with `ruby file.rb` in terminal.  
- **Basics**:  
  - Syntax: `puts "Hello, World!"`, Variables: `x = 10`.  
  - Gems: `gem install <gem_name>`.  

**Projects**:  
1. Basic calculator.  
2. Scraper for a website.  
3. Command-line to-do list app.  
4. Build a weather app using APIs.  
5. Create a text-based game.  

---

### **8. Java**
- **Install**: Download JDK from [oracle.com](https://oracle.com).  
- **Setup**: IDE (Eclipse/IntelliJ IDEA) or compile in terminal (`javac`).  
- **Basics**:  
  - Syntax: `public static void main(String[] args) { System.out.println("Hello, World!"); }`.  

**Projects**:  
1. Simple calculator app.  
2. Student grade management system.  
3. Library management system (CRUD).  
4. Banking system simulation.  
5. Create a text-based game.  

---

### **9. Assembly**
- **Install**: Use an assembler like NASM ([nasm.us](https://nasm.us)) or MASM.  
- **Setup**: Write `.asm` files, assemble with NASM, and link with a linker (e.g., LD).  
- **Basics**:  
  - Structure: Data, BSS, and Code sections.  
  - Example:  
    ```asm
    section .data
    msg db 'Hello, World!', 0
    section .text
    global _start
    _start:
        mov rax, 1
        mov rdi, 1
        mov rsi, msg
        mov rdx, 13
        syscall
        mov rax, 60
        xor rdi, rdi
        syscall
    ```  

**Projects**:  
1. Print "Hello, World!" to the console.  
2. Create a simple calculator.  
3. Program to reverse a string.  
4. Write a program to handle basic file I/O.  
5. Memory allocation and manipulation.  

---

### **10. Machine Code**
- **Install**: Use a hex editor or debugger (e.g., GDB, Radare2).  
- **Setup**: Write raw bytecode, debug in a low-level environment.  
- **Basics**:  
  - Understand opcodes and instructions specific to your CPU architecture (x86/x64, ARM).  

**Projects**:  
1. Write raw bytecode to display a message.  
2. Create a minimal bootloader.  
3. Develop a basic memory reader.  
4. Write machine code to blink LEDs on hardware (if applicable).  
5. Build a simple syscall handler.  

---

This is the **essential roadmap** to becoming proficient in each tool and language.
