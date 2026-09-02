<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>मेरी बारी कब आएगी?</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Arial,sans-serif;background:#f4f6f8;color:#17202a}
.wrap{max-width:520px;margin:auto;padding:18px}.card{background:white;border-radius:20px;padding:22px;margin:14px 0;box-shadow:0 5px 18px #00000012}
h1{font-size:25px;margin:5px 0 8px}.sub{color:#65717d;margin-bottom:20px}
.big{text-align:center;font-size:48px;font-weight:800;margin:15px 0 4px}.center{text-align:center}
.status{display:inline-block;padding:8px 14px;border-radius:999px;font-weight:700;margin:10px}
.info{display:flex;justify-content:space-between;padding:12px 0;border-bottom:1px solid #eee}
button{border:0;border-radius:14px;padding:14px 18px;font-size:17px;font-weight:700;cursor:pointer;margin:5px}
.plus{font-size:28px;min-width:70px}.reset{width:100%;margin-top:14px;background:#17202a;color:white}
.tabs{display:flex;gap:8px}.tab{flex:1;background:#e9edf1}.active{background:#17202a;color:white}
.hidden{display:none}.note{font-size:13px;color:#68737d;line-height:1.5}
</style>
</head>
<body>
<div class="wrap">
  <div class="card">
    <h1>🏪 मेरी बारी कब आएगी?</h1>
    <div class="sub">छोटा Queue & Wait-Time Demo</div>
    <div class="tabs">
      <button class="tab active" onclick="show('customer',this)">👤 ग्राहक</button>
      <button class="tab" onclick="show('shop',this)">🏪 दुकानदार</button>
    </div>
  </div>

  <section id="customer">
    <div class="card center">
      <div class="sub">ABC Salon</div>
      <div class="big" id="wait">20</div>
      <div>मिनट अनुमानित इंतज़ार</div>
      <div class="status" id="status">🟢 सामान्य</div>
      <div class="info"><span>👥 आपसे पहले</span><b id="people">4 लोग</b></div>
      <div class="info"><span>🔄 आखिरी अपडेट</span><b>अभी</b></div>
    </div>
    <div class="card note">
      ℹ️ यह Demo है। वास्तविक Business Version में QR Code, अलग-अलग दुकानों के खाते और लाइव डेटा जोड़ा जाएगा।
    </div>
  </section>

  <section id="shop" class="hidden">
    <div class="card center">
      <h2>दुकानदार पैनल</h2>
      <p>अभी कतार में</p>
      <div class="big" id="shopPeople">4</div>
      <button class="plus" onclick="change(1)">＋</button>
      <button class="plus" onclick="change(-1)">−</button>
      <p id="shopWait">अनुमानित इंतज़ार: 20 मिनट</p>
      <button class="reset" onclick="resetQueue()">कतार रीसेट करें</button>
    </div>
  </section>
</div>

<script>
let people=4;
function update(){
  let wait=people*5;
  document.getElementById('people').textContent=people+' लोग';
  document.getElementById('shopPeople').textContent=people;
  document.getElementById('wait').textContent=wait;
  document.getElementById('shopWait').textContent='अनुमानित इंतज़ार: '+wait+' मिनट';
  let s=document.getElementById('status');
  if(people<=3){s.textContent='🟢 सामान्य';}
  else if(people<=7){s.textContent='🟡 थोड़ी भीड़';}
  else{s.textContent='🔴 ज्यादा भीड़';}
}
function change(n){people=Math.max(0,people+n);update();}
function resetQueue(){people=0;update();}
function show(id,btn){
  document.getElementById('customer').classList.toggle('hidden',id!=='customer');
  document.getElementById('shop').classList.toggle('hidden',id!=='shop');
  document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
  btn.classList.add('active');
}
update();
</script>
</body>
</html>
