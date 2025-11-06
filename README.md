# 🎨 Guia Completo: Dashboards Animados no GitHub

## 📋 Índice
1. [Configuração Básica](#configuracao-basica)
2. [Dashboards Automáticos](#dashboards-automaticos)
3. [Animações Avançadas](#animacoes-avancadas)
4. [Personalização de Temas](#personalizacao-temas)
5. [Troubleshooting](#troubleshooting)

---

## 🚀 Configuração Básica

### Passo 1: Criar Repositório Especial

1. Crie um repositório com **EXATAMENTE** o mesmo nome do seu usuário
   - Ex: Se seu username é `joaosilva`, crie o repo `joaosilva`
2. Marque como **Público**
3. Adicione um `README.md`
4. Cole o conteúdo do artifact "Profile README"

### Passo 2: Substituir Informações

Substitua todos os campos:
- `SEU_USERNAME` → Seu usuário GitHub
- `[SEU NOME]` → Seu nome completo
- `seu-linkedin` → URL do seu LinkedIn
- `seu-email` → Seu email
- `projeto1`, `projeto2`, etc → Nomes reais dos seus repositórios

---

## ⚡ Dashboards Automáticos

### 1️⃣ GitHub Stats (Estatísticas)

**Funciona automaticamente!** Apenas substitua `SEU_USERNAME`:

```markdown
![GitHub Stats](https://github-readme-stats.vercel.app/api?username=SEU_USERNAME&show_icons=true&theme=tokyonight)
```

**Personalização de Temas:**
- `tokyonight` (tema padrão - escuro com azul/roxo)
- `radical` (rosa/roxo vibrante)
- `dark` (escuro simples)
- `dracula` (roxo estilo Dracula)
- `monokai` (verde/amarelo)
- `gruvbox` (marrom/laranja)
- `onedark` (escuro One Dark)
- `cobalt` (azul escuro)
- `synthwave` (synthwave 80s)
- `highcontrast` (alto contraste)
- `algolia` (azul Algolia)

**Opções adicionais:**
```markdown
?username=SEU_USERNAME
&show_icons=true          # Mostra ícones
&theme=tokyonight         # Tema
&include_all_commits=true # Conta todos os commits
&count_private=true       # Conta repos privados
&hide_border=true         # Remove borda
&border_radius=10         # Bordas arredondadas
&hide=issues,contribs     # Esconde itens específicos
&show=reviews,prs_merged  # Mostra itens específicos
```

### 2️⃣ GitHub Streak (Sequência)

```markdown
![GitHub Streak](https://streak-stats.demolab.com?user=SEU_USERNAME&theme=tokyonight&hide_border=true)
```

**Temas disponíveis:** (mesmos do GitHub Stats)

### 3️⃣ Top Languages (Linguagens Mais Usadas)

```markdown
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=SEU_USERNAME&layout=compact&theme=tokyonight)
```

**Layouts:**
- `compact` (compacto, horizontal)
- `normal` (vertical com barras)
- `donut` (gráfico de rosquinha)
- `donut-vertical` (rosquinha vertical)
- `pie` (gráfico de pizza)

### 4️⃣ GitHub Trophies (Troféus)

```markdown
![Trophy](https://github-profile-trophy.vercel.app/?username=SEU_USERNAME&theme=tokyonight&no-frame=true&row=2&column=3)
```

**Opções:**
- `row=2` - Número de linhas
- `column=3` - Número de colunas
- `no-frame=true` - Remove moldura
- `no-bg=true` - Remove fundo
- `margin-w=15` - Margem horizontal
- `margin-h=15` - Margem vertical

### 5️⃣ Contribution Graph (Gráfico de Contribuições)

```markdown
![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=SEU_USERNAME&theme=tokyo-night)
```

**Temas:**
- `tokyo-night` (escuro azul/roxo)
- `dracula` (roxo Dracula)
- `github-compact` (GitHub padrão)
- `react-dark` (React escuro)
- `xcode` (Xcode light)
- `rogue` (escuro verde)

---

## 🐍 Animação da Cobrinha (Snake)

### Passo a Passo Completo:

#### 1. Criar estrutura de pastas

No seu repositório de perfil, crie:
```
seu-username/
├── .github/
│   └── workflows/
│       └── snake.yml
└── README.md
```

#### 2. Adicionar arquivo snake.yml

Copie o conteúdo do artifact "GitHub Actions - Animações Automáticas" para `.github/workflows/snake.yml`

#### 3. Ativar GitHub Actions

1. Vá em **Settings** do repositório
2. Clique em **Actions** → **General**
3. Em **Workflow permissions**, selecione:
   - ✅ Read and write permissions
4. Salve

#### 4. Executar manualmente (primeira vez)

1. Vá em **Actions** no topo do repositório
2. Clique em **Generate Snake Animation**
3. Clique em **Run workflow** → **Run workflow**
4. Aguarde ~1 minuto

#### 5. Verificar funcionamento

Após executar, uma branch `output` será criada com o arquivo SVG da cobrinha.

#### 6. Adicionar no README

Já está no README que forneci:
```markdown
![Snake animation](https://raw.githubusercontent.com/SEU_USERNAME/SEU_USERNAME/output/github-contribution-grid-snake-dark.svg)
```

---

## 🎯 Atividades Recentes Automáticas

### 1. Instalar GitHub Activity

Crie: `.github/workflows/update-activity.yml` com o conteúdo do artifact.

### 2. Adicionar no README

Entre estas tags no seu README:
```markdown
<!--START_SECTION:activity-->
<!--END_SECTION:activity-->
```

As atividades aparecerão automaticamente aqui!

---

## ⏱️ WakaTime Stats (Tempo de Código)

### Setup Completo:

#### 1. Criar conta no WakaTime

1. Acesse: https://wakatime.com/
2. Crie uma conta gratuita
3. Baixe a extensão para VS Code

#### 2. Instalar extensão VS Code

1. Abra VS Code
2. Procure por "WakaTime"
3. Instale e configure com sua API key

#### 3. Pegar API Key

1. Vá em: https://wakatime.com/settings/api-key
2. Copie sua API key

#### 4. Adicionar Secret no GitHub

1. Vá em **Settings** → **Secrets and variables** → **Actions**
2. Clique em **New repository secret**
3. Nome: `WAKATIME_API_KEY`
4. Value: Cole sua API key
5. Salve

#### 5. Adicionar workflow

Crie `.github/workflows/update-stats.yml` com conteúdo do artifact.

#### 6. Adicionar no README

```markdown
<!--START_SECTION:waka-->
<!--END_SECTION:waka-->
```

Após 1 dia de uso, suas estatísticas aparecerão!

---

## 🎨 Cards Personalizados dos Projetos

Para mostrar cards animados dos seus projetos:

```markdown
[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=SEU_USERNAME&repo=NOME_DO_REPO&theme=tokyonight)](https://github.com/SEU_USERNAME/NOME_DO_REPO)
```

**Exemplo prático:**
```markdown
[![Project 1](https://github-readme-stats.vercel.app/api/pin/?username=joaosilva&repo=landing-page&theme=tokyonight)](https://github.com/joaosilva/landing-page)
```

---

## 🎭 Typing SVG (Texto Animado)

Personalize seu texto animado:

```markdown
![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=2E9EF7&center=true&vCenter=true&width=435&lines=Primeira+Linha;Segunda+Linha;Terceira+Linha)
```

**Opções:**
- `font=Fira+Code` - Fonte (use + para espaços)
- `size=32` - Tamanho da fonte
- `duration=2800` - Velocidade de digitação
- `pause=2000` - Pausa entre linhas
- `color=2E9EF7` - Cor do texto (hex sem #)
- `center=true` - Centralizar
- `width=435` - Largura
- `lines=Linha1;Linha2` - Suas linhas (use ; para separar)

**Gerador visual:** https://readme-typing-svg.herokuapp.com/demo/

---

## 🌈 Badges Personalizados

### Shields.io Badges

```markdown
![Badge](https://img.shields.io/badge/TEXTO-VALOR-COR?style=ESTILO&logo=LOGO)
```

**Exemplos:**
```markdown
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
```

**Estilos disponíveis:**
- `flat` - Simples e plano
- `flat-square` - Quadrado
- `for-the-badge` - Grande e destacado (recomendado)
- `plastic` - Com brilho
- `social` - Estilo redes sociais

**Gerador:** https://shields.io/

### Skill Icons (Ícones Animados)

```markdown
![My Skills](https://skillicons.dev/icons?i=html,css,js,nodejs,python,git)
```

**Opções:**
- `i=html,css,js` - Lista de tecnologias
- `theme=dark` - Tema escuro
- `theme=light` - Tema claro
- `perline=6` - Ícones por linha

**Tecnologias disponíveis:** html, css, js, ts, react, vue, angular, nodejs, python, java, php, ruby, go, rust, docker, git, github, vscode, figma, e muito mais!

---

## 🎪 Outros Elementos Animados

### 1. Profile Views Counter

```markdown
![](https://komarev.com/ghpvc/?username=SEU_USERNAME&color=blueviolet&style=for-the-badge)
```

**Cores:** blue, green, red, orange, blueviolet, brightgreen

### 2. GitHub Readme Quotes

```markdown
![Quote](https://github-readme-quotes.herokuapp.com/quote?theme=tokyonight)
```

### 3. Random Dev Meme

```markdown
![Meme](https://random-memer.herokuapp.com/)
```

### 4. Spotify Playing

```markdown
![Spotify](https://spotify-github-profile.vercel.app/api/view?uid=SEU_SPOTIFY_ID&cover_image=true&theme=default)
```

---

## 🔧 Personalização de Cores

### Encontrar código Hex de cores:

1. Acesse: https://htmlcolorcodes.com/
2. Escolha sua cor
3. Copie o código (ex: `2E9EF7`)
4. Use sem o `#` nas URLs

### Paletas prontas:

**Tokyo Night (Azul/Roxo):**
- `#1a1b26` - Fundo
- `#7aa2f7` - Azul principal
- `#bb9af7` - Roxo
- `#9ece6a` - Verde

**Dracula (Roxo/Rosa):**
- `#282a36` - Fundo
- `#bd93f9` - Roxo
- `#ff79c6` - Rosa
- `#50fa7b` - Verde

**Nord (Azul Frio):**
- `#2e3440` - Fundo
- `#88c0d0` - Azul claro
- `#81a1c1` - Azul médio
- `#5e81ac` - Azul escuro

---

## 🐛 Troubleshooting

### ❌ Snake não aparece

**Soluções:**
1. Verifique se as permissões do Actions estão corretas
2. Execute o workflow manualmente
3. Aguarde 5-10 minutos após primeira execução
4. Verifique se a branch `output` foi criada
5. Use a URL correta: `https://raw.githubusercontent.com/SEU_USERNAME/SEU_USERNAME/output/github-contribution-grid-snake-dark.svg`

### ❌ Stats não carregam

**Soluções:**
1. Verifique se o repositório é público
2. Confirme que o username está correto
3. Tente diferentes temas
4. Limpe o cache: adicione `&cache_seconds=1800` na URL
5. Use uma instância alternativa: `https://github-readme-stats-sigma-five.vercel.app/api/...`

### ❌ WakaTime não atualiza

**Soluções:**
1. Verifique se a extensão está instalada no VS Code
2. Confirme que está logado no WakaTime
3. Certifique-se que o secret `WAKATIME_API_KEY` está correto
4. Aguarde 24h após começar a usar
5. Verifique se o workflow está rodando em Actions

### ❌ Badges não aparecem

**Soluções:**
1. Verifique a sintaxe do markdown
2. Confirme que os logos existem (veja lista em shields.io)
3. Certifique-se que as cores estão em hex sem `#`
4. Teste a URL do badge diretamente no navegador

---

## 📚 Recursos Úteis

### Geradores Visuais:
- **Typing SVG:** https://readme-typing-svg.herokuapp.com/demo/
- **Shields.io:** https://shields.io/
- **GitHub Stats:** https://github.com/anuraghazra/github-readme-stats
- **Skill Icons:** https://skillicons.dev/

### Inspiração:
- **Awesome GitHub Profile README:** https://github.com/abhisheknaiidu/awesome-github-profile-readme
- **Profile Readme Generator:** https://rahuldkjain.github.io/gh-profile-readme-generator/

### Documentação:
- **GitHub Actions:** https://docs.github.com/pt/actions
- **Markdown Guide:** https://www.markdownguide.org/

---

## ✅ Checklist Final

- [ ] Repositório de perfil criado (mesmo nome do username)
- [ ] README.md adicionado e personalizado
- [ ] Todos os `SEU_USERNAME` substituídos
- [ ] Links de email, LinkedIn e portfolio adicionados
- [ ] GitHub Actions configurado (se usar Snake)
- [ ] Permissões de Actions ativadas
- [ ] Snake executado pelo menos uma vez
- [ ] Cards dos projetos atualizados com repos reais
- [ ] Temas personalizados escolhidos
- [ ] Profile views counter funcionando
- [ ] Badges de tecnologias corretos
- [ ] WakaTime configurado (opcional)
- [ ] Testado em modo escuro E claro do GitHub

---

## 🎉 Pronto!

Seu perfil GitHub agora está **PROFISSIONAL** e vai impressionar qualquer recrutador!

**Dicas finais:**
- Commit regularmente para manter o gráfico verde
- Documente bem seus projetos
- Mantenha o README atualizado
- Mostre projetos completos e funcionais
- Responda issues e PRs rapidamente

**Boa sorte na busca pelo seu primeiro emprego! 🚀**