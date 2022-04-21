---
title: 'Solución al error de VS  “The breakpoint will not currently be hit. No symbols have been loaded for this document.”'
author: afi6cu
date: 2020-11-24T06:50:42+00:00
site-sidebar-layout:
  - default
site-content-layout:
  - default
theme-transparent-header-meta:
  - default
categories:
  - Software

---
Si trabajas o jugueteas con Microsoft Visual Studio 2017 o 2019 (e incluso con alguna versión anterior) y utilizas dll externas que quieres debugar, hay ocasiones que aunque tengas todo bien configurado, no tira. Te suelen salir los breakpoints huecos y te dice: “The breakpoint will not currently be hit. No symbols have been loaded for this document.” (al menos si lo tienes en Inglés).

La **solución** es muy sencilla, recompila todo y actualiza dll, pdb y lib. Que sean todos de la misma compilación y todo listo. VS mete timestamps en los binarios, y si no coinciden, nunca funcionará.

## Otras cosas a mirar

Si sigue sin funcionarte hay varios ajustes que deberías tener hechos:

  * Asegúrate que compilas la dll con el flag debug ( /DEBUG )
  * Intenta cargar los símbolos (pdb) de la dll mediante el botón derecho del ratón en la ventana de módulos. Esta ventana se habilita en Debug > Windows > Modules
  * En la solución del proyecto que usa la DLL (proyecto destino) desmarca «Just My Code» in Tools >Options > Debugging > General > Enable Just My Code (JMC).

Y si aún así te sigue fallando, te dejo por aquí algunos hilos interesantes: <a href="https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md" target="_blank" rel="noreferrer noopener">1</a>, <a href="https://stackoverflow.com/questions/2155930/how-do-i-remedy-the-breakpoint-will-not-currently-be-hit-no-symbols-have-been" target="_blank" rel="noreferrer noopener">2</a>, <a href="https://stackoverflow.com/questions/5309722/a-matching-symbol-file-was-not-found-in-this-folder" target="_blank" rel="noreferrer noopener">3</a>. Quizá ahí, como expanden la info te puedan ayudar.

Happy Debugging!