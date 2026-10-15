# Requerimientos de interfaz: clientes y contactos

Qué tiene que poder hacer cada rol, qué ve y en qué orden, sin atarse a un diseño. El diseño
concreto está en [maquetas/](maquetas/). Estilo: [sistema visual](../../docs/sistema-visual.md).

**Maquetas aprobadas por Carlos el 2026-10-15** (decisiones 40 y 41): `contactos`.

## Contactos

- Buscador por nombre, correo o CUIT y filtro por personas u organizaciones. De cada uno:
  nombre, si es persona u organización, la organización de la persona, cuántos documentos
  tiene y lo pendiente, resaltado.
- Nuevo contacto: persona (nombre, apellido, correo y, opcionales, celular, DNI, CUIT o CUIL y
  organización) u organización (razón social y, opcionales, CUIT, correo y teléfono). El DNI
  dice para qué sirve.
- Estados: sin contactos y correo repetido (ofrece abrir el existente).

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
