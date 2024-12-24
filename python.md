### **Python**

#### **Objective**:  
Master Python for problem-solving, automation, and building functional applications from beginner to intermediate level.

---

### **Step 1: Installation**
1. **Download Python**:  
   - Go to [python.org](https://www.python.org).  
   - Install the latest stable version. **During installation**, check the box for **"Add Python to PATH"**.

2. **Verify Installation**:  
   - Open your terminal (Command Prompt, PowerShell, or Bash).  
   - Run: `python --version` or `python3 --version`.

3. **Install Pip**:  
   - Pip is Python’s package manager, pre-installed in most Python distributions. Verify with: `pip --version`.  
   - Update pip: `pip install --upgrade pip`.

---

### **Step 2: Setup**
1. **Choose an IDE or Text Editor**:  
   - Recommended:  
     - **VS Code** (install Python extension).  
     - **PyCharm** (full IDE for Python).  
     - Built-in: Use Python’s `IDLE`.  

2. **Create a Project Environment**:  
   - Use virtual environments to avoid dependency conflicts.  
     - Create: `python -m venv venv_name`  
     - Activate:  
       - Windows: `venv_name\Scripts\activate`  
       - Linux/macOS: `source venv_name/bin/activate`  
     - Install libraries within the virtual environment: `pip install <library>`.

3. **Organize Files**:  
   - Use a clear folder structure:  
     ```
     project_name/
       ├── main.py
       ├── requirements.txt
       ├── venv/
       ├── scripts/
       └── data/
     ```

---

### **Step 3: Python Basics**
#### 1. **Core Syntax**:  
- **Hello World**:  
   ```python
   print("Hello, World!")
   ```
- **Variables**:  
   ```python
   name = "Commander"
   age = 25
   print(f"Name: {name}, Age: {age}")
   ```
- **Data Types**: Strings, Integers, Lists, Dictionaries, etc.  
   ```python
   numbers = [1, 2, 3]
   person = {"name": "John", "age": 30}
   ```

#### 2. **Conditionals**:  
   ```python
   age = 18
   if age >= 18:
       print("You are an adult.")
   else:
       print("You are a minor.")
   ```

#### 3. **Loops**:  
   ```python
   for i in range(1, 6):
       print(f"Number: {i}")

   count = 0
   while count < 5:
       print(count)
       count += 1
   ```

#### 4. **Functions**:  
   ```python
   def greet(name):
       return f"Hello, {name}!"
   print(greet("Commander"))
   ```

#### 5. **File I/O**:  
   ```python
   with open("example.txt", "w") as file:
       file.write("Hello, World!")

   with open("example.txt", "r") as file:
       print(file.read())
   ```

#### 6. **Modules and Libraries**:  
   ```python
   import math
   print(math.sqrt(16))
   ```

---

### **Step 4: Install Essential Libraries**
1. **Common Libraries**:  
   - `pip install` the following:  
     - **Requests**: API calls - `pip install requests`  
     - **Pandas**: Data handling - `pip install pandas`  
     - **Matplotlib**: Visualization - `pip install matplotlib`  
     - **Flask**: Web apps - `pip install flask`  
     - **OpenPyXL**: Excel automation - `pip install openpyxl`  

2. **Check Installed Libraries**:  
   ```bash
   pip freeze
   ```

---

### **Step 5: Projects (Beginner to Intermediate)**

#### **Project 1: Basic Calculator**  
**Purpose**: Perform basic math operations.  
**Code**:  
```python
def calculator():
    operation = input("Choose (+, -, *, /): ")
    num1 = float(input("Enter first number: "))
    num2 = float(input("Enter second number: "))

    if operation == "+":
        print(f"Result: {num1 + num2}")
    elif operation == "-":
        print(f"Result: {num1 - num2}")
    elif operation == "*":
        print(f"Result: {num1 * num2}")
    elif operation == "/":
        print(f"Result: {num1 / num2}")
    else:
        print("Invalid operation")

calculator()
```

---

#### **Project 2: Weather App (API Integration)**  
**Purpose**: Fetch live weather data using an API.  
**Steps**:  
1. Get an API key from [OpenWeatherMap](https://openweathermap.org/api).  
2. Install requests: `pip install requests`.  

**Code**:  
```python
import requests

def get_weather(city):
    api_key = "your_api_key_here"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        print(f"Weather in {city}: {data['main']['temp']}°C")
    else:
        print("City not found")

city = input("Enter city name: ")
get_weather(city)
```

---

#### **Project 3: To-Do List (CRUD Operations)**  
**Purpose**: Manage tasks.  
**Code**:  
```python
tasks = []

def add_task(task):
    tasks.append(task)
    print(f"Added: {task}")

def remove_task(task):
    tasks.remove(task)
    print(f"Removed: {task}")

def list_tasks():
    print("Tasks:")
    for i, task in enumerate(tasks):
        print(f"{i + 1}. {task}")

while True:
    print("\n1. Add Task\n2. Remove Task\n3. View Tasks\n4. Exit")
    choice = input("Choose an option: ")
    if choice == "1":
        task = input("Enter task: ")
        add_task(task)
    elif choice == "2":
        task = input("Enter task to remove: ")
        remove_task(task)
    elif choice == "3":
        list_tasks()
    elif choice == "4":
        break
    else:
        print("Invalid choice.")
```

---

#### **Project 4: Data Visualization with Matplotlib**  
**Purpose**: Create a graph from data.  
**Steps**:  
1. Install matplotlib: `pip install matplotlib`.  

**Code**:  
```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 20, 25, 30, 35]

plt.plot(x, y)
plt.title("Sample Graph")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")
plt.show()
```

---

#### **Project 5: File Encryption Tool**  
**Purpose**: Encrypt/decrypt text in files.  
**Steps**:  
1. Install cryptography: `pip install cryptography`.  

**Code**:  
```python
from cryptography.fernet import Fernet

# Generate and save a key
key = Fernet.generate_key()
with open("key.key", "wb") as key_file:
    key_file.write(key)

# Load the key
with open("key.key", "rb") as key_file:
    key = key_file.read()

cipher = Fernet(key)

# Encrypt
with open("data.txt", "rb") as file:
    data = file.read()
encrypted = cipher.encrypt(data)
with open("data.txt", "wb") as file:
    file.write(encrypted)

# Decrypt
with open("data.txt", "rb") as file:
    encrypted_data = file.read()
decrypted = cipher.decrypt(encrypted_data)
print(decrypted.decode())
```

---

### **Final Notes**  
1. **Keep Practicing**: Build larger projects like APIs, automation scripts, or small games.  
2. **Expand Knowledge**: Learn frameworks like Flask/Django (web dev) or Pandas/Numpy (data analysis).  
3. **Debugging Skills**: Learn to use `pdb` or VS Code’s debugger.  

This equips you with Python essentials for real-world applications. 
