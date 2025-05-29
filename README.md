# sada<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Kỉ niệm 2 tháng nèeeeee</title>
  <style>
    body {
      margin: 0;
      background: black;
      overflow: hidden;
      font-family: sans-serif;
    }

    .msg {
      position: absolute;
      color: #00ffff;
      font-size: 24px;
      white-space: nowrap;
      text-shadow: 0 0 10px #00ffff;
      animation: fly 10s linear infinite;
    }

    @keyframes fly {
      from {
        transform: translateY(100vh) rotate(0deg);
        opacity: 0;
      }
      to {
        transform: translateY(-100vh) rotate(360deg);
        opacity: 1;
      }
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 0;
    }

    .soundcloud-player {
      position: fixed;
      bottom: 20px;
      left: 20px;
      z-index: 10;
    }
  </style>
</head>
<body>
  <!-- Nhạc nền từ SoundCloud -->
  <div class="soundcloud-player">
    <iframe width="300" height="80" scrolling="no" frameborder="no" allow="autoplay"
      src="https://w.soundcloud.com/player/?url=https%3A//soundcloud.com/01112001/y2meta-com-soobin-b-t-n-l-n&color=%2300ffff&auto_play=true&hide_related=false&show_comments=false&show_user=false&show_reposts=false&show_teaser=false&visual=false">
    </iframe>
  </div>

  <!-- Sao lấp lánh bằng Three.js -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
  <script>
    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 1, 1000);
    const renderer = new THREE.WebGLRenderer();
    renderer.setSize(window.innerWidth, window.innerHeight);
    document.body.appendChild(renderer.domElement);

    function createStars(count) {
      const geometry = new THREE.BufferGeometry();
      const vertices = [];
      for (let i = 0; i < count; i++) {
        const x = (Math.random() - 0.5) * 2000;
        const y = (Math.random() - 0.5) * 2000;
        const z = (Math.random() - 0.5) * 2000;
        vertices.push(x, y, z);
      }
      geometry.setAttribute('position', new THREE.Float32BufferAttribute(vertices, 3));
      const material = new THREE.PointsMaterial({ color: 0xffffff, size: 1 });
      const stars = new THREE.Points(geometry, material);
      scene.add(stars);
    }

    createStars(1000);
    camera.position.z = 5;

    function animate() {
      requestAnimationFrame(animate);
      renderer.render(scene, camera);
    }
    animate();

    // Responsive
    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });
  </script>

  <!-- Chữ bay bằng CSS -->
  <script>
    const msg = "Chúc em bé iuu ngày càng iu anh hơn nheeeee♡";
    for (let i = 0; i < 50; i++) {
      const span = document.createElement('span');
      span.className = 'msg';
      span.textContent = msg;
      span.style.left = Math.random() * 100 + 'vw';
      span.style.top = Math.random() * 100 + 'vh';
      span.style.animationDuration = (5 + Math.random() * 5) + 's';
      document.body.appendChild(span);
    }
  </script>
</body>
</html>
