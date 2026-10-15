# Feature Specification: Inicio y documentos

**Feature Branch**: `002-documentos`

**Created**: 2026-10-15

**Status**: Aprobada (2026-10-15)

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Decisiones 18, 30 y 31 de Carlos (2026-10-15): la primera versión tiene todas las pantallas
de las maquetas. Esta capacidad cubre Inicio, la lista de documentos y el detalle de un
documento de la maqueta de Lovable. Se apoya en los pedidos de firma de la capacidad 001.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo. -->

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Saber qué hay que hacer hoy (Priority: P1)

Al entrar, el abogado ve en Inicio lo que necesita su atención: cuántos documentos esperan
su acción, cuántos esperan la firma de otros, cuántos se completaron este mes y cuántos están
demorados o vencidos; la lista de lo que requiere atención, los documentos recientes, los
próximos vencimientos y la actividad reciente.

**Why this priority**: es la pantalla de entrada y la que ordena el trabajo del día.

**Independent Test**: con pedidos en distintos estados, entrar y comprobar que los números y
las listas coinciden con ellos.

**Acceptance Scenarios**:

1. **E01** **Given** un abogado con dos pedidos que esperan su firma, **When** entra,
   **Then** Inicio muestra «2» en «Esperando mi acción» y los dos en «Requiere tu atención».
2. **E02** **Given** un pedido vencido, **When** el abogado entra, **Then** figura en
   «Demorados o vencidos» y en «Requiere tu atención».
3. **E03** **Given** pedidos con vencimiento en los próximos días, **When** el abogado entra,
   **Then** los ve en «Próximos vencimientos», del más cercano al más lejano.

---

### User Story 2 - Encontrar un documento (Priority: P1)

El abogado ve todos los documentos del estudio a los que tiene acceso, filtra por estado y
por cliente, busca por nombre y ve de cada uno el cliente, el estado, la última actividad,
la próxima acción y el responsable.

**Why this priority**: sin la lista no se puede seguir más de un pedido.

**Independent Test**: con diez documentos de tres clientes, filtrar por un cliente y un
estado y comprobar el resultado.

**Acceptance Scenarios**:

1. **E04** **Given** documentos en distintos estados, **When** el abogado elige «Esperando a
   otros», **Then** ve solo esos.
2. **E05** **Given** documentos de varios clientes, **When** elige un cliente, **Then** ve
   solo los de ese cliente.
3. **E06** **Given** un documento «Contrato de locación», **When** escribe «locación» en el
   buscador, **Then** lo encuentra.
4. **E07** **Given** un documento que espera la firma de otros, **When** aprieta «Recordar»
   en su fila, **Then** se manda un recordatorio, como en la capacidad 001.

---

### User Story 3 - Ver el detalle de un documento (Priority: P1)

El abogado abre un documento y ve la vista previa, los participantes con su estado, la
próxima acción y su fecha límite, y la línea de tiempo. Desde ahí recuerda, descarga,
archiva o cancela el proceso de firma.

**Why this priority**: es donde se sigue un pedido en particular.

**Independent Test**: abrir un pedido con un firmante que ya firmó y otro que solo lo vio, y
comprobar los estados y la línea de tiempo.

**Acceptance Scenarios**:

1. **E08** **Given** un pedido con un firmante que firmó y otro que lo vio, **When** el
   abogado abre el detalle, **Then** ve a uno «Firmado» y al otro «Visualizado», y los dos
   eventos en la línea de tiempo.
2. **E09** **Given** un documento completado, **When** el abogado lo archiva, **Then** deja
   de aparecer en «Todos» y aparece en «Archivados».
3. **E10** **Given** un documento completado, **When** aprieta «Descargar», **Then** baja el
   documento firmado y la constancia.
4. **E11** **Given** un pedido con dos firmantes, de los que uno ya firmó, **When** el
   solicitante abre el editor y mueve el campo del otro, **Then** el cambio se guarda, el
   otro recibe el pedido de nuevo, y los campos del que ya firmó no se pueden mover.
5. **E12** **Given** un documento sin cliente, **When** se lo ve en la lista, **Then** la
   columna del cliente queda vacía y el filtro por cliente no lo muestra.

### Edge Cases

- Un abogado sin permiso sobre un documento no lo ve ni en la lista ni en el buscador.
- Un estudio sin documentos: Inicio y la lista lo dicen y ofrecen «Nuevo documento».
- Archivar un documento que espera firmas.

## Requirements *(mandatory)*

### Functional Requirements

- **RF-31**: Inicio muestra un saludo con el nombre y la fecha, y cuatro números: esperando
  mi acción, esperando firma de otros, completados este mes, y demorados o vencidos.
- **RF-32**: Inicio lista lo que requiere atención del abogado, ordenado por urgencia, con
  acceso directo a cada uno.
- **RF-33**: Inicio muestra los documentos recientes, los próximos vencimientos y la
  actividad reciente del estudio.
- **RF-34**: La lista de documentos muestra, por documento: nombre, etiquetas, cliente,
  estado, última actividad, próxima acción y responsable.
- **RF-35**: La lista se filtra por estado (todos, esperando mi acción, esperando a otros,
  completados, archivados) y por cliente, y se pagina.
- **RF-36**: Un buscador en todas las pantallas encuentra documentos, clientes y plantillas
  por nombre.
- **RF-37**: El detalle de un documento muestra el nombre, el estado, el tipo, el cliente,
  el responsable, la vista previa paginada, los participantes con su estado, la próxima
  acción con su fecha límite y la línea de tiempo de eventos de la capacidad 001.
- **RF-38**: Desde el detalle se puede recordar, descargar, archivar, cancelar el proceso de
  firma y abrir el editor.
- **RF-38a**: El editor cambia todo lo referente a la firma de un pedido: los destinatarios,
  el orden, el canal, la identidad, la posición de la firma y los campos, y el vencimiento
  (decisión 30). Lo de un firmante que ya firmó no se puede cambiar, y cada firmante afectado
  por un cambio recibe el pedido de nuevo.
- **RF-39**: Un documento se puede archivar y desarchivar; archivado no aparece en «Todos».
- **RF-40**: Cada documento tiene uno o más firmantes y un responsable del estudio; el
  cliente y las etiquetas son opcionales (decisión 31).
- **RNF-05**: Inicio, la lista y el detalle se usan completos en el celular y en la
  computadora.

### Key Entities *(include if feature involves data)*

- **Documento** (de la capacidad 001), con su cliente, su responsable, sus etiquetas y si
  está archivado.
- **Cliente**: el contacto o la organización de la capacidad 004.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Un abogado encuentra cualquier documento en menos de 15 segundos.
- **SC-002**: Los números de Inicio coinciden siempre con los filtros de la lista.

## Assumptions

Supuestos aprobados por Carlos el 2026-10-15 (decisión 39):

- «Demorado» es un pedido que vence en los próximos tres días sin estar completo.
- Lo de un firmante que ya firmó no se cambia en el editor, porque su firma quedó hecha sobre
  esa versión del documento.
- La próxima acción se deduce del estado: esperar la firma de alguien, revisar, reenviar,
  completar destinatarios o ninguna.
