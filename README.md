<!doctype html>
<html lang="th">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Notto.Studio — Photo Portal</title>
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"/>
<!-- QRCode.js Library -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
<!-- HTML5-QRCode Library -->
<script src="https://unpkg.com/html5-qrcode" type="text/javascript"></script>

<style>
  :root{
    --bg:#faf9f6;
    --card:#fff;
    --muted:#6b7280;
    --accent:#c49a53;
    --guest-accent: #c49a53;
    --guest-title-color: #0f172a;
    --guest-title-size: 2.2rem;
    --cover-height: 220px;
    --shadow:0 6px 18px rgba(12,12,12,0.06);
    --bg-cover-desktop: url('https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=2000&auto=format&fit=crop');
    --bg-cover-mobile: url('https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=1000&auto=format&fit=crop');
  }
  body{font-family:Inter,system-ui,Segoe UI,Roboto,Arial;background:var(--bg);margin:0;color:#111;}
  
  header{display:flex;align-items:center;justify-content:space-between;padding:14px 24px;background:linear-gradient(90deg,#fff 0%, #fff0 100%);box-shadow:0 1px 0 rgba(0,0,0,0.04);position:sticky;top:0;z-index:30;}
  header h1{font-size:18px;margin:0;color:#0f172a;}
  
  .container{max-width:1200px;margin:18px auto;padding:0 18px;}
  .layout{display:grid;grid-template-columns:350px 1fr;gap:18px;align-items:start;} 
  .card{background:var(--card);border-radius:12px;padding:14px;box-shadow:var(--shadow);}
  
  .btn{background:var(--accent);color:#fff;padding:10px 12px;border-radius:10px;border:0;cursor:pointer;font-weight:600; transition: all 0.2s;}
  .btn:hover{filter: brightness(0.95); transform: translateY(-1px);}
  .btn.ghost{background:transparent;border:1px solid #ddd;color:var(--muted);font-weight:600;}
  .btn.blue{background:#3b82f6;color:white;border:none;}
  .btn.dark{background:#1e293b;color:white;border:none;}
  .btn.green{background:#10b981;color:white;border:none;}
  .btn.drive{background:#1f2937;color:white;border:none; display:flex; align-items:center; justify-content:center; gap:8px;}
  
  .source-toggle { display: flex; background: #f1f5f9; padding: 4px; border-radius: 12px; margin-bottom: 20px; }
  .source-toggle .btn { flex: 1; border-radius: 8px; font-size: 14px; padding: 8px; color: #64748b; background: transparent; box-shadow: none; }
  .source-toggle .btn.active { background: #fff; color: #0f172a; box-shadow: 0 2px 5px rgba(0,0,0,0.05); font-weight: 700; }

  input[type="text"], input[type="password"] { width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 6px; box-sizing: border-box; }
  
  .style-box { background: #fff8eb; border: 1px dashed #fcd34d; border-radius: 10px; padding: 16px; margin-bottom: 20px;}
  .style-box h4 { margin: 0 0 12px 0; font-size: 15px; color: #92400e; display:flex; align-items:center; gap:6px;}
  .input-group { margin-bottom: 12px; }
  .input-group label { display: block; font-size: 12px; color: #666; margin-bottom: 4px; font-weight: 500;}
  
  input[type=range] { -webkit-appearance: none; width: 100%; background: transparent; margin: 8px 0; }
  input[type=range]::-webkit-slider-thumb { -webkit-appearance: none; height: 16px; width: 16px; border-radius: 50%; background: var(--accent); cursor: pointer; margin-top: -6px; }
  input[type=range]::-webkit-slider-runnable-track { width: 100%; height: 4px; cursor: pointer; background: #ddd; border-radius: 2px; }

  /* Login View */
  #loginView { display: flex; align-items: center; justify-content: center; min-height: 100vh; background: #f8fafc; position: relative; z-index: 100; }
  .login-card { background: #fff; width: 100%; max-width: 420px; border-radius: 24px; box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.1); overflow: hidden; margin: 20px; }
  .login-cover { height: 180px; background-image: url('https://images.unsplash.com/photo-1469334031218-e382a71b716b?q=80&w=1600&auto=format&fit=crop'); background-size: cover; background-position: center; position: relative; }
  .login-cover::after { content: ''; position: absolute; inset: 0; background: linear-gradient(to top, rgba(0,0,0,0.6), transparent); }
  .login-body { padding: 32px; text-align: center; }
  .login-title { font-size: 28px; font-weight: 800; margin: 0 0 8px 0; color: #0f172a; letter-spacing: -0.5px; }
  .login-subtitle { color: #64748b; font-size: 14px; margin-bottom: 24px; }
  .login-input { width: 100%; padding: 12px 16px; margin-bottom: 12px; border: 1px solid #e2e8f0; border-radius: 12px; font-size: 15px; transition: all 0.2s; outline: none; }
  .login-input:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(196, 154, 83, 0.1); }
  .login-btn { width: 100%; padding: 12px; background: var(--accent); color: white; font-weight: 600; border: none; border-radius: 12px; cursor: pointer; font-size: 16px; margin-top: 8px; transition: background 0.2s; }
  .login-btn:hover { background: #b08a4a; }

  /* Guest View */
  #guestView { display: none; background: #fff; min-height: 100vh; padding: 0 0 80px 0; text-align: center; position: relative; }
  #guestView.active { display: block; }
  .guest-cover { width: 100%; height: var(--cover-height); background-color: #eee; background-size: cover; background-position: center; position: relative; margin-bottom: -40px; border-bottom-left-radius: 40px; border-bottom-right-radius: 40px; box-shadow: 0 10px 30px rgba(0,0,0,0.1); transition: height 0.3s ease; }
  @media (orientation: landscape) { .guest-cover { background-image: var(--bg-cover-desktop); } }
  @media (orientation: portrait) { .guest-cover { background-image: var(--bg-cover-mobile); } }
  .guest-content-wrapper { position: relative; z-index: 10; padding: 0 24px; }
  .guest-header { margin-bottom: 30px; margin-top: 10px; padding: 0 10px; }
  .guest-header h1 { font-size: var(--guest-title-size); color: var(--guest-title-color); margin-bottom: 8px; font-weight: 800; line-height: 1.2; text-shadow: 0 2px 10px rgba(255,255,255,0.8); }
  .guest-info h2 { font-size: 1.2rem; font-weight: 500; color: #475569; margin: 0 0 8px 0; }
  .guest-info p { font-size: 0.95rem; color: #64748b; margin: 0; display:flex; align-items:center; justify-content:center; gap:8px; }
  .drive-link-card { background: white; border-radius: 24px; padding: 30px 20px; box-shadow: 0 20px 60px rgba(0,0,0,0.08); margin-top: 30px; border: 1px solid #f1f5f9; max-width: 400px; margin-left: auto; margin-right: auto; display: none; }
  .drive-link-card.visible { display: block; }
  .drive-btn { background: var(--guest-accent); color: white; padding: 16px 24px; border-radius: 16px; font-size: 16px; font-weight: 600; text-decoration: none; display: inline-flex; align-items: center; gap: 10px; box-shadow: 0 10px 20px rgba(0,0,0,0.15); transition: transform 0.2s; width: 100%; justify-content: center; border: none; cursor: pointer; }
  .drive-btn:hover { transform: translateY(-2px); box-shadow: 0 15px 30px rgba(0,0,0,0.2); }
  .guest-qr-container { background: white; padding: 12px; border-radius: 16px; box-shadow: 0 10px 30px rgba(0,0,0,0.08); display: inline-block; margin-bottom: 20px; border: 4px solid var(--guest-accent); }
  .back-home-btn { position: absolute; top: 20px; left: 20px; background: rgba(255,255,255,0.9); border: 1px solid rgba(0,0,0,0.1); color: #333; padding: 8px 16px; border-radius: 12px; font-weight: 600; cursor: pointer; display: flex; align-items: center; gap: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); transition: all 0.2s; z-index: 50; }
  .back-home-btn:hover { background: #fff; transform: translateY(-2px); box-shadow: 0 4px 12px rgba(0,0,0,0.15); }
  .guest-watermark { position: fixed; bottom: 20px; right: 20px; background: rgba(255, 255, 255, 0.9); padding: 8px 16px; border-radius: 12px; font-size: 13px; color: #444; font-weight: 600; box-shadow: 0 4px 15px rgba(0,0,0,0.1); z-index: 40; pointer-events: none; display: none; align-items: center; gap: 10px; backdrop-filter: blur(5px); border: 1px solid rgba(255,255,255,0.5); }
  .guest-watermark.visible { display: flex; }
  .guest-watermark span { color: var(--guest-accent); }
  .guest-watermark img { max-height: 30px; width: auto; display: block; border-radius: 4px; }
  .exit-btn { position: fixed; bottom: 20px; left: 20px; opacity: 0.5; transition: opacity 0.3s; background: #000; color: #fff; padding: 8px 16px; border-radius: 30px; font-size: 12px; border: none; cursor: pointer; z-index: 50; }
  .exit-btn:hover { opacity: 1; }

  .guest-gallery-container { max-width: 1200px; margin: 0 auto; text-align: left; padding: 0 20px; }

  /* Photo Card */
  .photo-card { position: relative; }
  .download-icon-btn { position: absolute; top: 10px; right: 10px; width: 44px; height: 44px; border-radius: 50%; background: var(--guest-accent); border: 2px solid white; box-shadow: 0 4px 10px rgba(0,0,0,0.2); display: flex; align-items: center; justify-content: center; cursor: pointer; opacity: 1; z-index: 10; color: #fff; font-size: 20px; transition: transform 0.2s ease; }
  .download-icon-btn:hover { transform: scale(1.1); background: #333; }
  .edit-icon-btn { position: absolute; top: 10px; left: 10px; width: 32px; height: 32px; border-radius: 50%; background: rgba(255, 255, 255, 0.95); border: 0; box-shadow: 0 2px 8px rgba(0,0,0,0.2); display: flex; align-items: center; justify-content: center; cursor: pointer; opacity: 0; transform: scale(0.9); transition: all 0.2s ease; z-index: 10; color: #444; font-size: 14px; }
  .photo-card:hover .edit-icon-btn { opacity: 1; transform: scale(1); }
  .edit-icon-btn:hover { background: #3b82f6; color: #fff; }

  /* Editor View */
  #editorView { position: fixed; inset: 0; background: #fff; z-index: 200; display: none; flex-direction: column; }
  #editorView.active { display: flex; }
  .editor-header { padding: 16px 24px; border-bottom: 1px solid #eee; display: flex; justify-content: space-between; align-items: center; background: #fff; }
  .editor-main { flex: 1; display: flex; overflow: hidden; }
  .editor-canvas-area { flex: 1; background: #f8fafc; display: flex; align-items: center; justify-content: center; padding: 20px; position: relative; }
  .editor-canvas-area img { max-width: 100%; max-height: 100%; box-shadow: 0 10px 40px rgba(0,0,0,0.15); transition: filter 0.2s ease; }
  .editor-controls { width: 320px; background: #fff; border-left: 1px solid #eee; overflow-y: auto; padding: 20px; }
  .control-group { margin-bottom: 24px; }
  .control-group h5 { margin: 0 0 12px 0; font-size: 13px; color: #94a3b8; text-transform: uppercase; letter-spacing: 0.5px; }
  .slider-row { display: flex; align-items: center; margin-bottom: 12px; }
  .slider-label { width: 80px; font-size: 13px; color: #475569; font-weight: 500; }
  .slider-input { flex: 1; margin: 0 10px; cursor: pointer; }
  .slider-value { width: 30px; font-size: 12px; color: #64748b; text-align: right; }
  
  /* AI Caption Area in Editor */
  .ai-caption-box { margin-top: 20px; padding: 16px; background: #fdf2f8; border: 1px solid #fbcfe8; border-radius: 12px; }
  .ai-caption-result { width: 100%; height: 80px; padding: 8px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb; font-size: 13px; color: #374151; resize: vertical; }
  .loading-dots:after { content: ' .'; animation: dots 1s steps(5, end) infinite; }
  @keyframes dots { 0%, 20% { content: ' .'; } 40% { content: ' ..'; } 60% { content: ' ...'; } 100% { content: ''; } }

  /* Scanner View */
  #scannerView { display: none; min-height: 100vh; background: #f8fafc; flex-direction: column; }
  .scanner-card { background: white; max-width: 500px; width: 90%; margin: 40px auto; padding: 24px; border-radius: 20px; box-shadow: 0 10px 30px rgba(0,0,0,0.08); text-align: center; }
  #reader { width: 100%; border-radius: 12px; overflow: hidden; margin-bottom: 20px; background: #000; }
  .scan-result-box { margin-top: 16px; padding: 12px; background: #ecfdf5; border: 1px solid #a7f3d0; border-radius: 8px; color: #065f46; word-break: break-all; display: none; }
  
  .status{margin-top:8px;font-size:13px;color:var(--muted);}
  .progress{margin-top:8px;background:#f3f4f6;border-radius:8px;padding:8px;font-size:13px;color:#111;}
  .progress-item{display:flex;justify-content:space-between;gap:12px;padding:6px 8px;border-radius:8px;background:#fff;margin-bottom:6px;align-items:center;}
  .progress-item .bar{flex:1;height:10px;background:#eee;border-radius:6px;margin:0 10px;overflow:hidden;}
  .progress-item .bar > i{display:block;height:100%;background:var(--accent);width:0%;}
</style>
</head>
<body>

<!-- LOGIN VIEW -->
<div id="loginView">
  <div class="login-card">
    <div class="login-cover"></div>
    <div class="login-body">
      <h2 class="login-title">Notto.Studio</h2>
      <p class="login-subtitle">ระบบจัดการรูปภาพและสร้าง QR Code</p>
      
      <form id="loginForm" onsubmit="event.preventDefault(); handleLogin();">
        <div style="text-align:left; margin-bottom:12px;">
            <input type="text" id="usernameInput" class="login-input" placeholder="User" required>
        </div>
        <div style="text-align:left; margin-bottom:24px;">
            <input type="password" id="passwordInput" class="login-input" placeholder="Password" required>
        </div>
        <button type="submit" class="btn" style="width:100%; padding:14px; font-size:16px;">เข้าสู่ระบบ</button>
      </form>
    </div>
  </div>
</div>

<!-- EDITOR VIEW -->
<div id="editorView">
  <div class="editor-header">
    <div style="font-weight:700; font-size:18px; color:#0f172a;">Photo Editor</div>
    <div style="display:flex; gap:10px;">
      <button class="btn ghost" onclick="closeEditor()">ยกเลิก</button>
      <button class="btn blue" onclick="applyToCurrent()">✅ รูปเดียว</button>
      <button class="btn dark" onclick="applyToAll()">✅✅ ทั้งหมด</button>
    </div>
  </div>
  <div class="editor-main">
    <div class="editor-canvas-area">
      <img id="editorPreviewImg" src="" alt="Preview">
    </div>
    <div class="editor-controls">
      <!-- AI CAPTION SECTION -->
      <div class="ai-caption-box">
         <h5 style="margin:0 0 8px 0; color:#db2777; display:flex; align-items:center; gap:6px;">✨ AI Magic Caption</h5>
         <p style="font-size:12px; color:#666; margin-bottom:12px;">สร้างคำบรรยายรูปภาพอัตโนมัติจากข้อมูลงาน</p>
         <button class="btn magic" id="generateCaptionBtn" onclick="generateAICaption()" style="width:100%">🪄 สร้างคำบรรยาย (Generate)</button>
         <div id="aiLoading" class="small" style="display:none; color:#db2777; margin-top:8px;">กำลังคิดคำคม<span class="loading-dots"></span></div>
         <textarea id="aiCaptionResult" class="ai-caption-result" placeholder="ผลลัพธ์จะปรากฏที่นี่..."></textarea>
         <button class="btn ghost" onclick="copyCaption()" style="width:100%; margin-top:4px; font-size:12px;">คัดลอกข้อความ</button>
      </div>
      <hr style="border-top:1px dashed #eee; margin:20px 0;">
      <!-- Light -->
      <div class="control-group">
        <h5>Light</h5>
        <div class="slider-row"><span class="slider-label">Exposure</span><input type="range" class="slider-input" min="50" max="150" value="100" id="sl_exposure" oninput="updateEditor()"><span class="slider-value" id="val_exposure">100</span></div>
        <div class="slider-row"><span class="slider-label">Contrast</span><input type="range" class="slider-input" min="50" max="150" value="100" id="sl_contrast" oninput="updateEditor()"><span class="slider-value" id="val_contrast">100</span></div>
        <div class="slider-row"><span class="slider-label">Highlights</span><input type="range" class="slider-input" min="80" max="120" value="100" id="sl_highlights" oninput="updateEditor()"><span class="slider-value" id="val_highlights">100</span></div>
        <div class="slider-row"><span class="slider-label">Shadows</span><input type="range" class="slider-input" min="80" max="120" value="100" id="sl_shadows" oninput="updateEditor()"><span class="slider-value" id="val_shadows">100</span></div>
        <div class="slider-row"><span class="slider-label">Whites</span><input type="range" class="slider-input" min="90" max="110" value="100" id="sl_whites" oninput="updateEditor()"><span class="slider-value" id="val_whites">100</span></div>
        <div class="slider-row"><span class="slider-label">Blacks</span><input type="range" class="slider-input" min="90" max="110" value="100" id="sl_blacks" oninput="updateEditor()"><span class="slider-value" id="val_blacks">100</span></div>
      </div>
      <!-- Color -->
      <div class="control-group">
        <h5>Color</h5>
        <div class="slider-row"><span class="slider-label">Temp</span><input type="range" class="slider-input" min="0" max="50" value="0" id="sl_temp" oninput="updateEditor()"><span class="slider-value" id="val_temp">0</span></div>
        <div class="slider-row"><span class="slider-label">Tint</span><input type="range" class="slider-input" min="-20" max="20" value="0" id="sl_tint" oninput="updateEditor()"><span class="slider-value" id="val_tint">0</span></div>
        <div class="slider-row"><span class="slider-label">Vibrance</span><input type="range" class="slider-input" min="0" max="200" value="100" id="sl_vibrance" oninput="updateEditor()"><span class="slider-value" id="val_vibrance">100</span></div>
        <div class="slider-row"><span class="slider-label">Saturation</span><input type="range" class="slider-input" min="0" max="200" value="100" id="sl_saturation" oninput="updateEditor()"><span class="slider-value" id="val_saturation">100</span></div>
      </div>
      <!-- Effects -->
      <div class="control-group">
        <h5>Effects</h5>
        <div class="slider-row"><span class="slider-label">Texture</span><input type="range" class="slider-input" min="0" max="5" value="0" id="sl_texture" oninput="updateEditor()"><span class="slider-value" id="val_texture">0</span></div>
        <div class="slider-row"><span class="slider-label">Clarity</span><input type="range" class="slider-input" min="100" max="150" value="100" id="sl_clarity" oninput="updateEditor()"><span class="slider-value" id="val_clarity">0</span></div>
        <div class="slider-row"><span class="slider-label">Dehaze</span><input type="range" class="slider-input" min="100" max="130" value="100" id="sl_dehaze" oninput="updateEditor()"><span class="slider-value" id="val_dehaze">0</span></div>
      </div>
      <button class="btn ghost" style="width:100%" onclick="resetEditor()">รีเซ็ตค่าทั้งหมด</button>
    </div>
  </div>
</div>

<!-- SCANNER VIEW -->
<div id="scannerView">
  <header style="justify-content:center;">
    <h1 style="font-size:20px;">QR Scanner</h1>
  </header>
  <div class="scanner-card">
    <div style="margin-bottom:20px; color:var(--muted);">สแกน QR Code ของแขกเพื่อตรวจสอบลิงก์</div>
    <div id="reader"></div>
    <div id="scanResult" class="scan-result-box"></div>
    <div style="display:flex; gap:10px; margin-top:20px; flex-direction:column;">
      <button class="btn blue" id="startScanBtn" onclick="startScanner()">📷 เปิดกล้องสแกน</button>
      <button class="btn ghost" id="stopScanBtn" style="display:none; color:#ef4444; border-color:#ef4444;" onclick="stopScanner()">⏹ หยุดกล้อง</button>
      <hr style="width:100%; border-top:1px solid #eee; margin:10px 0;">
      <button class="btn dark" onclick="goToAdmin()">เข้าสู่หน้าจัดการ (Admin Dashboard) &rarr;</button>
    </div>
  </div>
</div>

<!-- ADMIN VIEW CONTAINER -->
<div id="adminView" style="display:none;">
  <header>
    <div>
      <h1>Notto.Studio Admin</h1>
      <div class="small">ตั้งค่าข้อมูลงาน และลิงก์รูปภาพ</div>
    </div>
    <div style="display:flex; gap:10px;">
      <button class="btn ghost" id="shareQrBtn" style="display:flex;align-items:center;gap:6px;">
        <span style="font-size:18px;">📱</span> สร้าง QR Code
      </button>
      <button class="btn dark" id="toGuestModeBtn" style="display:flex;align-items:center;gap:6px;">
        <span style="font-size:18px;">📺</span> เปิดหน้าจอแขก
      </button>
    </div>
  </header>

  <div class="container">
    <div class="layout">
      <!-- Left Column: Controls -->
      <div class="card left">
        <div class="controls">
          <h4 style="margin:0 0 10px 0; color:#334155;">📂 เลือกแหล่งที่มาของรูปภาพ</h4>
          <div class="source-toggle">
            <button class="btn active" id="btnSourceLocal" onclick="setSource('local')">💻 คอมพิวเตอร์</button>
            <button class="btn" id="btnSourceDrive" onclick="setSource('drive')">☁️ Google Drive</button>
          </div>

          <!-- SECTION: LOCAL / COMPUTER -->
          <div id="sectionLocal">
            <div style="margin-bottom:12px; padding:12px; background:#ecfdf5; border:1px dashed #10b981; border-radius:10px;">
                <div style="font-weight:600; font-size:14px; color:#047857; margin-bottom:6px;">🚀 อัปโหลดด่วน (Auto Upload)</div>
                <div style="display:flex; gap:6px;">
                    <button class="btn green" id="autoUploadFolderBtn" style="flex:1;">📂 โฟลเดอร์</button>
                    <button class="btn green" id="autoUploadFilesBtn" style="flex:1;">📄 ไฟล์ภาพ</button>
                </div>
                <!-- Inputs hidden -->
                <input type="file" id="autoUploadFolderInput" webkitdirectory directory multiple style="display:none">
                <input type="file" id="autoUploadFilesInput" multiple accept="image/*" style="display:none">
                <div class="small" style="color:#059669; margin-top:4px;">*ระบบจะเตรียมอัปโหลดทันที (จำลอง)</div>
            </div>
            
            <label class="small">หรือ เลือกโฟลเดอร์แบบ Manual</label>
            <input type="file" id="folderInput" webkitdirectory directory multiple>
            <div style="display:flex;gap:8px;align-items:center;">
                <input type="checkbox" id="autoUploadCheckbox" checked>
                <label for="autoUploadCheckbox" class="small">Auto upload</label>
            </div>
            <div style="display:flex;gap:8px;align-items:center;margin-top:6px;">
                <label class="small">Concurrent:</label>
                <input id="concurrencyInput" type="number" min="1" max="10" value="3" style="width:50px;padding:4px;border-radius:6px;border:1px solid #ddd;">
            </div>
            <div class="small">รูปเดี่ยว</div>
            <div style="display:flex;gap:8px;">
                <input type="file" id="fileSingle" accept="image/*" style="flex:1">
                <button class="btn ghost" id="addSingleBtn">เพิ่ม</button>
            </div>
            <hr>
            <div class="small">รายการโฟลเดอร์</div>
            <div class="folder-list" id="folderList"><div class="small">ยังไม่เลือกโฟลเดอร์</div></div>
            <div style="display:flex;gap:8px;margin-top:10px;">
                <button class="btn" id="uploadFolderBtn">อัปโหลดทั้งหมด</button>
                <button class="btn ghost" id="cancelAllBtn" style="background:#ef4444;color:#fff;border:0;">ยกเลิก</button>
            </div>
            <div class="status" id="status">สถานะ: พร้อม</div>
            <div class="progress" id="progressBox" style="display:none;"></div>
          </div>

          <!-- SECTION: GOOGLE DRIVE -->
          <div id="sectionDrive" style="display:none;">
            <div class="style-box" style="background:#f0f9ff; border-color:#bae6fd;">
                <h4>☁️ ตั้งค่า Google Drive Link</h4>
                <div class="input-group">
                    <label>ลิงก์ Google Drive Folder</label>
                    <input type="text" id="driveUrlInput" class="input-control" 
                        value="https://drive.google.com/drive/folders/1SQ9rlFwYWvGCj9vFjikNVh0sZzBOM5n8?usp=sharing"
                        placeholder="วางลิงก์ Google Drive ที่นี่">
                    <div class="small" style="color:#0369a1; margin-top:4px;">*รูปทั้งหมดจะดึงมาจากลิงก์นี้เมื่อแขกสแกน</div>
                </div>
            </div>
            <div style="padding:20px; background:#fff; border-radius:12px; text-align:center; color:#64748b;">
                <p>ในโหมดนี้ ระบบจะไม่เก็บรูปไว้บน Server<br>แต่จะพาแขกไปยัง Google Drive โดยตรง</p>
                <p style="font-size:12px;">(เหมาะสำหรับรูปจำนวนมาก หรือไฟล์ความละเอียดสูง)</p>
            </div>
          </div>

          <hr>

          <!-- Guest Customization Section (UPDATED) -->
          <div class="style-box">
            <h4>🎨 ตกแต่งหน้าจอแขก</h4>
            
            <div style="display:flex; gap:10px;">
                <div style="flex:1" class="input-group">
                    <label>ชื่องาน (Event Title)</label>
                    <input type="text" id="eventTitleInput" class="input-control" value="SAVE THE MEMORY">
                </div>
                <div style="width:100px" class="input-group">
                    <label>ขนาดตัวอักษร</label>
                    <input type="range" id="titleSizeInput" min="1.5" max="4" step="0.1" value="2.2" style="width:100%;">
                </div>
            </div>
            
            <div style="display:flex; gap:10px; margin-bottom:12px;">
                 <div style="width:50%" class="input-group">
                    <label>สีธีม (Theme)</label>
                    <input type="color" id="themeColorInput" value="#c49a53" style="width:100%; height:36px; border:none; padding:0; cursor:pointer; background:none;">
                </div>
                <div style="width:50%" class="input-group">
                    <label>สีตัวอักษร (Font)</label>
                    <input type="color" id="titleColorInput" value="#0f172a" style="width:100%; height:36px; border:none; padding:0; cursor:pointer; background:none;">
                </div>
            </div>

            <div class="input-group">
                <label>ชื่อ บ่าว-สาว / เจ้าภาพ</label>
                <input type="text" id="eventHostsInput" class="input-control" placeholder="เช่น Punn & Bow">
            </div>
            
            <div style="display:flex; gap:10px;">
                <div style="flex:1" class="input-group">
                    <label>วันที่</label>
                    <input type="text" id="eventDateInput" class="input-control" placeholder="12 ธ.ค. 2568">
                </div>
                <div style="flex:1" class="input-group">
                    <label>สถานที่</label>
                    <input type="text" id="eventLocationInput" class="input-control" placeholder="โรงแรม...">
                </div>
            </div>
            
            <div class="input-group">
                <label>เครดิตช่างภาพ (Watermark Text)</label>
                <input type="text" id="watermarkInput" class="input-control" placeholder="เช่น Photo by Punn">
            </div>

            <hr style="border-top:1px dashed #fcd34d; margin:15px 0;">
            <div style="margin-bottom:8px; font-weight:600; font-size:13px; color:#92400e;">🖼️ รูปปก (Cover Images)</div>
            
            <div class="input-group">
                <label>รูปปกแนวนอน (Desktop/Landscape)</label>
                <div style="display:flex; gap:6px;">
                    <input type="file" id="coverImgHInput" accept="image/*" class="input-control" style="font-size:11px;">
                    <button class="btn ghost" id="removeCoverHBtn" style="padding:4px 8px; font-size:12px;">ลบ</button>
                </div>
            </div>
            <div class="input-group">
                <label>รูปปกแนวตั้ง (Mobile/Portrait)</label>
                <div style="display:flex; gap:6px;">
                    <input type="file" id="coverImgVInput" accept="image/*" class="input-control" style="font-size:11px;">
                    <button class="btn ghost" id="removeCoverVBtn" style="padding:4px 8px; font-size:12px;">ลบ</button>
                </div>
            </div>
            
            <div class="input-group">
                <label>ปรับความสูงรูปปก (ประมาณ 4 นิ้ว ~ 380px)</label>
                <input type="range" id="coverHeightInput" min="150" max="600" value="220" style="width:100%;">
                <div class="small" style="text-align:right; color:#666;" id="coverHeightVal">220px</div>
            </div>

            <button class="btn dark" id="previewGuestBtn" style="width:100%; margin-top:4px;">👁️ แสดงตัวอย่างหน้าจอแขก</button>
          </div>

        </div>
      </div>

      <!-- Right Column: Preview/Instruction -->
      <div class="card right">
        <!-- Face Search Section -->
        <div id="faceSearchWrapper">
            <div class="face-search-box">
                <h4><span style="font-size:18px">☺</span> ค้นหาจากใบหน้า (Local Mode)</h4>
                <div class="small" id="modelStatus" style="color:#f59e0b; margin-bottom:8px;">กำลังโหลด AI Model...</div>
                <div class="face-preview" id="facePreviewContainer">
                <span class="small" style="color:#888">รูปต้นแบบ</span>
                <img id="refFaceImg" style="display:none">
                <video id="faceVideo" autoplay muted style="display:none"></video>
                </div>
                <div style="display:grid; grid-template-columns: 1fr 1fr; gap:6px;">
                <button class="btn blue" id="openCamBtn" onclick="startCamera()">📷 กล้อง</button>
                <button class="btn ghost" id="uploadFaceBtn" onclick="document.getElementById('faceInput').click()">📂 อัปรูป</button>
                <input type="file" id="faceInput" accept="image/*" style="display:none">
                </div>
                <div id="camControls" style="display:none; margin-top:6px;">
                <button class="btn" id="captureBtn" style="width:100%; background:#ef4444;" onclick="captureFace()">ถ่ายรูป</button>
                </div>
                <div id="searchControls" style="display:none; margin-top:8px;">
                <button class="btn" id="startSearchBtn" style="width:100%;">🔍 เริ่มค้นหา</button>
                <button class="btn ghost" id="resetSearchBtn" style="width:100%; margin-top:4px;">ล้างผล</button>
                </div>
            </div>
            <div class="topbar" style="margin-top:10px;">
                <div>
                    <strong id="currentFolderLabel">Gallery ทั้งหมด</strong><br>
                    <span class="small" id="countLabel">รูปทั้งหมด: 0</span>
                </div>
                <div>
                    <button class="btn ghost" id="reloadCloudBtn" onclick="loadAdminPhotos()">↻ Cloud Gallery</button>
                    <button class="btn ghost" id="clearBtn" onclick="clearAllData()">ล้าง</button>
                </div>
            </div>
            <div class="gallery-grid" id="galleryGrid"></div>
        </div>

        <!-- Drive Mode Instruction -->
        <div id="driveModeInstruction" style="display:none; text-align:center; padding:40px; color:#64748b;">
            <div style="font-size:60px; margin-bottom:16px;">☁️</div>
            <h3 style="margin:0 0 8px 0; color:#334155;">คุณกำลังอยู่ในโหมด Google Drive</h3>
            <p>ในโหมดนี้ รูปภาพจะแสดงผ่าน Google Drive เท่านั้น<br>ระบบค้นหาใบหน้าและ Gallery จะถูกปิดใช้งาน</p>
            <div style="margin-top:30px; padding:20px; background:#f8fafc; border-radius:12px;">
                <strong>ลิงก์ปัจจุบัน:</strong><br>
                <span id="currentDriveLinkDisplay" style="word-break:break-all; font-size:13px; color:var(--accent);">รอการระบุ...</span>
            </div>
        </div>
      </div>
    </div>
  </div>
</div>
<!-- END ADMIN VIEW -->

<!-- GUEST VIEW CONTAINER -->
<div id="guestView">
  <div class="guest-content-wrapper">
      
      <!-- QR Code moved to Top -->
      <div class="guest-header">
        <div style="text-align:center;">
            <div class="guest-qr-container">
              <div id="guestQrCode"></div>
              <div style="font-size:12px; color:#999; margin-top:4px;">สแกนเพื่อส่งต่อ</div>
            </div>
        </div>

        <h1 id="guestEventTitleDisplay">SAVE THE MEMORY</h1>
        
        <div class="guest-info">
            <h2 id="guestEventHostsDisplay"></h2>
            <p>
                <span id="guestEventDateDisplay"></span> 
                <span id="guestEventLocationSeparator" style="display:none">•</span> 
                <span id="guestEventLocationDisplay"></span>
            </p>
        </div>
      </div>

      <!-- Cover Image (Responsive & Adjustable Height) -->
      <div class="guest-cover" id="guestCoverImg"></div>

      <!-- Drive Link Card -->
      <div class="drive-link-card" id="guestDriveCard">
        <div style="text-align:center; margin-bottom:20px;">
            <img src="https://upload.wikimedia.org/wikipedia/commons/d/da/Google_Drive_logo.png" style="width:64px; height:64px; margin-bottom:12px;">
            <h3 style="margin:0; color:#333;">อัลบั้มรูปภาพออนไลน์</h3>
            <p style="color:#666; font-size:14px; margin-top:4px;">รูปภาพทั้งหมดถูกจัดเก็บไว้บน Google Drive</p>
        </div>
        <a id="guestDriveBtn" href="#" target="_blank" class="drive-btn">📂 เปิดอัลบั้มรูปใน Google Drive</a>
        <p style="text-align:center; font-size:12px; color:#999; margin-top:16px;">กดปุ่มด้านบนเพื่อดูและดาวน์โหลดรูปภาพทั้งหมด</p>
      </div>

      <!-- Gallery Grid -->
      <div class="guest-gallery-container" id="guestLocalGalleryContainer">
        <h3 style="border-bottom:1px solid #eee; padding-bottom:10px; color:#334155; margin-bottom:20px;">รูปภาพทั้งหมด (Gallery)</h3>
        <div class="gallery-grid" id="guestGalleryGrid">
          <!-- Gallery content -->
        </div>
      </div>
  </div>
  
  <button class="back-home-btn" id="backToAdminTopBtn"><span style="font-size:1.2rem;">🏠</span> กลับหน้าหลัก</button>
  <button class="exit-btn" id="exitGuestModeBtn">กลับสู่โหมด Admin</button>
  <div class="guest-watermark" id="guestWatermarkDisplay"></div>
</div>

<!-- QR Code Modal (Admin Only) -->
<div class="lightbox" id="qrModal" onclick="hideQr()">
  <div class="qr-content" onclick="event.stopPropagation()">
    <h3>QR Code สำหรับแขก</h3>
    <div id="qrcode" style="display:flex; justify-content:center; margin:24px 0;"></div>
    <p class="small" style="color:#666; margin-bottom:20px;">เมื่อสแกน แขกจะเข้าสู่หน้า Guest View</p>
    <button class="btn" style="width:100%" onclick="hideQr()">ปิดหน้าต่าง</button>
  </div>
</div>

<div class="lightbox" id="lightbox" onclick="hideLightbox()"><img id="lightboxImg" src=""></div>

<script type="module">
  // SINGLE MODULE SCRIPT TO FIX SCOPE ISSUES
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
  import { getStorage, ref as sRef, uploadBytesResumable, getDownloadURL } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-storage.js";
  import { getFirestore, collection, addDoc, getDocs, query, orderBy } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";

  // --- CONFIG ---
  const firebaseConfig = { apiKey: "API_KEY", authDomain: "project.firebaseapp.com", projectId: "project", storageBucket: "project.appspot.com", messagingSenderId: "sender", appId: "app" };
  const app = initializeApp(firebaseConfig);
  const apiKey = ""; 
  
  const mockCloudPhotos = [
      { name: 'Wedding 01', url: 'https://images.unsplash.com/photo-1519741497674-611481863552?q=80&w=600&auto=format&fit=crop' },
      { name: 'Wedding 02', url: 'https://images.unsplash.com/photo-1511285560982-1351cdeb9821?q=80&w=600&auto=format&fit=crop' },
      { name: 'Wedding 03', url: 'https://images.unsplash.com/photo-1515934751635-c81c6bc9a2d8?q=80&w=600&auto=format&fit=crop' }
  ];

  let folders = {};
  let currentFolder = null;
  let activeUploadTasks = new Map();
  let cancelRequested = false;
  let currentDriveUrl = "https://drive.google.com/drive/folders/1SQ9rlFwYWvGCj9vFjikNVh0sZzBOM5n8?usp=sharing";
  let uploadSource = 'local';
  let editSettings = { exposure: 100, contrast: 100, highlights: 100, shadows: 100, whites: 100, blacks: 100, temp: 0, tint: 0, vibrance: 100, saturation: 100, texture: 0, clarity: 100, dehaze: 100 };
  let currentEditImg = null;
  let html5QrcodeScanner = null;

  // --- GLOBAL HELPERS (Attach to window for HTML access) ---
  window.handleLogin = () => {
    const user = document.getElementById('usernameInput').value;
    const pass = document.getElementById('passwordInput').value;
    if (user === "11111" && pass === "00000") {
        document.getElementById('loginView').style.display = 'none';
        document.getElementById('scannerView').style.display = 'flex';
    } else { alert("รหัสผ่านไม่ถูกต้อง"); }
  };
  
  // -- Auto Guest --
  (function autoGuestHandler(){
      try {
        const params = new URLSearchParams(window.location.search);
        // ถ้ามีโหมด guest ให้โชว์ guest view ทันที
        if (params.get('guest') === '1' || params.get('mode') === 'guest' || params.get('quickscan') === '1') {
          // hide login/admin
          const lv = document.getElementById('loginView');
          const av = document.getElementById('adminView');
          const sc = document.getElementById('scannerView');
          const gv = document.getElementById('guestView');
          if (lv) lv.style.display = 'none';
          if (av) av.style.display = 'none';
          if (sc) sc.style.display = 'none';
          if (gv) gv.classList.add('active');

          // ถ้ามีพาราม drive ให้เซ็ตลิงก์
          const drive = params.get('drive');
          if (drive) {
            try {
              const decoded = decodeURIComponent(drive);
              const gbtn = document.getElementById('guestDriveBtn');
              if (gbtn) { gbtn.href = decoded; document.getElementById('guestDriveCard').classList.add('visible'); document.getElementById('guestLocalGalleryContainer').style.display = 'none'; }
            } catch(e){}
          } else {
             // Local mode
             document.getElementById('guestLocalGalleryContainer').style.display = 'block';
             document.getElementById('guestDriveCard').classList.remove('visible');
             // Load Mock/Cloud
             window.loadGuestPhotosFromCloud();
          }

          // ซ่อนปุ่ม Admin
          const backBtn = document.getElementById('backToAdminTopBtn');
          const exitBtn = document.getElementById('exitGuestModeBtn');
          if (backBtn) backBtn.style.display='none';
          if (exitBtn) exitBtn.style.display='none';
          
          new QRCode(document.getElementById('guestQrCode'), { text: window.location.href, width: 120, height: 120 });
        }
      } catch(e){ console.warn("autoGuestHandler error", e); }
  })();

  window.setSource = (source) => {
      uploadSource = source;
      const btnLocal = document.getElementById('btnSourceLocal');
      const btnDrive = document.getElementById('btnSourceDrive');
      const secLocal = document.getElementById('sectionLocal');
      const secDrive = document.getElementById('sectionDrive');
      const faceWrapper = document.getElementById('faceSearchWrapper');
      const driveInst = document.getElementById('driveModeInstruction');

      if (source === 'local') {
          btnLocal.classList.add('active'); btnDrive.classList.remove('active');
          secLocal.style.display = 'block'; secDrive.style.display = 'none';
          faceWrapper.style.display = 'block'; driveInst.style.display = 'none';
      } else {
          btnDrive.classList.add('active'); btnLocal.classList.remove('active');
          secDrive.style.display = 'block'; secLocal.style.display = 'none';
          faceWrapper.style.display = 'none'; driveInst.style.display = 'block';
      }
  };

  window.goToAdmin = () => {
      if (html5QrcodeScanner) { html5QrcodeScanner.stop().catch(console.error); html5QrcodeScanner = null; }
      document.getElementById('scannerView').style.display = 'none';
      document.getElementById('adminView').style.display = 'block';
      window.setSource('local');
      window.loadAdminPhotos(); // Load initial photos
      setTimeout(() => { if(typeof map !== 'undefined') map.invalidateSize(); }, 300);
  };

  // LOAD ADMIN PHOTOS (Mock Cloud)
  window.loadAdminPhotos = () => {
      const grid = document.getElementById('galleryGrid');
      grid.innerHTML = '';
      
      let filesToShow = [];
      Object.values(folders).forEach(arr => filesToShow = filesToShow.concat(arr));
      
      if (filesToShow.length > 0) {
          document.getElementById('currentFolderLabel').innerText = "Local Staging (" + filesToShow.length + ")";
          filesToShow.forEach(file => {
             const reader = new FileReader();
             const card = document.createElement('div'); card.className = 'photo-card photo-card-image-wrap';
             reader.onload = (ev) => {
                 card.innerHTML = `
                  <div style="position:relative; width:100%; height:100%;">
                    <img loading="lazy" src="${ev.target.result}" class="editable-img" onerror="this.src='https://placehold.co/300x200?text=Error';">
                    <button class="download-icon-btn" onclick="event.stopPropagation(); downloadFile('${ev.target.result}', '${file.name}')">⬇</button>
                    <button class="edit-icon-btn" onclick="event.stopPropagation(); openEditor('${ev.target.result}', '${file.name}', this.parentElement.querySelector('.editable-img'))">🎨</button>
                  </div>`;
             };
             reader.readAsDataURL(file);
             grid.appendChild(card);
          });
      } else {
          document.getElementById('currentFolderLabel').innerText = "Cloud Gallery (" + mockCloudPhotos.length + ")";
          mockCloudPhotos.forEach(photo => {
             const card = document.createElement('div'); card.className = 'photo-card photo-card-image-wrap';
             card.innerHTML = `
              <div style="position:relative; width:100%; height:100%;">
                <img loading="lazy" src="${photo.url}" class="editable-img" onerror="this.src='https://placehold.co/300x200?text=Error';">
                <button class="download-icon-btn" onclick="event.stopPropagation(); downloadFile('${photo.url}', '${photo.name}.jpg')">⬇</button>
                <button class="edit-icon-btn" onclick="event.stopPropagation(); openEditor('${photo.url}', '${photo.name}', this.parentElement.querySelector('.editable-img'))">🎨</button>
              </div>`;
             grid.appendChild(card);
          });
      }
      document.getElementById('countLabel').innerText = 'รูปทั้งหมด: ' + (filesToShow.length || mockCloudPhotos.length);
  };
  
  // LOAD GUEST PHOTOS (Mock)
  window.loadGuestPhotosFromCloud = () => {
      const gallery = document.getElementById('guestGalleryGrid');
      gallery.innerHTML = '';
      mockCloudPhotos.forEach(photo => {
         const card = document.createElement('div'); card.className = 'photo-card photo-card-image-wrap';
         card.innerHTML = `
           <div style="position:relative; width:100%; height:100%;">
             <img src="${photo.url}" onerror="this.src='https://placehold.co/300x200?text=Error';">
             <button class="download-icon-btn" onclick="downloadFile('${photo.url}','${photo.name}.jpg')">⬇</button>
           </div>`;
         gallery.appendChild(card);
      });
  };

  document.getElementById('reloadCloudBtn').onclick = window.loadAdminPhotos;

  window.openEditor = (url, name, imgElement) => {
    currentEditImg = imgElement;
    document.getElementById('editorPreviewImg').src = url;
    document.getElementById('editorView').classList.add('active');
    updateEditorUI();
  };

  window.closeEditor = () => { document.getElementById('editorView').classList.remove('active'); currentEditImg = null; };
  window.updateEditor = () => {
    editSettings.exposure = document.getElementById('sl_exposure').value;
    editSettings.contrast = document.getElementById('sl_contrast').value;
    document.getElementById('editorPreviewImg').style.filter = `brightness(${editSettings.exposure}%) contrast(${editSettings.contrast}%)`;
  };

  window.applyToCurrent = () => window.closeEditor(); // Mock apply
  window.applyToAll = () => { window.closeEditor(); alert("Applied to all"); };
  window.resetEditor = () => { /* reset logic */ };

  window.downloadFile = (url, filename) => {
    const a = document.createElement('a');
    a.href = url;
    a.download = filename;
    document.body.appendChild(a);
    a.click();
    document.body.removeChild(a);
  };
  
  // === GEMINI API INTEGRATION ===
  window.generateAICaption = async () => {
      const btn = document.getElementById('generateCaptionBtn');
      const loader = document.getElementById('aiLoading');
      const resultArea = document.getElementById('aiCaptionResult');
      
      const eventTitle = document.getElementById('eventTitleInput').value;
      const hosts = document.getElementById('eventHostsInput').value;
      const location = document.getElementById('eventLocationInput').value;
      
      if(!eventTitle) { alert("กรุณากรอกชื่องานก่อนครับ"); return; }
      
      btn.disabled = true;
      btn.style.opacity = '0.7';
      loader.style.display = 'block';
      resultArea.value = '';
      
      try {
        const prompt = `Write a heartwarming and fun social media caption in Thai for a photo from the event '${eventTitle}' (Hosts: ${hosts}, Location: ${location}). Include relevant emojis and hashtags.`;
        
        const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ contents: [{ parts: [{ text: prompt }] }] })
        });
        
        const data = await response.json();
        const generatedText = data.candidates?.[0]?.content?.parts?.[0]?.text || "ไม่สามารถสร้างคำบรรยายได้";
        
        resultArea.value = generatedText;
        
      } catch (error) {
          console.error(error);
          resultArea.value = "เกิดข้อผิดพลาดในการเชื่อมต่อ AI";
      } finally {
          btn.disabled = false;
          btn.style.opacity = '1';
          loader.style.display = 'none';
      }
  };
  
  window.copyCaption = () => {
      const copyText = document.getElementById("aiCaptionResult");
      copyText.select();
      document.execCommand("copy");
      alert("คัดลอกคำบรรยายแล้ว!");
  };

  window.showLightbox = (src) => { document.getElementById('lightboxImg').src = src; document.getElementById('lightbox').classList.add('show'); };
  window.hideLightbox = () => document.getElementById('lightbox').classList.remove('show');
  window.hideQr = () => document.getElementById('qrModal').classList.remove('show');

  // --- UPLOAD LOGIC (SIMULATION FIXED) ---
  const progressBox = document.getElementById('progressBox');
  const statusEl = document.getElementById('status');

  function ensureProgressBox() { progressBox.style.display = 'block'; progressBox.innerHTML = ''; }
  function createProgressItem(uid, name) { 
      ensureProgressBox(); 
      const d = document.createElement('div'); d.className = 'progress-item'; d.id='p_'+uid; 
      d.innerHTML=`<div style="max-width:35%">${name}</div><div class="bar"><i style="width:0%"></i></div><div class="small" id="pct_${uid}">0%</div>`; 
      progressBox.appendChild(d); 
  }
  function updateProgressItem(uid, name, pct) { 
      const e=document.getElementById('p_'+uid); 
      if(e){ e.querySelector('.bar>i').style.width=pct+'%'; document.getElementById('pct_'+uid).innerText=pct+'%'; } 
  }
  function setStatus(text, color='') { statusEl.innerText = 'สถานะ: ' + text; statusEl.style.color = color || ''; }

  window.uploadFolders = async (targetFolders) => {
    cancelRequested = false; 
    const fileQueue = [];
    if (!folders) return;
    
    for (const fn of targetFolders) { 
        if(folders[fn]) { (folders[fn]||[]).forEach(f => fileQueue.push({ file: f, folderName: fn })); }
    }
    if (!fileQueue.length) return;
    
    ensureProgressBox();
    fileQueue.slice(0, 5).forEach((item, i) => createProgressItem(i, item.file.name));
    if(fileQueue.length > 5) createProgressItem(999, `...และอีก ${fileQueue.length-5} ไฟล์`);
    
    let completed = 0;
    const total = fileQueue.length;
    
    // SIMULATION INTERVAL
    const interval = setInterval(() => {
        if(cancelRequested || completed >= total) {
            clearInterval(interval);
            if(!cancelRequested) {
                setStatus('อัปโหลดเสร็จสิ้น (จำลอง)', 'green');
                // Mock adding to cloud
                fileQueue.forEach(item => {
                    const reader = new FileReader();
                    reader.onload = (e) => {
                        mockCloudPhotos.unshift({ name: item.file.name, url: e.target.result });
                    };
                    reader.readAsDataURL(item.file);
                });
                setTimeout(() => window.loadAdminPhotos(), 1000); // Reload gallery
            } else setStatus('ยกเลิกแล้ว', 'red');
            
            setTimeout(()=> { if(!cancelRequested) progressBox.style.display='none'; }, 3000);
            return;
        }
        
        for(let i=0; i<Math.min(5, total); i++) {
            updateProgressItem(i, fileQueue[i].file.name, Math.floor(Math.random() * 100));
        }
        
        completed += 1; // Speed up
        setStatus(`กำลังอัปโหลด (จำลอง)... ${Math.min(completed, total)}/${total}`);
    }, 100);
  };

  // --- EVENT LISTENERS ---
  document.getElementById('shareQrBtn').onclick = () => {
    document.getElementById('qrModal').classList.add('show');
    const qrcodeContainer = document.getElementById('qrcode');
    qrcodeContainer.innerHTML = '';
    
    // base URL แบบหน้าเว็บปกติ
    const baseUrl = window.location.origin + window.location.pathname;

    // บังคับให้เป็น guest mode 100%
    let guestUrl = baseUrl + '?guest=1';

    // ถ้าใช้ Google Drive
    if (uploadSource === 'drive') {
        guestUrl += '&drive=' + encodeURIComponent(currentDriveUrl);
    }

    new QRCode(qrcodeContainer, {
        text: guestUrl,
        width: 220,
        height: 220
    });
  };
  // --- Permission helper modal (in-page) ---
  function showPermissionDialogWithOpen(reason) {
    const ua = navigator.userAgent || '';
    const inApp = /Line|FBAN|FBAV|Instagram|FB_IAB|Messenger/i.test(ua);
    let message = `ไม่สามารถเข้าถึงกล้อง: ${reason}\n\n`;
    if (inApp) {
      message += "คุณกำลังเปิดจากแอป (เช่น LINE/Facebook/IG) — แอปพวกนี้มักบล็อกกล้อง\n";
      message += "1) กดเมนู > Open in Browser (เปิดในเบราว์เซอร์)\n";
      message += "2) หรือกดปุ่มด้านล่างเพื่อเปิดหน้านี้ในเบราว์เซอร์โดยตรง\n\n";
    } else {
      message += "โปรดอนุญาตกล้องในการตั้งค่าเบราว์เซอร์ หรือรีเซ็ตการตั้งค่าของไซต์ แล้วรีเฟรช";
    }

    // ใช้ confirm เพื่อให้มีปุ่มให้กด (ง่าย)
    if (confirm(message + "\n\nกด 'OK' เพื่อเปิดหน้านี้ในเบราว์เซอร์ (แท็บใหม่)")) {
      // เปิดตัวเองในเบราว์เซอร์แท็บใหม่พร้อมพาราม quickscan
      const url = window.location.href.split('?')[0] + '?quickscan=1';
      window.open(url, '_blank');
    }
  }

  // --- Improved startScanner with permission handling ---
  window.startScanner = async () => {
    try {
      if (html5QrcodeScanner) {
        console.log("Scanner already running");
        return;
      }

      if (navigator.permissions && navigator.permissions.query) {
        try {
          const status = await navigator.permissions.query({ name: 'camera' });
          if (status.state === 'denied') {
            showPermissionDialogWithOpen("สิทธิ์กล้องถูกปฏิเสธแล้ว (Permissions API)");
            return;
          }
        } catch (permErr) {
          console.warn("Permissions API camera check failed:", permErr);
        }
      }

      html5QrcodeScanner = new Html5Qrcode("reader");

      await html5QrcodeScanner.start(
        { facingMode: "environment" },
        { fps: 10, qrbox: { width: 250, height: 250 } },
        (decodedText) => {
          document.getElementById('scanResult').style.display = 'block';
          document.getElementById('scanResult').innerText = "Found: " + decodedText;
        },
        (errorMsg) => {}
      );

      document.getElementById('startScanBtn').style.display = 'none';
      document.getElementById('stopScanBtn').style.display = 'inline-block';
    } catch (err) {
      console.error("startScanner error:", err);
      showPermissionDialogWithOpen(err && err.name ? err.name : String(err));
    }
  };

  // --- Improved stopScanner (safe) ---
  window.stopScanner = async () => {
      if (html5QrcodeScanner) { await html5QrcodeScanner.stop(); html5QrcodeScanner = null; }
      startScanBtn.style.display = 'inline-block'; stopScanBtn.style.display = 'none';
  };

  // Auto Upload Inputs
  const autoUploadFolderInput = document.getElementById('autoUploadFolderInput');
  const autoUploadFilesInput = document.getElementById('autoUploadFilesInput');
  
  const handleAuto = (e) => {
      const files = Array.from(e.target.files || []);
      if(!files.length) return;
      const fname = "Auto Upload " + new Date().toLocaleTimeString();
      folders[fname] = files;
      // Refresh Folder List Logic (simplified)
      const list = document.getElementById('folderList');
      const el = document.createElement('div'); el.className='folder-item'; 
      el.innerHTML = `<div>${fname}</div><div class="small">${files.length} img</div>`;
      list.appendChild(el);
      
      window.uploadFolders([fname]);
      e.target.value = '';
  };
  
  document.getElementById('autoUploadFolderBtn').onclick = () => autoUploadFolderInput.click();
  document.getElementById('autoUploadFilesBtn').onclick = () => autoUploadFilesInput.click();
  autoUploadFolderInput.onchange = handleAuto;
  autoUploadFilesInput.onchange = handleAuto;

  // Manual Folder Input
  document.getElementById('folderInput').addEventListener('change', handleAuto);
  document.getElementById('uploadFolderBtn').addEventListener('click', () => { if(Object.keys(folders).length) window.uploadFolders(Object.keys(folders)); });
  document.getElementById('cancelAllBtn').addEventListener('click', () => { cancelRequested = true; setStatus('ยกเลิก', 'red'); });

  // Map
  const map = L.map('map').setView([13.736717,100.523186], 6);
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png',{ attribution:'&copy; OSM' }).addTo(map);

  // Check URL Params for Guest Mode on Load
  const urlParams = new URLSearchParams(window.location.search);
  if (urlParams.get('mode') === 'guest') {
      document.getElementById('loginView').style.display = 'none';
      document.getElementById('guestView').classList.add('active');
      document.getElementById('backToAdminTopBtn').style.display = 'none';
      document.getElementById('exitGuestModeBtn').style.display = 'none';
      switchToGuestMode();
  }

  // Internal helpers
  function updateEditorUI() {
    for (const key in editSettings) {
        const el = document.getElementById('val_' + key);
        if (el) el.innerText = editSettings[key];
        const input = document.getElementById('sl_' + key);
        if (input) input.value = editSettings[key];
    }
  }
  function generateFilterString() {
    let brightness = parseInt(editSettings.exposure) + (parseInt(editSettings.highlights) - 100)/5 + (parseInt(editSettings.whites) - 100)/5;
    let contrast = parseInt(editSettings.contrast) + (parseInt(editSettings.clarity) - 100)/4 + (parseInt(editSettings.dehaze) - 100)/4;
    let saturate = parseInt(editSettings.saturation) + (parseInt(editSettings.vibrance) - 100)/2;
    let sepia = editSettings.temp;
    let hue = editSettings.tint;
    let blur = editSettings.texture;
    return `brightness(${brightness}%) contrast(${contrast}%) saturate(${saturate}%) sepia(${sepia}%) hue-rotate(${hue}deg) blur(${blur}px)`;
  }

</script>
</body>
</html>
