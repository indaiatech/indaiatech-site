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
        pointer-events: none;
        z-index: 1;
    }

    .dot {
        position: absolute;
        width: var(--dot-size, 1px);
        height: var(--dot-size, 1px);
        background: rgba(255, 255, 255, var(--dot-opacity, 0.08));
        border-radius: 50%;
        transition: transform var(--transition-speed, 0.3s) ease, background var(--transition-speed, 0.3s) ease;
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
    }

    .step-card img {
        z-index: 10;
        position: relative;
    }

    .benefit-card:hover, .step-card:hover {
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

    .footer {
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(10px);
        padding: 16rem 4rem 4rem;
        color: #f8fafd;
        position: relative;
        z-index: 2;
    }

    .footer-content {
        max-width: 1200px;
        margin: 0 auto;
    }

    .footer-grid {
        /* margin-bottom: 4rem; */
    }

    .footer-brand {
        max-width: 600px;
    }

    .footer-logo {
        margin-bottom: 2rem;
    }

    .footer-logo .indaia {
        font-size: 2rem;
        font-weight: 200;
        color: #f8fafd;
    }

    .footer-logo .tech {
        font-size: 2rem;
        font-weight: 400;
        background: linear-gradient(252deg, #6521FF, #B493FF);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .footer-tagline {
        font-size: 1.5rem;
        color: #f8fafd;
        margin-bottom: 1.5rem;
        line-height: 1.4;
    }

    .footer-description {
        color: #aaa;
        font-size: 1.1rem;
        line-height: 1.6;
    }

    .rocket-container {
        position: relative;
        width: 100%;
        height: 100px;
        /* margin: 2rem 0; */
        overflow: hidden;
        image-rendering: pixelated;
    }

    .rocket {
        position: absolute;
        width: 30px;
        height: 10px;
        cursor: pointer;
        user-select: none;
        z-index: 1000;
        filter: drop-shadow(0 0 10px rgba(101, 33, 255, 0.3)) 
                contrast(1.2) 
                brightness(1.2);
        transition: transform 0.3s ease, filter 0.3s ease;
        transform-origin: center;
        image-rendering: pixelated;
        bottom: 0;
    }

    .rocket-body {
        position: absolute;
        width: 0;
        height: 0;
        border-left: 15px solid transparent;
        border-right: 15px solid transparent;
        border-bottom: 30px solid #B493FF;
    }

    .rocket-thruster {
        position: absolute;
        top: 30px;
        left: -10px;
        width: 20px;
        height: 10px;
        background: linear-gradient(to bottom, #6521FF, transparent);
        clip-path: polygon(0 0, 100% 0, 50% 100%);
    }

    .rocket:hover {
        transform: scale(1.2);
        filter: drop-shadow(0 0 20px rgba(101, 33, 255, 0.5)) 
                contrast(1.4) 
                brightness(1.4);
    }

    .bullet {
        position: fixed;
        width: 2px;
        height: 15px;
        background: #B493FF;
        pointer-events: none;
        z-index: 9999;
        opacity: 0;
        filter: drop-shadow(0 0 15px rgba(101, 33, 255, 0.8)) 
                contrast(1.2) 
                brightness(1.2);
        transition: opacity 0.3s ease;
        image-rendering: pixelated;
    }

    .bullet::before {
        content: '';
        position: absolute;
        top: -5px;
        left: -1px;
        width: 4px;
        height: 4px;
        background: #B493FF;
        border-radius: 50%;
        filter: blur(1px);
    }

    .bullet.active {
        opacity: 1;
    }

    .bullet-trail {
        position: absolute;
        width: 1px;
        height: 20px;
        background: linear-gradient(
            to bottom,
            #B493FF,
            transparent
        );
        opacity: 0.8;
        transform-origin: bottom;
        pointer-events: none;
        image-rendering: pixelated;
        box-shadow: 0 0 10px rgba(101, 33, 255, 0.5);
    }

    .pixel-dust {
        position: absolute;
        width: 2px;
        height: 2px;
        background: #B493FF;
        border-radius: 0;
        pointer-events: none;
        opacity: 0;
        filter: blur(0.5px);
    }

    @keyframes pixelDust {
        0% {
            transform: translate(0, 0) scale(1);
            opacity: 0.8;
        }
        100% {
            transform: translate(var(--tx), var(--ty)) scale(0);
            opacity: 0;
        }
    }

    .footer-bottom {
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        padding-top: 2rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 1rem;
        color: #aaa;
    }

    .footer-links {
        display: flex;
        gap: 2rem;
    }

    .footer-links a {
        color: #f8fafd;
        text-decoration: none;
        transition: color 0.3s ease;
        font-size: 1rem;
        text-decoration: underline;
        text-decoration-color: #a880ff;
        text-decoration-thickness: 2px;
        text-underline-offset: 6px;
    }

    .footer-links a:hover {
        color: #a880ff;
    }

    @media (max-width: 768px) {
        .footer {
            padding: 4rem 2rem 2rem;
        }
        
        .footer-bottom {
            flex-direction: column;
            gap: 1rem;
            text-align: center;
        }
        
        .footer-links {
            justify-content: center;
        }
        
        .footer-tagline {
            font-size: 1.3rem;
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
        <a href="#features">comece GRÁTIS</a>
        <a href="#pricing">language (pt-BR)</a>
        <a href="#contact">entrar</a>
    </div>
</nav>

<div class="hero">
    <video class="video-background" autoplay muted loop playsinline>
        <source src="/videos/app-demo.mp4" type="video/mp4">
    </video>
    <div class="video-gradient"></div>
    <div class="hero-content">
        <h1><strong>Atendimento</strong> por <strong>AI</strong><br>com <strong>personalização</strong></h1>
        <h2>GRÁTIS por 1 mês.</h2>
        <p>depois R$ 99/mês, cancele quando quiser, sem multa.</p>
        <button class="cta-button"><span>Comece Já!</span></button>
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
                    <li>Automatizado mas humanizado</li>
                    <li>Respostas quase que instantâneas para simular atendimento humado</li>
                    <li>Fluxo personalizado para casos especiais</li>
                </ul>
            </div>
            <div class="benefit-card">
                <h3>Para você</h3>
                <ul>
                    <li>Qualidade no atendimento</li>
                    <li>Gestão centralizada</li>
                    <li>Sem gestão de pessoas</li>
                    <li>Relatórios detalhados</li>
                    <li>Custo baixo</li>
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

<footer class="footer">
    <div class="footer-content">
        <div class="footer-grid">
            <div class="footer-brand">
                <div class="footer-logo">
                    <span class="indaia">indaia</span>
                    <span class="tech">tech</span>
                </div>
                <p class="footer-tagline">Transformando atendimento com inteligência artificial</p>
                <p class="footer-description">Somos uma empresa focada em transformar o atendimento ao cliente através de soluções inovadoras de inteligência artificial, tornando o processo mais eficiente e personalizado.</p>
            </div>
        </div>
        
        <div class="rocket-container">
            <div class="rocket">
                <div class="rocket-body"></div>
                <div class="rocket-thruster"></div>
            </div>
        </div>
        
        <div class="footer-bottom">
            <div class="footer-links">
                <a href="#privacy">Privacidade</a>
                <a href="#terms">Termos de uso</a>
            </div>
            <p>&copy; {new Date().getFullYear()} indaiatech. Todos os direitos reservados.</p>
        </div>
    </div>
</footer>

<script>
    // Dots pattern configuration
    const dotsConfig = {
        count: 600,
        size: 1,
        baseOpacity: 0.08,
        maxOpacity: 0.5,
        interactionRadius: 200,
        maxScale: 3,
        clustering: 0.8,
        transitionSpeed: 0.3,
        gridSpacing: 20,  // Space between dots in pixels
        gridOffset: 10    // Offset to create a more natural look
    };

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

    // Create interactive dots pattern
    function createDotsPattern() {
        const container = document.getElementById('dotsPattern');
        const dots = [];

        // Calculate grid dimensions
        const containerWidth = container.offsetWidth;
        const containerHeight = container.offsetHeight;
        const cols = Math.ceil(containerWidth / dotsConfig.gridSpacing);
        const rows = Math.ceil(containerHeight / dotsConfig.gridSpacing);

        // Create grid of dots
        for (let row = 0; row < rows; row++) {
            for (let col = 0; col < cols; col++) {
                const dot = document.createElement('div');
                dot.className = 'dot';
                
                // Calculate position with slight offset for natural look
                const offsetX = (Math.random() - 0.5) * dotsConfig.gridOffset;
                const offsetY = (Math.random() - 0.5) * dotsConfig.gridOffset;
                
                const x = (col * dotsConfig.gridSpacing) + offsetX;
                const y = (row * dotsConfig.gridSpacing) + offsetY;
                
                dot.style.left = `${x}px`;
                dot.style.top = `${y}px`;
                
                container.appendChild(dot);
                dots.push(dot);
            }
        }

        // Mouse move effect
        document.querySelector('.benefits').addEventListener('mousemove', (e) => {
            const rect = e.currentTarget.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;

            dots.forEach(dot => {
                const dotX = parseFloat(dot.style.left);
                const dotY = parseFloat(dot.style.top);
                
                const distance = Math.sqrt(
                    Math.pow(x - dotX, 2) + 
                    Math.pow(y - dotY, 2)
                );
                
                if (distance < dotsConfig.interactionRadius) {
                    const intensity = 1 - (distance / dotsConfig.interactionRadius);
                    dot.style.transform = `scale(${1 + intensity * dotsConfig.maxScale})`;
                    dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity + intensity * (dotsConfig.maxOpacity - dotsConfig.baseOpacity)})`;
                } else {
                    dot.style.transform = 'scale(1)';
                    dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity})`;
                }
            });
        });

        // Reset dots on mouse leave
        document.querySelector('.benefits').addEventListener('mouseleave', () => {
            dots.forEach(dot => {
                dot.style.transform = 'scale(1)';
                dot.style.background = `rgba(255, 255, 255, ${dotsConfig.baseOpacity})`;
            });
        });

        // Handle window resize
        let resizeTimeout;
        window.addEventListener('resize', () => {
            clearTimeout(resizeTimeout);
            resizeTimeout = setTimeout(() => {
                // Remove all existing dots
                dots.forEach(dot => dot.remove());
                // Recreate the pattern
                createDotsPattern();
            }, 250);
        });
    }

    // Initialize dots pattern
    createDotsPattern();

    // Rocket and bullet functionality
    const rocket = document.querySelector('.rocket');
    const rocketContainer = document.querySelector('.rocket-container');
    const footerGrid = document.querySelector('.footer-grid');
    let bullet = null;
    let lastMouseX = 0;
    let targetX = 0;
    let currentX = 0;
    let animationFrame = null;
    let isFiring = false;
    let lastFireTime = 0;
    const fireRate = 100; // Minimum time between shots in milliseconds

    // Prevent space key from scrolling
    document.addEventListener('keydown', (e) => {
        if (e.code === 'Space') {
            e.preventDefault();
            if (!isFiring) {
                isFiring = true;
                fireBullet();
                
                // Set up continuous firing
                const fireInterval = setInterval(() => {
                    if (isFiring) {
                        fireBullet();
                    } else {
                        clearInterval(fireInterval);
                    }
                }, fireRate);
            }
        }
    });

    document.addEventListener('keyup', (e) => {
        if (e.code === 'Space') {
            isFiring = false;
        }
    });

    // Handle mouse down for continuous firing from footer-grid and rocket-container
    [footerGrid, rocketContainer].forEach(element => {
        element.addEventListener('mousedown', () => {
            isFiring = true;
            fireBullet(); // Fire immediately on click
            
            // Set up continuous firing
            const fireInterval = setInterval(() => {
                if (isFiring) {
                    fireBullet();
                } else {
                    clearInterval(fireInterval);
                }
            }, fireRate);
        });
    });

    // Handle mouse up to stop firing
    document.addEventListener('mouseup', () => {
        isFiring = false;
    });

    // Create bullet element
    function createBullet() {
        const bulletElement = document.createElement('div');
        bulletElement.className = 'bullet';
        document.body.appendChild(bulletElement);
        return bulletElement;
    }

    // Create bullet trail
    function createBulletTrail() {
        const trail = document.createElement('div');
        trail.className = 'bullet-trail';
        document.body.appendChild(trail);
        return trail;
    }

    // Create pixel dust effect
    function createPixelDust(x, y) {
        const dust = document.createElement('div');
        dust.className = 'pixel-dust';
        dust.style.left = `${x}px`;
        dust.style.top = `${y}px`;
        
        // Random direction
        const angle = Math.random() * Math.PI * 2;
        const distance = 20 + Math.random() * 30;
        const tx = Math.cos(angle) * distance;
        const ty = Math.sin(angle) * distance;
        
        dust.style.setProperty('--tx', `${tx}px`);
        dust.style.setProperty('--ty', `${ty}px`);
        
        document.body.appendChild(dust);
        
        const animation = dust.animate([
            { transform: 'translate(0, 0) scale(1)', opacity: 0.8 },
            { transform: `translate(${tx}px, ${ty}px) scale(0)`, opacity: 0 }
        ], {
            duration: 500 + Math.random() * 500,
            easing: 'ease-out',
            fill: 'forwards'
        });
        
        animation.onfinish = () => dust.remove();
    }

    // Smooth animation function
    function animateRocket() {
        const dx = targetX - currentX;
        currentX += dx * 0.1; // Smoothing factor
        
        if (Math.abs(dx) > 0.1) {
            rocket.style.left = `${currentX}px`;
        } else {
            rocket.style.left = `${targetX}px`;
        }
        
        // Always request next frame to keep movement smooth
        animationFrame = requestAnimationFrame(animateRocket);
    }

    // Start the animation loop
    animateRocket();

    // Handle mouse move for rocket
    document.addEventListener('mousemove', (e) => {
        const containerRect = rocketContainer.getBoundingClientRect();
        const rocketWidth = rocket.offsetWidth;
        
        // Calculate target position
        targetX = Math.max(0, Math.min(
            e.clientX - containerRect.left - (rocketWidth / 2),
            containerRect.width - rocketWidth
        ));
        
        lastMouseX = e.clientX;
    });

    // Fire bullet function
    function fireBullet() {
        const now = Date.now();
        if (now - lastFireTime < fireRate) return; // Rate limiting
        
        lastFireTime = now;
        const rocketRect = rocket.getBoundingClientRect();
        const bullet = createBullet();
        const trail = createBulletTrail();
        
        // Position bullet and trail at rocket's center
        const bulletX = rocketRect.left + rocketRect.width / 2;
        const bulletY = rocketRect.top;
        
        bullet.style.left = `${bulletX}px`;
        bullet.style.top = `${bulletY}px`;
        
        trail.style.left = `${bulletX}px`;
        trail.style.top = `${bulletY}px`;
        
        // Create initial pixel dust
        for (let i = 0; i < 3; i++) {
            createPixelDust(bulletX, bulletY);
        }
        
        // Trigger animation
        requestAnimationFrame(() => {
            bullet.classList.add('active');
            
            // Animate bullet upward with pixel dust trail
            const animation = bullet.animate([
                { transform: 'translateY(0)', opacity: 1 },
                { transform: 'translateY(-100vh)', opacity: 0 }
            ], {
                duration: 1500,
                easing: 'ease-out',
                fill: 'forwards'
            });
            
            // Create pixel dust during animation
            const dustInterval = setInterval(() => {
                const currentY = parseFloat(bullet.style.top);
                createPixelDust(bulletX, currentY);
            }, 30);
            
            // Animate trail
            const trailAnimation = trail.animate([
                { transform: 'scaleY(1)', opacity: 0.8 },
                { transform: 'scaleY(0)', opacity: 0 }
            ], {
                duration: 1500,
                easing: 'ease-out',
                fill: 'forwards'
            });
            
            // Remove elements after animation
            animation.onfinish = () => {
                clearInterval(dustInterval);
                bullet.remove();
                trail.remove();
            };
        });
    }

    // Clean up animation frame on unmount
    onDestroy(() => {
        if (animationFrame) {
            cancelAnimationFrame(animationFrame);
        }
    });
</script>
</div>