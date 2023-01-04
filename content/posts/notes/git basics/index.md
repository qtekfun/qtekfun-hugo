---
title: "Git Basics"
date: 2022-04-19T21:13:25+01:00
draft: false
---
Cada vez que me reconfiguro un ordenador voy añadiendo nuevos alias de git que voy cogiendo con la experiencía como desarrollador. En este artículo documento los básicos que hago cuando me configuro git. 

## ¿Como saber qué alias tengo configurados en git?
Esta es una pregunta que alguna vez me he hecho y hoy he solucionado. Y el comando es:

`git config --get-regexp alias`

Pero realmente, creo que tendria que ser una característica de git, igual que cuando haces un `alias` en unix y te lista los alias del perfil del usuario. Por ello, en el siguiente punto, lo teneis definido.
De esa manera al escribir un `git alias` os listará los alias.

## Mis alias imprescindibles de git

```
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
git config --global core.editor "vim"
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.backup '!f() { git branch $(date "+backup/%Y/%m/%d/%H%M%S") "$@"; }; f'
git config --global alias.alias 'git config --get-regexp alias'
git config --global alias.lg "log --graph --branches=local/ HEAD main --oneline"
git config --global alias.lg1 "log --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white black)%s%C(reset) %C(bold cyan)-- %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date=relative --branches=local/"
git config --global alias.lg2 "log --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white black)%s%C(reset) %C(bold cyan)-- %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date=relative --branches=local/ HEAD main"
git config --global alias.lg3 "log --graph --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white black)%s%C(reset) %C(bold cyan)-- %an%C(reset)%C(bold yellow)%d%C(reset)' --abbrev-commit --date=relative --all'"
```

## Mejor curso gratis para aprender Git en 2022 {#h-mejor-curso-gratis-para-aprender-git-en-2022}

De lo que mejor he visto, esta página gratuita e interactiva será lo mejor que puedes hacer para aprender Git: <a href="https://learngitbranching.js.org/" target="_blank" rel="noreferrer noopener">Learn Git Branching</a>

No obstante, seguiré documentando ...