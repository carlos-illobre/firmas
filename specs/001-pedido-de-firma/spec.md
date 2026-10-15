# Feature Specification: Pedido de firma

**Feature Branch**: `001-pedido-de-firma`

**Created**: 2026-10-15

**Status**: Aprobada (2026-10-15)

**Maquetas**: Aprobadas (2026-10-15, decisiones 40 y 41); ver [ux.md](ux.md)

**Input**: Las decisiones de Carlos del 2026-10-15 (5, 7, 8, 11 a 17, 19 a 29 y 36 de
[docs/decisiones-de-negocio.md](../../docs/decisiones-de-negocio.md)): un abogado prepara un
documento, carga a los firmantes, elige cómo firma y se identifica cada uno, y lo envía; cada
firmante firma desde el correo con firma electrónica; al terminar
queda el documento firmado y una constancia de lo que pasó.

<!-- Cada escenario de aceptación lleva un número que no se repite en este archivo:
     «1. **E01** **Given** …». El paso de QA agrega los de error, los de borde y los que
     salen de la sección «Seguridad» del plan. Cada prueba nombra su escenario (001-E01). -->

## Primera y segunda versión

Carlos decidió el 2026-10-15 que la primera versión no use proveedores pagos (decisión 42).
Lo que dice **(segunda versión)** está especificado y aprobado, pero no entra en la primera:

| Primera versión | Segunda versión |
|---|---|
| Firma electrónica | Firma digital: archivo, token y Firma Digital Remota |
| Pedido por correo | Pedido por WhatsApp |
| Identidad: correo, código por correo, foto del DNI guardada sin validar | Código por SMS o WhatsApp, validación contra RENAPER |

## Palabras

- **Solicitante**: el abogado, o cualquier miembro del estudio con cuenta, que prepara y envía
  el pedido: quien requiere la firma. Es uno de los dos roles del producto (decisión 36).
- **Pedido de firma**: un documento con sus destinatarios, el orden, los campos, el
  vencimiento y los recordatorios. Es lo que en DocuSign se llama «sobre».
- **Destinatario**: cada persona del pedido. Es **firmante** (el otro rol del producto) o
  **recibe copia**. No necesita cuenta (decisión 12).
- **Revisor**: un miembro del estudio que aprueba el pedido antes de que salga, si el
  solicitante pidió revisión (decisión 28).
- **Firma digital**: la que se hace con un certificado de firma digital del firmante.
- **Firma electrónica**: la que se hace sin certificado, apretando un botón, después de
  comprobar la identidad del firmante como eligió el solicitante.
- **Constancia**: el documento que se genera al terminar, con lo que pasó en el pedido.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Preparar y enviar un pedido de firma (Priority: P1)

El solicitante sube un PDF o un Word, carga a los firmantes y a quienes reciben copia, elige
el orden de firma, ubica los campos de cada firmante en el documento, elige el vencimiento,
y lo envía. El recorrido tiene cuatro pasos: documento, destinatarios, campos, y revisar y
enviar.

**Why this priority**: sin pedido no hay nada que firmar; es el corazón del producto.

**Independent Test**: preparar un pedido con un PDF y dos firmantes, enviarlo y comprobar
que el primer firmante recibe el correo.

**Acceptance Scenarios**:

1. **E01** **Given** un solicitante con cuenta, **When** sube un PDF, carga dos firmantes con
   nombre y correo, ubica un campo de firma para cada uno, elige un vencimiento y envía,
   **Then** el pedido queda «Esperando a otros» y los firmantes reciben el pedido por el
   canal elegido.
2. **E02** **Given** un solicitante que sube un Word, **When** pasa al paso de destinatarios,
   **Then** el documento ya está convertido a PDF, el solicitante ve ese PDF y lo que se envía
   y se firma es ese PDF (decisión 14).
3. **E03** **Given** un pedido con orden «uno después del otro», **When** se envía, **Then**
   solo el primer firmante recibe el pedido; cada uno recibe el suyo cuando firma el
   anterior (decisión 15).
4. **E04** **Given** un pedido con orden «todos a la vez», **When** se envía, **Then** todos
   los firmantes reciben el pedido al mismo tiempo.
5. **E05** **Given** un firmante sin campo de firma, **When** el solicitante quiere enviar,
   **Then** no puede, y se le dice qué firmante no tiene campo.
6. **E06** **Given** un pedido a medio preparar, **When** el solicitante sale del recorrido,
   **Then** queda guardado como «Borrador» y lo puede retomar.
7. **E07** **Given** un destinatario marcado «recibe copia», **When** se completa el pedido,
   **Then** recibe el documento firmado y la constancia, sin haber tenido que firmar.
8. **E23** **Given** un documento que es una compraventa de un inmueble, **When** el
   solicitante lo sube, **Then** ve un cartel que explica que ese contrato exige escritura
   pública y elige si sigue o no.
9. **E24** **Given** un archivo de más de 50 MB, **When** el solicitante lo sube, **Then** no
   se acepta y se le dice el máximo.
10. **E25** **Given** un pedido con «Pedir revisión» y dos revisores, **When** los dos
    aprueban, **Then** el pedido sale; **When** uno lo devuelve con un comentario, **Then**
    vuelve al solicitante como borrador con ese comentario.

---

### User Story 2 - Firmar desde el correo (Priority: P1)

El firmante recibe el pedido, aprieta el botón del mensaje y llega al documento sin crear
una cuenta. Si el solicitante eligió una forma de comprobar su identidad, la pasa primero. Lee
el documento, completa sus campos y firma con firma electrónica, apretando un botón
(decisiones 12 y 42). La firma digital es de la segunda versión.

**Why this priority**: es la otra mitad del corazón del producto, y la usa gente que no es
abogada, a menudo desde el celular.

**Independent Test**: con un pedido enviado, abrir el enlace del firmante, comprobar su
identidad, firmar con firma electrónica y ver que el pedido avanza.

**Acceptance Scenarios**:

1. **E08** **Given** un firmante que recibió el pedido, **When** aprieta el botón del
   mensaje, **Then** ve el documento completo, sin crear cuenta, con sus campos marcados y
   la opción de descargar una copia.
2. **E09** **Given** un firmante para quien el solicitante eligió código por correo, **When**
   abre el pedido, **Then** tiene que ingresar el código que le llegó al correo antes de ver
   el documento.
3. **E26** **Given** un firmante para quien el solicitante eligió código por correo y foto del
   DNI, **When** abre el pedido, **Then** tiene que pasar las dos antes de ver el documento, y
   las fotos quedan en la constancia.
4. **E10** **Given** un firmante, **When** completa sus campos y aprieta «Firmar», **Then**
   firma con firma electrónica y el pedido registra la firma con la forma
   de identidad que usó.
5. **E11** *(segunda versión)* **Given** un firmante con certificado de firma digital,
   **When** elige firmar con él, **Then** puede hacerlo subiendo el archivo del certificado,
   con su token o con la Plataforma de Firma Digital Remota, y la firma queda hecha con ese
   certificado.
6. **E12** **Given** un firmante con campos obligatorios sin completar, **When** quiere
   firmar, **Then** no puede, y el producto lo lleva al próximo campo pendiente.
7. **E13** **Given** el último firmante, **When** firma, **Then** el pedido pasa a
   «Completado», y todos los destinatarios y el solicitante reciben el documento firmado y la
   constancia.

---

### User Story 3 - Rechazo, vencimiento, recordatorios y cancelación (Priority: P2)

Si un firmante rechaza firmar o el pedido vence, el pedido se cancela, se avisa al solicitante
y se le ofrece reenviarlo (decisión 17). Mientras tanto, el producto manda recordatorios
automáticos (decisión 22), el solicitante puede mandar uno cuando quiera, y puede cancelar el
pedido.

**Why this priority**: sin esto un pedido puede quedar abierto para siempre, pero el
recorrido principal funciona sin ello.

**Independent Test**: enviar un pedido, rechazarlo como firmante y comprobar que el
solicitante recibe el aviso y puede reenviarlo.

**Acceptance Scenarios**:

1. **E14** **Given** un firmante que abrió el pedido, **When** lo rechaza, **Then** tiene
   que escribir el motivo, el pedido pasa a «Rechazado», nadie más puede firmarlo, y el
   solicitante recibe un aviso con el motivo y la opción de reenviarlo.
2. **E15** **Given** un pedido sin completar, **When** llega su vencimiento, **Then** pasa
   a «Vencido», nadie puede firmarlo, y el solicitante recibe un aviso con la opción de
   reenviarlo.
3. **E16** **Given** un pedido rechazado o vencido, **When** el solicitante lo reenvía,
   **Then** se arma un pedido nuevo con el mismo documento, destinatarios y campos, que puede
   cambiar antes de enviar; el anterior queda como estaba.
4. **E17** **Given** un pedido esperando firmas, **When** pasa el tiempo de un recordatorio,
   **Then** cada firmante que todavía no firmó y ya recibió el pedido recibe un recordatorio
   por su canal.
5. **E18** **Given** un pedido esperando firmas, **When** el solicitante aprieta «Recordar»,
   **Then** se manda un recordatorio a los firmantes que todavía no firmaron.
6. **E19** **Given** un pedido esperando firmas, **When** el solicitante lo cancela, **Then**
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
- Un firmante figura dos veces, o el solicitante es también firmante.
- El correo de un firmante rebota: se avisa al solicitante.
- Un firmante abre el enlace de un pedido rechazado, vencido, cancelado o que ya firmó.
- *(Segunda versión)* El certificado del firmante está vencido o revocado.
- Un firmante quiere delegar la firma en otra persona.
- El documento final y la constancia tienen que poder verificarse sin el producto.

## Requirements *(mandatory)*

### Functional Requirements

**El documento**

- **RF-01**: El solicitante empieza un pedido de tres formas: subiendo un archivo, usando una
  plantilla del estudio o creando el documento desde cero (decisión 11). Las plantillas y la
  redacción desde cero están en la capacidad 003.
- **RF-02**: Se pueden subir archivos PDF y Word. Un Word se convierte a PDF antes de seguir;
  el solicitante ve el PDF convertido, y lo que se envía y se firma es ese PDF (decisión 14).
  Cada archivo pesa 50 MB como mucho, como en DocuSign (decisión 25); no hay un máximo de
  páginas.
- **RF-02a**: Si el documento es de los que la ley obliga a hacer por escritura pública (por
  ejemplo, los que adquieren, modifican o extinguen derechos reales sobre inmuebles), aparece
  un cartel que explica que el producto no los puede otorgar, y el solicitante decide si
  sigue (decisión 24). El producto lo detecta por el texto del documento (decisión 41). *Código Civil y Comercial, arts. 285 y 1017.*

**Los destinatarios**

- **RF-03**: El solicitante carga cada destinatario con nombre y apellido y correo; y, en la
  segunda versión, si el canal o la forma de identidad lo piden, teléfono celular. Marca si es firmante o recibe
  copia. Puede agregarse a sí mismo como firmante.
- **RF-04**: El solicitante elige el orden de firma: uno después del otro, en el orden que
  arma, o todos a la vez (decisión 15).
- **RF-05**: Para cada firmante, el solicitante elige una o dos formas de comprobar su
  identidad: correo, código por correo o foto del DNI (decisiones 13, 20, 27 y 42). Con dos,
  el firmante pasa las dos. La foto del DNI, frente y dorso, se guarda en la constancia sin
  validarla contra nada. *(Segunda versión)* También código por SMS, código por WhatsApp y
  validación contra RENAPER.
- **RF-06**: Para cada destinatario, el solicitante elige el canal por el que le llega el
  pedido: correo (decisiones 21, 26 y 42). *(Segunda versión)* También WhatsApp.

**Los campos**

- **RF-07**: El solicitante ubica sobre las páginas del documento los campos de cada firmante.
  Cada firmante tiene un color propio, y sus campos se ven con ese color
  ([sistema visual](../../docs/sistema-visual.md)).
- **RF-08**: Cada firmante tiene al menos un campo de firma. Un campo puede ser obligatorio u
  opcional.

**El envío**

- **RF-09**: Antes de enviar, el solicitante ve un resumen: el documento, los destinatarios con
  su orden, canal e identidad, y los campos. Puede escribir un mensaje para los destinatarios.
- **RF-09a**: Antes de enviar, el solicitante puede tildar «Pedir revisión» y elegir a uno o
  más miembros del estudio como revisores (decisión 28). Cada revisor aprueba o devuelve el
  pedido con un comentario, que es obligatorio para devolverlo (decisión 41). Cuando todos aprueban, el pedido sale solo; si uno lo devuelve,
  vuelve al solicitante como borrador, con el comentario.
- **RF-10**: El solicitante elige cuándo vence el pedido (decisión 22). Por defecto vence a los
  14 días, salvo que el estudio fije otro plazo (decisión 41).
- **RF-11**: El producto manda recordatorios automáticos a los firmantes que todavía no
  firmaron (decisión 22). El solicitante puede, además, mandar un recordatorio cuando quiera.
- **RF-12**: Un pedido a medio preparar queda guardado como borrador, y el solicitante lo puede
  retomar o borrar.

**La firma**

- **RF-13**: Cada firmante recibe un mensaje con un botón que lo lleva a su pedido, sin
  crear cuenta. El enlace es personal: lleva solo a lo que le toca a ese firmante (decisión
  12).
- **RF-14**: Si el solicitante eligió una forma de identidad, el firmante la pasa antes de ver
  el documento. Un código de identidad admite 3 intentos; después, el acceso al pedido se
  bloquea 15 minutos (decisión 41).
- **RF-15**: El firmante ve el documento completo, puede descargar una copia, y el producto lo
  lleva de un campo pendiente al siguiente.
- **RF-16**: El firmante firma con firma electrónica apretando un botón (decisiones 12 y 42).
  *(Segunda versión)* También puede elegir firma digital, con su certificado de una de tres
  formas: subiendo el archivo del certificado, con su token, o con la Plataforma de Firma
  Digital Remota (decisiones 5 y 19).
- **RF-17**: El firmante puede rechazar el pedido, escribiendo el motivo.
- **RF-18**: Con el orden «uno después del otro», cada firmante recibe el pedido cuando firma
  el anterior.

**Cómo termina**

- **RF-19**: Un pedido está en uno de estos estados: Borrador, En revisión, Esperando a otros,
  Esperando mi acción (cuando le toca firmar o revisar a quien lo mira), Completado,
  Rechazado, Vencido o Cancelado.
- **RF-20**: Si un firmante rechaza o el pedido vence, el pedido se cancela, nadie más lo
  puede firmar, se avisa al solicitante y se le ofrece reenviarlo. Reenviar arma un pedido
  nuevo con el mismo documento, destinatarios y campos, que se puede cambiar antes de enviar
  (decisión 17).
- **RF-21**: El solicitante puede cancelar un pedido que espera firmas, después de confirmarlo
  (decisión 41). Se avisa a los firmantes
  que ya lo habían recibido.
- **RF-22**: Cuando firma el último firmante, el pedido pasa a Completado y el solicitante y
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

- **RNF-01**: Todo el recorrido del solicitante y del firmante se usa completo en el celular y
  en la computadora (constitución, principio III).
- **RNF-02**: Solo el solicitante, los miembros del estudio con permiso y los destinatarios del
  pedido pueden ver el documento: está amparado por el secreto profesional (constitución,
  principio VI). Quién del estudio ve qué se define en la capacidad 007.
- **RNF-03**: El enlace de un firmante no se puede adivinar y deja de servir cuando el pedido
  termina, se cancela o vence.
- **RNF-04**: Los textos que ve el firmante están en castellano, con voseo, y no suponen que
  sabe de derecho.

### Reglas jurídicas

Verificadas el 2026-10-15 en argentina.gob.ar: la ley 25.506 en su texto actualizado, el
Código Civil y Comercial (ley 26.994) en su texto original y el decreto 182/2019.

- **RF-26** *(segunda versión)*: Una firma hecha con certificado vale como firma digital solo si el certificado
  estaba vigente al firmar, la firma se verifica con los datos del certificado y el
  certificado lo emitió un certificador licenciado. Si falla alguna de las tres, el producto
  no la presenta como firma digital. *Ley 25.506, arts. 9, 14 y 15.*
- **RF-27** *(segunda versión)*: Una firma digital válida satisface la exigencia de firma de puño y letra, y se
  presume, salvo prueba en contrario, que es del titular del certificado y que el documento
  no cambió desde que se firmó. *Ley 25.506, arts. 3, 7 y 8; Código Civil y Comercial,
  art. 288.*
- **RF-28**: La firma electrónica es la que no reúne los requisitos de la firma digital. Si
  quien firmó la desconoce, quien la invoca tiene que probar que es válida; por eso la
  constancia junta la prueba de quién firmó y de que el documento no cambió. *Ley 25.506,
  art. 5; Código Civil y Comercial, arts. 314 y 319, que dejan al juez ponderar la
  confiabilidad de los soportes y de los procedimientos técnicos.*
- **RF-29**: El producto le dice al solicitante y al firmante, en palabras simples, qué vale la
  firma electrónica: vale como prueba, que hay que sostener con la constancia si se la
  desconoce. *Ley 25.506, art. 5.* *(Segunda versión)* También qué vale la digital: equivale
  a la de puño y letra. *Ley 25.506, art. 3.*
- **RF-30** *(segunda versión)*: La firma digital remota es una firma digital: el certificado lo guarda la
  Plataforma de Firma Digital Remota, creada por el decreto 892/2017, y su uso puede tener
  aranceles. *Decreto 182/2019, considerandos y art. 25 de su anexo.*

La ley 25.506 ya no excluye ningún acto (su art. 4 fue derogado por la ley 27.446), pero los
contratos que la ley obliga a hacer por escritura pública, como los de derechos reales sobre
inmuebles, no se pueden otorgar con este producto. *Código Civil y Comercial, arts. 285, 299
y 1017.* Por eso, el cartel de RF-02a.

Qué tiene que tener la constancia más allá de lo anterior, y cuánto tiempo se guarda, no
tiene una norma identificada: es una pregunta abierta.

### Key Entities *(include if feature involves data)*

- **Pedido de firma**: el documento, el solicitante, el estudio, el estado, el orden de firma,
  el vencimiento, los recordatorios, el mensaje y, si es un reenvío, el pedido del que salió.
- **Documento**: el archivo original, el PDF que se firma, su huella, sus páginas y, al
  terminar, el PDF firmado y su huella.
- **Destinatario**: nombre, correo, teléfono, si firma o recibe copia, su lugar en el orden,
  su color, el canal, la forma de identidad y su estado (enviado, visto, firmado, rechazado).
- **Campo**: a qué firmante pertenece, su tipo, su página y su lugar, si es obligatorio y su
  valor una vez completado.
- **Firma**: quién firmó, cuándo, si fue electrónica o (en la segunda versión) digital, con qué certificado o con qué
  forma de identidad.
- **Evento**: el pedido, quién, qué pasó, cuándo, desde qué dirección IP y dispositivo.
- **Constancia**: el pedido, los eventos que resume, su fecha y su huella.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: Un solicitante que nunca usó el producto prepara y envía un pedido de un PDF con
  dos firmantes en menos de 3 minutos.
- **SC-002**: Un firmante sin cuenta firma con firma electrónica desde el celular en menos de
  2 minutos desde que abre el mensaje.
- **SC-003**: El 100 % de los pedidos completados tienen su constancia, y la huella de cada
  documento firmado coincide con la de la constancia.
- **SC-004**: Ningún pedido rechazado, vencido o cancelado se puede firmar.

## Assumptions

Carlos aprobó estos supuestos el 2026-10-15 (decisiones 29 y 39).

- Los tipos de campo son: firma, iniciales, nombre, fecha de firma y texto libre, como en
  DocuSign.
- Con firma electrónica, el firmante, además de apretar el botón, ve su nombre escrito como
  firma en el documento; no la dibuja.
- Los recordatorios automáticos salen cada tres días, y el solicitante puede cambiarlo o
  apagarlos en cada pedido.
- El solicitante recibe un aviso cuando se completa, se rechaza o vence un pedido; no uno por
  cada firma.
- El documento firmado y la constancia llegan como enlace de descarga en el mensaje, no como
  adjunto.
- Un firmante no puede delegar la firma en otra persona.
- El solicitante con cuenta pertenece a un estudio; las cuentas y el ingreso están en la
  capacidad 007.
- Los documentos firmados y las constancias se guardan mientras exista la
  cuenta del estudio, y el estudio los puede descargar en cualquier momento. Si la ley exige
  un plazo, es la pregunta abierta sobre conservación.
