# Feature Specification: Tareas y vencimientos

**Feature Branch**: `005-tareas`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisión 18 de Carlos (2026-10-15): la pantalla de Tareas del diseño de Figma está
en la primera versión.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Organizar seguimientos, revisiones y fechas (Priority: P1)

El abogado anota tareas (revisar un documento, recordar una firma, una fecha contractual),
las asigna a sí mismo o a otro miembro del estudio, y las ve en lista o en calendario.

**Why this priority**: el producto acompaña el trabajo del estudio más allá de la firma.

**Independent Test**: crear una tarea para hoy vinculada a un documento, asignarla y verla en
«Hoy» y en el calendario.

**Acceptance Scenarios**:

1. **E01** **Given** un abogado, **When** crea la tarea «Revisar acuerdo» para hoy, con
   prioridad alta y vinculada a un documento, **Then** la ve en «Mis tareas» y en «Hoy», con
   el documento y el cliente.
2. **E02** **Given** una tarea asignada a otro miembro, **When** ese miembro entra, **Then**
   la ve en «Mis tareas», y quien la asignó la ve en «Asignadas».
3. **E03** **Given** tareas con fecha, **When** el abogado elige «Calendario», **Then** las
   ve en sus días.
4. **E04** **Given** tareas pendientes, **When** el abogado mira el menú, **Then** ve
   cuántas tiene.

### Edge Cases

- Una tarea vinculada a un documento que se archiva o se cancela.
- Una tarea vencida sin completar.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-51**: Una tarea tiene título, fecha, tipo (revisión, seguimiento, vencimiento),
  prioridad, responsable y, opcionalmente, un documento y un cliente vinculados.
- **RF-52**: Las tareas se ven en lista o en calendario, y se filtran en mis tareas,
  asignadas por mí y de hoy.
- **RF-53**: Las tareas se crean, editan, completan y borran.
- **RF-54**: El menú muestra cuántas tareas pendientes tiene el abogado.
- **RNF-08**: Las tareas se usan completas en el celular y en la computadora.

### Key Entities *(include if feature involves data)*

- **Tarea**: título, fecha, tipo, prioridad, responsable, quién la creó, documento y cliente
  vinculados, y si está completa.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Crear una tarea lleva menos de 20 segundos.

## Assumptions

- Las tareas las crea el abogado; el producto no crea tareas solo.

## Preguntas

- [NEEDS CLARIFICATION: las preguntas de «005 · Tareas» en
  [preguntas-abiertas.md](../preguntas-abiertas.md)]
