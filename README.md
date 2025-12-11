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
    .portfolio-img { width:100%; height:18rem; object-fit:cover; display:block; background:#f5f5f5; }
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
    </div>
  </section>

  <!-- PORTFOLIO -->
  <section id="portfolio" class="py-20 bg-stone-50">
    <div class="container mx-auto px-6">
      <div class="text-center max-w-3xl mx-auto mb-10 reveal">
        <h2 class="text-3xl font-bold text-gray-900 mb-3">ผลงานที่ผ่านมา</h2>
        <p class="text-gray-600">ตัวอย่างภาพจากงานพิธีต่าง ๆ — หากไฟล์รูปอยู่ในโฟลเดอร์เดียวกับไฟล์นี้ รูปจะแสดงขึ้น</p>
      </div>

<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 reveal">

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1548545811-92523297a7da?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409325.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409977.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06869.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC06887.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07259.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1606800052052-a08af7148866?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/DSC07277.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8711.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8723.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1623167198303-3453b3b64415?q=80&w=1200'">
  </div>

  <div class="overflow-hidden rounded-xl shadow">
    <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/IMG_8813.jpg"
         alt="portfolio" class="portfolio-img"
         onerror="this.src='https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=1200'">
  </div>

</div>

  </section>
<!-- ===== Booking / Availability Calendar (ว่าง/เต็ม) ===== -->
<section id="booking" class="py-12 bg-white">
  <div class="container mx-auto px-6">
    <div class="text-center mb-6">
      <h2 class="text-2xl font-bold">เช็คคิวงาน / จองคิว</h2>
      <p class="text-gray-600">คลิกวันที่ที่ต้องการเพื่อดูสถานะหรือจองคิว — ระบบจะเปิดแชท LINE ให้กรอกข้อมูลยืนยัน</p>
    </div>

    <div class="max-w-3xl mx-auto bg-stone-50 p-6 rounded-xl shadow">
      <div class="flex items-center justify-between mb-4">
        <div>
          <button id="prevMonth" class="px-3 py-1 rounded bg-gray-200 hover:bg-gray-300">‹</button>
          <button id="nextMonth" class="px-3 py-1 rounded bg-gray-200 hover:bg-gray-300">›</button>
        </div>
        <div class="text-lg font-semibold" id="calendarLabel">เดือน ปี</div>
        <div>
          <button id="resetView" class="px-3 py-1 rounded bg-brand-gold text-white">วันนี้</button>
        </div>
      </div>

      <div id="calendar" class="grid grid-cols-7 gap-2 text-sm">
        <!-- หัววัน -->
        <div class="text-center font-medium">อา</div>
        <div class="text-center font-medium">จ</div>
        <div class="text-center font-medium">อ</div>
        <div class="text-center font-medium">พ</div>
        <div class="text-center font-medium">พฤ</div>
        <div class="text-center font-medium">ศ</div>
        <div class="text-center font-medium">ส</div>
        <!-- วันจะถูกเติมด้วย JS -->
      </div>

      <div class="mt-4 flex items-center gap-4">
        <div class="inline-flex items-center gap-2"><span class="w-4 h-4 block rounded" style="background:#C5A059"></span> มีคิว (เต็ม)</div>
        <div class="inline-flex items-center gap-2"><span class="w-4 h-4 block rounded bg-white border"></span> ว่าง</div>
        <div class="ml-auto text-xs text-gray-500">จดจำคิวในเบราเซอร์นี้ (local)</div>
      </div>

      <div class="mt-6">
        <div class="text-sm text-gray-700 mb-2 font-medium">คิวที่จองแล้ว (ตัวอย่าง)</div>
        <ul id="bookedList" class="text-sm text-gray-600 list-disc list-inside"></ul>
      </div>
    </div>
  </div>
</section>

<script>
/*
  Simple availability calendar
  - เก็บคิวใน localStorage (key: "stm_bookings")
  - รูปแบบวันที่: YYYY-MM-DD
  - ถ้าต้องการดึงจากไฟล์ JSON ของ repo ให้แก้ fetchBookings() ให้เรียกไฟล์ raw JSON
*/

// ---- ตัวอย่างคิวเริ่มต้น (ถ้าต้องการให้เริ่มว่าง ให้ลบรายการนี้) ----
let exampleBooked = [
  // "2025-12-24", "2025-12-31"
];

// ---- ฟังก์ชันช่วยเหลือ ----
function toISO(date) {
  const y = date.getFullYear();
  const m = String(date.getMonth()+1).padStart(2,'0');
  const d = String(date.getDate()).padStart(2,'0');
  return `${y}-${m}-${d}`;
}

// ---- อ่าน/เขียนคิวจาก localStorage ----
function loadBookings() {
  const raw = localStorage.getItem('stm_bookings');
  if (!raw) {
    // เริ่มด้วย example (ถ้ามี)
    localStorage.setItem('stm_bookings', JSON.stringify(exampleBooked));
    return exampleBooked.slice();
  }
  try {
    return JSON.parse(raw) || [];
  } catch(e) {
    return [];
  }
}

function saveBookings(list) {
  localStorage.setItem('stm_bookings', JSON.stringify(list));
}

// ---- ตัวแปรสถานะปฏิทิน ----
let current = new Date();
let bookedDates = loadBookings();

// ---- render calendar ----
function renderCalendar(year, month) {
  const calendar = document.getElementById('calendar');
  // เก็บหัววันไว้แล้ว: เคลียร์เฉพาะวันจริง (ตำแหน่ง 7 ข้อความแรกคือหัว)
  // ลบทุกอย่างหลังหัววัน
  while (calendar.children.length > 7) calendar.removeChild(calendar.lastChild);

  const first = new Date(year, month, 1);
  const last = new Date(year, month + 1, 0);
  const startDay = first.getDay(); // 0-6
  const totalDays = last.getDate();

  // ใส่ช่องว่างก่อนวันแรก
  for (let i=0;i<startDay;i++){
    const empty = document.createElement('div');
    empty.className = 'h-20';
    calendar.appendChild(empty);
  }

  for (let d=1; d<=totalDays; d++){
    const day = new Date(year, month, d);
    const iso = toISO(day);
    const cell = document.createElement('div');
    cell.className = 'h-24 p-2 rounded-lg flex flex-col justify-between cursor-pointer masonry-day';
    const isBooked = bookedDates.includes(iso);

    // style
    cell.style.border = '1px solid rgba(0,0,0,0.06)';
    cell.style.background = isBooked ? '#C5A059' : '#fff';
    cell.style.color = isBooked ? '#fff' : '#111';
    cell.title = isBooked ? 'มีคิวแล้ว' : 'ว่าง';

    // inner
    const top = document.createElement('div');
    top.className = 'flex justify-between items-start';
    const dateSpan = document.createElement('div');
    dateSpan.className = 'text-sm font-medium';
    dateSpan.textContent = d;
    const statusSpan = document.createElement('div');
    statusSpan.className = 'text-xs';
    statusSpan.textContent = isBooked ? 'เต็ม' : 'ว่าง';
    top.appendChild(dateSpan);
    top.appendChild(statusSpan);

    const btnWrap = document.createElement('div');
    btnWrap.className = 'text-right';
    const btn = document.createElement('button');
    btn.className = 'px-3 py-1 rounded text-xs';
    btn.textContent = isBooked ? 'ดู/ยกเลิก' : 'จอง';
    btn.style.background = isBooked ? 'rgba(0,0,0,0.12)' : '#C5A059';
    btn.style.color = isBooked ? '#fff' : '#fff';
    btn.onclick = function(e){
      e.stopPropagation();
      onDateClick(iso);
    };
    btnWrap.appendChild(btn);

    cell.appendChild(top);
    cell.appendChild(btnWrap);

    calendar.appendChild(cell);
  }

  // label
  const label = document.getElementById('calendarLabel');
  label.textContent = `${year} / ${String(month+1).padStart(2,'0')}`;
  renderBookedList();
}

// ---- แสดงรายการคิวด้านล่าง ----
function renderBookedList() {
  const list = document.getElementById('bookedList');
  list.innerHTML = '';
  if (!bookedDates.length) {
    list.innerHTML = '<li>ยังไม่มีคิวจอง</li>';
    return;
  }
  // แสดงเรียงจากใกล้->ไกล
  const sorted = bookedDates.slice().sort();
  for (const d of sorted) {
    const li = document.createElement('li');
    li.textContent = d;
    // ปุ่มยกเลิก
    const cancel = document.createElement('button');
    cancel.textContent = ' ยกเลิก';
    cancel.className = 'ml-3 text-xs text-red-600';
    cancel.onclick = function(){
      if (!confirm('ยืนยันยกเลิกคิว '+d+' ?')) return;
      bookedDates = bookedDates.filter(x=>x!==d);
      saveBookings(bookedDates);
      renderCalendar(current.getFullYear(), current.getMonth());
    };
    li.appendChild(cancel);
    list.appendChild(li);
  }
}

// ---- เมื่อคลิกวันที่ ----
function onDateClick(isoDate) {
  const isBooked = bookedDates.includes(isoDate);
  if (isBooked) {
    // ยืนยันดู/ยกเลิก -> เราให้ยกเลิกได้
    if (!confirm('วันที่ '+isoDate+' มีคิวแล้ว ต้องการยกเลิกไหม?')) return;
    bookedDates = bookedDates.filter(x=>x!==isoDate);
    saveBookings(bookedDates);
    renderCalendar(current.getFullYear(), current.getMonth());
    alert('ยกเลิกคิวเรียบร้อย (local)');
    return;
  }

  // ถ้าว่าง -> ยืนยันจองและส่ง LINE
  const want = confirm('วันที่ '+isoDate+' ว่าง — ต้องการจองวันที่นี้หรือไม่? (จะเปิด LINE เพื่อส่งข้อความยืนยัน)');
  if (!want) return;

  // เซฟ local ก่อน แล้วเปิด LINE chat พร้อมข้อความ
  bookedDates.push(isoDate);
  saveBookings(bookedDates);
  renderCalendar(current.getFullYear(), current.getMonth());

  // สร้างข้อความการจอง (ปรับตามต้องการ)
  const text = encodeURIComponent(`สวัสดีครับ/ค่ะ ผมอยากจองคิวถ่ายภาพวันที่ ${isoDate} ชื่อ: ___ เบอร์ติดต่อ: ___`);
  // เปลี่ยนเป็น Line ID ของร้าน (savethememory7) หรือ link ที่น๊อตต้องการ
  const lineURL = `https://line.me/ti/p/~savethememory7?text=${text}`;

  // เปิดหน้าใหม่ (หรือ window.location.href)
  window.open(lineURL,'_blank');
}

// ---- ปุ่ม prev/next/today ----
document.getElementById('prevMonth').addEventListener('click', ()=>{
  current.setMonth(current.getMonth()-1);
  renderCalendar(current.getFullYear(), current.getMonth());
});
document.getElementById('nextMonth').addEventListener('click', ()=>{
  current.setMonth(current.getMonth()+1);
  renderCalendar(current.getFullYear(), current.getMonth());
});
document.getElementById('resetView').addEventListener('click', ()=>{
  current = new Date();
  renderCalendar(current.getFullYear(), current.getMonth());
});

// ---- initial render ----
renderCalendar(current.getFullYear(), current.getMonth());

/* ----- ขยาย: ถ้าต้องการดึงคิวจากไฟล์ JSON ใน repo (raw.githubusercontent.com)
ตัวอย่าง: เก็บไฟล์ bookings.json ใน repo (path: /data/bookings.json)
เนื้อหา: ["2025-12-24","2025-12-31"]
ถ้าต้องการให้ระบบดึงแทน localStorage ให้ใช้โค้ดนี้แทน loadBookings() หรือเรียก fetch ในตอนโหลดหน้า:
fetch('https://raw.githubusercontent.com/USERNAME/REPO/main/data/bookings.json')
  .then(r=>r.json()).then(arr=>{
     bookedDates = arr || [];
     saveBookings(bookedDates); // อัพเดต local
     renderCalendar(current.getFullYear(), current.getMonth());
  });
หมายเหตุ: ถ้าเปลี่ยนไฟล์ JSON ใน repo ต้อง commit และ GitHub Pages จะอัปเดต
*/
</script>

  <!-- ... ส่วนที่เหลือเหมือนเดิม ... -->

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
