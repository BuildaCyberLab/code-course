### **Assembly**

#### **Objective**:  
Master assembly language for low-level programming, understanding hardware operations, and creating efficient system-level applications.

---

### **Step 1: Installation**

1. **Install an Assembler**:  
   - **NASM (Netwide Assembler)**:  
     - Download from [nasm.us](https://nasm.us).  
     - Install and ensure the `nasm` command is added to your system PATH.  
   - **MASM (Microsoft Assembler)**:  
     - Comes with Visual Studio for Windows.  
   - **FASM (Flat Assembler)**:  
     - Lightweight option, available from [flatassembler.net](https://flatassembler.net).  

2. **Linker**:  
   - Use **GNU LD** (comes with GCC) or **GoLink** for Windows to convert `.obj` files into executables.  

3. **Verify Installation**:  
   - For NASM:  
     ```bash
     nasm -v
     ```

4. **Editor**:  
   - Use **Visual Studio Code** or **Sublime Text** for writing assembly code.

---

### **Step 2: Setup**

1. **File Structure**:  
   - Save assembly files with `.asm` extension.  

2. **Compile and Link**:  
   - **For NASM**:  
     ```bash
     nasm -f elf64 -o program.o program.asm    # Compile to object file
     ld -o program program.o                  # Link to create executable
     ./program                                # Run the executable
     ```

   - **For MASM (Windows)**:  
     ```cmd
     ml /c /coff program.asm                  # Compile to object file
     link /SUBSYSTEM:CONSOLE program.obj      # Link to create executable
     program.exe                              # Run the executable
     ```

---

### **Step 3: Assembly Basics**

#### 1. **Core Syntax**:
- **Hello World (Linux)**:  
   ```asm
   section .data
       msg db 'Hello, World!', 0Ah
       len equ $ - msg

   section .text
       global _start

   _start:
       mov rax, 1          ; syscall: write
       mov rdi, 1          ; file descriptor: stdout
       mov rsi, msg        ; address of string
       mov rdx, len        ; length of string
       syscall             ; call kernel

       mov rax, 60         ; syscall: exit
       xor rdi, rdi        ; exit code: 0
       syscall
   ```

#### 2. **Registers**:  
   - General Purpose: `rax`, `rbx`, `rcx`, `rdx`.  
   - Special Purpose: `rsp` (stack pointer), `rbp` (base pointer).  
   - Segment Registers: `cs`, `ds`, `ss`.  

---

#### 3. **Memory Operations**:  
- **Data Declaration**:  
   ```asm
   section .data
       number db 10         ; Define 8-bit data
       word dw 1000         ; Define 16-bit data
       dword dd 12345678h   ; Define 32-bit data
       qword dq 1234567890h ; Define 64-bit data
   ```

- **Load and Store**:  
   ```asm
   mov rax, [number]         ; Load value of "number" into rax
   mov [word], rax           ; Store rax into "word"
   ```

---

#### 4. **Arithmetic Operations**:  
   ```asm
   mov rax, 5
   add rax, 3                ; rax = rax + 3
   sub rax, 2                ; rax = rax - 2
   imul rbx, 4               ; Multiply rbx by 4
   idiv rcx                  ; Divide rax by rcx (result in rax, remainder in rdx)
   ```

---

#### 5. **Conditionals**:  
   ```asm
   mov rax, 10
   cmp rax, 5                ; Compare rax with 5
   jg greater                ; Jump to "greater" if rax > 5
   jl less                   ; Jump to "less" if rax < 5

   greater:
       mov rbx, 1
       jmp end

   less:
       mov rbx, 0

   end:
   ```

---

#### 6. **Loops**:  
   ```asm
   mov rcx, 5                ; Set counter
   loop_start:
       dec rcx               ; Decrement counter
       jnz loop_start        ; Repeat if counter != 0
   ```

---

#### 7. **Functions (Subroutines)**:  
   ```asm
   section .text
       global _start

   _start:
       call my_function
       mov rax, 60           ; Exit syscall
       xor rdi, rdi
       syscall

   my_function:
       mov rax, 42
       ret
   ```

---

### **Step 4: Projects (Beginner to Intermediate)**

#### **Project 1: Print String to Console (Linux)**  
**Purpose**: Display a string using system calls.  
**Code**:  
   ```asm
   section .data
       msg db "Hello, Assembly!", 0Ah
       len equ $ - msg

   section .text
       global _start

   _start:
       mov rax, 1            ; syscall: write
       mov rdi, 1            ; file descriptor: stdout
       mov rsi, msg          ; address of string
       mov rdx, len          ; length of string
       syscall               ; call kernel

       mov rax, 60           ; syscall: exit
       xor rdi, rdi          ; exit code: 0
       syscall
   ```

---

#### **Project 2: Basic Calculator**  
**Purpose**: Perform addition and subtraction.  
**Code**:  
   ```asm
   section .text
       global _start

   _start:
       mov rax, 10           ; First number
       add rax, 20           ; Add second number
       sub rax, 5            ; Subtract third number

       mov rdi, 60           ; Exit syscall
       syscall
   ```

---

#### **Project 3: Reverse a String**  
**Purpose**: Reverse a string in memory.  
**Code**:  
   ```asm
   section .data
       str db "Hello", 0

   section .text
       global _start

   _start:
       ; Write code to reverse string
       mov rdi, 60           ; Exit syscall
       syscall
   ```

---

#### **Project 4: File Reader**  
**Purpose**: Read a file and display its contents.  
**Code**:  
   ```asm
   section .text
       global _start

   _start:
       ; Open, read, and display file content
       mov rdi, 60           ; Exit syscall
       syscall
   ```

---

#### **Project 5: Memory Manipulation**  
**Purpose**: Copy data between memory locations.  
**Code**:  
   ```asm
   section .bss
       buffer resb 10

   section .text
       global _start

   _start:
       mov rsi, source
       mov rdi, buffer
       mov rcx, 10
       rep movsb              ; Copy 10 bytes from source to buffer
       mov rdi, 60
       syscall
   ```

---

### **Step 5: Advanced Concepts**

1. **Interrupts**:  
   - Trigger specific hardware/software actions:  
     ```asm
     int 0x80                ; Linux syscall interrupt
     ```

2. **Stack Operations**:  
   ```asm
   push rax                 ; Push value onto stack
   pop rbx                  ; Pop value from stack into rbx
   ```

3. **Linking with C**:  
   - Use assembly with C programs for performance-critical sections.  

4. **Optimization**:  
   - Optimize loops and memory operations for better performance.

---

### **Step 6: Debugging Tools**

1. **GDB (GNU Debugger)**:  
   - Run assembly programs step-by-step:  
     ```bash
     gdb ./program
     ```

2. **objdump**:  
   - Disassemble compiled programs:  
     ```bash
     objdump -d program
     ```

---

### **Final Notes**

1. **Understand Hardware**: Assembly teaches you how the CPU and memory interact.  
2. **Optimize for Performance**: Use assembly for tasks where speed and efficiency matter.  
3. **Practice on Real Projects**: Create small, functional utilities to deepen understanding.
