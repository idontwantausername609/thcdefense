all css code belongs in "# style.css"
do not duplicate css code


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>THC Defense Mobile Hamburger Nav (With Up Animation)</title>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Cinzel', serif;
      background: #f9f9f9;
    }
    .mobile-header {
      background: #1a1a1a;
      color: #fff;
      font-family: 'Cinzel', serif;
      position: relative;
      z-index: 100;
      box-shadow: 0 2px 8px rgba(30,30,30,0.11);
    }
    .mobile-nav-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1rem 1.2rem;
    }
    .mobile-logo {
      font-size: 2rem;
      font-weight: 400;
      letter-spacing: 0.07em;
      color: #fff;
    }
    .hamburger {
      display: flex;
      flex-direction: column;
      justify-content: center;
      gap: 0.33em;
      width: 36px;
      height: 36px;
      background: none;
      border: none;
      cursor: pointer;
      z-index: 200;
    }
    .hamburger span {
      display: block;
      height: 3px;
      width: 28px;
      background: #fff;
      border-radius: 3px;
      transition: 0.3s;
    }
    .mobile-menu {
      display: none;
      flex-direction: column;
      background: #1a1a1a;
      width: 100%;
      padding: 0.2rem 0 0.5rem 0;
      text-align: right;
      box-shadow: 0 6px 18px rgba(0,0,0,0.10);
      position: absolute;
      top: 100%;
      left: 0;
    }
    .mobile-menu a {
      color: #fff;
      padding: 1rem 1.7rem 1rem 1.7rem;
      font-size: 1.13rem;
      font-family: 'Cinzel', serif;
      text-decoration: none;
      display: block;
      border-bottom: 1px solid #222;
      transition: background 0.19s;
      text-align: right;
      letter-spacing: 0.03em;
    }
    .mobile-menu a:last-child {
      border-bottom: none;
    }
    .mobile-menu a:hover,
    .mobile-menu a.active {
      background: #232323;
      color: #fff;
    }

    /* Menu Animations */
    @keyframes menuDown {
      from { opacity: 0; transform: translateY(-10px);}
      to   { opacity: 1; transform: translateY(0);}
    }
    @keyframes menuUp {
      from { opacity: 1; transform: translateY(0);}
      to   { opacity: 0; transform: translateY(-10px);}
    }
    .mobile-menu.show {
      display: flex;
      animation: menuDown 0.28s cubic-bezier(.67,.17,.32,.99) forwards;
    }
    .mobile-menu.hiding {
      display: flex;
      animation: menuUp 0.22s cubic-bezier(.67,.17,.32,.99) forwards;
    }
    /* Responsive: Hide on desktop */
    @media (min-width: 700px) {
      .mobile-header, .mobile-menu, .mobile-nav-bar, .hamburger {
        display: none !important;
      }
    }
    main {
      padding: 2.5rem 1.5rem 1.5rem 1.5rem;
      max-width: 650px;
      margin: 0 auto;
      text-align: center;
    }
    h2 {
      margin-top: 2.5rem;
      font-family: 'Cinzel', serif;
      color: #1a1a1a;
      letter-spacing: 0.07em;
      font-size: 2rem;
      font-weight: 400;
    }
  </style>
</head>
<body>
  <header class="mobile-header">
    <div class="mobile-nav-bar">
      <div class="mobile-logo">THC Defense</div>
      <button class="hamburger" id="hamburger-menu" aria-label="Menu">
        <span></span><span></span><span></span>
      </button>
    </div>
    <nav class="mobile-menu" id="mobile-menu">
      <a href="#" class="active">Home</a>
      <a href="#">Arrest Records</a>
      <a href="#">Marijuana Laws</a>
      <a href="#">FAQs</a>
      <a href="#">Contact</a>
    </nav>
  </header>
  <main>
    <h2>THC Defense Mobile Hamburger Nav Demo</h2>
    <p>
      Tap the <strong>hamburger icon</strong> to see the menu.<br>
      Close the menu to watch the “menu up” animation.<br>
      <em>Customize colors, logo, and link destinations as needed!</em>
    </p>
  </main>
  <script>
    const hamburger = document.getElementById('hamburger-menu');
    const menu = document.getElementById('mobile-menu');
    hamburger.onclick = function() {
      if (!menu.classList.contains('show')) {
        menu.style.display = 'flex'; // ensure menu is visible before animating
        menu.classList.add('show');
        menu.classList.remove('hiding');
      } else {
        menu.classList.remove('show');
        menu.classList.add('hiding');
        // After animation, hide menu fully
        setTimeout(() => {
          menu.classList.remove('hiding');
          menu.style.display = "none";
        }, 220); // Match menuUp duration
      }
    };
    // Re-enable menu display on open
    menu.addEventListener('animationstart', function(e) {
      if (e.animationName === 'menuDown') menu.style.display = 'flex';
    });
    // Close menu when link is clicked
   Array.from(document.querySelectorAll('.mobile-menu a')).forEach(link => {
      link.onclick = () => {
        menu.classList.remove('show');
        menu.classList.add('hiding');
        setTimeout(() => {
          menu.classList.remove('hiding');
          menu.style.display = "none";
        }, 220);
      };
    });
  </script>
</body>
</html>
