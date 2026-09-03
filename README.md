<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=yes">
  <title>ARS Visual · Portofolio Profesional</title>
  <!-- Google Fonts: Inter + Manrope untuk kombinasi modern -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Manrope:wght@500;600;700;800&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 (free icons) untuk sosial media & UI -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    /* ===== RESET & VARIABEL ===== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    :root {
      --bg: #ffffff;
      --bg-soft: #f9fafb;
      --surface: #ffffff;
      --text-primary: #1a1c1e;
      --text-secondary: #5f6b7a;
      --text-muted: #8b95a5;
      --accent: #1f4b3f; /* dark green elegan */
      --accent-soft: #e6ede9;
      --border: #eaeef2;
      --shadow-sm: 0 4px 12px rgba(0,0,0,0.03), 0 2px 6px rgba(0,0,0,0.03);
      --shadow-md: 0 10px 25px rgba(0,0,0,0.05);
      --radius: 18px;
      --radius-sm: 12px;
      --transition: 0.25s cubic-bezier(0.2, 0.9, 0.3, 1);
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      background-color: var(--bg);
      font-family: 'Inter', sans-serif;
      color: var(--text-primary);
      line-height: 1.6;
      -webkit-font-smoothing: antialiased;
    }

    h1, h2, h3, h4, h5, h6 {
      font-family: 'Manrope', sans-serif;
      font-weight: 700;
      letter-spacing: -0.02em;
      line-height: 1.2;
      color: var(--text-primary);
    }

    a {
      text-decoration: none;
      color: inherit;
    }

    img {
      display: block;
      max-width: 100%;
      height: auto;
    }

    .container {
      width: 100%;
      max-width: 1280px;
      margin: 0 auto;
      padding: 0 24px;
    }

    /* ===== ANIMASI HALUS (fade-up saat scroll) ===== */
    .fade-section {
      opacity: 0;
      transform: translateY(25px);
      transition: opacity 0.8s ease, transform 0.8s ease;
    }

    .fade-section.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ===== NAVBAR STICKY ===== */
    .navbar {
      position: sticky;
      top: 0;
      width: 100%;
      background: rgba(255,255,255,0.82);
      backdrop-filter: blur(14px);
      -webkit-backdrop-filter: blur(14px);
      z-index: 1000;
      border-bottom: 1px solid var(--border);
      transition: box-shadow 0.2s;
    }

    .navbar.scrolled {
      box-shadow: 0 6px 18px rgba(0,0,0,0.03);
    }

    .nav-container {
      display: flex;
      align-items: center;
      justify-content: space-between;
      height: 72px;
    }

    .logo {
      font-family: 'Manrope', sans-serif;
      font-weight: 800;
      font-size: 1.6rem;
      color: var(--text-primary);
      letter-spacing: -0.03em;
    }
    .logo span {
      color: var(--accent);
    }

    .nav-links {
      display: flex;
      gap: 2rem;
      align-items: center;
    }

    .nav-links a {
      font-size: 0.95rem;
      font-weight: 500;
      color: var(--text-secondary);
      transition: color 0.2s;
      position: relative;
    }
    .nav-links a:hover {
      color: var(--accent);
    }

    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      background: none;
      border: none;
      cursor: pointer;
      padding: 8px;
    }
    .hamburger span {
      display: block;
      width: 26px;
      height: 2.5px;
      background: var(--text-primary);
      border-radius: 4px;
      transition: 0.3s;
    }

    /* Mobile menu */
    .mobile-menu {
      position: fixed;
      top: 72px;
      left: 0;
      right: 0;
      background: white;
      border-bottom: 1px solid var(--border);
      box-shadow: var(--shadow-md);
      transform: translateY(-120%);
      transition: transform 0.35s ease;
      z-index: 999;
      padding: 1rem 2rem 2rem;
    }
    .mobile-menu.open {
      transform: translateY(0);
    }
    .mobile-menu a {
      display: block;
      padding: 0.9rem 0;
      font-weight: 500;
      border-bottom: 1px solid #f0f2f5;
    }

    /* ===== BUTTONS & CTA ===== */
    .btn {
      display: inline-block;
      background: var(--accent);
      color: white;
      padding: 0.8rem 1.8rem;
      border-radius: 40px;
      font-weight: 600;
      font-size: 0.95rem;
      border: none;
      cursor: pointer;
      transition: background 0.25s, transform 0.2s, box-shadow 0.2s;
      box-shadow: var(--shadow-sm);
      letter-spacing: 0.01em;
    }
    .btn:hover {
      background: #16372e;
      transform: translateY(-2px);
      box-shadow: var(--shadow-md);
    }
    .btn-outline {
      background: transparent;
      border: 1.5px solid var(--accent);
      color: var(--accent);
      box-shadow: none;
    }
    .btn-outline:hover {
      background: var(--accent-soft);
    }

    /* ===== HERO SECTION ===== */
    .hero {
      background: linear-gradient(105deg, #ffffff 0%, #f6f8f7 100%);
      padding: 2rem 0 4rem;
    }
    .hero-grid {
      display: grid;
      grid-template-columns: 1.1fr 1fr;
      gap: 3rem;
      align-items: center;
    }
    .hero-text h1 {
      font-size: 3.8rem;
      font-weight: 800;
      margin-bottom: 1.2rem;
      line-height: 1.1;
    }
    .hero-text .lead {
      font-size: 1.2rem;
      color: var(--text-secondary);
      margin-bottom: 2.5rem;
      max-width: 450px;
    }
    .hero-img-wrapper {
      position: relative;
      border-radius: 32px;
      overflow: hidden;
      box-shadow: var(--shadow-md);
      aspect-ratio: 4/5;
      background: #d9e0dc;
    }
    .hero-img-wrapper img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.7s ease;
    }
    .hero-img-wrapper:hover img {
      transform: scale(1.02);
    }

    /* ===== SECTION GENERIC ===== */
    section {
      padding: 5rem 0;
    }
    .section-title {
      font-size: 2.5rem;
      font-weight: 700;
      margin-bottom: 0.8rem;
    }
    .section-sub {
      color: var(--text-secondary);
      margin-bottom: 3rem;
      font-size: 1.1rem;
    }

    /* ===== STATS ===== */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 1.5rem;
      margin: 2rem 0;
    }
    .stat-card {
      background: white;
      padding: 1.8rem 1.5rem;
      border-radius: var(--radius);
      box-shadow: var(--shadow-sm);
      border: 1px solid var(--border);
      text-align: center;
    }
    .stat-number {
      font-size: 2.5rem;
      font-weight: 800;
      color: var(--accent);
    }

    /* ===== CV TIMELINE ===== */
    .timeline {
      position: relative;
      margin: 2rem 0;
      padding-left: 2rem;
      border-left: 2px solid var(--accent-soft);
    }
    .timeline-item {
      margin-bottom: 2rem;
      position: relative;
    }
    .timeline-item::before {
      content: '';
      position: absolute;
      left: -2.4rem;
      top: 0.5rem;
      width: 12px;
      height: 12px;
      background: var(--accent);
      border-radius: 50%;
    }

    /* ===== GALLERY & FILTER ===== */
    .filter-buttons {
      display: flex;
      flex-wrap: wrap;
      gap: 0.8rem;
      margin-bottom: 2rem;
    }
    .filter-btn {
      background: var(--bg-soft);
      border: 1px solid var(--border);
      padding: 0.5rem 1.4rem;
      border-radius: 40px;
      font-weight: 500;
      cursor: pointer;
      transition: 0.2s;
      color: var(--text-secondary);
    }
    .filter-btn.active, .filter-btn:hover {
      background: var(--accent);
      color: white;
      border-color: var(--accent);
    }

    .gallery-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
      gap: 1.2rem;
    }
    .gallery-item {
      border-radius: var(--radius);
      overflow: hidden;
      cursor: pointer;
      position: relative;
      box-shadow: var(--shadow-sm);
      transition: transform 0.3s, box-shadow 0.3s;
      aspect-ratio: 3/4;
      background: #e3e6e9;
    }
    .gallery-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      transition: transform 0.7s;
    }
    .gallery-item:hover img {
      transform: scale(1.05);
    }
    .gallery-item:hover {
      box-shadow: var(--shadow-md);
    }

    /* Lightbox */
    .lightbox {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.85);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 2000;
      opacity: 0;
      pointer-events: none;
      transition: opacity 0.3s;
    }
    .lightbox.active {
      opacity: 1;
      pointer-events: auto;
    }
    .lightbox img {
      max-width: 90vw;
      max-height: 85vh;
      border-radius: 16px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.4);
    }

    /* ===== ARTIKEL & TESTIMONI ===== */
    .article-card {
      background: white;
      border-radius: var(--radius);
      overflow: hidden;
      box-shadow: var(--shadow-sm);
      transition: 0.25s;
      border: 1px solid var(--border);
    }
    .article-card:hover {
      box-shadow: var(--shadow-md);
    }
    .article-thumb {
      aspect-ratio: 16/9;
      background: #dfe3e6;
      overflow: hidden;
    }
    .article-thumb img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .testimonial-card {
      background: white;
      padding: 2rem;
      border-radius: var(--radius);
      box-shadow: var(--shadow-sm);
      border: 1px solid var(--border);
      text-align: center;
    }
    .stars {
      color: #d4af37;
      letter-spacing: 2px;
      margin-bottom: 0.8rem;
    }

    /* ===== SOCIAL MEDIA ===== */
    .social-links {
      display: flex;
      flex-wrap: wrap;
      gap: 1.5rem;
      justify-content: center;
    }
    .social-icon {
      width: 64px;
      height: 64px;
      background: white;
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2rem;
      box-shadow: var(--shadow-sm);
      transition: 0.25s;
      border: 1px solid var(--border);
    }
    .social-icon:hover {
      transform: translateY(-6px);
      background: var(--accent-soft);
    }

    /* ===== KONTAK & FORM ===== */
    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1.2fr;
      gap: 3rem;
    }
    .form-group {
      margin-bottom: 1.4rem;
    }
    input, textarea {
      width: 100%;
      padding: 0.9rem 1.2rem;
      border: 1px solid var(--border);
      border-radius: 14px;
      font-family: inherit;
      background: var(--bg-soft);
      transition: 0.2s;
    }
    input:focus, textarea:focus {
      outline: none;
      border-color: var(--accent);
      background: white;
    }

    /* Floating WhatsApp */
    .wa-float {
      position: fixed;
      bottom: 2rem;
      right: 1.5rem;
      background: #25D366;
      width: 60px;
      height: 60px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 2rem;
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
      z-index: 1500;
      transition: 0.3s;
    }
    .wa-float:hover {
      transform: scale(1.05);
    }

    /* ===== FOOTER ===== */
    footer {
      background: #fafbfc;
      padding: 4rem 0 2rem;
      border-top: 1px solid var(--border);
    }

    /* ===== RESPONSIVE ===== */
    @media (max-width: 1024px) {
      .hero-grid {
        grid-template-columns: 1fr;
        text-align: center;
      }
      .hero-text .lead {
        margin-left: auto;
        margin-right: auto;
      }
      .contact-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 768px) {
      .nav-links {
        display: none;
      }
      .hamburger {
        display: flex;
      }
      .section-title {
        font-size: 2rem;
      }
      .stats-grid {
        grid-template-columns: 1fr 1fr;
      }
      .gallery-grid {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    @media (max-width: 480px) {
      .stats-grid {
        grid-template-columns: 1fr;
      }
      .gallery-grid {
        grid-template-columns: 1fr;
      }
      .btn {
        padding: 0.7rem 1.5rem;
      }
    }
  </style>
</head>
<body>
  <!-- NAVBAR -->
  <nav class="navbar" id="navbar">
    <div class="container nav-container">
      <a href="#" class="logo">ARS<span>.</span></a>
      <div class="nav-links">
        <a href="#beranda">Beranda</a>
        <a href="#tentang">Tentang Kami</a>
        <a href="#cv">CV</a>
        <a href="#karya">Hasil Karya</a>
        <a href="#artikel">Artikel</a>
        <a href="#sosmed">Media Sosial</a>
        <a href="#kontak">Kontak</a>
        <a href="#testimoni">Testimoni</a>
      </div>
      <button class="hamburger" id="hamburger" aria-label="Menu">
        <span></span><span></span><span></span>
      </button>
    </div>
    <!-- Mobile Menu -->
    <div class="mobile-menu" id="mobileMenu">
      <a href="#beranda">Beranda</a>
      <a href="#tentang">Tentang Kami</a>
      <a href="#cv">CV</a>
      <a href="#karya">Hasil Karya</a>
      <a href="#artikel">Artikel</a>
      <a href="#sosmed">Media Sosial</a>
      <a href="#kontak">Kontak</a>
      <a href="#testimoni">Testimoni</a>
    </div>
  </nav>

  <!-- HERO SECTION -->
  <section class="hero" id="beranda">
    <div class="container hero-grid">
      <div class="hero-text fade-section">
        <h1>Mengabadikan Cerita,<br>Menciptakan Karya.</h1>
        <p class="lead">Portofolio fotografi profesional yang mengubah momen menjadi cerita visual yang berkesan.</p>
        <div style="display: flex; gap: 1rem; flex-wrap: wrap; justify-content: center; max-width: 400px; margin: 0 auto;">
          <a href="#karya" class="btn">Lihat Hasil Karya</a>
          <a href="#kontak" class="btn btn-outline">Hubungi Kami</a>
        </div>
      </div>
      <div class="hero-img-wrapper fade-section">
        <img src="https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e?q=80&w=1000&auto=format&fit=crop" alt="Fotografer profesional">
      </div>
    </div>
  </section>

  <!-- TENTANG KAMI -->
  <section id="tentang" class="fade-section">
    <div class="container">
      <h2 class="section-title">Tentang Kami</h2>
      <div style="display: grid; grid-template-columns: 1fr 1.2fr; gap: 3rem; align-items: center;">
        <div>
          <img src="https://images.unsplash.com/photo-1600880292203-757bb62b4baf?q=80&w=800&auto=format&fit=crop" alt="Team" style="border-radius: 28px; box-shadow: var(--shadow-md); width: 100%; aspect-ratio: 1/1; object-fit: cover;">
        </div>
        <div>
          <p style="color: var(--text-secondary); font-size: 1.1rem; margin-bottom: 1.5rem;">Kami adalah tim visual yang berfokus pada fotografi premium, mengutamakan detail dan cerita dalam setiap bingkai. Berpengalaman sejak 2018, kami telah menyelesaikan lebih dari 250 proyek.</p>
          <div class="stats-grid" style="margin: 1.5rem 0;">
            <div class="stat-card"><div class="stat-number">250+</div><div>Proyek</div></div>
            <div class="stat-card"><div class="stat-number">8</div><div>Tahun Pengalaman</div></div>
            <div class="stat-card"><div class="stat-number">40+</div><div>Klien</div></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CV -->
  <section id="cv" style="background: var(--bg-soft);">
    <div class="container fade-section">
      <h2 class="section-title">CV</h2>
      <p style="color:var(--text-secondary)">Pelajar · SMKN 42 Jakarta</p>
      <div class="timeline">
        <div class="timeline-item"><h4>Pendidikan</h4><p>SMKN 42 Jakarta (2023 - Sekarang)</p></div>
        <div class="timeline-item"><h4>Magang Fotografi</h4><p>Studio Visual Jakarta (2025)</p></div>
        <div class="timeline-item"><h4>Proyek Pribadi</h4><p>Portrait & Event 2024-2026</p></div>
      </div>
      <a href="#" class="btn" style="margin-top: 1rem;">Download CV</a>
    </div>
  </section>

  <!-- HASIL KARYA / GALLERY -->
  <section id="karya">
    <div class="container fade-section">
      <h2 class="section-title">Hasil Karya</h2>
      <div class="filter-buttons">
        <button class="filter-btn active" data-filter="all">Semua</button>
        <button class="filter-btn" data-filter="portrait">Portrait</button>
        <button class="filter-btn" data-filter="event">Event</button>
        <button class="filter-btn" data-filter="wedding">Wedding</button>
        <button class="filter-btn" data-filter="product">Product</button>
        <button class="filter-btn" data-filter="landscape">Landscape</button>
        <button class="filter-btn" data-filter="commercial">Commercial</button>
      </div>
      <div class="gallery-grid" id="galleryGrid">
        <!-- item contoh, akan difilter lewat js sederhana dengan kategori data -->
        <div class="gallery-item" data-category="portrait"><img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=600&auto=format&fit=crop" alt="Portrait"></div>
        <div class="gallery-item" data-category="event"><img src="https://images.unsplash.com/photo-1540575467063-178a50c2df87?q=80&w=600&auto=format&fit=crop" alt="Event"></div>
        <div class="gallery-item" data-category="wedding"><img src="https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=600&auto=format&fit=crop" alt="Wedding"></div>
        <div class="gallery-item" data-category="product"><img src="https://images.unsplash.com/photo-1523275335684-37898b6baf30?q=80&w=600&auto=format&fit=crop" alt="Product"></div>
        <div class="gallery-item" data-category="landscape"><img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?q=80&w=600&auto=format&fit=crop" alt="Landscape"></div>
        <div class="gallery-item" data-category="commercial"><img src="https://images.unsplash.com/photo-1556740738-b6a63e27c4df?q=80&w=600&auto=format&fit=crop" alt="Commercial"></div>
        <div class="gallery-item" data-category="portrait"><img src="https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?q=80&w=600&auto=format&fit=crop" alt="Portrait 2"></div>
        <div class="gallery-item" data-category="event"><img src="https://images.unsplash.com/photo-1492684223066-81342ee5ff30?q=80&w=600&auto=format&fit=crop" alt="Event 2"></div>
      </div>
    </div>
  </section>

  <!-- LIGHTBOX -->
  <div class="lightbox" id="lightbox">
    <img src="" alt="lightbox" id="lightboxImg">
  </div>

  <!-- ARTIKEL -->
  <section id="artikel" style="background: var(--bg-soft);">
    <div class="container fade-section">
      <h2 class="section-title">Artikel</h2>
      <div style="display: grid; grid-template-columns: repeat(auto-fill, minmax(280px,1fr)); gap: 2rem;">
        <div class="article-card"><div class="article-thumb"><img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?q=80&w=800&auto=format&fit=crop" alt="Artikel"></div><div style="padding:1.5rem"><h4>Tips Pencahayaan Natural</h4><p style="color:var(--text-secondary)">12 Juni 2026 · Fotografi</p><p>Ringkasan singkat artikel tentang teknik memanfaatkan cahaya alami...</p></div></div>
        <div class="article-card"><div class="article-thumb"><img src="https://images.unsplash.com/photo-1516035069371-29a1b244cc32?q=80&w=800&auto=format&fit=crop" alt="Artikel"></div><div style="padding:1.5rem"><h4>Komposisi Minimalis</h4><p style="color:var(--text-secondary)">28 Mei 2026 · Teknik</p><p>Menguasai seni ruang kosong dalam frame.</p></div></div>
      </div>
    </div>
  </section>

  <!-- MEDIA SOSIAL -->
  <section id="sosmed">
    <div class="container fade-section text-center">
      <h2 class="section-title">Media Sosial</h2>
      <div class="social-links">
        <a href="#" class="social-icon" target="_blank"><i class="fab fa-instagram"></i></a>
        <a href="#" class="social-icon" target="_blank"><i class="fab fa-facebook-f"></i></a>
        <a href="#" class="social-icon" target="_blank"><i class="fab fa-tiktok"></i></a>
        <a href="#" class="social-icon" target="_blank"><i class="fab fa-youtube"></i></a>
        <a href="#" class="social-icon" target="_blank"><i class="fab fa-linkedin-in"></i></a>
      </div>
    </div>
  </section>

  <!-- KONTAK -->
  <section id="kontak" style="background: var(--bg-soft);">
    <div class="container fade-section">
      <h2 class="section-title">Kontak</h2>
      <div class="contact-grid">
        <div>
          <p><i class="fas fa-phone"></i> WhatsApp: +62 812-3456-7890</p>
          <p><i class="fas fa-envelope"></i> halo@arsvisual.id</p>
          <p><i class="fas fa-map-marker-alt"></i> Jakarta, Indonesia</p>
          <p><i class="fas fa-clock"></i> Jam Kerja: 09.00 - 18.00 WIB</p>
        </div>
        <div>
          <form>
            <div class="form-group"><input type="text" placeholder="Nama"></div>
            <div class="form-group"><input type="email" placeholder="Email"></div>
            <div class="form-group"><input type="text" placeholder="Nomor WhatsApp"></div>
            <div class="form-group"><input type="text" placeholder="Subjek"></div>
            <div class="form-group"><textarea rows="4" placeholder="Pesan"></textarea></div>
            <button class="btn" type="button">Kirim Pesan</button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- TESTIMONI -->
  <section id="testimoni">
    <div class="container fade-section">
      <h2 class="section-title">Testimoni</h2>
      <div style="display: grid; grid-template-columns: repeat(3,1fr); gap: 2rem;" id="testimoniGrid">
        <div class="testimonial-card"><div class="stars">★★★★★</div><img src="https://i.pravatar.cc/80?img=1" alt="Avatar" style="border-radius:50%; margin:0 auto 0.8rem; width:60px; height:60px;"><h4>Rina Wijaya</h4><p>CEO Creative Studio</p><p>"Hasil foto sangat profesional, komunikasi mudah."</p></div>
        <div class="testimonial-card"><div class="stars">★★★★★</div><img src="https://i.pravatar.cc/80?img=2" alt="Avatar" style="border-radius:50%; margin:0 auto 0.8rem; width:60px; height:60px;"><h4>Bima Prakoso</h4><p>Event Organizer</p><p>"Dokumentasi event sempurna, tepat waktu."</p></div>
        <div class="testimonial-card"><div class="stars">★★★★★</div><img src="https://i.pravatar.cc/80?img=3" alt="Avatar" style="border-radius:50%; margin:0 auto 0.8rem; width:60px; height:60px;"><h4>Sari Dewi</h4><p>Bridal Owner</p><p>"Foto prewedding melebihi ekspektasi."</p></div>
      </div>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="container" style="display: flex; flex-wrap: wrap; justify-content: space-between; gap: 2rem;">
      <div style="max-width: 300px;"><h3>ARS<span>.</span></h3><p style="color: var(--text-secondary);">Portofolio fotografi profesional dengan sentuhan elegan.</p></div>
      <div><a href="#" style="display:block; margin-bottom:0.4rem;">Privacy Policy</a><a href="#">Terms</a></div>
      <div><p>© 2026 ARS Visual. All rights reserved.</p></div>
    </div>
  </footer>

  <!-- FLOATING WHATSAPP -->
  <a href="#" class="wa-float" target="_blank"><i class="fab fa-whatsapp"></i></a>

  <script>
    // Smooth scroll & navbar shadow
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      navbar.classList.toggle('scrolled', window.scrollY > 50);
    });

    // Hamburger menu
    const hamburger = document.getElementById('hamburger');
    const mobileMenu = document.getElementById('mobileMenu');
    hamburger.addEventListener('click', () => {
      mobileMenu.classList.toggle('open');
    });
    // close mobile menu on link click
    document.querySelectorAll('.mobile-menu a').forEach(link => {
      link.addEventListener('click', () => mobileMenu.classList.remove('open'));
    });

    // Fade-section on scroll (Intersection Observer)
    const fadeSections = document.querySelectorAll('.fade-section');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.15 });
    fadeSections.forEach(section => observer.observe(section));

    // Gallery filter sederhana
    const filterButtons = document.querySelectorAll('.filter-btn');
    const galleryItems = document.querySelectorAll('.gallery-item');
    filterButtons.forEach(btn => {
      btn.addEventListener('click', () => {
        filterButtons.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');
        const filter = btn.dataset.filter;
        galleryItems.forEach(item => {
          if (filter === 'all' || item.dataset.category === filter) {
            item.style.display = 'block';
          } else {
            item.style.display = 'none';
          }
        });
      });
    });

    // Lightbox
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightboxImg');
    galleryItems.forEach(item => {
      item.addEventListener('click', () => {
        const imgSrc = item.querySelector('img').src;
        lightboxImg.src = imgSrc;
        lightbox.classList.add('active');
      });
    });
    lightbox.addEventListener('click', () => {
      lightbox.classList.remove('active');
    });

    // lazy load images (native)
    document.querySelectorAll('img').forEach(img => {
      img.loading = 'lazy';
    });
  </script>
</body>
</html>
