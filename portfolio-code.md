# portfolio - full code

**What it is:** Plain HTML + CSS portfolio

**Files in this project:**
- `index.html`
- `style.css`

---

## index.html

````html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Divy Vaghasiya | Portfolio</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- ===== NAVIGATION ===== -->
  <header class="navbar">
    <a href="#home" class="logo">Divy<span>.</span></a>
    <nav>
      <a href="#about">About</a>
      <a href="#education">Education</a>
      <a href="#skills">Skills</a>
      <a href="#projects">Projects</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <!-- ===== HERO / INTRO ===== -->
    <section id="home" class="hero">
      <img src="profile.jpg" alt="Photo of Divy Vaghasiya" class="profile-pic">
      <div class="hero-text">
        <p class="greeting">Hello, I'm</p>
        <h1>Divy Vipulbhai Vaghasiya</h1>
        <p class="tagline">Student at SCET &middot; Aspiring Web Developer</p>
        <div class="hero-buttons">
          <a href="#projects" class="btn">View my work</a>
          <a href="#contact" class="btn btn-outline">Contact me</a>
        </div>
      </div>
    </section>

    <!-- ===== ABOUT ===== -->
    <section id="about">
      <h2>About Me</h2>
      <p>
        I'm Divy, a student at SCET (Sarvajanik College of Engineering &amp; Technology), Surat.
        I enjoy learning how websites are built and I'm currently learning
        HTML, CSS and JavaScript to create clean, responsive web pages.
        I like turning ideas into things people can actually use.
      </p>
    </section>

    <!-- ===== EDUCATION ===== -->
    <section id="education">
      <h2>Education</h2>
      <div class="card">
        <h3>Sarvajanik College of Engineering &amp; Technology (SCET)</h3>
        <p class="meta">Surat, Gujarat &middot; Currently studying</p>
        <!-- TODO: replace with your branch and years, e.g. "B.E. Computer Engineering · 2024 – 2028" -->
        <p>Your Degree / Branch &middot; Start year &ndash; End year</p>
      </div>
    </section>

    <!-- ===== SKILLS ===== -->
    <section id="skills">
      <h2>Skills</h2>
      <div class="skills">
        <span class="skill">HTML</span>
        <span class="skill">CSS</span>
        <span class="skill">JavaScript</span>
        <span class="skill">Responsive Design</span>
        <span class="skill">Flexbox &amp; Grid</span>
        <span class="skill">Using AI tools (Claude)</span>
      </div>
    </section>

    <!-- ===== PROJECTS ===== -->
    <section id="projects">
      <h2>Projects</h2>
      <div class="project-grid">
        <div class="card">
          <h3>Personal Portfolio</h3>
          <p>This one-page website, built with HTML and CSS. It works on phones and desktops.</p>
          <p class="meta">HTML &middot; CSS</p>
        </div>
        <!-- Copy this card for each new project you build -->
        <div class="card">
          <h3>Coming soon</h3>
          <p>My next JavaScript project will go here.</p>
          <p class="meta">JavaScript</p>
        </div>
      </div>
    </section>

    <!-- ===== CONTACT ===== -->
    <section id="contact">
      <h2>Contact</h2>
      <p>Want to connect or work together? Reach out!</p>
      <div class="contact-links">
        <!-- TODO: put your real links here -->
        <a href="mailto:your-email@example.com" class="btn">Email</a>
        <a href="https://github.com/your-username" target="_blank" class="btn btn-outline">GitHub</a>
        <a href="https://linkedin.com/in/your-username" target="_blank" class="btn btn-outline">LinkedIn</a>
      </div>
    </section>
  </main>

  <!-- ===== FOOTER ===== -->
  <footer>
    <p>&copy; 2026 Divy Vipulbhai Vaghasiya</p>
  </footer>

</body>
</html>
````

---

## style.css

````css
/* ===== BASIC SETUP ===== */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Colors stored in variables so you can change the theme in one place */
:root {
  --bg: #f5f7fa;
  --card: #ffffff;
  --text: #1f2937;
  --muted: #6b7280;
  --accent: #0f766e;       /* teal, matches the shirt in the photo */
  --accent-dark: #115e59;
}

html {
  scroll-behavior: smooth;  /* smooth scrolling when clicking nav links */
}

body {
  font-family: "Segoe UI", Arial, sans-serif;
  background: var(--bg);
  color: var(--text);
  line-height: 1.6;
}

/* ===== NAVBAR ===== */
.navbar {
  position: sticky;
  top: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 8%;
  background: var(--card);
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  z-index: 10;
}

.logo {
  font-size: 24px;
  font-weight: bold;
  color: var(--text);
  text-decoration: none;
}

.logo span {
  color: var(--accent);
}

nav a {
  margin-left: 24px;
  color: var(--muted);
  text-decoration: none;
  font-weight: 500;
}

nav a:hover {
  color: var(--accent);
}

/* ===== SECTIONS ===== */
section {
  max-width: 900px;
  margin: 0 auto;
  padding: 70px 20px;
}

h2 {
  font-size: 30px;
  margin-bottom: 20px;
  position: relative;
}

/* small colored line under each heading */
h2::after {
  content: "";
  display: block;
  width: 50px;
  height: 4px;
  background: var(--accent);
  border-radius: 2px;
  margin-top: 6px;
}

/* ===== HERO ===== */
.hero {
  display: flex;
  align-items: center;
  gap: 50px;
  min-height: 85vh;
}

.profile-pic {
  width: 240px;
  height: 240px;
  object-fit: cover;          /* crops the photo to fill the circle */
  object-position: center top;
  border-radius: 50%;
  border: 6px solid var(--card);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
}

.greeting {
  color: var(--accent);
  font-weight: 600;
  font-size: 18px;
}

.hero h1 {
  font-size: 42px;
  line-height: 1.2;
  margin: 6px 0 10px;
}

.tagline {
  color: var(--muted);
  font-size: 18px;
  margin-bottom: 24px;
}

/* ===== BUTTONS ===== */
.btn {
  display: inline-block;
  padding: 10px 22px;
  margin: 4px 8px 4px 0;
  background: var(--accent);
  color: white;
  border: 2px solid var(--accent);
  border-radius: 8px;
  text-decoration: none;
  font-weight: 600;
  transition: 0.2s;
}

.btn:hover {
  background: var(--accent-dark);
  border-color: var(--accent-dark);
}

.btn-outline {
  background: transparent;
  color: var(--accent);
}

.btn-outline:hover {
  color: white;
}

/* ===== CARDS ===== */
.card {
  background: var(--card);
  padding: 24px;
  border-radius: 12px;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.06);
}

.card h3 {
  margin-bottom: 6px;
}

.meta {
  color: var(--muted);
  font-size: 14px;
  margin-bottom: 8px;
}

/* ===== SKILLS ===== */
.skills {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}

.skill {
  background: var(--card);
  border: 2px solid var(--accent);
  color: var(--accent);
  padding: 8px 16px;
  border-radius: 999px;   /* pill shape */
  font-weight: 600;
}

/* ===== PROJECTS ===== */
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

/* ===== CONTACT ===== */
.contact-links {
  margin-top: 16px;
}

/* ===== FOOTER ===== */
footer {
  text-align: center;
  padding: 24px;
  color: var(--muted);
  border-top: 1px solid #e5e7eb;
}

/* ===== RESPONSIVE: PHONES ===== */
@media (max-width: 700px) {
  .navbar {
    flex-direction: column;
    gap: 8px;
    padding: 12px 16px;
  }

  nav a {
    margin: 0 8px;
    font-size: 14px;
  }

  .hero {
    flex-direction: column;
    text-align: center;
    gap: 24px;
    padding-top: 40px;
  }

  .profile-pic {
    width: 180px;
    height: 180px;
  }

  .hero h1 {
    font-size: 30px;
  }
}
````

