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
