# Feature Specification: Cuentas, equipo y configuración

**Feature Branch**: `007-configuracion`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisión 18 de Carlos (2026-10-15): la pantalla de Configuración del diseño de
Figma está en la primera versión. Decisión 6: por ahora nadie paga.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Entrar al producto (Priority: P1)

Un abogado crea su cuenta y la de su estudio, e ingresa al producto. Los firmantes no
necesitan cuenta (decisión 12).

**Why this priority**: sin cuenta no hay remitente.

**Independent Test**: crear una cuenta, salir y volver a entrar.

**Acceptance Scenarios**:

1. **E01** **Given** alguien sin cuenta, **When** se registra con su nombre, su correo, una
   contraseña y el nombre de su estudio, **Then** confirma el correo y entra a su estudio.
2. **E02** **Given** un usuario que olvidó la contraseña, **When** la pide de nuevo, **Then**
   recibe un enlace por correo para cambiarla.

---

### User Story 2 - Armar el equipo (Priority: P1)

El administrador del estudio invita a colaboradores y les da un rol que dice qué pueden
hacer y ver.

**Why this priority**: un estudio trabaja en equipo, y los documentos tienen secreto
profesional.

**Independent Test**: invitar a un colaborador, que acepte, y comprobar que ve lo que su rol
permite.

**Acceptance Scenarios**:

1. **E03** **Given** un administrador, **When** invita a un colaborador por correo con un
   rol, **Then** el colaborador recibe la invitación y, al aceptarla, entra al estudio.
2. **E04** **Given** un colaborador al que se le quita el acceso, **When** intenta entrar,
   **Then** ya no puede ver nada del estudio.

---

### User Story 3 - Ajustar el producto (Priority: P2)

El estudio configura la seguridad de acceso, qué avisos recibe cada uno, las preferencias de
los documentos (formato de fecha, recordatorios y forma de firma predeterminados), las
integraciones y sus datos.

**Why this priority**: tiene valores razonables por defecto; se ajusta después.

**Independent Test**: cambiar los recordatorios predeterminados y comprobar que un pedido
nuevo los trae.

**Acceptance Scenarios**:

1. **E05** **Given** recordatorios predeterminados cada dos días, **When** se arma un pedido
   nuevo, **Then** trae esa frecuencia, que se puede cambiar.
2. **E06** **Given** un usuario que apagó el aviso de pedidos completados, **When** se
   completa uno suyo, **Then** no recibe ese aviso.

### Edge Cases

- El último administrador no se puede quitar a sí mismo.
- Una invitación vencida o ya usada.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-53**: Un abogado se registra con nombre, correo y contraseña, crea su estudio,
  confirma su correo, entra y sale, y recupera la contraseña.
- **RF-54**: El administrador invita colaboradores por correo, les asigna un rol, se lo
  cambia y les quita el acceso.
- **RF-55**: La seguridad y autenticación del estudio se configura: métodos de acceso y
  políticas.
- **RF-56**: Cada usuario elige qué avisos recibe.
- **RF-57**: El estudio fija las preferencias de los documentos: formato de fecha,
  recordatorios y vencimiento predeterminados, y forma de firma predeterminada.
- **RF-58**: El estudio guarda sus datos: nombre, logo e información de contacto.
- **RF-59**: El estudio conecta integraciones con herramientas propias.
- **RNF-10**: Las contraseñas no se guardan en claro y los intentos de ingreso fallidos se
  limitan.

### Key Entities *(include if feature involves data)*

- **Estudio**: nombre, datos, preferencias e integraciones.
- **Usuario**: nombre, correo, rol, estudio y sus avisos.
- **Invitación**: correo, rol, quién invitó, vencimiento y si se usó.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Un abogado se registra y envía su primer pedido en menos de 5 minutos.

## Assumptions

- Hay dos roles: administrador, que hace todo, y colaborador, que maneja documentos pero no
  la configuración.
- Un usuario pertenece a un solo estudio.
- «Facturación y plan» no está en la primera versión, porque nadie paga (decisión 6).

## Preguntas

- [NEEDS CLARIFICATION: las preguntas de «007 · Configuración» en
  [preguntas-abiertas.md](../preguntas-abiertas.md)]
