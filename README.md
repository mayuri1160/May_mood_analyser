# May_mood_analyser
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>May — Pastel Mood Analyser</title>
<style>
  :root{
    --bg: #fdfaff;
    --card: #ffffff;
    --muted: #7a7a8c;
    --radius: 18px;
    --shadow: 0 8px 30px rgba(184, 175, 255, 0.25);
    --smooth: 220ms cubic-bezier(.2,.9,.3,1);
  }

  body{
    margin:0;
    background:var(--bg);
    font-family: "Poppins", sans-serif;
    display:flex;
    justify-content:center;
    align-items:center;
    min-height:100vh;
    padding:24px;
  }

  .card{
    width:100%;
    max-width:520px;
    background:var(--card);
    border-radius:var(--radius);
    padding:28px;
    box-shadow:var(--shadow);
    border:1px solid rgba(255,255,255,0.9);
  }

  h1{
    margin:0 0 8px 0;
    font-size:22px;
    font-weight:600;
    color:#5d4dbd;
  }

  p.lead{
    margin:0 0 16px 0;
    font-size:14px;
    color:var(--muted);
  }

  .input-row{
    display:flex;
    gap:10px;
    margin-bottom:16px;
  }

  input{
    flex:1;
    padding:12px 16px;
    border-radius:14px;
    border:1px solid #e2dafe;
    background:#faf7ff;
    font-size:15px;
    outline:none;
    transition:var(--smooth);
  }
  input:focus{
    border-color:#c0b0ff;
    box-shadow:0 0 0 3px rgba(192,176,255,0.35);
  }

  button{
    padding:12px 16px;
    border-radius:14px;
    border:0;
    background:#b49bff;
    color:white;
    font-size:14px;
    font-weight:600;
    cursor:pointer;
    box-shadow:0 6px 20px rgba(180,155,255,0.4);
    transition:var(--smooth);
  }
  button:active{
    transform:translateY(1px);
    box-shadow:none;
  }

  .result{
    margin-top:20px;
    padding:16px;
    border-radius:14px;
    display:flex;
    gap:12px;
    align-items:center;
    background:#f6f1ff;
    min-height:70px;
    animation: pop .3s ease;
  }

  .emoji{
    font-size:30px;
    width:50px;
    height:50px;
    display:flex;
    align-items:center;
    justify-content:center;
    border-radius:12px;
    background:white;
    box-shadow:0 3px 8px rgba(0,0,0,0.05);
  }

  .text .title{
    font-weight:700;
    margin-bottom:4px;
    font-size:16px;
  }
  .text .sub{
    color:var(--muted);
    font-size:13px;
  }

  @keyframes pop {
    0% { transform: scale(0.9); opacity: 0.4; }
    100% { transform: scale(1); opacity: 1; }
  }
</style>
</head>
<body>
<div class="card">
  <h1>May — Pastel Mood Analyser</h1>
  <p class="lead">Type how you feel (happy, sad, excited, thakle, khushi).</p>

  <div class="input-row">
    <input id="moodInput" type="text" placeholder="Type your mood..." />
    <button id="analyzeBtn">Analyze</button>
  </div>

  <div id="result" class="result" hidden>
    <div class="emoji" id="emoji">🙂</div>
    <div class="text">
      <div class="title" id="resultTitle">Mood Result</div>
      <div class="sub" id="resultSub">Message appears here</div>
    </div>
  </div>
</div>

<script>
const moods = [
  {keys:["happy","khush","khushi"], emoji:"😊", title:"Tumhi happy ahat!", sub:"Love your vibe!", color:"#e8fff3"},
  {keys:["sad","dukhi"], emoji:"😔", title:"Thoda dukhi vatat aahe", sub:"Sending you a warm hug.", color:"#eaf3ff"},
  {keys:["excited","josh"], emoji:"🤩", title:"Woah! Excited mood!", sub:"Enjoy that energy!", color:"#fff3e6"},
  {keys:["tired","thak","thakle"], emoji:"😴", title:"Thakle ahat ka?", sub:"A little rest helps.", color:"#f9f9f9"},
  {keys:["angry","rag"], emoji:"😡", title:"Thoda shant raha", sub:"Deep breath.", color:"#ffecec"},
];

const def = {emoji:"🤔", title:"Interesting mood!", sub:"Every feeling matters.", color:"#ffffff"};

function analyze(t){
  t = t.toLowerCase();
  for(const m of moods){
    for(const k of m.keys){
      if(t.includes(k)) return m;
    }
  }
  return def;
}

const input = document.getElementById("moodInput");
const result = document.getElementById("result");
const emoji = document.getElementById("emoji");
const title = document.getElementById("resultTitle");
const sub = document.getElementById("resultSub");

document.getElementById("analyzeBtn").onclick = () => {
  if(!input.value.trim()) return;
  const m = analyze(input.value);
  emoji.textContent = m.emoji;
  title.textContent = m.title;
  sub.textContent = m.sub;
  result.style.background = m.color;
  result.hidden = false;
};
</script>
</body>
</html>


---

