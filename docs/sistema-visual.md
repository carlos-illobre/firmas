# Sistema visual

Los colores, la tipografía y los componentes que Carlos aprobó. Lo decide la primera
maqueta aprobada (paso 2); cada decisión nueva se suma acá con sus valores, para que la
pantalla siguiente no vuelva a decidirla.

Lo único decidido hoy es la preferencia de Carlos para todos sus proyectos: estilo panel de
administración, con barra lateral oscura, tarjetas y tablas con los estados en pastillas.

Los estilos salen de la maqueta de Carlos en Lovable, y las pantallas que ahí faltan, del
diseño en Figma con los estilos de la de Lovable (decisión 10 de
[decisiones-de-negocio.md](decisiones-de-negocio.md)). Los valores se escriben acá cuando
se puedan leer de la maqueta.

## Lo que sale de la maqueta de Lovable

Leído de la maqueta el 2026-10-15, por ingeniería inversa: los valores son los de su hoja de
estilos. La maqueta se llama «LexFirma»; el nombre del producto todavía no está decidido.

### Colores

En OKLCH, como los define la maqueta.

| Uso | Valor |
|---|---|
| Fondo de la página | `oklch(98.2% .004 95)`, un blanco apenas cálido |
| Texto | `oklch(21% .03 264)` |
| Tarjetas | `oklch(100% 0 0)` |
| Principal: botones, enlaces, foco | `oklch(52% .13 256)`, azul; el texto encima, `oklch(98.5% .005 250)` |
| Barra lateral | `oklch(24% .055 268)`, azul marino; texto `oklch(96% .01 250)`, texto apagado `oklch(72% .03 260)` |
| Ítem activo de la barra lateral | el azul principal al 20 % sobre el marino |
| Secundario y apagado | `oklch(95.5% .008 250)`; texto apagado `oklch(52% .03 260)` |
| Acento | `oklch(94% .02 256)`; su texto `oklch(35% .09 256)` |
| Bordes | `oklch(91.5% .01 255)`; campos `oklch(90% .012 255)` |
| Peligro | `oklch(55% .2 27)` |
| Éxito | `oklch(55% .12 155)`; fondo suave `oklch(94% .04 155)` |
| Aviso | `oklch(62% .12 70)`; texto `oklch(30% .06 70)`; fondo suave `oklch(95% .05 85)` |
| Información, fondo suave | `oklch(94% .025 256)` |
| Firmantes 1, 2 y 3 | `oklch(52% .13 256)` azul, `oklch(60% .14 330)` magenta, `oklch(60% .13 160)` verde |

Cada firmante tiene su color, y con ese color se marcan sus campos en el documento y su
punto en la lista de participantes.

### Tipografía

Inter. Título de página 24 px, peso 600. Título de tarjeta 16 px, peso 600. Texto 14 px;
secundario 12 px. Botones 14 px, peso 500.

### Formas

- Radio base de 10 px (`.625rem`) en botones, tarjetas e ítems de menú.
- Sombra de las tarjetas y botones apenas marcada: `0 1px 3px` y `0 1px 2px -1px`, negro al
  10 %.
- Estados en pastillas redondas con fondo suave y texto del mismo tono: azul «Esperando a
  otros», amarillo «Esperando mi acción», verde «Completado», rojo «Vencido».

### Estructura

- Barra lateral fija de 256 px, azul marino: la marca y el estudio arriba, el botón
  «Nuevo documento», el menú con íconos de línea y el usuario abajo.
- Barra superior con el buscador a la izquierda y «Vista del firmante» a la derecha, sobre el
  fondo de la página al 95 %.
- Contenido con márgenes de 32 px: título, subtítulo y el botón principal a la derecha;
  debajo, tarjetas de resumen y tarjetas con listas.

## Qué pantalla sale de dónde

La maqueta de Lovable tiene Inicio, Documentos, el detalle de un documento y Nuevo
documento, en cuatro pasos: documento, destinatarios, campos, y revisar y enviar. Plantillas,
Contactos y clientes, Tareas y vencimientos, Informes y actividad, Configuración y la Vista
del firmante dan 404 ahí: salen del diseño de Figma, con los estilos de arriba.
