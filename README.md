<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prodigy Pawn - Professional Online Chess Coaching</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #2c3e50;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
            --text: #2c3e50;
            --bg-primary: #ffffff;
            --bg-secondary: #ecf0f1;
            --card-bg: #ffffff;
            --border-color: #ecf0f1;
        }

        [data-theme="dark"] {
            --primary: #ecf0f1;
            --secondary: #3498db;
            --accent: #e74c3c;
            --light: #2c3e50;
            --dark: #1a252f;
            --text: #ecf0f1;
            --bg-primary: #1a252f;
            --bg-secondary: #2c3e50;
            --card-bg: #34495e;
            --border-color: #4a5f7f;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text);
            background: var(--bg-primary);
            overflow-x: hidden;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        /* Navigation */
        nav {
            background: var(--card-bg);
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            padding: 1rem 0;
            transition: background-color 0.3s ease;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 1.8rem;
            font-weight: bold;
            color: var(--text);
        }

        .logo-icon {
            font-size: 2.5rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            color: var(--text);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
            padding: 0.5rem 0;
            position: relative;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--secondary);
            transition: width 0.3s;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Theme Toggle Button */
        .theme-toggle {
            background: var(--secondary);
            border: none;
            color: white;
            width: 45px;
            height: 45px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.3rem;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            box-shadow: 0 2px 8px rgba(0,0,0,0.15);
        }

        .theme-toggle:hover {
            transform: scale(1.1) rotate(15deg);
            box-shadow: 0 4px 12px rgba(52, 152, 219, 0.4);
        }

        .nav-cta {
            background: var(--secondary);
            color: white;
            padding: 0.75rem 1.5rem;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
        }

        .nav-cta:hover {
            background: #2980b9;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.3);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(135deg, var(--dark) 0%, var(--primary) 100%);
            color: white;
            padding: 8rem 2rem 6rem;
            margin-top: 70px;
            text-align: center;
            transition: background 0.3s ease;
        }

        .hero-content {
            max-width: 900px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            line-height: 1.2;
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            opacity: 0.95;
        }

        .hero-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
        }

        .btn-primary {
            background: var(--secondary);
            color: white;
            padding: 1rem 2.5rem;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            transition: all 0.3s;
            border: 2px solid var(--secondary);
        }

        .btn-primary:hover {
            background: #2980b9;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(52, 152, 219, 0.4);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            padding: 1rem 2.5rem;
            border-radius: 5px;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            border: 2px solid white;
            transition: all 0.3s;
        }

        .btn-secondary:hover {
            background: white;
            color: var(--dark);
        }

        /* Mission Section */
        .mission {
            padding: 5rem 2rem;
            background: var(--bg-primary);
            transition: background-color 0.3s ease;
        }

        .mission-content {
            max-width: 1000px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            color: var(--text);
            text-align: center;
            margin-bottom: 1rem;
        }

        .section-subtitle {
            text-align: center;
            color: var(--text);
            opacity: 0.7;
            font-size: 1.2rem;
            margin-bottom: 3rem;
        }

        .mission-text {
            font-size: 1.1rem;
            line-height: 1.8;
            color: var(--text);
            opacity: 0.85;
            margin-bottom: 2rem;
            text-align: center;
        }

        .goals-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 1.5rem;
            margin-top: 3rem;
        }

        .goal-card {
            background: var(--card-bg);
            padding: 1.5rem;
            border-radius: 8px;
            border-left: 4px solid var(--secondary);
            transition: all 0.3s;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }

        .goal-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .goal-card h3 {
            color: var(--text);
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .goal-card p {
            color: var(--text);
            opacity: 0.8;
        }

        .goal-icon {
            color: var(--secondary);
            font-size: 1.3rem;
        }

        /* Features Section */
        .features {
            padding: 5rem 2rem;
            background: var(--bg-secondary);
            transition: background-color 0.3s ease;
        }

        .features-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .features-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .feature-card {
            background: var(--card-bg);
            padding: 2.5rem 2rem;
            border-radius: 8px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .feature-icon {
            font-size: 3.5rem;
            margin-bottom: 1rem;
        }

        .feature-card h3 {
            color: var(--text);
            margin-bottom: 1rem;
            font-size: 1.4rem;
        }

        .feature-card p {
            color: var(--text);
            opacity: 0.8;
            line-height: 1.6;
        }

        /* Programs Section */
        .programs {
            padding: 5rem 2rem;
            background: var(--bg-primary);
            transition: background-color 0.3s ease;
        }

        .programs-container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .programs-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .program-card {
            background: var(--card-bg);
            border: 2px solid var(--border-color);
            border-radius: 8px;
            overflow: hidden;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }

        .program-card:hover {
            border-color: var(--secondary);
            box-shadow: 0 10px 30px rgba(52, 152, 219, 0.2);
            transform: translateY(-5px);
        }

        .program-header {
            background: var(--dark);
            color: white;
            padding: 2rem;
            text-align: center;
        }

        .program-header h3 {
            font-size: 1.8rem;
            margin-bottom: 0.5rem;
        }

        .program-level {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .program-body {
            padding: 2rem;
        }

        .program-features {
            list-style: none;
            margin-bottom: 1.5rem;
        }

        .program-features li {
            padding: 0.75rem 0;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            align-items: center;
            gap: 0.75rem;
            color: var(--text);
        }

        .program-features li:last-child {
            border-bottom: none;
        }

        .checkmark {
            color: var(--secondary);
            font-weight: bold;
        }

        .program-price {
            text-align: center;
            padding: 1.5rem;
            background: var(--bg-secondary);
            font-size: 1.1rem;
            color: var(--text);
            font-weight: 600;
        }

        /* Stats Section */
        .stats {
            padding: 4rem 2rem;
            background: var(--dark);
            color: white;
            transition: background-color 0.3s ease;
        }

        .stats-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
            text-align: center;
        }

        .stat-item h3 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            color: var(--secondary);
        }

        .stat-item p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        /* Contact Section */
        .contact {
            padding: 5rem 2rem;
            background: var(--bg-primary);
            transition: background-color 0.3s ease;
        }

        .contact-container {
            max-width: 1000px;
            margin: 0 auto;
        }

        .contact-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .contact-card {
            background: var(--card-bg);
            padding: 2rem;
            border-radius: 8px;
            text-align: center;
            transition: all 0.3s;
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }

        .contact-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .contact-icon {
            font-size: 3rem;
            color: var(--secondary);
            margin-bottom: 1rem;
        }

        .contact-card h3 {
            color: var(--text);
            margin-bottom: 0.5rem;
        }

        .contact-card p {
            color: var(--text);
            opacity: 0.8;
        }

        .contact-card a {
            color: var(--secondary);
            text-decoration: none;
            font-weight: 500;
        }

        .contact-card a:hover {
            text-decoration: underline;
        }

        /* CTA Section */
        .cta {
            padding: 5rem 2rem;
            background: linear-gradient(135deg, var(--secondary) 0%, #2980b9 100%);
            color: white;
            text-align: center;
        }

        .cta h2 {
            font-size: 2.5rem;
            margin-bottom: 1rem;
        }

        .cta p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            opacity: 0.95;
        }

        .cta .btn-primary {
            background: white;
            color: var(--secondary);
        }

        .cta .btn-primary:hover {
            background: var(--bg-secondary);
            color: var(--dark);
        }

        /* Footer */
        footer {
            background: var(--dark);
            color: white;
            padding: 3rem 2rem 1.5rem;
            transition: background-color 0.3s ease;
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            text-align: center;
        }

        .footer-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
            flex-wrap: wrap;
        }

        .footer-links a {
            color: white;
            text-decoration: none;
            opacity: 0.8;
            transition: opacity 0.3s;
        }

        .footer-links a:hover {
            opacity: 1;
        }

        .copyright {
            opacity: 0.7;
            font-size: 0.9rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255,255,255,0.1);
        }

        /* Mobile Menu */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            color: var(--text);
            cursor: pointer;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .hero p {
                font-size: 1.1rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .stats-container {
                grid-template-columns: repeat(2, 1fr);
            }

            .hero-buttons {
                flex-direction: column;
            }

            .btn-primary, .btn-secondary {
                width: 100%;
            }
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .fade-in {
            animation: fadeInUp 0.6s ease-out;
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <div class="logo">
                <span class="logo-icon">♟️</span>
                <span>Prodigy Pawn</span>
            </div>
            <ul class="nav-links">
                <li><a href="#about">About</a></li>
                <li><a href="#programs">Programs</a></li>
                <li><a href="#features">Features</a></li>
                <li><a href="#contact">Contact</a></li>
                <li><button class="theme-toggle" id="themeToggle" aria-label="Toggle theme">🌙</button></li>
            </ul>
            <a href="#contact" class="nav-cta">Get Started</a>
            <button class="mobile-menu-btn">☰</button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <div class="hero-content fade-in">
            <h1>Master Chess with Professional Online Coaching</h1>
            <p>Empowering minds through strategic thinking, discipline, and sportsmanship</p>
            <div class="hero-buttons">
                <a href="#contact" class="btn-primary">Start Your Journey</a>
                <a href="#programs" class="btn-secondary">Explore Programs</a>
            </div>
        </div>
    </section>

    <!-- Mission Section -->
    <section class="mission" id="about">
        <div class="mission-content">
            <h2 class="section-title">Our Mission</h2>
            <p class="section-subtitle">Nurturing Young Minds Through Chess</p>
            
            <p class="mission-text">
                Our community is dedicated to nurturing young minds through the game of chess. Our association focuses on empowering youth by developing strategic thinking, discipline, patience, confidence, and sportsmanship.
            </p>

            <div class="goals-grid">
                <div class="goal-card">
                    <h3><span class="goal-icon">🎯</span> Promote Chess</h3>
                    <p>Promote chess among children and young players of all skill levels</p>
                </div>
                <div class="goal-card">
                    <h3><span class="goal-icon">📚</span> Structured Learning</h3>
                    <p>Provide structured learning, training, and expert guidance</p>
                </div>
                <div class="goal-card">
                    <h3><span class="goal-icon">🏆</span> Tournaments & Events</h3>
                    <p>Organize training sessions, tournaments, and friendly matches</p>
                </div>
                <div class="goal-card">
                    <h3><span class="goal-icon">⚔️</span> Healthy Competition</h3>
                    <p>Encourage healthy competition and sportsmanship</p>
                </div>
                <div class="goal-card">
                    <h3><span class="goal-icon">⭐</span> Nurture Talent</h3>
                    <p>Identify and support emerging chess talent</p>
                </div>
                <div class="goal-card">
                    <h3><span class="goal-icon">💡</span> Build Skills</h3>
                    <p>Build leadership, focus, and decision-making skills</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Features Section -->
    <section class="features" id="features">
        <div class="features-container">
            <h2 class="section-title">Why Choose Prodigy Pawn?</h2>
            <p class="section-subtitle">Comprehensive chess education for all ages</p>
            
            <div class="features-grid">
                <div class="feature-card">
                    <div class="feature-icon">👨‍🏫</div>
                    <h3>Certified Coaches</h3>
                    <p>Learn from experienced and certified chess coaches with proven track records</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">👥</div>
                    <h3>One-on-One Coaching</h3>
                    <p>Personalized attention with customized training plans for rapid improvement</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">👨‍👩‍👧‍👦</div>
                    <h3>Group Classes</h3>
                    <p>Interactive group sessions for collaborative learning and peer motivation</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🎓</div>
                    <h3>Beginner to Advanced</h3>
                    <p>Structured curriculum designed for all skill levels and ages</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">🏅</div>
                    <h3>Tournament Preparation</h3>
                    <p>Specialized training to excel in competitive chess tournaments</p>
                </div>
                <div class="feature-card">
                    <div class="feature-icon">⏰</div>
                    <h3>Flexible Scheduling</h3>
                    <p>Choose class timings that fit your schedule with online convenience</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Programs Section -->
    <section class="programs" id="programs">
        <div class="programs-container">
            <h2 class="section-title">Our Programs</h2>
            <p class="section-subtitle">Tailored training for every player</p>
            
            <div class="programs-grid">
                <div class="program-card">
                    <div class="program-header">
                        <h3>Beginner Program</h3>
                        <p class="program-level">For New Players</p>
                    </div>
                    <div class="program-body">
                        <ul class="program-features">
                            <li><span class="checkmark">✓</span> Learn chess fundamentals</li>
                            <li><span class="checkmark">✓</span> Basic tactics and strategies</li>
                            <li><span class="checkmark">✓</span> Opening principles</li>
                            <li><span class="checkmark">✓</span> Endgame basics</li>
                            <li><span class="checkmark">✓</span> Practice games</li>
                        </ul>
                    </div>
                    <div class="program-price">Contact for Pricing</div>
                </div>

                <div class="program-card">
                    <div class="program-header">
                        <h3>Intermediate Program</h3>
                        <p class="program-level">For Developing Players</p>
                    </div>
                    <div class="program-body">
                        <ul class="program-features">
                            <li><span class="checkmark">✓</span> Advanced tactics</li>
                            <li><span class="checkmark">✓</span> Opening repertoire</li>
                            <li><span class="checkmark">✓</span> Positional understanding</li>
                            <li><span class="checkmark">✓</span> Game analysis</li>
                            <li><span class="checkmark">✓</span> Tournament preparation</li>
                        </ul>
                    </div>
                    <div class="program-price">Contact for Pricing</div>
                </div>

                <div class="program-card">
                    <div class="program-header">
                        <h3>Advanced Program</h3>
                        <p class="program-level">For Competitive Players</p>
                    </div>
                    <div class="program-body">
                        <ul class="program-features">
                            <li><span class="checkmark">✓</span> Master-level strategies</li>
                            <li><span class="checkmark">✓</span> Deep opening preparation</li>
                            <li><span class="checkmark">✓</span> Complex endgames</li>
                            <li><span class="checkmark">✓</span> Professional game analysis</li>
                            <li><span class="checkmark">✓</span> Tournament coaching</li>
                        </ul>
                    </div>
                    <div class="program-price">Contact for Pricing</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Stats Section -->
    <section class="stats">
        <div class="stats-container">
            <div class="stat-item">
                <h3>500+</h3>
                <p>Students Trained</p>
            </div>
            <div class="stat-item">
                <h3>15+</h3>
                <p>Expert Coaches</p>
            </div>
            <div class="stat-item">
                <h3>95%</h3>
                <p>Success Rate</p>
            </div>
            <div class="stat-item">
                <h3>50+</h3>
                <p>Tournaments Organized</p>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="contact" id="contact">
        <div class="contact-container">
            <h2 class="section-title">Get In Touch</h2>
            <p class="section-subtitle">Ready to start your chess journey?</p>
            
            <div class="contact-grid">
                <div class="contact-card">
                    <div class="contact-icon">📧</div>
                    <h3>Email Us</h3>
                    <p><a href="mailto:blacklistmg7@gmail.com">blacklistmg7@gmail.com</a></p>
                </div>
                <div class="contact-card">
                    <div class="contact-icon">📱</div>
                    <h3>Call Us</h3>
                    <p><a href="tel:+916003281596">+91-6003281596</a></p>
                </div>
                <div class="contact-card">
                    <div class="contact-icon">💬</div>
                    <h3>WhatsApp</h3>
                    <p><a href="https://wa.me/916003281596">Chat with us</a></p>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA Section -->
    <section class="cta">
        <div class="cta-content">
            <h2>Ready to Make Your Move?</h2>
            <p>Join Prodigy Pawn today and unlock your chess potential</p>
            <a href="#contact" class="btn-primary">Enroll Now</a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-container">
            <div class="footer-links">
                <a href="#about">About</a>
                <a href="#programs">Programs</a>
                <a href="#features">Features</a>
                <a href="#contact">Contact</a>
            </div>
            <div class="copyright">
                <p>&copy; 2024 Prodigy Pawn. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <script>
        // Theme Toggle Functionality
        const themeToggle = document.getElementById('themeToggle');
        const htmlElement = document.documentElement;
        
        // Check for saved theme preference or default to 'light'
        const currentTheme = localStorage.getItem('theme') || 'light';
        htmlElement.setAttribute('data-theme', currentTheme);
        updateThemeIcon(currentTheme);

        themeToggle.addEventListener('click', () => {
            const currentTheme = htmlElement.getAttribute('data-theme');
            const newTheme = currentTheme === 'light' ? 'dark' : 'light';
            
            htmlElement.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', newTheme);
            updateThemeIcon(newTheme);
        });

        function updateThemeIcon(theme) {
            themeToggle.textContent = theme === 'light' ? '🌙' : '☀️';
        }

        // Smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
