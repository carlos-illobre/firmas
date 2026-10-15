# Sesiones de Claude Code en la nube

Las sesiones que trabajan en Firmas corren en la nube de Anthropic (claude.ai/code, o
**Cloud** en la app de escritorio). Clonan el repositorio, trabajan y suben a `main`.

No trabajen a la vez dos sesiones que suban a `main`.

## Dominios que no están en la lista

**Si hace falta un dominio que la red no deja pasar, se le pide permiso a Carlos.** En una
sesión en la nube, si una descarga o una conexión falla porque el dominio no está entre los
permitidos del entorno, el agente frena esa parte y le dice a Carlos qué dominio es, para
qué lo necesita y qué alternativa hay. Carlos decide si lo agrega al entorno. Mientras tanto
no se busca otro camino para llegar igual (otro espejo, otro servicio, bajarlo por otro
lado ni copiarlo al repositorio).

## El entorno `firmas`

Mientras no haya código, alcanza con el entorno por defecto: lo único que corre son las dos
herramientas de `tests/`, con Node. Cuando el paso 3 elija el stack, se crea el entorno
`firmas` con **Add cloud environment** y se escribe acá: acceso a internet, variables y
script de preparación, con las versiones fijadas.

## Las skills

Las de Spec Kit (`speckit-*`), la de maquetas (`ux`) y las de animación (`animate`,
`animation-performance`, `review-animations`, `find-animation-opportunities`,
`improve-animations`) están copiadas en `.claude/skills/` de `ferre`, porque la nube no
tiene las globales. Las de animación son una versión adaptada: ninguna animación corre en
el hilo principal (el detalle, en el `ADAPTATION.md` de cada una).
