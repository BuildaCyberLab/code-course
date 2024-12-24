### **PowerShell**

#### **Objective**:  
Master PowerShell to automate tasks, manage systems, and streamline workflows for Windows environments (and cross-platform systems with PowerShell Core).

---

### **Step 1: Installation**

1. **Windows**:  
   - PowerShell is pre-installed on Windows.  
   - To check the version:  
     ```powershell
     $PSVersionTable.PSVersion
     ```  
   - For the latest version, install **PowerShell Core** ([Download Here](https://github.com/PowerShell/PowerShell)).

2. **macOS/Linux**:  
   - Install PowerShell Core:  
     ```bash
     brew install --cask powershell     # macOS
     sudo apt-get install powershell    # Ubuntu
     ```
   - Run it with:  
     ```bash
     pwsh
     ```

---

### **Step 2: Setup**

1. **Editor/IDE**:  
   - Use **Windows PowerShell ISE** (default on Windows) or **Visual Studio Code** with the PowerShell extension.  

2. **Execution Policy**:  
   - Set up script execution permissions:  
     ```powershell
     Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
     ```

3. **File Structure**:  
   - Save scripts as `.ps1` files.  
   - Use a clear structure:  
     ```
     scripts/
       ├── backup.ps1
       ├── monitor.ps1
       └── utilities.ps1
     ```

4. **Run Scripts**:  
   - Execute a script:  
     ```powershell
     .\script.ps1
     ```

---

### **Step 3: PowerShell Basics**

#### 1. **Core Commands**:  
- **Get Help**:  
   ```powershell
   Get-Help <command> -Examples
   ```

- **List Files**:  
   ```powershell
   Get-ChildItem
   ```

- **Run a Command**:  
   ```powershell
   Write-Output "Hello, World!"
   ```

- **Variables**:  
   ```powershell
   $name = "Commander"
   $age = 30
   Write-Output "Name: $name, Age: $age"
   ```

#### 2. **Conditionals**:  
   ```powershell
   $age = 20
   if ($age -ge 18) {
       Write-Output "You are an adult."
   } else {
       Write-Output "You are a minor."
   }
   ```

#### 3. **Loops**:  
   ```powershell
   # For loop
   For ($i = 1; $i -le 5; $i++) {
       Write-Output "Number $i"
   }

   # While loop
   $count = 0
   While ($count -lt 5) {
       Write-Output "Count: $count"
       $count++
   }
   ```

#### 4. **Functions**:  
   ```powershell
   Function Greet {
       Param([string]$Name)
       Write-Output "Hello, $Name!"
   }
   Greet -Name "Commander"
   ```

#### 5. **Pipelines and Filters**:  
   ```powershell
   Get-Process | Where-Object {$_.CPU -gt 10} | Select-Object Name, CPU
   ```

#### 6. **File I/O**:  
   ```powershell
   # Write to a file
   "Hello, PowerShell!" | Out-File -FilePath "example.txt"

   # Read from a file
   Get-Content "example.txt"
   ```

---

### **Step 4: Useful PowerShell Cmdlets**

1. **System Info**:  
   ```powershell
   Get-ComputerInfo
   Get-Process
   ```

2. **User Management**:  
   ```powershell
   Get-LocalUser
   New-LocalUser -Name "TestUser" -Password (ConvertTo-SecureString "Password123" -AsPlainText -Force)
   ```

3. **Network Management**:  
   ```powershell
   Test-Connection google.com
   Get-NetIPAddress
   ```

4. **Task Automation**:  
   ```powershell
   Start-ScheduledTask -TaskName "MyTask"
   ```

---

### **Step 5: Projects (Beginner to Intermediate)**

#### **Project 1: Automated Folder Organizer**  
**Purpose**: Organize files into folders based on their extensions.  
**Code**:  
```powershell
$sourcePath = "C:\Downloads"
$destinationPath = "C:\Organized"

Get-ChildItem $sourcePath | ForEach-Object {
    $extension = $_.Extension
    $targetFolder = Join-Path $destinationPath $extension.TrimStart(".")
    If (!(Test-Path $targetFolder)) {
        New-Item -ItemType Directory -Path $targetFolder
    }
    Move-Item $_.FullName -Destination $targetFolder
}
Write-Output "Files organized successfully!"
```

---

#### **Project 2: System Backup Script**  
**Purpose**: Back up important files to a target location.  
**Code**:  
```powershell
$source = "C:\ImportantFiles"
$backup = "D:\Backups"

Copy-Item -Path $source -Destination $backup -Recurse
Write-Output "Backup complete!"
```

---

#### **Project 3: Network Monitor**  
**Purpose**: Monitor and log active network connections.  
**Code**:  
```powershell
$logFile = "C:\NetworkLogs.txt"

While ($true) {
    Get-NetTCPConnection | Select-Object LocalAddress, RemoteAddress, State | Out-File -Append -FilePath $logFile
    Start-Sleep -Seconds 60
}
```

---

#### **Project 4: User Account Audit**  
**Purpose**: List and export local user accounts with details.  
**Code**:  
```powershell
Get-LocalUser | Select-Object Name, Enabled, LastLogon | Export-Csv -Path "C:\UserAudit.csv" -NoTypeInformation
Write-Output "User audit exported to C:\UserAudit.csv"
```

---

#### **Project 5: System Resource Monitor**  
**Purpose**: Monitor CPU and memory usage and alert if thresholds are exceeded.  
**Code**:  
```powershell
$cpuThreshold = 80
$memoryThreshold = 80

While ($true) {
    $cpuUsage = (Get-Counter '\Processor(_Total)\% Processor Time').CounterSamples[0].CookedValue
    $memoryUsage = (Get-Counter '\Memory\% Committed Bytes In Use').CounterSamples[0].CookedValue

    If ($cpuUsage -gt $cpuThreshold) {
        Write-Warning "High CPU usage: $cpuUsage%"
    }

    If ($memoryUsage -gt $memoryThreshold) {
        Write-Warning "High memory usage: $memoryUsage%"
    }

    Start-Sleep -Seconds 30
}
```

---

### **Step 6: Advanced Concepts**

1. **Scheduled Tasks**:  
   Automate script execution at specific times.  
   ```powershell
   $action = New-ScheduledTaskAction -Execute "powershell.exe" -Argument "C:\Scripts\backup.ps1"
   $trigger = New-ScheduledTaskTrigger -Daily -At 3AM
   Register-ScheduledTask -TaskName "DailyBackup" -Action $action -Trigger $trigger
   ```

2. **PowerShell Remoting**:  
   Manage remote systems with `Enter-PSSession`:  
   ```powershell
   Enter-PSSession -ComputerName RemotePC -Credential (Get-Credential)
   ```

3. **Modules and Functions**:  
   Create reusable modules:  
   ```powershell
   Function Get-SystemInfo {
       Get-ComputerInfo
   }
   Export-ModuleMember -Function Get-SystemInfo
   ```

4. **Logging**:  
   Add logging to scripts for troubleshooting.  
   ```powershell
   Start-Transcript -Path "C:\Logs\log.txt" -Append
   ```

---

### **Final Notes**

1. PowerShell is essential for **automation** in IT administration.  
2. Focus on **real-world scripts** to simplify repetitive tasks.  
3. **Expand Knowledge**: Dive into DSC (Desired State Configuration), PowerShell for Azure, or Active Directory management.

Mastering PowerShell gives you total control over Windows systems and beyond. 
