<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>บริการถ่ายภาพงานพิธี - Save The Memory</title>
  <meta name="description" content="บริการถ่ายภาพงานพิธีแบบมืออาชีพ เก็บทุกโมเมนต์สำคัญให้สวยงามและครบถ้วนที่สุด">

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&display=swap" rel="stylesheet">

  <!-- Tailwind CDN -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- FontAwesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />

  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: { sans: ['Prompt', 'sans-serif'] },
          colors: {
            brand: { gold: '#C5A059', dark: '#1a1a1a', light: '#f9f9f9', cream: '#f5f0e6' }
          }
        }
      }
    }
  </script>

  <style>
    html { scroll-behavior: smooth; }
    .page-section { min-height: 100vh; display:flex; flex-direction:column; justify-content:center; position:relative; overflow:hidden; }
    .reveal { opacity:0; transform: translateY(30px); transition: all .8s ease-out; }
    .reveal.active { opacity:1; transform: translateY(0); }
    /* กำหนดขนาดการแสดงตัวอย่างภาพให้เรียบร้อย */
    .portfolio-img { width:100%; height:18rem; object-fit:cover; display:block; }
  </style>
</head>
<body class="font-sans text-gray-800 antialiased bg-stone-50">

  <!-- NAV -->
  <nav class="fixed top-0 w-full z-50 bg-white/90 backdrop-blur-md shadow-sm py-4 px-6">
    <div class="max-w-6xl mx-auto flex justify-between items-center">
      <a href="#home" class="text-xl font-bold text-gray-900 tracking-tighter">SAVE THE MEMORY<span class="text-brand-gold">.</span></a>
      <div class="hidden md:flex space-x-8 text-sm font-medium text-gray-600">
        <a href="#home" class="hover:text-brand-gold">หน้าแรก</a>
        <a href="#team" class="hover:text-brand-gold">ทีมงาน</a>
        <a href="#portfolio" class="hover:text-brand-gold">ผลงาน</a>
        <a href="#service" class="hover:text-brand-gold">บริการ</a>
        <a href="#pricing" class="hover:text-brand-gold">ราคา</a>
        <a href="#contact" class="px-4 py-2 bg-brand-gold text-white rounded-full hover:bg-yellow-600">จองคิว</a>
      </div>

      <button class="md:hidden text-2xl" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
        <i class="fa-solid fa-bars"></i>
      </button>
    </div>

    <div id="mobile-menu" class="hidden absolute top-full left-0 w-full bg-white shadow-lg md:hidden flex flex-col items-center py-4 space-y-4">
      <a href="#home" class="text-gray-700">หน้าแรก</a>
      <a href="#team" class="text-gray-700">ทีมงาน</a>
      <a href="#portfolio" class="text-gray-700">ผลงาน</a>
      <a href="#service" class="text-gray-700">บริการ</a>
      <a href="#pricing" class="text-gray-700">ราคา</a>
      <a href="#contact" class="text-brand-gold font-bold">ติดต่อเรา</a>
    </div>
  </nav>

  <!-- HERO -->
  <section id="home" class="page-section relative text-white pt-24">
    <div class="absolute inset-0 z-0">
      <img src="https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=2070&auto=format&fit=crop" alt="bg" class="w-full h-full object-cover">
      <div class="absolute inset-0 bg-black/40"></div>
    </div>

    <div class="relative z-10 container mx-auto px-6 text-center reveal active">
      <div class="mb-4 inline-block px-4 py-1 border border-white/30 rounded-full text-xs uppercase tracking-widest">Brochure</div>
      <h1 class="text-4xl md:text-6xl font-bold mb-6">บริการถ่ายภาพ<br><span class="text-brand-gold">งานพิธีแบบมืออาชีพ</span></h1>
      <p class="text-lg md:text-xl font-light mb-8 max-w-2xl mx-auto text-gray-200">เก็บทุกโมเมนต์สำคัญให้สวยงามและครบถ้วนที่สุด ❤️</p>
      <div class="flex justify-center gap-4">
        <a href="#portfolio" class="px-6 py-3 bg-white text-gray-900 rounded-full">ดูผลงาน</a>
        <a href="#contact" class="px-6 py-3 bg-brand-gold text-white rounded-full">จองคิว</a>
      </div>
    </div>
  </section>

  <!-- TEAM -->
  <section id="team" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <div class="text-center max-w-3xl mx-auto mb-12 reveal">
        <h2 class="text-3xl font-bold text-gray-900 mb-3">ยินดีให้บริการในวันสำคัญของคุณ</h2>
        <p class="text-gray-600">ทีมงานมืออาชีพ พร้อมดูแลตั้งแต่ต้นจนจบพิธี</p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div class="p-6 bg-gray-50 rounded-2xl text-center">
          <i class="fa-solid fa-user-group text-brand-gold text-3xl mb-3"></i>
          <h3 class="font-bold">ช่างภาพ 2 คน</h3>
          <p class="text-sm text-gray-500">เก็บภาพครอบคลุมทุกมุม</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center">
          <i class="fa-solid fa-camera text-brand-gold text-3xl mb-3"></i>
          <h3 class="font-bold">กล้อง 3 ตัว</h3>
          <p class="text-sm text-gray-500">เลนส์ครบทุกระยะ</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center">
          <i class="fa-solid fa-lightbulb text-brand-gold text-3xl mb-3"></i>
          <h3 class="font-bold">ไฟ 6 ดวง</h3>
          <p class="text-sm text-gray-500">แสงสวยทุกรายละเอียด</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center">
          <i class="fa-solid fa-wand-magic-sparkles text-brand-gold text-3xl mb-3"></i>
          <h3 class="font-bold">รีทัชมาตรฐานโปร</h3>
          <p class="text-sm text-gray-500">Mood & Tone เป็นเอกลักษณ์</p>
        </div>
      </div>
    </div>
  </section>

  <!-- PORTFOLIO -->
  <section id="portfolio" class="py-20 bg-stone-50">
    <div class="container mx-auto px-6">
      <div class="text-center max-w-3xl mx-auto mb-10 reveal">
        <h2 class="text-3xl font-bold text-gray-900 mb-3">ผลงานที่ผ่านมา</h2>
        <p class="text-gray-600">ตัวอย่างภาพจากงานพิธีต่าง ๆ — หากไฟล์รูปอยู่ในโฟลเดอร์เดียวกับไฟล์นี้ รูปจะแสดงขึ้น</p>
      </div>

      <!-- Gallery grid: ถ้าภาพอยู่ในโฟลเดอร์เดียวกัน ให้ใช้ชื่อไฟล์ตรง ๆ -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 reveal">
        <div class="overflow-hidden rounded-xl shadow">
          <img src="A7409308.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="DSC07259.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="DSC07277.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="IMG_8708.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="IMG_8897.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1623167198303-3453b3b64415?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="A7400001.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1548545811-92523297a7da?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="A7409325.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="A7409977.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="DSC06869.jpg" alt="portfolio" class="portfolio-img" onerror="this.onerror=null;this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
        </div>
      </div>

      <div class="text-center mt-8 reveal">
        <a href="#contact" class="inline-block px-6 py-3 bg-brand-gold text-white rounded-full">ต้องการดูเพิ่มเติม / จองคิว</a>
      </div>
    </div>
  </section>

  <!-- SERVICE -->
  <section id="service" class="py-20 bg-brand-cream/30">
    <div class="container mx-auto px-6">
      <div class="flex flex-col lg:flex-row items-center gap-12">
        <div class="lg:w-1/2 reveal">
          <img src="https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1978" alt="candid" class="rounded-lg shadow-2xl w-full h-[420px] object-cover">
        </div>
        <div class="lg:w-1/2 reveal">
          <h3 class="text-3xl font-bold mb-4">มากกว่าแค่ถ่ายภาพ คือการ <span class="text-brand-gold">ดูแลใส่ใจ</span></h3>
          <p class="text-gray-600">ทีมงานพร้อมช่วยจัดลำดับพิธี ดูแลจังหวะสำคัญ และเก็บรายละเอียดทุกช็อต</p>
        </div>
      </div>
    </div>
  </section>

  <!-- PRICING -->
  <section id="pricing" class="py-20 bg-white">
    <div class="container mx-auto px-6">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div class="p-6 bg-white rounded-2xl shadow">
          <h4 class="font-bold text-xl mb-3">กำหนดการส่งงาน</h4>
          <ul class="text-gray-600 list-disc list-inside">
            <li>ส่งงานไฟล์ภาพคมชัดสูง (High Resolution)</li>
            <li>อัปโหลดผ่าน Cloud Drive ภายใน 2 วัน (มาตรฐาน)</li>
          </ul>
        </div>

        <div class="p-6 bg-gradient-to-br from-brand-cream to-white rounded-2xl shadow relative">
          <div class="absolute top-4 right-4 text-xs bg-brand-gold text-white px-3 py-1 rounded-bl">โปรโมชั่น</div>
          <h4 class="font-bold text-xl mb-3">ราคาแพ็กเกจ</h4>
          <p class="text-3xl font-bold text-brand-gold mb-2">4,000 บาท <span class="text-sm text-gray-500">(ปกติ 5,500)</span></p>
          <p class="text-sm text-gray-500">มัดจำจองคิว: 500 บาท</p>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="page-section bg-gray-50 py-20">
    <div class="container mx-auto px-6 relative z-10 text-center">
      <div class="max-w-3xl mx-auto bg-white p-10 rounded-3xl shadow-2xl border">
        <h2 class="text-3xl font-bold mb-4">สนใจจองคิว / สอบถาม</h2>
        <p class="text-gray-600 mb-6">อย่าปล่อยให้วันสำคัญผ่านไปโดยไม่มีภาพสวยๆ นะครับ</p>

        <div class="flex flex-col md:flex-row justify-center gap-4">
          <a href="https://line.me/ti/p/~savethememory7" target="_blank" class="px-6 py-3 bg-[#06C755] text-white rounded-xl flex items-center gap-3">
            <i class="fa-brands fa-line text-2xl"></i> savethememory7
          </a>
          <a href="tel:0630288737" class="px-6 py-3 bg-gray-800 text-white rounded-xl flex items-center gap-3">
            <i class="fa-solid fa-phone-volume"></i> 063-028-8737
          </a>
        </div>

        <p class="text-sm text-gray-400 mt-6">&copy; Save The Memory Photography</p>
      </div>
    </div>
  </section>

  <!-- Floating action for mobile -->
  <div class="fixed bottom-6 right-6 z-50 md:hidden flex flex-col gap-3">
    <a href="https://line.me/ti/p/~savethememory7" class="w-14 h-14 bg-[#06C755] rounded-full text-white flex items-center justify-center">
      <i class="fa-brands fa-line"></i>
    </a>
    <a href="tel:0630288737" class="w-14 h-14 bg-brand-gold rounded-full text-white flex items-center justify-center">
      <i class="fa-solid fa-phone"></i>
    </a>
  </div>

  <script>
    function reveal() {
      var reveals = document.querySelectorAll('.reveal');
      for (var i=0;i<reveals.length;i++){
        var windowH = window.innerHeight;
        var top = reveals[i].getBoundingClientRect().top;
        if (top < windowH - 150) reveals[i].classList.add('active');
      }
    }
    window.addEventListener('scroll', reveal);
    reveal();
  </script>
</body>
</html>
