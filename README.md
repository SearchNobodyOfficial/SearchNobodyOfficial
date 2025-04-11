<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SearchNobody – All About Anime</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@700&family=Urbanist:wght@300;500;800&family=Noto+Sans+JP:wght@400;700&display=swap" rel="stylesheet">
  <style>
    /* ===== CORE VARIABLES ===== */
    :root {
      --primary: #00796B;            /* Professional Teal */
      --secondary: #009688;          /* Complementary Accent */
      --dark: #212121;               /* Dark text */
      --light: #ffffff;              /* White background */
      --header-height: 80px;
      --transition: cubic-bezier(0.4, 0, 0.2, 1);
    }

    /* ===== HEADER TEXT STYLES ===== */
    .header-text {
      font-family: 'Oswald', sans-serif;
      font-size: 2.8rem;
      color: var(--primary); /* Using your main teal color */
      margin-bottom: 0.5rem;
    }

    .anime-subtitle {
      font-family: 'Noto Sans JP', sans-serif;
      font-size: 1.4rem;
      color: var(--dark); /* Pure black text */
      letter-spacing: 2px;
      display: block;
      font-weight: 700; /* Bold for better visibility */
    }

    .title-wrapper {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
    }

    /* ===== REST OF CSS (UNCHANGED) ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
      font-size: 62.5%;
    }

    body {
      background-color: var(--light);
      color: var(--dark);
      font-family: 'Urbanist', sans-serif;
      line-height: 1.7;
      overflow-x: hidden;
    }

    .master-header {
      position: fixed;
      top: 0;
      width: 100%;
      height: var(--header-height);
      padding: 0 5%;
      background: rgba(255, 255, 255, 0.95);
      backdrop-filter: blur(12px);
      display: flex;
      justify-content: space-between;
      align-items: center;
      z-index: 1000;
      border-bottom: 1px solid rgba(0, 0, 0, 0.1);
      transition: all 0.4s var(--transition);
    }

    .brand-container {
      display: flex;
      align-items: center;
      gap: 2rem;
    }

    .nav-menu {
      display: flex;
      gap: 4rem;
    }

    .nav-link {
      color: var(--dark);
      text-decoration: none;
      font-size: 1.6rem;
      font-weight: 500;
      position: relative;
      padding: 1rem 0;
      transition: all 0.3s var(--transition);
    }

    .nav-link::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--primary);
      transition: width 0.3s var(--transition);
    }

    .nav-link:hover::after {
      width: 100%;
    }

    .hero-section {
      min-height: 80vh;
      padding: calc(var(--header-height) + 2rem) 5% 2rem;
      display: flex;
      align-items: center;
      position: relative;
      overflow: hidden;
    }

    .hero-backdrop {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(45deg, rgba(0, 121, 107, 0.15), rgba(0, 121, 107, 0.10));
      z-index: -1;
      opacity: 0.8;
    }

    .hero-content {
      max-width: 120rem;
      margin: 0 auto;
      text-align: center;
    }

    .hero-title {
      font-family: 'Oswald', sans-serif;
      font-size: 6rem;
      line-height: 1.1;
      color: var(--primary);
      text-shadow: 0 0 3rem rgba(0, 121, 107, 0.3);
      margin-bottom: 1.5rem;
    }

    .hero-subtitle {
      font-size: 2rem;
      color: var(--dark);
      margin-bottom: 2rem;
    }

    .about-container {
      max-width: 80rem;
      margin: 4rem auto 0;
      text-align: center;
      padding: 2rem 5%;
    }

    .about-text {
      font-size: 1.8rem;
      line-height: 1.8;
      opacity: 0.9;
    }

    .content-section {
      padding: 8rem 5%;
      scroll-margin-top: calc(var(--header-height) + 2rem);
    }

    .section-heading {
      font-family: 'Noto Sans JP', sans-serif;
      font-size: 4rem;
      text-align: center;
      margin-bottom: 6rem;
      position: relative;
    }

    .section-heading::after {
      content: '';
      position: absolute;
      bottom: -2rem;
      left: 50%;
      transform: translateX(-50%);
      width: 8rem;
      height: 0.4rem;
      background: var(--primary);
      border-radius: 2rem;
    }

    .video-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(32rem, 1fr));
      gap: 4rem;
      max-width: 140rem;
      margin: 0 auto;
    }

    .video-card {
      background: rgba(0, 0, 0, 0.03);
      border-radius: 2rem;
      overflow: hidden;
      transform: translateY(5rem);
      opacity: 0;
      transition: all 0.6s var(--transition);
    }

    .video-card.visible {
      transform: translateY(0);
      opacity: 1;
    }

    .video-frame {
      width: 100%;
      height: 25rem;
      border: none;
    }

    .social-bar {
      position: fixed;
      right: 3rem;
      top: 50%;
      transform: translateY(-50%);
      display: flex;
      flex-direction: column;
      gap: 2rem;
      z-index: 1000;
      opacity: 1;
      transition: all 0.4s var(--transition);
    }

    .social-bar.hidden {
      opacity: 0;
      transform: translateY(-50%) translateX(150%);
    }

    .social-icon {
      width: 5rem;
      height: 5rem;
      border-radius: 50%;
      background: rgba(0, 0, 0, 0.03);
      backdrop-filter: blur(1rem);
      display: flex;
      align-items: center;
      justify-content: center;
      transition: all 0.3s var(--transition);
      border: 1px solid rgba(0, 121, 107, 0.3);
    }

    .copyright-footer {
      padding: 4rem 5%;
      text-align: center;
      background: rgba(0, 0, 0, 0.04);
      border-top: 1px solid var(--primary);
      margin-top: 4rem;
    }

    .copyright-text {
      font-size: 1.4rem;
      opacity: 0.7;
    }

    @media (max-width: 768px) {
      html {
        font-size: 55%;
      }
      .nav-menu {
        display: none;
      }
      .hero-title {
        font-size: 4rem;
      }
      .header-text {
        font-size: 2.2rem;
      }
      .anime-subtitle {
        font-size: 1.1rem;
      }
    }
  </style>
</head>
<body>
  <!-- HEADER -->
  <header class="master-header">
    <div class="brand-container">
      <div class="title-wrapper">
        <h1 class="header-text">SEARCHNOBODY</h1>
        <span class="anime-subtitle">アニメへの情熱</span>
      </div>
      <nav class="nav-menu">
        <a href="#reviews" class="nav-link">Reviews</a>
        <a href="#videos" class="nav-link">Videos</a>
        <a href="#about" class="nav-link">About</a>
      </nav>
    </div>
  </header>

  <!-- REST OF CONTENT -->
  <section class="hero-section" id="home">
    <div class="hero-backdrop"></div>
    <div class="hero-content">
      <h1 class="hero-title">All About Anime</h1>
      <p class="hero-subtitle">Discover the latest updates, news, and reviews on anime from a true fan.</p>
    </div>
  </section>

  <section class="about-container" id="about">
    <h2 class="section-heading">About Me</h2>
    <p class="about-text">
      SearchNobody focuses on bringing you the latest anime updates, news, reviews, and fun facts. I'm just a simple anime fan running my YouTube channel and sharing what I love about anime – no professional team, just genuine passion.
    </p>
  </section>

  <section class="content-section" id="videos">
    <h2 class="section-heading">Videos</h2>
    <div class="video-grid">
      <div class="video-card">
        <iframe class="video-frame" src="https://www.youtube.com/embed/_C-6QdtIkPM" allowfullscreen></iframe>
      </div>
      <div class="video-card">
        <iframe class="video-frame" src="https://www.youtube.com/embed/MedPj64I50o" allowfullscreen></iframe>
      </div>
      <div class="video-card">
        <iframe class="video-frame" src="https://www.youtube.com/embed/IAEn9a3TyP4" allowfullscreen></iframe>
      </div>
    </div>
  </section>

  <div class="social-bar" id="socialBar">
    <a href="https://youtube.com/@search.nobody" class="social-icon" target="_blank">
      <i class="fab fa-youtube"></i>
    </a>
    <a href="https://instagram.com/search.nobody" class="social-icon" target="_blank">
      <i class="fab fa-instagram"></i>
    </a>
  </div>

  <footer class="copyright-footer">
    <p class="copyright-text">
      © 2024 SearchNobody. All rights reserved<br>
      Unauthorized duplication or distribution strictly prohibited
    </p>
  </footer>

  <script>
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.1 });
    
    document.querySelectorAll('.video-card').forEach(card => {
      observer.observe(card);
    });

    let lastScroll = 0;
    const socialBar = document.getElementById('socialBar');
    window.addEventListener('scroll', () => {
      const currentScroll = window.scrollY;
      if (currentScroll > lastScroll && currentScroll > 200) {
        socialBar.classList.add('hidden');
      } else {
        socialBar.classList.remove('hidden');
      }
      lastScroll = currentScroll;
    });

    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function(e) {
        e.preventDefault();
        const target = document.querySelector(this.getAttribute('href'));
        if(target) {
          window.scrollTo({
            top: target.offsetTop - 100,
            behavior: 'smooth'
          });
        }
      });
    });
  </script>
</body>
</html>
