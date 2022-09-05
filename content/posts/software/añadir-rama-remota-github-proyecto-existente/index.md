---
title: ¿Cómo configurar una rama remota de github en un proyecto local existente?
date: 2022-08-25T05:00:00+02:00
draft: false
---
Si has creado un proyecto en local y lo que quieres es, tras crear un proyecto de Github que este sea tu "remote" te explico los pasos para hacerlo:

* Hacer aunque sea un commit local
      git add .
      git commit -am "init"

* Configurar repo remoto (Se puede usar la dirección ssh):
      git remote add origin https://github.com/[user]/[project_name].git

* Configurar la url remota:
      git config remote.origin.url https://[user]@github.com/[user]/[project_name]

* initial push to github:
      git push -u origin master

set tracking info - master:
      git branch --set-upstream-to origin/master
      tip:
            before do this, the remote repo should at least contain 1 commit,
            you can do this by push once, or create a file remotely (e.g. README.md).

check the project on github, to see is it ok.

fuente [1](https://stackoverflow.com/questions/27645794/how-to-set-a-local-git-project-to-remote)