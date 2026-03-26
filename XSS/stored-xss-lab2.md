# Stored XSS - Lab 2

### Description
This lab demonstrates **Stored Cross-Site Scripting (XSS)**. Unlike reflected XSS, the malicious script is saved on the web server (in this case, as a comment) and is executed in the browser of anyone who views the affected page.

### Vulnerable Parameter
* **Field:** Comment Textarea
* **Page:** Blog Post View (`/post?postId=2`)

### Payload Used
```html
<script>alert(1)</script>
