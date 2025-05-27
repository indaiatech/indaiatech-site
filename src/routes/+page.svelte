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
        padding: 2rem 3rem;
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
        gap: 2rem;
    }

    .nav-links a {
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

    .benefits, .steps, .testimonials {
        padding: 6rem 4rem;
        color: #f8fafd;
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
        background: linear-gradient(55deg,#dcccff,#b694ff 74%,#a880ff);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .benefits-grid, .steps-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 2rem;
    }

    .benefit-card, .step-card {
        background: rgba(255, 255, 255, 0.05);
        padding: 2rem;
        border-radius: 15px;
        backdrop-filter: blur(10px);
        transition: transform 0.3s ease;
    }

    .benefit-card:hover, .step-card:hover {
        transform: translateY(-5px);
    }

    .benefit-card h3, .step-card h3 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        color: #a880ff;
    }

    .benefit-card ul {
        list-style: none;
        padding: 0;
    }

    .benefit-card li {
        margin-bottom: 0.8rem;
        padding-left: 1.5rem;
        position: relative;
    }

    .benefit-card li::before {
        content: "→";
        position: absolute;
        left: 0;
        color: #a880ff;
    }

    .step-number {
        width: 40px;
        height: 40px;
        background: linear-gradient(252deg, #6521FF, #B493FF);
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 1rem;
        font-weight: bold;
    }

    .testimonials-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 2rem;
    }

    .testimonial-card {
        background: rgba(255, 255, 255, 0.05);
        padding: 2rem;
        border-radius: 15px;
        backdrop-filter: blur(10px);
        text-align: center;
    }

    .testimonial-card p {
        font-size: 1.2rem;
        margin-bottom: 1rem;
        font-style: italic;
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

    .footer {
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(10px);
        padding: 4rem 2rem 2rem;
        color: #f8fafd;
        position: relative;
        z-index: 2;
    }

    .footer-content {
        max-width: 1200px;
        margin: 0 auto;
    }

    .footer-grid {
        display: grid;
        grid-template-columns: 2fr repeat(3, 1fr);
        gap: 4rem;
        margin-bottom: 3rem;
    }

    .footer-brand {
        max-width: 300px;
    }

    .footer-logo {
        margin-bottom: 1rem;
    }

    .footer-logo .indaia {
        font-size: 1.5rem;
        font-weight: 200;
        color: #f8fafd;
    }

    .footer-logo .tech {
        font-size: 1.5rem;
        font-weight: 400;
        background: linear-gradient(252deg, #6521FF, #B493FF);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .footer-brand p {
        color: #aaa;
        margin-bottom: 1.5rem;
        font-size: 0.9rem;
    }

    .social-links {
        display: flex;
        gap: 1rem;
    }

    .social-links a {
        color: #f8fafd;
        transition: color 0.3s ease;
    }

    .social-links a:hover {
        color: #a880ff;
    }

    .footer-links h4 {
        color: #f8fafd;
        font-size: 1.1rem;
        margin-bottom: 1.5rem;
        font-weight: 400;
    }

    .footer-links ul {
        list-style: none;
        padding: 0;
        margin: 0;
    }

    .footer-links li {
        margin-bottom: 0.8rem;
    }

    .footer-links a {
        color: #f8fafd;
        text-decoration: none;
        transition: color 0.3s ease;
        font-size: 0.9rem;
        text-decoration: underline;
        text-decoration-color: #a880ff;
        text-decoration-thickness: 2px;
        text-underline-offset: 6px;
    }

    .footer-links a:hover {
        color: #a880ff;
        text-decoration-thickness: 2px;
    }

    .footer-bottom {
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        padding-top: 2rem;
        text-align: center;
        font-size: 0.9rem;
        color: #aaa;
    }

    @media (max-width: 768px) {
        .footer-grid {
            grid-template-columns: 1fr;
            gap: 2rem;
        }
        
        .footer-brand {
            max-width: 100%;
            text-align: center;
        }
        
        .social-links {
            justify-content: center;
        }
        
        .footer-links {
            text-align: center;
        }
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

<section class="benefits">
    <div class="section-content">
        <h2>Benefícios</h2>
        <div class="benefits-grid">
            <div class="benefit-card">
                <h3>Para Você</h3>
                <ul>
                    <li>Atendimento 24/7</li>
                    <li>Automatizado mas humanizado</li>
                    <li>Respostas instantâneas</li>
                    <li>Suporte personalizado</li>
                </ul>
            </div>
            <div class="benefit-card">
                <h3>Para Profissionais</h3>
                <ul>
                    <li>Gestão centralizada</li>
                    <li>Análise de desempenho</li>
                    <li>Relatórios detalhados</li>
                    <li>Escalabilidade</li>
                </ul>
            </div>
        </div>
    </div>
</section>

<section class="steps">
    <div class="section-content">
        <h2>Como Começar</h2>
        <div class="steps-grid">
            <div class="step-card">
                <div class="step-number">1</div>
                <h3>Personalização Simples</h3>
                <p>Configure sua identidade e respostas em minutos</p>
            </div>
            <div class="step-card">
                <div class="step-number">2</div>
                <h3>Integração WhatsApp</h3>
                <p>Conecte seu número e comece imediatamente</p>
            </div>
            <div class="step-card">
                <div class="step-number">3</div>
                <h3>Dashboard Completo</h3>
                <p>Acesse métricas e gerencie conversas</p>
            </div>
            <div class="step-card">
                <div class="step-number">4</div>
                <h3>Notificações e Reports</h3>
                <p>Receba atualizações e relatórios detalhados</p>
            </div>
        </div>
    </div>
</section>

<section class="testimonials">
    <div class="section-content">
        <h2>O Que Dizem Nossos Usuários</h2>
        <div class="testimonials-grid">
            <div class="testimonial-card">
                <p>"Como um novo funcionário eficiente e eficaz"</p>
                <span class="author">- Cliente Satisfeito</span>
            </div>
            <div class="testimonial-card">
                <p>"Sempre disponível"</p>
                <span class="author">- Empresa Parceira</span>
            </div>
            <div class="testimonial-card">
                <p>"Agora sem mais dores de cabeça"</p>
                <span class="author">- Usuário Premium</span>
            </div>
        </div>
    </div>
</section>

<footer class="footer">
    <div class="footer-content">
        <div class="footer-grid">
            <div class="footer-brand">
                <div class="footer-logo">
                    <span class="indaia">indaia</span>
                    <span class="tech">tech</span>
                </div>
                <p>Transformando atendimento com inteligência artificial</p>
                <div class="social-links">
                    <a href="https://instagram.com/indaiatech" target="_blank" rel="noopener noreferrer">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect>
                            <path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path>
                            <line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line>
                        </svg>
                    </a>
                </div>
            </div>
            
            <div class="footer-links">
                <h4>Empresa</h4>
                <ul>
                    <li><a href="#about">Sobre nós</a></li>
                    <li><a href="#careers">Carreiras</a></li>
                    <li><a href="#contact">Contato</a></li>
                </ul>
            </div>
            
            <div class="footer-links">
                <h4>Produto</h4>
                <ul>
                    <li><a href="#features">Funcionalidades</a></li>
                    <li><a href="#pricing">Preços</a></li>
                    <li><a href="#faq">FAQ</a></li>
                </ul>
            </div>
            
            <div class="footer-links">
                <h4>Legal</h4>
                <ul>
                    <li><a href="#privacy">Privacidade</a></li>
                    <li><a href="#terms">Termos</a></li>
                    <li><a href="#security">Segurança</a></li>
                </ul>
            </div>
        </div>
        
        <div class="footer-bottom">
            <p>&copy; {new Date().getFullYear()} IndaiaTech. Todos os direitos reservados.</p>
        </div>
    </div>
</footer>

<script>
    // Mouse follow effect for logo tech text
    const logoContainer = document.querySelector('.logo-container');
    const techText = document.querySelector('.tech');
    
    // Set initial gradient animation
    function updateGradient() {
        const angle = (Date.now() / 50) % 360;
        const startColor = `hsl(${angle}, 100%, 50%)`;
        const endColor = `hsl(${(angle + 60) % 360}, 100%, 70%)`;
        
        techText.style.setProperty('--gradient-angle', `${angle}deg`);
        techText.style.setProperty('--gradient-start', startColor);
        techText.style.setProperty('--gradient-end', endColor);
        techText.style.textShadow = `0 0 15px rgba(101, 33, 255, 0.5)`;
        
        requestAnimationFrame(updateGradient);
    }
    
    // Start the gradient animation
    updateGradient();
    
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