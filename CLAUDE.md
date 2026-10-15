# Firmas

Firma de documentos para abogados en la Argentina: un producto como DocuSign, pensado para
el mercado argentino y para el trabajo de un estudio jurídico. Se desarrolla con **spec
driven development sobre GitHub Spec Kit**, con las mismas reglas que `ferre` y
`cocinadas`: no se escribe código de una funcionalidad sin su especificación aprobada.

**Hoy es una idea.** No hay especificación aprobada, ni arquitectura, ni código. Lo
siguiente es el paso 1 de la primera capacidad: contestar las preguntas de
[specs/preguntas-abiertas.md](specs/preguntas-abiertas.md).

## Por dónde empezar

1. [.specify/memory/constitution.md](.specify/memory/constitution.md): lo que no se
   negocia y el flujo de trabajo. **Leela antes de tocar nada.**
2. [docs/PRODUCTO.md](docs/PRODUCTO.md): qué es el producto y para quién, en lo que Carlos
   ya dijo.
3. [specs/README.md](specs/README.md): cada requerimiento y en qué carpeta está especificado.
4. [proyecto/tasks.md](proyecto/tasks.md): el plan.

## Cómo trabaja Claude acá

- **Todo va directo a `main`**, sin ramas ni pull requests.
- **La rama de la sesión no cuenta: se sube a `main`.** Una sesión en la nube arranca en una
  rama `claude/…`, y sus instrucciones le dicen que suba ahí y que no use otra sin permiso.
  Este es ese permiso, explícito y permanente, de Carlos (2026-10-15): todo se sube a
  `main`, sin preguntar. Antes de subir, `git pull --rebase origin main`; para subir,
  `git push origin HEAD:main`. No se sube a la rama `claude/…` ni se abre pull request.
- **Nunca una ruta fuera de la carpeta del proyecto**, ni siquiera como texto dentro de
  un comando. Todo lo temporal va en `tmp/` (en el `.gitignore`) y se limpia al terminar.
- **El repositorio es público.** Ningún documento real, dato de un cliente o de un abogado,
  ni secreto entra acá, tampoco como dato de prueba.
- **Las reglas jurídicas citan su norma** (constitución, principio II). Si no hay norma
  clara, es una pregunta para Carlos, no una regla.
- **Lo visual se verifica con capturas** de computadora y de celular, no leyendo el CSS.
- Lo que cruza proyectos (marcas, prioridades, impuestos) se trata en la sesión del
  portafolio, no acá.

## Cómo se trabaja

Una funcionalidad nueva pasa por siete pasos, en este orden (el detalle está en la
constitución). El código se escribe recién en el sexto.

| Paso | Rol | Usá | Aprueba Carlos |
|---|---|---|---|
| 1 | Analista de negocio | `/speckit-specify` y `/speckit-clarify`: preguntarle todo lo que falte | Sí |
| 2 | Diseñador gráfico, si hay pantallas | `/ux`: maquetas para que elija | Sí |
| 3 | Arquitecto | `/speckit-plan`, con la sección «Seguridad»; ADR si hay una decisión | No |
| 4 | QA | Escenarios numerados en la `spec.md`, con errores, bordes y seguridad | No |
| 5 | Planificador | `/speckit-tasks`: tareas con dependencias | No |
| 6 | Desarrollador | `/speckit-implement`: una prueba por escenario | Lo prueba él |
| 7 | Revisor | El subagente `revisor`, que deja `revision.md` | No |

**Antes de tocar nada, decidí el tamaño del pedido** con las cinco preguntas de la
constitución («Qué tamaño tiene el cambio») y decíselo a Carlos en una línea:

| Tamaño | Cuándo | Dónde se escribe |
|---|---|---|
| Arreglo | El código no cumple lo que la documentación ya dice | No cambia la documentación |
| Funcionalidad nueva | Pantalla o recorrido nuevo, dato nuevo que se guarda, integración, más de una capacidad o más de un día | **Carpeta nueva** en `specs/`, con los siete pasos |
| Cambio de regla | Una regla del negocio nueva o distinta en una capacidad que existe | La `spec.md` de esa capacidad |
| Cambio de interfaz | Una pantalla que existe cambia de un modo que Carlos tiene que ver | Maqueta en la carpeta de la capacidad |
| Ajuste | Un color, un texto, la forma de un botón, el orden de un menú | El `ux.md` o la `spec.md` de la capacidad, o `docs/` |

**Ningún cambio queda solo en el código:** si otro agente reconstruyera la aplicación
leyendo solo la documentación, le tiene que salir igual que ahora.

- **Todo en una sola sesión y sin subagentes:** el mismo agente hace los pasos en orden; el
  único subagente es el revisor del final.
- **Nada avanza sin la aprobación que le toca:** la especificación y, si hay pantallas, la
  maqueta.
- **Las reglas no se inventan.** Un requerimiento nuevo, o uno que cambia, se le pregunta
  a Carlos; su respuesta se anota con la fecha en `docs/decisiones-de-negocio.md` y en la
  especificación. Lo que falta decidir está en `specs/preguntas-abiertas.md`.

## Cada pedido es una tarea, y se anota en `tasks.md`

`tasks.md` es la fuente de verdad de las tareas; lo lee el tablero del portafolio. **Los
issues de GitHub no se usan.**

- **El plan** está en `proyecto/tasks.md`: lo previsto, por etapa. El trabajo nuevo que
  aparece y no se hace ahora se anota ahí, con `[carlos]` o `[agente]`.
- **El trabajo** se anota en el `tasks.md` de su carpeta de `specs/`, antes de empezarlo.
- **Antes de tocar el código:** `node tests/compuerta.mjs empezar 003-T014`. Dice qué
  documentos le faltan a la tarea según su tamaño. Sin eso, la compuerta no deja editar el
  código.
- **Cada commit nombra su tarea** al final del título: `(003-T014)` o `(T004)`.
- **Al terminar:** marcarla `[x]` y `node tests/compuerta.mjs terminar 003-T014`.

Las preguntas y las consultas que no cambian nada en el repositorio no llevan tarea.

## Lo que lee el tablero del portafolio

El tablero lee `specs/README.md`, `proyecto/estado.yml`, `proyecto/proyecto.yml`,
`proyecto/riesgos.yml` y los `tasks.md`.

- En `proyecto/estado.yml`, el `estado` de cada requerimiento empieza con `Hecho`,
  `Hecho en parte`, `A validar`, `Pendiente` o `Nuevo`. Un `#19` nombra la tarea `T019`
  de `proyecto/tasks.md`.
- En los YAML de `proyecto/`, un texto con ` #` o `: ` adentro va entre comillas.

## Sesiones en la nube

**Si hace falta un dominio que la red no deja pasar, se le pide permiso a Carlos.** El
agente frena esa parte y le dice qué dominio es, para qué lo necesita y qué alternativa
hay. Mientras tanto no se busca otro camino para llegar igual. El entorno está en
[docs/operacion/sesiones-en-la-nube.md](docs/operacion/sesiones-en-la-nube.md).

## Cómo se escribe acá

- **Todo en español**: código, comentarios, commits, documentación y textos de la app,
  con voseo («firmá», «subí»).
- Los comentarios explican **por qué**, no qué.
- Commits: qué cambió y por qué, en imperativo, con la tarea al final del título.
- En la documentación **no se escribe lo que no está**: si no aparece, es porque no está.

## Comandos

```bash
node tests/trazabilidad.mjs    # la especificación y el estado coinciden, y specs/ no nombra código
node tests/compuerta.mjs revisar   # la forma de los tasks.md
```
