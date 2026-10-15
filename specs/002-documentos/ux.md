# Requerimientos de interfaz: inicio y documentos

Qué tiene que poder hacer cada rol, qué ve y en qué orden, sin atarse a un diseño. El diseño
concreto está en [maquetas/](maquetas/). Estilo: [sistema visual](../../docs/sistema-visual.md).

**Maquetas aprobadas por Carlos el 2026-10-15** (decisiones 40 y 41): `inicio`, `documentos`, `documento` y `editor`.

## Inicio

- Saludo con nombre y fecha, y una línea con lo pendiente. Cuatro números: esperando mi
  acción, esperando firma de otros, completados este mes, demorados o vencidos.
- «Requiere tu atención» primero, con la acción de cada uno (firmar, revisar, reenviar, ver);
  después documentos recientes, próximos vencimientos y actividad reciente.
- Estados: estudio sin documentos (invita a «Nuevo documento») y nada pendiente.

## Documentos

- Filtros por estado con su cantidad, buscador por nombre y filtro por cliente. De cada
  documento: nombre, etiquetas, cliente o «Sin cliente», estado, última actividad, próxima
  acción, responsable y la acción directa (recordar, firmar).
- En el celular, cada documento muestra nombre, cliente y estado; el resto se ve al abrirlo.
- Estados: filtro sin resultados (con «Sacar filtros») y archivados vacío.

## Detalle de un documento

- Nombre y estado, cliente, responsable y etiquetas; acciones: recordar, abrir el editor y
  descargar. La vista previa paginada, la línea de tiempo con acceso a la constancia, los
  participantes con su orden, color, canal, identidad y estado, la próxima acción con su
  fecha, y archivar o cancelar el pedido.
- Estados: rechazado (con el motivo y «Reenviar»), vencido (con «Reenviar»), completado (con
  «Descargar») y la confirmación de cancelar.

## Editor de la firma

- Dice qué no se puede cambiar porque ya firmaron, y a quién se le va a reenviar. Se mueven
  los campos y se cambian canal, identidad, campos y vencimiento de quien no firmó.

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
