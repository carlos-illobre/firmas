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
   ingresa y firma con él. Si no lo tiene, firma con firma electrónica. Responde la
   pregunta 1 y, en parte, la 2: el producto no es certificador, usa el certificado que
   ya tiene cada uno. Falta verificar qué normas rigen cada una (ley 25.506 y su decreto
   reglamentario) antes de escribirlo como regla.
6. **Quién paga.** Nadie, por ahora: no hace falta cobrar para empezar el desarrollo.
   Responde la pregunta 4.
7. **Quiénes firman.** Hay una pantalla para cargar los datos de los firmantes, que no
   necesariamente son abogados. Responde la pregunta 5, salvo si los que no son abogados
   necesitan cuenta.
8. **Qué documentos.** Cualquiera: el tipo no importa. El documento se adjunta como
   archivo. Responde la pregunta 6 y, en parte, la 12.
9. **Fechas.** No hay fecha límite: la primera versión sale cuando esté. Responde la
   primera mitad de la pregunta 20.
10. **El estilo.** La idea es un clon de DocuSign, pero más lindo y más usable. Los estilos
    salen de la maqueta de Carlos en Lovable
    (<https://lovable.dev/preview/IH4hFkwJsosb9khZpHbXWAcIIZ8NlFs5>), por ingeniería
    inversa. Las pantallas que en esa maqueta dan 404 se completan con el diseño en Figma
    (<https://raid-score-17949864.figma.site>), pero con los estilos de la de Lovable.
