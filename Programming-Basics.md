# Programming

## Why?

- **Understanding Web Applications**
- **Task Automation**
- **Building New Tools**
- **Exploitation**

## Programming

- The process of creating code that a computer can understand and execute
    - **Python has an interpreter**
    - **Golang has a compiler**

![Untitled Diagram.drawio56565656.png](/images/Untitled%20Diagram.drawio56565656.png)

## Syntax

- Rules and conventions that define how code should be written and structured to be understood by a compiler or interpreter

## Package Manager

- A tool that simplifies the process of installing, managing, and updating third-party libraries and dependencies in a project

---

## Fundamentals

### Variable

- A storage location used to hold data temporarily in memory

```python
x = 10
```

### Data Types

1. **String**: Text data
2. **Integer**: Whole numbers
3. **Boolean**: True or False values

```python
x = 10  # Integer
name = "Navid"  # String
is_student = True  # Boolean
```

### List (Array)

- A collection of data that can be of the same or different types. Elements are stored sequentially and can be accessed using an index
- Indexing starts at **0**

```python
numbers = [1, 2, 3]

print(numbers[0])  # 1
print(numbers[1])  # 2
print(numbers[2])  # 3
```

### Dictionary

- A data structure that stores key-value pairs. Each key is unique and is associated with a specific value

```python
person = {'name': 'Navid', 'age': 18}

print(person.get('name'))  # Navid
```

### Conditionals

- Allows the execution of code based on whether a condition is true or false

```python
x = 10

if x > 5:
    print("x is greater than 5")
else:
    print("x is not greater than 5")
```

- **Indent**: Telling the interpreter the blocks of code

### Loops

- Used to iterate over a sequence (like a list or dictionary) or execute code repeatedly until a condition is met

```python
fruits = ["apple", "banana"]

for fruit in fruits:
    print(fruit)
```

### Function

- A reusable block of code that performs a specific task or calculation. Functions can also return values

```python
def add_numbers(a, b):
    return a + b

result = add_numbers(3, 5)
print(result)  # 8
```

### User Input

- Allows the program to take input from the user, typically from the command line or terminal

```python
import sys

user_input = sys.argv[1]
print(user_input)
```

- How to run the code with input:
    
    ```bash
    >> python3 file.py Navid
    ```
    

### I/O

- Input and Output operations involve reading data from a source or writing data to a destination, such as a file
- For example, consider a simple `.txt` file containing the following content:
    
    ```
    This is line 1.
    This is line 2.
    This is line 3.
    
    ```
    
- We can read this file in Python using the following code:
    
    ```python
    file_name = 'sample.txt'
    
    with open(file_name, 'r') as file:
        content = file.read()
        print(content)
    
    ```
    

### Class

- Important for handling **object injection** and **insecure deserialization** in white-box pentesting
- A template (blueprint) for creating objects
    - It defines a set of attributes (data)
    - It defines a set of methods (functions)
    - An object is an instance of a class
    - Classes are fundamental to object-oriented programming
- Example of a simple class:
    
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age
    
    person = Person("Navid", 18)
    
    print(person.name)  # Output: Navid
    print(person.age)   # Output: 18
    
    ```
    
- **Explanation**:
    - The `__init__()` method is a **constructor** that gets called automatically when an object is created from the class. It initializes the object's attributes, like `name` and `age` in this example
    - The `self` keyword refers to the current instance of the class. It is used to access variables (attributes) and methods within the class
- **Class Chain**:
    - **Class** → **Initiate** → **Object** ⇒ **Data**, **Attributes**, and **Methods** (with some methods automatically called, like the constructor `__init__()`)
- **Constructor**: The `__init__()` function acts as a **constructor**, meaning it is automatically invoked when creating an object. It sets initial values for the object's attributes

---

## JSON

- JSON is a lightweight data format

```python
data = {"name": "Navid", "age": 18, "city": "New York"} # JSON

print(data["name"]) # Navid
```

```python
data = '{"name": "Navid", "age": 18, "city": "New York"}' # String

print(data["name"]) # no response
```

- Parse: Analyzing a sequence of character or data

![Untitled Diagram.drawio787878.png](/images/Untitled%20Diagram.drawio787878.png)

```python
import json

data = '{"name": "Navid", "age": 18, "city": "New York"}'  # String

json_data = json.loads(data)  # Parse String to JSON
```

- We can also **convert JSON back to a String** using `json.dumps()`

### How to Extract Information?

1. **Regex**: Use regular expressions for pattern matching.
2. **Conditional Parsing**: Parse → Object → Extract

## Regex (Regular Expressions)

- **Definition**: A powerful tool for pattern matching and string manipulation.

```python
text = "Hello, my email is navid@gmail.com"

email_pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9._]+\\.[A-Z|a-z]{2,7}\b'

```

### Common Regex Patterns

- **`[a-zA-Z]`** : Matches any character from 'a' to 'z' and 'A' to 'Z'
- **`[0-9]`** : Matches any single digit
- **`\w`** : Matches any word character (alphanumeric + underscore)
- **`\d`** : Matches any digit.
- **`\s`** : Matches any whitespace (spaces, tabs, line breaks)
- **`\W`** : Matches any non-word character
- **`\D`** : Matches any non-digit character
- **`\S`** : Matches any non-whitespace character
- **`.`** : Matches any character except a newline
- **`^`** : Matches the start of a string
- **`$`** : Matches the end of a string
- **`*`** : Matches zero or more occurrences
- **`+`** : Matches one or more occurrences
- **`?`** : Makes the previous character optional
- **`|`** : Acts as an OR operator in patterns
- **`(abc)`** : Captures a group of characters
- **`\t \n \r`** : Represents tab, newline, and carriage return
- **`\.`** : Escapes special characters, such as a dot ('.')
    - Escape: not parsing the next character

### Example

1. ^https?:\/\/google\.com$
    - https://google.com
    - https://google.com
2. \d{5}(-\d{4})?
    - 41123-4534
    - 55661

---

## Requests LIB

- A popular third-party package

```python
import requests

r = requests.session()
res = r.get("https://wordlists.assetnote.io/data/automated.json")

for item in res.json().get('data'):
    print(f"https://wordlists.assetnote.io/data/automated.json/{item.get('Filename')}")
    # item['Filename'] = item.get('Filename')
```

## BeatifulSoup

- Parsing HTML and XML documents

```python
import requests
from bs4 import BeautifulSoup

# Create a session
r = requests.session()

# Make a GET request to the webpage
res = r.get('https://memoryleaks.ir/wp-login.php')

# Parse the HTML content using BeautifulSoup
soup = BeautifulSoup(res.text, 'html.parser')

# Find the div tag with the class 'c4wp_captcha_field' and extract the data-nonce attribute
div_tag = soup.find('div', class_='c4wp_captcha_field')

if div_tag:
    data_nonce = div_tag.get('data-nonce')
    print("data-nonce:", data_nonce)
else:
    print("No div with the specified class found.")

```

---

## Tasks

Extract the value of the `data-nonce` attribute with Regex:

```python
import requests, re

r = requests.session()
res = r.get('https://memoryleaks.ir/wp-login.php')

match = re.search(r'data-nonce="(\w+)"', res.text)

if match:
    print("Found nonce:", match.group(1))
else:
    print("Nonce not found")
```

Sheypoor login-er with python code:

```python
import requests, warnings, json
from colorama import Fore

r = requests.Session()

proxies = {
    "http": "http://127.0.0.1:8081",
    "https": "http://127.0.0.1:8081",
}

r.proxies.update(proxies)

r.verify = False

warnings.filterwarnings('ignore', message='Unverified HTTPS request')

art = """

   _____ _                                         _             _                      
  / ____| |                                       | |           (_)                     
 | (___ | |__   ___ _   _ _ __   ___   ___  _ __  | | ___   __ _ _ _ __ ______ ___ _ __ 
  \___ \| '_ \ / _ \ | | | '_ \ / _ \ / _ \| '__| | |/ _ \ / _` | | '_ \______/ _ \ '__|
  ____) | | | |  __/ |_| | |_) | (_) | (_) | |    | | (_) | (_| | | | | |    |  __/ |   
 |_____/|_| |_|\___|\__, | .__/ \___/ \___/|_|    |_|\___/ \__, |_|_| |_|     \___|_|   
                     __/ | |                                __/ |                       
                    |___/|_|                               |___/                        

"""

print(f"{Fore.LIGHTBLUE_EX}{art}")

phone_number = input(f"{Fore.LIGHTGREEN_EX}\nEnter phone number: ")

response = r.post("https://www.sheypoor.com/api/v10.0.0/auth/send",
    headers={
        "Referer": "https://www.sheypoor.com/session",
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:131.0)",
        "Content-Type": "application/json;charset=utf-8"
    },
    data=json.dumps({
        "username": phone_number
        }),
    allow_redirects=False
)

if response.status_code == 200:
    print(f"{Fore.LIGHTYELLOW_EX}[+] OTP sent successfully!")
else:
    print(f"{Fore.LIGHTRED_EX}[-] Error sending OTP:", response.status_code, response.text)
    exit()

otp_code = input(f"{Fore.LIGHTGREEN_EX}Enter OTP code: ")

response = r.post("https://www.sheypoor.com/api/v10.0.0/auth/verify",
    headers={
        "Origin": "https://www.sheypoor.com",
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:131.0)",
        "Referer": "https://www.sheypoor.com/session",
        "Content-Type": "application/json;charset=utf-8"
    },
    data=json.dumps({
        "verification_code": otp_code
        }),
    allow_redirects=False
)

if response.status_code == 200:
    print(f"{Fore.LIGHTYELLOW_EX}[+] OTP verified successfully!")
else:
    print(f"{Fore.LIGHTRED_EX}[-] Error verifying OTP:", response.status_code, response.text)
    exit()

response = r.get("https://www.sheypoor.com/api/v10.0.0/user/profile",
    headers={
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:131.0)",
        "Referer": "https://www.sheypoor.com/session/my-profile"
    },
    allow_redirects=False
)

if response.status_code == 200:
    profile_data = response.json().get("data")
    if profile_data:
        print(f"{Fore.LIGHTWHITE_EX}User ID: {profile_data.get('id')}")
        print(f"{Fore.LIGHTWHITE_EX}Name: {profile_data.get('attributes').get('name')}")
        print(f"{Fore.LIGHTWHITE_EX}Image: {profile_data.get('attributes').get('image')}")
        print(f"{Fore.LIGHTWHITE_EX}Public Link: {profile_data.get('attributes').get('publicLink')}")
    else:
        print(f"{Fore.LIGHTRED_EX}[-] Error: Could not retrieve profile data.")
else:
    print(f"{Fore.LIGHTRED_EX}[-] Error fetching profile:", response.status_code, response.text)

print(Fore.RESET)
```

Digikala login-er with python code:

```python
import requests, json, urllib3

# 1. phone number -> HTTP
# 2. OTP -> HTTP (login)
# 3. GET user profile -> HTTP (data)

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

ascii_art = """
 ____  _       _ _         _         _             _                        
|  _ \\(_) __ _(_) | ____ _| | __ _  | | ___   __ _(_)_ __         ___ _ __  
| | | | |/ _` | | |/ / _` | |/ _` | | |/ _ \\ / _` | | '_ \\ _____ / _ \\ '__| 
| |_| | | (_| | |   < (_| | | (_| | | | (_) | (_| | | | | |_____|  __/ |    
|____/|_|\\__, |_|_|\\_\\__,_|_|\\__,_| |_|\\___/ \\__, |_|_| |_|      \\___|_|    
         |___/                               |___/                           
"""

print(ascii_art)

# Create a session
r = requests.session()

proxies = {
    "http": "http://127.0.0.1:8080",
    "https": "http://127.0.0.1:8080",
}

r.proxies.update(proxies)
r.verify = False

# Python code to take user input interactively
phone_number = input("Enter phone number: ")

if phone_number:

    data = {
        "username": phone_number,
        "otp_call": False
    }

    # Set the headers
    headers = {
        "Content-Type": "application/json"
    }

    res = r.post('https://api.digikala.com/v1/user/authenticate/', headers=headers, data=json.dumps(data))

    if res.json().get("status") == 200:
        print("[+] SMS has been sent")

        otp_code = input("Enter enter OTP code: ")

        data = {
            "type": "otp",
            "username": phone_number,
            "code": otp_code
        }

        res = r.post('https://api.digikala.com/v1/user/login/otp/', headers=headers, data=json.dumps(data))

        if res.json().get("status") == 200:
            res = r.get('https://api.digikala.com/v1/user/init/')
            user_data = res.json().get('data').get('user')

            print(f"user id: {user_data['id']}")
            print(f"user id: {user_data['first_name']}")
            print(f"user id: {user_data['last_name']}")
        else:
            print(f"[-] Error: {res.text}")

    else:
        print(f"[-] Error: {res.text}")
```