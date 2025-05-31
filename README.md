### Olá 

###### Sobre o Wellington
Olá! Sou Wellington Antunes, tenho 22 anos e sou estudante de Análise de Dados pela EBAC (Escola Britânica de Artes Criativas e Tecnologia).

Tenho desenvolvido competências técnicas em Excel avançado, Python, Power BI, SQL e outras ferramentas voltadas para análise, modelagem e visualização de dados.

Estou em constante evolução, buscando transformar dados em informações valiosas e apoiar decisões baseadas em evidências.

Gosto de aprender, encarar desafios e contribuir com soluções que realmente fazem a diferença. Se você busca um perfil analítico, curioso e comprometido, estou pronto para agregar à sua equipe ou projeto.


[![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=Wellantunes&show_icons=true&blueberry )](https://github.com/anuraghazra/github-readme-stats)



[![Readme Card](https://github-readme-stats.vercel.app/api/pin/?username=Wellantunes&repo=Projeto_Restaurante&theme=dark)](https://github.com/anuraghazra/github-readme-stats)


[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Wellantunes&layout=compact)](https://github.com/anuraghazra/github-readme-stats)


[<img src='https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white' alt='Linkedin' height='30'>]([https://www.linkedin.com/in/pedrobrocaldi/](https://www.linkedin.com/in/wellington-antuness/))

name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


