
# Reflected XSS - Lab 3 (Attribute Breakout)

### Description
This lab demonstrates a **Reflected Cross-Site Scripting (XSS)** vulnerability. 

### Vulnerable Parameter
* **Parameter:** `search`
* **Vulnerable URL:** `/?search="><script>alert(1)</script>`

### Payload Used
```html
"><script>alert(1)</script>
```
Steps to Reproduce
Navigate to the home page of the vulnerable application.

In the search bar, enter the following breakout payload: "><script>alert(1)</script>.

The "> characters close the current HTML attribute and tag.

Click the Search button.

An alert box with "1" appears.

Proof of Concept
![Reflected XSS Proof](reflected-xss-proof-2.PNG)


