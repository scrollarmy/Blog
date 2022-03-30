---
layout: post
title: Transformar vscode en el cliente git para linux que no existe
subtitle: Extensiones para transformar el editor de codigo en cliente GIT
comments: false
readtime: true
---

# Transformar vscode en el cliente git para linux que no existe

Vamos a ver un conjunto de extensiones para poder trabajar en el dia a dia mas facilmente

Hace un tiempo que no hay un cliente git que domine el mercado en linux y sea open source, hoy en dia una alternativa solida es SmartGit pero si no te cierra o preferis integrar todo en VsCode te compartimos una serie de extensiones que agregan funcionalidades y facilitan el trabajo del dia a dia.

> Para instalar las extensiones ejecutamos el comando 'control+p' y luego en el cuadro de texto pegamos el comando 'ext install ...'

## Git lens - ayudas visuales por doquier
Desarrollado por GitKraken esta extensión nos va a facilitar ver cambios por autor en el codigo, una barra inferior con datos sobre la rama y un visor de revisiones interesante

`ext install eamodio.gitlens`

![](https://raw.githubusercontent.com/gitkraken/vscode-gitlens/main/images/docs/current-line-blame.png){: .mx-auto.d-block :}

## Git history - Interfaz para revisiones de historicos muy completa

Super comodo para la hora de realizar busquedas, ver el historial de una o varias ramas totalmente de manera visual, comparar ramas y commits, tagear puntos en el repo y alguna función mas que se nos olvida

`ext install donjayamanne.githistory`

![](https://raw.githubusercontent.com/DonJayamanne/gitHistoryVSCode/master/images/lineHistoryCommandv3.gif){: .mx-auto.d-block :}

## Git Graph - Ver graficamente el estado de tu repositorio

Hace poco tuvimos un incidente en produccion donde luego de varias horas, descubrimos que todo inició dado un mal manejo de ramas que terminó arrastrando basura hasta la rama master, con esta extensión pudimos revisar merge a merge como mutaba nuestro repo y encontrar la solución.

`ext install mhutchie.git-graph`

![](https://github.com/mhutchie/vscode-git-graph/raw/master/resources/demo.gif){: .mx-auto.d-block :}

## Git Project Manager - Manejo de diferentes proyectos desde vscode

Con un solo comando podemos saltar de proyecto en proyecto o abrirlos en nuevas ventanas. recomendado por su facilidad para abrir repos sin pensar en nada mas, solo tipear el comando y el nombre del repositorio

`ext install felipecaputo.git-project-manager`

Este es el unico que tenemos que configurar antes de utilizar, para ello en pagina donde instalamos la extensión seleccionamos 'Extension Settings'

![texto](https://i.imgur.com/fHWOHYz.png){: .mx-auto.d-block :}

y dentro de base project settings vamos a editar el setting.json

![](https://i.imgur.com/13KJV6Z.png){: .mx-auto.d-block :}

y buscamos gitProjectManager.baseProjectsFolders donde vamos a agregar nuestro user

```
"gitProjectManager.baseProjectsFolders": [        
    "/home/<user>/Documents/"
]
```

y listo. Podemos ejecutar un escaneo con la opción "Refresh projects" que demorará unos segundos la primera vez y tenemos la extensión lista para utilizar

![](https://github.com/felipecaputo/git-project-manager/raw/HEAD/img/openProject.gif){: .mx-auto.d-block :}

# Conclusión

Con esto no estamos cerca de dejar de necesitar un cliente competente pero podemos realizar nuestras tareas basicas mucho mas facilmente. Lo unico que no encontramos forma de manejar de manera comoda las credenciales que no sean de github, quedará como un pendiente.