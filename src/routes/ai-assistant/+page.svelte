<script lang="ts">
    import { onMount } from 'svelte';
    import Footer from '$lib/components/Footer.svelte';

    let showLanguageDropdown: boolean = false;
    let currentLanguage: 'pt-BR' | 'en-US' = 'pt-BR';

    function toggleLanguageDropdown(): void {
        showLanguageDropdown = !showLanguageDropdown;
    }

    function selectLanguage(lang: 'pt-BR' | 'en-US'): void {
        currentLanguage = lang;
        showLanguageDropdown = false;
        // Here you can add logic to change the language of your application
    }

    onMount(() => {
        // Close dropdown when clicking outside
        const handleClickOutside = (e: MouseEvent) => {
            const dropdown = document.querySelector('.language-dropdown');
            if (dropdown && !dropdown.contains(e.target as Node)) {
                showLanguageDropdown = false;
            }
        };

        document.addEventListener('click', handleClickOutside);

        // Dots pattern configuration
        const dotsConfig = {
            gridSize: 20, // 20x20 grid
            size: 1,
            baseOpacity: 0.03,
            maxOpacity: 1.0,   // Changed to full opacity
            interactionRadius: 80,
            maxScale: 1.5,
            transitionSpeed: 0.2
        };

        // Mouse follow effect for logo tech text
        const logoContainer = document.querySelector('.logo-container') as HTMLElement | null;
        const techText = document.querySelector('.tech') as HTMLElement | null;
        
        // Set initial gradient animation
        function updateGradient() {
            if (!techText) return;
            const angle = (Date.now() / 50) % 360;
            const startColor = `hsl(${angle}, 100%, 50%)`;
            const endColor = `hsl(${(angle + 60) % 360}, 100%, 70%)`;
            
            techText.style.setProperty('--gradient-angle', `${angle}deg`);
            techText.style.setProperty('--gradient-start', startColor);
            techText.style.setProperty('--gradient-end', endColor);
            techText.style.textShadow = `0 0 15px rgba(101, 33, 255, 0.5)`;
            
            requestAnimationFrame(updateGradient);
        }
        
        updateGradient();
        
        if (logoContainer && techText) {
            logoContainer.addEventListener('mousemove', (e: MouseEvent) => {
                const rect = logoContainer.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                
                const angle = Math.atan2(y - centerY, x - centerX) * (180 / Math.PI);
                const gradientAngle = (angle + 90) % 360;
                
                // Calculate distance from center for intensity
                const distance = Math.sqrt(Math.pow(x - centerX, 2) + Math.pow(y - centerY, 2));
                const maxDistance = Math.sqrt(Math.pow(rect.width/2, 2) + Math.pow(rect.height/2, 2));
                const intensity = 1 - (distance / maxDistance);
                
                // Update gradient with more intense colors based on mouse position
                const startColor = `hsl(${gradientAngle}, 100%, 50%)`;
                const endColor = `hsl(${(gradientAngle + 60) % 360}, 100%, 70%)`;
                
                techText.style.setProperty('--gradient-angle', `${gradientAngle}deg`);
                techText.style.setProperty('--gradient-start', startColor);
                techText.style.setProperty('--gradient-end', endColor);
                techText.style.textShadow = `0 0 ${10 + intensity * 20}px rgba(101, 33, 255, ${0.3 + intensity * 0.4})`;
            });

            logoContainer.addEventListener('mouseleave', () => {
                techText.style.setProperty('--gradient-angle', '252deg');
                techText.style.setProperty('--gradient-start', '#6521FF');
                techText.style.setProperty('--gradient-end', '#B493FF');
                techText.style.textShadow = 'none';
            });
        }

        // Mouse follow effect for button
        const button = document.querySelector('.cta-button') as HTMLElement | null;
        if (button) {
            button.addEventListener('mousemove', (e: MouseEvent) => {
                const rect = button.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                
                const centerX = rect.width / 2;
                const centerY = rect.height / 2;
                
                const angle = Math.atan2(y - centerY, x - centerX) * (180 / Math.PI);
                const gradientAngle = (angle + 90) % 360;
                
                // Calculate distance from center for intensity
                const distance = Math.sqrt(Math.pow(x - centerX, 2) + Math.pow(y - centerY, 2));
                const maxDistance = Math.sqrt(Math.pow(rect.width/2, 2) + Math.pow(rect.height/2, 2));
                const intensity = 1 - (distance / maxDistance);
                
                // Update gradient with more intense colors based on mouse position
                const startColor = `hsl(${gradientAngle}, 100%, 50%)`;
                const endColor = `hsl(${(gradientAngle + 60) % 360}, 100%, 70%)`;
                
                button.style.background = `linear-gradient(${gradientAngle}deg, ${startColor}, ${endColor})`;
                button.style.boxShadow = `0 0 ${20 + intensity * 30}px rgba(101, 33, 255, ${0.3 + intensity * 0.4})`;
            });

            button.addEventListener('mouseleave', () => {
                button.style.background = 'linear-gradient(252deg, #6521FF, #B493FF)';
                button.style.boxShadow = '0 0 20px rgba(101, 33, 255, 0.3)';
            });
        }

        // Create additional floating particles
        function createParticle() {
            const particle = document.createElement('div');
            particle.className = 'particle';

            // Random position around the logo
            const angle = Math.random() * 2 * Math.PI;
            const radius = 15 + Math.random() * 10; // Reduced radius: 15-25px from center
            const logo = document.querySelector('.logo-container') as HTMLElement | null;
            if (!logo) return;
            const logoRect = logo.getBoundingClientRect();
            const containerW = logo.offsetWidth;
            const containerH = logo.offsetHeight;
            // Center of the logo in percent
            const centerX = 50;
            const centerY = 50;
            // Calculate position in percent
            const left = centerX + Math.cos(angle) * radius * 0.9 / containerW * 100;
            const top = centerY + Math.sin(angle) * radius * 0.9 / containerH * 100;
            particle.style.left = `calc(${left}% - 1px)`;
            particle.style.top = `calc(${top}% - 1px)`;

            // Animate outward from the center with continuous fade out
            const moveAngle = angle + (Math.random() - 0.5) * Math.PI / 3; // More vertical variation
            const moveDistance = 200 + Math.random() * 100; // Much increased horizontal movement: 200-300px
            const wobbleAmount = 30 + Math.random() * 20; // Random wobble amount
            const wobbleFrequency = 2 + Math.random() * 2; // Random wobble frequency

            particle.animate([
                { 
                    transform: 'translate(0, 0) scale(1)', 
                    opacity: 0 
                },
                { 
                    transform: `translate(${Math.cos(moveAngle) * moveDistance * 0.2}px, ${Math.sin(moveAngle) * moveDistance * 0.2}px) scale(1)`, 
                    opacity: 0.9,
                    offset: 0.3
                },
                { 
                    transform: `translate(${Math.cos(moveAngle) * moveDistance * 0.5}px, ${Math.sin(moveAngle) * moveDistance * 0.3}px) scale(0.8)`, 
                    opacity: 0.3,
                    offset: 0.6
                },
                { 
                    transform: `translate(${Math.cos(moveAngle) * moveDistance}px, ${Math.sin(moveAngle) * moveDistance * 0.4}px) scale(0.5)`, 
                    opacity: 0 
                }
            ], {
                duration: 8000,
                easing: 'ease-out',
                fill: 'forwards'
            });

            const particlesContainer = document.querySelector('.particles');
            if (particlesContainer) {
                particlesContainer.appendChild(particle);
            }

            setTimeout(() => {
                particle.remove();
            }, 8000);
        }

        // Spawn particles periodically
        setInterval(() => {
            for (let i = 0; i < 2; i++) {
                createParticle();
            }
        }, 800);

        // Create interactive dots pattern
        function createDotsPattern() {
            const container = document.getElementById('dotsPattern') as HTMLElement | null;
            if (!container) {
                console.error('Dots container not found');
                return;
            }

            // Clear any existing dots
            container.innerHTML = '';
            const dots: HTMLElement[] = [];

            // Calculate grid dimensions
            const containerWidth = container.offsetWidth;
            const containerHeight = container.offsetHeight;
            const spacingX = containerWidth / (dotsConfig.gridSize + 1);
            const spacingY = containerHeight / (dotsConfig.gridSize + 1);

            // Create 20x20 grid of dots
            for (let row = 0; row < dotsConfig.gridSize; row++) {
                for (let col = 0; col < dotsConfig.gridSize; col++) {
                    const dot = document.createElement('div');
                    dot.className = 'dot';
                    
                    // Calculate position
                    const x = spacingX * (col + 1);
                    const y = spacingY * (row + 1);
                    
                    dot.style.left = `${x}px`;
                    dot.style.top = `${y}px`;
                    
                    container.appendChild(dot);
                    dots.push(dot);
                }
            }

            // Optimized mouse move effect
            let rafId: number | null = null;
            
            const updateDots = (x: number, y: number, rect: DOMRect) => {
                if (rafId) cancelAnimationFrame(rafId);
                
                rafId = requestAnimationFrame(() => {
                    dots.forEach(dot => {
                        const dotX = parseFloat(dot.style.left);
                        const dotY = parseFloat(dot.style.top);
                        
                        const distance = Math.sqrt(
                            Math.pow(x - dotX, 2) + 
                            Math.pow(y - dotY, 2)
                        );
                        
                        if (distance < dotsConfig.interactionRadius) {
                            const intensity = Math.pow(1 - (distance / dotsConfig.interactionRadius), 2);
                            dot.style.transform = `scale(${1 + intensity * dotsConfig.maxScale})`;
                            dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity + intensity * (dotsConfig.maxOpacity - dotsConfig.baseOpacity)})`;
                        } else {
                            dot.style.transform = 'scale(1)';
                            dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity})`;
                        }
                    });
                });
            };

            const handleMouseMove = (e: MouseEvent) => {
                const rect = container.getBoundingClientRect();
                const x = e.clientX - rect.left;
                const y = e.clientY - rect.top;
                updateDots(x, y, rect);
            };

            const handleMouseLeave = () => {
                if (rafId) cancelAnimationFrame(rafId);
                dots.forEach(dot => {
                    dot.style.transform = 'scale(1)';
                    dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity})`;
                });
            };

            // Add mouse move listeners to both container and benefit cards
            container.addEventListener('mousemove', handleMouseMove);
            container.addEventListener('mouseleave', handleMouseLeave);

            // Add mouse move listeners to benefit cards
            const benefitCards = document.querySelectorAll('.benefit-card');
            benefitCards.forEach(card => {
                card.addEventListener('mousemove', ((e: Event) => {
                    const mouseEvent = e as MouseEvent;
                    const rect = container.getBoundingClientRect();
                    const cardRect = card.getBoundingClientRect();
                    const x = mouseEvent.clientX - rect.left;
                    const y = mouseEvent.clientY - rect.top;
                    updateDots(x, y, rect);
                }) as EventListener);
            });

            // Optimized window resize handler
            let resizeTimeout: ReturnType<typeof setTimeout>;
            const handleResize = () => {
                clearTimeout(resizeTimeout);
                resizeTimeout = setTimeout(() => {
                    createDotsPattern();
                }, 250);
            };

            window.removeEventListener('resize', handleResize);
            window.addEventListener('resize', handleResize);
        }

        // Initialize dots pattern
        createDotsPattern();


        return () => {
            document.removeEventListener('click', handleClickOutside);
        };
    });
</script>

<div>
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@200;600&display=swap" rel="stylesheet">
<style>
    body {
        margin: 0;
        padding: 0;
        background: #000;
        font-family: 'Nunito', sans-serif;
        overflow-x: hidden;
        cursor: default;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    a, button {
        cursor: pointer!important;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
    }

    .navbar {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 3rem;
        /* background: rgba(10, 10, 10, 0.8); */
        backdrop-filter: blur(10px);
        z-index: 1000;
    }

    .logo-container {
        display: flex;
        align-items: flex-end;
        position: relative;
        cursor: pointer;
        z-index: 1000;
        position: relative;
    }

    .indaia, .tech {
        display: inline;
        background: none;
        -webkit-background-clip: initial;
        -webkit-text-fill-color: initial;
        background-clip: initial;
        text-fill-color: initial;
        color: inherit;
    }

    .indaia {
        font-family: 'Nunito', sans-serif;
        font-weight: 200;
        font-size: 2rem;
        color: #f8fafd;
        margin: 0;
        padding: 0;
        line-height: 1;
        opacity: 0;
        transform: translateX(-30px);
        animation: slideInLeft 1.2s ease-out 0.3s forwards;
        position: relative;
    }

    .tech {
        font-family: 'Nunito', sans-serif;
        font-weight: 400;
        font-size: 2rem;
        color: #a880ff;
        margin: 0;
        padding: 0;
        line-height: 1;
        margin-left: 2px;
        opacity: 0;
        transform: translateX(30px);
        animation: slideInRight 1.2s ease-out 0.8s forwards, gradientAnimation 3s linear infinite;
        position: relative;
        --gradient-angle: 252deg;
        --gradient-start: #6521FF;
        --gradient-end: #B493FF;
        background: linear-gradient(var(--gradient-angle), var(--gradient-start), var(--gradient-end));
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        color: transparent;
        transition: all 0.3s ease;
    }

    @keyframes slideInLeft {
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }

    @keyframes slideInRight {
        to {
            opacity: 1;
            transform: translateX(0);
        }
    }

    @keyframes gradientAnimation {
        0% {
            --gradient-angle: 0deg;
        }
        100% {
            --gradient-angle: 360deg;
        }
    }

    .particles {
        position: absolute;
        width: 100%;
        height: 100%;
        pointer-events: none;
        top: 0;
        left: 0;
    }

    .particle {
        position: absolute;
        width: 2px;
        height: 2px;
        background: #00d4ff;
        border-radius: 50%;
        opacity: 0;
    }

    .logo-container:hover .indaia {
    }

    .logo-container:hover .tech {
        background: linear-gradient(var(--gradient-angle), var(--gradient-start), var(--gradient-end));
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        color: transparent;
        transition: all 0.3s ease;
    }

    .nav-links {
        display: flex;
        gap: 0.6rem;
        position: relative;
    }

    .nav-links a {
        padding: 1rem;
        text-decoration: none;
        font-weight: 200;
        font-family: 'Nunito', sans-serif;
        transition: color 0.3s ease;
        color: #f8fafd;
        text-decoration: underline;
        text-decoration-color: #a880ff;
        text-decoration-thickness: 2px;
        text-underline-offset: 6px;
    }

    .nav-links a:hover {
        color: #a880ff;
        text-decoration-thickness: 2px;
    }

    .language-dropdown {
        position: relative;
        display: inline-block;
    }

    .language-dropdown-content {
        display: none;
        position: absolute;
        right: 0;
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(10px);
        min-width: 160px;
        box-shadow: 0 8px 16px rgba(0,0,0,0.2);
        z-index: 1001;
        border-radius: 8px;
        padding: 0.5rem 0;
    }

    .language-dropdown-content.show {
        display: block;
    }

    .language-dropdown-content a {
        color: #f8fafd;
        padding: 0.75rem 1rem;
        text-decoration: none;
        display: block;
        transition: all 0.3s ease;
        text-decoration: none;
    }

    .language-dropdown-content a:hover {
        background: rgba(168, 128, 255, 0.1);
        color: #a880ff;
    }

    .language-dropdown-content a.active {
        color: #a880ff;
        background: rgba(168, 128, 255, 0.1);
    }

    .hero {
        position: relative;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: left;
        text-align: left;
        color: #f8fafd;
        z-index: 1;
    }

    .hero::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(135deg, rgba(0,0,0,0.6) 50%, rgba(0,0,0,0) 100%);
        z-index: 2;
    }

    .video-background {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: 1;
    }

    /* .video-gradient {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 50%;
        background: linear-gradient(to bottom, transparent, rgba(0,0,0,1));
        z-index: 3;
    } */

    .video-gradient {
        position: absolute;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 30%;
        background: linear-gradient(to bottom, transparent, #1a1a1a);
        z-index: 3;
    }

    .hero-content {
        max-width: 800px;
        padding: 4rem;
        z-index: 4;
    }

    .hero h1 {
        font-size: 3.5rem;
        line-height: 3.5rem;
        margin-bottom: 4rem;
        font-weight: 200;
        font-family: 'Nunito', sans-serif;
    }

    .hero h1 strong {
        font-weight: 400;
    }

    .hero h2 {
        font-size: 2.5rem;
        margin-bottom: 0;
        font-family: 'Nunito', sans-serif;
        background: linear-gradient(55deg,#dcccff,#b694ff 74%,#a880ff);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        color: transparent;
    }

    .hero p {
        font-size: 1.2rem;
        margin: 0 0 2rem 0;
        font-family: 'Nunito', sans-serif;
    }

    .cta-button {
        background: linear-gradient(252deg, #6521FF, #B493FF);
        color: white;
        border: none;
        padding: 16px 32px;
        font-size: 16px;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        border-radius: 30px;
        cursor: pointer;
        transition: all 0.3s ease;
        font-weight: 500;
        letter-spacing: -0.01em;
        position: relative;
        overflow: hidden;
        box-shadow: 0 0 20px rgba(101, 33, 255, 0.3);
    }

    .cta-button::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(252deg, #5A1DE8, #A385E6);
        opacity: 0;
        transition: opacity 0.3s ease;
        filter: blur(10px);
    }

    .cta-button:hover::before {
        opacity: 0.5;
    }

    .cta-button span {
        position: relative;
        z-index: 1;
        text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
    }

    /* .bg-pattern {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        opacity: 0.03;
        background-image: 
            linear-gradient(90deg, #00d4ff 1px, transparent 1px),
            linear-gradient(180deg, #00d4ff 1px, transparent 1px);
        background-size: 50px 50px;
        animation: patternMove 20s linear infinite;
        z-index: -1;
    } */

    @keyframes patternMove {
        0% {
            transform: translate(0, 0);
        }
        100% {
            transform: translate(50px, 50px);
        }
    }

    @media (max-width: 768px) {
        .hero h1 { font-size: 2.5rem; }
        .hero h2 { font-size: 2rem; }
        .hero p { font-size: 1.2rem; }
        .nav-links { gap: 1rem; }
        .indaia, .tech { font-size: 1.5rem; }
    }

    .benefits {
        padding: 6rem 4rem;
        color: #e0e0e0;
        position: relative;
        z-index: 2;
        background: #1a1a1a;
        overflow: hidden;
    }

    .dots-pattern {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: all;
        z-index: 1;
        overflow: hidden;
    }

    .dot {
        position: absolute;
        width: 4px;
        height: 4px;
        background: rgba(255, 255, 255, var(--dot-opacity, 0.03));
        border-radius: 50%;
        transition: transform var(--transition-speed, 0.2s) ease, background var(--transition-speed, 0.2s) ease;
        pointer-events: none;
        will-change: transform, background;
    }

    .benefits .section-content {
        position: relative;
        z-index: 2;
    }

    .steps {
        padding: 6rem 4rem 10rem 4rem;
        color: #e0e0e0;
        position: relative;
        z-index: 2;
        background: #262626;
    }

    .testimonials {
        padding: 6rem 4rem 10rem 4rem;
        color: #e0e0e0;
        position: relative;
        z-index: 2;
        background: #1a1a1a;
        background-image: url('/images/bg.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        position: relative;
    }

    .testimonials::before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.7);
        z-index: 1;
    }

    .testimonials .section-content {
        position: relative;
        z-index: 2;
    }

    .section-content {
        max-width: 1200px;
        margin: 0 auto;
    }

    .section-content h2 {
        font-size: 2.5rem;
        margin-bottom: 3rem;
        text-align: center;
        font-weight: 200;
        background: linear-gradient(55deg,#a880ff,#b694ff 74%,#c4a8ff);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .benefits-grid, .steps-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 2rem;
    }

    .benefit-card, .step-card {
        background: rgba(255, 255, 255, 0.03);
        padding: 2rem;
        border-radius: 15px;
        backdrop-filter: blur(10px);
        transition: transform 0.3s ease;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
        position: relative;
        overflow: hidden;
    }

    .step-card img {
        width: 100%;
        height: auto;
        object-fit: contain;
        margin-bottom: 1rem;
        max-height: 200px;
        display: block;
        z-index: 10;
        position: relative;
    }

    .step-card:hover, .step-card:hover {
        transform: translateY(-5px);
        background: rgba(255, 255, 255, 0.05);
    }

    .benefit-card h3, .step-card h3 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        color: #f2f2f2;
        font-weight: 400;
    }

    .benefit-card ul {
        list-style: none;
        padding: 0;
    }

    .benefit-card li {
        margin-bottom: 0.8rem;
        padding-left: 1.5rem;
        position: relative;
        color: #e0e0e0;
    }

    .benefit-card li::before {
        content: "→";
        position: absolute;
        left: 0;
        color: #a880ff;
    }

    .step-number {
        position: absolute;
        top: -3rem;
        left: -2rem;
        font-size: 16rem;
        font-weight: 800;
        color: rgba(168, 128, 255, 0.15);
        line-height: 1;
        z-index: 1;
    }

    .testimonials-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 2rem;
    }

    .testimonial-card {
        background: rgba(255, 255, 255, 0.03);
        padding: 2rem;
        border-radius: 15px;
        backdrop-filter: blur(10px);
        text-align: center;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
    }

    .testimonial-card p {
        font-size: 1.2rem;
        margin-bottom: 1rem;
        font-style: italic;
        color: #e0e0e0;
    }

    .testimonial-card .author {
        color: #a880ff;
        font-weight: 600;
    }

    @media (max-width: 768px) {
        .benefits, .steps, .testimonials {
            padding: 4rem 2rem;
        }
        
        .section-content h2 {
            font-size: 2rem;
        }
    }

    .language-button {
        background: none;
        border: none;
        color: #f8fafd;
        font-family: 'Nunito', sans-serif;
        font-weight: 200;
        font-size: 1rem;
        cursor: pointer;
        text-decoration: underline;
        text-decoration-color: #a880ff;
        text-decoration-thickness: 2px;
        text-underline-offset: 6px;
        padding: 1rem;
    }

    .language-button:hover {
        color: #a880ff;
    }

    .language-option {
        background: none;
        border: none;
        color: #f8fafd;
        font-family: 'Nunito', sans-serif;
        font-weight: 200;
        font-size: 1rem;
        cursor: pointer;
        width: 100%;
        text-align: left;
        padding: 0.75rem 1rem;
        transition: all 0.3s ease;
    }

    .language-option:hover {
        background: rgba(168, 128, 255, 0.1);
        color: #a880ff;
    }

    .language-option.active {
        color: #a880ff;
        background: rgba(168, 128, 255, 0.1);
    }
</style>

<nav class="navbar">
    <div class="logo-container">
        <div class="particles">
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
        </div>
        <h1 class="indaia">indaia</h1>
        <h1 class="tech">tech</h1>
    </div>
    <div class="nav-links">
        <div class="language-dropdown">
            <button class="language-button" on:click={toggleLanguageDropdown}>language ({currentLanguage})</button>
            <div class="language-dropdown-content" class:show={showLanguageDropdown}>
                <button class="language-option" class:active={currentLanguage === 'pt-BR'} on:click={() => selectLanguage('pt-BR')}>Português (BR)</button>
                <button class="language-option" class:active={currentLanguage === 'en-US'} on:click={() => selectLanguage('en-US')}>English (US)</button>
            </div>
        </div>
        <a href="#contact">entrar</a>
    </div>
</nav>

<div class="hero">
    <video class="video-background" autoplay muted loop playsinline>
        <source src="/videos/app-demo.mp4" type="video/mp4">
    </video>
    <div class="video-gradient"></div>
    <div class="hero-content">
        <h1>O melhor <strong>atendimento</strong> por <strong>AI</strong><br>para o seu <strong>negócio</strong></h1>
        <h2>GRÁTIS por um mês!</h2>
        <p>depois R$ 99 por mês, cancele quando quiser, sem multa.</p>
        <button class="cta-button"><span>Eu quero!</span></button>
    </div>
</div>

<div class="bg-pattern"></div>

<section class="benefits">
    <div class="dots-pattern" id="dotsPattern"></div>
    <div class="section-content">
        <h2>Benefícios</h2>
        <div class="benefits-grid">
            <div class="benefit-card">
                <h3>Para seu cliente</h3>
                <ul>
                    <li>Atendimento 24/7</li>
                    <li>Respostas fluídas como o melhor do atendimento humado</li>
                    <li>Fluxo personalizado para casos especiais</li>
                </ul>
            </div>
            <div class="benefit-card">
                <h3>Para você</h3>
                <ul>
                    <li>Sem gestão de pessoas, sem demissões</li>
                    <li>Sem falhas, com a mesma qualidade no atendimento</li>
                    <li>Gestão centralizada</li>
                    <li>Relatórios detalhados</li>
                    <li>Custo extremamente baixo</li>
                </ul>
            </div>
        </div>
    </div>
</section>

<section class="steps">
    <div class="section-content">
        <h2>Como começar</h2>
        <div class="steps-grid">
            <div class="step-card">
                <img src="/images/0.png" alt="Personalização" class="step-image">
                <div class="step-number">1</div>
                <h3>Personalização</h3>
                <p>Em 2 min você já pode começar a usar.</p>
            </div>
            <div class="step-card">
                <img src="/images/4.png" alt="Integração WhatsApp" class="step-image">
                <div class="step-number">2</div>
                <h3>Integração WhatsApp</h3>
                <p>Conecte seu número e pronto!</p>
            </div>
            <div class="step-card">
                <img src="/images/2.png" alt="Dashboard Completo" class="step-image">
                <div class="step-number">3</div>
                <h3>Dashboard Completo</h3>
                <p>Acesse métricas e gerencie conversas de fluxos especiais</p>
            </div>
            <div class="step-card">
                <img src="/images/3.png" alt="Notificações e Reports" class="step-image">
                <div class="step-number">4</div>
                <h3>Notificações e Reports</h3>
                <p>Receba atualizações e relatórios detalhados</p>
            </div>
        </div>
    </div>
</section>

<section class="testimonials">
    <div class="section-content">
        <h2>Quem testou disse</h2>
        <div class="testimonials-grid">
            <div class="testimonial-card">
                <p>"É como um novo funcionário eficiente"</p>
                <span class="author">— Rafael Sato, advogado.</span>
            </div>
            <div class="testimonial-card">
                <p>"Nada como estar sempre disponível"</p>
                <span class="author">— Carlos Sanches, vendedor.</span>
            </div>
            <div class="testimonial-card">
                <p>"Agora sim, sem mais dores de cabeça"</p>
                <span class="author">— Cintia Menezes, dentista.</span>
            </div>
        </div>
    </div>
</section>

    <Footer />
</div>
