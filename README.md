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

    /* ===================== SCAN ANIMATION (NEW) ===================== */
    .qr-scanner {
      position: relative;
      overflow: hidden;
      border-radius: 8px;
    }
    .qr-scan-line {
      position: absolute;
      width: 100%;
      height: 4px;
      background: rgba(197, 160, 89, 0.8);
      box-shadow: 0 0 10px #C5A059, 0 0 20px #C5A059;
      top: 0;
      left: 0;
      animation: scanMove 2.5s infinite linear;
      z-index: 10;
    }
    .qr-glow {
      animation: pulseGlow 2s infinite ease-in-out;
    }
    
    @keyframes scanMove {
      0% { top: -10%; opacity: 0; }
      10% { opacity: 1; }
      90% { opacity: 1; }
      100% { top: 110%; opacity: 0; }
    }
    @keyframes pulseGlow {
      0%, 100% { box-shadow: 0 0 15px rgba(197, 160, 89, 0.2); }
      50% { box-shadow: 0 0 25px rgba(197, 160, 89, 0.6); }
    }

    /* ===================== LIGHTBOX CSS (NEW) ===================== */
    #lightbox {
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,.85);
      display: none;
      justify-content: center;
      align-items: center;
      padding: 20px;
      z-index: 9999;
    }

    #lightbox.active { display: flex; }

    .lb-card {
      background: #fff;
      border-radius: 16px;
      max-width: 900px;
      width: 100%;
      padding: 20px;
      display: flex;
      gap: 20px;
      animation: fadeIn .25s ease-out;
    }

    #lbImg {
      width: 50%;
      height: auto;
      border-radius: 12px;
      object-fit: cover;
    }

    .lb-content { flex: 1; }

    @media (max-width: 768px) {
      .lb-card { flex-direction: column; }
      #lbImg { width: 100%; }
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
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

  <!-- GALLERY -->
  <section id="portfolio" class="pb-12 pt-16">
    <div class="max-w-6xl mx-auto px-6">
      <h2 class="text-2xl font-bold mb-4">ผลงานที่ผ่านมา</h2>
      <p class="text-gray-600 mb-6">คลิกที่รูปเพื่อดูรายละเอียดและจองคิว</p>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">

        <!-- Image 1 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg"
               data-title="Pre-wedding Moment"
               data-desc="ภาพถ่ายพรีเวดดิ้งสไตล์โรแมนติก แสงธรรมชาติ"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1548545811-92523297a7da?q=80&w=1200'">
        </div>

        <!-- Image 2 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg"
               data-title="Thai Ceremony"
               data-desc="พิธีสวมมงคลสมรส บรรยากาศอบอุ่นเป็นกันเอง"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
        </div>

        <!-- Image 3 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409325.jpg"
               data-title="Wedding Details"
               data-desc="เก็บรายละเอียดของชำร่วยและแหวนแต่งงานอย่างประณีต"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <!-- Image 4 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409977.jpg"
               data-title="Candid Shot"
               data-desc="ช่วงเวลาเผลอที่เป็นธรรมชาติและมีความหมาย"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
        </div>

        <!-- Image 5 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06869.jpg"
               data-title="Family Group"
               data-desc="ภาพครอบครัวพร้อมหน้าพร้อมตาในวันสำคัญ"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
        </div>

        <!-- Image 6 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06887.jpg"
               data-title="Ceremony Setup"
               data-desc="การจัดวางองค์ประกอบในงานพิธีที่สวยงาม"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <!-- Image 7 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07259.jpg"
               data-title="Couple Portrait"
               data-desc="ภาพพอร์เทรตคู่รัก สื่ออารมณ์ความรักที่ชัดเจน"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
        </div>

        <!-- Image 8 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07277.jpg"
               data-title="Flower Shower"
               data-desc="ช็อตโปรยดอกไม้ แสดงความยินดี"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
        </div>

        <!-- Image 9 -->
        <div class="masonry-item">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8711.jpg"
               data-title="Wedding Rings"
               data-desc="แหวนแทนใจ สัญลักษณ์แห่งความรักนิรันดร์"
               class="w-full h-64 object-cover rounded-xl cursor-pointer hover:opacity-90 transition fade-up"
               onclick="openLightbox(this)"
               onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
        </div>
      </div>

    </div>
  </section>

  <!-- MORE CARE SECTION -->
  <section id="services" class="py-20 bg-[#fffaf8]">
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
        <div class="flex gap-4 fade-up">
          <div class="w-12 h-12 bg-green-100 text-green-700 rounded-full flex items-center justify-center">
            <i class="fa-solid fa-list-check"></i>
          </div>
          <div>
            <h3 class="font-bold">ช่วยจัดลำดับพิธี</h3>
            <p class="text-sm text-gray-600">ให้คำแนะนำเพื่อให้งานลื่นไหล</p>
          </div>
        </div>
        <div class="flex gap-4 fade-up">
          <div class="w-12 h-12 bg-blue-100 text-blue-700 rounded-full flex items-center justify-center">
            <i class="fa-solid fa-heart"></i>
          </div>
          <div>
            <h3 class="font-bold">ดูแลทุกจังหวะสำคัญ</h3>
            <p class="text-sm text-gray-600">ไม่พลาดรอยยิ้มและน้ำตา</p>
          </div>
        </div>
        <div class="flex gap-4 fade-up">
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

  <!-- PROMOTION / QR -->
  <section id="promo" class="py-20 bg-[#0f1724] text-white">
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
          
          <!-- Animated QR Section -->
          <div class="flex justify-center md:justify-end">
            <button id="openQrBtn" class="group relative bg-white/5 p-4 rounded-xl w-64 h-64 flex flex-col items-center justify-center hover:bg-white/10 transition qr-glow">
              
              <!-- QR Image with Scanner -->
              <div class="qr-scanner w-40 h-40 bg-white p-2 mb-2 relative">
                <!-- Using API to generate example QR for line ID -->
                <img id="qrImg" src="https://api.qrserver.com/v1/create-qr-code/?size=150x150&data=https://line.me/ti/p/~savethememory7" alt="qr" class="w-full h-full object-contain">
                <!-- Scan Line Animation -->
                <div class="qr-scan-line"></div>
              </div>

              <span class="bg-[#C5A059] text-black text-xs px-3 py-1 rounded-full font-bold mt-2 group-hover:scale-105 transition">
                <i class="fa-solid fa-camera mr-1"></i> SCAN ME
              </span>
            </button>
          </div>

        </div>
      </div>
    </div>
  </section>

  <!-- PRICING TOGGLE -->
  <section id="pricing" class="py-20 bg-white">
    <div class="max-w-5xl mx-auto px-6">
      <h2 class="text-3xl font-extrabold mb-2">ราคาแพ็กเกจ</h2>
      <p class="text-gray-600 mb-6">เลือกประเภทงานเพื่อดูราคา</p>

      <!-- Toggle -->
      <div class="inline-flex bg-gray-100 p-1 rounded-full mb-8">
        <button class="toggle-btn bg-white shadow px-5 py-2 rounded-full transition-all" data-key="ceremony">งานพิธี</button>
        <button class="toggle-btn px-5 py-2 rounded-full transition-all" data-key="prewedding">งานคู่รัก</button>
        <button class="toggle-btn px-5 py-2 rounded-full transition-all" data-key="family">งานครอบครัว</button>
      </div>

      <!-- Card -->
      <div id="priceCard" class="bg-[#fdf8ef] p-10 rounded-2xl shadow border border-[#e9dfc9] transition-all">
        <h3 id="pTitle" class="text-2xl font-bold">งานพิธี</h3>
        <p id="pDesc" class="text-gray-600 mt-1">รายละเอียดงานพิธี</p>
        <div class="flex items-end gap-3 mt-4">
          <span id="pPrice" class="text-5xl font-extrabold text-brand">4,000</span>
          <span>บาท</span>
        </div>
        <ul id="pList" class="mt-6 space-y-2 text-gray-700"></ul>
      </div>
    </div>
  </section>

  <!-- BOOKING calendar -->
  <!-- Added id="calendarGrid" so lightbox button can scroll here -->
  <section id="booking" class="py-20 bg-white" id="calendarGrid">
    <div class="max-w-6xl mx-auto px-6" id="calendarGrid"> <!-- ID added for scroll target -->
      <h2 class="text-2xl font-bold mb-4">จองคิวถ่ายภาพ</h2>
      <p class="text-gray-600 mb-4">เลือกวันที่ต้องการ</p>
      <iframe src="https://calendar.google.com/calendar/embed?src=en.th%23holiday%40group.v.calendar.google.com&ctz=Asia%2FBangkok" class="w-full h-96 rounded-xl border"></iframe>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" class="py-12">
    <div class="max-w-4xl mx-auto text-center">
      <h3 class="text-xl font-bold mb-3">ติดต่อเรา</h3>
      <p class="text-gray-600">LINE: savethememory7 • โทร: 063-028-8737</p>
    </div>
  </section>

  <!-- QR modal -->
  <div id="qrModal" class="fixed inset-0 z-50 hidden items-center justify-center bg-black/60 p-6">
    <div class="bg-white rounded-xl max-w-md w-full p-6 relative">
      <button id="closeQrModal" class="absolute top-4 right-4 text-gray-600 hover:text-gray-900"><i class="fa-solid fa-xmark"></i></button>
      <h4 class="font-bold text-lg mb-4">สแกนหรือดาวน์โหลดรูป</h4>
      <div class="flex flex-col items-center gap-4">
        <!-- Using API to generate example QR for line ID -->
        <img id="qrLarge" src="https://api.qrserver.com/v1/create-qr-code/?size=300x300&data=https://line.me/ti/p/~savethememory7" alt="QR" class="w-64 h-64 object-contain">
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

  <!-- ===================== LIGHTBOX HTML (NEW) ===================== -->
  <div id="lightbox">
    <div class="lb-card">
      <img id="lbImg" src="" alt="preview">
      <div class="lb-content">
        <div class="flex justify-between mb-3">
          <h3 id="lbTitle" class="text-lg font-bold"></h3>
          <button onclick="closeLightbox()" class="text-sm text-gray-500 hover:text-black">
            ปิด ✕
          </button>
        </div>
        <p id="lbDesc" class="text-gray-500 mb-6"></p>
        <button id="lbBook" class="px-5 py-2 rounded bg-[#C5A059] text-black font-semibold shadow hover:bg-[#b08d4b] transition">
          จองวันที่นี้
        </button>
      </div>
    </div>
  </div>

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

    // ======= QR modal =======
    const openQrBtn = qs('#openQrBtn');
    const qrModal = qs('#qrModal');
    const closeQrModal = qs('#closeQrModal');
    // Using user's Line ID
    const QR_TARGET_URL = 'https://line.me/ti/p/~savethememory7';
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

    qs('#prevSlide').addEventListener('click', ()=>{ stopAuto(); current = (current-1+heroSlides.length)%heroSlides.length; renderSlide(current); startAuto(); });
    qs('#nextSlide').addEventListener('click', ()=>{ stopAuto(); current = (current+1)%heroSlides.length; renderSlide(current); startAuto(); });

    const toggleBg = qs('#toggleBg'), heroVideo = qs('#heroVideo');
    toggleBg.addEventListener('click', ()=>{
      useVideo = !useVideo;
      if(useVideo && heroVideo.querySelector('source')){
        heroVideo.classList.remove('hidden'); slidesEl.classList.add('hidden'); heroVideo.play(); toggleBg.textContent = 'Video On';
      } else {
        heroVideo.pause(); heroVideo.classList.add('hidden'); slidesEl.classList.remove('hidden'); toggleBg.textContent = 'Video Off';
      }
    });

    renderSlide(current);
    startAuto();

    // ======= Pricing Toggle Logic =======
    const DATA = {
      ceremony: {
        title: "งานพิธี",
        desc: "ครอบคลุมทุกช็อตพิธีการสำคัญ ไม่พลาดทุกอารมณ์",
        price: "4,000",
        list: ["ช่างภาพ 2 คน", "กล้อง 3 ตัว", "ไฟส่องสว่าง 6 ดวง", "ไฟล์ภาพความละเอียดสูง"]
      },
      prewedding: {
        title: "งานคู่รัก (พรีเวดดิ้ง)",
        desc: "ถ่ายภาพคู่รักโทนสวย สบายๆ เป็นธรรมชาติ",
        price: "2,500",
        list: ["ไฟล์รีทัชโทนคู่รัก", "ภาพความละเอียดสูง", "ถ่ายนอกสถานที่ (ไม่รวมค่าเดินทาง)"]
      },
      family: {
        title: "งานครอบครัว (ขึ้นบ้านใหม่)",
        desc: "เก็บบรรยากาศอบอุ่นของครอบครัว",
        price: "3,500",
        list: ["ช่างภาพ 1-2 คน", "เก็บภาพบรรยากาศ", "ไฟล์พร้อมส่ง Cloud Drive"]
      }
    };

    const toggleBtns = document.querySelectorAll(".toggle-btn");
    const pTitle = document.getElementById("pTitle");
    const pDesc = document.getElementById("pDesc");
    const pPrice = document.getElementById("pPrice");
    const pList = document.getElementById("pList");

    // Init first item
    renderPricing("ceremony");

    toggleBtns.forEach(btn=>{
      btn.addEventListener("click",()=>{
        toggleBtns.forEach(b=>b.classList.remove("bg-white","shadow"));
        btn.classList.add("bg-white","shadow");
        renderPricing(btn.dataset.key);
      });
    });

    function renderPricing(key){
      const d = DATA[key];
      pTitle.textContent = d.title;
      pDesc.textContent = d.desc;
      pPrice.textContent = d.price;
      pList.innerHTML = "";
      d.list.forEach(i=>{
        const li = document.createElement("li");
        li.innerHTML = `<i class="fa-solid fa-check text-[#C5A059] mr-2"></i>${i}`;
        pList.appendChild(li);
      });
    }

    // ===================== LIGHTBOX JS (UPDATED) =====================
    function openLightbox(img) {
      qs("#lbImg").src = img.src;
      qs("#lbTitle").textContent = img.dataset.title || "รายละเอียดภาพ";
      qs("#lbDesc").textContent = img.dataset.desc || "";
      qs("#lightbox").classList.add("active");

      qs("#lbBook").onclick = () => {
        closeLightbox();
        window.scrollTo({ top: document.querySelector("#calendarGrid").offsetTop - 20, behavior: "smooth" });
      };
    }

    function closeLightbox() {
      qs("#lightbox").classList.remove("active");
    }

    document.addEventListener("keydown", e => {
      if (e.key === "Escape") closeLightbox();
    });

  </script>
</body>
</html>
