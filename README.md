# Philly-sports-
<Schedule for the Next Week>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#0a0a0f">
<title>Philly Sports This Week</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0a0a0f;
    --bg2: #111118;
    --bg3: #1a1a24;
    --border: #2a2a3a;
    --text: #e8e8f0;
    --muted: #7a7a9a;
    --accent: #ff4b1f;
    --gold: #f5c518;
    --green: #22c55e;
    --blue: #3b82f6;

    --phillies: #e81828;
    --flyers: #f74902;
    --sixers: #006bb6;
    --eagles: #004c54;
    --union: #071b2c;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Barlow', sans-serif;
    min-height: 100vh;
    padding-bottom: 2rem;
  }

  header {
    background: linear-gradient(135deg, #0a0a0f 0%, #141420 100%);
    border-bottom: 2px solid var(--accent);
    padding: 1.2rem 1rem 1rem;
    position: sticky;
    top: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 0.5rem;
  }

  .header-left h1 {
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 900;
    font-size: 1.6rem;
    letter-spacing: 0.03em;
    text-transform: uppercase;
    line-height: 1;
  }
  .header-left h1 span { color: var(--accent); }
  .header-left .subtitle {
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-top: 0.2rem;
  }

  #refresh-btn {
    background: var(--accent);
    color: white;
    border: none;
    border-radius: 8px;
    padding: 0.6rem 1rem;
    font-family: 'Barlow Condensed', sans-serif;
    font-weight: 700;
    font-size: 0.9rem;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 0.4rem;
    flex-shrink: 0;
  }
  #refresh-btn svg { transition: transform 0.6s; }
  .spinning svg { animation: spin 1s linear infinite; }
  @keyframes spin { to { transform: rotate(360deg); } }

  #status-bar {
    padding: 0.5rem 1rem;
    font-size: 0.72rem;
    color: var(--muted);
    text-align: center;
    letter-spacing: 0.05em;
    min-height: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
  }

  .dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: var(--green);
    animation: pulse 2s ease-in-out infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }

  #content { padding: 0 0.75rem; }

  .team-section {
    margin-bottom: 1.25rem;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid var(--border);
    background: var(--bg2);
  }

  .team-header {
    padding: 0.7rem 1rem;
    display: flex;
    align-items: center;
    gap: 0.6rem;
  }

  .team-logo { width: 32px; height: 32px; object-fit: contain; }
  .team-name { font-family: 'Barlow Condensed', sans-serif; font-weight: 800; font-size: 1.05rem; text-transform: uppercase; }
  .team-league { font-size: 0.65rem; font-weight: 600; color: var(--muted); margin-left: auto; background: rgba(255,255,255,0.08); padding: 0.2rem 0.5rem; border-radius: 4px; }

  .game-card {
    padding: 0.75rem 1rem;
    border-bottom: 1px solid var(--border);
    display: grid;
    grid-template-columns: auto 1fr auto;
    gap: 0.5rem 0.75rem;
    align-items: center;
  }

  .game-date { font-family: 'Barlow Condensed', sans-serif; font-weight: 700; color: var(--muted); font-size: 0.8rem; text-transform: uppercase; }
  .game-date .day { font-size: 1rem; color: var(--text); display: block; }

  .game-matchup { font-family: 'Barlow Condensed', sans-serif; font-weight: 700; font-size: 1rem; }
  .game-meta { font-size: 0.72rem; color: var(--muted); display: flex; gap: 0.5rem; }

  .location-badge { font-size: 0.65rem; font-weight: 700; padding: 0.2rem 0.45rem; border-radius: 4px; text-transform: uppercase; }
  .home { background: rgba(34,197,94,0.15); color: #22c55e; border: 1px solid rgba(34,197,94,0.3); }
  .away { background: rgba(251,146,60,0.15); color: #fb923c; border: 1px solid rgba(251,146,60,0.3); }

  .no-games { padding: 1rem; text-align: center; color: var(--muted); font-style: italic; font-size: 0.8rem; }
  .last-updated { text-align: center; font-size: 0.68rem; color: var(--muted); padding-top: 1rem; }
</style>
</head>
<body>

<header>
  <div class="header-left">
    <h1>Philly <span>Sports</span></h1>
    <div class="subtitle">Live Schedule Tracker</div>
  </div>
  <button id="refresh-btn" onclick="fetchSchedules()">
    <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
      <path d="M21 2v6h-6"/><path d="M3 12a9 9 0 0 1 15-6.7L21 8"/><path d="M3 22v-6h6"/><path d="M21 12a9 9 0 0 1-15 6.7L3 16"/>
    </svg>
    Refresh
  </button>
</header>

<div id="status-bar"><div class="dot"></div> Connecting to ESPN Data...</div>
<div id="content"></div>

<script>
const PHILLY_TEAMS = [
  { name: 'Eagles',  sprt: 'football', slug: 'nfl', id: '21', league: 'NFL', color: '#004C54' },
  { name: 'Sixers',  sprt: 'basketball',slug: 'nba', id: '20', league: 'NBA', color: '#006BB6' },
  { name: 'Phillies', sprt: 'baseball', slug: 'mlb', id: '22', league: 'MLB', color: '#E81828' },
  { name: 'Flyers',  sprt: 'hockey', slug: 'nhl', id: '15', league: 'NHL', color: '#F74902' },
  { name: 'Union',   sprt: 'soccer', slug: 'soccer/usa.1', id: '11091', league: 'MLS', color: '#071B2C' }
];

async function fetchSchedules() {
    const btn = document.getElementById('refresh-btn');
    const statusBar = document.getElementById('status-bar');
    const content = document.getElementById('content');
    
    btn.classList.add('spinning');
    content.innerHTML = '<div class="no-games">Fetching locker room data...</div>';

    try {
        const teamData = {};

        for (const team of PHILLY_TEAMS) {
            try {
                const res = await fetch(`https://site.api.espn.com/apis/site/v2/sports/${team.sprt}/${team.slug}/teams/${team.id}/schedule`);
                const data = await res.json();
                
                // Get games occurring from now until 14 days out
                const now = new Date();
                const twoWeeks = new Date(now.getTime() + (7 * 24 * 60 * 60 * 1000));

                teamData[team.name] = (data.events || [])
                    .filter(e => {
                        const gameDate = new Date(e.date);
                        return gameDate >= now && gameDate <= twoWeeks;
                    })
                    .map(e => {
                        const game = e.competitions[0];
                        const opponent = game.competitors.find(c => c.id !== team.id);
                        const isHome = game.competitors.find(c => c.id === team.id).homeAway === 'home';
                        const dateObj = new Date(e.date);
                        
                        return {
                            day: dateObj.toLocaleDateString('en-US', {weekday: 'short'}),
                            date: dateObj.toLocaleDateString('en-US', {month: 'short', day: 'numeric'}),
                            time: dateObj.toLocaleTimeString([], {hour: '2-digit', minute: '2-digit'}),
                            matchup: isHome ? `vs ${opponent.team.abbreviation}` : `@ ${opponent.team.abbreviation}`,
                            location: isHome ? 'home' : 'away',
                            tv: game.broadcasts?.[0]?.names?.[0] || 'TBD',
                            oppLogo: opponent.team.logo
                        };
                    });
            } catch (err) {
                console.error(`Failed to fetch ${team.name}`, err);
                teamData[team.name] = [];
            }
        }

        renderAll(teamData);
        statusBar.innerHTML = `<div class="dot"></div> Live — ${new Date().toLocaleTimeString([], {hour:'2-digit', minute:'2-digit'})}`;
    } catch (err) {
        statusBar.innerHTML = `⚠️ Connection Error`;
    } finally {
        btn.classList.remove('spinning');
    }
}

function renderAll(teamData) {
    const content = document.getElementById('content');
    content.innerHTML = PHILLY_TEAMS.map(team => {
        const games = teamData[team.name] || [];
        const gamesHtml = games.length ? games.map(g => `
            <div class="game-card">
                <div class="game-date">
                    <span class="day">${g.day}</span>
                    ${g.date}
                </div>
                <div class="game-info">
                    <div class="game-matchup">${g.matchup}</div>
                    <div class="game-meta">
                        <span>🕐 ${g.time}</span>
                        <span>📺 ${g.tv}</span>
                    </div>
                </div>
                <div class="location-badge ${g.location}">${g.location}</div>
            </div>
        `).join('') : '<div class="no-games">No games next 14 days</div>';

        return `
            <div class="team-section">
                <div class="team-header" style="background: linear-gradient(90deg, ${team.color}44 0%, transparent 100%); border-bottom: 1px solid ${team.color}66">
                    <span class="team-name" style="color: ${team.color === '#071B2C' ? '#b49a5e' : team.color}">${team.name}</span>
                    <span class="team-league">${team.league}</span>
                </div>
                <div class="game-list">${gamesHtml}</div>
            </div>
        `;
    }).join('') + `<div class="last-updated">Schedule data provided by ESPN Public API</div>`;
}

// Initial Load
fetchSchedules();
</script>
</body>
</html>
