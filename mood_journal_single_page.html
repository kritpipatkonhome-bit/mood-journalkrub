<!--
ไฟล์: mood_journal_single_page.html
คำอธิบาย: เว็บหน้าเดียวสำหรับ "บันทึกอารมณ์ 7 ครั้ง" (Single Page App)
เทคโนโลยี: HTML + CSS + JavaScript (Chart.js + EmailJS)

สิ่งที่จะอยู่ในไฟล์นี้:
1) UI ให้กรอกอีเมลก่อนเริ่ม
2) ปุ่มเลือกอิโมจิ 5 ระดับ (ให้คะแนน 5 -> 1)
3) เก็บข้อมูลเป็น array ใน localStorage ตามอีเมลของผู้ใช้
4) เมื่อครบ 7 ครั้ง -> สรุปผลเป็นกราฟแท่ง (Chart.js)
5) ส่งอีเมลสรุปผลไปยังอีเมลที่ผู้ใช้กรอกด้วย EmailJS
6) ล้างข้อมูลสำหรับรอบถัดไปหลังส่งอีเมลสำเร็จ

*** อ่านส่วน "SETUP EmailJS" ด้านล่างในเอกสารนี้ก่อนทดลองใช้งาน ***
-->

<!doctype html>
<html lang="th">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>บันทึกอารมณ์ 7 ครั้ง</title>
  <!-- Chart.js CDN -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <!-- EmailJS SDK CDN -->
  <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
  <style>
    :root{--bg:#f7f9fc;--card:#ffffff;--accent:#4f46e5;--muted:#6b7280}
    *{box-sizing:border-box;font-family:Inter, Roboto, "Noto Sans Thai", system-ui, -apple-system, 'Segoe UI', 'Helvetica Neue', Arial}
    body{margin:0;background:var(--bg);color:#111}
    .wrap{max-width:900px;margin:28px auto;padding:20px}
    .card{background:var(--card);padding:18px;border-radius:12px;box-shadow:0 6px 20px rgba(15,23,42,0.06);}
    h1{margin:0 0 8px 0;font-size:22px}
    p.lead{margin:0 0 12px 0;color:var(--muted)}
    label{display:block;margin-bottom:6px;font-weight:600}
    input[type=email]{width:100%;padding:10px;border-radius:8px;border:1px solid #e6e9ef}
    button{cursor:pointer}

    .row{display:flex;gap:12px;align-items:center}
    .emoji-row{display:flex;gap:10px;flex-wrap:wrap;margin:12px 0}
    .emoji-btn{width:84px;height:84px;border-radius:12px;border:1px solid #e6e9ef;background:#fff;font-size:28px;display:flex;flex-direction:column;align-items:center;justify-content:center;cursor:pointer}
    .emoji-btn.selected{outline:3px solid rgba(79,70,229,0.18);transform:translateY(-4px)}
    .controls{display:flex;gap:10px;margin-top:10px}
    .btn-primary{background:var(--accent);color:#fff;padding:10px 14px;border-radius:10px;border:none}
    .btn-ghost{background:transparent;border:1px solid #ddd;padding:10px 12px;border-radius:10px}
    .muted{color:var(--muted);font-size:13px}

    #moodChart{margin-top:18px}
    #summary{margin-top:12px;padding:12px;border-radius:10px;background:#fbfbff}
    pre{white-space:pre-wrap;word-break:break-word}

    footer{margin-top:18px;color:var(--muted);font-size:13px}

    /* responsive */
    @media (max-width:600px){.emoji-btn{width:64px;height:64px;font-size:22px}}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card">
      <h1>บันทึกอารมณ์ 7 วัน</h1>
      <p class="lead">กรอกอีเมลก่อนเริ่ม → บันทึกอารมณ์ 7 วัน แล้วระบบจะสรุปผลเป็นกราฟแล้วส่งอีเมลสรุปให้</p>

      <!-- SECTION: Email input -->
      <div id="email-section">
        <label for="userEmail">อีเมลของคุณ (ใช้รับสรุปผล)</label>
        <input id="userEmail" type="email" placeholder="you@example.com" />
        <div style="margin-top:10px;display:flex;gap:8px;align-items:center">
          <button id="startBtn" class="btn-primary">เริ่มบันทึก</button>
          <div class="muted">หรือถ้าคุณทดสอบ ให้ใส่อีเมลจริงที่คุณเข้าถึงได้</div>
        </div>
        <div id="emailMsg" class="muted" style="margin-top:8px"></div>
      </div>

      <!-- MAIN APP (ซ่อนก่อนเริ่ม) -->
      <div id="main-app" style="display:none;margin-top:14px">
        <div class="row" style="justify-content:space-between;align-items:center">
          <div>
            <div class="muted">ผู้ใช้:</div>
            <div id="displayEmail" style="font-weight:700"></div>
          </div>
          <div style="text-align:right">
            <div class="muted">ความคืบหน้า</div>
            <div id="progress">บันทึกแล้ว <strong id="count">0</strong> / 7</div>
          </div>
        </div>

        <hr style="margin:12px 0" />

        <label>เลือกอารมณ์ (1 = บึ้ง ... 5 = ยิ้มมาก)</label>
        <div class="emoji-row">
          <button class="emoji-btn" data-score="5">😄<div style="font-size:12px;margin-top:4px">ดีมาก</div></button>
          <button class="emoji-btn" data-score="4">🙂<div style="font-size:12px;margin-top:4px">ดี</div></button>
          <button class="emoji-btn" data-score="3">😐<div style="font-size:12px;margin-top:4px">เฉยๆ</div></button>
          <button class="emoji-btn" data-score="2">🙁<div style="font-size:12px;margin-top:4px">เศร้า</div></button>
          <button class="emoji-btn" data-score="1">😡<div style="font-size:12px;margin-top:4px">บึ้ง</div></button>
        </div>

        <div class="controls">
          <button id="saveBtn" class="btn-primary">บันทึกอารมณ์</button>
          <button id="resetBtn" class="btn-ghost" style="display:none">เริ่มใหม่ / เคลียร์</button>
          <div id="status" class="muted"></div>
        </div>

        <canvas id="moodChart" style="display:none;max-width:100%;height:260px"></canvas>
        <div id="summary" style="display:none"></div>
      </div>

      <footer>
        <strong>หมายเหตุ:</strong> ข้อมูลจะถูกเก็บในเบราว์เซอร์ (localStorage) และจะถูกส่งไปยังบริการ EmailJS เมื่อครบ 7 ครั้ง (หากตั้งค่า EmailJS ไว้)
      </footer>
    </div>

    

  <script>
  // -----------------------------
  // CONFIG: ใส่ค่า EmailJS ของคุณที่นี่
  // -----------------------------
  const EMAILJS_USER_ID = 'YgaXFL--CNWu3M3eU';      // ตัวอย่าง 'user_xxx' หรือ public key
  const EMAILJS_SERVICE_ID = 'service_i6osw67';   // ตัวอย่าง 'service_xxx'
  const EMAILJS_TEMPLATE_ID = 'template_wm4wqep'; // ตัวอย่าง 'template_xxx'
  // -----------------------------

  // อย่าแก้าตรงนี้ถ้าไม่แน่ใจ — ระบบจะแจ้งเตือนให้ใส่ค่า

  // ไม่เรียก init ถ้าค่าเป็น placeholder
  if (EMAILJS_USER_ID && !EMAILJS_USER_ID.includes('YOUR_')) {
    try { emailjs.init(EMAILJS_USER_ID); } catch(e){ console.warn('EmailJS init error', e); }
  }

  // helper selectors
  const $ = id => document.getElementById(id);
  const emailInput = $('userEmail');
  const startBtn = $('startBtn');
  const emailMsg = $('emailMsg');
  const mainApp = $('main-app');
  const displayEmail = $('displayEmail');
  const countEl = $('count');
  const saveBtn = $('saveBtn');
  const resetBtn = $('resetBtn');
  const status = $('status');
  const moodChartEl = $('moodChart');
  const summaryEl = $('summary');

  let selectedScore = null;
  let entries = []; // array of {score, at}
  let currentEmail = null;
  let chart = null;

  function sanitizeEmailKey(email){ return 'mood_journal_' + email.replace(/[^a-z0-9]/gi,'_').toLowerCase(); }

  function loadEntries(email){
    try{
      const raw = localStorage.getItem(sanitizeEmailKey(email));
      if(raw) return JSON.parse(raw);
    }catch(e){ console.error(e); }
    return [];
  }
  function saveEntries(email, arr){ localStorage.setItem(sanitizeEmailKey(email), JSON.stringify(arr)); }
  function clearEntries(email){ localStorage.removeItem(sanitizeEmailKey(email)); }

  function validateEmail(email){ return /\S+@\S+\.\S+/.test(email); }

  startBtn.addEventListener('click', ()=>{
    const v = emailInput.value.trim();
    if(!validateEmail(v)){
      emailMsg.textContent = 'กรุณาใส่อีเมลให้ถูกต้อง เช่น you@example.com';
      return;
    }
    emailMsg.textContent = '';
    currentEmail = v;
    entries = loadEntries(currentEmail) || [];
    displayEmail.textContent = currentEmail;

    // toggle UI
    $('email-section').style.display = 'none';
    mainApp.style.display = 'block';
    updateUI();

    // init emailjs if configured
    if (EMAILJS_USER_ID && !EMAILJS_USER_ID.includes('YOUR_')) {
      try{ emailjs.init(EMAILJS_USER_ID); } catch(err){ console.warn('EmailJS init fail', err); }
    }

    // If there are already 7 entries stored, show summary immediately
    if(entries.length >= 7){
      computeSummary();
    }
  });

  // emoji buttons
  document.querySelectorAll('.emoji-btn').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      document.querySelectorAll('.emoji-btn').forEach(b=>b.classList.remove('selected'));
      btn.classList.add('selected');
      selectedScore = Number(btn.dataset.score);
      status.textContent = 'เลือกอารมณ์: ' + btn.textContent.trim();
    });
  });

  saveBtn.addEventListener('click', ()=>{
    if(!currentEmail){ status.textContent = 'กรุณากรอกอีเมลและกด เริ่มบันทึก ก่อน'; return; }
    if(selectedScore === null){ status.textContent = 'กรุณาเลือกอารมณ์ก่อนกดบันทึก'; return; }
    if(entries.length >= 7){ status.textContent = 'ครบ 7 วันแล้ว โปรดรีเซ็ตหรือดูสรุป'; return; }

    entries.push({score: Number(selectedScore), at: new Date().toISOString()});
    saveEntries(currentEmail, entries);
    // reset selection
    document.querySelectorAll('.emoji-btn').forEach(b=>b.classList.remove('selected'));
    selectedScore = null;
    status.textContent = 'บันทึกเรียบร้อย ✅';
    updateUI();

    if(entries.length === 7){
      computeSummary();
    }
  });

  resetBtn.addEventListener('click', ()=>{
    if(!currentEmail) return;
    if(confirm('ต้องการล้างข้อมูลการบันทึกสำหรับอีเมลนี้ไหม?')){
      clearEntries(currentEmail);
      entries = [];
      updateUI();
      status.textContent = 'ข้อมูลถูกล้างแล้ว';
      summaryEl.style.display='none';
      moodChartEl.style.display='none';
      if(chart){ chart.destroy(); chart=null; }
    }
  });

  function updateUI(){
    countEl.textContent = entries.length;
    saveBtn.disabled = (entries.length >= 7);
    resetBtn.style.display = (entries.length>0)?'inline-block':'none';
    // show simple progress
    if(entries.length>0){
      status.textContent = 'บันทึกล่าสุด: ' + entries[entries.length-1].score + ' (คะแนน)';
    }
  }

  function computeSummary(){
    // counts of scores 5..1
    const counts = {5:0,4:0,3:0,2:0,1:0};
    let total = 0;
    entries.forEach(e=>{ counts[e.score] = (counts[e.score]||0)+1; total += Number(e.score); });
    const totalScore = total; // 7..35
    const label = getLabel(totalScore);
    const message = getMessage(totalScore);

    // prepare chart data (labels: ดีมาก..บึ้ง)
    const chartLabels = ['ดีมาก (5)','ดี (4)','เฉยๆ (3)','เศร้า (2)','บึ้ง (1)'];
    const chartData = [counts[5], counts[4], counts[3], counts[2], counts[1]];

    // show summary text
    summaryEl.style.display = 'block';
    summaryEl.innerHTML = `<strong>สรุปคะแนนรวม:</strong> ${totalScore} / 35<br/><strong>ผล:</strong> ${label}<br/><strong>คำแนะนำ:</strong> ${message}`;

    // render chart
    moodChartEl.style.display = 'block';
    const ctx = moodChartEl.getContext('2d');
    if(chart) chart.destroy();
    chart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: chartLabels,
        datasets: [{
          label: 'จำนวนครั้ง',
          data: chartData,
          // default colors used by Chart.js
          borderWidth: 1
        }]
      },
      options: {
        scales: { y: { beginAtZero:true, precision:0, ticks:{stepSize:1} } },
        plugins: { legend: { display:false } }
      }
    });

    // send email via EmailJS (ถ้าตั้งค่า)
    sendEmail(currentEmail, totalScore, label, message, counts);
  }

  function getLabel(total){
    if(total >= 30) return 'อารมณ์ดีมาก';
    if(total >= 24) return 'อารมณ์ค่อนข้างดี';
    if(total >= 18) return 'อารมณ์ปกติ/เฉยๆ';
    if(total >= 12) return 'อารมณ์ค่อนข้างแย่';
    return 'อารมณ์แย่มาก';
  }

  function getMessage(total){
    if(total >= 30) return 'เยี่ยมเลย! ช่วงนี้ดูอารมณ์ดีมากๆ ขอให้รักษาพลังบวกนี้ไว้นะ!';
    if(total >= 24) return 'วันนี้ดูมีความสุขดีนะ รักษาใจที่สดใสไว้เสมอ!';
    if(total >= 18) return 'ชีวิตมีขึ้นมีลงเป็นธรรมดา ขอให้วันต่อไปสดใสขึ้นอีกหน่อยนะ!';
    if(total >= 12) return 'พักผ่อนให้เพียงพอ แล้วลองทำสิ่งที่ชอบดูนะ เป็นกำลังใจให้นะ ❤️';
    return 'พักผ่อนบ้างน้า เป็นห่วงนะ ขอให้วันต่อไปใจเย็นขึ้นอีกนิดนะ 🌿';
  }

  function formatCounts(counts){
	return Object.entries(counts)
		.map(([score, count]) => `คะแนน ${score} = ${count} ครั้ง`)
		.join('\n');
  }

  function sendEmail(toEmail, totalScore, label, messageText, counts){
    // Template parameters sent to EmailJS
    const templateParams = {
      to_email: toEmail,
      total_score: totalScore,
      label: label,
      message: messageText,
      counts: formatCounts(counts)
    };

    // check placeholder config
    if(!EMAILJS_USER_ID || EMAILJS_USER_ID.includes('YOUR_') || !EMAILJS_SERVICE_ID || EMAILJS_SERVICE_ID.includes('YOUR_') || !EMAILJS_TEMPLATE_ID || EMAILJS_TEMPLATE_ID.includes('YOUR_')){
      // ถ้าไม่ได้ตั้งค่า EmailJS จะแสดงข้อความแนะนำให้ผู้ใช้ใส่ค่า
      status.textContent = 'ยังไม่ได้ตั้งค่า EmailJS — ใส่ค่า EMAILJS_USER_ID / SERVICE_ID / TEMPLATE_ID ในไฟล์นี้ก่อนส่งอีเมล';
      console.warn('EmailJS not configured. Skipping send.');
      return;
    }

    status.textContent = 'กำลังส่งสรุปทางอีเมล...';
    emailjs.send(EMAILJS_SERVICE_ID, EMAILJS_TEMPLATE_ID, templateParams)
      .then(function(response){
        console.log('SUCCESS!', response.status, response.text);
        status.textContent = 'ส่งอีเมลสรุปผลเรียบร้อย ✅';
        // หลังส่งเรียบร้อย ล้างข้อมูลสำหรับรอบถัดไป
        clearEntries(currentEmail);
        resetBtn.style.display = 'none';
      }, function(error){
        console.error('FAILED...', error);
        status.textContent = 'เกิดข้อผิดพลาดในการส่งอีเมล — ตรวจสอบ Console';
      });
  }

  // สำหรับการทดสอบ: ถ้าต้องการลบข้อมูลทั้งหมดของทุกอีเมล ให้เรียก localStorage.clear() ใน Console
  </script>
</body>
</html>
