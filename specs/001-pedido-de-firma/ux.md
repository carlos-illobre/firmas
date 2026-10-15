# Requerimientos de interfaz: pedido de firma

Qué tiene que poder hacer cada rol, qué ve y en qué orden, sin atarse a un diseño. El diseño
concreto está en [maquetas/](maquetas/). Estilo: [sistema visual](../../docs/sistema-visual.md).

**Maquetas aprobadas por Carlos el 2026-10-15** (decisiones 40 y 41): `nuevo-1-documento`, `nuevo-2-destinatarios`, `nuevo-3-campos`, `nuevo-4-revisar`, `revision`, `mensajes`, `firmante-identidad`, `firmante`, `firmante-firmar`, `firmante-estados` y `constancia`.

## Preparar y enviar (solicitante)

- El recorrido tiene cuatro pasos a la vista, con el actual marcado: documento,
  destinatarios, campos, y revisar y enviar. Se puede volver a un paso anterior sin perder lo
  cargado; salir guarda un borrador.
- **Documento**: primero, cómo empezar (subir un archivo, usar una plantilla, crear desde
  cero). Al subir un Word se avisa que se convirtió a PDF y se ofrece verlo. Se ve el nombre
  del documento, editable, y se pueden elegir cliente y etiquetas, los dos opcionales.
- **Destinatarios**: por cada uno, nombre, correo, rol (firmante o recibe copia), canal
  (correo o WhatsApp), celular cuando hace falta, y, si firma, una o dos formas de identidad.
  El orden de firma se activa con un interruptor y se ve como un número por destinatario.
  Escribir un nombre sugiere contactos guardados. La revisión se pide con una casilla y la
  elección de los revisores.
- **Campos**: el documento a la izquierda y, al lado, a qué firmante se le ubican campos, los
  tipos de campo y el campo elegido, con «obligatorio». Cada firmante tiene su color, y sus
  campos se ven con ese color. En el celular se toca el campo y después el lugar.
- **Revisar y enviar**: resumen de documento, destinatarios con orden, canal e identidad, y
  revisión; vencimiento, recordatorios y mensaje. El botón dice lo que va a pasar: «Enviar a
  firmar» o «Enviar a revisión».
- **Estados**: convirtiendo, archivo de más de 50 MB, Word que no se convierte, contrato que
  exige escritura pública (con «Seguir igual» y «Cambiar el documento»), correo o celular
  inválidos, más de dos formas de identidad, firmante sin campo de firma, enviado y en
  revisión.

## Revisar (revisor)

- El documento y, al lado, firmantes, vencimiento y los otros revisores. «Aprobar» y
  «Devolver con comentario»; para devolver, el comentario es obligatorio.
- El solicitante ve la devolución con el comentario y puede editar y reenviar a revisión.

## Firmar (firmante)

- **El mensaje** dice quién pide la firma, de qué estudio, qué documento, hasta cuándo, el
  mensaje del solicitante, y un solo botón: «Revisar y firmar». Aclara que no hace falta
  cuenta. Los recordatorios y el aviso de que terminó usan el mismo canal.
- **Identidad**: antes de ver el documento, un paso por cada forma pedida, con «Paso 1 de 2».
  Código: se dice a qué celular terminado en qué números se mandó, y se puede pedir otro.
  DNI: frente y dorso, diciendo para qué se usan.
- **Documento y panel de firma**: el documento entero y un panel con lo hecho, lo que falta y
  el próximo paso, con un solo botón principal que lleva al próximo campo pendiente. La
  elección entre firma digital y electrónica dice en una línea qué vale cada una. En el
  celular, el panel es una hoja abajo con el progreso y el botón.
- **Firma digital**: elegir Firma Digital Remota, token o archivo del certificado, con una
  línea sobre cada uno; el archivo no se guarda.
- **Firma electrónica**: se ve cómo va a quedar la firma (el nombre escrito) y qué queda
  registrado antes de apretar «Firmar».
- **Rechazar**: pide el motivo y avisa que no se puede deshacer.
- **Estados**: código incorrecto, demasiados intentos (15 minutos), foto ilegible,
  certificado vencido (con la opción de firmar con firma electrónica), firmado, rechazado,
  vencido, cancelado, ya firmado, otro lo rechazó y enlace que no existe.
- La barra superior dice «Conexión segura» y no tiene menú: el firmante no tiene cuenta.

## Constancia y verificación

- La constancia muestra número, fecha y hora de Buenos Aires, documento, solicitante,
  estado, huellas del original y del firmado, y por firmante: contacto, forma de firma,
  identidad con su resultado y cada evento con fecha, hora, IP y dispositivo. Cierra con qué
  vale cada firma, en palabras simples y con su norma.
- La verificación no pide cuenta: se sube el PDF y dice si coincide con lo firmado o si
  cambió.

## Chequeo contra la constitución

- Principio III, celular y computadora: cada pantalla tiene su maqueta en las dos, sin
  desbordes, y se usa completa en las dos.
- Principio IV, el diseño aprobado es regla: las maquetas de `maquetas/` son las aprobadas;
  cambiarlas es cambiar un requerimiento.
- Principio VI, seguro por defecto: los datos de ejemplo de las maquetas son inventados.
- Principio VIII, castellano: los textos van con voseo y con las palabras del oficio
  (solicitante, firmante, pedido de firma, constancia).
- Teclado: en la computadora, todo se hace con el teclado, con el foco visible y en el orden
  en que se lee la pantalla.
