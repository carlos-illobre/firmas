# Especificaciones de Firmas

La entrada al proyecto: de qué se trata y dónde está escrito cada requerimiento. Con lo que
hay en esta carpeta, alguien que nunca vio el código tiene que poder construir de nuevo una
aplicación que cumpla todos los requerimientos, funcionales y no funcionales.

**Acá no se dice si algo está hecho.** Eso depende del código de hoy y vive en
[proyecto/estado.yml](../proyecto/estado.yml).

## De qué se trata

Firma de documentos para abogados en la Argentina: un producto como DocuSign, pensado para
el mercado argentino y para el trabajo de un estudio jurídico. Qué es y para quién, en
[docs/PRODUCTO.md](../docs/PRODUCTO.md).

## Cómo está organizado

| Dónde | Qué tiene |
|---|---|
| [La constitución](../.specify/memory/constitution.md) | Lo que no se negocia y el flujo de trabajo |
| `001` en adelante | Una por capacidad: `resumen.md`, `spec.md`, `ux.md` y, donde hay datos, `data-model.md` |
| [preguntas-abiertas.md](preguntas-abiertas.md) | Lo que todavía no está decidido |

## Requerimientos

Todos en borrador: esperan la aprobación de Carlos (paso 1).

### 001 · Pedido de firma

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-01 | Se empieza subiendo un archivo, con una plantilla o desde cero | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-02 | PDF o Word; el Word se convierte a PDF y se firma el PDF | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-03 | Destinatarios con nombre, correo y teléfono; firman o reciben copia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-04 | Orden de firma: uno después del otro o todos a la vez | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-05 | Forma de identidad por firmante: correo, SMS, WhatsApp, DNI o RENAPER | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-06 | Canal por destinatario: correo u otro medio | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-07 | Campos ubicados en el documento, con el color de cada firmante | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-08 | Cada firmante, al menos un campo de firma | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-09 | Resumen y mensaje antes de enviar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-10 | Vencimiento elegido por el remitente | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-11 | Recordatorios automáticos y a pedido | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-12 | Borradores | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-13 | Enlace personal en el mensaje, sin cuenta | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-14 | Identidad comprobada antes de ver el documento | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-15 | Ver todo, descargar y recorrer los campos pendientes | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-16 | Firma digital (archivo, token o firma remota) o electrónica (botón) | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-17 | Rechazar con motivo | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-18 | En orden, cada uno recibe al firmar el anterior | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-19 | Estados del pedido | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-20 | Rechazo o vencimiento: se cancela, se avisa, se puede reenviar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-21 | El remitente puede cancelar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-22 | Al completarse, todos reciben el documento firmado y la constancia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-23 | Qué dice la constancia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-24 | Registro de eventos que no se puede borrar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-25 | Huella del documento firmado | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-01 | Celular y computadora | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-02 | Solo ven el documento quienes corresponde | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-03 | Enlace imposible de adivinar, que vence con el pedido | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-04 | Textos claros para quien no es abogado | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |

### 002 · Inicio y documentos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-26 | Inicio muestra un saludo con el nombre y la fecha, y cuatro números: esperando mi acción,… | [002-documentos](002-documentos/spec.md) |
| RF-27 | Inicio lista lo que requiere atención del abogado, ordenado por urgencia, con acceso… | [002-documentos](002-documentos/spec.md) |
| RF-28 | Inicio muestra los documentos recientes, los próximos vencimientos y la actividad reciente… | [002-documentos](002-documentos/spec.md) |
| RF-29 | La lista de documentos muestra, por documento: nombre, etiquetas, cliente, estado, última… | [002-documentos](002-documentos/spec.md) |
| RF-30 | La lista se filtra por estado (todos, esperando mi acción, esperando a otros, completados,… | [002-documentos](002-documentos/spec.md) |
| RF-31 | Un buscador en todas las pantallas encuentra documentos, clientes y plantillas por nombre | [002-documentos](002-documentos/spec.md) |
| RF-32 | El detalle de un documento muestra el nombre, el estado, el tipo, el cliente, el… | [002-documentos](002-documentos/spec.md) |
| RF-33 | Desde el detalle se puede recordar, descargar, archivar y cancelar el proceso de firma | [002-documentos](002-documentos/spec.md) |
| RF-34 | Un documento se puede archivar y desarchivar; archivado no aparece en «Todos» | [002-documentos](002-documentos/spec.md) |
| RF-35 | Cada documento tiene un cliente, un responsable del estudio y etiquetas opcionales | [002-documentos](002-documentos/spec.md) |
| RNF-05 | Inicio, la lista y el detalle se usan completos en el celular y en la computadora | [002-documentos](002-documentos/spec.md) |

### 003 · Plantillas y documentos desde cero

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-36 | Hay plantillas del estudio, con nombre, categoría, texto, datos variables y, opcionalmente,… | [003-plantillas](003-plantillas/spec.md) |
| RF-37 | Usar una plantilla pide completar sus datos variables y arma el documento del pedido sin… | [003-plantillas](003-plantillas/spec.md) |
| RF-38 | Las plantillas se listan con su categoría, cuándo y quién la usó por última vez; se filtran… | [003-plantillas](003-plantillas/spec.md) |
| RF-39 | Se pueden crear, editar y borrar plantillas | [003-plantillas](003-plantillas/spec.md) |
| RF-40 | Se puede redactar un documento desde cero en el producto, con formato básico (títulos,… | [003-plantillas](003-plantillas/spec.md) |
| RNF-06 | Usar una plantilla funciona en el celular y en la computadora | [003-plantillas](003-plantillas/spec.md) |

### 004 · Clientes y contactos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-41 | Hay contactos de dos clases: personas y organizaciones | [004-contactos](004-contactos/spec.md) |
| RF-42 | De una persona se guarda nombre y apellido, correo y teléfono; de una organización, su nombre | [004-contactos](004-contactos/spec.md) |
| RF-43 | La lista de contactos muestra, de cada uno, cuántos documentos tiene asociados y cuántos… | [004-contactos](004-contactos/spec.md) |
| RF-44 | Al cargar destinatarios en un pedido se sugieren los contactos guardados | [004-contactos](004-contactos/spec.md) |
| RF-45 | Los contactos se crean, editan y borran | [004-contactos](004-contactos/spec.md) |
| RNF-07 | Los datos de los contactos son datos personales y se tratan como tales; su norma (ley… | [004-contactos](004-contactos/spec.md) |

### 005 · Tareas y vencimientos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-46 | Una tarea tiene título, fecha, tipo (revisión, seguimiento, vencimiento), prioridad,… | [005-tareas](005-tareas/spec.md) |
| RF-47 | Las tareas se ven en lista o en calendario, y se filtran en mis tareas, asignadas por mí y… | [005-tareas](005-tareas/spec.md) |
| RF-48 | Las tareas se crean, editan, completan y borran | [005-tareas](005-tareas/spec.md) |
| RF-49 | El menú muestra cuántas tareas pendientes tiene el abogado | [005-tareas](005-tareas/spec.md) |
| RNF-08 | Las tareas se usan completas en el celular y en la computadora | [005-tareas](005-tareas/spec.md) |

### 006 · Historial y auditoría

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-50 | El historial muestra los eventos de la capacidad 001 y los del estudio (descargas, cambios… | [006-actividad](006-actividad/spec.md) |
| RF-51 | Se filtra por período, por participante y por acción | [006-actividad](006-actividad/spec.md) |
| RF-52 | Se exporta lo filtrado | [006-actividad](006-actividad/spec.md) |
| RNF-09 | Nadie puede borrar ni cambiar un evento, tampoco un administrador | [006-actividad](006-actividad/spec.md) |

### 007 · Cuentas, equipo y configuración

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-53 | Un abogado se registra con nombre, correo y contraseña, crea su estudio, confirma su… | [007-configuracion](007-configuracion/spec.md) |
| RF-54 | El administrador invita colaboradores por correo, les asigna un rol, se lo cambia y les… | [007-configuracion](007-configuracion/spec.md) |
| RF-55 | La seguridad y autenticación del estudio se configura: métodos de acceso y políticas | [007-configuracion](007-configuracion/spec.md) |
| RF-56 | Cada usuario elige qué avisos recibe | [007-configuracion](007-configuracion/spec.md) |
| RF-57 | El estudio fija las preferencias de los documentos: formato de fecha, recordatorios y… | [007-configuracion](007-configuracion/spec.md) |
| RF-58 | El estudio guarda sus datos: nombre, logo e información de contacto | [007-configuracion](007-configuracion/spec.md) |
| RF-59 | El estudio conecta integraciones con herramientas propias | [007-configuracion](007-configuracion/spec.md) |
| RNF-10 | Las contraseñas no se guardan en claro y los intentos de ingreso fallidos se limitan | [007-configuracion](007-configuracion/spec.md) |
