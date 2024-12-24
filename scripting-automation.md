### **Scripting and Automation (in Cybersecurity)**

#### **Objective**:  
Master scripting for repetitive tasks, system management, and process automation using shell scripts (Bash for Linux/macOS, Batch/PowerShell for Windows).  

---

### **Step 1: Installation**
- **Linux/macOS**:  
  - Pre-installed. No extra steps required.  
  - Verify: Open terminal and type `bash --version` (Bash) or `zsh --version` (Zsh, default on macOS).  

- **Windows**:  
  - Use **Command Prompt** (Batch) or install **PowerShell** (if not already installed).  
  - For Linux-like scripting, install **Git Bash** or enable Windows Subsystem for Linux (WSL).  
  - Verify: Open terminal and type `powershell` or `bash` (Git Bash).  

---

### **Step 2: Setup**
1. **Tools**:  
   - Use a basic text editor: Notepad (Windows), nano/vim (Linux), or Visual Studio Code for advanced use.  
   - Install **VS Code extensions**:  
     - Bash IDE or PowerShell for scripting highlights.  

2. **Execution Setup**:  
   - Make scripts executable:  
     - Linux/macOS: `chmod +x script.sh`  
     - Windows (PowerShell): `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`  

3. **File Structure**:  
   - Use clear folder structures: e.g., `/scripts` for all your scripts.  

---

### **Step 3: Navigation Basics**
Learn these core commands for all environments:  
1. **Change directory**:  
   - `cd /path/to/folder`  
2. **List contents**:  
   - `ls` (Linux/macOS), `dir` (Windows)  
3. **Create files**:  
   - `touch file.sh` (Linux/macOS), `type nul > file.bat` (Windows)  
4. **Create folders**:  
   - `mkdir folder_name`  
5. **Run scripts**:  
   - `./script.sh` (Linux/macOS), `script.bat` or `.\script.ps1` (Windows).  

---

### **Step 4: Basics of Scripting**
#### **Linux/macOS (Bash)**  
1. **Hello World**:  
   ```bash
   #!/bin/bash
   echo "Hello, World!"
   ```  

2. **Variables**:  
   ```bash
   name="Top Commander"
   echo "Welcome, $name"
   ```  

3. **Loops**:  
   ```bash
   for i in {1..5}; do
       echo "Number $i"
   done
   ```  

4. **If Statements**:  
   ```bash
   if [ -f "file.txt" ]; then
       echo "File exists."
   else
       echo "File not found."
   fi
   ```  

5. **Functions**:  
   ```bash
   greet() {
       echo "Hello, $1!"
   }
   greet "User"
   ```  

#### **Windows (Batch)**  
1. **Hello World**:  
   ```batch
   @echo off
   echo Hello, World!
   ```  

2. **Variables**:  
   ```batch
   @echo off
   set name=Top Commander
   echo Welcome, %name%
   ```  

3. **Loops**:  
   ```batch
   @echo off
   for /l %%i in (1,1,5) do echo Number %%i
   ```  

4. **If Statements**:  
   ```batch
   @echo off
   if exist file.txt (
       echo File exists.
   ) else (
       echo File not found.
   )
   ```  

5. **Functions (Subroutines)**:  
   ```batch
   @echo off
   call :greet User
   exit /b

   :greet
   echo Hello, %1!
   exit /b
   ```  

#### **Windows (PowerShell)**  
1. **Hello World**:  
   ```powershell
   Write-Output "Hello, World!"
   ```  

2. **Variables**:  
   ```powershell
   $name = "Top Commander"
   Write-Output "Welcome, $name"
   ```  

3. **Loops**:  
   ```powershell
   For ($i = 1; $i -le 5; $i++) {
       Write-Output "Number $i"
   }
   ```  

4. **If Statements**:  
   ```powershell
   If (Test-Path "file.txt") {
       Write-Output "File exists."
   } Else {
       Write-Output "File not found."
   }
   ```  

5. **Functions**:  
   ```powershell
   Function Greet {
       Param([string]$Name)
       Write-Output "Hello, $Name!"
   }
   Greet -Name "User"
   ```  

---

### **Step 5: Projects (Beginner to Intermediate)**  

#### **Project 1: File Renaming Script**
**Purpose**: Rename all files in a directory to include a timestamp.  
- **Linux/macOS** (Bash):  
   ```bash
   #!/bin/bash
   for file in *; do
       mv "$file" "$(date +%Y%m%d)_$file"
   done
   ```  

- **Windows** (PowerShell):  
   ```powershell
   Get-ChildItem * | Rename-Item -NewName { "$(Get-Date -Format yyyyMMdd)_$_" }
   ```  

---

#### **Project 2: Automated Backup Script**
**Purpose**: Copy files from one directory to a backup location.  
- **Linux/macOS**:  
   ```bash
   #!/bin/bash
   src="/path/to/source"
   dest="/path/to/backup"
   cp -r "$src" "$dest"
   echo "Backup complete!"
   ```  

- **Windows** (Batch):  
   ```batch
   xcopy C:\source C:\backup /E /I /Y
   echo Backup complete!
   ```  

---

#### **Project 3: System Stats Fetcher**
**Purpose**: Display basic CPU and memory stats.  
- **Linux/macOS**:  
   ```bash
   #!/bin/bash
   echo "CPU Usage:"
   top -b -n 1 | grep "Cpu(s)"
   echo "Memory Usage:"
   free -h
   ```  

- **Windows** (PowerShell):  
   ```powershell
   Get-Process | Sort-Object CPU -Descending | Select-Object -First 5
   Get-WmiObject Win32_OperatingSystem | Select-Object TotalVisibleMemorySize,FreePhysicalMemory
   ```  

---

#### **Project 4: Cleanup Script**
**Purpose**: Delete all temporary or unused files.  
- **Linux/macOS**:  
   ```bash
   #!/bin/bash
   find /tmp -type f -mtime +7 -delete
   echo "Old temp files deleted."
   ```  

- **Windows** (Batch):  
   ```batch
   del /q /s C:\Temp\*.*
   echo Temp files deleted.
   ```  

---

#### **Project 5: Scheduled Shutdown**
**Purpose**: Automate shutting down the system after a delay.  
- **Linux/macOS**:  
   ```bash
   #!/bin/bash
   echo "System will shut down in 1 hour."
   sudo shutdown -h +60
   ```  

- **Windows** (Batch):  
   ```batch
   shutdown /s /t 3600
   echo System will shut down in 1 hour.
   ```  

---

### **Final Notes**  
Master these scripts by practicing and tweaking them for real-world tasks. Automation saves time and avoids human error. Expand gradually into tools like **Ansible** or **Python** for more complex scripting automation.
