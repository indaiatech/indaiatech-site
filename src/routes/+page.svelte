<script lang="ts">
    import Footer from '$lib/components/Footer.svelte';
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
            background: radial-gradient(ellipse 80% 60% at 70% 20%, rgba(101, 33, 255, 0.15), transparent), #000;
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
            display: inline-block;
            text-decoration: none;
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

        .section {
            padding: 6rem 4rem;
            color: #e0e0e0;
            position: relative;
            z-index: 2;
            background: #1a1a1a;
        }

        .section.alt {
            background: #262626;
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
            color: transparent;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 2rem;
        }

        .card {
            background: rgba(255, 255, 255, 0.03);
            padding: 2rem;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            transition: transform 0.3s ease, background 0.3s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2);
            position: relative;
            overflow: hidden;
        }

        .card:hover {
            transform: translateY(-5px);
            background: rgba(255, 255, 255, 0.05);
        }

        .card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #f2f2f2;
            font-weight: 400;
        }

        .card p {
            font-size: 1.05rem;
            line-height: 1.6;
            margin: 0;
        }

        .card ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .card li {
            margin-bottom: 0.8rem;
            padding-left: 1.5rem;
            position: relative;
            color: #e0e0e0;
        }

        .card li:last-child {
            margin-bottom: 0;
        }

        .card li::before {
            content: "→";
            position: absolute;
            left: 0;
            color: #a880ff;
        }

        .card-link {
            display: inline-block;
            margin-top: 1.5rem;
            color: #a880ff;
            font-weight: 600;
            text-decoration: underline;
            text-decoration-color: #a880ff;
            text-decoration-thickness: 2px;
            text-underline-offset: 6px;
        }

        .card-link:hover {
            color: #c4a8ff;
        }

        .about p {
            font-size: 1.15rem;
            line-height: 1.8;
            margin: 0 0 1.5rem 0;
            text-align: center;
        }

        .about p:last-child {
            margin-bottom: 0;
        }

        @media (max-width: 768px) {
            .hero h1 { font-size: 2.5rem; line-height: 2.5rem; }
            .hero h2 { font-size: 2rem; }
            .hero p { font-size: 1.2rem; }
            .section { padding: 4rem 2rem; }
            .indaia, .tech { font-size: 1.5rem; }
        }
    </style>

    <nav class="navbar">
        <div class="logo-container">
            <h1 class="indaia">indaia</h1>
            <h1 class="tech">tech</h1>
        </div>
    </nav>

    <div class="hero">
        <div class="hero-content">
            <h1>O futuro da sua empresa é <strong>inteligente</strong></h1>
            <h2>Soluções, plataforma e produtos de AI</h2>
            <p>Colocamos inteligência artificial para trabalhar dentro do seu negócio.</p>
            <a class="cta-button" href="#empresa"><span>Saiba mais</span></a>
        </div>
    </div>

    <section class="section" id="empresa">
        <div class="section-content">
            <h2>A empresa</h2>
            <div class="about">
                <p>A indaiatech é uma empresa de tecnologia de Indaiatuba, São Paulo, focada em inteligência artificial. Desenvolvemos soluções sob medida, mantemos uma plataforma de AI e criamos produtos que usam IA para resolver problemas reais de empresas.</p>
                <p>Time de alta performance, todos sócios do negócio — comprometimento total com cada projeto, do primeiro contato ao resultado.</p>
            </div>
        </div>
    </section>

    <section class="section alt" id="solucoes">
        <div class="section-content">
            <h2>Soluções AI</h2>
            <div class="grid">
                <div class="card">
                    <h3>Atendimento com AI</h3>
                    <ul>
                        <li>Agentes de IA que atendem seus clientes</li>
                        <li>Respostas naturais, 24/7</li>
                        <li>Integração com os seus canais</li>
                    </ul>
                </div>
                <div class="card">
                    <h3>Automação inteligente</h3>
                    <ul>
                        <li>Processos repetitivos executados por IA</li>
                        <li>Menos erro operacional</li>
                        <li>Mais tempo para o que importa</li>
                    </ul>
                </div>
                <div class="card">
                    <h3>Dados e insights</h3>
                    <ul>
                        <li>Análise inteligente dos seus dados</li>
                        <li>Informação clara para decidir</li>
                        <li>Relatórios sob medida</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section class="section" id="plataforma">
        <div class="section-content">
            <h2>Plataforma AI</h2>
            <div class="grid">
                <div class="card">
                    <h3>A base que conecta AI ao seu negócio</h3>
                    <ul>
                        <li>Treinamento com os dados da sua empresa</li>
                        <li>Integração com WhatsApp, web e outros canais</li>
                        <li>Evolui com novos modelos e produtos</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section class="section alt" id="produtos">
        <div class="section-content">
            <h2>Produtos AI</h2>
            <div class="grid">
                <div class="card">
                    <h3>AI Assistant</h3>
                    <p>Atendimento por inteligência artificial para o seu negócio.</p>
                    <a class="card-link" href="/ai-assistant">Conhecer o AI Assistant →</a>
                </div>
            </div>
        </div>
    </section>

    <Footer />
</div>
