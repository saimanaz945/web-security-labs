# DOM-based XSS - jQuery Anchor href Sink

### Description
This lab demonstrates a **DOM-based XSS** vulnerability. The application uses a jQuery selector to update the `href` attribute of an anchor element using data from the `location.search` source (the `returnPath` parameter).

### Vulnerable Source & Sink
* **Source:** `location.search` (URL parameter `returnPath`)
* **Sink:** jQuery `.attr("href", ...)`
* **Vulnerable URL:** `/feedback?returnPath=javascript:alert(document.cookie)`

### Payload Used
```javascript
javascript:alert(document.cookie)
Steps to Reproduce
Go to the Feedback page of the lab.

Observe the URL contains a returnPath parameter.

Modify the URL parameter to: ?returnPath=javascript:alert(document.cookie).

Press Enter to load the modified URL.

Click the "Back" link on the page.

An alert box showing your session cookies will appear.

Proof of Concept

