### **Machine Code**

#### **Objective**:  
Understand machine code fundamentals, write low-level programs directly in binary or hexadecimal, and manipulate systems at the hardware level.

---

### **Step 1: What is Machine Code?**

1. **Definition**:  
   - Machine code is the binary representation of instructions executed directly by the CPU.  
   - It is architecture-specific (e.g., x86, ARM, RISC-V).

2. **Why Learn Machine Code?**  
   - To understand how CPUs execute instructions.  
   - To optimize performance-critical sections of code.  
   - To debug programs and analyze malware or firmware.  

3. **Example**:  
   - Assembly Instruction: `mov eax, 1`  
   - Machine Code (x86): `B8 01 00 00 00`  

---

### **Step 2: Setup**

1. **Tools Required**:  
   - **Hex Editor**: For viewing/editing binary files (e.g., HxD for Windows, HexFiend for macOS).  
   - **Assembler**: NASM or FASM to convert assembly to machine code.  
   - **Debugger**: GDB (Linux), x64dbg (Windows).  
   - **Emulator**: QEMU or Bochs for testing machine code in a controlled environment.  

2. **File Structure**:  
   - Use `.bin` for raw binary files.  
   - Save instructions as a binary or hexadecimal representation.

---

### **Step 3: Basic Concepts**

#### 1. **Instruction Format**:  
   - **Opcode**: Specifies the operation (e.g., `B8` for `mov eax`).  
   - **Operands**: Specify registers, memory, or constants (e.g., `01 00 00 00` for the immediate value `1`).  

---

#### 2. **CPU Registers (x86)**:  
   - General Purpose: `EAX`, `EBX`, `ECX`, `EDX`.  
   - Special Purpose: `ESP` (Stack Pointer), `EBP` (Base Pointer), `EIP` (Instruction Pointer).  

---

#### 3. **Memory Layout**:  
   - Machine code interacts with memory directly using addresses.  
   - Example: `A3 00 10 00 00` stores the value in `EAX` at memory address `0x00100000`.

---

#### 4. **Execution**:  
   - The CPU fetches, decodes, and executes machine instructions in a cycle.  

---

### **Step 4: Writing Machine Code**

1. **Basic Program (x86)**:  
   - **Purpose**: Write `1` to `EAX`.  

   **Machine Code (Hexadecimal)**:  
   ```
   B8 01 00 00 00   ; mov eax, 1
   C3                ; ret (return)
   ```

   **Steps to Create and Run**:  
   1. Save as `program.bin` using a hex editor.  
   2. Load into a debugger or emulator:  
      ```bash
      qemu-system-i386 -hda program.bin
      ```

---

2. **Hello World (Linux Syscall)**:  
   - **Purpose**: Print a message using Linux system calls.  

   **Machine Code (Hexadecimal)**:  
   ```
   B8 04 00 00 00   ; mov eax, 4 (syscall: write)
   BB 01 00 00 00   ; mov ebx, 1 (file descriptor: stdout)
   B9 10 00 00 00   ; mov ecx, 0x0010 (address of message)
   BA 0E 00 00 00   ; mov edx, 14 (length of message)
   CD 80            ; int 0x80 (call kernel)
   B8 01 00 00 00   ; mov eax, 1 (syscall: exit)
   CD 80            ; int 0x80
   ```

   **Steps**:  
   1. Assemble or write raw binary using a hex editor.  
   2. Test in an emulator or Linux environment.  

---

3. **Arithmetic Operations**:  
   - **Purpose**: Add `5` and `3`, store result in `EAX`.  

   **Machine Code (Hexadecimal)**:  
   ```
   B8 05 00 00 00   ; mov eax, 5
   05 03 00 00 00   ; add eax, 3
   C3                ; ret
   ```

---

### **Step 5: Projects (Beginner to Intermediate)**

#### **Project 1: Minimal Bootloader**  
**Purpose**: Write a bootloader that prints "OK" on the screen.  

**Steps**:  
1. **Machine Code**:  
   ```asm
   B4 0E              ; mov ah, 0Eh (BIOS Teletype Output)
   B0 4F              ; mov al, 'O'
   CD 10              ; int 10h (BIOS interrupt)
   B0 4B              ; mov al, 'K'
   CD 10              ; int 10h
   F4                 ; hlt
   ```

2. **Save as `boot.bin`** using a hex editor.  

3. **Test**:  
   ```bash
   qemu-system-x86_64 -drive format=raw,file=boot.bin
   ```

---

#### **Project 2: Memory Copy**  
**Purpose**: Copy 16 bytes from one memory location to another.  

**Machine Code (Hexadecimal)**:  
```
8B 0E             ; mov ecx, [esi] (copy value at source to ecx)
89 0F             ; mov [edi], ecx (write value at destination)
F3 A4             ; rep movsb (copy 16 bytes)
```

---

#### **Project 3: XOR Encryption**  
**Purpose**: Encrypt a string in memory using XOR.  

**Machine Code (Hexadecimal)**:  
```
30 1C 07          ; xor [edi], bl (encrypt one byte)
47                 ; inc edi
E2 FA             ; loop (repeat for all bytes)
```

---

#### **Project 4: System Call Table**  
**Purpose**: Explore syscall table by executing direct syscalls.  

**Example**: Invoke `exit` syscall in Linux.  
```
B8 01 00 00 00    ; mov eax, 1 (syscall: exit)
31 DB             ; xor ebx, ebx (exit code: 0)
CD 80             ; int 0x80
```

---

#### **Project 5: Fibonacci Sequence**  
**Purpose**: Generate Fibonacci numbers in machine code.  

**Machine Code (Hexadecimal)**:  
```
8B 44 24 04       ; mov eax, [esp+4] (first input)
8B 4C 24 08       ; mov ecx, [esp+8] (second input)
01 C1             ; add ecx, eax
89 4C 24 0C       ; mov [esp+12], ecx (store result)
C3                ; ret
```

---

### **Step 6: Debugging and Testing**

1. **GDB (GNU Debugger)**:  
   - Load and step through machine code:  
     ```bash
     gdb program
     break *0x08048000
     run
     ```

2. **Emulators**:  
   - Use **QEMU** or **Bochs** to test machine code in a virtual environment.  

3. **Hex Editors**:  
   - Edit raw binaries for testing and refinement.

---

### **Step 7: Advanced Topics**

1. **Interrupts**:  
   - Use software (`int`) and hardware interrupts for I/O and system calls.  
   - Example: `int 0x80` for Linux system calls.  

2. **Stack Management**:  
   - Push and pop values to manage function calls.  
   ```asm
   50       ; push eax
   58       ; pop eax
   ```

3. **Optimization**:  
   - Minimize instruction count for performance.  

4. **Reverse Engineering**:  
   - Analyze compiled programs to understand their behavior.  

---

### **Final Notes**

1. Machine code is **CPU-specific**—know your target architecture (e.g., x86, ARM).  
2. **Start Simple**: Write small programs like string manipulations or arithmetic operations.  
3. **Practice on Real Hardware**: Use emulators or low-cost development boards. 
