<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Most Chronically Online NFL Fans | Bookies.com</title>
<link href="https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600;700&family=Source+Sans+3:wght@400;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bookies-blue: #1A3A5C;
    --bookies-blue-accent: #3B7DD8;
    --bookies-border: #E2E8F0;
    --bookies-text: #1A202C;
    --bookies-muted: #718096;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body {
    font-family: 'Source Sans 3', 'Segoe UI', sans-serif;
    background: #FAFBFD;
    color: var(--bookies-text);
    min-height: 100vh;
  }
  .top-bar { height: 5px; background: linear-gradient(90deg, var(--bookies-blue), var(--bookies-blue-accent), var(--bookies-blue)); }
  .container { max-width: 880px; margin: 0 auto; padding: 36px 20px 60px; }
  .header { text-align: center; margin-bottom: 36px; }
  .header h1 { font-family: 'Oswald', sans-serif; font-size: clamp(26px, 5vw, 44px); font-weight: 700; text-transform: uppercase; letter-spacing: 0.5px; line-height: 1.1; margin-bottom: 12px; color: var(--bookies-blue); }
  .header h1 .accent { color: var(--bookies-blue-accent); }
  .header .subtitle { font-size: 15px; color: var(--bookies-muted); max-width: 520px; margin: 0 auto; line-height: 1.6; }
  .controls { display: flex; justify-content: center; gap: 6px; margin-bottom: 28px; flex-wrap: wrap; }
  .controls button { font-family: 'Source Sans 3', sans-serif; font-size: 13px; font-weight: 600; padding: 7px 18px; border: 1.5px solid var(--bookies-border); border-radius: 6px; background: #fff; color: var(--bookies-muted); cursor: pointer; transition: all 0.2s ease; }
  .controls button:hover { border-color: var(--bookies-blue-accent); color: var(--bookies-blue); }
  .controls button.active { background: var(--bookies-blue); border-color: var(--bookies-blue); color: #fff; }
  .chart-card { background: #fff; border-radius: 12px; border: 1px solid var(--bookies-border); box-shadow: 0 1px 3px rgba(0,0,0,0.04), 0 4px 12px rgba(0,0,0,0.03); overflow: hidden; }
  .chart-header-row { display: grid; grid-template-columns: 48px 1fr 60px; align-items: center; gap: 12px; padding: 12px 20px; background: var(--bookies-blue); color: #fff; font-family: 'Oswald', sans-serif; font-size: 11px; font-weight: 600; letter-spacing: 1.5px; text-transform: uppercase; }
  .chart-header-row .h-score { text-align: right; }
  .team-row { display: grid; grid-template-columns: 48px 1fr 60px; align-items: center; gap: 12px; padding: 9px 20px; border-bottom: 1px solid var(--bookies-border); cursor: pointer; transition: background 0.15s ease; opacity: 0; transform: translateY(8px); }
  .team-row:last-child { border-bottom: none; }
  .team-row:hover { background: rgba(59, 125, 216, 0.04); }
  .team-row.top3 { padding: 11px 20px; }
  .team-row.even { background: rgba(245,247,250,0.5); }
  .team-row.even:hover { background: rgba(59, 125, 216, 0.04); }
  .team-row.animate { opacity: 1; transform: translateY(0); }
  .rank-col { width: 36px; height: 36px; display: flex; align-items: center; justify-content: center; }
  .rank-num { font-family: 'Oswald', sans-serif; font-size: 15px; font-weight: 600; color: var(--bookies-muted); }
  .team-info { display: flex; align-items: center; gap: 12px; min-width: 0; }
  .team-logo { width: 32px; height: 32px; object-fit: contain; flex-shrink: 0; }
  .team-row.top3 .team-logo { width: 38px; height: 38px; }
  .team-details { flex: 1; min-width: 0; }
  .team-name-row { display: flex; align-items: center; gap: 8px; }
  .team-name { font-family: 'Oswald', sans-serif; font-size: 14px; font-weight: 500; text-transform: uppercase; letter-spacing: 0.3px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; color: var(--bookies-text); }
  .team-row.top3 .team-name { font-size: 16px; font-weight: 600; }
  .conf-tag { font-size: 9px; font-weight: 700; letter-spacing: 0.8px; padding: 1px 6px; border-radius: 3px; text-transform: uppercase; flex-shrink: 0; }
  .conf-tag.nfc { background: #EBF4FF; color: #2B6CB0; }
  .conf-tag.afc { background: #FFF5F5; color: #C53030; }
  .bar-container { height: 5px; background: #EDF2F7; border-radius: 3px; overflow: hidden; margin-top: 5px; }
  .bar { height: 100%; border-radius: 3px; width: 0%; transition: width 1s cubic-bezier(0.25, 0.46, 0.45, 0.94); background: linear-gradient(90deg, var(--bookies-blue), var(--bookies-blue-accent)); }
  .bar.gold { background: linear-gradient(90deg, #B7791F, #D69E2E); }
  .bar.silver { background: linear-gradient(90deg, #718096, #A0AEC0); }
  .bar.bronze { background: linear-gradient(90deg, #9C6E3C, #C4956A); }
  .score-col { font-family: 'Oswald', sans-serif; font-size: 17px; font-weight: 700; text-align: right; color: var(--bookies-blue); }
  .tooltip { display: none; position: fixed; background: #fff; border: 1px solid var(--bookies-border); border-radius: 10px; padding: 16px 20px; z-index: 1000; box-shadow: 0 4px 20px rgba(0,0,0,0.12); pointer-events: none; min-width: 230px; }
  .tooltip.visible { display: block; }
  .tooltip-team { font-family: 'Oswald', sans-serif; font-size: 16px; font-weight: 600; text-transform: uppercase; margin-bottom: 10px; display: flex; align-items: center; gap: 10px; color: var(--bookies-blue); }
  .tooltip-team img { width: 30px; height: 30px; object-fit: contain; }
  .tooltip-stats { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
  .tooltip-stat-label { font-size: 10px; color: var(--bookies-muted); text-transform: uppercase; letter-spacing: 1px; font-weight: 600; }
  .tooltip-stat-value { font-family: 'Oswald', sans-serif; font-size: 22px; font-weight: 700; color: var(--bookies-blue); }
  .tooltip-percentile { font-size: 12px; color: var(--bookies-muted); margin-top: 10px; padding-top: 10px; border-top: 1px solid var(--bookies-border); }
  .footer { text-align: center; margin-top: 32px; }
  .footer-brand { font-family: 'Oswald', sans-serif; font-weight: 700; font-size: 13px; letter-spacing: 2px; text-transform: uppercase; color: var(--bookies-blue); margin-bottom: 4px; }
  .footer-note { font-size: 12px; color: var(--bookies-muted); line-height: 1.5; }
  @media (max-width: 600px) {
    .container { padding: 20px 12px 40px; }
    .team-row, .chart-header-row { grid-template-columns: 40px 1fr 46px; gap: 8px; padding-left: 12px; padding-right: 12px; }
    .team-logo { width: 26px; height: 26px; }
    .team-row.top3 .team-logo { width: 30px; height: 30px; }
    .team-name { font-size: 12px; }
    .team-row.top3 .team-name { font-size: 14px; }
    .score-col { font-size: 14px; }
    .conf-tag { display: none; }
    .controls button { font-size: 12px; padding: 6px 12px; }
  }
</style>
</head>
<body>
<div class="top-bar"></div>
<div class="container">
  <div class="header">
    <h1>Most <span class="accent">Chronically Online</span><br>NFL Fans</h1>
    <p class="subtitle">Ranking all 32 NFL fanbases by their online activity score — measuring social media engagement, forum activity, and digital discourse.</p>
  </div>
  <div class="controls">
    <button class="active" data-filter="all">All Teams</button>
    <button data-filter="nfc">NFC</button>
    <button data-filter="afc">AFC</button>
    <button data-filter="top10">Top 10</button>
    <button data-filter="bottom10">Bottom 10</button>
  </div>
  <div class="chart-card">
    <div class="chart-header-row">
      <div>Rank</div><div>Team</div><div class="h-score">Score</div>
    </div>
    <div id="chart"></div>
  </div>
  <div class="footer">
    <div class="footer-brand">Bookies.com</div>
    <div class="footer-note">Data compiled from social media engagement, subreddit activity, forum posts, and online discourse metrics.</div>
  </div>
</div>
<div class="tooltip" id="tooltip"></div>

<svg style="display:none">
  <defs>
    <radialGradient id="grad-gold" cx="0.35" cy="0.3"><stop offset="0%" stop-color="#FFE066"/><stop offset="100%" stop-color="#D4A012"/></radialGradient>
    <radialGradient id="grad-silver" cx="0.35" cy="0.3"><stop offset="0%" stop-color="#F7FAFC"/><stop offset="100%" stop-color="#CBD5E0"/></radialGradient>
    <radialGradient id="grad-bronze" cx="0.35" cy="0.3"><stop offset="0%" stop-color="#F6E2C8"/><stop offset="100%" stop-color="#C4956A"/></radialGradient>
  </defs>
</svg>

<script>
const teams = [
  { rank:1, name:"Chicago Bears", abbr:"chi", wiki:"commons/5/5c/Chicago_Bears_logo.svg", score:808, conf:"NFC" },
  { rank:2, name:"Cincinnati Bengals", abbr:"cin", wiki:"commons/8/81/Cincinnati_Bengals_logo.svg", score:665, conf:"AFC" },
  { rank:3, name:"Seattle Seahawks", abbr:"sea", wiki:"en/a/a3/Seattle_Seahawks_2024_logo.svg", score:585, conf:"NFC" },
  { rank:4, name:"New England Patriots", abbr:"ne", wiki:"en/b/b9/New_England_Patriots_logo.svg", score:425, conf:"AFC" },
  { rank:5, name:"Philadelphia Eagles", abbr:"phi", wiki:"en/a/a3/Philadelphia_Eagles_logo.svg", score:402, conf:"NFC" },
  { rank:6, name:"San Francisco 49ers", abbr:"sf", wiki:"commons/3/3a/San_Francisco_49ers_logo.svg", score:388, conf:"NFC" },
  { rank:7, name:"Washington Commanders", abbr:"wsh", wiki:"en/5/54/Washington_Commanders_logo.svg", score:380, conf:"NFC" },
  { rank:8, name:"Detroit Lions", abbr:"det", wiki:"en/7/71/Detroit_Lions_logo.svg", score:374, conf:"NFC" },
  { rank:9, name:"Minnesota Vikings", abbr:"min", wiki:"en/4/48/Minnesota_Vikings_logo.svg", score:366, conf:"NFC" },
  { rank:10, name:"Pittsburgh Steelers", abbr:"pit", wiki:"commons/c/c8/Pittsburgh_Steelers_logo.svg", score:352, conf:"AFC" },
  { rank:11, name:"Green Bay Packers", abbr:"gb", wiki:"commons/5/50/Green_Bay_Packers_logo.svg", score:345, conf:"NFC" },
  { rank:12, name:"Atlanta Falcons", abbr:"atl", wiki:"en/c/c5/Atlanta_Falcons_logo.svg", score:339, conf:"NFC" },
  { rank:13, name:"Houston Texans", abbr:"hou", wiki:"en/2/28/Houston_Texans_logo.svg", score:332, conf:"AFC" },
  { rank:14, name:"Baltimore Ravens", abbr:"bal", wiki:"en/1/16/Baltimore_Ravens_logo.svg", score:326, conf:"AFC" },
  { rank:15, name:"New York Giants", abbr:"nyg", wiki:"en/6/60/New_York_Giants_logo.svg", score:319, conf:"NFC" },
  { rank:16, name:"Kansas City Chiefs", abbr:"kc", wiki:"en/e/e1/Kansas_City_Chiefs_logo.svg", score:312, conf:"AFC" },
  { rank:17, name:"New Orleans Saints", abbr:"no", wiki:"en/5/50/New_Orleans_Saints_logo.svg", score:305, conf:"NFC" },
  { rank:18, name:"Denver Broncos", abbr:"den", wiki:"en/4/44/Denver_Broncos_logo.svg", score:297, conf:"AFC" },
  { rank:19, name:"Tampa Bay Buccaneers", abbr:"tb", wiki:"en/a/a2/Tampa_Bay_Buccaneers_logo.svg", score:288, conf:"NFC" },
  { rank:20, name:"Miami Dolphins", abbr:"mia", wiki:"en/4/44/Miami_Dolphins_logo.svg", score:279, conf:"AFC" },
  { rank:21, name:"Los Angeles Chargers", abbr:"lac", wiki:"en/a/a6/Los_Angeles_Chargers_logo.svg", score:270, conf:"AFC" },
  { rank:22, name:"Los Angeles Rams", abbr:"lar", wiki:"en/8/8b/Los_Angeles_Rams_logo.svg", score:261, conf:"NFC" },
  { rank:23, name:"Indianapolis Colts", abbr:"ind", wiki:"commons/0/00/Indianapolis_Colts_logo.svg", score:252, conf:"AFC" },
  { rank:24, name:"New York Jets", abbr:"nyj", wiki:"en/4/4e/New_York_Jets_logo_%282024%29.svg", score:243, conf:"AFC" },
  { rank:25, name:"Arizona Cardinals", abbr:"ari", wiki:"en/7/72/Arizona_Cardinals_logo.svg", score:233, conf:"NFC" },
  { rank:26, name:"Tennessee Titans", abbr:"ten", wiki:"en/2/20/Tennessee_Titans_logo.svg", score:224, conf:"AFC" },
  { rank:27, name:"Las Vegas Raiders", abbr:"lv", wiki:"en/d/d1/Las_Vegas_Raiders_wordmark.svg", score:215, conf:"AFC" },
  { rank:28, name:"Buffalo Bills", abbr:"buf", wiki:"en/7/77/Buffalo_Bills_logo.svg", score:206, conf:"AFC" },
  { rank:29, name:"Carolina Panthers", abbr:"car", wiki:"en/1/1c/Carolina_Panthers_logo.svg", score:197, conf:"NFC" },
  { rank:30, name:"Jacksonville Jaguars", abbr:"jax", wiki:"en/1/19/Jacksonville_Jaguars_logo.svg", score:188, conf:"AFC" },
  { rank:31, name:"Cleveland Browns", abbr:"cle", wiki:"en/d/d9/Cleveland_Browns_logo.svg", score:116, conf:"AFC" },
  { rank:32, name:"Dallas Cowboys", abbr:"dal", wiki:"commons/1/15/Dallas_Cowboys.svg", score:94, conf:"NFC" }
];

const MAX = 808;
const chart = document.getElementById('chart');
const tooltipEl = document.getElementById('tooltip');

function logoThumb(team) {
  const file = team.wiki.split('/').pop();
  const decoded = file.replace(/%28/g,'(').replace(/%29/g,')');
  const isCommons = team.wiki.startsWith('commons');
  const base = isCommons ? 'commons' : 'en';
  const subpath = team.wiki.replace(/^(commons|en)\//, '');
  return `https://upload.wikimedia.org/wikipedia/${base}/thumb/${subpath}/100px-${decoded}.png`;
}

function espnLogo(abbr) {
  return `https://a.espncdn.com/i/teamlogos/nfl/500/${abbr}.png`;
}

function medalSvg(rank) {
  const c = {
    1: { grad:'url(#grad-gold)', stroke:'#B7791F', ribbon:'#D69E2E', tf:'#7C5A00', n:'1' },
    2: { grad:'url(#grad-silver)', stroke:'#A0AEC0', ribbon:'#A0AEC0', tf:'#4A5568', n:'2' },
    3: { grad:'url(#grad-bronze)', stroke:'#C4956A', ribbon:'#C4956A', tf:'#6B4226', n:'3' }
  }[rank];
  return `<svg width="32" height="32" viewBox="0 0 32 32" fill="none"><path d="M16 2 L13.5 9 L16 7.5 L18.5 9 Z" fill="${c.ribbon}"/><circle cx="16" cy="18" r="11.5" fill="${c.grad}" stroke="${c.stroke}" stroke-width="1.5"/><text x="16" y="22.5" text-anchor="middle" font-size="13" font-weight="800" font-family="Oswald,sans-serif" fill="${c.tf}">${c.n}</text></svg>`;
}

function renderChart(filter) {
  chart.innerHTML = '';
  let list = [...teams];
  if (filter === 'nfc') list = teams.filter(t => t.conf === 'NFC');
  else if (filter === 'afc') list = teams.filter(t => t.conf === 'AFC');
  else if (filter === 'top10') list = teams.slice(0, 10);
  else if (filter === 'bottom10') list = teams.slice(-10);

  list.forEach((team, i) => {
    const row = document.createElement('div');
    const isTop3 = team.rank <= 3;
    row.className = 'team-row' + (isTop3 ? ' top3' : '') + (i % 2 === 1 ? ' even' : '');
    const barWidth = (team.score / MAX) * 100;
    const barClass = team.rank === 1 ? 'gold' : team.rank === 2 ? 'silver' : team.rank === 3 ? 'bronze' : '';
    const rankHtml = isTop3 ? medalSvg(team.rank) : `<span class="rank-num">${team.rank}</span>`;

    row.innerHTML = `
      <div class="rank-col">${rankHtml}</div>
      <div class="team-info">
        <img class="team-logo" src="${logoThumb(team)}" alt="${team.name}" loading="lazy"
             onerror="this.onerror=null;this.src='${espnLogo(team.abbr)}'">
        <div class="team-details">
          <div class="team-name-row">
            <span class="team-name">${team.name}</span>
            <span class="conf-tag ${team.conf.toLowerCase()}">${team.conf}</span>
          </div>
          <div class="bar-container"><div class="bar ${barClass}" data-width="${barWidth}"></div></div>
        </div>
      </div>
      <div class="score-col">${team.score}</div>`;

    row.addEventListener('mouseenter', e => showTooltip(e, team));
    row.addEventListener('mousemove', e => moveTooltip(e));
    row.addEventListener('mouseleave', hideTooltip);
    chart.appendChild(row);

    setTimeout(() => {
      row.classList.add('animate');
      row.style.transition = `opacity 0.35s ease ${i*0.025}s, transform 0.35s ease ${i*0.025}s`;
    }, 50);
    setTimeout(() => { row.querySelector('.bar').style.width = barWidth + '%'; }, 150 + i * 35);
  });
}

const avg = teams.reduce((s,t) => s + t.score, 0) / teams.length;

function showTooltip(e, team) {
  const vsAvg = ((team.score - avg) / avg * 100).toFixed(0);
  const label = vsAvg > 0 ? `+${vsAvg}%` : `${vsAvg}%`;
  const color = vsAvg > 0 ? '#2B6CB0' : '#C53030';
  const pct = Math.round((32 - team.rank + 1) / 32 * 100);
  tooltipEl.innerHTML = `
    <div class="tooltip-team">
      <img src="${logoThumb(team)}" alt="" onerror="this.onerror=null;this.src='${espnLogo(team.abbr)}'">
      ${team.name}
    </div>
    <div class="tooltip-stats">
      <div><div class="tooltip-stat-label">Score</div><div class="tooltip-stat-value">${team.score}</div></div>
      <div><div class="tooltip-stat-label">vs. Average</div><div class="tooltip-stat-value" style="color:${color}">${label}</div></div>
    </div>
    <div class="tooltip-percentile">Rank #${team.rank} of 32 · ${team.conf} · Top ${pct}%</div>`;
  tooltipEl.classList.add('visible');
  moveTooltip(e);
}

function moveTooltip(e) {
  let x = e.clientX + 16, y = e.clientY + 16;
  const r = tooltipEl.getBoundingClientRect();
  if (x + r.width > window.innerWidth - 16) x = e.clientX - r.width - 16;
  if (y + r.height > window.innerHeight - 16) y = e.clientY - r.height - 16;
  tooltipEl.style.left = x + 'px';
  tooltipEl.style.top = y + 'px';
}

function hideTooltip() { tooltipEl.classList.remove('visible'); }

document.querySelectorAll('.controls button').forEach(btn => {
  btn.addEventListener('click', () => {
    document.querySelectorAll('.controls button').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    renderChart(btn.dataset.filter);
  });
});

renderChart('all');
</script>
</body>
</html>
