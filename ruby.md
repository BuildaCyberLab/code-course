### **Ruby**

#### **Objective**:  
Master Ruby for web development, scripting, and object-oriented programming. Learn how to build dynamic, real-world applications.

---

### **Step 1: Installation**

1. **Install Ruby**:  
   - **Windows**:  
     - Use the RubyInstaller: [rubyinstaller.org](https://rubyinstaller.org).  
     - Add Ruby to the system PATH during installation.  
   - **macOS**:  
     - Ruby comes pre-installed. Update with Homebrew:  
       ```bash
       brew install ruby
       ```  
   - **Linux**:  
     - Install via package manager:  
       ```bash
       sudo apt-get install ruby-full
       ```

2. **Verify Installation**:  
   ```bash
   ruby --version
   gem --version
   ```

3. **Install a Version Manager (Optional)**:  
   Use **RVM** or **rbenv** to manage Ruby versions.  
   - Install RVM:  
     ```bash
     curl -sSL https://get.rvm.io | bash -s stable
     rvm install ruby
     ```  

---

### **Step 2: Setup**

1. **Editor**:  
   - Recommended: **Visual Studio Code** (with Ruby extension) or Sublime Text.  

2. **File Structure**:  
   - Ruby scripts use `.rb` extensions. Organize as:  
     ```
     project_name/
       ├── main.rb
       ├── lib/
       ├── data/
       └── README.md
     ```

3. **Run a Ruby Script**:  
   ```bash
   ruby main.rb
   ```

---

### **Step 3: Ruby Basics**

#### 1. **Core Syntax**:  
- **Hello World**:  
   ```ruby
   puts "Hello, World!"
   ```

- **Variables**:  
   ```ruby
   name = "Commander"
   age = 30
   pi = 3.14
   ```

- **Data Types**: Strings, Numbers, Arrays, Hashes, Symbols:  
   ```ruby
   fruits = ["apple", "banana", "cherry"]
   person = { name: "John", age: 30 }
   ```

---

#### 2. **Conditionals**:  
   ```ruby
   age = 18
   if age >= 18
     puts "You are an adult."
   else
     puts "You are a minor."
   end
   ```

---

#### 3. **Loops**:  
   ```ruby
   # For loop
   for i in 1..5 do
     puts "Number #{i}"
   end

   # Each loop
   [1, 2, 3].each do |num|
     puts num
   end

   # While loop
   count = 0
   while count < 5
     puts count
     count += 1
   end
   ```

---

#### 4. **Functions**:  
   ```ruby
   def greet(name)
     "Hello, #{name}!"
   end
   puts greet("Commander")
   ```

---

#### 5. **Object-Oriented Programming (OOP)**:  

1. **Classes and Objects**:  
   ```ruby
   class Person
     attr_accessor :name, :age

     def initialize(name, age)
       @name = name
       @age = age
     end

     def introduce
       puts "Name: #{@name}, Age: #{@age}"
     end
   end

   person = Person.new("Commander", 30)
   person.introduce
   ```

2. **Inheritance**:  
   ```ruby
   class Animal
     def speak
       puts "I am an animal."
     end
   end

   class Dog < Animal
     def speak
       puts "Woof!"
     end
   end

   dog = Dog.new
   dog.speak
   ```

---

#### 6. **File I/O**:  
   ```ruby
   # Write to a file
   File.open("example.txt", "w") { |file| file.puts("Hello, File!") }

   # Read from a file
   File.readlines("example.txt").each { |line| puts line }
   ```

---

### **Step 4: Useful Gems**

1. **Install Gems**:  
   - Ruby uses **gems** (libraries). Install with:  
     ```bash
     gem install <gem_name>
     ```

2. **Essential Gems**:  
   - **Sinatra**: Lightweight web apps (`gem install sinatra`).  
   - **Rails**: Full-stack web framework (`gem install rails`).  
   - **Pry**: Debugging tool (`gem install pry`).  
   - **RSpec**: Testing framework (`gem install rspec`).  

---

### **Step 5: Projects (Beginner to Intermediate)**

#### **Project 1: Basic Calculator**  
**Purpose**: Perform basic math operations.  
**Code**:  
```ruby
puts "Enter first number:"
num1 = gets.chomp.to_f
puts "Enter operator (+, -, *, /):"
operator = gets.chomp
puts "Enter second number:"
num2 = gets.chomp.to_f

result = case operator
         when "+" then num1 + num2
         when "-" then num1 - num2
         when "*" then num1 * num2
         when "/" then num1 / num2
         else "Invalid operator"
         end
puts "Result: #{result}"
```

---

#### **Project 2: To-Do List (CRUD Operations)**  
**Purpose**: Add, view, and remove tasks.  
**Code**:  
```ruby
tasks = []

loop do
  puts "\n1. Add Task\n2. View Tasks\n3. Remove Task\n4. Exit"
  choice = gets.chomp.to_i

  case choice
  when 1
    puts "Enter a task:"
    tasks << gets.chomp
  when 2
    puts "Tasks:"
    tasks.each_with_index { |task, index| puts "#{index + 1}. #{task}" }
  when 3
    puts "Enter task number to remove:"
    task_num = gets.chomp.to_i
    tasks.delete_at(task_num - 1)
  when 4
    break
  else
    puts "Invalid choice!"
  end
end
```

---

#### **Project 3: File Encryption Tool**  
**Purpose**: Encrypt and decrypt text files.  
**Code**:  
```ruby
require 'openssl'

key = "my_secret_key"

def encrypt_file(input, output, key)
  cipher = OpenSSL::Cipher.new('AES-256-CBC').encrypt
  cipher.key = key

  encrypted = ""
  File.open(input, "rb") do |file|
    encrypted = cipher.update(file.read) + cipher.final
  end

  File.open(output, "wb") { |file| file.write(encrypted) }
  puts "File encrypted!"
end

def decrypt_file(input, output, key)
  cipher = OpenSSL::Cipher.new('AES-256-CBC').decrypt
  cipher.key = key

  decrypted = ""
  File.open(input, "rb") do |file|
    decrypted = cipher.update(file.read) + cipher.final
  end

  File.open(output, "wb") { |file| file.write(decrypted) }
  puts "File decrypted!"
end

encrypt_file("plain.txt", "encrypted.txt", key)
decrypt_file("encrypted.txt", "decrypted.txt", key)
```

---

#### **Project 4: Web App with Sinatra**  
**Purpose**: Build a simple web application.  
**Steps**:  
1. Install Sinatra:  
   ```bash
   gem install sinatra
   ```

2. Code:  
   ```ruby
   require 'sinatra'

   get '/' do
     "Hello, World!"
   end
   ```

3. Run the app:  
   ```bash
   ruby app.rb
   ```

4. Access at `http://localhost:4567`.

---

#### **Project 5: Weather Fetcher**  
**Purpose**: Fetch live weather data using an API.  
**Steps**:  
1. Install `httparty`:  
   ```bash
   gem install httparty
   ```

2. Code:  
   ```ruby
   require 'httparty'

   def get_weather(city)
     api_key = "your_api_key"
     response = HTTParty.get("http://api.openweathermap.org/data/2.5/weather?q=#{city}&appid=#{api_key}&units=metric")
     if response.code == 200
       puts "Weather in #{city}: #{response['main']['temp']}°C"
     else
       puts "City not found!"
     end
   end

   puts "Enter city name:"
   city = gets.chomp
   get_weather(city)
   ```

---

### **Step 6: Advanced Concepts**

1. **Metaprogramming**:  
   - Learn how Ruby lets you write code that writes code.  
   - Example:  
     ```ruby
     class MyClass
       define_method(:dynamic_method) { |arg| puts "Hello, #{arg}!" }
     end
     MyClass.new.dynamic_method("World")
     ```

2. **Rails Framework**:  
   - Dive into Rails for full-stack web development:  
     ```bash
     gem install rails
     rails new my_app
     ```

3. **Debugging with Pry**:  
   ```ruby
   require 'pry'
   binding.pry  # Add this line to pause execution
   ```

---

### **Final Notes**

1. Ruby is ideal for web development, scripting, and rapid prototyping.  
2. Master both scripting and frameworks like Sinatra or Rails for real-world applications.  
3. Practice writing clean, reusable code with real-world projects.
