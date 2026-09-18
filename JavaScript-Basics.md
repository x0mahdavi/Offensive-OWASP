# JavaScript

## Why?

- Every website has JavaScript
- To discover vulnerabilities (XSS, etc)
- To bypass security devices (Firewall, etc)
- To conduct narrow recon in bug bounty
- To exploit vulnerabilities (XSS, etc)

## Browser

![JS1.png](/images/JS1.png)

### Main Components of a Web Browser

1. **User Interface**
2. **Rendering Engine**
3. **Browser Engine**
4. **Networking**
5. **JavaScript Interpreter**
6. **Data Storage**

### Headless Browser

Is a web browser without a user interface, allowing it to run in the background for tasks like automation and testing

```bash
google-chrome --headless http://voorivex.academy
```

## HTML

Standard markup language

- To create and structure content on the web
- Set of tags and elements (pre-defined)
- To define the text, images, etc of web pages
- Allowing browsers to interpret and display the content

![JS2.png](/images/JS2.png)

The `<script>` tag is used to run JavaScript

```html
<script>
    alert('Yallah');
</script>
```

A great resource for all HTML tags and attributes is [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)

Here’s a simple example of an HTML code:

```html
<html>
<head>
    <title>The Adventures of My Cat Lucky</title>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <meta name="description" content="The adventures of my pet, with stories, pictures and movies.">
    <meta name="keywords" content="cat,lucky,pet,animal">
    <link rel="stylesheet" type="text/css" href="/style.css">
    <link rel="shortcut icon" href="/favicon.ico">
</head>
<body>
    <h1>The Adventures of My Cat Lucky</h1>
    <div id="mainContent">
        <p>My cat Lucky has a lot of adventures.</p>
        <p>Here's a picture of Lucky:</p>
        <img src="lucky.jpg" alt="Lucky">
    </div>
    <div id="sidebar">
        <h2>Buy our stuff!</h2>
        <p>Some of our products include <span class="product">SuperWidgets</span></p>
    </div>
</body>
</html>
```

## Console

Allows developers to interact with the JavaScript

- Debugging JavaScript code by logging messages
- Inspecting variables and objects during runtime
- Tracking errors and warnings

---

## Loading

![JS3.png](/images/JS3.png)

- An HTTP request is first sent, and the response is received. The browser then parses the HTML code line by line. It may send additional requests based on the HTML, which could be cross-origin
    - While parsing the second line, the browser triggers an HTTP request to `/logo.png`
    - The third line triggers an HTTP request to `/jquery.js`
    - The fourth line contains JavaScript, which may or may not send another HTTP request. In this example, it results in updating the page

## Document Object Model (DOM)

**Programming interface for the web** that allows JavaScript to dynamically access and update the content, structure, and style of a web page

- Content manipulation dynamically

![JS4.png](/images/JS4.png)

### Document Object

- **Object**: Groups data and related behaviors
- document object has various data
    
    ```jsx
    document.location              //    https://voorivex.academy/
    documnet.location.hostname    //    voorivex.academy
    document.cookie
    ```
    

### SELECT

```jsx
document.getElementById
document.getElementsByName
document.getElementsByClassName
```

Example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Change Content Example</title>
</head>
<body>
    <h1 id="heading">Original Heading</h1>
    <p name="paragraph">Original Paragraph</p>
    <div class="content">Original Content</div>

    <script>
        var headingElement = document.getElementById('heading');
        var paragraphElements = document.getElementsByName('paragraph')[0];
        var contentElements = document.getElementsByClassName('content')[0];
        
        console.log(headingElement.textContent);  //  Original Heading
        
    </script>
</body>
</html>
```

To modify the content of a DOM element, both `innerText` and `innerHTML` can be used:

- **`innerHTML`**: Changes the content inside an element and can also handle HTML tags
- **`innerText`**: Changes the visible text inside an element, ignoring any HTML tags

```jsx
headingElement.innerText = 'Changed';
headingElement.innerHTML = '<p>Changed</p>';
```

### Event Handlers

invoked when a specific event occurs. This is important because it allows us to execute JavaScript

- **onclick**: Triggered when an element is clicked, used for interactive actions
- **onload**: Fired when the page or an image finishes loading, ensuring elements are ready
- **onchange**: Triggered when the value of an input element changes, responding to user input

For a complete list of event handlers, check the [JavaScript Event Reference on W3Schools](https://www.w3schools.com/js/js_events.asp)

```html
<!DOCTYPE html>
<html>
<head>
    <title>Change Page Content After 5 Seconds</title>
</head>
<body>
    <h1 id="content" onclick="alert('clicked')">Original Content</h1>

    <script>
        // Function to change the page content
        function changeContent() {
            var contentElement = document.getElementById('content');
            contentElement.innerText = 'New Content After 5 Seconds';
        }

        // Call the changeContent function after 5 seconds (5000 milliseconds)
        setTimeout(changeContent, 5000);
    </script>
</body>
</html>
```

---

## Fundamentals

### Variable

```jsx
var name = "Mamad";
let name = "Mamad";
const name = 30;  // Value won't change
```

### Data Types

1. **Boolean**
    
    ```jsx
    let isTrue = true;
    
    ```
    
2. **Array**
    
    ```jsx
    let colors = ["red", "green", "blue"];
    
    ```
    
3. **Object**
    
    ```jsx
    let person = {
        firstName: "Mamad",
        lastName: "Mamadi"
    };
    
    ```
    

### Conditions

1. **if statement**
    
    ```jsx
    let age = 20;
    
    if (age > 30) {
        console.log("I'm over 30");
    } else {
        console.log("I'm under 30");
    }
    
    ```
    
2. **switch statement**
    
    ```jsx
    let day = 3;
    
    switch (day) {
        case 1:
            console.log("Monday");
            break;
        case 2:
            console.log("Tuesday");
            break;
        case 3:
            console.log("Wednesday");
            break;
        default:
            console.log("Other day");
            break;
    }
    
    ```
    

## Loops

```jsx
let numbers = [1, 2, 3, 4, 5];

for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}

```

### Functions

1. **Regular function**
    
    ```jsx
    function showMessage(from, text) {
        console.log(from + ': ' + text);
    }
    
    showMessage('Ann', 'Hello!');
    showMessage('Ann', "What's up?");
    
    ```
    
2. **Function expression**
    
    ```jsx
    let sayHi = function() {
        console.log("Hello");
    };
    
    sayHi();
    
    ```
    
3. **Arrow function**
    
    ```jsx
    let sum = (a, b) => {
        return a + b;
    };
    
    console.log(sum(5, 10));
    
    ```
    

### Callback functions

Intended to be executed after a specific task or event

```jsx
function greet(name, callback) {
    console.log("Hello, " + name);
    callback();
}

function sayGoodbye() {
    console.log("Goodbye!");
}

greet("Mamad", sayGoodbye);

```

### Debugging

Process of finding and fixing errors in code

---

## XmlHttpRequest

cURL sends HTTP request in shell but XmlHttpRequest sends HTTP request in browser

### Difference between cURL and XmlHttpRequest:

- cURL is a binary executable but XmlHttpRequest is a built-in class in browsers

```jsx
var xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data");
// xhr.open("GET", "/"); ---> send a request to the root of the current domain

xhr.onreadystatechange = function() {
  if (xhr.readyState === 4) { 
   if (xhr.status === 200) {
      console.log(xhr.responseText);
    } else {
      console.error("Request failed with status:", xhr.status);
    }
  }
};

xhr.send(); 
```

### Explanation of `onreadystatechange`

- `onreadystatechange` is an **event handler** associated with the `XMLHttpRequest` object. It’s triggered each time the `readyState` property changes, representing the request's progress through different stages
    - **`readyState = 4`**: Request is complete, and the HTTP response has been fully received (other values include `0`, `1`, `2`, and `3` for earlier stages; see [MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState) for more details)

### **Callback Function as an Event Handler (like `onreadystatechange`)**

- In some cases, such as events, the callback function is assigned as a **property** of an object. For example, `onreadystatechange` is a property of the `XMLHttpRequest` object that points to a callback function

## Frames

To embed another web page within the current page

```html
<iframe src="https://memoryleaks.ir"></iframe>
```

## Same Origin Policy (SOP)

Is is a fundamental security feature

- Rules for different origins
- **origin**: schema://host:port

```jsx
window.origin;
```

### What is rule?

- One origin can not access or manipulate data from a different origin

---

## Post Message

Allows cross origin communication between different windows or iframes

### **Sending a message**: window or iframe that wants to send a message, the postMessage method to data to another window or iframe

```html
<!DOCTYPE html>
<html>
<head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Start</title>

        <script>
                var game_url = "http://127.0.0.1:8000/case1/index.html";
                function popup() {
                        window.test = open(game_url, "pop", "width=850,height=750,resizable=1");
                        setTimeout(msg, 1000);
                }
                function msg() {
                        window.test.postMessage(JSON.stringify({"readyToPlay": true, "name": "Voorivex"}), "*");
                }
        </script>
</head>
<body>

<h1>Start</h1>
<input type="button" value="Start" onclick="popup()" >

</body>
</html>
```

- **`window.test`**: Stores a reference to the new popup window created by `open()`, allowing control over it
- **`window.test.postMessage()`**: Sends a cross-origin message (JSON data) to `window.test` to share information securely

### **Receiving a message**: window or iframe what wants to  send a message, an event listener for the message event

```html
<!DOCTYPE html>
<html>
<head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>Some Site</title>

        <script>
                var postMessageHandler = function(e) {
                        // e.origin should be checked here
                        msg = JSON.parse(e.data)
                        if (msg.readyToPlay){
                                document.getElementById("fs").innerText = "Ready to showcase your SUDOKU skills Mr. " + msg.name;
                                if (msg.url){
                                        window.open(msg.url)
                                }
                        }
                        console.log(e.origin);
                        console.log(e.source);
                        console.log(e.data);
                }
                window.addEventListener("message", postMessageHandler, false);
        </script>

</head>
<body>

<h2 id="fs">Game is loading...</h2>
<img src="Sudoku.png">

</body>
</html>
```

- **`e.data`**: Contains the message data sent via `postMessage()`
- **`window.addEventListener("message", postMessageHandler, false)`**:
    - Listens for `"message"` events, which occur when a message is received from another window
    - The `postMessageHandler` function is triggered whenever a message is received

---

## Tasks

### **1. DOM Manipulation**

- open a random website, add the following tags by browser’s console
    - Image tag pointing to [this image](https://memoryleaks.ir/wp-content/themes/yashar/assets/img/logo.png), when it’s loaded, pop an alert
    
    ```jsx
    // Host: voorviex.academy
    
    document.getElementsByClassName("MuiBox-root css-jwi9ed")[0].innerHTML = "<img src='https://memoryleaks.ir/wp-content/themes/yashar/assets/img/logo.png' onload='alert(\"Yallah\")'>";
    ```
    
    - Script tag sourced to the [jQuery](https://code.jquery.com/jquery-3.6.0.min.js), when it’s loaded, use jQuery to update the DOM (change the title or anything else)
    
    ```jsx
    var jq = document.createElement('script');
    jq.src = "https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js";
    document.getElementsByTagName('head')[0].appendChild(jq);
    
    jQuery.noConflict();
    
    setTimeout(function() {
      jQuery("title").html('Yallah Navid'); 
    }, 2000);
    ```
    

### **2. XmlHttpRequest + DOM**

Write a JavaScript code to get data from [this](https://reqres.in/) REST API and update the DOM to show the data

```jsx
// Host: voorviex.academy

const xhr = new XMLHttpRequest();
xhr.open("GET", "https://reqres.in/api/users?page=2", true);

xhr.onreadystatechange = function() {
  if (xhr.readyState === 4 && xhr.status === 200) {
    const data = JSON.parse(xhr.responseText);
    document.getElementsByClassName("MuiBox-root css-jwi9ed")[0].innerHTML = `<p>${JSON.stringify(data)}</p>`;
  }
};

xhr.send();
```

### **3. User Information + XmlHttpRequest**

Write a code to get user’s information (such as IP address, browser info and etc) and send it to your server

[Flask-postMessage.zip](https://prod-files-secure.s3.us-west-2.amazonaws.com/eb72149f-aebd-46a2-b9ce-50e06d3ad55b/7126a43c-31bc-4ce5-b358-648444466d44/Flask-postMessage.zip)

```bash
unzip Flask-postMessage.zip -d . && pip3 install Flask flask-cors
```

### **4. Post Message**

Write a simple web application to handle the PostMessage, write the JavaScript code to send message to it-