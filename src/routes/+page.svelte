<script lang="ts">
    import { onMount } from 'svelte';
    import Footer from '$lib/components/Footer.svelte';

    onMount(() => {
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
    });
</script>

<div>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
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
            backdrop-filter: blur(10px);
            z-index: 1000;
        }

        .logo-container {
            display: flex;
            align-items: flex-end;
            position: relative;
            cursor: pointer;
            z-index: 1000;
        }

        .indaia, .tech {
            display: inline;
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
            margin-bottom: 2rem;
            font-weight: 200;
            font-family: 'Nunito', sans-serif;
        }

        .hero h1 strong {
            font-weight: 400;
        }

        .hero p {
            font-size: 1.2rem;
            margin: 0;
            font-family: 'Nunito', sans-serif;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; line-height: 2.5rem; }
            .hero p { font-size: 1.2rem; }
            .indaia, .tech { font-size: 1.5rem; }
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
    </nav>

    <div class="hero">
        <video class="video-background" autoplay muted loop playsinline>
            <source src="/videos/app-demo.mp4" type="video/mp4">
        </video>
        <div class="video-gradient"></div>
        <div class="hero-content">
            <h1>The future of your business is <strong>intelligent</strong></h1>
            <p>Indaia Tech builds AI solutions, an AI platform and AI products for companies.</p>
        </div>
    </div>

    <Footer lang="en" />
</div>
