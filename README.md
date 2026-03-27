<div align="center" style="margin-bottom: 60px;">

  <!-- 네온 사이버펑크 헤더 -->
  <div style="position: relative; height: 420px; background: radial-gradient(circle at 50% 30%, #2a004d 0%, #0a0a0a 75%); border: 2px solid #ff00ff; border-radius: 24px; overflow: hidden; box-shadow: 0 0 80px rgba(255, 0, 255, 0.4);">
    
    <!-- 파티클 캔버스 -->
    <canvas id="readme-particles" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; pointer-events: none;"></canvas>
    
    <!-- 스캔라인 효과 -->
    <div style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: linear-gradient(transparent 50%, rgba(0, 255, 255, 0.05) 50%); background-size: 100% 6px; animation: scanline 8s linear infinite; z-index: 2; pointer-events: none;"></div>
    
    <!-- 메인 타이틀 -->
    <div style="position: relative; z-index: 3; height: 100%; display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; padding: 40px 20px;">
      <h1 style="font-size: 5.5rem; font-weight: 900; margin: 0; letter-spacing: 8px; font-family: 'Orbitron', system-ui, sans-serif; 
                 background: linear-gradient(90deg, #ff00ff, #00ffff, #ff00ff);
                 -webkit-background-clip: text;
                 -webkit-text-fill-color: transparent;
                 text-shadow: 0 0 40px #ff00ff, 0 0 80px #00ffff;
                 animation: glitch 2.5s infinite alternate;">
        NEON VOID
      </h1>
      <p style="font-size: 2rem; margin-top: 20px; letter-spacing: 10px; color: #00ffff; font-family: monospace; text-shadow: 0 0 20px #00ffff;">
        2026 • CYBERPUNK ENERGY
      </p>
    </div>
  </div>

  <br><br>

  <h2 style="font-size: 2.8rem; background: linear-gradient(90deg, #ff00ff, #00ffff); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">
    🔥 이 프로젝트 개쩐다
  </h2>

  <p style="font-size: 1.4rem; max-width: 800px; margin: 30px auto; line-height: 1.8;">
    단 하나의 README.md로도 미친 첫인상을 주는 사이버펑크 스타일 프로젝트.<br>
    네온, 글리치, 파티클, 글래스 효과까지 다 때려박음.
  </p>

  <div style="margin: 50px 0; display: flex; gap: 25px; justify-content: center; flex-wrap: wrap;">
    <a href="#" style="padding: 18px 45px; background: transparent; color: #ff00ff; border: 3px solid #ff00ff; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 1.2rem; transition: 0.4s;">
      ★ STAR THIS REPO
    </a>
    <a href="#" style="padding: 18px 45px; background: #00ffff; color: #0a0a0a; border: 3px solid #00ffff; border-radius: 50px; text-decoration: none; font-weight: bold; font-size: 1.2rem; transition: 0.4s;">
      FORK &amp; BUILD
    </a>
  </div>

</div>

<!-- 파티클 자바스크립트 (GitHub에서 작동) -->
<script>
  const canvas = document.getElementById('readme-particles');
  if (canvas) {
    const ctx = canvas.getContext('2d');
    
    function resizeCanvas() {
      canvas.width = canvas.offsetWidth;
      canvas.height = canvas.offsetHeight;
    }
    resizeCanvas();
    window.addEventListener('resize', resizeCanvas);

    let particles = [];

    class Particle {
      constructor() {
        this.x = Math.random() * canvas.width;
        this.y = Math.random() * canvas.height;
        this.size = Math.random() * 3 + 1;
        this.speedX = Math.random() * 1.2 - 0.6;
        this.speedY = Math.random() * 1.2 - 0.6;
        this.color = Math.random() > 0.5 ? '#ff00ff' : '#00ffff';
      }
      update() {
        this.x += this.speedX;
        this.y += this.speedY;
        if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
        if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
      }
      draw() {
        ctx.fillStyle = this.color;
        ctx.shadowBlur = 20;
        ctx.shadowColor = this.color;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    function initParticles() {
      particles = [];
      for (let i = 0; i < 140; i++) {
        particles.push(new Particle());
      }
    }

    function animate() {
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      particles.forEach(p => {
        p.update();
        p.draw();
      });
      requestAnimationFrame(animate);
    }

    initParticles();
    animate();
  }
</script>

<style>
  @keyframes glitch {
    0% { transform: translate(0); }
    20% { transform: translate(-4px, 4px); }
    40% { transform: translate(-4px, -4px); }
    60% { transform: translate(4px, 4px); }
    80% { transform: translate(4px, -4px); }
    100% { transform: translate(0); }
  }
  @keyframes scanline {
    0% { transform: translateY(-100%); }
    100% { transform: translateY(300%); }
  }
</style>
