
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>競合店分析</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;500;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #0a0e1a;
  --surface: #111827;
  --surface2: #1a2332;
  --border: #1e3a5f;
  --accent: #00d4ff;
  --accent2: #ff6b35;
  --accent3: #00ff9d;
  --warn: #ffd166;
  --danger: #ff4d6d;
  --text: #e8f4fd;
  --muted: #7a9ab5;
  --score-bg: #0d1f35;
  --tab-h: 56px;
  --header-h: 52px;
}
* { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }
html, body { height: 100%; overflow: hidden; }
body { font-family: 'Noto Sans JP', sans-serif; background: var(--bg); color: var(--text); font-size: 15px; }

/* HEADER */
.hdr {
  position: fixed; top: 0; left: 0; right: 0; height: var(--header-h);
  background: #0d1527; border-bottom: 1px solid var(--border);
  display: flex; align-items: center; padding: 0 16px; gap: 12px;
  z-index: 200;
}
.hdr-title { font-size: 17px; font-weight: 700; color: var(--accent); letter-spacing: 1px; flex: 1; }
.hdr-progress {
  font-family: 'Space Mono', monospace; font-size: 12px; color: var(--muted);
}
.hdr-progress span { color: var(--accent3); font-weight: 700; }

/* BOTTOM TAB BAR */
.tab-bar {
  position: fixed; bottom: 0; left: 0; right: 0; height: var(--tab-h);
  background: #0d1527; border-top: 1px solid var(--border);
  display: flex; z-index: 200;
}
.tb {
  flex: 1; display: flex; flex-direction: column; align-items: center;
  justify-content: center; gap: 3px; border: none; background: transparent;
  color: var(--muted); font-size: 10px; font-family: 'Noto Sans JP', sans-serif;
  padding: 0; cursor: pointer; transition: color 0.15s;
  -webkit-tap-highlight-color: transparent;
  min-height: 44px;
}
.tb .ico { font-size: 20px; line-height: 1; }
.tb.active { color: var(--accent); }
.tb.active .ico { filter: drop-shadow(0 0 4px var(--accent)); }

/* SCROLL AREA */
.scroll-area {
  position: fixed;
  top: var(--header-h); bottom: var(--tab-h); left: 0; right: 0;
  overflow-y: auto; -webkit-overflow-scrolling: touch;
}
.panel { display: none; padding: 16px 14px 20px; }
.panel.active { display: block; }

/* STORE SETUP */
.setup-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px; margin-bottom: 14px;
}
.setup-card h2 { font-size: 12px; color: var(--muted); letter-spacing: 1.5px; text-transform: uppercase; margin-bottom: 12px; }
.field-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
.field-row.single { grid-template-columns: 1fr; }
label { display: block; font-size: 11px; color: var(--muted); margin-bottom: 4px; }
input[type=text], input[type=date], select {
  width: 100%; background: var(--score-bg); border: 1px solid var(--border);
  border-radius: 8px; color: var(--text); padding: 11px 12px;
  font-family: 'Noto Sans JP', sans-serif; font-size: 14px; outline: none;
  -webkit-appearance: none; appearance: none;
}
input:focus, select:focus { border-color: var(--accent); }
select { background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' fill='none'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%237a9ab5' stroke-width='1.5' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 12px center; padding-right: 32px; }

/* PROGRESS BAR */
.prog-wrap { margin-bottom: 4px; }
.prog-track { height: 4px; background: var(--score-bg); border-radius: 2px; overflow: hidden; margin-top: 6px; }
.prog-fill { height: 100%; border-radius: 2px; background: linear-gradient(90deg, var(--accent), var(--accent3)); transition: width 0.4s ease; }

/* CAT HEADER */
.cat-hdr {
  display: flex; align-items: center; gap: 10px;
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 12px 14px; margin-bottom: 12px;
}
.cat-ico { font-size: 26px; }
.cat-info { flex: 1; }
.cat-info .name { font-size: 15px; font-weight: 700; }
.cat-info .sub { font-size: 11px; color: var(--muted); margin-top: 2px; }
.cat-weight { font-family: 'Space Mono', monospace; font-size: 11px; color: var(--accent); background: rgba(0,212,255,0.1); border: 1px solid rgba(0,212,255,0.25); border-radius: 20px; padding: 3px 10px; }

/* CRITERION CARD */
.crit-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px; margin-bottom: 10px;
}
.crit-name { font-size: 14px; font-weight: 500; line-height: 1.5; margin-bottom: 12px; }

/* SCORE SECTION */
.score-section { margin-bottom: 10px; }
.score-who {
  display: flex; align-items: center; gap: 6px;
  font-size: 12px; font-weight: 600; margin-bottom: 8px;
}
.who-dot { width: 8px; height: 8px; border-radius: 50%; flex-shrink: 0; }
.who-dot.my { background: var(--accent); }
.who-dot.rival { background: var(--accent2); }

/* SCORE BUTTONS — large tap targets */
.score-btns { display: flex; gap: 6px; }
.sc {
  flex: 1; height: 48px; border-radius: 8px;
  border: 1.5px solid var(--border); background: var(--score-bg);
  color: var(--muted); font-size: 15px; font-weight: 700;
  font-family: 'Space Mono', monospace;
  cursor: pointer; transition: all 0.12s; display: flex; align-items: center; justify-content: center;
}
.sc:active { transform: scale(0.92); }
.sc.s1 { border-color: var(--danger); background: rgba(255,77,109,0.15); color: var(--danger); }
.sc.s2 { border-color: #ff8c42; background: rgba(255,140,66,0.12); color: #ff8c42; }
.sc.s3 { border-color: var(--warn); background: rgba(255,209,102,0.12); color: var(--warn); }
.sc.s4 { border-color: #52d68a; background: rgba(82,214,138,0.12); color: #52d68a; }
.sc.s5 { border-color: var(--accent3); background: rgba(0,255,157,0.12); color: var(--accent3); }
.score-labels-row { display: flex; gap: 6px; margin-top: 4px; }
.slbl { flex: 1; text-align: center; font-size: 9px; color: var(--muted); line-height: 1.3; }

/* NOTE INPUT */
.note-wrap { margin-top: 10px; }
.note-wrap input {
  background: var(--score-bg); border: 1px solid var(--border);
  border-radius: 8px; color: var(--muted); padding: 10px 12px;
  font-size: 13px; width: 100%; outline: none;
}
.note-wrap input:focus { border-color: rgba(0,212,255,0.4); color: var(--text); }
.note-wrap input::placeholder { color: #3a5a75; }

/* DIVIDER */
.score-divider { height: 1px; background: var(--border); margin: 10px 0; }

/* RESULTS */
.total-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
.total-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 16px 12px; text-align: center;
  position: relative; overflow: hidden;
}
.total-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; }
.total-card.my::before { background: var(--accent); }
.total-card.rival::before { background: var(--accent2); }
.total-who { font-size: 10px; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 4px; }
.total-name { font-size: 13px; font-weight: 700; margin-bottom: 10px; line-height: 1.3; min-height: 36px; display: flex; align-items: center; justify-content: center; }
.total-score {
  font-family: 'Space Mono', monospace; font-size: 44px; font-weight: 700; line-height: 1;
}
.total-score.my { color: var(--accent); }
.total-score.rival { color: var(--accent2); }
.total-max { font-size: 14px; color: var(--muted); }
.grade-badge {
  display: inline-block; margin-top: 8px;
  padding: 3px 12px; border-radius: 20px; font-size: 12px; font-weight: 700;
  border: 1px solid currentColor;
}

.diff-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px 16px; margin-bottom: 10px;
  display: flex; align-items: center; gap: 14px;
}
.diff-num { font-family: 'Space Mono', monospace; font-size: 36px; font-weight: 700; flex-shrink: 0; }
.diff-num.pos { color: var(--accent3); }
.diff-num.neg { color: var(--danger); }
.diff-num.zer { color: var(--warn); }
.diff-msg { font-size: 13px; color: var(--muted); line-height: 1.6; }

/* BREAKDOWN */
.section-card {
  background: var(--surface); border: 1px solid var(--border);
  border-radius: 12px; padding: 14px; margin-bottom: 10px;
}
.section-ttl { font-size: 11px; color: var(--muted); letter-spacing: 1.5px; text-transform: uppercase; margin-bottom: 14px; }
.bk-row { margin-bottom: 12px; }
.bk-label { font-size: 12px; margin-bottom: 4px; }
.bk-bars { display: grid; gap: 4px; }
.bar-line { display: flex; align-items: center; gap: 8px; }
.bar-who { font-size: 10px; width: 20px; color: var(--muted); }
.bar-track { flex: 1; height: 8px; background: var(--score-bg); border-radius: 4px; overflow: hidden; }
.bar-my { height: 100%; border-radius: 4px; background: var(--accent); transition: width 0.5s ease; }
.bar-rv { height: 100%; border-radius: 4px; background: var(--accent2); transition: width 0.5s ease; }
.bar-pt { font-family: 'Space Mono', monospace; font-size: 11px; width: 36px; text-align: right; }

/* INSIGHTS */
.insight-card {
  border-radius: 10px; padding: 12px 14px; margin-bottom: 8px;
  border-left: 3px solid;
}
.insight-card.str { border-color: var(--accent3); background: rgba(0,255,157,0.04); }
.insight-card.wk { border-color: var(--danger); background: rgba(255,77,109,0.04); }
.insight-card.op { border-color: var(--warn); background: rgba(255,209,102,0.04); }
.insight-lbl { font-size: 10px; letter-spacing: 1.5px; text-transform: uppercase; margin-bottom: 5px; }
.insight-card.str .insight-lbl { color: var(--accent3); }
.insight-card.wk .insight-lbl { color: var(--danger); }
.insight-card.op .insight-lbl { color: var(--warn); }
.insight-txt { font-size: 13px; line-height: 1.7; }

/* DETAIL ROWS */
.det-row {
  padding: 10px 0; border-bottom: 1px solid rgba(30,58,95,0.5);
  display: grid; grid-template-columns: 1fr auto auto auto; gap: 8px; align-items: start;
}
.det-name { font-size: 12px; line-height: 1.5; }
.det-scores { display: flex; gap: 6px; align-items: center; }
.det-s { font-family: 'Space Mono', monospace; font-size: 12px; }
.det-my { color: var(--accent); }
.det-rv { color: var(--accent2); }
.det-diff { font-family: 'Space Mono', monospace; font-size: 12px; }
.det-note { font-size: 11px; color: var(--muted); margin-top: 3px; grid-column: 1 / -1; }

/* ACTION BUTTONS */
.act-btn {
  width: 100%; padding: 14px; border-radius: 10px; border: none;
  font-family: 'Noto Sans JP', sans-serif; font-size: 14px; font-weight: 700;
  cursor: pointer; margin-bottom: 10px; display: flex; align-items: center; justify-content: center; gap: 8px;
}
.act-btn.primary { background: var(--accent); color: #000; }
.act-btn.secondary { background: var(--surface2); color: var(--text); border: 1px solid var(--border); }
.act-btn.danger { background: rgba(255,77,109,0.1); color: var(--danger); border: 1px solid rgba(255,77,109,0.3); }
.act-btn:active { opacity: 0.8; transform: scale(0.98); }

/* EMPTY STATE */
.empty-hint { text-align: center; padding: 40px 20px; color: var(--muted); font-size: 14px; line-height: 1.8; }
</style>
</head>
<body>

<div class="hdr">
  <div class="hdr-title">📊 競合分析</div>
  <div class="hdr-progress" id="hdr-prog"><span id="hdr-pct">0%</span> 入力済</div>
</div>

<div class="scroll-area">
  <!-- SETUP -->
  <div class="panel active" id="panel-setup">
    <div class="setup-card">
      <h2>基本情報</h2>
      <div class="field-row">
        <div><label>自店名</label><input type="text" id="my-name" placeholder="○○スーパー 本店"></div>
        <div><label>競合店名</label><input type="text" id="rival-name" placeholder="△△マート"></div>
      </div>
      <div class="field-row">
        <div><label>調査日</label><input type="date" id="survey-date"></div>
        <div><label>調査者</label><input type="text" id="surveyor" placeholder="担当者名"></div>
      </div>
      <div class="field-row single">
        <div><label>調査時間帯</label>
          <select id="survey-time">
            <option>開店直後 (9-11時)</option>
            <option>昼ピーク (11-14時)</option>
            <option>午後 (14-17時)</option>
            <option selected>夕方ピーク (17-20時)</option>
            <option>閉店前 (20時以降)</option>
          </select>
        </div>
      </div>
      <div class="prog-wrap">
        <div style="display:flex;justify-content:space-between;font-size:11px;color:var(--muted);">
          <span>評価入力進捗</span><span id="prog-txt">0 / 0 項目</span>
        </div>
        <div class="prog-track"><div class="prog-fill" id="prog-fill" style="width:0%"></div></div>
      </div>
    </div>
    <div style="text-align:center;padding:16px 0 8px;">
      <div style="font-size:13px;color:var(--muted);margin-bottom:12px;">下のタブから各カテゴリを評価してください</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;">
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">💴</div>
          <div style="font-size:12px;color:var(--muted);">価格競争力</div>
        </div>
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">🥬</div>
          <div style="font-size:12px;color:var(--muted);">鮮度・品質</div>
        </div>
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">📦</div>
          <div style="font-size:12px;color:var(--muted);">品揃え</div>
        </div>
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">😊</div>
          <div style="font-size:12px;color:var(--muted);">サービス</div>
        </div>
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">🏪</div>
          <div style="font-size:12px;color:var(--muted);">店舗環境</div>
        </div>
        <div style="background:var(--surface);border:1px solid var(--border);border-radius:10px;padding:12px;text-align:center;">
          <div style="font-size:22px;margin-bottom:4px;">📣</div>
          <div style="font-size:12px;color:var(--muted);">販促</div>
        </div>
      </div>
    </div>
  </div>

  <!-- CATEGORY PANELS -->
  <div class="panel" id="panel-price"></div>
  <div class="panel" id="panel-fresh"></div>
  <div class="panel" id="panel-assort"></div>
  <div class="panel" id="panel-service"></div>
  <div class="panel" id="panel-store"></div>
  <div class="panel" id="panel-promo"></div>
  <div class="panel" id="panel-results"></div>
</div>

<!-- BOTTOM TAB BAR -->
<div class="tab-bar">
  <button class="tb active" onclick="nav('setup',this)">
    <span class="ico">🏠</span><span>設定</span>
  </button>
  <button class="tb" onclick="nav('price',this)">
    <span class="ico">💴</span><span>価格</span>
  </button>
  <button class="tb" onclick="nav('fresh',this)">
    <span class="ico">🥬</span><span>鮮度</span>
  </button>
  <button class="tb" onclick="nav('assort',this)">
    <span class="ico">📦</span><span>品揃え</span>
  </button>
  <button class="tb" onclick="nav('service',this)">
    <span class="ico">😊</span><span>接客</span>
  </button>
  <button class="tb" onclick="nav('store',this)">
    <span class="ico">🏪</span><span>環境</span>
  </button>
  <button class="tb" onclick="nav('promo',this)">
    <span class="ico">📣</span><span>販促</span>
  </button>
  <button class="tb" onclick="nav('results',this)">
    <span class="ico">📊</span><span>結果</span>
  </button>
</div>

<script>
const CATS = [
  { id:'price', label:'価格競争力', ico:'💴', weight:1.5, sub:'生鮮・加工品・日配品の価格水準',
    criteria:[
      {id:'p1', name:'生鮮定番品（野菜・肉・魚）の価格水準', w:3},
      {id:'p2', name:'PBブランド商品の充実度と価格', w:2},
      {id:'p3', name:'特売・週替わりセールの訴求力', w:2},
      {id:'p4', name:'タイムサービス・見切り品の活用', w:1},
      {id:'p5', name:'加工食品・日配品の価格競争力', w:2},
    ]},
  { id:'fresh', label:'鮮度・品質', ico:'🥬', weight:1.5, sub:'商品の新鮮さ・品質管理状況',
    criteria:[
      {id:'f1', name:'青果の鮮度・見た目のクオリティ', w:3},
      {id:'f2', name:'精肉の色・鮮度・パッケージ清潔感', w:3},
      {id:'f3', name:'鮮魚の鮮度・品揃え・温度管理', w:3},
      {id:'f4', name:'惣菜の品質・調理仕立て感', w:2},
      {id:'f5', name:'ベーカリー・麺類の鮮度', w:1},
    ]},
  { id:'assort', label:'品揃え', ico:'📦', weight:1.2, sub:'商品種類数・カテゴリカバレッジ',
    criteria:[
      {id:'a1', name:'カテゴリ深さ（各部門のSKU数）', w:2},
      {id:'a2', name:'地域・地場商品・産地直送品', w:2},
      {id:'a3', name:'健康・オーガニック・機能性食品', w:2},
      {id:'a4', name:'日用品・非食品の品揃え', w:1},
      {id:'a5', name:'季節商品・トレンド商品への対応', w:2},
    ]},
  { id:'service', label:'接客・サービス', ico:'😊', weight:1.0, sub:'スタッフ対応・レジ・顧客体験',
    criteria:[
      {id:'s1', name:'スタッフの挨拶・接客姿勢', w:2},
      {id:'s2', name:'レジ待ち時間・スムーズさ', w:3},
      {id:'s3', name:'スタッフの商品知識・案内力', w:2},
      {id:'s4', name:'袋詰め・包装の丁寧さ', w:1},
      {id:'s5', name:'セルフレジ・キャッシュレス対応', w:2},
    ]},
  { id:'store', label:'店舗環境', ico:'🏪', weight:1.0, sub:'売場づくり・清潔度・動線',
    criteria:[
      {id:'e1', name:'売場・通路の清潔感', w:2},
      {id:'e2', name:'売場レイアウト・回遊しやすさ', w:2},
      {id:'e3', name:'陳列の見やすさ・フェイス管理', w:2},
      {id:'e4', name:'照明・温度・BGMの快適さ', w:1},
      {id:'e5', name:'駐車場・アクセスの利便性', w:1},
    ]},
  { id:'promo', label:'販促・集客', ico:'📣', weight:1.0, sub:'チラシ・POP・ポイント施策',
    criteria:[
      {id:'r1', name:'チラシ・折込の充実度と価格訴求力', w:2},
      {id:'r2', name:'売場POP・値札の見やすさ', w:2},
      {id:'r3', name:'ポイントカード・アプリ会員施策', w:2},
      {id:'r4', name:'試食・イベント・デモ販の活発さ', w:2},
      {id:'r5', name:'SNS・デジタル販促の活用度', w:1},
    ]},
];

const SLABELS = ['要改善','不十分','普通','良い','優秀'];
const scores = {};
CATS.forEach(c => c.criteria.forEach(cr => { scores[cr.id] = {my:0, rival:0, note:''}; }));



function init() {
  document.getElementById('survey-date').valueAsDate = new Date();

  // RENDER CATEGORY PANELS
  CATS.forEach(cat => {
    const el = document.getElementById('panel-' + cat.id);
    let html = `<div class="cat-hdr"><span class="cat-ico">${cat.ico}</span><div class="cat-info"><div class="name">${cat.label}</div><div class="sub">${cat.sub}</div></div><div class="cat-weight">×${cat.weight}</div></div>`;
    cat.criteria.forEach(cr => {
      html += `<div class="crit-card">
        <div class="crit-name">${cr.name}</div>
        <div class="score-section">
          <div class="score-who"><div class="who-dot my"></div><span style="color:var(--accent)">自店</span></div>
          <div class="score-btns">${[1,2,3,4,5].map(n=>`<button class="sc" id="my-${cr.id}-${n}" onclick="setS('${cr.id}','my',${n})">${n}</button>`).join('')}</div>
          <div class="score-labels-row">${SLABELS.map(l=>`<div class="slbl">${l}</div>`).join('')}</div>
        </div>
        <div class="score-divider"></div>
        <div class="score-section">
          <div class="score-who"><div class="who-dot rival"></div><span style="color:var(--accent2)">競合店</span></div>
          <div class="score-btns">${[1,2,3,4,5].map(n=>`<button class="sc" id="rv-${cr.id}-${n}" onclick="setS('${cr.id}','rival',${n})">${n}</button>`).join('')}</div>
          <div class="score-labels-row">${SLABELS.map(l=>`<div class="slbl">${l}</div>`).join('')}</div>
        </div>
        <div class="note-wrap"><input type="text" id="note-${cr.id}" placeholder="📝 気づき・メモ" onchange="scores['${cr.id}'].note=this.value" value=""></div>
      </div>`;
    });
    el.innerHTML = html;
  });



  updateProgress();
}

function setS(id, who, val) {
  scores[id][who] = val;
  const prefix = who==='my' ? 'my' : 'rv';
  for(let n=1;n<=5;n++){
    const b=document.getElementById(`${prefix}-${id}-${n}`);
    if(b){b.className='sc';if(n===val)b.className='sc s'+n;}
  }
  updateProgress();
}

function updateProgress() {
  let tot=0, fil=0;
  CATS.forEach(c=>c.criteria.forEach(cr=>{tot+=2;if(scores[cr.id].my>0)fil++;if(scores[cr.id].rival>0)fil++;}));
  const pct=Math.round(fil/tot*100);
  document.getElementById('prog-fill').style.width=pct+'%';
  document.getElementById('prog-txt').textContent=`${fil} / ${tot} 項目`;
  document.getElementById('hdr-pct').textContent=pct+'%';
}

function nav(id, btn) {
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tb').forEach(t=>t.classList.remove('active'));
  document.getElementById('panel-'+id).classList.add('active');
  btn.classList.add('active');
  document.querySelector('.scroll-area').scrollTop=0;
  if(id==='results') renderResults();
}

function catScore(cat, who) {
  let sum=0, max=0;
  cat.criteria.forEach(cr=>{sum+=(scores[cr.id][who]||0)*cr.w;max+=5*cr.w;});
  return max>0 ? sum/max*100 : 0;
}

function totalScore(who) {
  let ws=0, wm=0;
  CATS.forEach(c=>{ws+=(catScore(c,who)/100)*c.weight;wm+=c.weight;});
  return wm>0 ? Math.round(ws/wm*100) : 0;
}

function grade(s) {
  if(s>=85) return {lbl:'S 卓越',color:'#00ff9d'};
  if(s>=70) return {lbl:'A 優秀',color:'#00d4ff'};
  if(s>=55) return {lbl:'B 標準',color:'#ffd166'};
  if(s>=40) return {lbl:'C 要改善',color:'#ff8c42'};
  return {lbl:'D 危機',color:'#ff4d6d'};
}

function renderResults() {
  const myN=document.getElementById('my-name').value||'自店';
  const rvN=document.getElementById('rival-name').value||'競合店';
  const myT=totalScore('my'), rvT=totalScore('rival');
  const diff=myT-rvT;
  const myG=grade(myT), rvG=grade(rvT);

  const diffClass=diff>0?'pos':diff<0?'neg':'zer';
  const diffMsg=diff>10?'✅ 自店が競合を大きくリード。優位性を維持・強化しましょう。'
    :diff>0?'🟡 自店がわずかにリード。強みを伸ばしましょう。'
    :diff===0?'🟠 同点。差別化ポイントの明確化が急務です。'
    :diff>-10?'🔴 競合にやや遅れています。重点項目の集中改善を。'
    :'🚨 競合に大きく遅れています。緊急対策が必要です。';

  // Breakdown
  let bkHTML='';
  CATS.forEach(c=>{
    const mp=Math.round(catScore(c,'my')), rp=Math.round(catScore(c,'rival'));
    bkHTML+=`<div class="bk-row">
      <div class="bk-label">${c.ico} ${c.label}</div>
      <div class="bk-bars">
        <div class="bar-line"><span class="bar-who" style="color:var(--accent)">自</span><div class="bar-track"><div class="bar-my" style="width:${mp}%"></div></div><span class="bar-pt" style="color:var(--accent)">${mp}pt</span></div>
        <div class="bar-line"><span class="bar-who" style="color:var(--accent2)">競</span><div class="bar-track"><div class="bar-rv" style="width:${rp}%"></div></div><span class="bar-pt" style="color:var(--accent2)">${rp}pt</span></div>
      </div>
    </div>`;
  });

  // Insights
  const str=[], wk=[], op=[];
  CATS.forEach(c=>{
    const mp=Math.round(catScore(c,'my')), rp=Math.round(catScore(c,'rival'));
    if(mp>=70) str.push(`${c.ico} ${c.label}（${mp}pt）`);
    if(mp<50)  wk.push(`${c.ico} ${c.label}（${mp}pt）`);
    if(rp>mp+15) op.push(`${c.ico} ${c.label}（差 −${rp-mp}pt）`);
  });

  // Detail
  let detHTML='';
  CATS.forEach(c=>{
    c.criteria.forEach(cr=>{
      const my=scores[cr.id].my||0, rv=scores[cr.id].rival||0;
      const d=my-rv;
      const dc=d>0?'color:var(--accent3)':d<0?'color:var(--danger)':'color:var(--muted)';
      detHTML+=`<div class="det-row">
        <div><div class="det-name">${cr.name}</div>${scores[cr.id].note?`<div class="det-note">💬 ${scores[cr.id].note}</div>`:''}</div>
        <span class="det-s det-my">${my||'—'}</span>
        <span class="det-s det-rv">${rv||'—'}</span>
        <span class="det-diff" style="${dc}">${my&&rv?(d>0?'+':'')+d:'—'}</span>
      </div>`;
    });
  });

  document.getElementById('panel-results').innerHTML = `
    <div class="total-grid">
      <div class="total-card my">
        <div class="total-who">自店</div>
        <div class="total-name">${myN}</div>
        <div class="total-score my">${myT}<span class="total-max">/100</span></div>
        <span class="grade-badge" style="color:${myG.color};border-color:${myG.color}">${myG.lbl}</span>
      </div>
      <div class="total-card rival">
        <div class="total-who">競合店</div>
        <div class="total-name">${rvN}</div>
        <div class="total-score rival">${rvT}<span class="total-max">/100</span></div>
        <span class="grade-badge" style="color:${rvG.color};border-color:${rvG.color}">${rvG.lbl}</span>
      </div>
    </div>

    <div class="diff-card">
      <div class="diff-num ${diffClass}">${diff>0?'+':''}${diff}pt</div>
      <div class="diff-msg">${diffMsg}</div>
    </div>

    <div class="section-card">
      <div class="section-ttl">カテゴリ別スコア</div>
      ${bkHTML}
    </div>

    <div class="section-card">
      <div class="section-ttl">分析インサイト</div>
      <div class="insight-card str"><div class="insight-lbl">✅ 自店の強み</div><div class="insight-txt">${str.length?str.join('<br>'):'70pt以上の項目なし'}</div></div>
      <div class="insight-card wk"><div class="insight-lbl">⚠️ 自店の弱み</div><div class="insight-txt">${wk.length?wk.join('<br>'):'50pt未満の項目なし'}</div></div>
      <div class="insight-card op"><div class="insight-lbl">🎯 要強化（競合差15pt超）</div><div class="insight-txt">${op.length?op.join('<br>'):'大きな差の項目なし'}</div></div>
    </div>

    <div class="section-card">
      <div class="section-ttl">評価項目詳細</div>
      <div style="display:flex;gap:16px;font-size:11px;color:var(--muted);margin-bottom:10px;">
        <span><span style="color:var(--accent)">■</span> 自店</span>
        <span><span style="color:var(--accent2)">■</span> 競合</span>
        <span>差（自店−競合）</span>
      </div>
      ${detHTML}
    </div>

    <button class="act-btn primary" onclick="exportCSV()">📥 CSVエクスポート</button>
    <button class="act-btn secondary" onclick="window.print()">🖨️ 印刷・PDF</button>
    <button class="act-btn danger" onclick="resetAll()">🗑️ データリセット</button>
  `;
}

function exportCSV() {
  const myN=document.getElementById('my-name').value||'自店';
  const rvN=document.getElementById('rival-name').value||'競合店';
  const date=document.getElementById('survey-date').value;
  let csv=`調査日,${date}\n自店,${myN}\n競合店,${rvN}\n\nカテゴリ,評価項目,自店,競合,差,メモ\n`;
  CATS.forEach(c=>c.criteria.forEach(cr=>{
    const s=scores[cr.id];
    const d=s.my&&s.rival?s.my-s.rival:'';
    csv+=`${c.label},${cr.name},${s.my||''},${s.rival||''},${d},"${s.note||''}"\n`;
  }));
  const a=document.createElement('a');
  a.href=URL.createObjectURL(new Blob(['\uFEFF'+csv],{type:'text/csv;charset=utf-8'}));
  a.download=`競合分析_${date}.csv`;
  a.click();
}

function resetAll() {
  if(!confirm('全データをリセットしますか？')) return;
  CATS.forEach(c=>c.criteria.forEach(cr=>{
    scores[cr.id]={my:0,rival:0,note:''};
    for(let n=1;n<=5;n++){
      const mb=document.getElementById(`my-${cr.id}-${n}`);
      const rb=document.getElementById(`rv-${cr.id}-${n}`);
      if(mb) mb.className='sc';
      if(rb) rb.className='sc';
    }
    const ne=document.getElementById('note-'+cr.id);
    if(ne) ne.value='';
  }));
  updateProgress();
}

init();
</script>
</body>
</html>
