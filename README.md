# .github/workflows/snake.yml
# Esta Action gera a animação da cobrinha comendo suas contribuições

name: Generate Snake Animation

on:
  schedule:
    - cron: "0 */12 * * *" # Executa a cada 12 horas
  workflow_dispatch:
  push:
    branches:
    - main

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10

    steps:
      - name: Generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

---

# .github/workflows/update-stats.yml
# Esta Action atualiza suas estatísticas automaticamente

name: Update Stats

on:
  schedule:
    - cron: '0 0 * * *' # Executa diariamente à meia-noite
  workflow_dispatch:

jobs:
  update-readme:
    name: Update this repo's README
    runs-on: ubuntu-latest
    steps:
      - uses: athul/waka-readme@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}

---

# .github/workflows/blog-post-workflow.yml
# Esta Action atualiza seus posts recentes automaticamente

name: Latest blog post workflow
on:
  schedule:
    - cron: '0 * * * *' # Executa a cada hora
  workflow_dispatch:

jobs:
  update-readme-with-blog:
    name: Update this repo's README with latest blog posts
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: gautamkrishnar/blog-post-workflow@master
        with:
          feed_list: "https://dev.to/feed/SEU_USERNAME"

---

# .github/workflows/update-activity.yml
# Esta Action mostra suas atividades recentes do GitHub

name: Update README

on:
  schedule:
    - cron: '*/30 * * * *' # Executa a cada 30 minutos
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    name: Update this repo's README with recent activity

    steps:
      - uses: actions/checkout@v2
      - uses: jamesgeorge007/github-activity-readme@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          COMMIT_MSG: 'Updated README with latest activity'
          MAX_LINES: 10