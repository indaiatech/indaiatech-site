<script lang="ts">
    import { onMount, onDestroy } from 'svelte';

    let { lang = 'pt' }: { lang?: 'pt' | 'en' } = $props();

    onMount(() => {
        // Rocket and bullet functionality
        const rocket = document.querySelector('.rocket') as HTMLElement | null;
        const footerGrid = document.querySelector('.footer-grid') as HTMLElement | null;
        let bullet = null;
        let lastMouseX = 0;
        let targetX = 0;
        let currentX = 0;
        let animationFrame: number | null = null;
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
        [footerGrid].forEach((element) => {
            if (element) {
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
            }
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
        function createPixelDust(x: number, y: number) {
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

        // Handle mouse move for rocket
        document.addEventListener('mousemove', (e: MouseEvent) => {
            const rocket = document.querySelector('.rocket') as HTMLElement | null;
            const rocketContainer = document.querySelector('.rocket-container') as HTMLElement | null;
            if (!rocket || !rocketContainer) return;
            
            const containerRect = rocketContainer.getBoundingClientRect();
            const rocketWidth = rocket.offsetWidth;
            
            // Calculate target position relative to the container
            targetX = Math.max(0, Math.min(
                e.clientX - containerRect.left - (rocketWidth / 2),
                containerRect.width - rocketWidth
            ));
        });

        // Smooth animation function
        function animateRocket() {
            const rocket = document.querySelector('.rocket') as HTMLElement | null;
            if (!rocket) return;
            
            const dx = targetX - currentX;
            currentX += dx * 0.1; // Smoothing factor
            
            if (Math.abs(dx) > 0.1) {
                rocket.style.left = `${currentX}px`;
            } else {
                rocket.style.left = `${targetX}px`;
            }
            
            animationFrame = requestAnimationFrame(animateRocket);
        }

        // Start the animation loop
        animateRocket();

        // Fire bullet function
        function fireBullet() {
            const now = Date.now();
            if (now - lastFireTime < fireRate) return; // Rate limiting
            
            lastFireTime = now;
            const rocket = document.querySelector('.rocket') as HTMLElement | null;
            if (!rocket) return;
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
    });
</script>

<footer class="footer">
    <div class="footer-content">
        <div class="footer-grid">
            {#if lang === 'pt'}
            <div class="footer-brand">
                <p class="footer-tagline">Transformando o atendimento ao cliente!</p>
                <p class="footer-description">Empresa fundada e com operação em Indaiatuba, São Paulo.<br />Time de tecnologia de alta performance, todos sócios do negócio,<br />então conte com o maior comprometimento em todos os sentidos!</p>
            </div>
            {/if}
        </div>
        
        <div class="rocket-container">
            <div class="rocket">
                <div class="rocket-body"></div>
                <div class="rocket-thruster"></div>
            </div>
        </div>
        
        <div class="footer-bottom">
            {#if lang === 'pt'}
            <div class="footer-links">
                <a href="#privacy">Privacidade</a>
                <a href="#terms">Termos de uso</a>
            </div>
            {/if}
            <p>&copy; {new Date().getFullYear()} indaiatech. {lang === 'pt' ? 'Todos os direitos reservados.' : 'All rights reserved.'}</p>
        </div>
    </div>
</footer>

<style>
    .footer {
        background: rgba(10, 10, 10, 0.95);
        backdrop-filter: blur(10px);
        /* padding: 16rem 4rem 4rem; */
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
        padding: 8rem 4rem 0rem;
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

    :global(.bullet) {
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

    :global(.bullet::before) {
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

    :global(.bullet.active) {
        opacity: 1;
    }

    :global(.bullet-trail) {
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

    :global(.pixel-dust) {
        position: absolute;
        width: 2px;
        height: 2px;
        background: #B493FF;
        border-radius: 0;
        pointer-events: none;
        opacity: 0;
        filter: blur(0.5px);
    }

    .footer-bottom {
        border-top: 1px solid rgba(255, 255, 255, 0.1);
        margin: 0 4rem;
        padding: 1rem 0 10rem;
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
