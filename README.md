[index.html](https://github.com/user-attachments/files/29314530/index.html)
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>מאגר מידע ליועצי משכנתאות</title>
<style>
body{font-family:Arial,sans-serif;background:#0f172a;color:#fff;margin:0;padding:20px}
.container{max-width:1400px;margin:auto}
h1{text-align:center}
input{width:100%;padding:14px;border-radius:12px;border:none;margin:15px 0}
.tabs{display:flex;gap:10px;flex-wrap:wrap;margin-bottom:15px}
.tab{padding:10px 16px;background:#1e293b;border-radius:10px;cursor:pointer}
.active{background:#2563eb}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:15px}
.card{background:rgba(255,255,255,.08);padding:15px;border-radius:15px;cursor:pointer}
.modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);align-items:center;justify-content:center}
.modal-content{background:#111827;padding:20px;border-radius:15px;max-width:700px;width:95%}
.btn{display:inline-block;padding:10px 15px;border-radius:10px;color:#fff;text-decoration:none;margin:5px}
.phone{background:#16a34a}.mail{background:#2563eb}.map{background:#ea580c}
</style>
</head>
<body>
<div class="container">
<h1>📊 מאגר מידע ליועצי משכנתאות</h1>
<div>סה"כ רשומות: <span id="count">0</span></div>
<input id="search" placeholder="חיפוש בכל השדות...">
<div id="tabs" class="tabs"></div>
<div id="grid" class="grid"></div>
</div>

<div class="modal" id="modal">
<div class="modal-content">
<div id="details"></div>
<button onclick="closeModal()">סגור</button>
</div>
</div>

<script>
const API_URL="https://script.google.com/macros/s/AKfycbzyimakjy8d3CGtK0Rw4qiN7d6XMgFe2cUh4zUUpSLFP6hbl1X4ZMpVyeqS8BQOHRLg/exec";
let data=[];
let currentSheet="הכל";

fetch(API_URL)
.then(r=>r.json())
.then(res=>{data=res;buildTabs();render();})
.catch(e=>alert("שגיאה בטעינת הנתונים: "+e));

function buildTabs(){
const sheets=["הכל",...new Set(data.map(x=>x._sheetName))];
document.getElementById("tabs").innerHTML=sheets.map((s,i)=>`<div class="tab ${i===0?'active':''}" onclick="selectSheet('${s}',this)">${s}</div>`).join('');
}
function selectSheet(s,el){
currentSheet=s;
document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
el.classList.add('active');
render();
}
function render(){
let rows=[...data];
if(currentSheet!=="הכל") rows=rows.filter(x=>x._sheetName===currentSheet);
const q=document.getElementById("search").value.toLowerCase();
if(q) rows=rows.filter(x=>JSON.stringify(x).toLowerCase().includes(q));
document.getElementById("count").innerText=rows.length;

document.getElementById("grid").innerHTML=rows.map(r=>{
const name=r["שם החברה "]||r["שם החברה"]||r["שם חברה"]||"ללא שם";
return `<div class="card" onclick="showCard(${data.indexOf(r)})">
<b>${name}</b><br>${r["טלפון"]||""}<br><small>${r._sheetName||""}</small>
</div>`;
}).join('');
}
document.getElementById("search").addEventListener("input",render);

function showCard(i){
const r=data[i];
let h='';
for(const k in r){
 if(k.startsWith('_')) continue;
 h+=`<p><b>${k}</b><br>${r[k]||''}</p>`;
}
if(r["טלפון"]) h+=`<a class="btn phone" href="tel:${r["טלפון"]}">📞 חיוג</a>`;
if(r['דוא"ל']) h+=`<a class="btn mail" href="mailto:${r['דוא"ל']}">✉️ מייל</a>`;
if(r["כתובת"]) h+=`<a class="btn map" target="_blank" href="https://maps.google.com/?q=${encodeURIComponent(r["כתובת"])}">📍 מפה</a>`;
document.getElementById("details").innerHTML=h;
document.getElementById("modal").style.display="flex";
}
function closeModal(){document.getElementById("modal").style.display="none";}
</script>
</body>
</html>
<!-- Injection By NetFree -->
<script src="https://netfree.link/injection-script/note-in-site.js" type="text/javascript" async  id="netfree-note-site" jsondata="%7B%22noteSite%22:%22%D7%9B%D7%93%D7%99%20%D7%A9%D7%94%D7%AA%D7%9E%D7%95%D7%A0%D7%95%D7%AA%20%D7%91%D7%90%D7%AA%D7%A8%20%D7%94%D7%96%D7%94%20%D7%99%D7%97%D7%96%D7%A8%D7%95%20%D7%9E%D7%91%D7%93%D7%99%D7%A7%D7%94%2C%20%D7%99%D7%A9%20%D7%9C%D7%94%D7%92%D7%93%D7%99%D7%A8%20%5C%22%D7%90%D7%A4%D7%A9%D7%A8%20%D7%9C%D7%A1%D7%A0%D7%9F%20%D7%AA%D7%95%D7%9B%D7%9F%20%D7%A9%D7%99%D7%93%D7%95%D7%A2%20%D7%9B%D7%90%D7%99%D7%A9%D7%99%20%D7%90%D7%95%20%D7%A4%D7%A8%D7%98%D7%99%5C%22%20%D7%91%D7%94%D7%92%D7%93%D7%A8%D7%95%D7%AA%20%D7%A1%D7%99%D7%A0%D7%95%D7%9F%20%5B%5B%D7%A6%D7%90%D7%98_AI_%D7%91%D7%A0%D7%98%D7%A4%D7%A8%D7%99%7C%D7%94%D7%99%D7%9B%D7%A0%D7%A1%D7%95%20%D7%9C%D7%9B%D7%90%D7%9F%20%D7%9C%D7%94%D7%A1%D7%91%D7%A8%20%D7%9E%D7%A4%D7%95%D7%A8%D7%98%5D%5D%22%2C%22noteSiteEn%22:%22For%20images%20on%20this%20website%20to%20work%20you%20need%20to%20set%20%5C%22Filter%20content%20that%20is%20known%20as%20personal%20or%20private%5C%22%20%5B%5BAI_Chats_in_NetFree%7CClick%20here%20to%20read%20more%5D%5D%22%7D"></script><script src="//netfree.link/injection-script/go-payment.js" type="text/javascript" async ></script>
<script src="//netfree.link/injection-script/popup-card-init.js" type="text/javascript" async ></script>
