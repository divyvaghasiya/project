# responsive-demo - full code

**What it is:** Responsive design demo (HTML + CSS)

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
  <!-- STEP 1: the viewport tag makes phones use their real screen width -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Responsive Demo</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- Shows which layout is active. Resize the window to watch it change. -->
  <div class="screen-badge"></div>

  <!-- ===== NAVBAR (flex) ===== -->
  <header class="navbar">
    <a href="#" class="logo">Travel<span>Go</span></a>
    <nav>
      <a href="#places">Places</a>
      <a href="#features">Features</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <main>
    <!-- ===== HERO (flex: side by side on desktop, stacked on phone) ===== -->
    <section class="hero">
      <div class="hero-text">
        <h1>Explore the world with us</h1>
        <p>This page is a responsive demo. Make the window narrower or open it
           on your phone and watch the layout change.</p>
        <a href="#places" class="btn">See places</a>
      </div>
      <img src="https://picsum.photos/id/1036/600/400" alt="Mountains and lake">
    </section>

    <!-- ===== PLACES (grid: 3 → 2 → 1 columns automatically) ===== -->
    <section id="places">
      <h2>Popular places</h2>
      <div class="cards">
        <div class="card">
          <img src="https://picsum.photos/id/1018/400/250" alt="Mountains">
          <h3>Mountains</h3>
          <p>Fresh air, big views and long hikes.</p>
        </div>
        <div class="card">
          <img src="https://picsum.photos/id/1015/400/250" alt="River valley">
          <h3>Rivers</h3>
          <p>Calm water and green valleys.</p>
        </div>
        <div class="card">
          <img src="https://picsum.photos/id/1040/400/250" alt="Old castle">
          <h3>Old towns</h3>
          <p>History, castles and narrow streets.</p>
        </div>
        <div class="card">
          <img src="https://picsum.photos/id/1043/400/250" alt="Forest">
          <h3>Forests</h3>
          <p>Quiet trails under tall trees.</p>
        </div>
        <div class="card">
          <img src="https://picsum.photos/id/1011/400/250" alt="Lake with boat">
          <h3>Lakes</h3>
          <p>Boating, swimming and sunsets.</p>
        </div>
        <div class="card">
          <img src="https://picsum.photos/id/1039/400/250" alt="Waterfall">
          <h3>Waterfalls</h3>
          <p>Loud, misty and beautiful.</p>
        </div>
      </div>
    </section>

    <!-- ===== FEATURES (flex with wrap) ===== -->
    <section id="features">
      <h2>Why choose us</h2>
      <div class="features">
        <div class="feature"><span>✈️</span> Cheap flights</div>
        <div class="feature"><span>🏨</span> Great hotels</div>
        <div class="feature"><span>🗺️</span> Local guides</div>
        <div class="feature"><span>💬</span> 24/7 support</div>
      </div>
    </section>

    <!-- ===== CONTACT FORM (two columns on desktop, one on phone) ===== -->
    <section id="contact">
      <h2>Contact us</h2>
      <form class="contact-form" onsubmit="event.preventDefault(); alert('Demo only, nothing was sent.');">
        <input type="text" placeholder="Your name">
        <input type="email" placeholder="Your email">
        <textarea rows="4" placeholder="Your message"></textarea>
        <button type="submit" class="btn">Send</button>
      </form>
    </section>
  </main>

  <footer>
    <p>Responsive demo &middot; made with HTML &amp; CSS</p>
  </footer>

</body>
</html>
````

---

## style.css

````css
/* =========================================
   RESPONSIVE DEMO
   Desktop styles come first.
   Tablet and phone changes are at the bottom.
   ========================================= */

/* ===== RESET ===== */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --accent: #2563eb;      /* blue */
  --bg: #f8fafc;
  --text: #0f172a;
  --muted: #64748b;
}

body {
  font-family: "Segoe UI", Arial, sans-serif;
  background: var(--bg);
  color: var(--text);
  line-height: 1.6;
}

/* STEP 3: images never overflow their box */
img {
  max-width: 100%;
  height: auto;
  display: block;
}

/* STEP 2: flexible width — fills the screen but never wider than 1100px */
section {
  width: 100%;
  max-width: 1100px;
  margin: 0 auto;
  padding: 50px 20px;
}

h2 {
  font-size: 30px;
  margin-bottom: 24px;
}

/* ===== SCREEN BADGE (shows the current layout) ===== */
.screen-badge {
  position: fixed;
  bottom: 16px;
  right: 16px;
  background: #111827;
  color: white;
  padding: 6px 14px;
  border-radius: 999px;
  font-size: 14px;
  z-index: 100;
}
.screen-badge::after {
  content: "💻 Desktop layout";
}

/* ===== NAVBAR (flex) ===== */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 5%;
  background: white;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.06);
  position: sticky;
  top: 0;
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

/* ===== HERO (flex: side by side) ===== */
.hero {
  display: flex;
  align-items: center;
  gap: 40px;
}

.hero-text {
  flex: 1;              /* text takes half the space */
}

.hero img {
  flex: 1;              /* image takes the other half */
  min-width: 0;         /* allows the image to shrink */
  border-radius: 16px;
}

.hero h1 {
  font-size: 48px;
  line-height: 1.2;
  margin-bottom: 16px;
}

.hero p {
  color: var(--muted);
  font-size: 18px;
  margin-bottom: 24px;
}

.btn {
  display: inline-block;
  background: var(--accent);
  color: white;
  padding: 12px 24px;
  border: none;
  border-radius: 8px;
  text-decoration: none;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
}
.btn:hover {
  opacity: 0.9;
}

/* ===== CARDS (STEP 4: grid that picks its own column count) ===== */
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);   /* 3 columns on desktop */
  gap: 20px;
}

.card {
  background: white;
  border-radius: 12px;
  overflow: hidden;      /* keeps the image inside the rounded corners */
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.06);
}
.card h3 {
  padding: 16px 16px 4px;
}
.card p {
  padding: 0 16px 16px;
  color: var(--muted);
}

/* ===== FEATURES (flex with wrap) ===== */
.features {
  display: flex;
  flex-wrap: wrap;       /* move to the next line when there's no room */
  gap: 16px;
}

.feature {
  flex: 1 1 200px;       /* grow, shrink, start at 200px wide */
  background: white;
  padding: 24px;
  border-radius: 12px;
  text-align: center;
  font-weight: 600;
  box-shadow: 0 4px 14px rgba(0, 0, 0, 0.06);
}
.feature span {
  display: block;
  font-size: 32px;
  margin-bottom: 8px;
}

/* ===== CONTACT FORM (grid: 2 columns) ===== */
.contact-form {
  display: grid;
  grid-template-columns: 1fr 1fr;   /* name and email side by side */
  gap: 16px;
}

.contact-form input,
.contact-form textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #cbd5e1;
  border-radius: 8px;
  font: inherit;
}

.contact-form textarea,
.contact-form button {
  grid-column: span 2;   /* take the full width (both columns) */
}

/* ===== FOOTER ===== */
footer {
  text-align: center;
  padding: 24px;
  color: var(--muted);
  border-top: 1px solid #e2e8f0;
}


/* =========================================
   STEP 5: MEDIA QUERIES
   ========================================= */

/* ---------- TABLET (1024px and below) ---------- */
@media (max-width: 1024px) {
  .screen-badge::after {
    content: "📱 Tablet layout";
  }

  /* Hero: stack it. Image on top (full width), text centered below */
  .hero {
    flex-direction: column-reverse;
    text-align: center;
    gap: 28px;
  }
  .hero img {
    width: 100%;
    max-height: 340px;
    object-fit: cover;     /* crop instead of stretching */
  }
  .hero p {
    max-width: 560px;
    margin-left: auto;     /* center the paragraph */
    margin-right: auto;
  }
  .hero h1 {
    font-size: 38px;
  }

  /* Cards: 3 → 2 columns */
  .cards {
    grid-template-columns: repeat(2, 1fr);
  }

  /* Features: neat 2 × 2 instead of 3 + 1 */
  .feature {
    flex: 1 1 calc(50% - 8px);   /* half the row minus half the gap */
  }
}

/* ---------- PHONE (600px and below) ---------- */
@media (max-width: 600px) {
  .screen-badge::after {
    content: "📱 Phone layout";
  }

  /* Navbar: logo above links */
  .navbar {
    flex-direction: column;
    gap: 8px;
  }
  nav a {
    margin: 0 10px;
  }

  /* Hero: already stacked by the tablet rules; just tighten it */
  .hero {
    gap: 24px;
    padding-top: 24px;
  }
  .hero img {
    max-height: 220px;
  }
  .hero h1 {
    font-size: 30px;
  }

  /* Cards: 2 → 1 column */
  .cards {
    grid-template-columns: 1fr;
  }

  /* Form: everything in one column */
  .contact-form {
    grid-template-columns: 1fr;
  }
  .contact-form textarea,
  .contact-form button {
    grid-column: span 1;
  }

  /* Smaller section spacing */
  section {
    padding: 36px 16px;
  }
  h2 {
    font-size: 24px;
  }
}
````

