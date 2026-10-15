# Feature Specification: Plantillas y documentos desde cero

**Feature Branch**: `003-plantillas`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisión 11 de Carlos (2026-10-15): un documento también se empieza con una
plantilla del estudio o desde cero. Decisión 18: la pantalla de Plantillas del diseño de
Figma está en la primera versión.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Usar una plantilla (Priority: P1)

El abogado elige una plantilla del estudio, completa sus datos variables (por ejemplo, las
partes y el monto) y sigue con el pedido de firma de la capacidad 001. La plantilla no
cambia.

**Why this priority**: es lo que más tiempo le ahorra a un estudio que firma muchos
documentos parecidos.

**Independent Test**: usar una plantilla con dos datos variables, completarlos y comprobar
que el documento del pedido los trae y la plantilla sigue igual.

**Acceptance Scenarios**:

1. **E01** **Given** una plantilla con los datos variables «Cliente» y «Monto», **When** el
   abogado la usa y los completa, **Then** el documento del pedido trae esos valores.
2. **E02** **Given** un documento armado con una plantilla, **When** se envía, **Then** la
   plantilla queda como estaba.
3. **E03** **Given** una plantilla con campos de firma ya ubicados, **When** se usa, **Then**
   el pedido trae esos campos, asignados a los firmantes que se carguen.

---

### User Story 2 - Crear y ordenar plantillas (Priority: P2)

El abogado crea una plantilla, la clasifica por categoría (servicios, confidencialidad,
comerciales, laborales, autorizaciones) y marca sus favoritas.

**Why this priority**: sin plantillas creadas no hay qué usar, pero se puede empezar
subiendo archivos.

**Independent Test**: crear una plantilla en «Laborales», marcarla favorita y encontrarla
filtrando.

**Acceptance Scenarios**:

1. **E04** **Given** un abogado, **When** crea una plantilla con un nombre, una categoría y
   un texto con datos variables, **Then** la ve en la lista, con quién la usó por última vez
   y cuándo.
2. **E05** **Given** varias plantillas, **When** filtra por «Laborales», **Then** ve solo
   esas.

---

### User Story 3 - Redactar desde cero (Priority: P2)

El abogado redacta el documento en el producto, sin archivo, y sigue con el pedido de firma.

**Why this priority**: completa las tres formas de empezar, pero las otras dos cubren lo más
común.

**Independent Test**: redactar un texto con títulos y párrafos, seguir al pedido y comprobar
que el PDF que se firma tiene ese texto.

**Acceptance Scenarios**:

1. **E06** **Given** un abogado en «Crear desde cero», **When** redacta un texto y sigue,
   **Then** el texto se convierte a PDF y ese PDF es el que se firma.

### Edge Cases

- Una plantilla con un dato variable sin completar no deja seguir.
- Borrar una plantilla que se usó en pedidos: los pedidos quedan como estaban.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-41**: Hay plantillas del estudio, con nombre, categoría, texto, datos variables y,
  opcionalmente, campos de firma por rol de firmante.
- **RF-42**: Usar una plantilla pide completar sus datos variables y arma el documento del
  pedido sin cambiar la plantilla.
- **RF-43**: Las plantillas se listan con su categoría, cuándo y quién la usó por última vez;
  se filtran por categoría y se marcan como favoritas.
- **RF-44**: Se pueden crear, editar y borrar plantillas.
- **RF-45**: Se puede redactar un documento desde cero en el producto, con formato básico
  (títulos, negrita, listas), que se convierte a PDF para firmar.
- **RNF-06**: Usar una plantilla funciona en el celular y en la computadora.

### Key Entities *(include if feature involves data)*

- **Plantilla**: nombre, categoría, texto, datos variables, campos por rol de firmante,
  favorita, última vez usada y por quién.
- **Dato variable**: nombre, tipo (texto, fecha, número) y si es obligatorio.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Armar un pedido desde una plantilla lleva menos de la mitad del tiempo que
  subiendo un archivo.

## Assumptions

- La maqueta aclara que sus plantillas son ejemplos ficticios: el producto no trae modelos
  jurídicos propios; cada estudio carga los suyos.
- Una plantilla se crea escribiendo su texto en el producto o subiendo un Word.

## Preguntas

- [NEEDS CLARIFICATION: las preguntas de «003 · Plantillas» en
  [preguntas-abiertas.md](../preguntas-abiertas.md)]
