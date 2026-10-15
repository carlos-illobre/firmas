# Feature Specification: Historial y auditoría

**Feature Branch**: `006-actividad`

**Created**: 2026-10-15

**Status**: Aprobada (2026-10-15)

**Maquetas**: Aprobadas (2026-10-15, decisiones 40 y 41); ver [ux.md](ux.md)

**Input**: Decisiones 18 y 35 de Carlos (2026-10-15): la pantalla de Actividad del diseño de Figma
está en la primera versión. Decisión 23: lo que pasa en cada pedido tiene que poder probarse.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Reconstruir lo que pasó (Priority: P1)

El abogado ve todos los eventos del estudio, agrupados por día y con la hora al segundo:
quién firmó, descargó, recibió un recordatorio, agregó a alguien. Filtra por período, por
participante y por acción, y exporta el registro.

**Why this priority**: es la trazabilidad que pide un estudio para responder ante un
cliente o un juzgado.

**Independent Test**: con un pedido firmado y descargado, filtrar por ese participante y
exportar, y comprobar que están los dos eventos.

**Acceptance Scenarios**:

1. **E01** **Given** eventos de varios días, **When** el abogado entra, **Then** los ve
   agrupados por día, del más nuevo al más viejo, con hora, minuto y segundo.
2. **E02** **Given** eventos de varios participantes, **When** filtra por uno y por «Firma
   completada», **Then** ve solo esos.
3. **E03** **Given** un filtro aplicado, **When** aprieta «Exportar registro», **Then**
   descarga los eventos filtrados.

### Edge Cases

- Un abogado sin permiso sobre un documento no ve sus eventos.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-55**: El historial muestra los eventos de la capacidad 001 y los del estudio
  (descargas, cambios de destinatarios, miembros agregados), agrupados por día, con hora al
  segundo, documento y resultado.
- **RF-56**: Se filtra por período, por participante y por acción.
- **RF-57**: Se exporta lo filtrado, en CSV (decisión 35).
- **RNF-09**: Nadie puede borrar ni cambiar un evento, tampoco un administrador.

### Key Entities *(include if feature involves data)*

- **Evento** (de la capacidad 001), más los del estudio.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Todo evento de un pedido aparece en el historial en menos de un minuto.

## Assumptions

Supuesto aprobado por Carlos el 2026-10-15 (decisión 39):

- Cada abogado ve los eventos de los documentos que puede ver.
