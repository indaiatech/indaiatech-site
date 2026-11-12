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
            <h1 class="indaia">indaia</h1>
            <h1 class="tech">tech</h1>
        </div>
    </nav>

    <div class="hero">
        <div class="hero-content">
            <h1>The future of your business is <strong>intelligent</strong></h1>
            <p>Indaia Tech builds AI solutions, an AI platform and AI products for companies.</p>
        </div>
    </div>

    <Footer />
</div>
