<!--
  Dashboard tecnológico para perfil GitHub
  Arquivo: github-dashboard.html
  Instruções de uso:
  - Abra este arquivo no navegador para ver o preview.
  - Substitua os dados de exemplo pelos seus (nome, bio, avatar, repos, estatísticas).
  - Se quiser automatizar com a API do GitHub, faça fetch para https://api.github.com/users/{username}/repos e https://api.github.com/users/{username} e injete os dados no DOM.
  - Este arquivo é responsivo e sem frameworks; estilos feitos em CSS puro.
--><!doctype html>

<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Dashboard GitHub — Perfil Tecnológico</title>
  <style>
    :root{
      --bg:#0f1724; /* dark */
      --card:#0b1220;
      --muted:#9aa8bd;
      --accent:#7c3aed; /* purple */
      --glass: rgba(255,255,255,0.04);
      --glass-2: rgba(255,255,255,0.02);
      --success: #16a34a;
      --danger:#ef4444;
      --radius:14px;
      --ff: Inter, ui-sans-serif, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;
    }
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:var(--ff);background:linear-gradient(180deg,var(--bg) 0%, #071021 100%);color:#e6eef6}
    a{color:inherit;text-decoration:none}.container{max-width:1100px;margin:36px auto;padding:28px}
.grid{display:grid;gap:20px}

/* Header */
header{display:flex;gap:20px;align-items:center}
.avatar{width:96px;height:96px;border-radius:18px;overflow:hidden;flex:0 0 96px;border:2px solid rgba(255,255,255,0.06)}
.avatar img{width:100%;height:100%;object-fit:cover;display:block}
.user{display:flex;flex-direction:column;gap:6px}
.user h1{margin:0;font-size:20px}
.user p{margin:0;color:var(--muted);font-size:13px}
.tags{display:flex;gap:8px;margin-top:8px}
.tag{background:var(--glass);padding:6px 10px;border-radius:999px;font-size:12px;color:var(--muted)}

/* Layout columns */
.main-grid{grid-template-columns: 1fr 340px}

/* Cards */
.card{background:linear-gradient(180deg,var(--card), rgba(12,18,28,0.7));padding:16px;border-radius:var(--radius);box-shadow:0 6px 18px rgba(2,6,23,0.6)}
.card h2{margin:0 0 12px 0;font-size:15px}
.stats{display:flex;gap:12px}
.stat{flex:1;padding:12px;background:var(--glass-2);border-radius:12px;text-align:center}
.stat strong{display:block;font-size:18px}
.stat span{display:block;color:var(--muted);font-size:12px}

/* Languages bar */
.lang-list{display:flex;flex-direction:column;gap:8px}
.lang{display:flex;align-items:center;gap:10px}
.lang .bar{height:10px;background:rgba(255,255,255,0.06);border-radius:999px;flex:1;overflow:hidden}
.lang .bar > i{display:block;height:100%;border-radius:999px}
.lang small{color:var(--muted);min-width:76px;text-align:right;font-size:12px}

/* Repos list */
.repo{display:flex;flex-direction:column;gap:6px;padding:12px;background:linear-gradient(90deg, rgba(255,255,255,0.01), rgba(255,255,255,0.02));border-radius:12px}
.repo .meta{display:flex;gap:10px;align-items:center;font-size:13px}
.repo .meta small{color:var(--muted)}
.repo .desc{color:var(--muted);font-size:13px}
.repo-list{display:grid;gap:10px}

/* Contributions heatmap (placeholder) */
.heat{display:flex;gap:6px;align-items:flex-end;height:110px}
.heat .col{display:flex;flex-direction:column;gap:6px}
.heat .cell{width:12px;height:12px;border-radius:3px;background:rgba(255,255,255,0.03)}

/* Footer */
footer{margin-top:18px;color:var(--muted);font-size:13px;text-align:center}

/* Responsiveness */
@media (max-width:980px){
  .main-grid{grid-template-columns:1fr}
  .avatar{width:76px;height:76px;flex:0 0 76px}
  .container{padding:18px}
}

/* small helpers */
.pill{display:inline-block;padding:6px 10px;border-radius:999px;background:rgba(255,255,255,0.03);font-size:12px}
.row{display:flex;gap:12px;align-items:center}
.muted{color:var(--muted)}

/* colored bars for languages (example palettes) */
.lang-js{background:linear-gradient(90deg,#f7df1e,#ffd54a)}
.lang-py{background:linear-gradient(90deg,#3572A5,#79b4e0)}
.lang-html{background:linear-gradient(90deg,#e34f26,#ff8a5a)}
.lang-css{background:linear-gradient(90deg,#264de4,#6a8eff)}
.lang-go{background:linear-gradient(90deg,#00ADD8,#5fd3ef)}

  </style>
</head>
<body>
  <div class="container">
    <header class="card row">
      <div class="avatar"><img src="https://avatars.githubusercontent.com/u/9919?s=200&v=4" alt="Avatar"></div>
      <div class="user">
        <h1 id="name">Seu Nome / @seu-usuario</h1>
        <p id="bio">Bio curta do GitHub — desenvolvedor(a) full-stack, entusiasta de automatização e infra.</p>
        <div class="tags" id="skills">
          <span class="tag">JavaScript</span>
          <span class="tag">React</span>
          <span class="tag">Docker</span>
        </div>
      </div>
      <div style="margin-left:auto;text-align:right">
        <div class="pill">Followers: <strong id="followers">128</strong></div>
        <div style="height:8px"></div>
        <a href="#repos" class="pill">Ver repositórios</a>
      </div>
    </header><div class="grid main-grid" style="margin-top:20px">
  <!-- Left column -->
  <div class="grid">
    <div class="card">
      <h2>Resumo</h2>
      <div class="stats">
        <div class="stat">
          <strong id="public-repos">24</strong>
          <span>Repositórios públicos</span>
        </div>
        <div class="stat">
          <strong id="stars">412</strong>
          <span>Stars</span>
        </div>
        <div class="stat">
          <strong id="prs">87</strong>
          <span>Contribuições (mês)</span>
        </div>
      </div>

      <div style="height:14px"></div>
      <h2>Tecnologias mais usadas</h2>
      <div class="lang-list" id="languages">
        <!-- Exemplo: ajustar width via style="--w:70%" e classe para cor -->
        <div class="lang"><small>JavaScript</small><div class="bar"><i class="lang-js" style="width:68%"></i></div><small>68%</small></div>
        <div class="lang"><small>Python</small><div class="bar"><i class="lang-py" style="width:22%"></i></div><small>22%</small></div>
        <div class="lang"><small>HTML</small><div class="bar"><i class="lang-html" style="width:10%"></i></div><small>10%</small></div>
      </div>
    </div>

    <div class="card" id="repos">
      <h2>Principais repositórios</h2>
      <div class="repo-list">
        <div class="repo">
          <div class="row" style="justify-content:space-between">
            <div>
              <a href="#" style="font-weight:600">nome-do-repo-1</a>
              <div class="meta"><small class="muted">react • 1.2k stars</small></div>
            </div>
            <div class="muted">Updated: 2025-10-14</div>
          </div>
          <div class="desc">Breve descrição do repositório — o que faz e tecnologias.</div>
        </div>

        <div class="repo">
          <div class="row" style="justify-content:space-between">
            <div>
              <a href="#" style="font-weight:600">infra-automation</a>
              <div class="meta"><small class="muted">ansible • 320 stars</small></div>
            </div>
            <div class="muted">Updated: 2025-09-06</div>
          </div>
          <div class="desc">Playbooks e scripts para provisionamento automático de servidores.</div>
        </div>

        <!-- Mais itens... -->
      </div>
    </div>

    <div class="card">
      <h2>Contribuições (Heatmap)</h2>
      <p class="muted" style="margin:6px 0 12px 0">Visual simplificado das contribuições — substitua por dados reais via API.</p>
      <div class="heat" id="heatmap">
        <!-- Gera colunas com células em JS (exemplo de 20 colunas) -->
        <!-- Cada coluna contém 7 células; cores mais escuras = mais contribuições -->
      </div>
    </div>

  </div>

  <!-- Right column -->
  <aside>
    <div class="card" style="margin-bottom:16px">
      <h2>Stack & foco</h2>
      <div style="display:flex;flex-direction:column;gap:8px">
        <div class="row"><strong>Backend</strong><div style="margin-left:auto" class="muted">Node.js • Python</div></div>
        <div class="row"><strong>Infra</strong><div style="margin-left:auto" class="muted">Docker • Kubernetes</div></div>
        <div class="row"><strong>Frontend</strong><div style="margin-left:auto" class="muted">React • SASS</div></div>
        <div class="row"><strong>Cloud</strong><div style="margin-left:auto" class="muted">AWS • GCP</div></div>
      </div>
    </div>

    <div class="card">
      <h2>Contatos</h2>
      <div class="muted" style="font-size:13px">Coloque aqui seus canais públicos</div>
      <div style="height:12px"></div>
      <div class="row"><span class="muted">Email</span><div style="margin-left:auto">seu@email.com</div></div>
      <div class="row"><span class="muted">Site</span><div style="margin-left:auto">seusite.com</div></div>
      <div class="row"><span class="muted">LinkedIn</span><div style="margin-left:auto">linkedin.com/in/seu</div></div>
    </div>

  </aside>
</div>

<footer>
  <div class="muted">Dashboard gerado — personalize com a API do GitHub para atualizar automaticamente. Template por ChatGPT.</div>
</footer>

  </div>  <script>
    // Script opcional para popular heatmap com valores aleatórios (substitua por dados reais)
    (function(){
      const heat = document.getElementById('heatmap');
      const cols = 20; // semanas
      for(let c=0;c<cols;c++){
        const col = document.createElement('div');col.className='col';
        for(let r=0;r<7;r++){
          const cell = document.createElement('div');cell.className='cell';
          // aleatório para demo
          const v = Math.floor(Math.random()*5);
          if(v>=4) cell.style.backgroundColor='rgba(124,58,237,0.95)';
          else if(v>=3) cell.style.backgroundColor='rgba(124,58,237,0.7)';
          else if(v>=2) cell.style.backgroundColor='rgba(124,58,237,0.45)';
          else if(v>=1) cell.style.backgroundColor='rgba(124,58,237,0.22)';
          else cell.style.backgroundColor='rgba(255,255,255,0.03)';
          col.appendChild(cell);
        }
        heat.appendChild(col);
      }
    })();

    // Exemplos de como popular dinamicamente (descomente e ajuste seu username)
    /*
    async function fetchGitHub(username){
      const userR = await fetch(`https://api.github.com/users/${username}`);
      const user = await userR.json();
      document.getElementById('name').textContent = user.name || user.login;
      document.getElementById('bio').textContent = user.bio || '';
      document.querySelector('.avatar img').src = user.avatar_url;
      document.getElementById('followers').textContent = user.followers;
      document.getElementById('public-repos').textContent = user.public_repos;

      const reposR = await fetch(`https://api.github.com/users/${username}/repos?per_page=6&sort=pushed`);
      const repos = await reposR.json();
      const list = document.querySelector('.repo-list');
      list.innerHTML='';
      repos.forEach(r=>{
        const el = document.createElement('div');el.className='repo';
        el.innerHTML = `
          <div class="row" style="justify-content:space-between">
            <div>
              <a href="${r.html_url}" target="_blank" style="font-weight:600">${r.name}</a>
              <div class="meta"><small class="muted">${r.language || ''} • ${r.stargazers_count} stars</small></div>
            </div>
            <div class="muted">Updated: ${new Date(r.pushed_at).toISOString().slice(0,10)}</div>
          </div>
          <div class="desc">${r.description || ''}</div>
        `;
        list.appendChild(el);
      })
    }
    // fetchGitHub('seu-usuario-aqui');
    */
  </script></body>
</html>