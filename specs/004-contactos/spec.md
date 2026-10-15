# Feature Specification: Clientes y contactos

**Feature Branch**: `004-contactos`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisión 18 de Carlos (2026-10-15): la pantalla de Contactos del diseño de Figma
está en la primera versión.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Tener a mano los clientes y sus contactos (Priority: P1)

El abogado guarda las personas y las organizaciones con las que trabaja: una organización
tiene contactos, y cada uno tiene sus datos. De cada uno ve cuántos documentos tiene y
cuántos pedidos están pendientes.

**Why this priority**: evita cargar los mismos datos en cada pedido y permite seguir el
trabajo por cliente.

**Independent Test**: crear una organización con un contacto, usarlo como firmante en un
pedido y ver el documento asociado.

**Acceptance Scenarios**:

1. **E01** **Given** un abogado, **When** crea la organización «Andina Tecnología S.A.» y el
   contacto «Lucía Ramos» dentro de ella, **Then** los ve en la lista, ella como contacto de
   Andina.
2. **E02** **Given** un contacto guardado, **When** el abogado carga destinatarios en un
   pedido y escribe su nombre, **Then** el producto lo sugiere y completa sus datos.
3. **E03** **Given** una organización con dos pedidos esperando firmas, **When** se la ve en
   la lista, **Then** dice «2 solicitudes pendientes» y lleva a sus documentos.

### Edge Cases

- Dos contactos con el mismo correo.
- Borrar un contacto que figura en pedidos: los pedidos quedan como estaban.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-46**: Hay contactos de dos clases: personas y organizaciones. Una persona puede
  pertenecer a una organización.
- **RF-47**: De una persona se guarda nombre y apellido, correo y teléfono; de una
  organización, su nombre.
- **RF-48**: La lista de contactos muestra, de cada uno, cuántos documentos tiene asociados y
  cuántos pedidos o revisiones están pendientes, y se filtra.
- **RF-49**: Al cargar destinatarios en un pedido se sugieren los contactos guardados.
- **RF-50**: Los contactos se crean, editan y borran.
- **RNF-07**: Los datos de los contactos son datos personales: se guardan solo los
  necesarios, ciertos y pertinentes, y con medidas que eviten que se adulteren, se pierdan o
  los vea quien no corresponde. *Ley 25.326, arts. 4 y 9, verificada el 2026-10-15 en
  argentina.gob.ar.*

### Key Entities *(include if feature involves data)*

- **Contacto**: persona u organización, sus datos, la organización a la que pertenece y los
  documentos en los que figura.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Cargar un firmante que ya es contacto lleva menos de 5 segundos.

## Assumptions

- Un firmante nuevo de un pedido no se guarda solo como contacto: el abogado elige guardarlo.
- Los contactos son del estudio, compartidos entre sus miembros.

## Preguntas

- [NEEDS CLARIFICATION: las preguntas de «004 · Contactos» en
  [preguntas-abiertas.md](../preguntas-abiertas.md)]
