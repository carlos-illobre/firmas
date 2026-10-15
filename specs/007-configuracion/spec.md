# Feature Specification: Cuentas, equipo y configuración

**Feature Branch**: `007-configuracion`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisiones 18, 36, 37 y 38 de Carlos (2026-10-15): la pantalla de Configuración del diseño de
Figma está en la primera versión. Decisión 6: por ahora nadie paga.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Entrar al producto (Priority: P1)

Un abogado crea su cuenta y la de su estudio, e ingresa al producto. Los firmantes no
necesitan cuenta (decisión 12).

**Why this priority**: sin cuenta no hay solicitante.

**Independent Test**: crear una cuenta, salir y volver a entrar.

**Acceptance Scenarios**:

1. **E01** **Given** alguien sin cuenta, **When** se registra con su nombre, su correo, una
   contraseña y el nombre de su estudio, **Then** confirma el correo y entra a su estudio.
2. **E02** **Given** un usuario que olvidó la contraseña, **When** la pide de nuevo, **Then**
   recibe un enlace por correo para cambiarla.

---

### User Story 2 - Armar el equipo (Priority: P1)

Un miembro del estudio invita a sus compañeros. Todos pueden lo mismo.

**Why this priority**: un estudio trabaja en equipo, y los documentos tienen secreto
profesional.

**Independent Test**: invitar a un compañero, que acepte, y comprobar que ve los documentos
del estudio.

**Acceptance Scenarios**:

1. **E03** **Given** un miembro del estudio, **When** invita a un compañero por correo,
   **Then** el compañero recibe la invitación y, al aceptarla, entra al estudio.
2. **E04** **Given** un miembro al que se le quita el acceso, **When** intenta entrar,
   **Then** ya no puede ver nada del estudio.

---

### User Story 3 - Ajustar el producto (Priority: P2)

El estudio configura la seguridad de acceso, qué avisos recibe cada uno, las preferencias de
los documentos (formato de fecha, recordatorios y forma de firma predeterminados) y sus
datos.

**Why this priority**: tiene valores razonables por defecto; se ajusta después.

**Independent Test**: cambiar los recordatorios predeterminados y comprobar que un pedido
nuevo los trae.

**Acceptance Scenarios**:

1. **E05** **Given** recordatorios predeterminados cada dos días, **When** se arma un pedido
   nuevo, **Then** trae esa frecuencia, que se puede cambiar.
2. **E06** **Given** un usuario que apagó el aviso de pedidos completados, **When** se
   completa uno suyo, **Then** no recibe ese aviso.

### Edge Cases

- El último miembro de un estudio no se puede quitar a sí mismo.
- Una invitación vencida o ya usada.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-58**: El registro es libre (decisión 38). Un abogado se registra con nombre, correo y contraseña, crea su estudio,
  confirma su correo, entra y sale, y recupera la contraseña.
- **RF-59**: Cualquier miembro del estudio invita a otros por correo y les quita el acceso.
  Dentro del estudio no hay roles: todos pueden lo mismo (decisión 36).
- **RF-60**: La seguridad y autenticación del estudio se configura: métodos de acceso y
  políticas.
- **RF-61**: Cada usuario elige qué avisos recibe.
- **RF-62**: El estudio fija las preferencias de los documentos: formato de fecha,
  recordatorios y vencimiento predeterminados, y forma de firma predeterminada.
- **RF-63**: El estudio guarda sus datos: nombre, logo e información de contacto.
- **RF-64**: El producto no se conecta con otros servicios, salvo los mínimos necesarios
  para funcionar: el envío de correos, de WhatsApp y de SMS, la validación de identidad, y la
  firma digital (decisión 37). No hay una sección de integraciones.
- **RNF-10**: Las contraseñas no se guardan en claro y los intentos de ingreso fallidos se
  limitan.

### Key Entities *(include if feature involves data)*

- **Estudio**: nombre, datos y preferencias.
- **Usuario**: nombre, correo, estudio y sus avisos.
- **Invitación**: correo, quién invitó, vencimiento y si se usó.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Un abogado se registra y envía su primer pedido en menos de 5 minutos.

## Assumptions

Supuestos a aprobar:

- Se entra con correo y contraseña, y se puede activar un segundo factor por código.
- Un usuario pertenece a un solo estudio. Quien se registra sin invitación crea un estudio
  nuevo.
- «Facturación y plan» no está en la primera versión, porque nadie paga (decisión 6).
