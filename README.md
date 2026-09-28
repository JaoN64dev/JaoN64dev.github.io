# JaoN64dev.github.io
<html lang="en"><head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Road to OBMEP 2027</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="">
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,500;12..96,700;12..96,800&amp;family=Atkinson+Hyperlegible:wght@400;700&amp;display=swap" rel="stylesheet">
<style>
:root{
  --paper:#FBFCF7; --grid:rgba(40,80,160,.075); --ink:#1B2F6B; --text:#1D2433; --muted:#5B6477;
  --hi:#F4D03F; --hi-soft:rgba(244,208,63,.45); --red:#C23B2E; --line:#D6DCE8; --done:#2E7D5B; --field:#FFFFFF;
  --display:"Bricolage Grotesque", "Segoe UI", system-ui, sans-serif;
  --body:"Atkinson Hyperlegible", "Segoe UI", system-ui, sans-serif;
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px); padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme: dark){
  :root:not([data-theme="light"]){
    --paper:#17221F; --grid:rgba(255,255,255,.035); --ink:#B9CCFF; --text:#E6ECE8; --muted:#9AA8A2;
    --hi:#E9C84A; --hi-soft:rgba(233,200,74,.28); --red:#F07A6A; --line:#2E3D38; --done:#6CCB9B; --field:#1D2A26;
  }
}
:root[data-theme="dark"]{
  --paper:#17221F; --grid:rgba(255,255,255,.035); --ink:#B9CCFF; --text:#E6ECE8; --muted:#9AA8A2;
  --hi:#E9C84A; --hi-soft:rgba(233,200,74,.28); --red:#F07A6A; --line:#2E3D38; --done:#6CCB9B; --field:#1D2A26;
}
*,*::before,*::after{box-sizing:inherit}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{
  margin:0; background-color:var(--paper); color:var(--text); font:17px/1.55 var(--body);
  background-image:linear-gradient(var(--grid) 1px,transparent 1px),linear-gradient(90deg,var(--grid) 1px,transparent 1px);
  background-size:24px 24px;
}
.wrap{max-width:860px; margin:0 auto; padding:32px 20px 64px}
h1{font:800 clamp(2.2rem,7vw,3.6rem)/1 var(--display); color:var(--ink); margin:0 0 8px; letter-spacing:-.02em}
h2{font:700 1.5rem/1.2 var(--display); color:var(--ink); margin:0 0 4px}
h3{font:700 1.15rem/1.25 var(--display); margin:0}
p{margin:0 0 12px}
.lede{color:var(--muted); max-width:60ch}
a{color:var(--ink)}
button,input,select,textarea{font:inherit; color:inherit}
:focus-visible{outline:3px solid var(--hi); outline-offset:2px}

/* timeline ruler */
.ruler{margin:28px 0 8px; position:relative}
.bar{display:flex; height:44px; border:2px solid var(--ink); border-radius:4px; overflow:hidden; background:var(--field)}
.seg{position:relative; border-right:2px solid var(--ink); overflow:hidden}
.seg:last-child{border-right:0}
.seg .fill{position:absolute; inset:0 auto 0 0; background:var(--hi-soft)}
.seg.now{background:repeating-linear-gradient(-45deg,transparent 0 6px,var(--hi-soft) 6px 8px)}
.seg span{position:relative; display:block; padding:4px 6px; font:700 .8rem/1.1 var(--display); color:var(--ink); white-space:nowrap}
.marker{position:absolute; top:-10px; bottom:-10px; width:3px; background:var(--red); transform:translateX(-1px)}
.marker b{position:absolute; top:-22px; left:50%; transform:translateX(-50%); font:700 .75rem var(--display); color:var(--red); white-space:nowrap}
.months{display:flex; justify-content:space-between; color:var(--muted); font-size:.8rem; margin-top:6px}
.facts{display:flex; flex-wrap:wrap; gap:8px 24px; margin:18px 0 0; color:var(--muted)}
.facts strong{color:var(--text)}

/* tabs */
.tabs{display:flex; gap:4px; margin:36px 0 20px; border-bottom:2px solid var(--line); overflow-x:auto}
.tab{background:none; border:0; padding:10px 14px; cursor:pointer; font:700 1rem var(--display); color:var(--muted); border-bottom:3px solid transparent; margin-bottom:-2px; white-space:nowrap}
.tab[aria-selected="true"]{color:var(--ink); border-bottom-color:var(--hi)}
.panel[hidden]{display:none}

/* phases */
.phase{padding:20px 0; border-top:1px dashed var(--line)}
.phase:first-child{border-top:0; padding-top:4px}
.phase-head{display:grid; grid-template-columns:auto 1fr auto; gap:14px; align-items:baseline}
.num{font:800 1.8rem/1 var(--display); color:var(--ink); min-width:1.4em}
.dates{color:var(--muted); font-size:.9rem}
.pct{font:700 .9rem var(--display); color:var(--done)}
.phase .why{color:var(--muted); margin:6px 0 10px calc(1.4em * 1.8 + 14px); font-size:.95rem}
.tasks{list-style:none; margin:0 0 0 calc(1.4em * 1.8 + 14px); padding:0}
.tasks li{margin:2px 0}
.tasks label{display:flex; gap:10px; align-items:flex-start; cursor:pointer; padding:4px 0}
.tasks input{width:20px; height:20px; margin-top:3px; accent-color:var(--done); flex:none}
.tasks input:checked + span{color:var(--muted); text-decoration:line-through; text-decoration-color:var(--done)}
@media (max-width:560px){ .phase .why,.tasks{margin-left:0} }

/* forms */
.row{display:flex; flex-wrap:wrap; gap:10px; align-items:flex-end; margin-bottom:12px}
.field{display:flex; flex-direction:column; gap:4px; font-size:.85rem; color:var(--muted)}
.field input,.field select,.field textarea{background:var(--field); border:1.5px solid var(--line); border-radius:4px; padding:8px 10px; font-size:1rem; color:var(--text)}
.field textarea{min-height:84px; resize:vertical; width:100%}
.grow{flex:1 1 220px}
.btn{background:var(--ink); color:var(--paper); border:0; border-radius:4px; padding:10px 16px; font:700 1rem var(--display); cursor:pointer}
.btn:hover{filter:brightness(1.1)}
.x{background:none; border:0; color:var(--muted); cursor:pointer; font-size:.85rem; padding:4px 6px; text-decoration:underline}
.x:hover{color:var(--red)}

/* log */
.week{display:flex; align-items:baseline; gap:12px; flex-wrap:wrap; margin:4px 0 14px}
.week .big{font:800 2.2rem/1 var(--display); color:var(--ink)}
.meter{height:10px; background:var(--field); border:1.5px solid var(--line); border-radius:6px; overflow:hidden; margin-bottom:20px}
.meter i{display:block; height:100%; background:var(--hi)}
.weeks{display:flex; gap:4px; align-items:flex-end; height:70px; margin:8px 0 4px}
.weeks div{flex:1; background:var(--ink); opacity:.75; border-radius:2px 2px 0 0; min-height:2px}
.weeks div.met{background:var(--done); opacity:1}
.small{font-size:.85rem; color:var(--muted)}
.entries{list-style:none; padding:0; margin:16px 0 0}
.entries li{display:grid; grid-template-columns:auto 1fr auto; gap:12px; padding:10px 0; border-bottom:1px solid var(--line); align-items:baseline}
.entries .when{font:700 .9rem var(--display); color:var(--ink); min-width:5.5em}
.entries .what small{display:block; color:var(--muted)}
.tag{display:inline-block; font-size:.78rem; padding:1px 8px; border-radius:10px; background:var(--hi-soft); color:var(--text); margin-right:6px}
.empty{color:var(--muted); font-style:italic; padding:12px 0}

/* notebook */
.note{padding:14px 0 14px 16px; border-left:4px solid var(--hi); margin:12px 0; background:linear-gradient(90deg,var(--hi-soft),transparent 60%)}
.note p{white-space:pre-wrap; margin:6px 0 0}
.filters{display:flex; gap:6px; flex-wrap:wrap; margin:18px 0 4px}
.chip{background:none; border:1.5px solid var(--line); border-radius:14px; padding:3px 12px; cursor:pointer; font-size:.85rem}
.chip[aria-pressed="true"]{background:var(--ink); color:var(--paper); border-color:var(--ink)}

/* resources */
.res{padding:14px 0; border-bottom:1px solid var(--line)}
.res h3 a{text-decoration-color:var(--hi); text-decoration-thickness:3px; text-underline-offset:3px}
.res p{color:var(--muted); margin:4px 0 0}

.status{position:fixed; right:12px; bottom:calc(12px + env(safe-area-inset-bottom,0px)); font-size:.8rem; background:var(--field); border:1px solid var(--line); border-radius:12px; padding:4px 10px; color:var(--muted)}
@media (prefers-reduced-motion:no-preference){ .meter i,.seg .fill{transition:width .4s ease} }
</style>
<style type="text/css">
.vfm--fixed[data-v-2836fdb5] {
  position: fixed;
}
.vfm--absolute[data-v-2836fdb5] {
  position: absolute;
}
.vfm--inset[data-v-2836fdb5] {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}
.vfm--overlay[data-v-2836fdb5] {
  background-color: rgba(0, 0, 0, 0.5);
}
.vfm--prevent-none[data-v-2836fdb5] {
  pointer-events: none;
}
.vfm--prevent-auto[data-v-2836fdb5] {
  pointer-events: auto;
}
.vfm--outline-none[data-v-2836fdb5]:focus {
  outline: none;
}
.vfm-enter-active[data-v-2836fdb5],
.vfm-leave-active[data-v-2836fdb5] {
  transition: opacity 0.2s;
}
.vfm-enter-from[data-v-2836fdb5],
.vfm-leave-to[data-v-2836fdb5] {
  opacity: 0;
}
.vfm--touch-none[data-v-2836fdb5] {
  touch-action: none;
}
.vfm--select-none[data-v-2836fdb5] {
  -webkit-user-select: none;
     -moz-user-select: none;
      -ms-user-select: none;
          user-select: none;
}
.vfm--resize-tr[data-v-2836fdb5],
.vfm--resize-br[data-v-2836fdb5],
.vfm--resize-bl[data-v-2836fdb5],
.vfm--resize-tl[data-v-2836fdb5] {
  width: 12px;
  height: 12px;
  z-index: 10;
}
.vfm--resize-t[data-v-2836fdb5] {
  top: -6px;
  left: 0;
  width: 100%;
  height: 12px;
  cursor: ns-resize;
}
.vfm--resize-tr[data-v-2836fdb5] {
  top: -6px;
  right: -6px;
  cursor: nesw-resize;
}
.vfm--resize-r[data-v-2836fdb5] {
  top: 0;
  right: -6px;
  width: 12px;
  height: 100%;
  cursor: ew-resize;
}
.vfm--resize-br[data-v-2836fdb5] {
  bottom: -6px;
  right: -6px;
  cursor: nwse-resize;
}
.vfm--resize-b[data-v-2836fdb5] {
  bottom: -6px;
  left: 0;
  width: 100%;
  height: 12px;
  cursor: ns-resize;
}
.vfm--resize-bl[data-v-2836fdb5] {
  bottom: -6px;
  left: -6px;
  cursor: nesw-resize;
}
.vfm--resize-l[data-v-2836fdb5] {
  top: 0;
  left: -6px;
  width: 12px;
  height: 100%;
  cursor: ew-resize;
}
.vfm--resize-tl[data-v-2836fdb5] {
  top: -6px;
  left: -6px;
  cursor: nwse-resize;
}
</style><style type="text/css">x-vue-echarts{display:block;width:100%;height:100%;min-width:0}
</style><link rel="stylesheet" href="chrome-extension://lkhiljgmbeecmljiogckofcalncmfnfo/assets/browser.css"><link rel="preconnect" href="https://migaku-public-data.migaku.com" crossorigin="anonymous"><link rel="preload" href="https://migaku-public-data.migaku.com/fonts/inter/InterVariable.woff2?v=4.0" as="font" type="font/woff" crossorigin="anonymous"><link rel="preload" href="https://migaku-public-data.migaku.com/fonts/gt-maru/GT-Maru-Black.woff2" as="font" type="font/woff" crossorigin="anonymous"><link rel="preconnect" href="https://migaku-public-data.migaku.com" crossorigin="anonymous"><link rel="preload" href="https://migaku-public-data.migaku.com/fonts/noto-sans-jp/noto-sans-jp-latin-ext-400-normal.woff2" as="font" type="font/woff2" crossorigin="anonymous"><link rel="preload" href="https://migaku-public-data.migaku.com/fonts/noto-sans-jp/noto-sans-jp-japanese-400-normal.woff2" as="font" type="font/woff2" crossorigin="anonymous"></head>
<body><div id="MigakuShadowDom" data-mgk-ready="false" data-mgk-lang-selected="ja" data-mgk-interface-lang="en" data-mgk-app-open="false"></div>
<div class="wrap">
  <h1>Road to OBMEP 2027</h1>
  <p class="lede">Nível 3 study plan. Tick off topics as you learn them, log your study time, and keep a notebook of the tricks you pick up.</p>

  <div class="ruler" aria-label="Timeline">
    <div class="bar" id="bar"><div class="seg" style="width:23.618090452261306%" title="Foundations"><div class="fill" style="width:0%"></div><span>Foundations</span></div><div class="seg" style="width:14.572864321608039%" title="Geometry and algebra"><div class="fill" style="width:0%"></div><span>Geometry and algebra</span></div><div class="seg" style="width:15.07537688442211%" title="Mixed problems"><div class="fill" style="width:0%"></div><span>Mixed problems</span></div><div class="seg" style="width:7.788944723618091%" title="Exam simulation"><div class="fill" style="width:0%"></div><span></span></div><div class="seg" style="width:38.19095477386934%" title="Second phase"><div class="fill" style="width:0%"></div><span>Second phase</span></div></div>
    <div class="marker" id="marker" style="left: 0%;"><b>You are here</b></div>
    <div class="months"><span>Oct 2026</span><span>Jan</span><span>Mar</span><span>Jun</span><span>Oct 2027</span></div>
  </div>
  <div class="facts" id="facts"><span><strong>247</strong> days to the first phase</span><span><strong>0/36</strong> plan items done</span><span><strong>0m</strong> studied so far</span><label>First phase date: <input type="date" id="examDate" value="2027-06-01" style="font-size:.9rem"> <span class="small">(estimate; update when the calendar is out)</span></label></div>

  <div class="tabs" role="tablist">
    <button class="tab" role="tab" aria-selected="true" data-tab="plan">Plan</button>
    <button class="tab" role="tab" aria-selected="false" data-tab="log">Study log</button>
    <button class="tab" role="tab" aria-selected="false" data-tab="notes">Notebook</button>
    <button class="tab" role="tab" aria-selected="false" data-tab="res">Resources</button>
  </div>

  <section class="panel" id="plan" role="tabpanel"><div class="phase">
      <div class="phase-head"><span class="num">1</span><div><h3>Foundations</h3><div class="dates">Now – December · 28 Sept to 31 Dec</div></div><span class="pct">0%</span></div>
      <p class="why">Number theory and counting show up constantly in OBMEP and reward practice. About 4–5 hours a week.</p>
      <ul class="tasks"><li><label><input type="checkbox" data-k="p1-0"><span>Divisibility and divisibility rules</span></label></li><li><label><input type="checkbox" data-k="p1-1"><span>Primes and prime factorization</span></label></li><li><label><input type="checkbox" data-k="p1-2"><span>GCD and LCM</span></label></li><li><label><input type="checkbox" data-k="p1-3"><span>Remainders and basic modular arithmetic</span></label></li><li><label><input type="checkbox" data-k="p1-4"><span>Read the first chapters of Iniciação à Aritmética</span></label></li><li><label><input type="checkbox" data-k="p1-5"><span>Multiplication principle</span></label></li><li><label><input type="checkbox" data-k="p1-6"><span>Permutations and combinations</span></label></li><li><label><input type="checkbox" data-k="p1-7"><span>Pigeonhole principle</span></label></li><li><label><input type="checkbox" data-k="p1-8"><span>Try one old Nível 3 first-phase exam, no time limit</span></label></li></ul>
    </div><div class="phase">
      <div class="phase-head"><span class="num">2</span><div><h3>Geometry and algebra</h3><div class="dates">January – February · 1 Jan to 28 Feb</div></div><span class="pct">0%</span></div>
      <p class="why">Use the school break to study a bit more each week. Keep doing a few number theory and counting problems so they stay fresh.</p>
      <ul class="tasks"><li><label><input type="checkbox" data-k="p2-0"><span>Angles, parallel lines and triangles</span></label></li><li><label><input type="checkbox" data-k="p2-1"><span>Similar triangles and Pythagoras</span></label></li><li><label><input type="checkbox" data-k="p2-2"><span>Areas of polygons</span></label></li><li><label><input type="checkbox" data-k="p2-3"><span>Circles and inscribed angles</span></label></li><li><label><input type="checkbox" data-k="p2-4"><span>Factoring and notable products</span></label></li><li><label><input type="checkbox" data-k="p2-5"><span>Equations and systems</span></label></li><li><label><input type="checkbox" data-k="p2-6"><span>Basic inequalities (AM–GM)</span></label></li><li><label><input type="checkbox" data-k="p2-7"><span>Probability basics (Métodos de Contagem e Probabilidade)</span></label></li></ul>
    </div><div class="phase">
      <div class="phase-head"><span class="num">3</span><div><h3>Mixed problems</h3><div class="dates">March – April · 1 Mar to 30 Apr</div></div><span class="pct">0%</span></div>
      <p class="why">Stop studying by topic. Mixed sets are what the real exam feels like.</p>
      <ul class="tasks"><li><label><input type="checkbox" data-k="p3-0"><span>Old first-phase exam #1</span></label></li><li><label><input type="checkbox" data-k="p3-1"><span>Old first-phase exam #2</span></label></li><li><label><input type="checkbox" data-k="p3-2"><span>Old first-phase exam #3</span></label></li><li><label><input type="checkbox" data-k="p3-3"><span>Old first-phase exam #4</span></label></li><li><label><input type="checkbox" data-k="p3-4"><span>Old first-phase exam #5</span></label></li><li><label><input type="checkbox" data-k="p3-5"><span>Work through one Banco de Questões</span></label></li><li><label><input type="checkbox" data-k="p3-6"><span>Review the notebook every week</span></label></li></ul>
    </div><div class="phase">
      <div class="phase-head"><span class="num">4</span><div><h3>Exam simulation</h3><div class="dates">May – first phase · 1 May to 1 Jun</div></div><span class="pct">0%</span></div>
      <p class="why">Real conditions: 20 questions, timed, no help. Then study every miss and every guess.</p>
      <ul class="tasks"><li><label><input type="checkbox" data-k="p4-0"><span>Timed exam #1</span></label></li><li><label><input type="checkbox" data-k="p4-1"><span>Timed exam #2</span></label></li><li><label><input type="checkbox" data-k="p4-2"><span>Timed exam #3</span></label></li><li><label><input type="checkbox" data-k="p4-3"><span>Timed exam #4</span></label></li><li><label><input type="checkbox" data-k="p4-4"><span>Redo every wrong or guessed question</span></label></li><li><label><input type="checkbox" data-k="p4-5"><span>Last week: review the notebook and rest</span></label></li></ul>
    </div><div class="phase">
      <div class="phase-head"><span class="num">5</span><div><h3>Second phase</h3><div class="dates">After the first phase – October · 1 Jun to 31 Oct</div></div><span class="pct">0%</span></div>
      <p class="why">Written solutions. Explain every step; partial credit depends on it.</p>
      <ul class="tasks"><li><label><input type="checkbox" data-k="p5-0"><span>Full written solutions to old second-phase exam #1</span></label></li><li><label><input type="checkbox" data-k="p5-1"><span>Old second-phase exam #2</span></label></li><li><label><input type="checkbox" data-k="p5-2"><span>Old second-phase exam #3</span></label></li><li><label><input type="checkbox" data-k="p5-3"><span>Old second-phase exam #4</span></label></li><li><label><input type="checkbox" data-k="p5-4"><span>Old second-phase exam #5</span></label></li><li><label><input type="checkbox" data-k="p5-5"><span>Compare each with the official solution and note what you missed</span></label></li></ul>
    </div></section>

  <section class="panel" id="log" role="tabpanel" hidden="">
    <h2>This week</h2>
    <div class="week"><span class="big" id="wkMin">0m</span><span class="small" id="wkGoal">of 4h goal</span></div>
    <div class="meter"><i id="wkBar" style="width: 0%;"></i></div>
    <div class="row">
      <label class="field">Date<input type="date" id="lDate"></label>
      <label class="field">Minutes<input type="number" id="lMin" min="5" step="5" value="60" style="width:6em"></label>
      <label class="field">Topic<select id="lTopic"><option>Number theory</option><option>Counting</option><option>Geometry</option><option>Algebra</option><option>Probability</option><option>Mixed / exams</option></select></label>
      <label class="field grow">What did you do?<input type="text" id="lNote" placeholder="e.g. 8 problems from Banco de Questões"></label>
      <button class="btn" id="lAdd">Log session</button>
    </div>
    <h3 style="margin-top:28px">Last 12 weeks</h3>
    <div class="weeks" id="weeks"><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div><div class="" style="height:0%" title="0m"></div></div>
    <p class="small">Green weeks hit your goal. Weekly goal: <input type="number" id="goal" min="30" step="30" style="width:5em" class="field"> minutes</p>
    <ul class="entries" id="entries"><li class="empty">No sessions yet. Log your first one above.</li></ul>
  </section>

  <section class="panel" id="notes" role="tabpanel" hidden="">
    <h2>Tricks notebook</h2>
    <p class="small">Every time a solution surprises you, write down the idea in your own words. Olympiad problems reuse the same ideas a lot.</p>
    <label class="field">Idea or trick<textarea id="nText" placeholder="e.g. A number is divisible by 9 when its digit sum is. Useful whenever a problem talks about digits."></textarea></label>
    <div class="row" style="margin-top:10px">
      <label class="field">Topic<select id="nTopic"><option>Number theory</option><option>Counting</option><option>Geometry</option><option>Algebra</option><option>Probability</option><option>Mixed / exams</option></select></label>
      <label class="field grow">Where it came from (optional)<input type="text" id="nSrc" placeholder="e.g. OBMEP 2019, 1ª fase, questão 14"></label>
      <button class="btn" id="nAdd">Save to notebook</button>
    </div>
    <div class="filters" id="filters"></div>
    <div id="noteList"><p class="empty">Your notebook is empty. Save the first trick you learn.</p></div>
  </section>

  <section class="panel" id="res" role="tabpanel" hidden="">
    <h2>Resources</h2>
    <p class="small">All free.</p>
    <div class="res"><h3><a href="https://www.obmep.org.br" target="_blank" rel="noopener">OBMEP official site</a></h3><p>Past exams with solutions for both phases, the yearly Banco de Questões, the PIC handouts, and the official calendar. Your main practice source.</p></div>
    <div class="res"><h3><a href="https://portaldaobmep.impa.br" target="_blank" rel="noopener">Portal da Matemática</a></h3><p>Video lessons and exercises by topic. Good for learning each topic the first time.</p></div>
    <div class="res"><h3>PIC handouts</h3><p><em>Iniciação à Aritmética</em> for number theory and <em>Métodos de Contagem e Probabilidade</em> for counting. Harder than the Portal lessons; use them in the second half of each topic. Find them on the OBMEP site.</p></div>
    <div class="res"><h3><a href="https://poti.impa.br" target="_blank" rel="noopener">POTI</a></h3><p>Free olympiad training with material by level. Check whether there's an in-person polo in Curitiba.</p></div>
    <div class="res"><h3><a href="https://noic.com.br" target="_blank" rel="noopener">NOIC</a></h3><p>Problem lists, weekly problems and guides written by former olympiad students.</p></div>
  </section>
</div>
<div class="status" id="status">Saved on this device</div>

<script>
const TOPICS = ["Number theory","Counting","Geometry","Algebra","Probability","Mixed / exams"];
const PHASES = [
  {id:"p1", name:"Foundations", start:"2026-09-28", end:"2026-12-31", range:"Now – December",
   why:"Number theory and counting show up constantly in OBMEP and reward practice. About 4–5 hours a week.",
   tasks:["Divisibility and divisibility rules","Primes and prime factorization","GCD and LCM","Remainders and basic modular arithmetic","Read the first chapters of Iniciação à Aritmética","Multiplication principle","Permutations and combinations","Pigeonhole principle","Try one old Nível 3 first-phase exam, no time limit"]},
  {id:"p2", name:"Geometry and algebra", start:"2027-01-01", end:"2027-02-28", range:"January – February",
   why:"Use the school break to study a bit more each week. Keep doing a few number theory and counting problems so they stay fresh.",
   tasks:["Angles, parallel lines and triangles","Similar triangles and Pythagoras","Areas of polygons","Circles and inscribed angles","Factoring and notable products","Equations and systems","Basic inequalities (AM–GM)","Probability basics (Métodos de Contagem e Probabilidade)"]},
  {id:"p3", name:"Mixed problems", start:"2027-03-01", end:"2027-04-30", range:"March – April",
   why:"Stop studying by topic. Mixed sets are what the real exam feels like.",
   tasks:["Old first-phase exam #1","Old first-phase exam #2","Old first-phase exam #3","Old first-phase exam #4","Old first-phase exam #5","Work through one Banco de Questões","Review the notebook every week"]},
  {id:"p4", name:"Exam simulation", start:"2027-05-01", end:"EXAM", range:"May – first phase",
   why:"Real conditions: 20 questions, timed, no help. Then study every miss and every guess.",
   tasks:["Timed exam #1","Timed exam #2","Timed exam #3","Timed exam #4","Redo every wrong or guessed question","Last week: review the notebook and rest"]},
  {id:"p5", name:"Second phase", start:"EXAM", end:"2027-10-31", range:"After the first phase – October",
   why:"Written solutions. Explain every step; partial credit depends on it.",
   tasks:["Full written solutions to old second-phase exam #1","Old second-phase exam #2","Old second-phase exam #3","Old second-phase exam #4","Old second-phase exam #5","Compare each with the official solution and note what you missed"]}
];
const DEFAULT = {done:{}, logs:[], notes:[], examDate:"2027-06-01", weeklyGoal:240};
let state = load();
let filter = "All";
const $ = id => document.getElementById(id);
const esc = s => String(s).replace(/[&<>"']/g, c => ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
const day = s => new Date(s + "T12:00:00");
const iso = d => d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0");
const today = () => iso(new Date());
const fmt = s => day(s).toLocaleDateString("en-GB",{day:"numeric",month:"short"});
const hrs = m => { const h=Math.floor(m/60), r=m%60; return h ? (r ? h+"h "+r+"m" : h+"h") : r+"m"; };

function load(){
  try { const raw = localStorage.getItem("obmep-tracker"); if (raw) return Object.assign({}, DEFAULT, JSON.parse(raw)); } catch(e){}
  return JSON.parse(JSON.stringify(DEFAULT));
}
function phaseDates(p){
  const s = p.start==="EXAM" ? state.examDate : p.start;
  const e = p.end==="EXAM" ? state.examDate : p.end;
  return [day(s), day(e)];
}

/* ---------- rendering ---------- */
function renderRuler(){
  const T0 = day("2026-09-28"), T1 = day("2027-10-31"), span = T1 - T0;
  const now = new Date();
  $("bar").innerHTML = PHASES.map(p => {
    const [s,e] = phaseDates(p);
    const w = Math.max(0,(e - s)/span*100);
    const pct = done(p)/p.tasks.length*100;
    const isNow = now >= s && now <= new Date(e.getTime()+864e5);
    return `<div class="seg${isNow?" now":""}" style="width:${w}%" title="${esc(p.name)}"><div class="fill" style="width:${pct}%"></div><span>${w>12?esc(p.name):""}</span></div>`;
  }).join("");
  const pos = Math.min(100, Math.max(0,(now - T0)/span*100));
  $("marker").style.left = pos + "%";
  const exam = day(state.examDate);
  const days = Math.ceil((exam - now)/864e5);
  const total = PHASES.reduce((a,p)=>a+p.tasks.length,0), got = PHASES.reduce((a,p)=>a+done(p),0);
  const mins = state.logs.reduce((a,l)=>a+l.min,0);
  $("facts").innerHTML =
    `<span><strong>${days>0?days:0}</strong> days to the first phase</span>`+
    `<span><strong>${got}/${total}</strong> plan items done</span>`+
    `<span><strong>${hrs(mins)}</strong> studied so far</span>`+
    `<label>First phase date: <input type="date" id="examDate" value="${state.examDate}" style="font-size:.9rem"> <span class="small">(estimate; update when the calendar is out)</span></label>`;
  $("examDate").onchange = e => { if(e.target.value){ state.examDate = e.target.value; save(); renderAll(); } };
}
function done(p){ return p.tasks.filter((_,i)=>state.done[p.id+"-"+i]).length; }

function renderPlan(){
  $("plan").innerHTML = PHASES.map((p,n) => {
    const [s,e] = phaseDates(p);
    const pct = Math.round(done(p)/p.tasks.length*100);
    return `<div class="phase">
      <div class="phase-head"><span class="num">${n+1}</span><div><h3>${esc(p.name)}</h3><div class="dates">${esc(p.range)} · ${fmt(iso(s))} to ${fmt(iso(e))}</div></div><span class="pct">${pct}%</span></div>
      <p class="why">${esc(p.why)}</p>
      <ul class="tasks">${p.tasks.map((t,i)=>{const k=p.id+"-"+i;return `<li><label><input type="checkbox" data-k="${k}" ${state.done[k]?"checked":""}><span>${esc(t)}</span></label></li>`;}).join("")}</ul>
    </div>`;
  }).join("");
  $("plan").querySelectorAll("input[type=checkbox]").forEach(cb => cb.onchange = () => {
    if (cb.checked) state.done[cb.dataset.k] = true; else delete state.done[cb.dataset.k];
    save(); renderRuler();
    const ph = cb.closest(".phase"); const p = PHASES[[...$("plan").children].indexOf(ph)];
    ph.querySelector(".pct").textContent = Math.round(done(p)/p.tasks.length*100)+"%";
  });
}

function weekStart(d){ const x = new Date(d); x.setHours(12,0,0,0); const k=(x.getDay()+6)%7; x.setDate(x.getDate()-k); return x; }
function renderLog(){
  const ws = weekStart(new Date());
  const inWeek = (l, start) => { const d = day(l.date); const end = new Date(start); end.setDate(end.getDate()+7); return d >= start && d < end; };
  const wk = state.logs.filter(l=>inWeek(l,ws)).reduce((a,l)=>a+l.min,0);
  $("wkMin").textContent = hrs(wk);
  $("wkGoal").textContent = "of " + hrs(state.weeklyGoal) + " goal";
  $("wkBar").style.width = Math.min(100, wk/state.weeklyGoal*100) + "%";
  $("goal").value = state.weeklyGoal;
  const bars = [], vals = [];
  for (let i=11;i>=0;i--){ const s=new Date(ws); s.setDate(s.getDate()-7*i); vals.push(state.logs.filter(l=>inWeek(l,s)).reduce((a,l)=>a+l.min,0)); }
  const mx = Math.max(state.weeklyGoal, ...vals);
  $("weeks").innerHTML = vals.map(v=>`<div class="${v>=state.weeklyGoal?"met":""}" style="height:${v/mx*100}%" title="${hrs(v)}"></div>`).join("");
  const list = [...state.logs].sort((a,b)=>b.date.localeCompare(a.date)||b.id-a.id).slice(0,30);
  $("entries").innerHTML = list.length ? list.map(l=>`<li><span class="when">${fmt(l.date)}</span><span class="what"><span class="tag">${esc(l.topic)}</span>${hrs(l.min)}${l.note?`<small>${esc(l.note)}</small>`:""}</span><button class="x" data-del="${l.id}">Delete</button></li>`).join("")
    : `<li class="empty">No sessions yet. Log your first one above.</li>`;
  $("entries").querySelectorAll("[data-del]").forEach(b=>b.onclick=()=>{ state.logs = state.logs.filter(l=>String(l.id)!==b.dataset.del); save(); renderLog(); renderRuler(); });
}

function renderNotes(){
  const used = ["All", ...TOPICS.filter(t=>state.notes.some(n=>n.topic===t))];
  if (!used.includes(filter)) filter = "All";
  $("filters").innerHTML = state.notes.length ? used.map(t=>`<button class="chip" aria-pressed="${t===filter}" data-f="${esc(t)}">${esc(t)}</button>`).join("") : "";
  $("filters").querySelectorAll(".chip").forEach(c=>c.onclick=()=>{ filter=c.dataset.f; renderNotes(); });
  const list = state.notes.filter(n=>filter==="All"||n.topic===filter).sort((a,b)=>b.id-a.id);
  $("noteList").innerHTML = list.length ? list.map(n=>`<div class="note"><span class="tag">${esc(n.topic)}</span><span class="small">${fmt(n.date)}${n.src?" · "+esc(n.src):""}</span> <button class="x" data-del="${n.id}">Delete</button><p>${esc(n.text)}</p></div>`).join("")
    : `<p class="empty">Your notebook is empty. Save the first trick you learn.</p>`;
  $("noteList").querySelectorAll("[data-del]").forEach(b=>b.onclick=()=>{ if(confirm("Delete this note?")){ state.notes = state.notes.filter(n=>String(n.id)!==b.dataset.del); save(); renderNotes(); }});
}
function renderAll(){ renderRuler(); renderPlan(); renderLog(); renderNotes(); }

/* ---------- inputs ---------- */
for (const sel of ["lTopic","nTopic"]) $(sel).innerHTML = TOPICS.map(t=>`<option>${t}</option>`).join("");
$("lDate").value = today();
$("lAdd").onclick = () => {
  const min = parseInt($("lMin").value,10);
  if (!min || min < 1) { $("lMin").focus(); return; }
  state.logs.push({id:Date.now(), date:$("lDate").value||today(), min, topic:$("lTopic").value, note:$("lNote").value.trim()});
  $("lNote").value = ""; save(); renderLog(); renderRuler();
};
$("goal").onchange = e => { const v=parseInt(e.target.value,10); if(v>0){ state.weeklyGoal=v; save(); renderLog(); } };
$("nAdd").onclick = () => {
  const text = $("nText").value.trim();
  if (!text) { $("nText").focus(); return; }
  state.notes.push({id:Date.now(), date:today(), topic:$("nTopic").value, src:$("nSrc").value.trim(), text});
  $("nText").value = ""; $("nSrc").value = ""; save(); renderNotes();
};
document.querySelectorAll(".tab").forEach(t => t.onclick = () => {
  document.querySelectorAll(".tab").forEach(x=>x.setAttribute("aria-selected", x===t));
  document.querySelectorAll(".panel").forEach(p=>p.hidden = p.id!==t.dataset.tab);
});

/* ---------- saving ---------- */
let ref = null, timer = null, writing = false, again = false;
const setStatus = s => $("status").textContent = s;
function save(){
  try { localStorage.setItem("obmep-tracker", JSON.stringify(state)); } catch(e){}
  if (ref) { setStatus("Saving…"); clearTimeout(timer); timer = setTimeout(flush, 1200); }
}
async function flush(){
  if (!ref) return;
  if (writing) { again = true; return; }
  writing = true;
  try { await ref.set(JSON.parse(JSON.stringify(state))); setStatus("Saved to your account"); }
  catch(e){ setStatus("Saved on this device only"); }
  writing = false;
  if (again) { again = false; flush(); }
}
renderAll();
(async () => {
  if (!window.claude || !window.claude.use) return;
  try {
    const [db, user] = await Promise.all([claude.use("db"), claude.use("user")]);
    if (!db || !user) return;
    const uid = await user.id();
    if (!uid) return;
    const r = db.doc("data/users/" + uid + "/progress");
    const snap = await r.get();
    if (snap.exists) { state = Object.assign({}, DEFAULT, JSON.parse(JSON.stringify(snap.data()))); renderAll(); }
    else { await r.set(JSON.parse(JSON.stringify(state))); }
    ref = r;
    try { localStorage.setItem("obmep-tracker", JSON.stringify(state)); } catch(e){}
    setStatus("Saved to your account");
  } catch(e) { setStatus("Saved on this device"); }
})();
</script>


</body></html>
