# Tasks: plan de Firmas

Las tareas del proyecto, por etapa. **Este archivo es la fuente de verdad**: lo lee el
tablero del portafolio, y una tarea existe cuando está escrita acá.

Cada tarea es una línea. Entre corchetes van quién la hace (`[carlos]` o `[agente]`),
la prioridad si no es la normal (`[alta]`, `[baja]`), `[definir]` si antes Carlos
tiene que decidir algo y `[en curso]` mientras se hace. Al final, entre paréntesis, de
qué depende, cuánto lleva y entre qué fechas va:

    - [ ] T041 [carlos] [alta] Llamar al plomero (depende de T040) (estimación 2h) (2026-10-20 a 2026-10-22)

Una tarea nueva lleva el número que sigue al más alto del archivo y va bajo su etapa. Al
terminarla se marca `[x]`; no se borra.

## Definición

- [x] T001 [agente] Crear el repositorio con el flujo de Spec Kit de ferre y cocinadas
- [ ] T002 [carlos] [alta] [definir] Contestar las preguntas abiertas (estimación 2h)
  Están en specs/preguntas-abiertas.md. Se pueden contestar en una sesión de este repositorio,
  que las anota en docs/decisiones-de-negocio.md.
- [ ] T003 [agente] [alta] Especificar la primera capacidad: paso 1, con /speckit-specify y /speckit-clarify (depende de T002)
- [ ] T004 [carlos] [alta] Aprobar la especificación de la primera capacidad (depende de T003)
- [ ] T005 [agente] Maquetas de la primera capacidad: paso 2, con /ux (depende de T004)
- [ ] T006 [carlos] Elegir y aprobar las maquetas (depende de T005)
- [ ] T007 [agente] Arquitectura: stack, alojamiento y proveedores de firma e identidad, con un ADR cada uno (depende de T004)
- [ ] T008 [carlos] Crear el entorno de la nube `firmas` (depende de T007)
  Cómo, en docs/operacion/sesiones-en-la-nube.md. Hace falta recién cuando haya código.
