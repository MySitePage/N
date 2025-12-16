<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NOCTURNE GARAGE | Automotive</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        /* PRECISE COLOR PALETTE */
        :root {
            --blood-deep: #7a0f14;
            --blood-glow: #b1121b;
            --text-offwhite: #f2f2f2;
            --text-muted: #8a8a8a;
            --bg-black: #0a0a0a;
            --bg-card: #141414;
            --border-dark: #2a2a2a;
            --overlay-white: rgba(255, 255, 255, 0.05);
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        html {
            scroll-behavior: smooth;
        }
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-black);
            color: var(--text-offwhite);
            overflow-x: hidden;
            line-height: 1.6;
            font-weight: 300;
            letter-spacing: 0.02em;
        }
        
        /* BACKGROUND - BRICK WALL */
        .bg-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }
        
        .brick-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(10, 10, 10, 0.9), rgba(10, 10, 10, 0.92)),
                url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR9gYPukoQhoEX8NNSmGWnqw83yAeKd6p-IylGsrZhygA&s=10');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            background-attachment: fixed;
        }
        
        .blood-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                135deg,
                rgba(122, 15, 20, 0.7) 0%,
                rgba(10, 10, 10, 0.9) 60%,
                rgba(122, 15, 20, 0.6) 100%
            );
            z-index: 1;
        }
        
        /* TINY FILM GRAIN */
        .film-grain {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)' opacity='0.03'/%3E%3C/svg%3E");
            z-index: 2;
            pointer-events: none;
            opacity: 0.1;
        }
        
        .container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 40px;
            position: relative;
            z-index: 10;
        }
        
        /* HEADER - MINIMAL */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            padding: 30px 0;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            background-color: rgba(10, 10, 10, 0.4);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid transparent;
        }
        
        header.scrolled {
            padding: 20px 0;
            background-color: rgba(10, 10, 10, 0.9);
            border-bottom: 1px solid rgba(122, 15, 20, 0.3);
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-family: 'Oswald', sans-serif;
            font-size: 24px;
            font-weight: 500;
            letter-spacing: 0.2em;
            color: var(--text-offwhite);
            text-decoration: none;
            text-transform: uppercase;
            position: relative;
            padding-left: 10px;
        }
        
        .logo::before {
            content: '';
            position: absolute;
            left: 0;
            top: 50%;
            transform: translateY(-50%);
            width: 4px;
            height: 18px;
            background-color: var(--blood-deep);
            box-shadow: 0 0 6px rgba(177, 18, 27, 0.6);
        }
        
        /* NAVIGATION - CLEAN LINES */
        nav ul {
            display: flex;
            list-style: none;
            gap: 40px;
        }
        
        nav a {
            font-family: 'Oswald', sans-serif;
            font-size: 14px;
            font-weight: 400;
            letter-spacing: 0.15em;
            color: var(--text-muted);
            text-decoration: none;
            text-transform: uppercase;
            position: relative;
            padding: 8px 0;
            transition: all 0.3s ease;
        }
        
        nav a:hover {
            color: var(--text-offwhite);
        }
        
        nav a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 1px;
            background-color: var(--blood-glow);
            box-shadow: 0 0 6px rgba(177, 18, 27, 0.6);
            transition: width 0.3s cubic-bezier(0.16, 1, 0.3, 1);
        }
        
        nav a:hover::after {
            width: 100%;
        }
        
        .nav-cta {
            font-family: 'Oswald', sans-serif;
            background: transparent;
            color: var(--text-offwhite);
            padding: 10px 28px;
            font-size: 13px;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            text-decoration: none;
            border: 1px solid var(--border-dark);
            transition: all 0.3s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            overflow: hidden;
        }
        
        .nav-cta::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(177, 18, 27, 0.05), transparent);
            transition: left 0.6s cubic-bezier(0.16, 1, 0.3, 1);
        }
        
        .nav-cta:hover {
            border-color: var(--blood-deep);
            box-shadow: 0 0 12px rgba(177, 18, 27, 0.2);
        }
        
        .nav-cta:hover::before {
            left: 100%;
        }
        
        .mobile-menu-btn {
            display: none;
            background: transparent;
            border: 1px solid var(--border-dark);
            color: var(--text-offwhite);
            width: 44px;
            height: 44px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .mobile-menu-btn:hover {
            border-color: var(--blood-deep);
        }
        
        /* HERO SECTION - CAR IMAGE WITH WHITE OVERLAY */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            overflow: hidden;
        }
        
        .hero-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(255, 255, 255, 0.08), rgba(255, 255, 255, 0.05)),
                url('https://images.unsplash.com/photo-1549399542-7e3f8b79c341?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            z-index: -1;
        }
        
        .hero-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                90deg,
                rgba(10, 10, 10, 0.95) 0%,
                rgba(10, 10, 10, 0.85) 50%,
                rgba(10, 10, 10, 0.95) 100%
            );
            z-index: -1;
        }
        
        .hero-content {
            max-width: 800px;
            padding: 120px 0;
        }
        
        .hero h1 {
            font-family: 'Oswald', sans-serif;
            font-size: 72px;
            font-weight: 500;
            letter-spacing: 0.15em;
            line-height: 1;
            color: var(--text-offwhite);
            text-transform: uppercase;
            margin-bottom: 30px;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.8);
        }
        
        .hero-line {
            width: 200px;
            height: 2px;
            background-color: var(--blood-deep);
            margin-bottom: 40px;
            position: relative;
            overflow: hidden;
        }
        
        .hero-line::after {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, var(--blood-glow), transparent);
            animation: line-glow 4s infinite;
        }
        
        @keyframes line-glow {
            0%, 100% { left: -100%; }
            50% { left: 100%; }
        }
        
        .hero-tagline {
            font-size: 18px;
            color: var(--text-muted);
            margin-bottom: 50px;
            max-width: 500px;
            line-height: 1.8;
            font-weight: 300;
        }
        
        .hero-button {
            display: inline-block;
            font-family: 'Oswald', sans-serif;
            background: transparent;
            color: var(--text-offwhite);
            padding: 16px 40px;
            font-size: 14px;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            text-decoration: none;
            border: 1px solid var(--border-dark);
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            overflow: hidden;
        }
        
        .hero-button:hover {
            border-color: var(--blood-deep);
            box-shadow: 0 0 20px rgba(177, 18, 27, 0.15);
            letter-spacing: 0.18em;
        }
        
        /* SECTION COMMON STYLES */
        section {
            padding: 120px 0;
            position: relative;
        }
        
        .section-title {
            font-family: 'Oswald', sans-serif;
            font-size: 40px;
            font-weight: 500;
            letter-spacing: 0.15em;
            color: var(--text-offwhite);
            text-transform: uppercase;
            margin-bottom: 70px;
            position: relative;
            display: inline-block;
        }
        
        .section-title::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: 0;
            width: 60px;
            height: 1px;
            background-color: var(--blood-deep);
            box-shadow: 0 0 8px rgba(177, 18, 27, 0.7);
        }
        
        /* SERVICES - LUXURY CARDS */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(380px, 1fr));
            gap: 30px;
        }
        
        .service-card {
            background-color: var(--bg-card);
            border: 1px solid var(--border-dark);
            padding: 40px;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            overflow: hidden;
        }
        
        .service-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, transparent 30%, rgba(122, 15, 20, 0.03) 50%, transparent 70%);
            z-index: 1;
            pointer-events: none;
        }
        
        .service-card:hover {
            border-color: var(--blood-deep);
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5), 0 0 20px rgba(177, 18, 27, 0.1);
            transform: translateY(-5px);
        }
        
        .service-icon {
            font-size: 36px;
            color: var(--blood-deep);
            margin-bottom: 25px;
            text-shadow: 0 0 8px rgba(177, 18, 27, 0.5);
            transition: all 0.4s ease;
        }
        
        .service-card:hover .service-icon {
            transform: scale(1.1);
            text-shadow: 0 0 12px rgba(177, 18, 27, 0.7);
        }
        
        .service-card h3 {
            font-family: 'Oswald', sans-serif;
            font-size: 20px;
            font-weight: 500;
            letter-spacing: 0.15em;
            color: var(--text-offwhite);
            text-transform: uppercase;
            margin-bottom: 15px;
        }
        
        .service-card p {
            color: var(--text-muted);
            font-size: 15px;
            line-height: 1.8;
            font-weight: 300;
        }
        
        /* SERVICE AREAS - MINIMAL */
        .areas-container {
            max-width: 1000px;
            margin: 0 auto;
        }
        
        .areas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }
        
        .area-item {
            background-color: var(--bg-card);
            border: 1px solid var(--border-dark);
            padding: 20px;
            text-align: center;
            font-family: 'Oswald', sans-serif;
            font-size: 14px;
            letter-spacing: 0.1em;
            color: var(--text-offwhite);
            text-transform: uppercase;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .area-item:hover {
            border-color: var(--blood-deep);
            color: var(--blood-glow);
            text-shadow: 0 0 8px rgba(177, 18, 27, 0.4);
        }
        
        /* TESTIMONIALS - LUXURY QUOTES */
        .testimonial-slider {
            max-width: 800px;
            margin: 0 auto;
        }
        
        .testimonial {
            background-color: var(--bg-card);
            border: 1px solid var(--border-dark);
            padding: 50px;
            position: relative;
        }
        
        .testimonial::before {
            content: '"';
            position: absolute;
            top: 20px;
            left: 30px;
            font-family: 'Oswald', sans-serif;
            font-size: 80px;
            color: var(--blood-deep);
            opacity: 0.2;
            line-height: 1;
        }
        
        .testimonial-text {
            font-size: 18px;
            color: var(--text-offwhite);
            line-height: 1.8;
            margin-bottom: 30px;
            font-weight: 300;
            font-style: italic;
            padding-left: 20px;
        }
        
        .testimonial-author {
            font-family: 'Oswald', sans-serif;
            font-size: 16px;
            letter-spacing: 0.1em;
            color: var(--blood-deep);
            text-transform: uppercase;
        }
        
        .testimonial-date {
            color: var(--text-muted);
            font-size: 14px;
            margin-left: 15px;
        }
        
        /* CONTACT - CLEAN FORM */
        .contact-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 60px;
        }
        
        .contact-info h3 {
            font-family: 'Oswald', sans-serif;
            font-size: 28px;
            letter-spacing: 0.15em;
            color: var(--text-offwhite);
            text-transform: uppercase;
            margin-bottom: 40px;
        }
        
        .contact-detail {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 1px solid var(--border-dark);
        }
        
        .contact-icon {
            width: 50px;
            height: 50px;
            background-color: var(--bg-card);
            border: 1px solid var(--border-dark);
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 20px;
            color: var(--blood-deep);
            font-size: 18px;
            transition: all 0.3s ease;
        }
        
        .contact-detail:hover .contact-icon {
            border-color: var(--blood-deep);
            box-shadow: 0 0 12px rgba(177, 18, 27, 0.2);
        }
        
        .contact-phone {
            font-family: 'Oswald', sans-serif;
            font-size: 24px;
            letter-spacing: 0.1em;
            color: var(--text-offwhite);
        }
        
        /* FORM - MINIMAL */
        .contact-form {
            background-color: var(--bg-card);
            border: 1px solid var(--border-dark);
            padding: 50px;
        }
        
        .form-group {
            margin-bottom: 25px;
        }
        
        .form-group label {
            display: block;
            font-family: 'Oswald', sans-serif;
            font-size: 12px;
            letter-spacing: 0.15em;
            color: var(--text-muted);
            text-transform: uppercase;
            margin-bottom: 10px;
        }
        
        .form-control {
            width: 100%;
            background-color: rgba(10, 10, 10, 0.5);
            border: 1px solid var(--border-dark);
            padding: 15px;
            color: var(--text-offwhite);
            font-family: 'Inter', sans-serif;
            font-size: 15px;
            transition: all 0.3s ease;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--blood-deep);
            box-shadow: 0 0 15px rgba(177, 18, 27, 0.15);
        }
        
        .submit-btn {
            width: 100%;
            background: transparent;
            border: 1px solid var(--border-dark);
            color: var(--text-offwhite);
            padding: 18px;
            font-family: 'Oswald', sans-serif;
            font-size: 13px;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            cursor: pointer;
            transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
            position: relative;
            overflow: hidden;
        }
        
        .submit-btn:hover {
            border-color: var(--blood-deep);
            letter-spacing: 0.18em;
            box-shadow: 0 0 20px rgba(177, 18, 27, 0.1);
        }
        
        /* FOOTER - CLEAN */
        footer {
            background-color: var(--bg-card);
            border-top: 1px solid var(--border-dark);
            padding: 80px 0 40px;
        }
        
        .footer-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 50px;
            margin-bottom: 60px;
        }
        
        .footer-section h4 {
            font-family: 'Oswald', sans-serif;
            font-size: 16px;
            letter-spacing: 0.15em;
            color: var(--text-offwhite);
            text-transform: uppercase;
            margin-bottom: 25px;
            position: relative;
            padding-bottom: 10px;
        }
        
        .footer-section h4::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 30px;
            height: 1px;
            background-color: var(--blood-deep);
            box-shadow: 0 0 6px rgba(177, 18, 27, 0.6);
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 12px;
        }
        
        .footer-links a {
            color: var(--text-muted);
            text-decoration: none;
            font-size: 14px;
            transition: all 0.3s ease;
        }
        
        .footer-links a:hover {
            color: var(--text-offwhite);
            padding-left: 5px;
        }
        
        .copyright {
            text-align: center;
            padding-top: 40px;
            border-top: 1px solid var(--border-dark);
            color: var(--text-muted);
            font-size: 13px;
            letter-spacing: 0.1em;
        }
        
        /* SCROLL INDICATOR - MINIMAL */
        .scroll-indicator {
            position: fixed;
            right: 40px;
            top: 50%;
            transform: translateY(-50%);
            z-index: 100;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        
        .scroll-dot {
            width: 10px;
            height: 10px;
            background-color: transparent;
            border: 1px solid var(--border-dark);
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }
        
        .scroll-dot.active {
            background-color: var(--blood-deep);
            border-color: var(--blood-deep);
            box-shadow: 0 0 8px rgba(177, 18, 27, 0.7);
        }
        
        .scroll-dot::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            width: 16px;
            height: 16px;
            border: 1px solid rgba(177, 18, 27, 0.3);
            border-radius: 50%;
            transition: transform 0.3s ease;
        }
        
        .scroll-dot.active::after {
            transform: translate(-50%, -50%) scale(1);
        }
        
        /* RESPONSIVE */
        @media (max-width: 1100px) {
            .hero h1 {
                font-size: 56px;
            }
            
            .services-grid {
                grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            }
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 0 25px;
            }
            
            .hero h1 {
                font-size: 42px;
            }
            
            .mobile-menu-btn {
                display: block;
            }
            
            nav ul {
                position: fixed;
                top: 90px;
                left: 0;
                width: 100%;
                background-color: rgba(10, 10, 10, 0.98);
                flex-direction: column;
                align-items: center;
                padding: 40px 0;
                gap: 30px;
                border-bottom: 1px solid var(--border-dark);
                transform: translateY(-150%);
                transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
                backdrop-filter: blur(20px);
            }
            
            nav ul.active {
                transform: translateY(0);
            }
            
            .scroll-indicator {
                display: none;
            }
            
            .contact-container {
                grid-template-columns: 1fr;
            }
            
            .contact-form {
                padding: 30px;
            }
        }
        
        @media (max-width: 480px) {
            .hero h1 {
                font-size: 36px;
            }
            
            .section-title {
                font-size: 32px;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .service-card {
                padding: 30px;
            }
        }
        
        /* CUSTOM SCROLLBAR */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(10, 10, 10, 0.5);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--blood-deep);
            border-radius: 0;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: var(--blood-glow);
            box-shadow: 0 0 6px rgba(177, 18, 27, 0.6);
        }
        
        /* GLASS MORPHISM EFFECTS */
        .glass-panel {
            background: rgba(20, 20, 20, 0.7);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(122, 15, 20, 0.1);
        }
    </style>
</head>
<body>
    <!-- BACKGROUND LAYERS -->
    <div class="bg-container">
        <div class="brick-bg"></div>
        <div class="blood-overlay"></div>
        <div class="film-grain"></div>
    </div>
    
    <!-- SCROLL INDICATOR -->
    <div class="scroll-indicator">
        <div class="scroll-dot active" data-section="home"></div>
        <div class="scroll-dot" data-section="services"></div>
        <div class="scroll-dot" data-section="areas"></div>
        <div class="scroll-dot" data-section="testimonials"></div>
        <div class="scroll-dot" data-section="contact"></div>
    </div>
    
    <!-- HEADER -->
    <header id="main-header">
        <div class="container header-container">
            <a href="#home" class="logo">NOCTURNE</a>
            
            <button class="mobile-menu-btn" id="mobileMenuBtn">
                <i class="fas fa-bars"></i>
            </button>
            
            <nav>
                <ul id="navMenu">
                    <li><a href="#home">GARAGE</a></li>
                    <li><a href="#services">SERVICES</a></li>
                    <li><a href="#areas">LOCATIONS</a></li>
                    <li><a href="#testimonials">CLIENTS</a></li>
                    <li><a href="#contact" class="nav-cta">INQUIRE</a></li>
                </ul>
            </nav>
        </div>
    </header>
    
    <!-- HERO SECTION WITH CAR IMAGE -->
    <section class="hero" id="home">
        <div class="hero-bg"></div>
        <div class="hero-overlay"></div>
        <div class="container">
            <div class="hero-content">
                <h1>NOCTURNE GARAGE</h1>
                <div class="hero-line"></div>
                <p class="hero-tagline">Where precision meets discretion. A private automotive service for collectors who value subtlety over spectacle. Work performed under cover of darkness.</p>
                <a href="#contact" class="hero-button">REQUEST ACCESS</a>
            </div>
        </div>
    </section>
    
    <!-- SERVICES -->
    <section class="services" id="services">
        <div class="container">
            <h2 class="section-title">SERVICES</h2>
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-shield-alt"></i>
                    </div>
                    <h3>ARMOR TREATMENT</h3>
                    <p>Advanced nanotechnology protection that bonds at molecular level. Creates an impenetrable barrier while preserving original factory finish.</p>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-gem"></i>
                    </div>
                    <h3>PRECISION CORRECTION</h3>
                    <p>Elimination of surface imperfections through meticulous compounding. Finish measured to within 2 microns of factory specification.</p>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-tint"></i>
                    </div>
                    <h3>CERAMIC SEALANT</h3>
                    <p>Proprietary 10H ceramic formula that creates permanent hydrophobic protection. Self-cleaning properties maintained for 5+ years.</p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- AREAS -->
    <section class="service-areas" id="areas">
        <div class="container">
            <h2 class="section-title">LOCATIONS</h2>
            <div class="areas-container">
                <p style="color: var(--text-muted); margin-bottom: 40px; font-weight: 300; max-width: 600px;">Private facilities located in secure, undisclosed locations. Access granted by appointment only to vetted clients.</p>
                <div class="areas-grid">
                    <div class="area-item">DOWNTOWN BUNKER</div>
                    <div class="area-item">NORTHSIDE FACILITY</div>
                    <div class="area-item">WATERFRONT GARAGE</div>
                    <div class="area-item">INDUSTRIAL COMPLEX</div>
                    <div class="area-item">PRIVATE ESTATES</div>
                    <div class="area-item">SECURE STORAGE</div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- TESTIMONIALS -->
    <section class="testimonials" id="testimonials">
        <div class="container">
            <h2 class="section-title">CLIENT TESTIMONY</h2>
            <div class="testimonial-slider">
                <div class="testimonial">
                    <p class="testimonial-text">Nocturne maintains my collection with surgical precision. Their discretion is absolute, and their work is flawless. They understand that true luxury doesn't announce itself.</p>
                    <div>
                        <span class="testimonial-author">VINCENT S.</span>
                        <span class="testimonial-date">• COLLECTOR</span>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <!-- CONTACT -->
    <section class="contact" id="contact">
        <div class="container">
            <h2 class="section-title">INQUIRY</h2>
            <div class="contact-container">
                <div class="contact-info">
                    <h3>ACCESS REQUEST</h3>
                    <p style="color: var(--text-muted); margin-bottom: 50px; font-weight: 300; line-height: 1.8;">All engagements begin with a vetting process. Complete the form or contact through secure channels. We will respond within 48 hours.</p>
                    
                    <div class="contact-detail">
                        <div class="contact-icon">
                            <i class="fas fa-phone-alt"></i>
                        </div>
                        <div>
                            <p style="color: var(--text-muted); font-size: 13px; letter-spacing: 0.1em; margin-bottom: 5px;">SECURE LINE</p>
                            <p class="contact-phone">(555) 340-NOCT</p>
                        </div>
                    </div>
                    
                    <div class="contact-detail">
                        <div class="contact-icon">
                            <i class="fas fa-envelope"></i>
                        </div>
                        <div>
                            <p style="color: var(--text-muted); font-size: 13px; letter-spacing: 0.1em; margin-bottom: 5px;">ENCRYPTED</p>
                            <p class="contact-phone">ACCESS@NOCTURNE.GARAGE</p>
                        </div>
                    </div>
                    
                    <div class="contact-detail">
                        <div class="contact-icon">
                            <i class="fas fa-clock"></i>
                        </div>
                        <div>
                            <p style="color: var(--text-muted); font-size: 13px; letter-spacing: 0.1em; margin-bottom: 5px;">OPERATIONS</p>
                            <p style="color: var(--text-offwhite);">2000 - 0600 • BY APPOINTMENT</p>
                        </div>
                    </div>
                </div>
                
                <div class="contact-form">
                    <form id="accessForm">
                        <div class="form-group">
                            <label for="name">FULL NAME</label>
                            <input type="text" id="name" class="form-control" placeholder="" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="contact">PREFERRED CONTACT</label>
                            <select id="contact" class="form-control" required>
                                <option value="">SELECT METHOD</option>
                                <option value="secure">SECURE LINE</option>
                                <option value="encrypted">ENCRYPTED EMAIL</option>
                                <option value="signal">SIGNAL</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="vehicle">VEHICLE(S)</label>
                            <input type="text" id="vehicle" class="form-control" placeholder="" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="service">SERVICE REQUEST</label>
                            <select id="service" class="form-control" required>
                                <option value="">SELECT SERVICE</option>
                                <option value="armor">ARMOR TREATMENT</option>
                                <option value="precision">PRECISION CORRECTION</option>
                                <option value="ceramic">CERAMIC SEALANT</option>
                                <option value="full">FULL PRESERVATION</option>
                            </select>
                        </div>
                        
                        <button type="submit" class="submit-btn">REQUEST VETTING</button>
                    </form>
                </div>
            </div>
        </div>
    </section>
    
    <!-- FOOTER -->
    <footer>
        <div class="container">
            <div class="footer-container">
                <div class="footer-section">
                    <h4>NOCTURNE</h4>
                    <p style="color: var(--text-muted); font-size: 14px; line-height: 1.8; font-weight: 300;">A private automotive preservation service operating with discretion and precision for serious collectors.</p>
                </div>
                
                <div class="footer-section">
                    <h4>NAVIGATION</h4>
                    <ul class="footer-links">
                        <li><a href="#home">Garage</a></li>
                        <li><a href="#services">Services</a></li>
                        <li><a href="#areas">Locations</a></li>
                        <li><a href="#testimonials">Clients</a></li>
                        <li><a href="#contact">Inquiry</a></li>
                    </ul>
                </div>
                
                <div class="footer-section">
                    <h4>SERVICES</h4>
                    <ul class="footer-links">
                        <li><a href="#">Armor Treatment</a></li>
                        <li><a href="#">Precision Correction</a></li>
                        <li><a href="#">Ceramic Sealant</a></li>
                        <li><a href="#">Interior Preservation</a></li>
                    </ul>
                </div>
                
                <div class="footer-section">
                    <h4>CONTACT</h4>
                    <ul class="footer-links">
                        <li>SECURE: (555) 340-NOCT</li>
                        <li>ENCRYPTED: ACCESS@NOCTURNE.GARAGE</li>
                        <li>HOURS: 2000 - 0600</li>
                        <li>APPOINTMENT ONLY</li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>© 2024 NOCTURNE GARAGE. ALL ACCESS RESTRICTED. DISCRETION GUARANTEED.</p>
            </div>
        </div>
    </footer>
    
    <script>
        // Mobile Menu
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const navMenu = document.getElementById('navMenu');
        
        mobileMenuBtn.addEventListener('click', () => {
            navMenu.classList.toggle('active');
            mobileMenuBtn.innerHTML = navMenu.classList.contains('active') 
                ? '<i class="fas fa-times"></i>' 
                : '<i class="fas fa-bars"></i>';
        });
        
        // Close mobile menu on link click
        document.querySelectorAll('nav a').forEach(link => {
            link.addEventListener('click', () => {
                navMenu.classList.remove('active');
                mobileMenuBtn.innerHTML = '<i class="fas fa-bars"></i>';
            });
        });
        
        // Header scroll effect
        const header = document.getElementById('main-header');
        window.addEventListener('scroll', () => {
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });
        
        // Form submission
        document.getElementById('accessForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const submitBtn = this.querySelector('.submit-btn');
            const originalText = submitBtn.textContent;
            
            submitBtn.textContent = 'REQUEST SENT';
            submitBtn.style.borderColor = 'var(--blood-deep)';
            submitBtn.style.boxShadow = '0 0 20px rgba(177, 18, 27, 0.2)';
            
            setTimeout(() => {
                submitBtn.textContent = originalText;
                submitBtn.style.borderColor = '';
                submitBtn.style.boxShadow = '';
                this.reset();
            }, 3000);
        });
        
        // Scroll indicator
        const sections = document.querySelectorAll('section[id]');
        const scrollDots = document.querySelectorAll('.scroll-dot');
        
        function updateScrollIndicator() {
            let currentSection = '';
            const scrollPosition = window.scrollY + 200;
            
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                
                if (scrollPosition >= sectionTop && scrollPosition < sectionTop + sectionHeight) {
                    currentSection = section.getAttribute('id');
                }
            });
            
            scrollDots.forEach(dot => {
                dot.classList.remove('active');
                if (dot.getAttribute('data-section') === currentSection) {
                    dot.classList.add('active');
                }
            });
        }
        
        // Scroll to section when clicking dots
        scrollDots.forEach(dot => {
            dot.addEventListener('click', function() {
                const sectionId = this.getAttribute('data-section');
                const targetSection = document.getElementById(sectionId);
                
                if (targetSection) {
                    window.scrollTo({
                        top: targetSection.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Smooth scroll for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 100,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Initialize
        updateScrollIndicator();
        window.addEventListener('scroll', updateScrollIndicator);
        
        // Service card icon glow on hover
        document.querySelectorAll('.service-card').forEach(card => {
            const icon = card.querySelector('.service-icon');
            
            card.addEventListener('mouseenter', () => {
                icon.style.textShadow = '0 0 12px rgba(177, 18, 27, 0.7)';
            });
            
            card.addEventListener('mouseleave', () => {
                icon.style.textShadow = '0 0 8px rgba(177, 18, 27, 0.5)';
            });
        });
        
        // Add subtle parallax to hero background
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const heroBg = document.querySelector('.hero-bg');
            if (heroBg) {
                heroBg.style.transform = `translateY(${scrolled * 0.3}px)`;
            }
        });
    </script>
</body>
</html>
