<div>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@200;600&display=swap" rel="stylesheet">
<style>
    body {
        margin: 0;
        padding: 0;
        background: #0a0a0a;
        font-family: 'Nunito', sans-serif;
        overflow-x: hidden;
        cursor: default;
    }

    .navbar {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 2rem 3rem 0 3rem;
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
        font-weight: 500;
        font-size: 2rem;
        color: #a880ff;
        margin: 0;
        padding: 0;
        line-height: 1;
        margin-left: 2px;
        opacity: 0;
        transform: translateX(30px);
        animation: slideInRight 1.2s ease-out 0.8s forwards;
        position: relative;
        --gradient-angle: 252deg;
        --gradient-start: #6521FF;
        --gradient-end: #B493FF;
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

    .nav-links {
        display: flex;
        gap: 2rem;
    }

    .nav-links a {
        color: #f8fafd;
        text-decoration: underline;
        text-decoration-color: #f2f2f2;
        text-decoration-thickness: 1px;
        text-underline-offset: 4px;
        font-weight: 200;
        font-family: 'Nunito', sans-serif;
        transition: color 0.3s ease;
    }

    .nav-links a:hover {
        color: #00d4ff;
        text-decoration-color: #00d4ff;
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

    .hero-content {
        max-width: 800px;
        padding: 4rem;
        z-index: 4;
    }

    .hero h1 {
        font-size: 3.5rem;
        margin-bottom: 1rem;
        font-weight: 200;
        font-family: 'Nunito', sans-serif;
    }

    .hero h1 strong {
        font-weight: 400;
    }

    .hero h2 {
        font-size: 2.5rem;
        margin-bottom: 1rem;
        font-family: 'Nunito', sans-serif;
        background: linear-gradient(55deg,#dcccff,#b694ff 74%,#a880ff);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        color: transparent;
    }

    .hero p {
        font-size: 1.2rem;
        margin-bottom: 2rem;
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

    .bg-pattern {
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
    }

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
        <a href="#features">comece grátis</a>
        <a href="#pricing">language (pt-BR)</a>
        <a href="#contact">entrar</a>
    </div>
</nav>

<div class="hero">
    <video class="video-background" autoplay muted loop playsinline>
        <source src="/videos/app-demo.mp4" type="video/mp4">
    </video>
    <div class="hero-content">
        <h1><strong>Atendimento</strong> por <strong>AI</strong><br>com <strong>personalização</strong></h1>
        <h2>GRÁTIS por 3 meses.</h2>
        <p>depois R$ 99/mês, cancele quando quiser, sem multa.</p>
        <button class="cta-button"><span>Comece Já!</span></button>
    </div>
</div>

<div class="bg-pattern"></div>

<script>
    // Mouse follow effect for logo tech text
    const logoContainer = document.querySelector('.logo-container');
    const techText = document.querySelector('.tech');
    
    logoContainer.addEventListener('mousemove', (e) => {
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

    // Mouse follow effect for button
    const button = document.querySelector('.cta-button');
    button.addEventListener('mousemove', (e) => {
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

    // Create additional floating particles
    function createParticle() {
        const particle = document.createElement('div');
        particle.className = 'particle';

        // Random position around the logo
        const angle = Math.random() * 2 * Math.PI;
        const radius = 15 + Math.random() * 10; // Reduced radius: 15-25px from center
        const logo = document.querySelector('.logo-container');
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

        document.querySelector('.particles').appendChild(particle);

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
</script>
</div>