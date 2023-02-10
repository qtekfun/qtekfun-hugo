---
title: "Configurar Prompt Powershell"
date: 2023-02-10T10:30:47+01:00
draft: false
---
Hace poco que me he reencontrado con Windows y que ando trabajando con Powershell. Echaba de menos los prompts que tenía en mi antiguo entorno de Ubuntu así que me puse a ver cómo funcionaba esto y completé el proceso por este articulo.

## Custom prompt en Powershell para Desarrolladores

Una de las cosas más importantes, al menos para mi, es el hecho de poder saber en qué rama de que repo estoy. Y para solucionar eso acabe investigando hasta dar con este prompt.

### Crear tu Powershell Profile

#### Comprobar si tenemos un Perfil creado

Para esto hay una manera muy sencilla y es lanzando el Powershell el comando `Test-Path $profile`. Si nos devuelve falso, tendremos que crear uno nuevo con el comando `New-Item -Path $profile -Type File -Force`.

#### Instalar git

En esto no voy a entrar, pero instalar git es obligado si no los siguientes pasos no funcionarán muy bien.

#### Instalar Posh-git

Es un pequeño módulo que nos servirá para obtener info en el prompt del repo de git en el que estemos. Para instalarlo el comando genérico es: `New-Item -Path $profile -Type File -Force` Pero si tenéis dudas os dejo el [repo de git de Posh-git](https://github.com/dahlbyk/posh-git) con toda la info de cómo instalarlo.

#### Personalizar el prompt

Para esto, lo mejor es ejecutar en Powershell `notepad $profile` y nos abrirá el fichero en Notepad. Ahora el que yo tengo configurado es

```Powershell
Import-Module posh-git
$GitPromptSettings.DefaultPromptPrefix.Text = '$(Get-Date -f "MM-dd HH:mm:ss") '
$GitPromptSettings.DefaultPromptPrefix.ForegroundColor = [ConsoleColor]::Magenta
$GitPromptSettings.DefaultPromptAbbreviateHomeDirectory = $false
$GitPromptSettings.DefaultPromptWriteStatusFirst = $true
$GitPromptSettings.DefaultPromptBeforeSuffix.Text = '`n$([DateTime]::now.ToString("MM-dd HH:mm:ss"))'
$GitPromptSettings.DefaultPromptBeforeSuffix.ForegroundColor = 0x808080
$GitPromptSettings.DefaultPromptSuffix = ' $((Get-History -Count 1).id + 1)$(">" * ($nestedPromptLevel + 1)) '
$GitPromptSettings.BeforePath = '{'
$GitPromptSettings.AfterPath = '}'
$GitPromptSettings.BeforePath.ForegroundColor = 'Red'
$GitPromptSettings.AfterPath.ForegroundColor = 'Red'
function global:PromptWriteErrorInfo() {
     if ($global:GitPromptValues.DollarQuestion) { return }

         if ($global:GitPromptValues.LastExitCode) {
           "`e[31m(" + $global:GitPromptValues.LastExitCode + ") `e[0m"
        }
            else {
              "`e[31m! `e[0m"
           }
}
$global:GitPromptSettings.DefaultPromptBeforeSuffix.Text = '`n$(PromptWriteErrorInfo)$([DateTime]::now.ToString("MM-dd HH:mm:ss"))'
```

y con esto tendremos un prompt supervitaminado que nos dará info del repo de git y además nos dará info del código de error del último comando lanzado.

Espero que lo disfrutéis. En [mi repo de GitHub](https://github.com/qtekfun/NewInstallationTools) tenéis más cositas chulas para Windows
