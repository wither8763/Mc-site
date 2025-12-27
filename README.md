# Mc-site
<!DOCTYPE html><html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CraftMine Bedrock</title>
<link href="https://fonts.cdnfonts.com/css/minecraft-4" rel="stylesheet">
<style>
*{box-sizing:border-box}
body{
  margin:0;
  background:#0f1a0f;
  color:#7CFC98;
  font-family:'Minecraft', monospace;
}
header{
  background:#1f3d1f;
  padding:16px;
  text-align:center;
  border-bottom:4px solid #00ff55;
}
section{padding:12px}
.card{
  border:3px solid #00ff55;
  margin:12px 0;
  padding:14px;
  background:#132613;
  border-radius:10px;
}
.button{
  display:block;
  margin-top:10px;
  padding:14px;
  text-align:center;
  border:3px solid #00ff55;
  border-radius:12px;
  background:#0f1a0f;
  color:#00ff55;
  text-decoration:none;
  font-size:16px;
}
.button:active{background:#00ff55;color:#0f1a0f}
.status{margin-top:6px;font-size:14px}
footer{text-align:center;padding:12px;font-size:11px;opacity:.85}
</style>
</head>
<body><header>
  <h1>☠️ CraftMine</h1>
  <p>Bedrock • Mobil First • Beleş</p>
</header><section>
  <div class="card">
    <h2>⛏️ Sunucu Bilgileri</h2>
    <p><b>IP:</b> Wither8763.artenos.me</p>
    <p><b>Port:</b> 58889</p>
    <p><b>Platform:</b> Bedrock Edition</p>
    <p class="status" id="status">Durum: kontrol ediliyor…</p><a class="button" onclick="copyIP()">IP + Port Kopyala</a>
<a class="button" onclick="copyOnlyIP()">Sadece IP Kopyala</a>
<a class="button" href="minecraft://?addExternalServer=CraftMine|Wither8763.artenos.me:58889">Minecraft'ta Aç</a>

  </div>  <div class="card">
    <h2>👥 Oyuncular</h2>
    <p id="players">Oyuncu sayısı: bilinmiyor</p>
  </div>  <div class="card">
    <h2>🧱 Mod</h2>
    <p>Survival • One Block • Wither teması</p>
  </div>
</section><footer>
  <p>%100 Beleş • CraftMine</p>
</footer><script>
const ip = "Wither8763.artenos.me";
const port = "58889";

function copyIP(){
  navigator.clipboard.writeText(ip+":"+port);
}
function copyOnlyIP(){
  navigator.clipboard.writeText(ip);
}

fetch("https://api.mcsrvstat.us/bedrock/2/"+ip+":"+port)
.then(r=>r.json())
.then(d=>{
  document.getElementById("status").innerText = "Durum: " + (d.online ? "Online 🟢" : "Offline 🔴");
  if(d.players){
    document.getElementById("players").innerText = "Oyuncu sayısı: " + d.players.online;
  }
})
.catch(()=>{
  document.getElementById("status").innerText = "Durum: Bilinmiyor";
});
</script></body>
</html>
