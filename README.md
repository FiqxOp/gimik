# gimik
<!DOCTYPE html>
<html lang="ms">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
<title>Gimik Perasmian | SK Padang Pekan</title>
<style>
:root {
  --gold: #f7d774;
  --gold2: #b8862b;
  --navy: #061126;
  --blue: #102b54;
  --white: #f8f5ec;
}
* { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
body {
  margin: 0;
  background: radial-gradient(ellipse at center, #17345d 0%, #071329 55%, #020611 100%);
  color: var(--white);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  min-height: 100vh;
  min-height: -webkit-fill-available;
  overflow: hidden;
  user-select: none;
  -webkit-user-select: none;
}
html {
  height: -webkit-fill-available;
}
body:before {
  content: "";
  position: fixed;
  inset: 0;
  background: linear-gradient(115deg, transparent 40%, #f7d7740c 50%, transparent 60%);
  pointer-events: none;
}

/* Header UI */
.top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: clamp(12px, 2vh, 20px) 4vw;
  border-bottom: 1px solid #f7d77455;
  background: #030a18a8;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
}
.brand { display: flex; align-items: center; gap: 15px; }
.crest {
  width: 50px;
  height: 50px;
  border: 2px solid var(--gold);
  border-radius: 12px;
  display: grid;
  place-items: center;
  color: var(--gold);
  font-weight: 900;
  letter-spacing: 1px;
  box-shadow: 0 0 22px #f7d77435;
  font-size: 14px;
}
h1 { font-size: clamp(16px, 2.2vw, 26px); margin: 0; color: var(--gold); letter-spacing: 1px; font-weight: 800; }
.sub { font-size: 11px; letter-spacing: 2px; color: #c8d3e7; margin-top: 4px; }
.status {
  font-size: 11px;
  color: var(--gold);
  border: 1px solid #f7d77466;
  padding: 8px 16px;
  border-radius: 30px;
  letter-spacing: 1px;
  background: rgba(247, 215, 116, 0.05);
}

/* Main Layout */
main {
  height: calc(100vh - 85px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}
.screen { width: min(1000px, 100%); text-align: center; position: relative; }
.eyebrow { color: var(--gold); font-size: 12px; letter-spacing: 5px; font-weight: bold; margin-bottom: 14px; }
h2 { font-size: clamp(28px, 5vw, 62px); line-height: 1.1; margin: 0 0 14px; text-transform: uppercase; text-shadow: 0 0 28px #f7d77440; }
.desc { color: #c8d3e7; letter-spacing: 1px; font-size: clamp(13px, 1.6vw, 16px); margin: 0 auto 24px; max-width: 680px; line-height: 1.6; }

/* Camera / Scan Display Frame */
.scan-stage {
  position: relative;
  width: min(360px, 75vw);
  height: 270px;
  margin: 0 auto 24px;
  border: 1px solid #f7d77480;
  border-radius: 24px;
  overflow: hidden;
  background: linear-gradient(145deg, #0b1c37, #020916);
  box-shadow: 0 0 55px #4ba8ff17, inset 0 0 40px #f7d7740b;
}
video#camera {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0.7;
  transform: scaleX(-1);
  display: none;
}
.scan-frame {
  position: absolute;
  inset: 25px 70px;
  border: 2px solid #f7d774;
  border-radius: 45% 45% 40% 40%;
  box-shadow: 0 0 20px #f7d77444;
  pointer-events: none;
}
.scan-frame:before, .scan-frame:after { content: ""; position: absolute; width: 20px; height: 20px; border-color: #fff3b0; border-style: solid; }
.scan-frame:before { top: -2px; left: -2px; border-width: 3px 0 0 3px; }
.scan-frame:after { bottom: -2px; right: -2px; border-width: 0 3px 3px 0; }

.scanline {
  position: absolute;
  left: 10%; right: 10%;
  height: 3px;
  top: 15%;
  background: linear-gradient(90deg, transparent, #9be7ff, #ffe9a0, transparent);
  box-shadow: 0 0 20px #79ddff;
  opacity: 0;
  pointer-events: none;
}
.scanning .scanline { opacity: 1; animation: scan 1.5s ease-in-out infinite alternate; }
@keyframes scan { from { top: 15%; } to { top: 85%; } }

.face-icon {
  position: absolute;
  inset: 0;
  display: grid;
  place-items: center;
  font-size: 80px;
  filter: drop-shadow(0 0 20px #f7d77466);
  pointer-events: none;
}
.scan-label {
  position: absolute;
  bottom: 12px; left: 0; right: 0;
  font-size: 11px;
  letter-spacing: 2px;
  color: #f7d774;
  font-weight: 600;
  text-shadow: 0 1px 3px rgba(0,0,0,0.8);
}

/* Touch Friendly Buttons */
.btns { display: flex; gap: 12px; justify-content: center; flex-wrap: wrap; }
button {
  border: 1px solid #f7d77488;
  background: #0b1b35;
  color: var(--white);
  padding: 16px 24px;
  border-radius: 12px;
  font-size: 15px;
  font-weight: bold;
  letter-spacing: 1px;
  cursor: pointer;
  transition: all 0.2s ease;
  touch-action: manipulation;
  min-height: 52px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
button:active { transform: scale(0.96); opacity: 0.9; }
button.primary {
  background: linear-gradient(110deg, #f8df8c, #bb8729);
  color: #0d131f;
  border: 0;
  box-shadow: 0 4px 20px rgba(247, 215, 116, 0.3);
}

.note { font-size: 11px; color: #8fa2c0; margin-top: 16px; line-height: 1.5; }

/* Fullscreen Overlay Displays */
.full {
  position: fixed;
  inset: 0;
  display: none;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 5vw;
  background: radial-gradient(ellipse at center, #1a3154, #030713 72%);
  z-index: 100;
}
.full.show { display: flex; }
.approved { font-size: clamp(16px, 2.5vw, 25px); color: #e8f0ff; letter-spacing: 4px; margin-bottom: 20px; font-weight: bold; }
.big {
  font-size: clamp(34px, 7.5vw, 84px);
  color: var(--gold);
  font-weight: 900;
  text-shadow: 0 0 35px #f7d77480;
  line-height: 1.15;
}
.tagline { letter-spacing: 5px; color: #dce6f7; margin-top: 25px; font-size: 13px; font-weight: 600; }
.count { font-size: clamp(50px, 10vw, 110px); font-weight: 900; color: white; margin-top: 15px; text-shadow: 0 0 25px rgba(255,255,255,0.5); }

/* Video Player Screen */
#videoScreen { background: #000; z-index: 200; padding: 0; }
#montage { width: 100%; height: 100%; object-fit: contain; background: #000; }
.video-controls { position: absolute; top: 20px; right: 20px; z-index: 210; }

/* Settings Panel */
#settings {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.85);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  z-index: 300;
  display: none;
  align-items: center;
  justify-content: center;
  padding: 20px;
}
#settings.show { display: flex; }
.panel {
  width: min(550px, 100%);
  background: #09162b;
  border: 1px solid #f7d77488;
  border-radius: 20px;
  padding: 28px;
  text-align: left;
  box-shadow: 0 10px 40px rgba(0,0,0,0.5);
}
.panel h3 { color: var(--gold); margin-top: 0; font-size: 20px; }
.panel label { display: block; font-size: 13px; color: #c8d3e7; margin: 16px 0 8px; font-weight: 600; }
.panel input {
  width: 100%;
  padding: 14px;
  border-radius: 10px;
  background: #020916;
  color: white;
  border: 1px solid #455875;
  font-size: 14px;
}
.panel .btns { justify-content: flex-end; margin-top: 24px; }

/* iPad Landscape / Portrait Tweaks */
@media (max-width: 768px) {
  .status { display: none; }
  main { padding: 12px; }
  .scan-stage { height: 230px; }
  button { padding: 14px 18px; font-size: 14px; }
}
</style>
</head>
<body>

<header class="top">
 <div class="brand">
  <div class="crest">SKPP</div>
  <div>
   <h1>MAJLIS ANUGERAH KECEMERLANGAN</h1>
   <div class="sub">SEKOLAH KEBANGSAAN PADANG PEKAN · JITRA, KEDAH</div>
  </div>
 </div>
 <div class="status">● SISTEM PERASMIAN DIGITAL</div>
</header>

<main>
 <section class="screen" id="home">
  <div class="eyebrow">PROTOKOL PERASMIAN DIGITAL</div>
  <h2>Imbasan Identiti<br><span style="color:var(--gold)">Guru Besar</span></h2>
  <p class="desc">Sila berdiri di hadapan iPad dan tekan butang imbasan untuk mengaktifkan protokol perasmian Majlis Anugerah Kecemerlangan SK Padang Pekan.</p>
  
  <div class="scan-stage" id="scanStage">
   <video id="camera" autoplay playsinline muted></video>
   <div class="face-icon" id="faceIcon">♙</div>
   <div class="scan-frame"></div>
   <div class="scanline"></div>
   <div class="scan-label" id="scanLabel">SISTEM SEDIA · MENUNGGU IMBASAN</div>
  </div>

  <div class="btns">
   <button class="primary" id="scanBtn">⌾ MULAKAN IMBASAN WAJAH</button>
   <button id="cameraBtn">📷 AKTIFKAN KAMERA IPAD</button>
   <button id="settingsBtn">⚙ TETAPAN VIDEO</button>
  </div>

  <div class="note">
   Nota teknikal: Kesan imbasan ini ialah simulasi visual khas untuk gimik pentas.<br>
   Urus setia boleh memilih fail video montaj daripada iPad terlebih dahulu melalui Tetapan Video.
  </div>
 </section>
</main>

<!-- Approved Display Screen -->
<section class="full" id="approvedScreen">
 <div>
  <div class="approved">✓ IDENTITI DIIMBAS · PROTOKOL AKTIF</div>
  <div class="eyebrow">DENGAN LAFAZ BISMILLAHIRRAHMANIRRAHIM</div>
  <div class="big">MAJLIS ANUGERAH<br>KECEMERLANGAN</div>
  <h2 style="font-size:clamp(20px,3.5vw,36px);margin-top:20px;color:#fff;">SEKOLAH KEBANGSAAN PADANG PEKAN</h2>
  <div class="big" style="font-size:clamp(26px,4.5vw,52px);margin-top:20px;">DENGAN INI DIRASMIKAN!</div>
  <div class="tagline">BERUSAHA · BERILMU · BERJASA</div>
  <div class="count" id="countdown">3</div>
 </div>
</section>

<!-- Video Player Screen -->
<section class="full" id="videoScreen">
 <video id="montage" playsinline controls></video>
 <div class="video-controls">
  <button id="closeVideo">✕ KEMBALI KE GIMIK</button>
 </div>
</section>

<!-- Settings Modal -->
<div id="settings">
 <div class="panel">
  <h3>⚙ Tetapan Urus Setia</h3>
  <p style="color:#b9c7dd;font-size:13px;line-height:1.5">Pilih fail video montaj daripada Galeri/Files iPad atau masukkan pautan video MP4.</p>
  
  <label>Fail Video (Dari iPad / Photos / Files)</label>
  <input type="file" id="videoFile" accept="video/*">
  
  <label>Atau Pautan Direct MP4 / WebM</label>
  <input type="url" id="videoUrl" placeholder="https://.../montaj.mp4">
  
  <div class="btns">
   <button id="cancelSettings">BATAL</button>
   <button class="primary" id="saveSettings">SIMPAN VIDEO</button>
  </div>
 </div>
</div>

<script>
const $ = id => document.getElementById(id);
let videoSource = '', localUrl = '', countTimer = null;
const cameraEl = $('camera');
const montageEl = $('montage');

// Settings Handlers
$('settingsBtn').onclick = () => $('settings').classList.add('show');
$('cancelSettings').onclick = () => $('settings').classList.remove('show');

$('saveSettings').onclick = () => {
  const f = $('videoFile').files[0];
  if (f) {
    if (localUrl) URL.revokeObjectURL(localUrl);
    localUrl = URL.createObjectURL(f);
    videoSource = localUrl;
    // Preload video stream for iOS/iPadOS compatibility
    montageEl.src = videoSource;
    montageEl.load();
  } else if ($('videoUrl').value.trim()) {
    videoSource = $('videoUrl').value.trim();
    montageEl.src = videoSource;
    montageEl.load();
  }
  $('settings').classList.remove('show');
};

// iPad Camera Activation (Front Camera Priority)
$('cameraBtn').onclick = async () => {
  try {
    const constraints = {
      video: {
        facingMode: "user", // Prioritize iPad front camera
        width: { ideal: 1280 },
        height: { ideal: 720 }
      },
      audio: false
    };
    const stream = await navigator.mediaDevices.getUserMedia(constraints);
    cameraEl.srcObject = stream;
    cameraEl.style.display = 'block';
    $('faceIcon').style.display = 'none';
    $('cameraBtn').textContent = '✓ KAMERA AKTIF';
    $('scanLabel').textContent = 'KAMERA AKTIF · SILA PANDANG KE HADAPAN';
  } catch (e) {
    console.error("Camera access error:", e);
    $('scanLabel').textContent = 'KAMERA DINOFAKAN / TIDAK DIBENARKAN · GIMIK TETAP BOLEH DIJALANKAN';
  }
};

// Start Scanning Gesture
$('scanBtn').onclick = () => {
  // Pre-trigger video playback (Crucial for iOS/Safari Autoplay Policies)
  if (videoSource) {
    montageEl.play().then(() => {
      montageEl.pause();
      montageEl.currentTime = 0;
    }).catch(() => {
      console.log("Audio/Video pre-activation ready");
    });
  }

  if (countTimer) clearInterval(countTimer);
  $('scanStage').classList.add('scanning');
  $('scanLabel').textContent = 'MENGIMBAS WAJAH...';
  $('scanBtn').disabled = true;
  $('scanBtn').style.opacity = '0.6';

  setTimeout(() => {
    $('scanStage').classList.remove('scanning');
    $('scanLabel').textContent = 'AKSES PERASMIAN DILULUSKAN';
    $('faceIcon').style.display = 'grid';
    $('faceIcon').textContent = '✓';
    $('faceIcon').style.color = '#f7d774';
    $('home').style.display = 'none';
    $('approvedScreen').classList.add('show');

    let n = 3;
    $('countdown').textContent = n;
    countTimer = setInterval(() => {
      n--;
      if (n > 0) {
        $('countdown').textContent = n;
      } else {
        clearInterval(countTimer);
        showVideo();
      }
    }, 1000);
  }, 3500);
};

// Video Launcher
function showVideo() {
  $('approvedScreen').classList.remove('show');
  $('videoScreen').classList.add('show');

  if (videoSource) {
    montageEl.src = videoSource;
    const playPromise = montageEl.play();
    if (playPromise !== undefined) {
      playPromise.catch(error => {
        console.log("Playback required interaction:", error);
        montageEl.controls = true;
      });
    }
  } else {
    montageEl.removeAttribute('src');
    montageEl.load();
    montageEl.controls = false;
    if (!$('noVideo')) {
      $('videoScreen').insertAdjacentHTML('beforeend', '<div id="noVideo" style="position:absolute;inset:0;display:grid;place-items:center;color:#f7d774;text-align:center;padding:30px;background:#000"><div><h2>VIDEO MONTAJ BELUM DIPILIH</h2><p style="color:#fff;margin-top:10px">Sila tekan “Kembali ke Gimik” dan pilih video dalam Tetapan Video.</p></div></div>');
    }
  }
}

// Reset / Close Video
$('closeVideo').onclick = () => {
  montageEl.pause();
  $('videoScreen').classList.remove('show');
  $('home').style.display = 'block';
  $('scanBtn').disabled = false;
  $('scanBtn').style.opacity = '1';
  $('scanLabel').textContent = 'SISTEM SEDIA · MENUNGGU IMBASAN';
  $('faceIcon').textContent = '♙';
  $('faceIcon').style.color = '';
  $('noVideo')?.remove();
};
</script>
</body>
</html>