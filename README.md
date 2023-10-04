# Hello World....

**Prazer me chamo Natan Lima!**<img align="right" alt="programer" height="180em" style="border-radius:50px;" src="https://veja.abril.com.br/wp-content/uploads/2016/05/giphy-3-original.gif">

- **Eterno aprendiz**
- **Desenvolvedor BackEnd**
- **Sempre aprendendo 1% mais todos os dias**

🎓 I study Software Development with a Focus on Back-End | @ Cubos Academy.




##
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white)


<div>
<a href="https://github.com/natanlimadev">
<img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=natanlimadev&layout=compact&langs_count=7&theme=dracula"/>
<img height="180em" src="https://github-readme-stats.vercel.app/api?username=natanlimadev&show_icons=true&theme=dracula&include_all_commits=true&count_private=true"/>
</div>


 ### Entre em contato comigo! 📭
<div>
<a href="https://www.linkedin.com/in/natanlimadesenvolvedor" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
<a href="https://api.WhatsApp.com/send?phone=5521993029125" target="_blank"><img src=https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white target="_blank"/>
<a href="mailto:natanlimadevrj@gmail.com" target="_blank"><img src=https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white>
</div>
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
    runs-on: ubuntu-latest
    timeout-minutes: 10
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
