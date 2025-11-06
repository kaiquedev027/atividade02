<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio Dashboard - Seu Nome</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0d1117;
            --bg-secondary: #161b22;
            --bg-tertiary: #1c2128;
            --accent-blue: #58a6ff;
            --accent-purple: #bc8cff;
            --accent-green: #3fb950;
            --accent-yellow: #d29922;
            --text-primary: #c9d1d9;
            --text-secondary: #8b949e;
            --border: #30363d;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Noto Sans', Helvetica, Arial, sans-serif;
            background: linear-gradient(135deg, #0d1117 0%, #161b22 100%);
            color: var(--text-primary);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        /* Header */
        .header {
            text-align: center;
            padding: 40px 20px;
            background: var(--bg-secondary);
            border-radius: 12px;
            margin-bottom: 30px;
            border: 1px solid var(--border);
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple), var(--accent-green));
        }

        .profile-img {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            border: 4px solid var(--accent-blue);
            margin-bottom: 20px;
            background: linear-gradient(135deg, var(--accent-blue), var(--accent-purple));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            margin-left: auto;
            margin-right: auto;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .header p {
            color: var(--text-secondary);
            font-size: 1.1em;
        }

        .typing-text {
            font-family: 'Courier New', monospace;
            color: var(--accent-green);
            margin-top: 10px;
        }

        /* Stats Grid */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: var(--bg-secondary);
            padding: 25px;
            border-radius: 12px;
            border: 1px solid var(--border);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--accent-blue), transparent);
            animation: shimmer 3s infinite;
        }

        @keyframes shimmer {
            0%, 100% { transform: translateX(-100%); }
            50% { transform: translateX(100%); }
        }

        .stat-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-blue);
            box-shadow: 0 10px 30px rgba(88, 166, 255, 0.2);
        }

        .stat-icon {
            font-size: 2em;
            margin-bottom: 15px;
        }

        .stat-value {
            font-size: 2.5em;
            font-weight: bold;
            margin-bottom: 5px;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .stat-label {
            color: var(--text-secondary);
            font-size: 0.9em;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        /* Skills Section */
        .skills-section {
            background: var(--bg-secondary);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid var(--border);
            margin-bottom: 30px;
        }

        .skills-section h2 {
            margin-bottom: 25px;
            font-size: 1.8em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .skill-bars {
            display: grid;
            gap: 20px;
        }

        .skill {
            position: relative;
        }

        .skill-name {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .skill-bar {
            height: 8px;
            background: var(--bg-tertiary);
            border-radius: 10px;
            overflow: hidden;
            position: relative;
        }

        .skill-progress {
            height: 100%;
            border-radius: 10px;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-purple));
            position: relative;
            animation: loadBar 2s ease-out;
        }

        @keyframes loadBar {
            from { width: 0; }
        }

        .skill-progress::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            animation: shimmerSkill 2s infinite;
        }

        @keyframes shimmerSkill {
            0%, 100% { transform: translateX(-100%); }
            50% { transform: translateX(100%); }
        }

        /* Projects Section */
        .projects-section {
            margin-bottom: 30px;
        }

        .projects-section h2 {
            margin-bottom: 25px;
            font-size: 1.8em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 20px;
        }

        .project-card {
            background: var(--bg-secondary);
            padding: 25px;
            border-radius: 12px;
            border: 1px solid var(--border);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .project-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-purple);
            box-shadow: 0 10px 30px rgba(188, 140, 255, 0.2);
        }

        .project-header {
            display: flex;
            justify-content: space-between;
            align-items: start;
            margin-bottom: 15px;
        }

        .project-title {
            font-size: 1.3em;
            font-weight: bold;
            color: var(--accent-blue);
        }

        .project-status {
            font-size: 0.75em;
            padding: 4px 12px;
            border-radius: 12px;
            background: rgba(63, 185, 80, 0.2);
            color: var(--accent-green);
            border: 1px solid var(--accent-green);
        }

        .project-description {
            color: var(--text-secondary);
            margin-bottom: 15px;
            line-height: 1.6;
        }

        .project-tags {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
            margin-bottom: 15px;
        }

        .tag {
            font-size: 0.8em;
            padding: 4px 10px;
            border-radius: 6px;
            background: var(--bg-tertiary);
            color: var(--accent-blue);
            border: 1px solid var(--border);
        }

        .project-links {
            display: flex;
            gap: 10px;
        }

        .project-link {
            padding: 8px 16px;
            border-radius: 6px;
            background: var(--bg-tertiary);
            color: var(--text-primary);
            text-decoration: none;
            font-size: 0.9em;
            border: 1px solid var(--border);
            transition: all 0.3s ease;
        }

        .project-link:hover {
            background: var(--accent-blue);
            border-color: var(--accent-blue);
            color: #fff;
        }

        /* Activity Chart */
        .activity-section {
            background: var(--bg-secondary);
            padding: 30px;
            border-radius: 12px;
            border: 1px solid var(--border);
            margin-bottom: 30px;
        }

        .activity-section h2 {
            margin-bottom: 25px;
            font-size: 1.8em;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .activity-chart {
            display: flex;
            align-items: flex-end;
            justify-content: space-between;
            height: 200px;
            gap: 8px;
        }

        .activity-bar {
            flex: 1;
            background: linear-gradient(to top, var(--accent-blue), var(--accent-purple));
            border-radius: 4px 4px 0 0;
            position: relative;
            transition: all 0.3s ease;
            animation: growBar 1s ease-out;
        }

        @keyframes growBar {
            from { height: 0 !important; }
        }

        .activity-bar:hover {
            opacity: 0.7;
        }

        .activity-label {
            display: flex;
            justify-content: space-between;
            margin-top: 10px;
            color: var(--text-secondary);
            font-size: 0.85em;
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 30px;
            background: var(--bg-secondary);
            border-radius: 12px;
            border: 1px solid var(--border);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }

        .social-link {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--bg-tertiary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-primary);
            text-decoration: none;
            font-size: 1.5em;
            border: 1px solid var(--border);
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: var(--accent-blue);
            border-color: var(--accent-blue);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(88, 166, 255, 0.4);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 1.8em;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
            }
        }

        /* Pulse Animation */
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.5; }
        }

        .pulse {
            animation: pulse 2s infinite;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="profile-img">👨‍💻</div>
            <h1>Seu Nome</h1>
            <p>Desenvolvedor Full Stack | HTML • CSS • JavaScript • Node.js • Python</p>
            <p class="typing-text">console.log("Buscando minha primeira oportunidade 🚀");</p>
        </div>

        <!-- Stats Grid -->
        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">📁</div>
                <div class="stat-value">15+</div>
                <div class="stat-label">Projetos</div>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">💻</div>
                <div class="stat-value">500+</div>
                <div class="stat-label">Commits</div>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">⭐</div>
                <div class="stat-value">50+</div>
                <div class="stat-label">Stars</div>
            </div>
            
            <div class="stat-card">
                <div class="stat-icon">🔥</div>
                <div class="stat-value">30</div>
                <div class="stat-label">Dia Streak</div>
            </div>
        </div>

        <!-- Skills Section -->
        <div class="skills-section">
            <h2>💡 Habilidades Técnicas</h2>
            <div class="skill-bars">
                <div class="skill">
                    <div class="skill-name">
                        <span>HTML5 & CSS3</span>
                        <span>90%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 90%"></div>
                    </div>
                </div>
                
                <div class="skill">
                    <div class="skill-name">
                        <span>JavaScript</span>
                        <span>85%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 85%"></div>
                    </div>
                </div>
                
                <div class="skill">
                    <div class="skill-name">
                        <span>TailwindCSS</span>
                        <span>80%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 80%"></div>
                    </div>
                </div>
                
                <div class="skill">
                    <div class="skill-name">
                        <span>Node.js</span>
                        <span>75%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 75%"></div>
                    </div>
                </div>
                
                <div class="skill">
                    <div class="skill-name">
                        <span>Python</span>
                        <span>70%</span>
                    </div>
                    <div class="skill-bar">
                        <div class="skill-progress" style="width: 70%"></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Activity Chart -->
        <div class="activity-section">
            <h2>📊 Atividade Semanal</h2>
            <div class="activity-chart">
                <div class="activity-bar" style="height: 80%"></div>
                <div class="activity-bar" style="height: 60%"></div>
                <div class="activity-bar" style="height: 90%"></div>
                <div class="activity-bar" style="height: 75%"></div>
                <div class="activity-bar" style="height: 95%"></div>
                <div class="activity-bar" style="height: 70%"></div>
                <div class="activity-bar" style="height: 85%"></div>
            </div>
            <div class="activity-label">
                <span>Dom</span>
                <span>Seg</span>
                <span>Ter</span>
                <span>Qua</span>
                <span>Qui</span>
                <span>Sex</span>
                <span>Sáb</span>
            </div>
        </div>

        <!-- Projects Section -->
        <div class="projects-section">
            <h2>🚀 Projetos em Destaque</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Landing Page Responsiva</div>
                        <div class="project-status">✓ Completo</div>
                    </div>
                    <p class="project-description">
                        Landing page moderna e totalmente responsiva com animações suaves e design profissional.
                    </p>
                    <div class="project-tags">
                        <span class="tag">HTML5</span>
                        <span class="tag">CSS3</span>
                        <span class="tag">JavaScript</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">👁️ Demo</a>
                        <a href="#" class="project-link">📂 Código</a>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">To-Do App Interativo</div>
                        <div class="project-status">✓ Completo</div>
                    </div>
                    <p class="project-description">
                        Aplicação de tarefas com CRUD completo, localStorage e interface intuitiva.
                    </p>
                    <div class="project-tags">
                        <span class="tag">JavaScript</span>
                        <span class="tag">LocalStorage</span>
                        <span class="tag">CSS3</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">👁️ Demo</a>
                        <a href="#" class="project-link">📂 Código</a>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">API RESTful</div>
                        <div class="project-status">✓ Completo</div>
                    </div>
                    <p class="project-description">
                        API completa com autenticação, validação e documentação para gerenciamento de usuários.
                    </p>
                    <div class="project-tags">
                        <span class="tag">Node.js</span>
                        <span class="tag">Express</span>
                        <span class="tag">JWT</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">📚 Docs</a>
                        <a href="#" class="project-link">📂 Código</a>
                    </div>
                </div>

                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Web Scraper</div>
                        <div class="project-status pulse">🚧 Em Desenvolvimento</div>
                    </div>
                    <p class="project-description">
                        Ferramenta de automação para extrair dados da web com Python e Beautiful Soup.
                    </p>
                    <div class="project-tags">
                        <span class="tag">Python</span>
                        <span class="tag">BeautifulSoup</span>
                        <span class="tag">Pandas</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">📂 Código</a>
                    </