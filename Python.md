# Python for Security

## Why?

* **Security Automation**
* **Web Application Testing**
* **API Testing**
* **Data Parsing**
* **Reconnaissance**
* **Building Security Tools**
* **Working with HTTP Requests**
* **Writing Custom Scripts**

Python is widely used in security because it provides a simple syntax and a large ecosystem of libraries for networking, web applications, automation, parsing, and data processing.

---

## Python

* A high-level programming language with an interpreter

```python
print("Hello, Security!")
```

Run the program:

```bash
python3 script.py
```

---

## Variables

* A variable is a name that references a value

```python
username = "admin"
port = 8080
is_authenticated = False

print(username)
print(port)
print(is_authenticated)
```

---

## Data Types

Common Python data types:

1. **String**
2. **Integer**
3. **Float**
4. **Boolean**
5. **List**
6. **Dictionary**
7. **Tuple**
8. **Set**

```python
name = "admin"       # String
port = 443           # Integer
version = 1.5       # Float
secure = True        # Boolean

ports = [80, 443]   # List

user = {
    "username": "admin",
    "role": "user"
}                    # Dictionary
```

---

## Lists

* A collection of values
* Indexing starts at **0**

```python
ports = [21, 22, 80, 443]

print(ports[0])  # 21
print(ports[2])  # 80
```

### Looping Through a List

```python
ports = [21, 22, 80, 443]

for port in ports:
    print(f"Port: {port}")
```

---

## Dictionary

* Stores data as **key-value pairs**

```python
user = {
    "username": "admin",
    "role": "administrator",
    "active": True
}

print(user["username"])
print(user.get("role"))
```

Dictionaries are especially useful when working with **JSON and API responses**.

---

## Conditions

* Used to execute code based on a condition

```python
status_code = 200

if status_code == 200:
    print("Request successful")
elif status_code == 404:
    print("Not found")
else:
    print("Something went wrong")
```

---

## Loops

### For Loop

```python
ports = [80, 443, 8080]

for port in ports:
    print(port)
```

### While Loop

```python
counter = 0

while counter < 5:
    print(counter)
    counter += 1
```

Loops are useful for tasks such as processing:

* URLs
* Ports
* HTTP responses
* Wordlists
* API results
* Log files

---

## Functions

* A reusable block of code

```python
def check_status(status_code):

    if status_code == 200:
        return "OK"

    return "Not OK"


result = check_status(200)

print(result)
```

Functions make security scripts easier to maintain and reuse.

---

## User Input

* Allows a program to receive input from the user

```python
target = input("Enter target: ")

print(f"Target: {target}")
```

Run:

```bash
python3 scanner.py
```

Example:

```text
Enter target: localhost
Target: localhost
```

---

## Command Line Arguments

Python can receive arguments from the command line.

```python
import sys

target = sys.argv[1]

print(f"Target: {target}")
```

Run:

```bash
python3 scanner.py localhost
```

Output:

```text
Target: localhost
```

### Multiple Arguments

```python
import sys

target = sys.argv[1]
port = sys.argv[2]

print(f"Target: {target}")
print(f"Port: {port}")
```

Run:

```bash
python3 scanner.py localhost 8080
```

---

# File I/O

Python can read and write files.

### Read a File

```python
with open("targets.txt", "r") as file:

    for line in file:
        print(line.strip())
```

### Write to a File

```python
with open("results.txt", "w") as file:
    file.write("Scan completed\n")
```

### Append to a File

```python
with open("results.txt", "a") as file:
    file.write("New result\n")
```

This is useful for processing:

* Wordlists
* URLs
* Logs
* Scan results
* Configuration files

---

# Exception Handling

Security scripts often interact with external systems, so errors are expected.

```python
try:

    number = int(input("Enter a number: "))

    print(number)

except ValueError:

    print("Invalid number")
```

### Handling Requests

```python
import requests

try:

    response = requests.get(
        "http://127.0.0.1:8000",
        timeout=5
    )

    print(response.status_code)

except requests.RequestException as error:

    print(f"Request failed: {error}")
```

---

# Modules

* A module is a Python file containing reusable code

Python includes many built-in modules.

```python
import os

print(os.getcwd())
```

Other useful modules:

```python
import sys
import json
import re
import socket
import urllib.parse
```

---

# Virtual Environment

* A virtual environment isolates project dependencies

Create one:

```bash
python3 -m venv venv
```

Activate:

```bash
source venv/bin/activate
```

Install a package:

```bash
pip install requests
```

Deactivate:

```bash
deactivate
```

---

# Requests

* `requests` is a popular library for making HTTP requests

Install:

```bash
pip install requests
```

### GET Request

```python
import requests

response = requests.get(
    "http://127.0.0.1:8000",
    timeout=5
)

print(response.status_code)
print(response.text)
```

### POST Request

```python
import requests

data = {
    "username": "admin",
    "password": "password"
}

response = requests.post(
    "http://127.0.0.1:8000/login",
    json=data,
    timeout=5
)

print(response.status_code)
print(response.text)
```

### Headers

```python
import requests

headers = {
    "User-Agent": "SecurityLab/1.0",
    "Accept": "application/json"
}

response = requests.get(
    "http://127.0.0.1:8000",
    headers=headers,
    timeout=5
)

print(response.status_code)
```

---

# Sessions

* A session allows requests to share cookies and other settings

```python
import requests

session = requests.Session()

response = session.get(
    "http://127.0.0.1:8000",
    timeout=5
)

print(response.cookies)
```

Sessions are useful when testing applications that use:

* Cookies
* Authentication
* CSRF tokens
* Multiple requests in the same session

---

# Proxies

Python requests can be sent through an HTTP proxy.

This is useful when testing applications through tools such as **Burp Suite** in a local lab.

```python
import requests

proxies = {
    "http": "http://127.0.0.1:8080",
    "https": "http://127.0.0.1:8080"
}

response = requests.get(
    "http://127.0.0.1:8000",
    proxies=proxies,
    timeout=5
)

print(response.status_code)
```

> Use a proxy against applications you own or are authorized to test.

---

# JSON

* JSON is commonly used by modern APIs

Example JSON:

```json
{
    "username": "admin",
    "role": "user"
}
```

Python dictionary:

```python
data = {
    "username": "admin",
    "role": "user"
}
```

### JSON String → Python Object

```python
import json

data = '{"username": "admin", "role": "user"}'

parsed = json.loads(data)

print(parsed["username"])
```

### Python Object → JSON String

```python
import json

data = {
    "username": "admin",
    "role": "user"
}

result = json.dumps(data)

print(result)
```

---

# Regular Expressions

* Regex can be used to find patterns inside text

```python
import re

text = "User: admin, ID: 12345"

match = re.search(
    r"ID:\s*(\d+)",
    text
)

if match:
    print(match.group(1))
```

Output:

```text
12345
```

Regex can be useful for extracting:

* URLs
* Email addresses
* IDs
* Tokens in controlled lab environments
* IP addresses
* Headers
* Log entries

---

# HTML Parsing

* `BeautifulSoup` can parse HTML documents

Install:

```bash
pip install beautifulsoup4
```

Example:

```python
from bs4 import BeautifulSoup

html = """
<html>
    <body>
        <h1>Security Lab</h1>
        <div data-id="12345">User</div>
    </body>
</html>
"""

soup = BeautifulSoup(html, "html.parser")

title = soup.find("h1")

print(title.text)
```

### Extract Attribute

```python
div = soup.find("div")

if div:
    print(div.get("data-id"))
```

---

# URL Parsing

Python provides tools for working with URLs.

```python
from urllib.parse import urlparse

url = "https://example.com:443/api/users?id=10"

parsed = urlparse(url)

print(parsed.scheme)
print(parsed.hostname)
print(parsed.port)
print(parsed.path)
print(parsed.query)
```

Output:

```text
https
example.com
443
/api/users
id=10
```

---

# DNS

Python can resolve hostnames.

```python
import socket

hostname = "localhost"

ip = socket.gethostbyname(hostname)

print(ip)
```

Example:

```text
127.0.0.1
```

---

# Hashing

Python can calculate cryptographic hashes.

```python
import hashlib

data = b"security"

hash_value = hashlib.sha256(data).hexdigest()

print(hash_value)
```

Hashing can be useful when working with:

* File integrity
* Fingerprinting
* Security tools
* Data comparison

> Hashing is not the same as encryption. A cryptographic hash is designed to be one-way.

---

# Base64

Python includes support for Base64 encoding and decoding.

```python
import base64

data = b"security"

encoded = base64.b64encode(data)

print(encoded)
```

Decode:

```python
decoded = base64.b64decode(encoded)

print(decoded)
```

Base64 is an **encoding**, not encryption.

---

# Subprocess

* The `subprocess` module allows Python to execute system commands

```python
import subprocess

result = subprocess.run(
    ["whoami"],
    capture_output=True,
    text=True
)

print(result.stdout)
```

Another example:

```python
import subprocess

result = subprocess.run(
    ["ls", "-la"],
    capture_output=True,
    text=True
)

print(result.stdout)
```

> Avoid passing untrusted user input directly into shell commands. Improper command construction can introduce command injection vulnerabilities.

---

# Working With Wordlists

A common task in security automation is processing a wordlist.

Example `words.txt`:

```text
admin
administrator
test
guest
user
```

Python:

```python
with open("words.txt", "r") as file:

    for word in file:

        word = word.strip()

        if word:
            print(word)
```

---

# HTTP Status Codes

Python can be used to analyze HTTP responses.

```python
import requests

response = requests.get(
    "http://127.0.0.1:8000",
    timeout=5
)

status = response.status_code

if status == 200:
    print("OK")

elif status == 404:
    print("Not Found")

elif status == 403:
    print("Forbidden")

else:
    print(f"Status: {status}")
```

---

# API Testing

Python is useful for testing APIs in an authorized environment.

Example local API:

```python
import requests

url = "http://127.0.0.1:8000/api/users"

response = requests.get(
    url,
    timeout=5
)

if response.status_code == 200:

    data = response.json()

    for user in data.get("users", []):
        print(user.get("username"))
```

---

# API Request Flow

A common API testing workflow:

```text
Request
   ↓
HTTP Method
   ↓
Headers
   ↓
Parameters / JSON
   ↓
Server
   ↓
HTTP Response
   ↓
Status Code
   ↓
Response Body
```

Example:

```python
response = requests.post(
    "http://127.0.0.1:8000/api/login",
    headers={
        "Content-Type": "application/json"
    },
    json={
        "username": "admin",
        "password": "password"
    },
    timeout=5
)

print(response.status_code)
print(response.text)
```

---

# Automation

Python becomes especially useful when a task needs to be repeated.

For example, checking a list of URLs:

```python
import requests

urls = [
    "http://127.0.0.1:8000",
    "http://127.0.0.1:8001",
    "http://127.0.0.1:8002"
]

for url in urls:

    try:

        response = requests.get(
            url,
            timeout=3
        )

        print(
            f"{url} -> {response.status_code}"
        )

    except requests.RequestException:

        print(
            f"{url} -> Connection failed"
        )
```

---

# Building a Simple Security Tool

A simple URL checker:

```python
import requests
import sys

if len(sys.argv) != 2:

    print("Usage: python3 checker.py <url>")
    sys.exit(1)

url = sys.argv[1]

try:

    response = requests.get(
        url,
        timeout=5
    )

    print(f"URL: {url}")
    print(f"Status: {response.status_code}")
    print(f"Server: {response.headers.get('Server')}")

except requests.RequestException as error:

    print(f"Error: {error}")
```

Run:

```bash
python3 checker.py http://127.0.0.1:8000
```

---

# Tasks

### Task 1 — URL Status Checker

Create a Python program that:

1. Receives a URL from the command line
2. Sends a GET request
3. Prints the status code
4. Prints the response size
5. Handles connection errors

---

### Task 2 — Wordlist Parser

Create a program that:

1. Reads a wordlist
2. Removes empty lines
3. Removes duplicate values
4. Prints the number of unique entries

Example:

```python
words = set()

with open("words.txt", "r") as file:

    for line in file:

        word = line.strip()

        if word:
            words.add(word)

print(f"Unique words: {len(words)}")
```

---

### Task 3 — HTTP Header Analyzer

Write a script that requests a local web application and prints:

* Status code
* Server header
* Content-Type
* Content-Length
* Set-Cookie

---

### Task 4 — JSON Parser

Given:

```json
{
    "users": [
        {
            "id": 1,
            "username": "admin"
        },
        {
            "id": 2,
            "username": "guest"
        }
    ]
}
```

Write Python code that prints only the usernames.

---

### Task 5 — Regex Extraction

Given:

```text
User: admin
ID: 12345
Role: administrator
```

Use Regex to extract:

```text
admin
12345
administrator
```

---

### Task 6 — Local API Testing

Create a local test API and write a Python script that:

1. Sends a GET request
2. Sends a POST request
3. Parses the JSON response
4. Prints the HTTP status code
5. Handles errors

---

# Security Libraries

Some useful Python libraries for security-related development:

| Library         | Purpose                  |
| --------------- | ------------------------ |
| `requests`      | HTTP requests            |
| `BeautifulSoup` | HTML parsing             |
| `re`            | Regular expressions      |
| `socket`        | Network communication    |
| `json`          | JSON processing          |
| `hashlib`       | Hashing                  |
| `base64`        | Base64 encoding/decoding |
| `urllib.parse`  | URL parsing              |
| `subprocess`    | Process execution        |
| `argparse`      | Command-line arguments   |

---

# Useful Concepts

Before building larger security tools, understand:

* Python syntax
* Functions
* Classes
* Exceptions
* File I/O
* JSON
* Regex
* HTTP
* Cookies
* Headers
* Sessions
* APIs
* URL parsing
* Command-line arguments
* Virtual environments

---

# Security Mindset

Python itself does not make a tool a security tool.

The important part is understanding:

```text
Input
  ↓
Processing
  ↓
Request / Action
  ↓
Response
  ↓
Analysis
  ↓
Result
```

The same Python knowledge can be used to build:

* Reconnaissance tools
* API testing tools
* HTTP clients
* Log analyzers
* Automation scripts
* Security scanners
* Data extraction tools
* Custom testing utilities

Always test against systems you own or have explicit permission to assess.
