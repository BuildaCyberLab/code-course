### **JavaScript**

#### **Objective**:  
Master JavaScript (JS) for web development, APIs, and dynamic, interactive applications.

---

### **Step 1: Installation**

1. **In Browser**:  
   - JavaScript is built into browsers like Chrome, Edge, and Firefox. Open the developer tools (`Ctrl+Shift+I` or `Cmd+Option+I`) and go to the **Console** tab to execute JS.

2. **For Backend (Node.js)**:  
   - Install Node.js from [nodejs.org](https://nodejs.org).  
   - Verify:  
     ```bash
     node --version
     npm --version
     ```

---

### **Step 2: Setup**

1. **Tools**:  
   - Use **Visual Studio Code (VS Code)** as your editor.  
     - Install the **"JavaScript (ES6)" extension** for linting.  
   - Debug JS in the browser or using Node.js.

2. **File Structure**:  
   - Use `.js` files for your scripts.  
     ```
     project_name/
       ├── index.html
       ├── script.js
       ├── styles.css
       └── assets/
     ```

3. **Link JavaScript to HTML**:  
   - Add this in your HTML `<head>` or at the end of `<body>`:  
     ```html
     <script src="script.js"></script>
     ```

4. **Run JS Code**:  
   - **In Browser**: Write code in `script.js` and open `index.html`.  
   - **In Node.js**: Run `node script.js` from the terminal.

---

### **Step 3: JavaScript Basics**

#### 1. **Core Syntax**:  
- **Hello World**:  
   ```javascript
   console.log("Hello, World!");
   ```

- **Variables**:  
   ```javascript
   let name = "Commander";
   const age = 25; // Constant
   var rank = "General"; // Old syntax (use sparingly)
   ```

- **Data Types**:  
   - **String**: `"text"`, **Number**: `42`, **Boolean**: `true/false`, **Array**: `[1, 2, 3]`, **Object**: `{ key: value }`.  

- **Comments**:  
   ```javascript
   // Single-line
   /* Multi-line */
   ```

---

#### 2. **Conditionals**:  
   ```javascript
   let age = 18;
   if (age >= 18) {
       console.log("You are an adult.");
   } else {
       console.log("You are a minor.");
   }
   ```

---

#### 3. **Loops**:  
   ```javascript
   // For loop
   for (let i = 0; i < 5; i++) {
       console.log(i);
   }

   // While loop
   let count = 0;
   while (count < 5) {
       console.log(count);
       count++;
   }
   ```

---

#### 4. **Functions**:  
   ```javascript
   // Regular function
   function greet(name) {
       return `Hello, ${name}!`;
   }
   console.log(greet("Commander"));

   // Arrow function
   const add = (a, b) => a + b;
   console.log(add(5, 3));
   ```

---

#### 5. **DOM Manipulation** (Frontend):  
   ```javascript
   // Access and modify elements
   document.querySelector("h1").textContent = "Welcome!";
   document.querySelector("#button").addEventListener("click", () => {
       alert("Button clicked!");
   });
   ```

---

#### 6. **Fetch API (Async Calls)**:  
   ```javascript
   fetch("https://jsonplaceholder.typicode.com/posts")
       .then(response => response.json())
       .then(data => console.log(data))
       .catch(error => console.error(error));
   ```

---

#### 7. **Modules** (Node.js):  
   ```javascript
   // Export module
   const greet = (name) => `Hello, ${name}!`;
   module.exports = greet;

   // Import module
   const greet = require('./greet');
   console.log(greet("Commander"));
   ```

---

### **Step 4: Projects (Beginner to Intermediate)**

#### **Project 1: Countdown Timer**  
**Purpose**: Create a simple timer that counts down from a given time.  
**Code**:  
```javascript
function countdown(seconds) {
    let timer = setInterval(() => {
        if (seconds <= 0) {
            clearInterval(timer);
            console.log("Time's up!");
        } else {
            console.log(seconds);
            seconds--;
        }
    }, 1000);
}
countdown(10);
```

---

#### **Project 2: Interactive To-Do List**  
**Purpose**: Add, display, and remove tasks dynamically.  
**Code**:  
```html
<ul id="tasks"></ul>
<input id="taskInput" type="text" placeholder="New Task">
<button id="addTask">Add Task</button>

<script>
document.querySelector("#addTask").addEventListener("click", () => {
    const taskInput = document.querySelector("#taskInput");
    const taskList = document.querySelector("#tasks");

    if (taskInput.value.trim()) {
        const li = document.createElement("li");
        li.textContent = taskInput.value;
        taskList.appendChild(li);
        taskInput.value = "";

        // Remove task on click
        li.addEventListener("click", () => li.remove());
    }
});
</script>
```

---

#### **Project 3: Weather App**  
**Purpose**: Fetch weather data using an API.  
**Steps**:  
1. Get an API key from [OpenWeatherMap](https://openweathermap.org/api).  
2. Use the Fetch API for data retrieval.  

**Code**:  
```javascript
const apiKey = "your_api_key_here";
const city = "London";

fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`)
    .then(response => response.json())
    .then(data => console.log(`Weather: ${data.main.temp}°C`))
    .catch(error => console.error("Error fetching weather data:", error));
```

---

#### **Project 4: Quiz App**  
**Purpose**: Build a simple interactive quiz with multiple-choice questions.  
**Code**:  
```javascript
const quiz = [
    { question: "What is 2+2?", options: [2, 3, 4], answer: 4 },
    { question: "What is 5+3?", options: [7, 8, 9], answer: 8 },
];

let score = 0;

quiz.forEach((q, index) => {
    const userAnswer = parseInt(prompt(`${q.question}\n${q.options.join(", ")}`));
    if (userAnswer === q.answer) {
        score++;
    }
});

alert(`Your score: ${score}/${quiz.length}`);
```

---

#### **Project 5: Basic Calculator (Frontend)**  
**Purpose**: Perform math operations dynamically using HTML + JS.  
**Code**:  
```html
<input id="num1" type="number" placeholder="Number 1">
<input id="num2" type="number" placeholder="Number 2">
<select id="operation">
    <option value="+">+</option>
    <option value="-">-</option>
    <option value="*">*</option>
    <option value="/">/</option>
</select>
<button id="calculate">Calculate</button>
<p id="result"></p>

<script>
document.querySelector("#calculate").addEventListener("click", () => {
    const num1 = parseFloat(document.querySelector("#num1").value);
    const num2 = parseFloat(document.querySelector("#num2").value);
    const operation = document.querySelector("#operation").value;

    let result;
    switch (operation) {
        case "+": result = num1 + num2; break;
        case "-": result = num1 - num2; break;
        case "*": result = num1 * num2; break;
        case "/": result = num1 / num2; break;
        default: result = "Invalid Operation";
    }
    document.querySelector("#result").textContent = `Result: ${result}`;
});
</script>
```

---

### **Step 5: Advanced Concepts to Explore**
1. **Event Bubbling and Delegation**.  
2. **Async/Await** for better API handling.  
3. **Working with LocalStorage/SessionStorage**.  
4. **Introduction to Frameworks**: Learn React.js, Vue.js, or Angular.  

---

### **Final Notes**  
JavaScript is **the most versatile language**. Build websites, interactive UI, and even backend systems (with Node.js). Mastering the basics ensures you’re ready for any JS framework or library. Stick to real-world projects to reinforce skills. 
