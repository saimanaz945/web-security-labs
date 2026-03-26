# Stored XSS - Lab 2

### Description
This lab demonstrates **Stored Cross-Site Scripting (XSS)**. Unlike reflected XSS, the malicious script is saved on the web server (in this case, as a comment) and is executed in the browser of anyone who views the affected page.

### Vulnerable Parameter
* **Field:** Comment Textarea
* **Page:** Blog Post View (`/post?postId=2`)

10. ### Payload Used
11. ```html
12. <script>alert(1)</script>
13. ```  <-- ADD THIS HERE TO TURN OFF THE GRAY BOX
14. 
15. ### Steps to Reproduce
16. 1. Go to the blog post located at `/post?postId=2`.
17. 2. Scroll down to the **"Leave a comment"** section.
...
22. ### Proof of Concept
23. ![Stored XSS Proof](stored-xss-proof.PNG)
