<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>競合店分析システム</title>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400;500;700;900&family=Bebas+Neue&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
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
    --text-muted: #7a9ab5;
    --score-bg: #0d1f35;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Noto Sans JP', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HEADER ── */
  header {
    background: linear-gradient(135deg, #0d1f35 0%, #091529 100%);
    border-bottom: 1px solid var(--border);
    padding: 16px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: sticky; top: 0; z-index: 100;
    backdrop-filter: blur(10px);
  }
  .logo {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 28px;
    letter-spacing: 3px;
    background: linear-gradient(90deg, var(--accent), var(--accent3));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .header-meta {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--text-muted);
    text-align: right;
  }
  #live-clock { color: var(--accent); font-size: 13px; }

  /* ── MAIN LAYOUT ── */
  .container { max-width: 1400px; margin: 0 auto; padding: 24px; }

  /* ── STORE INFO ── */
  .store-setup {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 20px 24px;
    margin-bottom: 24px;
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 16px;
    align-items: end;
  }
  .input-group label {
    display: block;
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .input-group input, .input-group select {
    width: 100%;
    background: var(--score-bg);
    border: 1px solid var(--border);
    border-radius: 6px;
    color: var(--text);
    padding: 10px 12px;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 14px;
    outline: none;
    transition: border-color 0.2s;
  }
  .input-group input:focus, .input-group select:focus {
    border-color: var(--accent);
    box-shadow: 0 0 0 2px rgba(0,212,255,0.15);
  }

  /* ── TABS ── */
  .tabs {
    display: flex;
    gap: 4px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 4px;
    margin-bottom: 24px;
    flex-wrap: wrap;
  }
  .tab {
    flex: 1;
    min-width: 100px;
    padding: 10px 14px;
    background: transparent;
    border: none;
    border-radius: 7px;
    color: var(--text-muted);
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
    white-space: nowrap;
    text-align: center;
  }
  .tab.active {
    background: var(--accent);
    color: #000;
    font-weight: 700;
  }
  .tab:hover:not(.active) {
    background: var(--surface2);
    color: var(--text);
  }

  /* ── CATEGORY PANEL ── */
  .panel { display: none; }
  .panel.active { display: block; }

  .category-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }
  .category-icon {
    width: 44px; height: 44px;
    border-radius: 10px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    background: var(--surface2);
    border: 1px solid var(--border);
  }
  .category-title { font-size: 20px; font-weight: 700; }
  .category-weight {
    margin-left: auto;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 20px;
    padding: 4px 14px;
    font-size: 12px;
    color: var(--accent);
    font-family: 'Space Mono', monospace;
  }

  /* ── CRITERIA GRID ── */
  .criteria-grid {
    display: grid;
    gap: 12px;
  }
  .criterion-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
    transition: border-color 0.2s;
  }
  .criterion-card:hover { border-color: var(--accent); }

  .criterion-top {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    margin-bottom: 12px;
  }
  .criterion-name {
    flex: 1;
    font-size: 14px;
    font-weight: 500;
    line-height: 1.4;
  }
  .criterion-weight-badge {
    background: rgba(0,212,255,0.1);
    border: 1px solid rgba(0,212,255,0.3);
    border-radius: 4px;
    padding: 2px 8px;
    font-size: 11px;
    color: var(--accent);
    font-family: 'Space Mono', monospace;
    white-space: nowrap;
  }

  /* ── SCORE BUTTONS ── */
  .score-buttons {
    display: flex;
    gap: 6px;
    align-items: center;
  }
  .score-btn {
    flex: 1;
    padding: 8px 4px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--score-bg);
    color: var(--text-muted);
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.15s;
    text-align: center;
    font-family: 'Space Mono', monospace;
  }
  .score-btn:hover { border-color: var(--accent); color: var(--text); }
  .score-btn.selected-1 { background: #3d1520; border-color: var(--danger); color: var(--danger); }
  .score-btn.selected-2 { background: #3d2a10; border-color: #ff8c42; color: #ff8c42; }
  .score-btn.selected-3 { background: #2a2a10; border-color: var(--warn); color: var(--warn); }
  .score-btn.selected-4 { background: #0d2e20; border-color: #52d68a; color: #52d68a; }
  .score-btn.selected-5 { background: #0d2e35; border-color: var(--accent3); color: var(--accent3); }

  .score-labels {
    display: flex;
    gap: 6px;
    margin-top: 4px;
  }
  .score-label {
    flex: 1;
    text-align: center;
    font-size: 9px;
    color: var(--text-muted);
    line-height: 1.2;
  }

  .criterion-note {
    margin-top: 10px;
  }
  .criterion-note input {
    width: 100%;
    background: var(--score-bg);
    border: 1px solid var(--border);
    border-radius: 5px;
    color: var(--text-muted);
    padding: 7px 10px;
    font-size: 12px;
    font-family: 'Noto Sans JP', sans-serif;
    outline: none;
    transition: all 0.2s;
  }
  .criterion-note input:focus {
    border-color: rgba(0,212,255,0.4);
    color: var(--text);
  }
  .criterion-note input::placeholder { color: #3a5a75; }

  /* ── RESULTS PANEL ── */
  #panel-results {
    animation: fadeIn 0.3s ease;
  }
  @keyframes fadeIn { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }

  .score-overview {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-bottom: 28px;
  }

  .big-score-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 28px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .big-score-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0; height: 3px;
  }
  .big-score-card.my-store::before { background: linear-gradient(90deg, var(--accent), var(--accent3)); }
  .big-score-card.rival-store::before { background: linear-gradient(90deg, var(--accent2), var(--warn)); }

  .score-store-label {
    font-size: 11px;
    color: var(--text-muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .score-store-name {
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 16px;
  }
  .score-big-number {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 80px;
    line-height: 1;
    letter-spacing: 2px;
  }
  .score-big-number.my-store { color: var(--accent); }
  .score-big-number.rival-store { color: var(--accent2); }
  .score-max { font-size: 20px; color: var(--text-muted); }
  .score-grade {
    margin-top: 10px;
    display: inline-block;
    padding: 4px 18px;
    border-radius: 20px;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 1px;
  }
  .score-diff-card {
    grid-column: span 2;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px 28px;
    display: flex;
    align-items: center;
    gap: 20px;
  }
  .diff-label { font-size: 12px; color: var(--text-muted); }
  .diff-value {
    font-family: 'Bebas Neue', sans-serif;
    font-size: 40px;
  }
  .diff-positive { color: var(--accent3); }
  .diff-negative { color: var(--danger); }
  .diff-zero { color: var(--warn); }

  /* ── RADAR / BREAKDOWN ── */
  .breakdown-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 24px;
    margin-bottom: 20px;
  }
  .breakdown-title {
    font-size: 14px;
    font-weight: 700;
    color: var(--text-muted);
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 20px;
  }
  .breakdown-row {
    display: grid;
    grid-template-columns: 160px 1fr 60px 60px;
    gap: 12px;
    align-items: center;
    margin-bottom: 14px;
  }
  .breakdown-cat { font-size: 13px; font-weight: 500; }
  .bar-track {
    height: 10px;
    background: var(--score-bg);
    border-radius: 5px;
    overflow: hidden;
    position: relative;
  }
  .bar-fill-my {
    height: 100%;
    border-radius: 5px;
    background: linear-gradient(90deg, var(--accent), var(--accent3));
    transition: width 0.6s cubic-bezier(0.4,0,0.2,1);
  }
  .bar-fill-rival {
    height: 100%;
    border-radius: 5px;
    background: linear-gradient(90deg, var(--accent2), var(--warn));
    transition: width 0.6s cubic-bezier(0.4,0,0.2,1);
  }
  .breakdown-score-my {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--accent);
    text-align: right;
  }
  .breakdown-score-rival {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--accent2);
    text-align: right;
  }

  /* ── INSIGHT CARDS ── */
  .insights-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 14px;
    margin-bottom: 20px;
  }
  .insight-card {
    background: var(--surface);
    border-radius: 10px;
    padding: 18px;
    border-left: 3px solid;
  }
  .insight-card.strength { border-color: var(--accent3); }
  .insight-card.weakness { border-color: var(--danger); }
  .insight-card.opportunity { border-color: var(--warn); }
  .insight-label {
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .insight-card.strength .insight-label { color: var(--accent3); }
  .insight-card.weakness .insight-label { color: var(--danger); }
  .insight-card.opportunity .insight-label { color: var(--warn); }
  .insight-text { font-size: 13px; line-height: 1.6; color: var(--text); }

  /* ── PRINT / EXPORT ── */
  .action-bar {
    display: flex;
    gap: 12px;
    margin-top: 24px;
    flex-wrap: wrap;
  }
  .btn {
    padding: 12px 24px;
    border-radius: 8px;
    border: none;
    font-family: 'Noto Sans JP', sans-serif;
    font-size: 14px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.2s;
    letter-spacing: 0.5px;
  }
  .btn-primary {
    background: linear-gradient(135deg, var(--accent), #0099cc);
    color: #000;
  }
  .btn-primary:hover { transform: translateY(-1px); box-shadow: 0 4px 20px rgba(0,212,255,0.4); }
  .btn-secondary {
    background: var(--surface2);
    color: var(--text);
    border: 1px solid var(--border);
  }
  .btn-secondary:hover { border-color: var(--accent); color: var(--accent); }
  .btn-danger {
    background: rgba(255,77,109,0.15);
    color: var(--danger);
    border: 1px solid rgba(255,77,109,0.3);
  }
  .btn-danger:hover { background: rgba(255,77,109,0.25); }

  /* ── PROGRESS BAR ── */
  .progress-bar-wrap {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px 20px;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .progress-label { font-size: 12px; color: var(--text-muted); white-space: nowrap; }
  .progress-track {
    flex: 1;
    height: 8px;
    background: var(--score-bg);
    border-radius: 4px;
    overflow: hidden;
  }
  .progress-fill {
    height: 100%;
    border-radius: 4px;
    background: linear-gradient(90deg, var(--accent), var(--accent3));
    transition: width 0.5s ease;
  }
  .progress-pct {
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--accent);
    white-space: nowrap;
  }

  /* ── DUAL MODE TOGGLE ── */
  .mode-indicator {
    display: flex;
    gap: 8px;
    align-items: center;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 10px 16px;
    margin-bottom: 16px;
    font-size: 13px;
  }
  .mode-dot { width: 8px; height: 8px; border-radius: 50%; }
  .mode-dot.my { background: var(--accent); }
  .mode-dot.rival { background: var(--accent2); }

  /* ── RESPONSIVE ── */
  @media (max-width: 700px) {
    .score-overview { grid-template-columns: 1fr; }
    .score-diff-card { grid-column: span 1; }
    .breakdown-row { grid-template-columns: 120px 1fr 50px 50px; }
    .store-setup { grid-template-columns: 1fr; }
  }

  /* ── PRINT ── */
  @media print {
    body { background: #fff; color: #000; }
    header, .tabs, .action-bar, .progress-bar-wrap, .store-setup { display: none; }
    .panel { display: block !important; }
    * { border-color: #ccc !important; }
  }

  .canvas-wrapper {
    position: relative;
    margin: 20px auto;
    max-width: 400px;
  }
</style>
</head>
<body>

<header>
  <div>
    <div class="logo">STORE SCOUT</div>
    <div style="font-size:11px;color:var(--text-muted);letter-spacing:1px;margin-top:2px;">競合店分析システム</div>
  </div>
  <div class="header-meta">
    <div id="live-clock"></div>
    <div style="margin-top:4px;">現場調査ツール v2.0</div>
  </div>
</header>

<div class="container">

  <!-- Store Setup -->
  <div class="store-setup">
    <div class="input-group">
      <label>自店名</label>
      <input type="text" id="my-store-name" placeholder="例：○○スーパー 本店" value="">
    </div>
    <div class="input-group">
      <label>競合店名</label>
      <input type="text" id="rival-store-name" placeholder="例：△△マート 駅前店" value="">
    </div>
    <div class="input-group">
      <label>調査日</label>
      <input type="date" id="survey-date">
    </div>
    <div class="input-group">
      <label>調査時間帯</label>
      <select id="survey-time">
        <option>開店直後 (9-11時)</option>
        <option>昼ピーク (11-14時)</option>
        <option>午後 (14-17時)</option>
        <option>夕方ピーク (17-20時)</option>
        <option>閉店前 (20時以降)</option>
      </select>
    </div>
    <div class="input-group">
      <label>調査者名</label>
      <input type="text" id="surveyor-name" placeholder="担当者名">
    </div>
  </div>

  <!-- Progress -->
  <div class="progress-bar-wrap">
    <span class="progress-label">入力進捗</span>
    <div class="progress-track"><div class="progress-fill" id="progress-fill" style="width:0%"></div></div>
    <span class="progress-pct" id="progress-pct">0%</span>
    <span style="font-size:11px;color:var(--text-muted);" id="progress-detail">0 / 0 項目</span>
  </div>

  <!-- Tabs -->
  <div class="tabs" id="tabs">
    <button class="tab active" onclick="showPanel('price')">💴 価格</button>
    <button class="tab" onclick="showPanel('fresh')">🥬 鮮度・品質</button>
    <button class="tab" onclick="showPanel('assort')">📦 品揃え</button>
    <button class="tab" onclick="showPanel('service')">😊 サービス</button>
    <button class="tab" onclick="showPanel('store')">🏪 店舗環境</button>
    <button class="tab" onclick="showPanel('promo')">📣 販促</button>
    <button class="tab" onclick="showPanel('results')" id="tab-results">📊 結果</button>
  </div>

  <!-- PANELS -->

  <!-- 1. 価格力 -->
  <div class="panel active" id="panel-price">
    <div class="category-header">
      <div class="category-icon">💴</div>
      <div>
        <div class="category-title">価格競争力</div>
        <div style="font-size:12px;color:var(--text-muted);">生鮮・加工品・日配品の価格水準を評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.5</div>
    </div>
    <div class="criteria-grid" id="criteria-price"></div>
  </div>

  <!-- 2. 鮮度・品質 -->
  <div class="panel" id="panel-fresh">
    <div class="category-header">
      <div class="category-icon">🥬</div>
      <div>
        <div class="category-title">鮮度・品質</div>
        <div style="font-size:12px;color:var(--text-muted);">商品の新鮮さ・品質管理状況を評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.5</div>
    </div>
    <div class="criteria-grid" id="criteria-fresh"></div>
  </div>

  <!-- 3. 品揃え -->
  <div class="panel" id="panel-assort">
    <div class="category-header">
      <div class="category-icon">📦</div>
      <div>
        <div class="category-title">品揃え・SKU</div>
        <div style="font-size:12px;color:var(--text-muted);">商品種類数・カテゴリカバレッジを評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.2</div>
    </div>
    <div class="criteria-grid" id="criteria-assort"></div>
  </div>

  <!-- 4. サービス -->
  <div class="panel" id="panel-service">
    <div class="category-header">
      <div class="category-icon">😊</div>
      <div>
        <div class="category-title">接客・サービス</div>
        <div style="font-size:12px;color:var(--text-muted);">スタッフ対応・レジ待ち・顧客体験を評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.0</div>
    </div>
    <div class="criteria-grid" id="criteria-service"></div>
  </div>

  <!-- 5. 店舗環境 -->
  <div class="panel" id="panel-store">
    <div class="category-header">
      <div class="category-icon">🏪</div>
      <div>
        <div class="category-title">店舗環境・清潔感</div>
        <div style="font-size:12px;color:var(--text-muted);">売場づくり・陳列・清潔度・動線を評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.0</div>
    </div>
    <div class="criteria-grid" id="criteria-store"></div>
  </div>

  <!-- 6. 販促 -->
  <div class="panel" id="panel-promo">
    <div class="category-header">
      <div class="category-icon">📣</div>
      <div>
        <div class="category-title">販促・集客力</div>
        <div style="font-size:12px;color:var(--text-muted);">チラシ・POP・特売・ポイント施策を評価</div>
      </div>
      <div class="category-weight">重み係数 ×1.0</div>
    </div>
    <div class="criteria-grid" id="criteria-promo"></div>
  </div>

  <!-- RESULTS -->
  <div class="panel" id="panel-results">
    <div id="results-content"></div>
  </div>

</div><!-- /container -->

<script>
// ============================================================
//  DATA DEFINITION
// ============================================================
const CATEGORIES = [
  {
    id: 'price', label: '価格競争力', icon: '💴', weight: 1.5,
    criteria: [
      { id: 'price_staple',  name: '生鮮定番品（野菜・肉・魚）の価格水準', w: 3 },
      { id: 'price_pb',      name: 'PB（プライベートブランド）商品の充実度と価格', w: 2 },
      { id: 'price_sale',    name: '特売・週替わりセールの訴求力', w: 2 },
      { id: 'price_tokka',   name: '特価品（見切り・タイムサービス）の活用', w: 1 },
      { id: 'price_kakou',   name: '加工食品・日配品の価格競争力', w: 2 },
    ]
  },
  {
    id: 'fresh', label: '鮮度・品質', icon: '🥬', weight: 1.5,
    criteria: [
      { id: 'fresh_veg',    name: '青果の鮮度・見た目のクオリティ', w: 3 },
      { id: 'fresh_meat',   name: '精肉の色・鮮度・パッケージ清潔感', w: 3 },
      { id: 'fresh_fish',   name: '鮮魚の鮮度・品揃え・陳列温度管理', w: 3 },
      { id: 'fresh_deli',   name: '惣菜の品質・調理仕立て感', w: 2 },
      { id: 'fresh_bakery', name: 'ベーカリー・麺類の焼き立て感・鮮度', w: 1 },
    ]
  },
  {
    id: 'assort', label: '品揃え', icon: '📦', weight: 1.2,
    criteria: [
      { id: 'assort_depth',    name: 'カテゴリ深さ（各部門のSKU数）', w: 2 },
      { id: 'assort_regional', name: '地域・地場商品・産地直送品の充実', w: 2 },
      { id: 'assort_health',   name: '健康・オーガニック・機能性食品の品揃え', w: 2 },
      { id: 'assort_nonfoods', name: '日用品・非食品の品揃え', w: 1 },
      { id: 'assort_seasonal', name: '季節商品・トレンド商品への対応速度', w: 2 },
    ]
  },
  {
    id: 'service', label: 'サービス', icon: '😊', weight: 1.0,
    criteria: [
      { id: 'svc_greeting',  name: 'スタッフの挨拶・接客姿勢', w: 2 },
      { id: 'svc_register',  name: 'レジ待ち時間・スムーズさ', w: 3 },
      { id: 'svc_knowledge', name: 'スタッフの商品知識・案内力', w: 2 },
      { id: 'svc_bagging',   name: '袋詰め・包装の丁寧さ', w: 1 },
      { id: 'svc_self',      name: 'セルフレジ・キャッシュレス対応', w: 2 },
    ]
  },
  {
    id: 'store', label: '店舗環境', icon: '🏪', weight: 1.0,
    criteria: [
      { id: 'env_clean',    name: '売場・バックヤード境界の清潔感', w: 2 },
      { id: 'env_layout',   name: '売場レイアウト・回遊しやすさ', w: 2 },
      { id: 'env_display',  name: '陳列の見やすさ・フェイス管理', w: 2 },
      { id: 'env_lighting', name: '照明・温度・BGMの快適さ', w: 1 },
      { id: 'env_parking',  name: '駐車場・アクセスの利便性', w: 1 },
    ]
  },
  {
    id: 'promo', label: '販促', icon: '📣', weight: 1.0,
    criteria: [
      { id: 'promo_flyer',  name: 'チラシ・折込の充実度と価格訴求力', w: 2 },
      { id: 'promo_pop',    name: '売場POP・値札の見やすさ・訴求力', w: 2 },
      { id: 'promo_point',  name: 'ポイントカード・アプリ会員施策', w: 2 },
      { id: 'promo_event',  name: '試食・イベント・デモ販の活発さ', w: 2 },
      { id: 'promo_sns',    name: 'SNS・デジタル販促の活用度', w: 1 },
    ]
  },
];

const SCORE_LABELS = ['要改善', '不十分', '普通', '良い', '優秀'];

// ============================================================
//  STATE
// ============================================================
const scores = {}; // { criterionId: { my: 0, rival: 0, note: '' } }
CATEGORIES.forEach(cat => cat.criteria.forEach(c => {
  scores[c.id] = { my: 0, rival: 0, note: '' };
}));

// ============================================================
//  INIT
// ============================================================
//  SAMPLE DATA
// ============================================================
const SAMPLE_DATA = {
  // 価格競争力
  price_staple:  { my: 3, rival: 4, note: '競合は週3回の特売で差をつけている' },
  price_pb:      { my: 4, rival: 3, note: '自店PBは品質・価格ともに好評' },
  price_sale:    { my: 3, rival: 5, note: '競合の目玉商品チラシが非常に強力' },
  price_tokka:   { my: 4, rival: 3, note: 'タイムサービスは自店が積極的' },
  price_kakou:   { my: 3, rival: 4, note: '競合は加工食品の特売頻度が高い' },
  // 鮮度・品質
  fresh_veg:     { my: 5, rival: 4, note: '地場野菜コーナーが好評・鮮度◎' },
  fresh_meat:    { my: 4, rival: 4, note: '両店ほぼ同水準。競合は色鮮やか' },
  fresh_fish:    { my: 3, rival: 5, note: '競合は港直送を前面訴求、差が大きい' },
  fresh_deli:    { my: 4, rival: 3, note: '自店惣菜は手作り感が強み' },
  fresh_bakery:  { my: 5, rival: 3, note: '自店ベーカリーは焼き立て時間が多い' },
  // 品揃え
  assort_depth:  { my: 4, rival: 4, note: '主要カテゴリのSKU数は互角' },
  assort_regional:{ my: 5, rival: 2, note: '地場商品・産地直送は自店の大きな差別化' },
  assort_health: { my: 3, rival: 4, note: '競合のオーガニックゾーンが拡大中' },
  assort_nonfoods:{ my: 3, rival: 4, note: '競合は日用品フロアが広い' },
  assort_seasonal:{ my: 4, rival: 3, note: '自店は季節提案の切り替えが早い' },
  // サービス
  svc_greeting:  { my: 4, rival: 3, note: '朝礼での接客訓練が効果的' },
  svc_register:  { my: 3, rival: 5, note: '競合はセミセルフレジ8台で待ち時間ほぼゼロ' },
  svc_knowledge: { my: 4, rival: 3, note: '生鮮スタッフの知識・説明力は自店が上' },
  svc_bagging:   { my: 4, rival: 4, note: '両店ともマイバッグ対応◎' },
  svc_self:      { my: 2, rival: 5, note: '競合はPayPay/交通系IC全対応。自店は要整備' },
  // 店舗環境
  env_clean:     { my: 5, rival: 4, note: '自店はクレンリネス管理が徹底されている' },
  env_layout:    { my: 4, rival: 3, note: '自店は食料品→惣菜→レジの動線が自然' },
  env_display:   { my: 3, rival: 4, note: '競合のゴールデンゾーン活用が上手い' },
  env_lighting:  { my: 4, rival: 4, note: '生鮮照明は両店ともLED演色性良好' },
  env_parking:   { my: 3, rival: 5, note: '競合は200台・屋根付き。自店は80台で不足気味' },
  // 販促
  promo_flyer:   { my: 4, rival: 5, note: '競合チラシは週2回・商圏カバー率高い' },
  promo_pop:     { my: 5, rival: 3, note: '自店POPは手書き風で親しみやすく好評' },
  promo_point:   { my: 3, rival: 5, note: '競合アプリは会員30万人・クーポン配信が強力' },
  promo_event:   { my: 4, rival: 3, note: '自店の試食・産地フェアは集客効果大' },
  promo_sns:     { my: 2, rival: 4, note: 'Instagram・LINE活用は競合が大きくリード' },
};

// ============================================================
window.addEventListener('DOMContentLoaded', () => {
  // Date default
  document.getElementById('survey-date').valueAsDate = new Date();

  // Clock
  updateClock();
  setInterval(updateClock, 1000);

  // Render criteria
  CATEGORIES.forEach(cat => renderCategory(cat));

  // Load sample data
  loadSampleData();
});

function updateClock() {
  const now = new Date();
  document.getElementById('live-clock').textContent =
    now.toLocaleTimeString('ja-JP', { hour: '2-digit', minute: '2-digit', second: '2-digit' });
}

// ============================================================
//  LOAD SAMPLE DATA
// ============================================================
function loadSampleData() {
  document.getElementById('my-store-name').value = 'フレッシュマート 中央店';
  document.getElementById('rival-store-name').value = 'メガストア 駅前店';
  document.getElementById('surveyor-name').value = '田中 一郎（MD部）';
  document.getElementById('survey-time').selectedIndex = 3;

  Object.entries(SAMPLE_DATA).forEach(([id, data]) => {
    scores[id].my = data.my;
    scores[id].rival = data.rival;
    scores[id].note = data.note;
    for (let n = 1; n <= 5; n++) {
      const mb = document.getElementById('my-' + id + '-' + n);
      const rb = document.getElementById('rival-' + id + '-' + n);
      if (mb) { mb.className = 'score-btn'; if (n === data.my) mb.classList.add('selected-' + n); }
      if (rb) { rb.className = 'score-btn'; if (n === data.rival) rb.classList.add('selected-' + n); }
    }
    const noteEl = document.getElementById('note-' + id);
    if (noteEl) noteEl.value = data.note;
  });

  updateProgress();

  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById('panel-results').classList.add('active');
  document.getElementById('tab-results').classList.add('active');
  renderResults();
}


// ============================================================
//  RENDER CRITERIA
// ============================================================
function renderCategory(cat) {
  const container = document.getElementById('criteria-' + cat.id);
  container.innerHTML = '';

  cat.criteria.forEach(c => {
    const card = document.createElement('div');
    card.className = 'criterion-card';
    card.innerHTML = `
      <div class="criterion-top">
        <div class="criterion-name">${c.name}</div>
        <div class="criterion-weight-badge">重み ×${c.w}</div>
      </div>

      <div class="mode-indicator">
        <div class="mode-dot my"></div>
        <span style="color:var(--accent);font-weight:600;font-size:12px;">自店評価</span>
        <span style="color:var(--text-muted);font-size:11px;margin-left:4px;">（1=最低 〜 5=最高）</span>
      </div>
      <div class="score-buttons" id="my-btns-${c.id}">
        ${[1,2,3,4,5].map(n=>`<button class="score-btn" onclick="setScore('${c.id}','my',${n})" id="my-${c.id}-${n}">${n}</button>`).join('')}
      </div>
      <div class="score-labels">
        ${SCORE_LABELS.map(l=>`<div class="score-label">${l}</div>`).join('')}
      </div>

      <div class="mode-indicator" style="margin-top:12px;">
        <div class="mode-dot rival"></div>
        <span style="color:var(--accent2);font-weight:600;font-size:12px;">競合店評価</span>
        <span style="color:var(--text-muted);font-size:11px;margin-left:4px;">（1=最低 〜 5=最高）</span>
      </div>
      <div class="score-buttons" id="rival-btns-${c.id}">
        ${[1,2,3,4,5].map(n=>`<button class="score-btn" onclick="setScore('${c.id}','rival',${n})" id="rival-${c.id}-${n}">${n}</button>`).join('')}
      </div>
      <div class="score-labels">
        ${SCORE_LABELS.map(l=>`<div class="score-label">${l}</div>`).join('')}
      </div>

      <div class="criterion-note">
        <input type="text" placeholder="📝 気づき・メモを入力..." id="note-${c.id}"
          onchange="scores['${c.id}'].note = this.value">
      </div>
    `;
    container.appendChild(card);
  });
}

// ============================================================
//  SCORE LOGIC
// ============================================================
function setScore(id, who, val) {
  scores[id][who] = val;
  // Update buttons
  for (let n = 1; n <= 5; n++) {
    const btn = document.getElementById(`${who}-${id}-${n}`);
    btn.className = 'score-btn';
    if (n === val) btn.classList.add(`selected-${n}`);
  }
  updateProgress();
}

function updateProgress() {
  let total = 0, filled = 0;
  CATEGORIES.forEach(cat => cat.criteria.forEach(c => {
    total += 2; // my + rival
    if (scores[c.id].my > 0) filled++;
    if (scores[c.id].rival > 0) filled++;
  }));
  const pct = Math.round(filled / total * 100);
  document.getElementById('progress-fill').style.width = pct + '%';
  document.getElementById('progress-pct').textContent = pct + '%';
  document.getElementById('progress-detail').textContent = `${filled} / ${total} 項目`;
}

// ============================================================
//  PANEL NAVIGATION
// ============================================================
function showPanel(id) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById('panel-' + id).classList.add('active');
  event.currentTarget.classList.add('active');

  if (id === 'results') renderResults();
}

// ============================================================
//  CALCULATE SCORES
// ============================================================
function calcCategoryScore(cat, who) {
  let sum = 0, weightSum = 0;
  cat.criteria.forEach(c => {
    const s = scores[c.id][who];
    if (s > 0) { sum += s * c.w; weightSum += c.w * 5; }
    else { weightSum += c.w * 5; }
  });
  return weightSum > 0 ? (sum / weightSum) * 100 : 0;
}

function calcTotalScore(who) {
  let weightedSum = 0, maxSum = 0;
  CATEGORIES.forEach(cat => {
    const catPct = calcCategoryScore(cat, who) / 100; // 0-1
    weightedSum += catPct * cat.weight;
    maxSum += cat.weight;
  });
  return maxSum > 0 ? Math.round(weightedSum / maxSum * 100) : 0;
}

function getGrade(score) {
  if (score >= 85) return { label: 'S 卓越', color: '#00ff9d', bg: 'rgba(0,255,157,0.1)' };
  if (score >= 70) return { label: 'A 優秀', color: '#00d4ff', bg: 'rgba(0,212,255,0.1)' };
  if (score >= 55) return { label: 'B 標準', color: '#ffd166', bg: 'rgba(255,209,102,0.1)' };
  if (score >= 40) return { label: 'C 要改善', color: '#ff8c42', bg: 'rgba(255,140,66,0.1)' };
  return { label: 'D 危機', color: '#ff4d6d', bg: 'rgba(255,77,109,0.1)' };
}

// ============================================================
//  RENDER RESULTS
// ============================================================
function renderResults() {
  const myName = document.getElementById('my-store-name').value || '自店';
  const rivalName = document.getElementById('rival-store-name').value || '競合店';
  const surveyDate = document.getElementById('survey-date').value;
  const surveyTime = document.getElementById('survey-time').value;
  const surveyor = document.getElementById('surveyor-name').value;

  const myTotal = calcTotalScore('my');
  const rivalTotal = calcTotalScore('rival');
  const diff = myTotal - rivalTotal;
  const myGrade = getGrade(myTotal);
  const rivalGrade = getGrade(rivalTotal);

  // Category breakdowns
  let breakdownRows = '';
  CATEGORIES.forEach(cat => {
    const myPct = Math.round(calcCategoryScore(cat, 'my'));
    const rivalPct = Math.round(calcCategoryScore(cat, 'rival'));
    breakdownRows += `
      <div class="breakdown-row">
        <div class="breakdown-cat">${cat.icon} ${cat.label}</div>
        <div>
          <div class="bar-track" style="margin-bottom:4px;">
            <div class="bar-fill-my" style="width:${myPct}%"></div>
          </div>
          <div class="bar-track">
            <div class="bar-fill-rival" style="width:${rivalPct}%"></div>
          </div>
        </div>
        <div class="breakdown-score-my">${myPct}pt</div>
        <div class="breakdown-score-rival">${rivalPct}pt</div>
      </div>
    `;
  });

  // Insights
  const strengths = [], weaknesses = [], opportunities = [];
  CATEGORIES.forEach(cat => {
    const myPct = Math.round(calcCategoryScore(cat, 'my'));
    const rivalPct = Math.round(calcCategoryScore(cat, 'rival'));
    if (myPct >= 70) strengths.push(`${cat.icon} ${cat.label}（${myPct}pt）`);
    if (myPct < 50) weaknesses.push(`${cat.icon} ${cat.label}（${myPct}pt）`);
    if (rivalPct > myPct + 15) opportunities.push(`${cat.icon} ${cat.label}（競合比 -${rivalPct - myPct}pt）`);
  });

  const insightsHTML = `
    <div class="insights-grid">
      <div class="insight-card strength">
        <div class="insight-label">✅ 自店の強み</div>
        <div class="insight-text">${strengths.length ? strengths.join('<br>') : '70pt以上の項目なし'}</div>
      </div>
      <div class="insight-card weakness">
        <div class="insight-label">⚠️ 自店の弱み</div>
        <div class="insight-text">${weaknesses.length ? weaknesses.join('<br>') : '50pt未満の項目なし'}</div>
      </div>
      <div class="insight-card opportunity">
        <div class="insight-label">🎯 要強化（競合差 15pt超）</div>
        <div class="insight-text">${opportunities.length ? opportunities.join('<br>') : '大きな差の項目なし'}</div>
      </div>
    </div>
  `;

  // Criterion detail table
  let detailRows = '';
  CATEGORIES.forEach(cat => {
    cat.criteria.forEach(c => {
      const my = scores[c.id].my;
      const rival = scores[c.id].rival;
      const d = my - rival;
      const dColor = d > 0 ? 'var(--accent3)' : d < 0 ? 'var(--danger)' : 'var(--text-muted)';
      const note = scores[c.id].note || '—';
      detailRows += `
        <tr style="border-bottom:1px solid var(--border);">
          <td style="padding:8px 6px;font-size:12px;color:var(--text-muted);">${cat.icon}</td>
          <td style="padding:8px 6px;font-size:13px;">${c.name}</td>
          <td style="padding:8px 6px;text-align:center;font-family:'Space Mono',monospace;color:var(--accent);">${my || '—'}</td>
          <td style="padding:8px 6px;text-align:center;font-family:'Space Mono',monospace;color:var(--accent2);">${rival || '—'}</td>
          <td style="padding:8px 6px;text-align:center;font-family:'Space Mono',monospace;color:${dColor};">${my && rival ? (d > 0 ? '+' : '') + d : '—'}</td>
          <td style="padding:8px 6px;font-size:12px;color:var(--text-muted);">${note}</td>
        </tr>
      `;
    });
  });

  document.getElementById('results-content').innerHTML = `
    <div style="margin-bottom:20px;">
      <div style="font-size:11px;color:var(--text-muted);letter-spacing:1px;">
        📅 ${surveyDate} ${surveyTime}　👤 ${surveyor || '記録者未入力'}
      </div>
    </div>

    <!-- Big Scores -->
    <div class="score-overview">
      <div class="big-score-card my-store">
        <div class="score-store-label">自店</div>
        <div class="score-store-name">${myName}</div>
        <div class="score-big-number my-store">${myTotal}<span class="score-max">/100</span></div>
        <span class="score-grade" style="background:${myGrade.bg};color:${myGrade.color};border:1px solid ${myGrade.color};">
          ${myGrade.label}
        </span>
      </div>
      <div class="big-score-card rival-store">
        <div class="score-store-label">競合店</div>
        <div class="score-store-name">${rivalName}</div>
        <div class="score-big-number rival-store">${rivalTotal}<span class="score-max">/100</span></div>
        <span class="score-grade" style="background:${rivalGrade.bg};color:${rivalGrade.color};border:1px solid ${rivalGrade.color};">
          ${rivalGrade.label}
        </span>
      </div>
      <div class="score-diff-card">
        <div>
          <div class="diff-label">スコア差（自店 − 競合）</div>
          <div class="diff-value ${diff > 0 ? 'diff-positive' : diff < 0 ? 'diff-negative' : 'diff-zero'}">
            ${diff > 0 ? '+' : ''}${diff}pt
          </div>
        </div>
        <div style="flex:1;font-size:13px;color:var(--text-muted);line-height:1.7;">
          ${diff > 10 ? '✅ 自店が競合を大きくリード。優位性を維持・強化しましょう。'
          : diff > 0 ? '🟡 自店がわずかにリード。引き続き強みを伸ばしましょう。'
          : diff === 0 ? '🟠 同点。差別化ポイントの明確化が急務です。'
          : diff > -10 ? '🔴 競合にやや遅れています。重点項目の集中改善を。'
          : '🚨 競合に大きく遅れています。緊急対策が必要です。'}
        </div>
      </div>
    </div>

    <!-- Category Breakdown -->
    <div class="breakdown-section">
      <div class="breakdown-title">カテゴリ別スコア比較</div>
      <div style="display:flex;gap:20px;margin-bottom:16px;font-size:12px;">
        <span><span style="display:inline-block;width:12px;height:8px;border-radius:2px;background:linear-gradient(90deg,var(--accent),var(--accent3));margin-right:6px;"></span>自店</span>
        <span><span style="display:inline-block;width:12px;height:8px;border-radius:2px;background:linear-gradient(90deg,var(--accent2),var(--warn));margin-right:6px;"></span>競合店</span>
      </div>
      ${breakdownRows}
    </div>

    <!-- Insights -->
    <div class="breakdown-section">
      <div class="breakdown-title">分析インサイト</div>
      ${insightsHTML}
    </div>

    <!-- Detail Table -->
    <div class="breakdown-section">
      <div class="breakdown-title">評価項目詳細</div>
      <div style="overflow-x:auto;">
        <table style="width:100%;border-collapse:collapse;">
          <thead>
            <tr style="border-bottom:2px solid var(--border);">
              <th style="padding:8px 6px;text-align:left;font-size:11px;color:var(--text-muted);letter-spacing:1px;"></th>
              <th style="padding:8px 6px;text-align:left;font-size:11px;color:var(--text-muted);letter-spacing:1px;">評価項目</th>
              <th style="padding:8px 6px;text-align:center;font-size:11px;color:var(--accent);letter-spacing:1px;">自店</th>
              <th style="padding:8px 6px;text-align:center;font-size:11px;color:var(--accent2);letter-spacing:1px;">競合</th>
              <th style="padding:8px 6px;text-align:center;font-size:11px;color:var(--text-muted);letter-spacing:1px;">差</th>
              <th style="padding:8px 6px;text-align:left;font-size:11px;color:var(--text-muted);letter-spacing:1px;">メモ</th>
            </tr>
          </thead>
          <tbody>${detailRows}</tbody>
        </table>
      </div>
    </div>

    <!-- Action Bar -->
    <div class="action-bar">
      <button class="btn btn-primary" onclick="window.print()">🖨️ 印刷・PDF出力</button>
      <button class="btn btn-secondary" onclick="exportCSV()">📥 CSVエクスポート</button>
      <button class="btn btn-danger" onclick="resetAll()">🗑️ データリセット</button>
    </div>
  `;
}

// ============================================================
//  EXPORT CSV
// ============================================================
function exportCSV() {
  const myName = document.getElementById('my-store-name').value || '自店';
  const rivalName = document.getElementById('rival-store-name').value || '競合店';
  const date = document.getElementById('survey-date').value;

  let csv = `調査日,${date}\n自店,${myName}\n競合店,${rivalName}\n\n`;
  csv += `カテゴリ,評価項目,自店スコア,競合スコア,差,メモ\n`;

  CATEGORIES.forEach(cat => {
    cat.criteria.forEach(c => {
      const s = scores[c.id];
      const diff = s.my && s.rival ? s.my - s.rival : '';
      csv += `${cat.label},${c.name},${s.my||''},${s.rival||''},${diff},"${s.note||''}"\n`;
    });
  });

  const blob = new Blob(['\uFEFF' + csv], { type: 'text/csv;charset=utf-8' });
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = `競合分析_${date}_${myName}.csv`;
  a.click();
}

// ============================================================
//  RESET
// ============================================================
function resetAll() {
  if (!confirm('全データをリセットしますか？')) return;
  CATEGORIES.forEach(cat => cat.criteria.forEach(c => {
    scores[c.id] = { my: 0, rival: 0, note: '' };
    for (let n = 1; n <= 5; n++) {
      const mb = document.getElementById(`my-${c.id}-${n}`);
      const rb = document.getElementById(`rival-${c.id}-${n}`);
      if (mb) mb.className = 'score-btn';
      if (rb) rb.className = 'score-btn';
    }
    const noteEl = document.getElementById(`note-${c.id}`);
    if (noteEl) noteEl.value = '';
  }));
  updateProgress();
}
</script>
</body>
</html>
