<!doctype html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>SAVE THE MEMORY — Portfolio & Booking</title>

  <!-- Tailwind CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"/>

  <style>
    :root{
      --brand:#C5A059;
    }
    body{font-family: 'Prompt', sans-serif; scroll-behavior: smooth;}
    .text-brand{color:var(--brand);}
    .bg-brand{background:var(--brand);}
    /* fade-up animation used by JS */
    .fade-up { opacity:0; transform: translateY(12px); transition: all 600ms cubic-bezier(.2,.9,.2,1); }
    .fade-up.in-view { opacity:1; transform: translateY(0); }
    /* hero overlay gradient */
    .hero-overlay{ background: linear-gradient(180deg, rgba(0,0,0,0.45) 0%, rgba(0,0,0,0.65) 60%, rgba(0,0,0,0.85) 100%); }
    /* small helpers */
    .glass { background: rgba(255,255,255,0.06); backdrop-filter: blur(4px); }
  </style>
</head>
<body class="bg-stone-50 text-gray-800">

  <!-- NAVBAR (single) -->
  <nav class="fixed top-0 left-0 w-full z-50 bg-white/70 backdrop-blur-md">
    <div class="max-w-6xl mx-auto px-4 md:px-6 py-3 flex items-center justify-between">
      <a href="#home" class="text-xl font-bold text-gray-800">SAVE THE MEMORY</a>

      <!-- Desktop menu -->
      <div class="hidden md:flex items-center gap-6">
        <a href="#home" class="nav-link text-gray-700">หน้าแรก</a>
        <a href="#team" class="nav-link text-gray-700">ทีมงาน</a>
        <a href="#portfolio" class="nav-link text-gray-700">ผลงาน</a>
        <a href="#services" class="nav-link text-gray-700">บริการ</a>
        <a href="#pricing" class="nav-link text-gray-700">ราคา</a>
        <a href="#booking" class="ml-4 px-4 py-2 rounded-full bg-brand text-black font-semibold">จองคิว</a>
      </div>

      <!-- Mobile hamburger -->
      <div class="md:hidden">
        <button id="hambtn" aria-label="เมนู" class="p-2 text-gray-700">
          <i class="fa-solid fa-bars text-2xl"></i>
        </button>
      </div>
    </div>

    <!-- Mobile menu (hidden by default) -->
    <div id="mobileMenu" class="hidden md:hidden bg-white/95 border-t">
      <div class="px-4 py-3 space-y-2">
        <a href="#home" class="block nav-link-mobile">หน้าแรก</a>
        <a href="#team" class="block nav-link-mobile">ทีมงาน</a>
        <a href="#portfolio" class="block nav-link-mobile">ผลงาน</a>
        <a href="#services" class="block nav-link-mobile">บริการ</a>
        <a href="#pricing" class="block nav-link-mobile">ราคา</a>
        <a href="#booking" class="block bg-brand text-black px-4 py-2 rounded-md text-center">จองคิว</a>
      </div>
    </div>
  </nav>

  <div class="pt-20"></div> <!-- spacing so hero not hidden -->

  <!-- HERO: slider + optional video background -->
  <section id="home" class="relative h-screen overflow-hidden">
    <!-- video (optional). Replace src with your video or remove -->
    <video id="heroVideo" class="absolute inset-0 w-full h-full object-cover hidden" muted loop playsinline>
      <!-- Example: set a video file URL if you want video background -->
      <!-- <source src="path/to/your-video.mp4" type="video/mp4"> -->
    </video>

    <!-- slider images as background elements -->
    <div id="heroSlides" class="absolute inset-0">
      <!-- slides inserted by JS for lazy swapping -->
    </div>

    <!-- dark overlay -->
    <div class="absolute inset-0 hero-overlay"></div>

    <!-- content -->
    <div class="relative z-20 flex items-center justify-center h-full">
      <div class="text-center px-6 max-w-3xl">
        <span class="inline-block bg-white/20 text-xs px-3 py-1 rounded-full mb-4">BROCHURE</span>
        <h1 class="text-3xl md:text-5xl font-extrabold text-white leading-tight drop-shadow-lg">
          บริการถ่ายภาพ<br/>
          <span class="text-brand">งานพิธีแบบมืออาชีพ</span>
        </h1>
        <p class="mt-4 text-gray-200">“เก็บทุกโมเมนต์สำคัญให้สวยงามและครบถ้วนที่สุด 💕”</p>

        <div class="mt-8 flex flex-wrap justify-center gap-4">
          <a href="#services" class="px-6 py-3 rounded-full bg-white text-gray-800 font-semibold shadow">ดูรายละเอียด</a>
          <a href="#booking" class="px-6 py-3 rounded-full bg-brand text-black font-semibold shadow">จองคิวถ่ายภาพ</a>
        </div>
      </div>
    </div>

    <!-- slider controls -->
    <div class="absolute left-6 bottom-8 z-30 flex items-center gap-3">
      <button id="prevSlide" class="p-2 bg-white/20 rounded-full text-white"><i class="fa-solid fa-chevron-left"></i></button>
      <button id="nextSlide" class="p-2 bg-white/20 rounded-full text-white"><i class="fa-solid fa-chevron-right"></i></button>
    </div>

    <!-- toggle video / images -->
    <div class="absolute right-6 bottom-8 z-30">
      <button id="toggleBg" class="px-3 py-2 bg-white/20 text-white rounded-full text-sm">Video Off</button>
    </div>
  </section>

  <!-- TEAM / FEATURES -->
  <section id="team" class="py-16">
    <div class="max-w-6xl mx-auto px-6">
      <div class="text-center mb-8">
        <h2 class="text-2xl font-extrabold">ยินดีให้บริการในวันสำคัญของคุณ</h2>
        <p class="text-gray-600 max-w-2xl mx-auto mt-2">ทีมงานมืออาชีพ พร้อมดูแลตั้งแต่ต้นจนจบพิธี</p>
      </div>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6">
        <div class="p-6 bg-gray-50 rounded-2xl text-center fade-up">
          <i class="fa-solid fa-user-group text-brand text-4xl mb-3"></i>
          <h3 class="font-bold">ช่างภาพ 2 คน</h3>
          <p class="text-sm text-gray-500">เก็บภาพครอบคลุมทุกมุม</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center fade-up">
          <i class="fa-solid fa-camera text-brand text-4xl mb-3"></i>
          <h3 class="font-bold">กล้อง 3 ตัว</h3>
          <p class="text-sm text-gray-500">เลนส์ครบทุกระยะ</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center fade-up">
          <i class="fa-solid fa-lightbulb text-brand text-4xl mb-3"></i>
          <h3 class="font-bold">ไฟ 6 ดวง</h3>
          <p class="text-sm text-gray-500">แสงสวยทุกช็อต</p>
        </div>
        <div class="p-6 bg-gray-50 rounded-2xl text-center fade-up">
          <i class="fa-solid fa-wand-magic-sparkles text-brand text-4xl mb-3"></i>
          <h3 class="font-bold">รีทัชมาตรฐานโปร</h3>
          <p class="text-sm text-gray-500">Mood & Tone เป็นเอกลักษณ์</p>
        </div>
      </div>
    </div>
  </section>

  <!-- MORE CARE SECTION -->
  <section id="services" class="py-16 bg-[#fffaf8]">
    <div class="max-w-6xl mx-auto px-6 lg:px-8">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
        <div class="fade-up">
          <h2 class="text-4xl font-extrabold leading-tight">มากกว่าแค่ถ่ายภาพ<br><span class="text-brand">คือการดูแลใส่ใจ</span></h2>
          <p class="text-gray-600 mt-4 max-w-xl">เราพร้อมสนับสนุนให้งานของคุณราบรื่นที่สุด ทีมงานของเราทำหน้าที่มากกว่าช่างภาพ</p>
        </div>

        <div class="space-y-6">
          <div class="flex gap-4 fade-up">
            <div class="w-12 h-12 bg-green-100 text-green-700 rounded-full flex items-center justify-center"><i class="fa-solid fa-list-check"></i></div>
            <div>
              <h3 class="font-semibold">ช่วยจัดลำดับพิธี</h3>
              <p class="text-sm text-gray-600">ให้คำแนะนำมุมภาพ ขั้นตอนต่าง ๆ</p>
            </div>
          </div>

          <div class="flex gap-4 fade-up">
            <div class="w-12 h-12 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center"><i class="fa-solid fa-heart"></i></div>
            <div>
              <h3 class="font-semibold">ดูแลทุกจังหวะสำคัญ</h3>
              <p class="text-sm text-gray-600">สแตนด์บายตลอดเวลา ไม่ให้พลาดช็อตสำคัญ</p>
            </div>
          </div>

          <div class="flex gap-4 fade-up">
            <div class="w-12 h-12 bg-pink-100 text-pink-600 rounded-full flex items-center justify-center"><i class="fa-solid fa-camera-retro"></i></div>
            <div>
              <h3 class="font-semibold">เก็บภาพครบถ้วน</h3>
              <ul class="list-disc ml-5 text-sm text-gray-600 mt-1">
                <li>ภาพพิธีการสำคัญ</li>
                <li>ภาพครอบครัวและญาติผู้ใหญ่</li>
                <li>ภาพบรรยากาศและรายละเอียด (Details)</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- GALLERY -->
  <section id="portfolio" class="py-16">
    <div class="max-w-6xl mx-auto px-6">
      <h2 class="text-2xl font-extrabold mb-4">ผลงานที่ผ่านมา</h2>
      <p class="text-gray-600 mb-6">คลิกเพื่อดูภาพใหญ่</p>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- thumbnail examples -->
        <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg" loading="lazy"
             class="w-full h-64 object-cover rounded-xl cursor-pointer fade-up" alt="portfolio" onclick="openLightbox(this.src)">
        <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg" loading="lazy"
             class="w-full h-64 object-cover rounded-xl cursor-pointer fade-up" alt="portfolio" onclick="openLightbox(this.src)">
        <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8723.jpg" loading="lazy"
             class="w-full h-64 object-cover rounded-xl cursor-pointer fade-up" alt="portfolio" onclick="openLightbox(this.src)">
      </div>
    </div>
  </section>

  <!-- PROMOTION / QR -->
  <section id="promo" class="py-16 bg-[#0f1724] text-white">
    <div class="max-w-6xl mx-auto px-6">
      <div class="bg-gradient-to-r from-[#0f1724] to-[#121826] rounded-2xl p-8 md:p-12 overflow-hidden relative">
        <div class="absolute inset-0 pointer-events-none" style="background-image: radial-gradient(rgba(255,255,255,0.02) 1px, transparent 1px); background-size:18px 18px;"></div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 items-center relative z-10">
          <div class="md:col-span-2">
            <span class="bg-[#C5A059] text-black px-3 py-1 rounded-full text-xs">RECOMMENDED</span>
            <h3 class="text-3xl md:text-4xl font-extrabold mt-3">บริการเสริมสุดฮิต! <span class="text-[#F2D8A8]">ระบบสแกน QR Code</span></h3>
            <p class="text-gray-300 mt-4">รับรูปหน้างานทันที — แชร์ไว โหลดง่าย สะดวกต่อแขก</p>
            <p class="text-[#F2D8A8] mt-6 text-3xl font-extrabold">+1,000 <span class="text-sm text-gray-300">บาท</span></p>
          </div>

          <div class="flex justify-center md:justify-end">
            <button id="openQrBtn" class="group bg-white/5 p-6 rounded-lg w-56 h-56 flex items-center justify-center">
              <img id="qrImg" src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/qr-placeholder.png" alt="qr" class="w-40 h-40 object-contain">
              <span class="absolute right-4 bottom-4 bg-[#C5A059] text-black text-xs px-3 py-1 rounded-full">SCAN ME</span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- PRICING + TOGGLE -->
  <section id="pricing" class="py-16">
    <div class="max-w-6xl mx-auto px-6">
      <div class="text-center mb-6">
        <h2 class="text-2xl font-extrabold">ราคาแพ็กเกจ</h2>
        <p class="text-gray-600">เลือกประเภทงานเพื่อดูราคาและรายละเอียด</p>
      </div>

      <div class="flex justify-center mb-6">
        <div id="tabs" class="inline-flex rounded-full bg-gray-100 p-1">
          <button class="tab-btn px-5 py-2 rounded-full bg-white shadow-sm" data-key="ceremony">งานพิธี</button>
          <button class="tab-btn px-5 py-2 rounded-full" data-key="prewedding">งานคู่รัก</button>
          <button class="tab-btn px-5 py-2 rounded-full" data-key="family">งานครอบครัว</button>
        </div>
      </div>

      <div id="pricingArea" class="bg-[#fdf8ef] rounded-2xl p-8 shadow border border-[#f0e7d3]">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
          <div>
            <div class="flex items-center gap-3 mb-3">
              <div id="pkgIcon" class="w-12 h-12 bg-yellow-50 text-[#C5A059] rounded-full flex items-center justify-center text-xl"><i class="fa-solid fa-tag"></i></div>
              <div>
                <div id="pkgTitle" class="text-xl font-bold">งานพิธี</div>
                <div id="pkgSubtitle" class="text-sm text-gray-600">แพ็กเกจงานพิธี ครอบคลุมทุกช่วงสำคัญ</div>
              </div>
            </div>

            <div class="mt-4">
              <div class="flex items-end gap-4">
                <div id="pkgPrice" class="text-4xl font-extrabold text-[#F2D8A8]">4,000</div>
                <div class="text-gray-700 mb-1">บาท</div>
                <div id="pkgTag" class="ml-2 text-xs bg-red-500 text-white px-2 py-1 rounded hidden">ลดพิเศษ</div>
              </div>
              <p id="pkgNote" class="text-xs text-gray-500 mt-2">*สำหรับลูกค้าจองเลย</p>
            </div>

            <ul id="pkgFeatures" class="mt-6 text-sm text-gray-700 space-y-2"></ul>

            <div class="mt-6 flex gap-3">
              <a id="bookNow" href="https://line.me/ti/p/~savethememory7" target="_blank" rel="noopener" class="px-4 py-2 bg-brand text-black rounded font-semibold">จองบริการนี้</a>
              <button id="moreBtn" class="px-4 py-2 border rounded text-sm">รายละเอียดเพิ่มเติม</button>
            </div>
          </div>

          <div class="flex justify-center md:justify-end">
            <div class="w-64 h-64 bg-white rounded-lg shadow overflow-hidden">
              <img id="pkgImg" src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg" alt="package" class="w-full h-full object-cover">
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>

  <!-- TIMELINE / DELIVERY -->
  <section id="delivery" class="py-16">
    <div class="max-w-6xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-10">
      <div class="bg-white p-8 rounded-2xl shadow">
        <h3 class="text-xl font-bold flex items-center gap-3"><i class="fa-solid fa-clock text-blue-600"></i> กำหนดการส่งงาน</h3>
        <ul class="mt-6 space-y-4">
          <li class="flex gap-3"><i class="fa-solid fa-circle-check text-green-500 mt-1"></i> ส่งงานไวภายใน 2 วัน (หรือเร็วกว่านั้น)</li>
          <li class="flex gap-3"><i class="fa-solid fa-circle-check text-green-500 mt-1"></i> ส่งเป็นไฟล์ความคมชัดสูง (High Resolution)</li>
          <li class="flex gap-3"><i class="fa-solid fa-circle-check text-green-500 mt-1"></i> อัปโหลดผ่าน Cloud Drive พร้อมแชร์ทันที</li>
        </ul>
      </div>

      <div class="bg-[#fdf8ef] p-8 rounded-2xl border border-[#f0e7d3] shadow relative">
        <span class="absolute top-4 right-4 bg-brand text-black px-3 py-1 text-xs rounded-full">โปรโมชัน ปี 2024</span>
        <h3 class="text-xl font-bold flex items-center gap-3"><i class="fa-solid fa-tag text-brand"></i> ราคาแพ็กเกจ</h3>
        <div class="mt-4">
          <p class="font-bold">⭐ งานพิธี (ราคาปกติ 5,500 บ.)</p>
          <div class="flex items-end gap-3 mt-3">
            <span class="text-4xl font-extrabold text-gray-900">4,000</span><span class="text-gray-700 mb-1">บาท</span>
            <span class="bg-red-500 text-white text-xs px-2 py-1 rounded mb-2">ลด 1,500!</span>
          </div>
          <p class="text-xs text-gray-500 mt-1">*สำหรับลูกค้าจองเลย</p>
        </div>

        <hr class="my-6 border-gray-200">

        <div class="space-y-3">
          <div class="flex justify-between items-center"><p class="text-gray-700">งานบวช เริ่มต้นที่</p><p class="font-semibold">3,500 บาท</p></div>
          <div class="flex justify-between items-center"><p class="text-gray-700">งานขาวดำ เริ่มต้นที่</p><p class="font-semibold">3,500 บาท</p></div>
        </div>

        <hr class="my-6 border-gray-200">

        <div class="flex justify-between"><p class="text-gray-700">มัดจำจองคิว</p><p class="font-bold">500 บาท</p></div>
      </div>
    </div>
  </section>

  <!-- BOOKING calendar (localStorage example) -->
  <section id="booking" class="py-16 bg-white">
    <div class="max-w-4xl mx-auto px-6">
      <h2 class="text-2xl font-extrabold mb-4">เช็คคิว / จองคิว</h2>
      <p class="text-gray-600 mb-4">เลือกวันที่ที่ต้องการเพื่อจอง — ข้อมูลจะถูกเก็บในเบราว์เซอร์ (local)</p>

      <div class="bg-stone-50 p-6 rounded-2xl shadow">
        <div id="calendar" class="grid grid-cols-7 gap-2 text-sm">
          <div class="text-center font-medium">อา</div><div class="text-center font-medium">จ</div><div class="text-center font-medium">อ</div>
          <div class="text-center font-medium">พ</div><div class="text-center font-medium">พฤ</div><div class="text-center font-medium">ศ</div><div class="text-center font-medium">ส</div>
        </div>

        <div class="mt-4">
          <div id="bookedList" class="text-sm text-gray-600"></div>
        </div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="py-12">
    <div class="max-w-4xl mx-auto px-6 text-center">
      <h3 class="text-xl font-bold mb-3">ติดต่อเรา</h3>
      <p class="text-gray-600">LINE: savethememory7 • โทร: 063-028-8737</p>
    </div>
  </section>

  <!-- LIGHTBOX for gallery -->
  <div id="lightbox" class="fixed inset-0 z-50 hidden items-center justify-center bg-black/70">
    <div class="max-w-4xl w-full p-4">
      <div class="bg-white rounded-lg overflow-hidden">
        <div class="flex justify-end p-2"><button onclick="closeLightbox()" class="text-gray-600"><i class="fa-solid fa-xmark"></i></button></div>
        <img id="lightboxImg" src="" alt="lightbox" class="w-full object-contain max-h-[80vh]">
      </div>
    </div>
  </div>

  <!-- QR modal -->
  <div id="qrModal" class="fixed inset-0 z-50 hidden items-center justify-center bg-black/60 p-6">
    <div class="bg-white rounded-xl max-w-md w-full p-6 relative">
      <button id="closeQrModal" class="absolute top-4 right-4 text-gray-600 hover:text-gray-900"><i class="fa-solid fa-xmark"></i></button>
      <h4 class="font-bold text-lg mb-4">สแกนหรือดาวน์โหลดรูป</h4>
      <div class="flex flex-col items-center gap-4">
        <img id="qrLarge" src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/qr-placeholder.png" alt="QR" class="w-64 h-64 object-contain">
        <div class="flex gap-3">
          <a id="qrLinkBtn" href="#" target="_blank" rel="noopener" class="px-4 py-2 bg-brand text-black rounded font-semibold">เปิดลิงก์รูป</a>
          <button id="copyBtn" class="px-4 py-2 border rounded text-sm">คัดลอกลิงก์</button>
        </div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <footer class="py-8 bg-gray-100 mt-12">
    <div class="max-w-6xl mx-auto px-6 text-center text-gray-600">
      © <span id="year"></span> SAVE THE MEMORY — All rights reserved
    </div>
  </footer>

  <!-- ====== SCRIPTS ====== -->
  <script>
  // ========== Basic helpers ==========
  const qs = s => document.querySelector(s);
  const qsa = s => document.querySelectorAll(s);

  // set year
  document.getElementById('year').textContent = new Date().getFullYear();

  // ======= Mobile hamburger =======
  const hambtn = qs('#hambtn'), mobileMenu = qs('#mobileMenu');
  hambtn && hambtn.addEventListener('click', ()=> {
    mobileMenu.classList.toggle('hidden');
  });
  // close mobile menu when clicking links
  qsa('.nav-link-mobile').forEach(a=> a.addEventListener('click', ()=> mobileMenu.classList.add('hidden')));

  // ======= Smooth scroll focus fix for hash (ensure offset for fixed nav) =======
  // For all internal links with hash, apply offset on click
  const OFFSET = 80; // nav height
  document.addEventListener('click', e=>{
    const a = e.target.closest('a[href^="#"]');
    if(a){
      const href = a.getAttribute('href');
      if(href && href.startsWith('#')){
        const el = document.querySelector(href);
        if(el){
          e.preventDefault();
          const top = el.getBoundingClientRect().top + window.scrollY - OFFSET;
          window.scrollTo({top, behavior:'smooth'});
          // update hash without jump
          history.replaceState(null,'',href);
        }
      }
    }
  });

  // ======= Fade-up animation (IntersectionObserver) =======
  const io = new IntersectionObserver((entries)=>{
    entries.forEach(en=>{
      if(en.isIntersecting) en.target.classList.add('in-view');
    });
  }, {threshold:0.12});
  qsa('.fade-up').forEach(el=>{
    el.classList.add('fade-up');
    io.observe(el);
  });

  // ======= Lightbox =======
  window.openLightbox = function(src){
    qs('#lightboxImg').src = src;
    qs('#lightbox').classList.remove('hidden');
  };
  window.closeLightbox = function(){ qs('#lightbox').classList.add('hidden'); };

  // ======= QR modal =======
  const openQrBtn = qs('#openQrBtn');
  const qrModal = qs('#qrModal');
  const closeQrModal = qs('#closeQrModal');
  const QR_TARGET_URL = 'https://example.com/your-qr-download-link'; // <-- เปลี่ยนเป็นของจริง
  if(openQrBtn){
    openQrBtn.addEventListener('click', ()=>{
      qrModal.classList.remove('hidden');
      qs('#qrLinkBtn').href = QR_TARGET_URL;
      qs('#copyBtn').dataset.copy = QR_TARGET_URL;
    });
  }
  closeQrModal && closeQrModal.addEventListener('click', ()=> qrModal.classList.add('hidden'));
  qs('#copyBtn') && qs('#copyBtn').addEventListener('click', async ()=>{
    const txt = qs('#copyBtn').dataset.copy || QR_TARGET_URL;
    try { await navigator.clipboard.writeText(txt); qs('#copyBtn').textContent = 'คัดลอกแล้ว'; setTimeout(()=> qs('#copyBtn').textContent = 'คัดลอกลิงก์',2000); }
    catch(e){ alert('คัดลอกไม่ได้ ลองเปิดลิงก์แทน'); }
  });

  // ======= Hero slider & Video toggle =======
  const heroSlides = [
    // replace or add your images (prefer web-optimized)
    'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409325.jpg',
    'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg',
    'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg'
  ];
  const slidesEl = qs('#heroSlides');
  let current = 0;
  let useVideo = false;
  let sliderInterval;

  function renderSlide(idx){
    slidesEl.innerHTML = '';
    const img = document.createElement('div');
    img.className = 'absolute inset-0 bg-center bg-cover transition-opacity duration-700';
    img.style.backgroundImage = `url("${heroSlides[idx]}")`;
    slidesEl.appendChild(img);
  }
  function startAuto(){
    stopAuto();
    sliderInterval = setInterval(()=>{ current = (current+1)%heroSlides.length; renderSlide(current); }, 5000);
  }
  function stopAuto(){ if(sliderInterval) clearInterval(sliderInterval); }

  // controls
  qs('#prevSlide').addEventListener('click', ()=>{ stopAuto(); current = (current-1+heroSlides.length)%heroSlides.length; renderSlide(current); startAuto(); });
  qs('#nextSlide').addEventListener('click', ()=>{ stopAuto(); current = (current+1)%heroSlides.length; renderSlide(current); startAuto(); });

  // toggle video
  const toggleBg = qs('#toggleBg'), heroVideo = qs('#heroVideo');
  toggleBg.addEventListener('click', ()=>{
    useVideo = !useVideo;
    if(useVideo && heroVideo.querySelector('source')){
      heroVideo.classList.remove('hidden'); slidesEl.classList.add('hidden'); heroVideo.play(); toggleBg.textContent = 'Video On';
    } else {
      heroVideo.pause(); heroVideo.classList.add('hidden'); slidesEl.classList.remove('hidden'); toggleBg.textContent = 'Video Off';
    }
  });

  // init hero
  renderSlide(current);
  startAuto();

  // ======= Pricing toggle data & logic =======
  const PACKAGES = {
    ceremony: {
      title:'งานพิธี',
      subtitle:'แพ็กเกจงานพิธี ครอบคลุมทุกช่วงสำคัญ',
      price:'4,000',
      note:'*สำหรับลูกค้าจองเลย',
      tag:'ลด 1,500!',
      tagVisible:true,
      icon:'fa-solid fa-bell-concierge',
      img:'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg',
      features:['ช่างภาพ 2 คน','กล้อง 3 ตัว + เลนส์ครบ','ไฟส่องสว่าง 6 ดวง','ส่งไฟล์ความละเอียดสูง']
    },
    prewedding: {
      title:'พรีเวดดิ้ง (Pre-wedding)',
      subtitle:'เซสชันคู่รัก จัดเต็มมู้ดโรแมนติก',
      price:'2,500',
      note:'*เริ่มต้น (ไม่รวมค่าเดินทาง/สถานที่)',
      tagVisible:false,
      icon:'fa-solid fa-heart',
      img:'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07259.jpg',
      features:['เซสชันถ่ายนอกสถานที่','ภาพรีทัชโทนคู่รัก','ไฟล์ความละเอียดสูง']
    },
    family: {
      title:'งานครอบครัว (ขึ้นบ้านใหม่)',
      subtitle:'เก็บบรรยากาศอบอุ่นของครอบครัว',
      price:'3,500',
      note:'*สามารถปรับแพ็กตามงบได้',
      tagVisible:false,
      icon:'fa-solid fa-house-chimney',
      img:'https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8723.jpg',
      features:['ช่างภาพ 1-2 คน','เก็บภาพบรรยากาศ','ไฟล์ส่งผ่าน Cloud Drive']
    }
  };

  function renderPackage(key){
    const d = PACKAGES[key];
    if(!d) return;
    qs('#pkgTitle').textContent = d.title;
    qs('#pkgSubtitle').textContent = d.subtitle;
    qs('#pkgPrice').textContent = d.price;
    qs('#pkgNote').textContent = d.note;
    qs('#pkgImg').src = d.img;
    qs('#pkgIcon').innerHTML = `<i class="${d.icon}"></i>`;
    if(d.tagVisible && d.tag){ qs('#pkgTag').textContent = d.tag; qs('#pkgTag').classList.remove('hidden'); } else qs('#pkgTag').classList.add('hidden');
    // features
    const ul = qs('#pkgFeatures'); ul.innerHTML=''; d.features.forEach(f=>{ const li=document.createElement('li'); li.className='flex items-start gap-3'; li.innerHTML=`<i class="fa-solid fa-check text-brand mt-1 w-4"></i><span>${f}</span>`; ul.appendChild(li);});
  }

  qsa('.tab-btn').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      qsa('.tab-btn').forEach(b=> b.classList.remove('bg-white','shadow-sm'));
      btn.classList.add('bg-white','shadow-sm');
      renderPackage(btn.dataset.key);
    });
  });
  // init default
  const defaultKey = 'ceremony';
  qs(`.tab-btn[data-key="${defaultKey}"]`).classList.add('bg-white','shadow-sm');
  renderPackage(defaultKey);

  // ======= Simple calendar (localStorage) =======
  const CAL_KEY='stm_bookings_v1';
  let bookedDates = JSON.parse(localStorage.getItem(CAL_KEY) || '[]');

  function toISO(date){ const y=date.getFullYear(), m=String(date.getMonth()+1).padStart(2,'0'), d=String(date.getDate()).padStart(2,'0'); return `${y}-${m}-${d}`; }
  function renderCalendar(){
    const now = new Date();
    const year = now.getFullYear(), month = now.getMonth();
    const first = new Date(year,month,1), last = new Date(year, month+1,0);
    const startDay = first.getDay(), total = last.getDate();
    const cal = qs('#calendar');
    // clear but keep headers (first 7)
    while(cal.children.length>7) cal.removeChild(cal.lastChild);
    // blanks
    for(let i=0;i<startDay;i++){ const empty=document.createElement('div'); empty.className='h-20'; cal.appendChild(empty); }
    for(let d=1; d<=total; d++){
      const date = new Date(year,month,d);
      const iso = toISO(date);
      const cell = document.createElement('div');
      const booked = bookedDates.includes(iso);
      cell.className = 'h-24 p-2 rounded-lg flex flex-col justify-between cursor-pointer bg-white';
      cell.style.border = '1px solid rgba(0,0,0,0.06)';
      if(booked){ cell.style.background = '#C5A059'; cell.style.color = '#fff'; }
      const top = document.createElement('div'); top.className='flex justify-between items-start';
      const dateSpan = document.createElement('div'); dateSpan.className='text-sm font-medium'; dateSpan.textContent=d;
      const status = document.createElement('div'); status.className='text-xs'; status.textContent = booked ? 'เต็ม' : 'ว่าง';
      top.appendChild(dateSpan); top.appendChild(status);
      const btnWrap = document.createElement('div'); btnWrap.className='text-right';
      const btn = document.createElement('button'); btn.className='px-3 py-1 rounded text-xs bg-[#C5A059] text-black'; btn.textContent = booked ? 'ดู/ยกเลิก' : 'จอง';
      btn.onclick = (e)=>{ e.stopPropagation(); onDateClick(iso); };
      btnWrap.appendChild(btn);
      cell.appendChild(top); cell.appendChild(btnWrap);
      cal.appendChild(cell);
    }
    renderBookedList();
  }

  function renderBookedList(){
    const el = qs('#bookedList'); el.innerHTML = '';
    if(bookedDates.length===0){ el.textContent = 'ยังไม่มีคิวจอง'; return; }
    const sorted = bookedDates.slice().sort();
    sorted.forEach(d=>{ const div=document.createElement('div'); div.className='flex justify-between items-center py-1'; div.innerHTML = `<span>${d}</span><button class="text-red-600 text-sm">ยกเลิก</button>`; div.querySelector('button').addEventListener('click', ()=>{ if(confirm('ยืนยันยกเลิก '+d+' ?')) { bookedDates = bookedDates.filter(x=>x!==d); localStorage.setItem(CAL_KEY, JSON.stringify(bookedDates)); renderCalendar(); } }); el.appendChild(div);});
  }

  function onDateClick(iso){
    if(bookedDates.includes(iso)){
      if(confirm('วันที่ '+iso+' มีคิวแล้ว ต้องการยกเลิกไหม?')){ bookedDates = bookedDates.filter(x=>x!==iso); localStorage.setItem(CAL_KEY, JSON.stringify(bookedDates)); renderCalendar(); alert('ยกเลิกคิวเรียบร้อย (local)'); }
      return;
    }
    if(!confirm('จองวันที่ '+iso+' ? (ข้อมูลจะถูกเก็บบนเครื่องของคุณ)')) return;
    bookedDates.push(iso); localStorage.setItem(CAL_KEY, JSON.stringify(bookedDates)); renderCalendar(); alert('จองเรียบร้อย (local)');
  }
  renderCalendar();

  // ======= Accessibility: close modals with ESC =======
  document.addEventListener('keydown', e=>{ if(e.key==='Escape'){ qs('#lightbox') && qs('#lightbox').classList.add('hidden'); qrModal && qrModal.classList.add('hidden'); } });

  </script>
</body>
</html>


<!-- =================================== -->
<!-- GALLERY -->
<!-- =================================== -->
<section id="portfolio" class="pb-12">
  <div class="max-w-6xl mx-auto px-6">
    <h2 class="text-2xl font-bold mb-4">ผลงานที่ผ่านมา</h2>

    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">

      <!-- ตัวอย่างรูป -->
      <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1548545811-92523297a7da?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409325.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409977.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06869.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06887.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07259.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07277.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8711.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8723.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1623167198303-3453b3b64415?q=80&w=1200'">
  </div>

  <div class="masonry-item">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8813.jpg"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">

    </div>
  </div>
</section>

<!-- LIGHTBOX -->
<div id="lightbox" class="fixed inset-0 bg-black/60 backdrop-blur-sm hidden items-center justify-center p-4 z-50">
  <div class="bg-white rounded-lg p-4 max-w-3xl w-full">
    <div class="flex justify-end">
      <button onclick="closeLightbox()" class="text-gray-600 text-xl">×</button>
    </div>
    <img id="lbImg" class="w-full max-h-[75vh] object-contain rounded">
  </div>
</div>

<script>
function openLightbox(src){
  document.getElementById("lbImg").src = src;
  document.getElementById("lightbox").classList.remove("hidden");
}
function closeLightbox(){
  document.getElementById("lightbox").classList.add("hidden");
}
</script>

<!-- =================================== -->
<!-- SECTION: ทีมงาน & อุปกรณ์ -->
<!-- =================================== -->
<section class="py-20 bg-white">
  <div class="max-w-6xl mx-auto px-6 text-center">

    <h2 class="text-3xl font-extrabold mb-3">ยินดีให้บริการในวันสำคัญของคุณ</h2>
    <p class="text-gray-600 max-w-2xl mx-auto mb-10">
      ทีมงานมืออาชีพ พร้อมดูแลตั้งแต่ต้นจนจบพิธี
    </p>

    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
      <div class="p-6 bg-gray-50 rounded-2xl text-center shadow">
        <i class="fa-solid fa-user-group text-brand text-4xl mb-3"></i>
        <h3 class="font-bold">ช่างภาพ 2 คน</h3>
        <p class="text-sm text-gray-500">ครบทุกมุม</p>
      </div>

      <div class="p-6 bg-gray-50 rounded-2xl text-center shadow">
        <i class="fa-solid fa-camera text-brand text-4xl mb-3"></i>
        <h3 class="font-bold">กล้อง 3 ตัว</h3>
        <p class="text-sm text-gray-500">เลนส์ครบช่วง</p>
      </div>

      <div class="p-6 bg-gray-50 rounded-2xl text-center shadow">
        <i class="fa-solid fa-lightbulb text-brand text-4xl mb-3"></i>
        <h3 class="font-bold">ไฟ 6 ดวง</h3>
        <p class="text-sm text-gray-500">แสงสวยทุกช็อต</p>
      </div>

      <div class="p-6 bg-gray-50 rounded-2xl text-center shadow">
        <i class="fa-solid fa-wand-magic-sparkles text-brand text-4xl mb-3"></i>
        <h3 class="font-bold">รีทัชโทนโปร</h3>
        <p class="text-sm text-gray-500">Mood & Tone พรีเมียม</p>
      </div>
    </div>

  </div>
</section>

<!-- =================================== -->
<!-- SECTION: ดูแลใส่ใจ -->
<!-- =================================== -->
<section class="py-20 bg-[#fffaf8]">
  <div class="max-w-6xl mx-auto px-6 lg:px-8 grid grid-cols-1 lg:grid-cols-2 gap-8">

    <div>
      <h2 class="text-4xl font-extrabold leading-snug">
        มากกว่าแค่ถ่ายภาพ<br>
        คือการ <span class="text-brand">ดูแลใส่ใจ</span>
      </h2>
      <p class="text-gray-600 mt-4">
        ทีมงานของเราดูแลครบทุกขั้นตอน
      </p>
    </div>

    <div class="space-y-6">

      <div class="flex gap-4">
        <div class="w-12 h-12 bg-green-100 text-green-700 rounded-full flex items-center justify-center">
          <i class="fa-solid fa-list-check"></i>
        </div>
        <div>
          <h3 class="font-bold">ช่วยจัดลำดับพิธี</h3>
          <p class="text-sm text-gray-600">ให้คำแนะนำเพื่อให้งานลื่นไหล</p>
        </div>
      </div>

      <div class="flex gap-4">
        <div class="w-12 h-12 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center">
          <i class="fa-solid fa-heart"></i>
        </div>
        <div>
          <h3 class="font-bold">ดูแลทุกจังหวะสำคัญ</h3>
          <p class="text-sm text-gray-600">ไม่พลาดรอยยิ้มและน้ำตา</p>
        </div>
      </div>

      <div class="flex gap-4">
        <div class="w-12 h-12 bg-pink-100 text-pink-600 rounded-full flex items-center justify-center">
          <i class="fa-solid fa-image"></i>
        </div>
        <div>
          <h3 class="font-bold">เก็บภาพครบถ้วน</h3>
          <ul class="text-sm text-gray-600 list-disc list-inside">
            <li>ภาพพิธีการ</li>
            <li>ภาพครอบครัว</li>
            <li>ภาพบรรยากาศ</li>
            <li>ภาพรายละเอียด (Details)</li>
          </ul>
        </div>
      </div>

    </div>

  </div>
</section>

<!-- =================================== -->
<!-- SECTION: ระบบสแกนรูป QR -->
<!-- =================================== -->
<section class="py-20 bg-[#0f1724] text-white">
  <div class="max-w-6xl mx-auto px-6">

    <div class="bg-[#101826] p-10 rounded-3xl border border-white/10 grid grid-cols-1 md:grid-cols-3 gap-6">

      <div class="md:col-span-2">
        <span class="bg-brand text-black text-xs px-3 py-1 rounded-full">RECOMMENDED</span>

        <h3 class="text-4xl font-extrabold mt-3 leading-snug">
          บริการเสริมสุดฮิต!<br>
          <span class="text-brand">ระบบสแกน QR Code</span>
        </h3>

        <p class="mt-4 text-gray-300">
          รับรูปหน้างานทันที เหมาะสำหรับงานพิธี งานแต่ง งานบวช
        </p>

        <p class="mt-6 text-4xl font-extrabold text-brand">
          +1,000 <span class="text-white text-base">บาท</span>
        </p>
      </div>

      <div class="flex justify-center md:justify-end">
        <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/qr-placeholder.png"
             class="w-48 h-48 bg-white rounded-lg object-contain p-4 shadow">
      </div>

    </div>

  </div>
</section>

<!-- =================================== -->
<!-- SECTION: โปรโมชัน ราคา -->
<!-- =================================== -->
<section class="py-20 bg-white">
  <div class="max-w-6xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-2 gap-10">

    <!-- ส่งงาน -->
    <div class="bg-white p-8 rounded-2xl border shadow">
      <h3 class="text-xl font-bold flex items-center gap-3">
        <i class="fa-solid fa-clock text-blue-600"></i> กำหนดส่งงาน
      </h3>

      <ul class="mt-6 space-y-3">
        <li class="flex gap-2 text-gray-700">
          <i class="fa-solid fa-circle-check text-green-500"></i>
          ส่งงานภายใน 2 วัน
        </li>
        <li class="flex gap-2 text-gray-700">
          <i class="fa-solid fa-circle-check text-green-500"></i>
          ไฟล์ความละเอียดสูง
        </li>
        <li class="flex gap-2 text-gray-700">
          <i class="fa-solid fa-circle-check text-green-500"></i>
          อัปโหลดผ่าน Cloud Drive
        </li>
      </ul>
    </div>

    <!-- ราคา -->
    <div class="bg-[#fdf8ef] p-8 rounded-2xl border border-[#f0e7d3] shadow relative">

      <span class="absolute top-4 right-4 bg-brand text-white text-xs px-3 py-1 rounded-full">โปรโมชันปี 2024</span>

      <h3 class="text-xl font-bold flex items-center gap-3">
        <i class="fa-solid fa-tag text-brand"></i> ราคาแพ็กเกจ
      </h3>

      <p class="mt-4 font-bold">⭐ งานพิธี (ปกติ 5,500)</p>

      <div class="flex items-end gap-3 mt-3">
        <span class="text-5xl font-extrabold text-gray-900">4,000</span>
        <span>บาท</span>
        <span class="bg-red-500 text-white text-xs px-2 py-1 rounded">ลด 1,500</span>
      </div>

      <hr class="my-6">

      <div class="flex justify-between">
        <p>งานบวช เริ่มต้นที่</p>
        <p class="font-bold">3,500 บาท</p>
      </div>

      <div class="flex justify-between mt-3">
        <p>งานขาวดำ เริ่มต้นที่</p>
        <p class="font-bold">3,500 บาท</p>
      </div>

      <hr class="my-6">

      <div class="flex justify-between">
        <p><i class="fa-solid fa-wallet text-brand"></i> มัดจำจองคิว</p>
        <p class="font-bold">500 บาท</p>
      </div>

    </div>

  </div>
</section>

<!-- =================================== -->
<!-- SECTION: Pricing Toggle -->
<!-- =================================== -->

<section class="py-20 bg-white">
  <div class="max-w-5xl mx-auto px-6">

    <h2 class="text-3xl font-extrabold mb-2">ราคาแพ็กเกจ</h2>
    <p class="text-gray-600 mb-6">เลือกประเภทงานเพื่อดูราคา</p>

    <!-- Toggle -->
    <div class="inline-flex bg-gray-100 p-1 rounded-full mb-8">
      <button class="toggle-btn bg-white shadow px-5 py-2 rounded-full" data-key="ceremony">งานพิธี</button>
      <button class="toggle-btn px-5 py-2 rounded-full" data-key="prewedding">งานคู่รัก</button>
      <button class="toggle-btn px-5 py-2 rounded-full" data-key="family">งานครอบครัว</button>
    </div>

    <!-- Card -->
    <div id="priceCard" class="bg-[#fdf8ef] p-10 rounded-2xl shadow border border-[#e9dfc9]">

      <h3 id="pTitle" class="text-2xl font-bold">งานพิธี</h3>
      <p id="pDesc" class="text-gray-600 mt-1">รายละเอียดงานพิธี</p>

      <div class="flex items-end gap-3 mt-4">
        <span id="pPrice" class="text-5xl font-extrabold">4000</span>
        <span>บาท</span>
      </div>

      <ul id="pList" class="mt-6 space-y-2 text-gray-700">
      </ul>

    </div>

  </div>
</section>

<script>
const DATA = {
  ceremony: {
    title: "งานพิธี",
    desc: "ครอบคลุมทุกช็อตพิธีการ",
    price: "4000",
    list: ["ช่างภาพ 2 คน", "กล้อง 3 ตัว", "ไฟ 6 ดวง"]
  },
  prewedding: {
    title: "งานคู่รัก (พรีเวดดิ้ง)",
    desc: "ถ่ายภาพคู่รักโทนสวย",
    price: "2500",
    list: ["ไฟล์รีทัชโทนคู่รัก", "ภาพความละเอียดสูง", "ถ่ายนอกสถานที่"]
  },
  family: {
    title: "งานครอบครัว (ขึ้นบ้านใหม่)",
    desc: "เก็บภาพครอบครัวอบอุ่น",
    price: "3500",
    list: ["ช่างภาพ 1-2 คน", "เก็บภาพบรรยากาศ", "ไฟล์พร้อมส่ง Cloud"]
  }
};

document.querySelectorAll(".toggle-btn").forEach(btn=>{
  btn.addEventListener("click",()=>{
    document.querySelectorAll(".toggle-btn").forEach(b=>b.classList.remove("bg-white","shadow"));
    btn.classList.add("bg-white","shadow");

    const key = btn.dataset.key;
    const d = DATA[key];

    document.getElementById("pTitle").textContent = d.title;
    document.getElementById("pDesc").textContent = d.desc;
    document.getElementById("pPrice").textContent = d.price;

    const ul = document.getElementById("pList");
    ul.innerHTML = "";
    d.list.forEach(i=>{
      const li = document.createElement("li");
      li.textContent = "• " + i;
      ul.appendChild(li);
    });
  });
});
</script>

<!-- =================================== -->
<!-- CALENDAR (ย่อ version) -->
<!-- =================================== -->

<section id="booking" class="py-20 bg-white">
  <div class="max-w-6xl mx-auto px-6">
    <h2 class="text-2xl font-bold mb-4">จองคิวถ่ายภาพ</h2>
    <p class="text-gray-600 mb-4">เลือกวันที่ต้องการ</p>

    <iframe src="https://calendar.google.com/calendar/embed" class="w-full h-96 rounded-xl border"></iframe>
  </div>
</section>

<!-- =================================== -->
<!-- CONTACT -->
<!-- =================================== -->
<section class="py-12">
  <div class="max-w-4xl mx-auto text-center">
    <h3 class="text-xl font-bold mb-3">ติดต่อเรา</h3>
    <p class="text-gray-600">LINE: savethememory7 • โทร: 063-028-8737</p>
  </div>
</section>

</body>
</html>

