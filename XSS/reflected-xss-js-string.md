# Reflected XSS - JavaScript String Angle Brackets HTML-Encoded

### Description
This lab demonstrates a **Reflected XSS** vulnerability where angle brackets `< >` are encoded by the server, but the input is reflected inside a JavaScript string. I bypassed the encoding by using a single quote to break out of the string literal and execute JavaScript directly.

### Vulnerable Parameter
* **Parameter:** `search`
* **Vulnerable URL:** `/?search='-alert(1)-'`

### Payload Used
```javascript
'-alert(1)-'
```
Steps to Reproduce
Search for a random string and inspect the page source.

Observe that the search term is reflected inside a JavaScript block: var searchTerms = 'YOUR_INPUT';.

Input the payload '-alert(1)-' into the search bar.

The resulting code becomes var searchTerms = ''-alert(1)-'';, which is valid JavaScript that executes the alert.

An alert box with "1" appears on the screen.
proof of concept
![reflected xss js string][reflected-xss-js-string.PNG)

