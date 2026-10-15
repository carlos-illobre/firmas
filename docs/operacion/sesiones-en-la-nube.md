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

Lo único que corre hoy son las dos herramientas de `tests/`, con Node. Cuando el paso 3
elija el stack, se escribe acá lo que falte: acceso a internet, variables y versiones.

### Script de preparación

Carlos lo agregó al entorno el 2026-10-15. Corre al arrancar cada sesión nueva; una sesión
que ya estaba abierta no lo corre.

```bash
#!/bin/bash
set -e
npm install -g pnpm@10.15.0
npx -y playwright@1.63.0 install --with-deps chromium
```

- **pnpm 10.15.0**, para instalar las dependencias cuando haya código.
- **Playwright 1.63.0 con su Chromium**, para las capturas de computadora y de celular que
  verifican lo visual, y para leer las maquetas de Lovable y Figma. La imagen de la nube ya
  trae otro Playwright y otro Chromium (en `/opt/pw-browsers`, con
  `PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1`); el de 1.63.0 es el que vale para el proyecto.

Si una sesión necesita estas herramientas y el script no corrió, el agente corre esas dos
líneas.

### Dominios

Además de los del entorno por defecto, Carlos habilitó estos por pedido de una sesión. Si
una sesión encuentra alguno cerrado, se lo pide de nuevo:

| Dominio | Para qué |
|---|---|
| `lovable.dev` y `*.lovable.app` | Leer la maqueta de Lovable |
| `*.figma.site` | Leer el diseño de Figma |
| `argentina.gob.ar` y `boletinoficial.gob.ar` | Verificar las normas que citan las reglas jurídicas |

## Las skills

Las de Spec Kit (`speckit-*`), la de maquetas (`ux`) y las de animación (`animate`,
`animation-performance`, `review-animations`, `find-animation-opportunities`,
`improve-animations`) están copiadas en `.claude/skills/` de `ferre`, porque la nube no
tiene las globales. Las de animación son una versión adaptada: ninguna animación corre en
el hilo principal (el detalle, en el `ADAPTATION.md` de cada una).
