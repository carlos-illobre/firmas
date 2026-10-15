# Decisiones de negocio

Lo que Carlos decidió sobre qué tiene que hacer el producto, por fecha. Es el par de los
[ADR](adr/README.md), que guardan las decisiones técnicas. Cada decisión está además en la
especificación que toca (`specs/`). Una decisión nueva se agrega acá con su fecha; las
anteriores no se reescriben: si una cambia, se agrega la nueva y se anota a cuál reemplaza.

Lo que todavía no está decidido está en
[specs/preguntas-abiertas.md](../specs/preguntas-abiertas.md).

## Decisiones del 2026-10-15

1. El proyecto es un producto como DocuSign, para el mercado argentino y con foco en
   abogados.
2. Se desarrolla con las mismas reglas de spec driven development que `ferre` y
   `cocinadas`.
3. El repositorio se llama `firmas` y es público.
4. Va en el primer grupo de prioridad del portafolio, con Ferretería y Minihotel.

## Decisiones del 2026-10-15, respuestas a las preguntas abiertas

5. **El valor de la firma.** Si el que firma tiene un certificado de firma digital, lo
   ingresa y firma con él. Si no lo tiene, firma con firma electrónica. El producto no es
   certificador: usa el certificado que ya tiene cada uno. Falta verificar qué normas rigen
   cada una (ley 25.506 y su decreto reglamentario) antes de escribirlo como regla.
6. **Quién paga.** Nadie, por ahora: no hace falta cobrar para empezar el desarrollo.
7. **Quiénes firman.** Hay una pantalla para cargar los datos de los firmantes, que no
   necesariamente son abogados.
8. **Qué documentos.** Cualquiera: el tipo no importa. El documento se adjunta como
   archivo.
9. **Fechas.** No hay fecha límite: la primera versión sale cuando esté.
10. **El estilo.** La idea es un clon de DocuSign, pero más lindo y más usable. Los estilos
    salen de la maqueta de Carlos en Lovable
    (<https://lovable.dev/preview/IH4hFkwJsosb9khZpHbXWAcIIZ8NlFs5>), por ingeniería
    inversa. Las pantallas que en esa maqueta dan 404 se completan con el diseño en Figma
    (<https://raid-score-17949864.figma.site>), pero con los estilos de la de Lovable.
11. **Cómo se empieza un documento.** De tres formas, como en la maqueta de Lovable:
    subiendo un archivo, usando una plantilla del estudio o creándolo desde cero en el
    producto. Amplía la decisión 8.
12. **Cómo firma quien no es abogado.** Como en DocuSign: recibe el documento por correo y
    aprieta un botón del correo. Ahí ingresa su certificado o, si no tiene, elige firma
    electrónica y firma apretando un botón. No necesita cuenta.
13. **Identidad en la firma electrónica.** Están disponibles todas las formas, para
    elegir: correo, código por SMS o WhatsApp, foto del DNI y validación contra RENAPER.
14. **Formatos.** Se puede subir PDF o Word. Un Word se convierte a PDF antes de mandarlo
    por correo.
15. **Orden de firma.** Lo elige quien envía: uno después del otro o todos a la vez.
16. **Cómo llega el pedido.** Se puede elegir el canal, además del correo de la
    decisión 12.
17. **Rechazo y vencimiento.** Si alguien rechaza firmar o el pedido vence, el pedido se
    cancela, se avisa a quien lo envió y se le ofrece reenviarlo.
18. **Lo mínimo de la primera versión.** Todas las pantallas de las maquetas: Inicio,
    Documentos, Nuevo documento, el detalle de un documento, Plantillas, Contactos,
    Tareas, Actividad, Configuración y la vista del firmante.
