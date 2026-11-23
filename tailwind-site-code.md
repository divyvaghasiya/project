# tailwind-site - full code

**What it is:** Tailwind CSS site

**Files in this project:**
- `index.html`

---

## index.html

````html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <!-- This line is REQUIRED for responsive design: it makes phones use their real width -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Chai Corner – Café</title>

  <!-- Tailwind CSS v4 (Play CDN – fine for learning, use npm + Vite for real projects) -->
  <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>

  <!-- Our own Tailwind settings: custom colors, font and class-based dark mode -->
  <style type="text/tailwindcss">
    @custom-variant dark (&:where(.dark, .dark *));

    @theme {
      --color-brand-50:  #fff7ed;
      --color-brand-100: #ffedd5;
      --color-brand-500: #f97316;
      --color-brand-600: #ea580c;
      --color-brand-700: #c2410c;
      --font-display: "Georgia", serif;
    }
  </style>
</head>

<body class="bg-white text-slate-800 dark:bg-slate-900 dark:text-slate-100 transition-colors">

  <!-- ================= NAVBAR ================= -->
  <header class="sticky top-0 z-50 bg-white/80 dark:bg-slate-900/80 backdrop-blur border-b border-slate-200 dark:border-slate-700">
    <nav class="max-w-6xl mx-auto px-4 h-16 flex items-center justify-between">
      <a href="#" class="font-display text-2xl font-bold text-brand-600">☕ Chai Corner</a>

      <!-- Desktop links: hidden on phones, shown from md (768px) and up -->
      <ul class="hidden md:flex items-center gap-8 font-medium">
        <li><a href="#menu" class="hover:text-brand-600 transition">Menu</a></li>
        <li><a href="#about" class="hover:text-brand-600 transition">About</a></li>
        <li><a href="#reviews" class="hover:text-brand-600 transition">Reviews</a></li>
        <li><a href="#contact" class="hover:text-brand-600 transition">Contact</a></li>
      </ul>

      <div class="flex items-center gap-2">
        <!-- Dark mode button -->
        <button id="themeBtn" class="p-2 rounded-full hover:bg-slate-100 dark:hover:bg-slate-800 transition" aria-label="Toggle dark mode">
          <span class="dark:hidden">🌙</span>
          <span class="hidden dark:inline">☀️</span>
        </button>

        <!-- Hamburger button: only visible on phones -->
        <button id="menuBtn" class="md:hidden p-2 rounded hover:bg-slate-100 dark:hover:bg-slate-800 text-2xl" aria-label="Open menu">☰</button>
      </div>
    </nav>

    <!-- Mobile menu: hidden until the ☰ button is clicked; never shown on md+ -->
    <ul id="mobileMenu" class="hidden md:hidden flex-col gap-1 px-4 pb-4 font-medium">
      <li><a href="#menu" class="block py-2 px-3 rounded hover:bg-brand-50 dark:hover:bg-slate-800">Menu</a></li>
      <li><a href="#about" class="block py-2 px-3 rounded hover:bg-brand-50 dark:hover:bg-slate-800">About</a></li>
      <li><a href="#reviews" class="block py-2 px-3 rounded hover:bg-brand-50 dark:hover:bg-slate-800">Reviews</a></li>
      <li><a href="#contact" class="block py-2 px-3 rounded hover:bg-brand-50 dark:hover:bg-slate-800">Contact</a></li>
    </ul>
  </header>

  <main>
    <!-- ================= HERO ================= -->
    <section class="bg-gradient-to-br from-brand-50 to-brand-100 dark:from-slate-800 dark:to-slate-900">
      <!-- 1 column on phones, 2 columns from md up -->
      <div class="max-w-6xl mx-auto px-4 py-16 md:py-24 grid md:grid-cols-2 gap-10 items-center">
        <div class="text-center md:text-left">
          <p class="text-brand-600 font-semibold uppercase tracking-wider text-sm">Fresh every morning</p>
          <!-- Text gets bigger on bigger screens -->
          <h1 class="mt-3 font-display text-4xl sm:text-5xl lg:text-6xl font-bold leading-tight">
            Your daily cup of <span class="text-brand-600">happiness</span>
          </h1>
          <p class="mt-5 text-lg text-slate-600 dark:text-slate-300 max-w-md mx-auto md:mx-0">
            Hand-brewed masala chai, fresh coffee and warm snacks in a cozy corner of the city.
          </p>
          <!-- Buttons stack on phones, sit side by side from sm up -->
          <div class="mt-8 flex flex-col sm:flex-row gap-3 justify-center md:justify-start">
            <a href="#menu" class="bg-brand-600 hover:bg-brand-700 text-white font-semibold px-6 py-3 rounded-full shadow-lg hover:shadow-xl hover:-translate-y-0.5 transition">
              See the Menu
            </a>
            <a href="#contact" class="border-2 border-brand-600 text-brand-600 hover:bg-brand-600 hover:text-white font-semibold px-6 py-3 rounded-full transition">
              Visit Us
            </a>
          </div>
        </div>

        <!-- Big emoji "illustration" -->
        <div class="flex justify-center">
          <div class="w-64 h-64 sm:w-80 sm:h-80 rounded-full bg-white dark:bg-slate-700 shadow-2xl flex items-center justify-center text-[8rem] sm:text-[10rem] animate-[bounce_3s_infinite]">
            🍵
          </div>
        </div>
      </div>
    </section>

    <!-- ================= MENU ================= -->
    <section id="menu" class="max-w-6xl mx-auto px-4 py-16 md:py-24 scroll-mt-16">
      <div class="text-center max-w-2xl mx-auto">
        <h2 class="font-display text-3xl sm:text-4xl font-bold">Our Menu</h2>
        <p class="mt-3 text-slate-600 dark:text-slate-300">Made fresh, served with love.</p>
      </div>

      <!-- Responsive grid: 1 → 2 → 3 → 4 columns as the screen grows -->
      <div id="menuGrid" class="mt-12 grid gap-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4"></div>
    </section>

    <!-- ================= ABOUT ================= -->
    <section id="about" class="bg-slate-50 dark:bg-slate-800 scroll-mt-16">
      <div class="max-w-6xl mx-auto px-4 py-16 md:py-24 grid lg:grid-cols-2 gap-12 items-center">
        <div>
          <h2 class="font-display text-3xl sm:text-4xl font-bold">Brewing since 2015</h2>
          <p class="mt-4 text-slate-600 dark:text-slate-300 leading-relaxed">
            What started as a tiny tea stall is now a favorite hangout for students, artists and anyone
            who needs a break. We use local spices, fresh milk and recipes passed down through our family.
          </p>
          <ul class="mt-6 space-y-3">
            <li class="flex items-center gap-3"><span class="text-brand-600">✔</span> Locally sourced ingredients</li>
            <li class="flex items-center gap-3"><span class="text-brand-600">✔</span> Free Wi-Fi and charging spots</li>
            <li class="flex items-center gap-3"><span class="text-brand-600">✔</span> Open 7 days a week</li>
          </ul>
        </div>

        <!-- Stats: 2 columns on phones, 4 on small screens, back to 2 next to the text on large screens -->
        <div class="grid grid-cols-2 sm:grid-cols-4 lg:grid-cols-2 gap-4">
          <div class="bg-white dark:bg-slate-900 rounded-2xl p-6 text-center shadow-sm">
            <p class="text-3xl sm:text-4xl font-bold text-brand-600">10+</p>
            <p class="mt-1 text-sm text-slate-500 dark:text-slate-400">Years</p>
          </div>
          <div class="bg-white dark:bg-slate-900 rounded-2xl p-6 text-center shadow-sm">
            <p class="text-3xl sm:text-4xl font-bold text-brand-600">25</p>
            <p class="mt-1 text-sm text-slate-500 dark:text-slate-400">Drinks</p>
          </div>
          <div class="bg-white dark:bg-slate-900 rounded-2xl p-6 text-center shadow-sm">
            <p class="text-3xl sm:text-4xl font-bold text-brand-600">50k</p>
            <p class="mt-1 text-sm text-slate-500 dark:text-slate-400">Cups served</p>
          </div>
          <div class="bg-white dark:bg-slate-900 rounded-2xl p-6 text-center shadow-sm">
            <p class="text-3xl sm:text-4xl font-bold text-brand-600">4.8★</p>
            <p class="mt-1 text-sm text-slate-500 dark:text-slate-400">Rating</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ================= REVIEWS ================= -->
    <section id="reviews" class="max-w-6xl mx-auto px-4 py-16 md:py-24 scroll-mt-16">
      <h2 class="text-center font-display text-3xl sm:text-4xl font-bold">What people say</h2>

      <!-- 1 column on phones, 3 from md up -->
      <div class="mt-12 grid md:grid-cols-3 gap-6">
        <figure class="p-6 rounded-2xl border border-slate-200 dark:border-slate-700 hover:shadow-lg transition">
          <p class="text-yellow-500">★★★★★</p>
          <blockquote class="mt-3 text-slate-600 dark:text-slate-300">"The best masala chai I've had outside my grandmother's kitchen."</blockquote>
          <figcaption class="mt-4 font-semibold">— Aarav, student</figcaption>
        </figure>
        <figure class="p-6 rounded-2xl border border-slate-200 dark:border-slate-700 hover:shadow-lg transition">
          <p class="text-yellow-500">★★★★★</p>
          <blockquote class="mt-3 text-slate-600 dark:text-slate-300">"Quiet, cozy and great Wi-Fi. My favorite place to work."</blockquote>
          <figcaption class="mt-4 font-semibold">— Meera, designer</figcaption>
        </figure>
        <figure class="p-6 rounded-2xl border border-slate-200 dark:border-slate-700 hover:shadow-lg transition">
          <p class="text-yellow-500">★★★★☆</p>
          <blockquote class="mt-3 text-slate-600 dark:text-slate-300">"Samosas are crispy and hot every single time. Friendly staff too!"</blockquote>
          <figcaption class="mt-4 font-semibold">— Kabir, engineer</figcaption>
        </figure>
      </div>
    </section>

    <!-- ================= CONTACT ================= -->
    <section id="contact" class="bg-brand-600 text-white scroll-mt-16">
      <div class="max-w-6xl mx-auto px-4 py-16 md:py-24 grid md:grid-cols-2 gap-12">
        <div>
          <h2 class="font-display text-3xl sm:text-4xl font-bold">Visit or message us</h2>
          <p class="mt-4 text-brand-100">We'd love to hear from you. Reserve a table or ask us anything.</p>
          <div class="mt-8 space-y-3">
            <p>📍 12 MG Road, Pune</p>
            <p>🕗 Mon–Sun: 7 AM – 10 PM</p>
            <p>📞 +91 00000 00000</p>
          </div>
        </div>

        <form id="contactForm" class="bg-white dark:bg-slate-900 text-slate-800 dark:text-slate-100 rounded-2xl p-6 sm:p-8 shadow-2xl space-y-4">
          <!-- Name + email side by side from sm up -->
          <div class="grid sm:grid-cols-2 gap-4">
            <label class="block">
              <span class="text-sm font-medium">Name</span>
              <input required type="text" class="mt-1 w-full rounded-lg border border-slate-300 dark:border-slate-600 bg-transparent px-3 py-2 focus:outline-none focus:ring-2 focus:ring-brand-500">
            </label>
            <label class="block">
              <span class="text-sm font-medium">Email</span>
              <input required type="email" class="peer mt-1 w-full rounded-lg border border-slate-300 dark:border-slate-600 bg-transparent px-3 py-2 focus:outline-none focus:ring-2 focus:ring-brand-500">
              <!-- Shown automatically when the email is invalid (Tailwind "peer" trick) -->
              <span class="hidden peer-user-invalid:block mt-1 text-xs text-red-500">Please enter a valid email.</span>
            </label>
          </div>
          <label class="block">
            <span class="text-sm font-medium">Message</span>
            <textarea required rows="4" class="mt-1 w-full rounded-lg border border-slate-300 dark:border-slate-600 bg-transparent px-3 py-2 focus:outline-none focus:ring-2 focus:ring-brand-500"></textarea>
          </label>
          <button type="submit" class="w-full bg-brand-600 hover:bg-brand-700 text-white font-semibold py-3 rounded-lg transition active:scale-95">
            Send Message
          </button>
          <p id="formMsg" class="hidden text-center text-green-600 font-medium">✅ Thanks! We'll get back to you soon.</p>
        </form>
      </div>
    </section>
  </main>

  <!-- ================= FOOTER ================= -->
  <footer class="bg-slate-900 text-slate-400">
    <!-- Stacks on phones, one row from sm up -->
    <div class="max-w-6xl mx-auto px-4 py-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-sm">
      <p>© <span id="year"></span> Chai Corner. Made with Tailwind CSS.</p>
      <div class="flex gap-6">
        <a href="#" class="hover:text-white transition">Instagram</a>
        <a href="#" class="hover:text-white transition">Twitter</a>
        <a href="#" class="hover:text-white transition">Facebook</a>
      </div>
    </div>
  </footer>

  <!-- ================= JAVASCRIPT ================= -->
  <script>
    // 1. Menu data: the cards are created from this list (no repeated HTML!)
    const menuItems = [
      { emoji: "🍵", name: "Masala Chai",    desc: "Spiced tea with ginger and cardamom.", price: 40,  tag: "Bestseller" },
      { emoji: "☕", name: "Filter Coffee",  desc: "Strong South Indian style coffee.",    price: 60,  tag: "" },
      { emoji: "🧋", name: "Cold Coffee",    desc: "Chilled, creamy and a little sweet.",  price: 120, tag: "New" },
      { emoji: "🥟", name: "Samosa (2 pcs)", desc: "Crispy pastry with spicy potato.",     price: 50,  tag: "" },
      { emoji: "🥪", name: "Grilled Sandwich", desc: "Veggies and cheese, toasted golden.", price: 110, tag: "" },
      { emoji: "🍪", name: "Butter Cookies", desc: "Baked fresh every morning.",          price: 70,  tag: "" },
      { emoji: "🥤", name: "Mango Lassi",    desc: "Thick yogurt drink with ripe mango.",  price: 90,  tag: "Seasonal" },
      { emoji: "🍰", name: "Chocolate Cake", desc: "Rich, moist slice with ganache.",      price: 140, tag: "" },
    ];

    // 2. Turn each item into a card and put all cards in the grid
    const menuGrid = document.querySelector("#menuGrid");
    menuGrid.innerHTML = menuItems.map(item => `
      <article class="group relative bg-white dark:bg-slate-800 rounded-2xl p-6 shadow-sm hover:shadow-xl hover:-translate-y-1 transition border border-slate-100 dark:border-slate-700">
        ${item.tag ? `<span class="absolute top-4 right-4 text-xs font-semibold bg-brand-100 text-brand-700 px-2 py-1 rounded-full">${item.tag}</span>` : ""}
        <div class="text-5xl group-hover:scale-110 transition">${item.emoji}</div>
        <h3 class="mt-4 text-lg font-bold">${item.name}</h3>
        <p class="mt-1 text-sm text-slate-500 dark:text-slate-400">${item.desc}</p>
        <p class="mt-4 text-xl font-bold text-brand-600">₹${item.price}</p>
      </article>
    `).join("");

    // 3. Mobile menu: show/hide when ☰ is clicked
    const menuBtn = document.querySelector("#menuBtn");
    const mobileMenu = document.querySelector("#mobileMenu");
    menuBtn.addEventListener("click", () => {
      mobileMenu.classList.toggle("hidden");
      mobileMenu.classList.toggle("flex");
      menuBtn.textContent = mobileMenu.classList.contains("hidden") ? "☰" : "✕";
    });
    // Close the mobile menu after tapping a link
    mobileMenu.querySelectorAll("a").forEach(link => {
      link.addEventListener("click", () => {
        mobileMenu.classList.add("hidden");
        mobileMenu.classList.remove("flex");
        menuBtn.textContent = "☰";
      });
    });

    // 4. Dark mode: add/remove the "dark" class on <html> and remember the choice
    const root = document.documentElement;
    try {
      if (localStorage.getItem("theme") === "dark") root.classList.add("dark");
    } catch (e) {}
    document.querySelector("#themeBtn").addEventListener("click", () => {
      root.classList.toggle("dark");
      try {
        localStorage.setItem("theme", root.classList.contains("dark") ? "dark" : "light");
      } catch (e) {}
    });

    // 5. Contact form: show a thank-you message instead of reloading the page
    document.querySelector("#contactForm").addEventListener("submit", (event) => {
      event.preventDefault();
      document.querySelector("#formMsg").classList.remove("hidden");
      event.target.reset();
    });

    // 6. Footer year updates automatically
    document.querySelector("#year").textContent = new Date().getFullYear();
  </script>
</body>
</html>
````

