# simple-portfolio - full code

**What it is:** Simple React + Vite portfolio (useState, useEffect, useContext)

**Files in this project:**
- `index.html`
- `package.json`
- `vite.config.js`
- `src/main.jsx`
- `src/App.jsx`
- `src/App.css`

---

## index.html

````html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Divy | Portfolio</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
````

---

## package.json

````json
{
  "name": "simple-portfolio",
  "private": true,
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build"
  },
  "dependencies": {
    "react": "^19.1.0",
    "react-dom": "^19.1.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^5.0.0",
    "vite": "^7.0.0"
  }
}
````

---

## vite.config.js

````javascript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
````

---

## src/main.jsx

````jsx
import { createRoot } from "react-dom/client";
import App from "./App";
import "./App.css";

createRoot(document.getElementById("root")).render(<App />);
````

---

## src/App.jsx

````jsx
import { createContext, useContext, useEffect, useState } from "react";

// ----- YOUR INFO (change these) -----
const name = "Divy Vaghasiya";
const phone = "+91 00000 00000";
const email = "your-email@example.com";

const skills = ["HTML", "CSS", "JavaScript", "React", "Vite", "Git"];

const projects = [
  { title: "Portfolio Website", text: "This website, made with React and Vite." },
  { title: "Todo App", text: "Add and manage daily tasks using React state." },
  { title: "Calculator", text: "A simple calculator made with JavaScript." },
];

// ===== useContext STEP 1: create a context (a shared "box" for the theme) =====
const ThemeContext = createContext();

// ----- NAVBAR (a child component) -----
function Navbar() {
  // useContext STEP 3: read the theme from the box. No props needed!
  const { dark, toggleTheme } = useContext(ThemeContext);

  return (
    <nav className="navbar">
      <h2>Divy.</h2>
      <div className="links">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#projects">Projects</a>
        <a href="#contact">Contact</a>
        <button className="theme-btn" onClick={toggleTheme}>
          {dark ? "☀️ Light" : "🌙 Dark"}
        </button>
      </div>
    </nav>
  );
}

// ----- FOOTER (another child that also reads the context) -----
function Footer() {
  const { dark } = useContext(ThemeContext);
  return (
    <footer>
      © 2026 {name} · {dark ? "Dark" : "Light"} mode
    </footer>
  );
}

// ----- THE WEBSITE -----
export default function App() {
  // ===== useState: the component's memory =====
  const [dark, setDark] = useState(false); // is dark mode on?
  const [message, setMessage] = useState(""); // text typed in the contact box
  const [sent, setSent] = useState(false); // has the form been sent?

  // ===== useEffect #1: runs every time "dark" changes =====
  // It adds or removes the "dark" class on <body>, so the CSS can change colors.
  useEffect(() => {
    document.body.className = dark ? "dark" : "";
  }, [dark]);

  // ===== useEffect #2: runs every time "sent" changes =====
  // After sending, hide the "Thanks" message after 3 seconds.
  useEffect(() => {
    if (!sent) return; // do nothing if not sent
    const timer = setTimeout(() => setSent(false), 3000);
    return () => clearTimeout(timer); // cleanup: cancel the timer if needed
  }, [sent]);

  function toggleTheme() {
    setDark(!dark); // flip true <-> false
  }

  function handleSubmit(e) {
    e.preventDefault(); // stop the page from reloading
    setSent(true);
    setMessage("");
  }

  return (
    // ===== useContext STEP 2: the Provider shares { dark, toggleTheme } with every child =====
    <ThemeContext.Provider value={{ dark, toggleTheme }}>
      <Navbar />

      {/* HOME */}
      <section id="home" className="home">
        <img src="/photo.webp" alt={"Photo of " + name} />
        <h1>Hi, I'm {name}</h1>
        <p>Student at SCET, Surat · Aspiring Web Developer</p>
      </section>

      {/* ABOUT */}
      <section id="about">
        <h2>About Me</h2>
        <p>
          I'm a student at SCET, Surat. I'm learning HTML, CSS, JavaScript and
          React, and I love building websites.
        </p>
      </section>

      {/* SKILLS */}
      <section id="skills">
        <h2>Skills</h2>
        <div className="skills">
          {skills.map((skill) => (
            <span key={skill}>{skill}</span>
          ))}
        </div>
      </section>

      {/* PROJECTS */}
      <section id="projects">
        <h2>Projects</h2>
        <div className="projects">
          {projects.map((project) => (
            <div key={project.title} className="card">
              <h3>{project.title}</h3>
              <p>{project.text}</p>
            </div>
          ))}
        </div>
      </section>

      {/* CONTACT */}
      <section id="contact">
        <h2>Contact</h2>
        <p>📞 {phone}</p>
        <p>✉️ {email}</p>

        <form onSubmit={handleSubmit}>
          <textarea
            placeholder="Write a message..."
            value={message}
            onChange={(e) => setMessage(e.target.value)}
            required
          />
          <button type="submit">Send</button>
        </form>

        {sent && <p className="thanks">Thanks for your message!</p>}
      </section>

      <Footer />
    </ThemeContext.Provider>
  );
}
````

---

## src/App.css

````css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: Arial, sans-serif;
  color: #333;
  background: #f5f7fb;
  line-height: 1.6;
}

/* NAVBAR */
.navbar {
  position: sticky;
  top: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 8px;
  padding: 16px 24px;
  background: #4f46e5;
  color: white;
}

.navbar a {
  color: white;
  text-decoration: none;
  margin-left: 16px;
}

.navbar a:hover {
  text-decoration: underline;
}

/* SECTIONS */
section {
  max-width: 900px;
  margin: 0 auto;
  padding: 60px 16px;
  text-align: center;
}

section h2 {
  font-size: 2rem;
  color: #4f46e5;
  margin-bottom: 20px;
}

/* HOME */
.home img {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  object-fit: cover;
  object-position: center 20%;
  border: 5px solid white;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.15);
}

.home h1 {
  margin: 20px 0 8px;
  font-size: 2.2rem;
}

/* SKILLS */
.skills {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 10px;
}

.skills span {
  background: #4f46e5;
  color: white;
  padding: 8px 18px;
  border-radius: 20px;
}

/* PROJECTS */
.projects {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
}

.card {
  background: white;
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.card h3 {
  margin-bottom: 8px;
}

/* CONTACT */
form {
  display: flex;
  flex-direction: column;
  gap: 12px;
  max-width: 400px;
  margin: 20px auto 0;
}

textarea {
  height: 100px;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 8px;
  font-family: inherit;
}

button {
  padding: 12px;
  background: #4f46e5;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1rem;
  cursor: pointer;
}

button:hover {
  background: #4338ca;
}

.thanks {
  margin-top: 12px;
  color: green;
}

/* FOOTER */
footer {
  text-align: center;
  padding: 20px;
  background: #222;
  color: white;
}

/* THEME BUTTON (in the navbar) */
.theme-btn {
  margin-left: 16px;
  padding: 6px 14px;
  background: white;
  color: #4f46e5;
  border-radius: 20px;
  font-size: 0.9rem;
}

.theme-btn:hover {
  background: #e0e7ff;
}

/* DARK MODE: used when <body> has class="dark" (set by useEffect) */
body {
  transition: background 0.3s, color 0.3s;
}

body.dark {
  background: #111827;
  color: #e5e7eb;
}

body.dark section h2 {
  color: #818cf8;
}

body.dark .card {
  background: #1f2937;
}

body.dark textarea {
  background: #1f2937;
  color: #e5e7eb;
  border-color: #374151;
}

body.dark .home img {
  border-color: #1f2937;
}

body.dark footer {
  background: #000;
}
````

