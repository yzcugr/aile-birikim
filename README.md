# aile-birikim
Didem&amp;Uğur Aile Birikim Takip
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Didem & Uğur - Aile Birikim</title>
<link rel="manifest" href="manifest.json">
<style>
body {
  margin:0;
  font-family: Arial, sans-serif;
  background:#111;
  color:white;
}
header{
  padding:20px;
  text-align:center;
  font-size:20px;
  font-weight:bold;
}
.card{
  background:#1e1e1e;
  margin:15px;
  padding:15px;
  border-radius:12px;
}
button{
  background:gold;
  border:none;
  padding:10px;
  border-radius:8px;
  width:100%;
  margin-top:10px;
}
input, select{
  width:100%;
  padding:8px;
  margin-top:8px;
  border-radius:6px;
  border:none;
}
.green{color:#00ff88;}
.red{color:#ff4d4d;}
</style>
</head>
<body>

<header>🌙 Didem & Uğur - Aile Birikim</header>

<div class="card">
<h3>İşlem Ekle</h3>
<select id="tur">
<option>Gram Altın</option>
<option>Çeyrek Altın</option>
<option>Dolar</option>
<option>Euro</option>
</select>
<input type="number" id="miktar" placeholder="Miktar">
<input type="number" id="fiyat" placeholder="Alış Fiyatı">
<button onclick="ekle()">Kaydet</button>
</div>

<div class="card">
<h3>Toplam Varlık</h3>
<p id="toplam">0 TL</p>
</div>

<script>
let veriler = JSON.parse(localStorage.getItem("veriler")) || [];

function ekle(){
  let tur = document.getElementById("tur").value;
  let miktar = parseFloat(document.getElementById("miktar").value);
  let fiyat = parseFloat(document.getElementById("fiyat").value);
  let toplam = miktar * fiyat;
  veriler.push({tur,miktar,fiyat,toplam});
  localStorage.setItem("veriler",JSON.stringify(veriler));
  hesapla();
}

function hesapla(){
  let toplam=0;
  veriler.forEach(v=>toplam+=v.toplam);
  document.getElementById("toplam").innerText = toplam.toFixed(2)+" TL";
}

hesapla();
</script>

</body>
</html>
manifest.json
{
  "name": "Didem & Uğur - Aile Birikim",
  "short_name": "Aile Birikim",
  "start_url": "index.html",
  "display": "standalone",
  "background_color": "#111111",
  "theme_color": "#111111",
  "icons": [
    {
      "src": "icon.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}

