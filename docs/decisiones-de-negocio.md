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
19. **Cómo se usa el certificado.** Se aceptan las tres formas: subir el archivo del
    certificado, usar el token del firmante y firmar con la Plataforma de Firma Digital
    Remota.
20. **Quién elige cómo se comprueba la identidad.** Quien envía, para cada firmante.
21. **El canal.** Lo elige quien envía: el correo u otro medio que elija.
22. **Vencimiento y recordatorios.** Quien envía elige cuándo vence el pedido. Hay
    recordatorios automáticos.
23. **La constancia.** Al terminar se genera una constancia de lo que pasó: quién firmó,
    cuándo, desde dónde, con qué forma de identidad y la huella del documento, pensada para
    presentarla en un juicio.
24. **Contratos que exigen escritura pública.** Si el documento es de los que la ley obliga
    a hacer por escritura pública, aparece un cartel que explica la situación, y quien envía
    decide si sigue.
25. **Tamaño del archivo.** El mismo que DocuSign: 50 MB por archivo (documentación de
    DocuSign para desarrolladores, «Rules and limits», consultada el 2026-10-15).
26. **Canales.** El pedido de firma se manda por correo o por WhatsApp.
27. **Identidad.** A cada firmante se le puede pedir una o dos formas de comprobar su
    identidad.
28. **Revisión antes de enviar.** Si quien envía tilda esa opción, el pedido pasa por una
    revisión antes de salir.
29. **Supuestos de la especificación 001.** Aprobados: tipos de campo, nombre escrito como
    firma electrónica, recordatorios cada tres días, avisos a quien envía, enlace en vez de
    adjunto y sin delegar la firma.
30. **«Abrir editor».** Edita todo lo referente a la firma de un documento: la posición de
    la firma, los campos y lo demás del pedido.
31. **Cliente.** Un documento puede no tener cliente; lo que siempre tiene es uno o varios
    firmantes.
32. **Plantillas.** Las crea quien envía. El producto trae, además, algunos modelos base que
    propone el agente.
33. **Datos de los contactos.** Los decide el agente.
34. **Tareas.** No hay tareas que se creen solas a partir de fechas del contrato.
35. **Historial.** Se exporta en CSV.
36. **Roles.** Solo hay dos: quien envía y quien recibe, con nombres del oficio si los hay.
    No hay roles dentro del estudio.
37. **Conexiones con otros servicios.** Solo las mínimas necesarias para que funcione.
38. **Registro.** Libre: cualquiera crea una cuenta.
39. **Especificaciones aprobadas.** Las siete especificaciones (001 a 007), con sus
    supuestos: el editor no cambia lo de quien ya firmó, los documentos y las constancias se
    guardan mientras exista la cuenta, se entra con correo y contraseña con un segundo factor
    opcional, las plantillas son de todo el estudio y «demorado» es lo que vence en tres días
    sin completarse. Los roles se llaman solicitante y firmante.
40. **Maqueta de la pantalla del firmante.** La variante B: el documento a la izquierda y un
    panel de firma a la derecha, con lo que ya hizo, lo que le falta y la elección entre
    firma digital y electrónica; en el celular, el panel es una hoja plegable abajo. Las
    demás pantallas siguen ese estilo.
41. **Maquetas aprobadas.** Todas las pantallas de las capacidades 001 a 007, con estos
    detalles: el cartel de escritura pública aparece cuando el producto lo detecta por el
    texto del documento; para devolver un pedido en revisión el comentario es obligatorio;
    el código de identidad admite 3 intentos y después bloquea el acceso 15 minutos; los
    pedidos vencen por defecto a los 14 días, que el estudio puede cambiar; la contraseña
    tiene al menos 10 caracteres; cancelar un pedido pide confirmación; el menú dice
    «Historial» en vez de «Actividad»; «Firmas» es el nombre provisorio; y el ingreso a la
    Firma Digital Remota se confirma en el paso 3.
