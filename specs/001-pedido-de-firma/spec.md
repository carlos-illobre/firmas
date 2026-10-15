# Feature Specification: Pedido de firma

**Feature Branch**: `001-pedido-de-firma`

**Created**: 2026-10-15

**Status**: Borrador  <!-- pasa a «Aprobada» cuando Carlos aprueba la especificación -->

**Maquetas**: Pendientes  <!-- «Aprobadas» cuando Carlos elige, o «No lleva pantallas» -->

**Input**: Las decisiones de Carlos del 2026-10-15 (5, 7, 8, 11 a 17 y 19 a 23 de
[docs/decisiones-de-negocio.md](../../docs/decisiones-de-negocio.md)): un abogado prepara un
documento, carga a los firmantes, elige cómo firma y se identifica cada uno, y lo envía; cada
firmante firma desde el correo, con su certificado o con firma electrónica; al terminar
queda el documento firmado y una constancia de lo que pasó.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo:
     «1. **E01** **Given** …». El paso de QA agrega los de error, los de borde y los que
     salen de la sección «Seguridad» del plan. Cada prueba nombra su escenario (001-E01). -->

## Palabras

- **Remitente**: el abogado, o cualquier miembro del estudio con cuenta, que prepara y envía
  el pedido.
- **Pedido de firma**: un documento con sus destinatarios, el orden, los campos, el
  vencimiento y los recordatorios. Es lo que en DocuSign se llama «sobre».
- **Destinatario**: cada persona del pedido. Es **firmante** o **recibe copia**. No necesita
  cuenta (decisión 12).
- **Firma digital**: la que se hace con un certificado de firma digital del firmante.
- **Firma electrónica**: la que se hace sin certificado, apretando un botón, después de
  comprobar la identidad del firmante como eligió el remitente.
- **Constancia**: el documento que se genera al terminar, con lo que pasó en el pedido.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Preparar y enviar un pedido de firma (Priority: P1)

El remitente sube un PDF o un Word, carga a los firmantes y a quienes reciben copia, elige
el orden de firma, ubica los campos de cada firmante en el documento, elige el vencimiento,
y lo envía. El recorrido tiene cuatro pasos: documento, destinatarios, campos, y revisar y
enviar.

**Why this priority**: sin pedido no hay nada que firmar; es el corazón del producto.

**Independent Test**: preparar un pedido con un PDF y dos firmantes, enviarlo y comprobar
que el primer firmante recibe el correo.

**Acceptance Scenarios**:

1. **E01** **Given** un remitente con cuenta, **When** sube un PDF, carga dos firmantes con
   nombre y correo, ubica un campo de firma para cada uno, elige un vencimiento y envía,
   **Then** el pedido queda «Esperando a otros» y los firmantes reciben el pedido por el
   canal elegido.
2. **E02** **Given** un remitente que sube un Word, **When** pasa al paso de destinatarios,
   **Then** el documento ya está convertido a PDF, el remitente ve ese PDF y lo que se envía
   y se firma es ese PDF (decisión 14).
3. **E03** **Given** un pedido con orden «uno después del otro», **When** se envía, **Then**
   solo el primer firmante recibe el pedido; cada uno recibe el suyo cuando firma el
   anterior (decisión 15).
4. **E04** **Given** un pedido con orden «todos a la vez», **When** se envía, **Then** todos
   los firmantes reciben el pedido al mismo tiempo.
5. **E05** **Given** un firmante sin campo de firma, **When** el remitente quiere enviar,
   **Then** no puede, y se le dice qué firmante no tiene campo.
6. **E06** **Given** un pedido a medio preparar, **When** el remitente sale del recorrido,
   **Then** queda guardado como «Borrador» y lo puede retomar.
7. **E07** **Given** un destinatario marcado «recibe copia», **When** se completa el pedido,
   **Then** recibe el documento firmado y la constancia, sin haber tenido que firmar.

---

### User Story 2 - Firmar desde el correo (Priority: P1)

El firmante recibe el pedido, aprieta el botón del mensaje y llega al documento sin crear
una cuenta. Si el remitente eligió una forma de comprobar su identidad, la pasa primero. Lee
el documento, completa sus campos y firma: con su certificado de firma digital, de una de
tres formas, o con firma electrónica apretando un botón (decisiones 12 y 19).

**Why this priority**: es la otra mitad del corazón del producto, y la usa gente que no es
abogada, a menudo desde el celular.

**Independent Test**: con un pedido enviado, abrir el enlace del firmante, comprobar su
identidad, firmar con firma electrónica y ver que el pedido avanza.

**Acceptance Scenarios**:

1. **E08** **Given** un firmante que recibió el pedido, **When** aprieta el botón del
   mensaje, **Then** ve el documento completo, sin crear cuenta, con sus campos marcados y
   la opción de descargar una copia.
2. **E09** **Given** un firmante para quien el remitente eligió código por SMS, **When** abre
   el pedido, **Then** tiene que ingresar el código que le llegó al teléfono antes de ver el
   documento.
3. **E10** **Given** un firmante sin certificado, **When** completa sus campos y elige firma
   electrónica, **Then** firma apretando un botón y el pedido registra la firma con la forma
   de identidad que usó.
4. **E11** **Given** un firmante con certificado de firma digital, **When** elige firmar con
   él, **Then** puede hacerlo subiendo el archivo del certificado, con su token o con la
   Plataforma de Firma Digital Remota, y la firma queda hecha con ese certificado.
5. **E12** **Given** un firmante con campos obligatorios sin completar, **When** quiere
   firmar, **Then** no puede, y el producto lo lleva al próximo campo pendiente.
6. **E13** **Given** el último firmante, **When** firma, **Then** el pedido pasa a
   «Completado», y todos los destinatarios y el remitente reciben el documento firmado y la
   constancia.

---

### User Story 3 - Rechazo, vencimiento, recordatorios y cancelación (Priority: P2)

Si un firmante rechaza firmar o el pedido vence, el pedido se cancela, se avisa al remitente
y se le ofrece reenviarlo (decisión 17). Mientras tanto, el producto manda recordatorios
automáticos (decisión 22), el remitente puede mandar uno cuando quiera, y puede cancelar el
pedido.

**Why this priority**: sin esto un pedido puede quedar abierto para siempre, pero el
recorrido principal funciona sin ello.

**Independent Test**: enviar un pedido, rechazarlo como firmante y comprobar que el
remitente recibe el aviso y puede reenviarlo.

**Acceptance Scenarios**:

1. **E14** **Given** un firmante que abrió el pedido, **When** lo rechaza, **Then** tiene
   que escribir el motivo, el pedido pasa a «Rechazado», nadie más puede firmarlo, y el
   remitente recibe un aviso con el motivo y la opción de reenviarlo.
2. **E15** **Given** un pedido sin completar, **When** llega su vencimiento, **Then** pasa
   a «Vencido», nadie puede firmarlo, y el remitente recibe un aviso con la opción de
   reenviarlo.
3. **E16** **Given** un pedido rechazado o vencido, **When** el remitente lo reenvía,
   **Then** se arma un pedido nuevo con el mismo documento, destinatarios y campos, que puede
   cambiar antes de enviar; el anterior queda como estaba.
4. **E17** **Given** un pedido esperando firmas, **When** pasa el tiempo de un recordatorio,
   **Then** cada firmante que todavía no firmó y ya recibió el pedido recibe un recordatorio
   por su canal.
5. **E18** **Given** un pedido esperando firmas, **When** el remitente aprieta «Recordar»,
   **Then** se manda un recordatorio a los firmantes que todavía no firmaron.
6. **E19** **Given** un pedido esperando firmas, **When** el remitente lo cancela, **Then**
   pasa a «Cancelado», nadie puede firmarlo y se avisa a los firmantes que ya lo habían
   recibido.

---

### User Story 4 - Constancia y prueba de lo que pasó (Priority: P2)

Cada cosa que pasa en un pedido queda registrada. Al completarse se genera una constancia,
pensada para presentarla en un juicio, con quién firmó, cuándo, desde dónde, con qué forma
de identidad y la huella del documento (decisión 23).

**Why this priority**: el valor de lo firmado depende de poder probarlo, pero la firma
existe antes que la constancia.

**Independent Test**: completar un pedido y comprobar que la constancia trae cada dato y que
la huella coincide con el documento firmado.

**Acceptance Scenarios**:

1. **E20** **Given** un pedido completado, **When** se abre la constancia, **Then** dice,
   por cada firmante: nombre, correo, forma de firma (digital o electrónica), forma de
   identidad usada, fecha y hora de cada evento, dirección IP y dispositivo desde donde
   firmó, y la huella del documento original y del firmado.
2. **E21** **Given** un documento firmado, **When** alguien le cambia un solo carácter,
   **Then** la huella ya no coincide y el producto lo informa al verificarlo.
3. **E22** **Given** un pedido, **When** se crea, se envía, alguien lo ve, firma, rechaza,
   recibe un recordatorio, vence o se cancela, **Then** queda un evento con quién, qué y
   cuándo, que no se puede borrar ni cambiar.

### Edge Cases

- El Word no se puede convertir (dañado, protegido con contraseña): se avisa y no se sigue.
- El PDF está protegido con contraseña o ya trae firmas digitales.
- Un firmante figura dos veces, o el remitente es también firmante.
- El correo de un firmante rebota: se avisa al remitente.
- Un firmante abre el enlace de un pedido rechazado, vencido, cancelado o que ya firmó.
- El certificado del firmante está vencido o revocado.
- Un firmante quiere delegar la firma en otra persona.
- El documento final y la constancia tienen que poder verificarse sin el producto.

## Requirements *(mandatory)*

### Functional Requirements

**El documento**

- **RF-01**: El remitente empieza un pedido de tres formas: subiendo un archivo, usando una
  plantilla del estudio o creando el documento desde cero (decisión 11). Las plantillas y la
  redacción desde cero están en la capacidad 003.
- **RF-02**: Se pueden subir archivos PDF y Word. Un Word se convierte a PDF antes de seguir;
  el remitente ve el PDF convertido, y lo que se envía y se firma es ese PDF (decisión 14).
  El tamaño y la cantidad de páginas máximas son una pregunta abierta.

**Los destinatarios**

- **RF-03**: El remitente carga cada destinatario con nombre y apellido, correo y, si el
  canal o la forma de identidad lo piden, teléfono celular. Marca si es firmante o recibe
  copia. Puede agregarse a sí mismo como firmante.
- **RF-04**: El remitente elige el orden de firma: uno después del otro, en el orden que
  arma, o todos a la vez (decisión 15).
- **RF-05**: Para cada firmante, el remitente elige cómo se comprueba su identidad si firma
  con firma electrónica: correo, código por SMS, código por WhatsApp, foto del DNI o
  validación contra RENAPER (decisiones 13 y 20).
- **RF-06**: Para cada destinatario, el remitente elige el canal por el que le llega el
  pedido: el correo u otro medio (decisión 21). Qué otros medios hay es una pregunta
  abierta.

**Los campos**

- **RF-07**: El remitente ubica sobre las páginas del documento los campos de cada firmante.
  Cada firmante tiene un color propio, y sus campos se ven con ese color
  ([sistema visual](../../docs/sistema-visual.md)).
- **RF-08**: Cada firmante tiene al menos un campo de firma. Un campo puede ser obligatorio u
  opcional.

**El envío**

- **RF-09**: Antes de enviar, el remitente ve un resumen: el documento, los destinatarios con
  su orden, canal e identidad, y los campos. Puede escribir un mensaje para los destinatarios.
- **RF-10**: El remitente elige cuándo vence el pedido (decisión 22).
- **RF-11**: El producto manda recordatorios automáticos a los firmantes que todavía no
  firmaron (decisión 22). El remitente puede, además, mandar un recordatorio cuando quiera.
- **RF-12**: Un pedido a medio preparar queda guardado como borrador, y el remitente lo puede
  retomar o borrar.

**La firma**

- **RF-13**: Cada firmante recibe un mensaje con un botón que lo lleva a su pedido, sin
  crear cuenta. El enlace es personal: lleva solo a lo que le toca a ese firmante (decisión
  12).
- **RF-14**: Si el remitente eligió una forma de identidad, el firmante la pasa antes de ver
  el documento.
- **RF-15**: El firmante ve el documento completo, puede descargar una copia, y el producto lo
  lleva de un campo pendiente al siguiente.
- **RF-16**: El firmante elige firmar con firma digital o con firma electrónica. Con firma
  digital usa su certificado de una de tres formas: subiendo el archivo del certificado, con
  su token, o con la Plataforma de Firma Digital Remota (decisiones 5 y 19). Con firma
  electrónica firma apretando un botón (decisión 12).
- **RF-17**: El firmante puede rechazar el pedido, escribiendo el motivo.
- **RF-18**: Con el orden «uno después del otro», cada firmante recibe el pedido cuando firma
  el anterior.

**Cómo termina**

- **RF-19**: Un pedido está en uno de estos estados: Borrador, Esperando a otros, Esperando
  mi acción (cuando le toca firmar al remitente), Completado, Rechazado, Vencido o Cancelado.
- **RF-20**: Si un firmante rechaza o el pedido vence, el pedido se cancela, nadie más lo
  puede firmar, se avisa al remitente y se le ofrece reenviarlo. Reenviar arma un pedido
  nuevo con el mismo documento, destinatarios y campos, que se puede cambiar antes de enviar
  (decisión 17).
- **RF-21**: El remitente puede cancelar un pedido que espera firmas. Se avisa a los firmantes
  que ya lo habían recibido.
- **RF-22**: Cuando firma el último firmante, el pedido pasa a Completado y el remitente y
  todos los destinatarios reciben el documento firmado y la constancia.

**La prueba**

- **RF-23**: Al completarse, se genera una constancia con, por cada firmante: nombre, correo,
  forma de firma, forma de identidad usada y su resultado, fecha y hora de cada evento,
  dirección IP y dispositivo; y la huella del documento original y del firmado (decisión 23).
- **RF-24**: Cada evento del pedido (creado, enviado, entregado, visto, identidad comprobada,
  firmado, rechazado, recordatorio, vencido, cancelado, descargado) queda registrado con
  quién, qué y cuándo. El registro no se puede borrar ni cambiar.
- **RF-25**: El documento firmado lleva la huella que permite comprobar que no cambió después
  de firmarse.

### Non-Functional Requirements

- **RNF-01**: Todo el recorrido del remitente y del firmante se usa completo en el celular y
  en la computadora (constitución, principio III).
- **RNF-02**: Solo el remitente, los miembros del estudio con permiso y los destinatarios del
  pedido pueden ver el documento: está amparado por el secreto profesional (constitución,
  principio VI). Quién del estudio ve qué se define en la capacidad 007.
- **RNF-03**: El enlace de un firmante no se puede adivinar y deja de servir cuando el pedido
  termina, se cancela o vence.
- **RNF-04**: Los textos que ve el firmante están en castellano, con voseo, y no suponen que
  sabe de derecho.

### Reglas jurídicas a verificar

Lo que sigue son decisiones de Carlos que necesitan su norma citada antes de ser reglas
(constitución, principio II). Las fuentes oficiales (infoleg.gob.ar, argentina.gob.ar,
boletinoficial.gob.ar, saij.gob.ar) no se pudieron consultar desde la sesión del 2026-10-15.

- La firma digital, con un certificado de un certificador licenciado, equivale a la firma
  de puño y letra: ley 25.506, arts. 2 y 3, y Código Civil y Comercial, art. 288. **A
  verificar.**
- La firma electrónica vale como prueba, pero si se la desconoce, quien la invoca tiene que
  probar que es válida: ley 25.506, art. 5. **A verificar.**
- La Plataforma de Firma Digital Remota y los certificados que emite: decreto 182/2019 y
  sus normas complementarias. **A verificar.**
- Qué tiene que tener la constancia para servir de prueba en un juicio, y cuánto tiempo se
  guarda: sin norma identificada; es una pregunta abierta.
- [NEEDS CLARIFICATION: verificar en las fuentes oficiales las normas de esta sección antes
  de aprobar la especificación]
- [NEEDS CLARIFICATION: las preguntas de «001 · Pedido de firma» en
  [preguntas-abiertas.md](../preguntas-abiertas.md)]

### Key Entities *(include if feature involves data)*

- **Pedido de firma**: el documento, el remitente, el estudio, el estado, el orden de firma,
  el vencimiento, los recordatorios, el mensaje y, si es un reenvío, el pedido del que salió.
- **Documento**: el archivo original, el PDF que se firma, su huella, sus páginas y, al
  terminar, el PDF firmado y su huella.
- **Destinatario**: nombre, correo, teléfono, si firma o recibe copia, su lugar en el orden,
  su color, el canal, la forma de identidad y su estado (enviado, visto, firmado, rechazado).
- **Campo**: a qué firmante pertenece, su tipo, su página y su lugar, si es obligatorio y su
  valor una vez completado.
- **Firma**: quién firmó, cuándo, si fue digital o electrónica, con qué certificado o con qué
  forma de identidad.
- **Evento**: el pedido, quién, qué pasó, cuándo, desde qué dirección IP y dispositivo.
- **Constancia**: el pedido, los eventos que resume, su fecha y su huella.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Un remitente que nunca usó el producto prepara y envía un pedido de un PDF con
  dos firmantes en menos de 3 minutos.
- **SC-002**: Un firmante sin cuenta firma con firma electrónica desde el celular en menos de
  2 minutos desde que abre el mensaje.
- **SC-003**: El 100 % de los pedidos completados tienen su constancia, y la huella de cada
  documento firmado coincide con la de la constancia.
- **SC-004**: Ningún pedido rechazado, vencido o cancelado se puede firmar.

## Assumptions

Supuestos para lo que Carlos no definió. Al aprobar la especificación, Carlos los aprueba o
los cambia.

- Los tipos de campo son: firma, iniciales, nombre, fecha de firma y texto libre, como en
  DocuSign.
- Con firma electrónica, el firmante, además de apretar el botón, ve su nombre escrito como
  firma en el documento; no la dibuja.
- Los recordatorios automáticos salen cada tres días, y el remitente puede cambiarlo o
  apagarlos en cada pedido.
- El remitente recibe un aviso cuando se completa, se rechaza o vence un pedido; no uno por
  cada firma.
- El documento firmado y la constancia llegan como enlace de descarga en el mensaje, no como
  adjunto.
- Un firmante no puede delegar la firma en otra persona.
- El remitente con cuenta pertenece a un estudio; las cuentas, el ingreso y los permisos
  están en la capacidad 007.
