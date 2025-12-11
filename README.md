<style>
  /* Masonry layout */
  .masonry {
    column-count: 1;
    column-gap: 1rem;
  }

  @media (min-width: 640px) {
    .masonry {
      column-count: 2;
    }
  }

  @media (min-width: 1024px) {
    .masonry {
      column-count: 3;
    }
  }

  .masonry-item {
    break-inside: avoid;
    margin-bottom: 1rem;
    overflow: hidden;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
  }

  .masonry-item img {
    width: 100%;
    display: block;
    border-radius: 12px;
    transition: transform .4s ease;
  }

  .masonry-item img:hover {
    transform: scale(1.05);
  }
</style>

<div class="masonry reveal">
  
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
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Save The Memory — Portfolio & Booking</title>
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  <style>
    body{font-family: 'Prompt', sans-serif;}
    .portfolio-img{width:100%;height:18rem;object-fit:cover;background:#f5f5f5;}
    #lightbox{backdrop-filter: blur(4px);}
    .disabled-day{opacity:0.4; pointer-events:none;}
  </style>
</head>
<body class="bg-stone-50 text-gray-800">

  <nav class="fixed top-0 w-full z-50 bg-white/90 py-4 px-6 shadow">
    <div class="max-w-6xl mx-auto flex justify-between items-center">
      <a href="#" class="text-lg font-bold">SAVE THE MEMORY</a>
      <div class="hidden md:flex gap-6">
        <a href="#portfolio">ผลงาน</a>
        <a href="#contact" class="px-3 py-1 bg-yellow-500 text-white rounded-md">จองคิว</a>
      </div>
    </div>
  </nav>

  <section class="pt-28 pb-12">
    <div class="max-w-6xl mx-auto px-6">
      <h2 class="text-2xl font-bold mb-4">ผลงานที่ผ่านมา</h2>
      <p class="text-gray-600 mb-6">คลิกที่รูปเพื่อดูภาพใหญ่ และกด "จองวันที่นี้" เพื่อจอง</p>

      <!-- Gallery: เปลี่ยนลิงก์รูปเป็นของน๊อต (raw.githubusercontent หรือโฮสต์อื่น) -->
      <div id="gallery" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <!-- ตัวอย่างรูป — เปลี่ยน src ให้ตรงกับไฟล์ที่อัพไว้ใน repo -->
        <div class="overflow-hidden rounded-xl shadow">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7400001.jpg"
               class="portfolio-img cursor-pointer"
               alt="portfolio"
               data-title="งานพิธี A"
               data-desc="รายละเอียดสั้น ๆ ของงานนี้"
               onclick="openLightbox(this)">
        </div>

        <div class="overflow-hidden rounded-xl shadow">
          <img src="https://raw.githubusercontent.com/notbyebye113-max/my-portfolio/main/A7409308.jpg"
               class="portfolio-img cursor-pointer"
               alt="portfolio"
               data-title="งานพิธี B"
               data-desc="รายละเอียดสั้น ๆ ของงานนี้"
               onclick="openLightbox(this)">
        </div>

        <!-- เพิ่ม <div> รูปตามที่ต้องการ โดยแก้ src -->
      </div>
    </div>
  </section>

  <!-- Lightbox Modal -->
  <div id="lightbox" class="fixed inset-0 z-50 hidden items-center justify-center bg-black/60 p-4">
    <div class="bg-white rounded-lg max-w-4xl w-full p-4">
      <div class="flex justify-between items-start">
        <div>
          <h3 id="lbTitle" class="text-xl font-bold"></h3>
          <p id="lbDesc" class="text-gray-600 text-sm"></p>
        </div>
        <div>
          <button class="text-gray-500" onclick="closeLightbox()">✕</button>
        </div>
      </div>

      <div class="mt-3">
        <img id="lbImg" src="" alt="" class="w-full h-[480px] object-contain bg-gray-100 rounded">
      </div>

      <div class="mt-4 flex items-center justify-between">
        <div>
          <label class="text-sm text-gray-600">เลือกวันที่จะจอง (YYYY-MM-DD):</label>
          <input id="bookDate" type="date" class="ml-2 p-2 border rounded" />
        </div>
        <div class="flex gap-2">
          <button onclick="openQuickBook()" class="px-4 py-2 bg-brand-gold text-white rounded" style="background:#C5A059">จองวันที่นี้</button>
          <button onclick="closeLightbox()" class="px-4 py-2 border rounded">ปิด</button>
        </div>
      </div>
      <p id="lbNote" class="text-sm text-gray-500 mt-2"></p>
    </div>
  </div>

  <!-- Toast -->
  <div id="toast" class="fixed bottom-6 right-6 hidden bg-black text-white px-4 py-2 rounded"></div>

  <!-- Contact placeholder -->
  <section id="contact" class="py-12">
    <div class="max-w-4xl mx-auto px-6">
      <div class="bg-white p-6 rounded-lg shadow text-center">
        <h3 class="text-xl font-bold mb-3">ติดต่อเรา</h3>
        <p class="text-gray-600">LINE: savethememory7 • โทร: 063-028-8737</p>
      </div>
    </div>
  </section>

<script>
/* ====== ตั้งค่านี้ก่อนใช้งาน ======
   - API_URL: เอา Web App URL จากขั้นตอน deploy Apps Script (doGet/doPost)
   - ถ้าอยากให้คนจองต้องกรอกชื่อ/เบอร์ใน modal ให้แก้ฟังก์ชัน openQuickBook ให้เรียกฟอร์มเพิ่มเติม
*/
const API_URL = 'REPLACE_WITH_YOUR_APPS_SCRIPT_WEBAPP_URL'; // <-- ใส่ตรงนี้

// helpers
function showToast(msg, timeout=3000){
  const t = document.getElementById('toast');
  t.textContent = msg; t.classList.remove('hidden');
  setTimeout(()=> t.classList.add('hidden'), timeout);
}

// open lightbox from clicked <img>
function openLightbox(imgEl){
  const src = imgEl.src;
  const title = imgEl.dataset.title || 'Photo';
  const desc = imgEl.dataset.desc || '';
  document.getElementById('lbImg').src = src;
  document.getElementById('lbTitle').textContent = title;
  document.getElementById('lbDesc').textContent = desc;
  document.getElementById('bookDate').value = ''; // reset
  document.getElementById('lbNote').textContent = '';
  document.getElementById('lightbox').classList.remove('hidden');

  // optionally pre-fill date (none here)
}

// close
function closeLightbox(){ document.getElementById('lightbox').classList.add('hidden'); }

// fetch bookings (GET)
async function fetchBookings(){
  try{
    const r = await fetch(API_URL);
    if(!r.ok) throw new Error('fetch fail');
    const arr = await r.json();
    return arr; // array of row objects (date,name,...)
  } catch(e){
    console.error(e);
    return [];
  }
}

// post booking (POST)
async function postBooking(payload){
  try{
    const r = await fetch(API_URL, {
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body: JSON.stringify(payload)
    });
    const j = await r.json();
    return j;
  } catch(e){
    console.error(e);
    return {ok:false, error:e.message};
  }
}

// quick book (from lightbox)
async function openQuickBook(){
  const dateInput = document.getElementById('bookDate').value;
  if(!dateInput){
    return alert('เลือกวันที่ก่อน');
  }
  const name = prompt('กรอกชื่อผู้จอง (จำเป็น)');
  if(!name) return alert('ต้องกรอกชื่อ');
  const phone = prompt('กรอกเบอร์ (ถ้ามี)');
  // ตรวจสอบคิวก่อนโพส (fetch bookings)
  const bookings = await fetchBookings();
  const taken = bookings.filter(b => b.date === dateInput && (b.status||'').toLowerCase() === 'booked');
  if(taken.length>0){
    if(!confirm('วันที่นี้มีคนจองแล้ว ต้องการจองทับหรือไม่?')) return;
  }
  // ส่ง POST
  showToast('กำลังจอง...');
  const res = await postBooking({ date: dateInput, name: name, phone: phone||'', email:'', notes:`จองจากหน้าเว็บ - รูป: ${document.getElementById('lbTitle').textContent}` });
  if(res && res.ok){
    showToast('จองเรียบร้อยแล้ว 🎉', 4000);
    closeLightbox();
  } else {
    showToast('จองไม่สำเร็จ: '+(res.error || 'unknown'));
  }
}

/* --- ปรับปรุง UI เพิ่ม: ทำให้วันที่มีคิวแสดงเป็น disabled ใน date picker --- */
async function markBookedDatesInPicker(){
  const bookings = await fetchBookings();
  const dateSet = new Set(bookings.filter(b=> (b.status||'').toLowerCase()==='booked').map(b=>b.date));
  const dp = document.getElementById('bookDate');
  // ไม่มีวิธี standard ปิดวันที่ใน native date input -> แสดงโน้ตด้านล่างแทน
  const bookedList = Array.from(dateSet).slice(0,30).join(', ');
  if(bookedList){
    document.getElementById('lbNote').textContent = 'วันที่ที่มีคิวแล้ว (ตัวอย่าง): ' + bookedList;
  } else {
    document.getElementById('lbNote').textContent = '';
  }
}

// initial
(async function init(){
  // ตรวจสอบ API_URL ความถูกต้องคร่าว ๆ
  if(API_URL.includes('REPLACE_WITH')){
    console.warn('ยังไม่ได้ตั้งค่า API_URL ใน index.html — ใส่ Web App URL จาก Apps Script');
  } else {
    await markBookedDatesInPicker();
  }
})();
</script>

</body>
</html>
