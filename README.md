# Nexus Tasks (Vulnerable Todo App)

This is a deliberately vulnerable Todo web application built for an educational demonstration of **Stored Cross-Site Scripting (XSS)**. 

**Disclaimer: This application contains intentional security flaws and should only be run locally for educational purposes.**

## Features
- Add tasks to an in-memory database.
- Click tasks to visually strike them out and remove them from the server.
- "Clear All Tasks" functionality to instantly reset the application state.
- **Intentional Stored XSS Vulnerability**: Task inputs are completely unsanitized before being rendered to the DOM, allowing arbitrary JavaScript execution.
- Separated modular structure with isolated HTML, CSS, and Client-side JS.

## Tech Stack
- **Backend:** Node.js, Express.js
- **Frontend:** Vanilla HTML, CSS (Glassmorphism Design), JavaScript

## How to Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/aviralawasthi-iiita/todo-app.git
   cd todo-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the local server:
   ```bash
   node server.js
   ```

4. Open your browser and navigate to `http://localhost:3000`.

## XSS Demonstration Proof of Concepts

To demonstrate the vulnerability, try adding any of the following payloads as a new task:

**The Classic Alert Box:**
```html
<script>alert('Stored XSS execution successful!');</script>
```

**Page Defacement (DOM Manipulation):**
```html
<script>
  document.body.style.background = 'red';
  document.body.innerHTML = '<h1 style="color:white;text-align:center;margin-top:20vh;">This page has been taken over.</h1>';
</script>
```
*(Note: If the page is completely defaced, you can reset the app by sending a POST request to `/clear-todos` or by restarting the node server.)*

## Demonstration Video

[\[Insert Google Drive Link to 10-Minute Video Here\]](https://drive.google.com/drive/folders/18QPZQMgE8muq6oY51tgjw3wQSI5dSoL4?usp=drive_link)
