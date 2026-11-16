<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8"><meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AH ACADEMY | مستر أحمد حسن</title>
<style>
*{box-sizing:border-box;font-family:'Segoe UI',Tahoma,sans-serif} body{margin:0;transition:.3s}
body.dark{background:#060a14;color:#fff} body.light{background:#f1f5f9;color:#0f172a}
:root{--main:#00c9a7;--main2:#0ea5e9}
.top{position:sticky;top:0;z-index:20;display:flex;justify-content:space-between;align-items:center;padding:13px 16px;backdrop-filter:blur(14px);border-bottom:1px solid rgba(128,128,128,.15)}
.dark .top{background:rgba(10,15,30,.85)} .light .top{background:rgba(255,255,255,.9)}
.logo{font-weight:900;font-size:21px;cursor:pointer} .logo span{color:var(--main)}
.btn{border:0;padding:11px 18px;border-radius:999px;font-weight:800;cursor:pointer} .btn-main{background:linear-gradient(90deg,var(--main),var(--main2));color:#02130c} .btn-ghost{background:rgba(128,128,128,.18);color:inherit}
.hero{padding:30px 16px;text-align:center}
.dark .hero{background:radial-gradient(circle at 50% 0%,#0d2f35 0%,#060a14 70%)} .light .hero{background:linear-gradient(180deg,#e0f2fe,#f1f5f9)}
.hero img{width:122px;height:122px;border-radius:28px;object-fit:cover;border:3px solid var(--main)}
.stats{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;margin:16px 0} .stat{padding:12px 14px;border-radius:16px;min-width:84px;text-align:center;border:1px solid rgba(128,128,128,.2)} .dark .stat{background:rgba(255,255,255,.06)} .light .stat{background:#fff} .stat b{font-size:20px;color:var(--main);display:block}
.container{max-width:950px;margin:auto;padding:14px}
.card{border-radius:20px;padding:16px;margin-bottom:12px;border:1px solid rgba(128,128,128,.2)} .dark .card{background:#101626} .light .card{background:#fff}
.lesson{padding:13px;border-radius:14px;margin-top:9px;display:flex;justify-content:space-between;align-items:center;border:1px solid rgba(128,128,128,.15)} .dark .lesson{background:#161f2e} .light .lesson{background:#f8fafc}
input,select{width:100%;padding:12px;border-radius:12px;border:1px solid #cbd5e1;margin:6px 0} .dark input,.dark select{background:#0b1220;color:white;border-color:#334155} .light input,.light select{background:#fff;color:#111}
.modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,.85);z-index:99;padding:14px;overflow:auto}
.modalBox{border-radius:22px;max-width:680px;margin:20px auto;padding:20px} .dark .modalBox{background:#111827;color:#fff} .light .modalBox{background:#fff;color:#111}
.opt{padding:12px;border-radius:12px;margin:8px 0;cursor:pointer;border:1px solid rgba(128,128,128,.2)}
.log{padding:9px;border-radius:10px;margin:6px 0;font-size:13px;border-right:3px solid var(--main)} .dark .log{background:#0b1220} .light .log{background:#f1f5f9}
.chip{background:rgba(0,201,167,.15);color:var(--main);padding:5px 10px;border-radius:999px;font-size:12px}
.empty{text-align:center;opacity:.65;padding:18px;border:1px dashed #94a3b8;border-radius:14px;margin-top:10px}
.videoBox iframe{width:100%;height:220px;border-radius:12px;border:0;margin-top:10px}
table{width:100%;border-collapse:collapse;font-size:13px} th,td{border-bottom:1px solid #475569;padding:9px;text-align:right} th{color:var(--main)}
.footer{text-align:center;opacity:.5;font-size:12px;padding:20px}
</style>
</head>
<body class="dark">
<div class="top"><div class="logo" id="logoSecret">AH <span>ACADEMY</span></div><div style="display:flex;gap:6px"><button class="btn btn-ghost" onclick="toggleTheme()">🌗</button><button class="btn btn-ghost" onclick="openM('loginM')">دخول</button><button class="btn btn-main" onclick="openM('regM')">حساب جديد</button></div></div>
<div class="hero">
<img id="tImg" src="https://via.placeholder.com/400x400.png?text=AH">
<h1 id="tName">منصة مستر أحمد حسن</h1>
<p>علوم متكاملة - الصف الأول الثانوي</p>
<div class="stats">
<div class="stat"><b id="statStudents">0</b> طالب</div>
<div class="stat"><b id="statVideos">0</b> فيديو</div>
<div class="stat"><b id="statLessons">0</b> درس</div>
<div class="stat"><b id="statExams">0</b> امتحان</div>
</div>
<button class="btn btn-main" onclick="openM('regM')">اعمل حسابك - كن أول طالب 🚀</button>
<p id="welcome" style="margin-top:12px;font-weight:700">أهلاً بيك في المنصة، اعمل حسابك وابدأ</p>
<p id="dbStatus" style="font-size:12px;opacity:.7">جارٍ الاتصال بقاعدة البيانات...</p>
</div>
<div class="container">
<div class="card"><h3>🎯 لوحة الطالب</h3><p id="myProg">سجل دخولك عشان تشوف نقاطك</p><p>نقاطك: <b id="myPoints">0</b> | تقدمك: <b id="myProgText">0%</b></p></div>
<div class="card"><h3>🏆 لوحة الشرف</h3><div id="leaders"></div></div>
<div id="courses"></div>
<div class="card"><h3>🏆 امتحان الوحدة</h3><p id="examInfo">الامتحان هيظهر هنا لما المدرس يضيفه</p><div id="quizArea"></div><button class="btn btn-main" onclick="startQuiz()">ابدأ الامتحان</button><p id="quizRes"></p><div id="cert" style="display:none;background:linear-gradient(135deg,#00c9a7,#0ea5e9);color:#02130c;padding:18px;border-radius:16px;text-align:center"><h2>🎓 شهادة تفوق</h2><p>الطالب</p><h1 id="certName"></h1><p>علوم متكاملة - أولى ثانوي</p></div></div>
<div class="card"><h3>💬 كلم المستر</h3><button class="btn btn-main" onclick="window.open('https://wa.me/201065298676','_blank')">واتساب مستر أحمد حسن</button></div>
</div>
<div class="footer">AH ACADEMY © 2026 | تطوير: يوسف فايق</div>
<div id="regM" class="modal"><div class="modalBox"><h2>📝 اعمل حساب طالب</h2><input id="rName" placeholder="اسم الطالب بالكامل *"><input id="rEmail" placeholder="البريد الإلكتروني أو رقم الموبايل *"><input type="password" id="rPass" placeholder="كلمة سر *"><input id="rCode" placeholder="كود الطالب *"><button class="btn btn-main" style="width:100%" onclick="register()">إنشاء حسابي</button><button class="btn btn-ghost" style="width:100%;margin-top:8px" onclick="closeM('regM')">قفل</button></div></div>
<div id="loginM" class="modal"><div class="modalBox"><h2>🔐 دخول الطالب</h2><input id="lEmail" placeholder="البريد أو الموبايل"><input type="password" id="lPass" placeholder="كلمة السر"><button class="btn btn-main" style="width:100%" onclick="login()">دخول</button><button class="btn btn-ghost" style="width:100%;margin-top:8px" onclick="closeM('loginM')">قفل</button></div></div>
<div id="adminM" class="modal"><div class="modalBox"><h2>🔒 لوحة التحكم</h2><input type="password" id="aPass" placeholder="كلمة السر"><button class="btn btn-main" style="width:100%" onclick="adminLogin()">دخول</button><div id="adminBox" style="display:none"><hr><h3>👥 الطلبة: <span id="stuCount">0</span></h3><div id="stuTable"></div><h3>📜 سجل النشاط</h3><div id="logs"></div><hr><h3>🎥 اضافة درس جديد</h3><input id="newLessonTitle" placeholder="اسم الدرس"><input id="newLessonVideo" placeholder="رابط فيديو اليوتيوب"><select id="newLessonUnit"><option value="0">الوحدة 1</option><option value="1">الوحدة 2</option><option value="2">الوحدة 3</option></select><button class="btn btn-main" style="width:100%" onclick="addLesson()">➕ اضافة الدرس</button><hr><h3>🎨 تعديل المنصة</h3><input id="eName" placeholder="اسم جديد للمنصة"><input id="eImg" placeholder="لينك صورة جديدة"><div style="display:flex;gap:10px;margin:8px 0"><div style="width:42px;height:42px;border-radius:50%;background:#00c9a7;cursor:pointer" onclick="setTheme('#00c9a7','#0ea5e9')"></div><div style="width:42px;height:42px;border-radius:50%;background:#8b5cf6;cursor:pointer" onclick="setTheme('#8b5cf6','#ec4899')"></div><div style="width:42px;height:42px;border-radius:50%;background:#f59e0b;cursor:pointer" onclick="setTheme('#f59e0b','#ef4444')"></div></div><button class="btn btn-main" style="width:100%" onclick="saveAdmin()">💾 حفظ التعديلات</button><button class="btn btn-ghost" style="width:100%;margin-top:8px" onclick="clearAll()">🗑️ مسح الكل</button></div><button class="btn btn-ghost" style="width:100%;margin-top:8px" onclick="closeM('adminM')">قفل</button></div></div>

<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore-compat.js"></script>
<script>
var firebaseConfig={apiKey:"AIzaSyAXJHghzn2zjp0LwJnz5PLhhYZJtGI9Wbw",authDomain:"ah-academy.firebaseapp.com",projectId:"ah-academy",storageBucket:"ah-academy.firebasestorage.app",messagingSenderId:"444583784645",appId:"1:444583784645:web:a5d7b73b41cd76be3b00ac",measurementId:"G-LDFVXCR5PS"};
firebase.initializeApp(firebaseConfig);
var db=firebase.firestore();
var clickCount=0;
document.getElementById('logoSecret').addEventListener('click',function(){clickCount++;if(clickCount>=5){clickCount=0;openM('adminM')}setTimeout(function(){clickCount=0},2000)});
var units=[{title:'الوحدة 1: النظام البيئي والطاقة',lessons:[]},{title:'الوحدة 2: المادة والكيمياء',lessons:[]},{title:'الوحدة 3: الفيزياء والأرض والفضاء',lessons:[]}];
var studentsCache=[],logsCache=[];
async function loadAll(){
try{
var sSnap=await db.collection("students").get();
studentsCache=sSnap.docs.map(function(d){var o=d.data();o.id=d.id;return o});
var uDoc=await db.collection("settings").doc("units").get();
if(uDoc.exists&&uDoc.data().units)units=uDoc.data().units;
var lSnap=await db.collection("logs").orderBy("time","desc").limit(60).get();
logsCache=lSnap.docs.map(function(d){return d.data().text});
document.getElementById('dbStatus').innerText='✅ متصل بقاعدة البيانات - '+studentsCache.length+' طالب';
}catch(e){document.getElementById('dbStatus').innerText='⚠️ مش متصل - راجع Rules في Firebase';console.log(e)}
render();updateMe();
}
async function addLog(m){var t=new Date().toLocaleString('ar-EG')+' - '+m;logsCache.unshift(t);logsCache=logsCache.slice(0,60);try{await db.collection("logs").add({text:t,time:Date.now()})}catch(e){}}
function toEmbed(url){if(!url)return'';var id='';if(url.indexOf('v=')>-1)id=url.split('v=')[1].split('&')[0];else if(url.indexOf('youtu.be/')>-1)id=url.split('youtu.be/')[1].split('?')[0];else if(url.indexOf('embed/')>-1)return url;if(id)return 'https://www.youtube.com/embed/'+id;return url}
function render(){
var total=0;units.forEach(function(u){total+=u.lessons.length});
document.getElementById('statLessons').innerText=total;document.getElementById('statVideos').innerText=total;document.getElementById('statStudents').innerText=studentsCache.length;
var h='';units.forEach(function(u){h+='<div class="card"><div style="display:flex;justify-content:space-between"><h3>'+u.title+'</h3><span class="chip">'+u.lessons.length+' درس</span></div>';
if(!u.lessons.length){h+='<div class="empty">لا توجد دروس بعد</div>'}else{u.lessons.forEach(function(les){h+='<div class="lesson"><div><b>▶️ '+les.title+'</b></div><button class="btn btn-main" onclick="openLesson(\''+les.title.replace(/'/g,"")+'\')">مشاهدة</button></div>';if(les.video)h+='<div class="videoBox"><iframe src="'+toEmbed(les.video)+'" allowfullscreen></iframe></div>'})}
h+='</div>'});document.getElementById('courses').innerHTML=h;
var leaders=document.getElementById('leaders');
if(!studentsCache.length){leaders.innerHTML='<div class="empty">🏆 لا يوجد أبطال بعد</div>'}else{var s=[].concat(studentsCache).sort(function(a,b){return (b.points||0)-(a.points||0)});leaders.innerHTML=s.slice(0,3).map(function(x,i){return '<div style="display:flex;gap:10px;padding:10px;border-radius:12px;margin-top:8px;border:1px solid rgba(128,128,128,.2)"><b>'+(i+1)+'</b><div><b>'+x.name+'</b><br><small>'+(x.points||0)+' نقطة - كود '+x.code+'</small></div></div>'}).join('')}
}
function openM(id){document.getElementById(id).style.display='block'}
function closeM(id){document.getElementById(id).style.display='none'}
function toggleTheme(){var b=document.body;if(b.classList.contains('dark')){b.classList.remove('dark');b.classList.add('light')}else{b.classList.remove('light');b.classList.add('dark')}}
async function register(){
var n=document.getElementById('rName').value.trim(),e=document.getElementById('rEmail').value.trim(),p=document.getElementById('rPass').value,c=document.getElementById('rCode').value.trim();
if(c==='AH-ADMIN-2026'){closeM('regM');openM('adminM');return}
if(!n||!e||!p||!c)return alert('املأ كل البيانات');
if(c.indexOf('AH-')!==0)return alert('الكود غير صحيح');
if(studentsCache.find(function(s){return s.email===e}))return alert('الحساب موجود');
var ns={name:n,email:e,pass:p,code:c,points:0,lastLogin:new Date().toLocaleString('ar-EG'),score:'-'};
try{var ref=await db.collection("students").add(ns);ns.id=ref.id;studentsCache.push(ns);localStorage.setItem('ah_final_cur',JSON.stringify(ns));await addLog('طالب جديد: '+n);document.getElementById('welcome').innerText='أهلاً بيك يا '+n;closeM('regM');alert('تم إنشاء حسابك ✅');render();updateMe()}catch(err){alert('مشكلة اتصال - راجع Rules')}
}
async function login(){
var e=document.getElementById('lEmail').value.trim(),p=document.getElementById('lPass').value;
var u=studentsCache.find(function(s){return s.email===e&&s.pass===p});if(!u)return alert('البيانات غير صحيحة');
u.lastLogin=new Date().toLocaleString('ar-EG');try{await db.collection("students").doc(u.id).update({lastLogin:u.lastLogin})}catch(e){}
localStorage.setItem('ah_final_cur',JSON.stringify(u));await addLog('دخل: '+u.name);closeM('loginM');updateMe();render();alert('أهلاً بيك يا '+u.name);
}
function updateMe(){var cur=JSON.parse(localStorage.getItem('ah_final_cur')||'null');if(!cur)return;document.getElementById('myProg').innerText='مسجل باسم: '+cur.name+' | كودك: '+cur.code;document.getElementById('myPoints').innerText=cur.points||0}
async function openLesson(title){
var cur=JSON.parse(localStorage.getItem('ah_final_cur')||'null');if(!cur)return alert('اعمل حساب الأول');
await addLog(cur.name+' فتح درس: '+title);
var u=studentsCache.find(function(s){return s.email===cur.email});
if(u){u.points=(u.points||0)+10;cur.points=u.points;localStorage.setItem('ah_final_cur',JSON.stringify(cur));try{await db.collection("students").doc(u.id).update({points:u.points})}catch(e){}updateMe();render()}
alert('جارٍ تشغيل: '+title);
}
var quiz=[{q:'أي مصدر طاقة متجددة؟',o:['الفحم','الطاقة الشمسية','البترول'],a:1}];var qi=0,sc=0;
function startQuiz(){qi=0;sc=0;showQ()}
function showQ(){
if(qi>=quiz.length){var per=Math.round(sc/quiz.length*100);document.getElementById('quizRes').innerText='نتيجتك: '+per+'%';var cur=JSON.parse(localStorage.getItem('ah_final_cur')||'null');if(cur){addLog(cur.name+' جاب '+per+'%');var u=studentsCache.find(function(s){return s.email===cur.email});if(u){u.score=per+'%';u.points=(u.points||0)+per;cur.points=u.points;localStorage.setItem('ah_final_cur',JSON.stringify(cur));db.collection("students").doc(u.id).update({score:u.score,points:u.points});updateMe();render()}if(per>=80){document.getElementById('cert').style.display='block';document.getElementById('certName').innerText=cur.name}}return}
var q=quiz[qi];var h='<p><b>'+q.q+'</b></p>';q.o.forEach(function(o,i){h+='<div class="opt" onclick="ans('+i+')">'+o+'</div>'});document.getElementById('quizArea').innerHTML=h;
}
function ans(i){if(i===quiz[qi].a)sc++;qi++;showQ()}
function adminLogin(){
if(document.getElementById('aPass').value==='admin123'){document.getElementById('adminBox').style.display='block';document.getElementById('stuCount').innerText=studentsCache.length;var ht='<table><tr><th>الاسم</th><th>البريد</th><th>الكود</th><th>النقاط</th><th>آخر دخول</th></tr>';studentsCache.forEach(function(s){ht+='<tr><td>'+s.name+'</td><td>'+s.email+'</td><td>'+s.code+'</td><td>'+s.points+'</td><td>'+s.lastLogin+'</td></tr>'});ht+='</table>';if(!studentsCache.length)ht='<p>لا يوجد طلبة بعد</p>';document.getElementById('stuTable').innerHTML=ht;document.getElementById('logs').innerHTML=logsCache.length?logsCache.map(function(l){return '<div class="log">'+l+'</div>'}).join(''):'<p>لا يوجد نشاط</p>'}else alert('كلمة السر غير صحيحة');
}
function setTheme(c1,c2){document.documentElement.style.setProperty('--main',c1);document.documentElement.style.setProperty('--main2',c2)}
async function addLesson(){
var t=document.getElementById('newLessonTitle').value.trim();var v=document.getElementById('newLessonVideo').value.trim();var u=document.getElementById('newLessonUnit').value;if(!t)return alert('اكتب اسم الدرس');if(!v)return alert('الصق رابط الفيديو');
units[u].lessons.push({title:t,video:v});try{await db.collection("settings").doc("units").set({units:units})}catch(e){}
render();alert('تم اضافة الدرس ✅');document.getElementById('newLessonTitle').value='';document.getElementById('newLessonVideo').value='';
}
async function clearAll(){if(!confirm('مسح الكل؟'))return;for(var i=0;i<studentsCache.length;i++){try{await db.collection("students").doc(studentsCache[i].id).delete()}catch(e){}}await db.collection("settings").doc("units").set({units:[{title:'الوحدة 1: النظام البيئي والطاقة',lessons:[]},{title:'الوحدة 2: المادة والكيمياء',lessons:[]},{title:'الوحدة 3: الفيزياء والأرض والفضاء',lessons:[]}]});location.reload()}
function saveAdmin(){var n=document.getElementById('eName').value;if(n)document.getElementById('tName').innerText=n;var im=document.getElementById('eImg').value;if(im)document.getElementById('tImg').src=im;alert('تم الحفظ');closeM('adminM')}
loadAll();
</script>
</body>
</html>
