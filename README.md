<!DOCTYPE html>  <html lang="id">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>  
  <title>CBT Python Dasar</title>    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">    <style>  
    *{  
      margin:0;  
      padding:0;  
      box-sizing:border-box;  
      font-family:'Poppins',sans-serif;  
    }  
  
    body{  
      min-height:100vh;  
      background:  
      radial-gradient(circle at top left,#00ffff22,transparent 30%),  
      radial-gradient(circle at bottom right,#0088ff22,transparent 30%),  
      linear-gradient(135deg,#020617,#07142a,#0f172a);  
      color:white;  
      overflow-x:hidden;  
      padding:20px;  
    }  
  
    .container{  
      max-width:1100px;  
      margin:auto;  
    }  
  
    .glass{  
      background:rgba(255,255,255,0.08);  
      border:1px solid rgba(255,255,255,0.12);  
      backdrop-filter:blur(14px);  
      border-radius:24px;  
      box-shadow:  
      0 0 20px rgba(0,255,255,0.15),  
      inset 0 0 15px rgba(255,255,255,0.03);  
    }  
  
    .header{  
      padding:25px;  
      margin-bottom:20px;  
      display:flex;  
      flex-wrap:wrap;  
      gap:20px;  
      justify-content:space-between;  
      align-items:center;  
    }  
  
    .title h1{  
      font-size:2rem;  
      color:#00e5ff;  
      text-shadow:0 0 12px #00e5ff;  
    }  
  
    .title p{  
      opacity:.8;  
      margin-top:5px;  
    }  
  
    .info-box{  
      display:flex;  
      gap:15px;  
      flex-wrap:wrap;  
    }  
  
    .info{  
      padding:12px 18px;  
      border-radius:14px;  
      background:rgba(255,255,255,0.06);  
      border:1px solid rgba(255,255,255,0.1);  
      text-align:center;  
      min-width:120px;  
    }  
  
    .info h3{  
      color:#00ffff;  
      font-size:1rem;  
    }  
  
    .progress-container{  
      margin-top:15px;  
    }  
  
    .progress-bar{  
      width:100%;  
      height:14px;  
      background:#111827;  
      border-radius:20px;  
      overflow:hidden;  
    }  
  
    .progress{  
      height:100%;  
      width:0%;  
      background:linear-gradient(90deg,#00e5ff,#0088ff);  
      box-shadow:0 0 15px #00e5ff;  
      transition:.4s;  
    }  
  
    .quiz-box{  
      padding:30px;  
      animation:fade .4s ease;  
    }  
  
    @keyframes fade{  
      from{  
        opacity:0;  
        transform:translateY(10px);  
      }  
      to{  
        opacity:1;  
        transform:translateY(0);  
      }  
    }  
  
    .question-number{  
      color:#00e5ff;  
      margin-bottom:10px;  
      font-weight:600;  
    }  
  
    .question{  
      font-size:1.25rem;  
      margin-bottom:25px;  
      line-height:1.6;  
    }  
  
    .options{  
      display:grid;  
      gap:15px;  
    }  
  
    .option{  
      padding:15px 18px;  
      border-radius:16px;  
      border:1px solid rgba(255,255,255,0.1);  
      background:rgba(255,255,255,0.05);  
      cursor:pointer;  
      transition:.3s;  
    }  
  
    .option:hover{  
      transform:translateY(-2px);  
      border-color:#00e5ff;  
      box-shadow:0 0 15px rgba(0,229,255,.4);  
    }  
  
    .option.selected{  
      background:rgba(0,229,255,0.2);  
      border-color:#00ffff;  
      box-shadow:0 0 15px #00e5ff;  
    }  
  
    .navigation{  
      margin-top:30px;  
      display:flex;  
      justify-content:space-between;  
      gap:15px;  
      flex-wrap:wrap;  
    }  
  
    .btn{  
      padding:13px 22px;  
      border:none;  
      border-radius:14px;  
      background:linear-gradient(90deg,#00e5ff,#0088ff);  
      color:white;  
      cursor:pointer;  
      font-weight:600;  
      transition:.3s;  
      box-shadow:0 0 15px rgba(0,229,255,.35);  
    }  
  
    .btn:hover{  
      transform:translateY(-3px) scale(1.02);  
      box-shadow:0 0 25px rgba(0,229,255,.6);  
    }  
  
    .question-nav{  
      display:grid;  
      grid-template-columns:repeat(auto-fit,minmax(45px,1fr));  
      gap:10px;  
      margin-top:25px;  
    }  
  
    .nav-btn{  
      height:45px;  
      border:none;  
      border-radius:12px;  
      background:#111827;  
      color:white;  
      cursor:pointer;  
      transition:.3s;  
      border:1px solid rgba(255,255,255,.08);  
    }  
  
    .nav-btn:hover{  
      border-color:#00e5ff;  
    }  
  
    .nav-btn.answered{  
      background:#00bcd4;  
      color:black;  
      font-weight:bold;  
    }  
  
    .nav-btn.active{  
      border:2px solid #00ffff;  
      box-shadow:0 0 15px #00ffff;  
    }  
  
    .result-box{  
      padding:40px;  
      text-align:center;  
      display:none;  
      animation:fade .5s ease;  
    }  
  
    .score{  
      font-size:4rem;  
      color:#00ffff;  
      text-shadow:0 0 20px #00ffff;  
    }  
  
    .grade{  
      font-size:2rem;  
      margin:10px 0;  
      color:#00e5ff;  
    }  
  
    .stats{  
      margin-top:20px;  
      display:grid;  
      grid-template-columns:repeat(auto-fit,minmax(180px,1fr));  
      gap:20px;  
    }  
  
    .stat{  
      padding:20px;  
      border-radius:18px;  
      background:rgba(255,255,255,0.05);  
    }  
  
    .motivation{  
      margin-top:25px;  
      font-size:1.1rem;  
      color:#d1f5ff;  
    }  
  
    @media(max-width:768px){  
      .title h1{  
        font-size:1.5rem;  
      }  
  
      .question{  
        font-size:1rem;  
      }  
  
      .header{  
        flex-direction:column;  
        align-items:flex-start;  
      }  
  
      .info-box{  
        width:100%;  
      }  
  
      .info{  
        flex:1;  
      }  
    }  
  
  </style>  </head>  
<body>  <div class="container">    <div class="header glass">  
    <div class="title">  
      <h1>CBT Koding & Kecerdasan Artifisial</h1>  
      <p>Python Dasar • 50 Soal Pilihan Ganda</p>  <div class="progress-container">  
    <div class="progress-bar">  
      <div class="progress" id="progress"></div>  
    </div>  
  </div>  
</div>  

<div class="info-box">  
  <div class="info">  
    <h3>Total Soal</h3>  
    <p>50</p>  
  </div>  

  <div class="info">  
    <h3>Timer</h3>  
    <p id="timer">60:00</p>  
  </div>  

  <div class="info">  
    <h3>Progress</h3>  
    <p id="progressText">0 / 50</p>  
  </div>  
</div>

  </div>    <div class="quiz-box glass" id="quizBox">  <div class="question-number" id="questionNumber"></div>  

<div class="question" id="question"></div>  

<div class="options" id="options"></div>  

<div class="navigation">  
  <button class="btn" onclick="prevQuestion()">Previous</button>  
  <button class="btn" onclick="nextQuestion()">Next</button>  
  <button class="btn" onclick="finishExam()">Selesai</button>  
</div>  

<div class="question-nav" id="questionNav"></div>

  </div>    <div class="result-box glass" id="resultBox">  <h1>Hasil Ujian</h1>  

<div class="score" id="scoreText">0</div>  

<div class="grade" id="gradeText">Grade A</div>  

<div class="stats">  

  <div class="stat">  
    <h3>Benar</h3>  
    <p id="correctText">0</p>  
  </div>  

  <div class="stat">  
    <h3>Salah</h3>  
    <p id="wrongText">0</p>  
  </div>  

  <div class="stat">  
    <h3>Persentase</h3>  
    <p id="percentageText">0%</p>  
  </div>  

</div>  

<div class="motivation" id="motivation"></div>

  </div>  </div>  <script>  
  
const questions = [  
{  
question:"Siapa pencipta Python?",  
options:["James Gosling","Guido van Rossum","Dennis Ritchie","Bjarne Stroustrup"],  
answer:"Guido van Rossum"  
},  
{  
question:"Python pertama kali dirilis tahun?",  
options:["1989","1991","1995","2000"],  
answer:"1991"  
},  
{  
question:"Nama Python berasal dari?",  
options:["Jenis ular","Monty Python","Nama kota","Nama ilmuwan"],  
answer:"Monty Python"  
},  
{  
question:"Warna logo Python adalah?",  
options:["Merah dan putih","Hitam dan putih","Biru dan kuning","Hijau dan hitam"],  
answer:"Biru dan kuning"  
},  
{  
question:"Ekstensi file Python adalah?",  
options:[".html",".js",".py",".exe"],  
answer:".py"  
},  
{  
question:"Simbol komentar pada Python adalah?",  
options:["//","<!--","#","**"],  
answer:"#"  
},  
{  
question:"Python menggunakan apa untuk blok kode?",  
options:["Kurung","Titik koma","Indentasi","Petik"],  
answer:"Indentasi"  
},  
{  
question:"Apa arti Python case sensitive?",  
options:["Huruf besar dan kecil dibedakan","Tidak ada error","Harus pakai angka","Tidak mendukung variabel"],  
answer:"Huruf besar dan kecil dibedakan"  
},  
{  
question:"Variabel yang valid pada Python adalah?",  
options:["1nama","nama-user","namaUser","class"],  
answer:"namaUser"  
},  
{  
question:"Tipe data dari angka 10 adalah?",  
options:["String","Float","Boolean","Integer"],  
answer:"Integer"  
},  
{  
question:"Tipe data dari 3.14 adalah?",  
options:["Float","Integer","String","Boolean"],  
answer:"Float"  
},  
{  
question:"Tipe data dari 'Halo' adalah?",  
options:["Integer","String","Boolean","Float"],  
answer:"String"  
},  
{  
question:"Nilai boolean terdiri dari?",  
options:["Ya dan Tidak","1 dan 2","True dan False","On dan Off"],  
answer:"True dan False"  
},  
{  
question:"Fungsi type() digunakan untuk?",  
options:["Menghapus data","Melihat tipe data","Mencetak teks","Menginput data"],  
answer:"Melihat tipe data"  
},  
{  
question:"Hasil int('10') adalah?",  
options:["'10'","10","10.0","Error"],  
answer:"10"  
},  
{  
question:"Operator pangkat pada Python adalah?",  
options:["^","//","**","%%"],  
answer:"**"  
},  
{  
question:"Hasil 2 ** 4 adalah?",  
options:["8","16","12","14"],  
answer:"16"  
},  
{  
question:"Hasil 10 % 4 adalah?",  
options:["2","4","1","0"],  
answer:"2"  
},  
{  
question:"Operator and digunakan untuk?",  
options:["Perkalian","Pengurangan","Logika DAN","Logika TIDAK"],  
answer:"Logika DAN"  
},  
{  
question:"Fungsi operator += adalah?",  
options:["Mengurangi nilai","Menambah dan menyimpan","Membagi","Membandingkan"],  
answer:"Menambah dan menyimpan"  
},  
{  
question:"Operator perbandingan digunakan untuk?",  
options:["Mengulang","Membandingkan nilai","Menyimpan data","Input data"],  
answer:"Membandingkan nilai"  
},  
{  
question:"Percabangan utama pada Python menggunakan?",  
options:["switch","if","goto","break"],  
answer:"if"  
},  
{  
question:"elif digunakan untuk?",  
options:["Kondisi tambahan","Mengulang","Menghapus","Input"],  
answer:"Kondisi tambahan"  
},  
{  
question:"else dijalankan ketika?",  
options:["Kondisi benar","Semua kondisi salah","Program error","Input kosong"],  
answer:"Semua kondisi salah"  
},  
{  
question:"Fungsi if adalah?",  
options:["Perulangan","Percabangan","Input","Komentar"],  
answer:"Percabangan"  
},  
{  
question:"Loop untuk mengulang data tertentu adalah?",  
options:["if","for","else","print"],  
answer:"for"  
},  
{  
question:"while digunakan ketika?",  
options:["Mengulang selama kondisi benar","Input data","Menghapus data","Membuat variabel"],  
answer:"Mengulang selama kondisi benar"  
},  
{  
question:"range() digunakan untuk?",  
options:["Input","Rentang angka","Komentar","Output"],  
answer:"Rentang angka"  
},  
{  
question:"Infinite loop adalah?",  
options:["Loop berhenti","Loop tanpa akhir","Loop error","Loop cepat"],  
answer:"Loop tanpa akhir"  
},  
{  
question:"print() digunakan untuk?",  
options:["Input","Mencetak output","Menghapus","Membandingkan"],  
answer:"Mencetak output"  
},  
{  
question:"input() digunakan untuk?",  
options:["Output","Percabangan","Menerima input user","Loop"],  
answer:"Menerima input user"  
},  
{  
question:"Tipe data default dari input() adalah?",  
options:["Integer","Boolean","String","Float"],  
answer:"String"  
},  
{  
question:"Manakah operator pembagian?",  
options:["*","/","+","%"],  
answer:"/"  
},  
{  
question:"Manakah operator perkalian?",  
options:["*","/","-","+"],  
answer:"*"  
},  
{  
question:"Komentar pada Python tidak akan?",  
options:["Dieksekusi","Ditampilkan","Dibaca programmer","Ditulis"],  
answer:"Dieksekusi"  
},  
{  
question:"Apa fungsi indentasi?",  
options:["Mempercantik","Menentukan blok kode","Menambah variabel","Menghapus data"],  
answer:"Menentukan blok kode"  
},  
{  
question:"Apa hasil type(5)?",  
options:["float","int","str","bool"],  
answer:"int"  
},  
{  
question:"Apa hasil type(True)?",  
options:["bool","int","float","str"],  
answer:"bool"  
},  
{  
question:"Hasil 5 > 3 adalah?",  
options:["False","0","Error","True"],  
answer:"True"  
},  
{  
question:"Operator not digunakan untuk?",  
options:["Membalik logika","Menambah","Membagi","Mengulang"],  
answer:"Membalik logika"  
},  
{  
question:"Apa hasil 4 + 6?",  
options:["8","9","10","12"],  
answer:"10"  
},  
{  
question:"Apa hasil 12 - 5?",  
options:["5","6","7","8"],  
answer:"7"  
},  
{  
question:"Apa hasil 3 * 4?",  
options:["7","9","12","15"],  
answer:"12"  
},  
{  
question:"Apa hasil 8 / 2?",  
options:["2","4","6","8"],  
answer:"4"  
},  
{  
question:"Python termasuk bahasa?",  
options:["Pemrograman","Musik","Game","Desain"],  
answer:"Pemrograman"  
},  
{  
question:"Python terkenal karena syntax yang?",  
options:["Rumit","Sulit","Sederhana","Panjang"],  
answer:"Sederhana"  
},  
{  
question:"Manakah yang termasuk float?",  
options:["10","2.5","True","'Halo'"],  
answer:"2.5"  
},  
{  
question:"Manakah yang termasuk string?",  
options:["100","False","'Python'","3.14"],  
answer:"'Python'"  
},  
{  
question:"Apa fungsi else pada percabangan?",  
options:["Mengulang","Pilihan terakhir","Input","Komentar"],  
answer:"Pilihan terakhir"  
},  
{  
question:"Loop tanpa kondisi berhenti disebut?",  
options:["for loop","nested loop","infinite loop","range loop"],  
answer:"infinite loop"  
},  
{  
question:"Apa fungsi variabel?",  
options:["Menyimpan data","Menghapus data","Mencetak data","Mengulang"],  
answer:"Menyimpan data"  
}  
];  
  
// RANDOM SOAL  
questions.sort(() => Math.random() - 0.5);  
  
let currentQuestion = 0;  
let answers = new Array(questions.length).fill(null);  
  
const questionElement = document.getElementById("question");  
const optionsElement = document.getElementById("options");  
const questionNumber = document.getElementById("questionNumber");  
const questionNav = document.getElementById("questionNav");  
  
function loadQuestion(){  
  
  const q = questions[currentQuestion];  
  
  questionNumber.innerHTML = `Soal ${currentQuestion + 1} dari ${questions.length}`;  
  questionElement.innerHTML = q.question;  
  
  optionsElement.innerHTML = "";  
  
  q.options.forEach(option => {  
  
    const div = document.createElement("div");  
    div.classList.add("option");  
  
    if(answers[currentQuestion] === option){  
      div.classList.add("selected");  
    }  
  
    div.innerHTML = option;  
  
    div.onclick = () => {  
      answers[currentQuestion] = option;  
      loadQuestion();  
      updateProgress();  
    };  
  
    optionsElement.appendChild(div);  
  
  });  
  
  renderQuestionNav();  
  
}  
  
function renderQuestionNav(){  
  
  questionNav.innerHTML = "";  
  
  questions.forEach((_,index)=>{  
  
    const btn = document.createElement("button");  
  
    btn.classList.add("nav-btn");  
  
    if(answers[index]){  
      btn.classList.add("answered");  
    }  
  
    if(index === currentQuestion){  
      btn.classList.add("active");  
    }  
  
    btn.innerText = index + 1;  
  
    btn.onclick = () => {  
      currentQuestion = index;  
      loadQuestion();  
    };  
  
    questionNav.appendChild(btn);  
  
  });  
  
}  
  
function nextQuestion(){  
  if(currentQuestion < questions.length - 1){  
    currentQuestion++;  
    loadQuestion();  
  }  
}  
  
function prevQuestion(){  
  if(currentQuestion > 0){  
    currentQuestion--;  
    loadQuestion();  
  }  
}  
  
function updateProgress(){  
  
  const answered = answers.filter(a => a !== null).length;  
  
  const percent = (answered / questions.length) * 100;  
  
  document.getElementById("progress").style.width = percent + "%";  
  
  document.getElementById("progressText").innerText =  
  `${answered} / ${questions.length}`;  
  
}  
  
// TIMER  
let time = 60 * 60;  
  
const timerElement = document.getElementById("timer");  
  
const timer = setInterval(()=>{  
  
  let minutes = Math.floor(time / 60);  
  let seconds = time % 60;  
  
  timerElement.innerText =  
  `${String(minutes).padStart(2,"0")}:${String(seconds).padStart(2,"0")}`;  
  
  time--;  
  
  if(time < 0){  
    clearInterval(timer);  
    finishExam(true);  
  }  
  
},1000);  
  
function finishExam(auto=false){  
  
  const unanswered = answers.filter(a => a === null).length;  
  
  if(unanswered > 0 && !auto){  
  
    const confirmFinish = confirm(  
      `Masih ada ${unanswered} soal belum dijawab. Yakin ingin selesai?`  
    );  
  
    if(!confirmFinish){  
      return;  
    }  
  
  }  
  
  clearInterval(timer);  
  
  let correct = 0;  
  
  questions.forEach((q,index)=>{  
    if(answers[index] === q.answer){  
      correct++;  
    }  
  });  
  
  const wrong = questions.length - correct;  
  
  const percentage = Math.round((correct / questions.length) * 100);  
  
  let grade = "";  
  
  if(percentage >= 90){  
    grade = "A";  
  }else if(percentage >= 80){  
    grade = "B";  
  }else if(percentage >= 70){  
    grade = "C";  
  }else{  
    grade = "D";  
  }  
  
  let motivation = "";  
  
  if(grade === "A"){  
    motivation = "🔥 Luar biasa! Kamu sangat menguasai Python dasar!";  
  }else if(grade === "B"){  
    motivation = "✨ Kerja bagus! Tinggal sedikit lagi menuju sempurna.";  
  }else if(grade === "C"){  
    motivation = "👍 Cukup baik! Terus latihan agar lebih mahir.";  
  }else{  
    motivation = "💪 Jangan menyerah! Belajar lagi dan coba kembali.";  
  }  
  
  document.getElementById("quizBox").style.display = "none";  
  document.getElementById("resultBox").style.display = "block";  
  
  document.getElementById("scoreText").innerText = percentage;  
  document.getElementById("gradeText").innerText = `Grade ${grade}`;  
  document.getElementById("correctText").innerText = correct;  
  document.getElementById("wrongText").innerText = wrong;  
  document.getElementById("percentageText").innerText = percentage + "%";  
  document.getElementById("motivation").innerText = motivation;  
  
}  
  
loadQuestion();  
updateProgress();  
  
</script>  </body>  
</html>  
