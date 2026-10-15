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

Especificaciones aprobadas por Carlos el 2026-10-15. Falta el paso 2: las maquetas.

### 001 · Pedido de firma

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-01 | Se empieza subiendo un archivo, con una plantilla o desde cero | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-02 | PDF o Word de hasta 50 MB; el Word se convierte a PDF y se firma el PDF | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-02a | Cartel si el contrato exige escritura pública; el solicitante decide | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-03 | Destinatarios con nombre, correo y teléfono; firman o reciben copia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-04 | Orden de firma: uno después del otro o todos a la vez | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-05 | Una o dos formas de identidad por firmante: correo, SMS, WhatsApp, DNI o RENAPER | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-06 | Canal por destinatario: correo o WhatsApp | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-07 | Campos ubicados en el documento, con el color de cada firmante | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-08 | Cada firmante, al menos un campo de firma | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-09 | Resumen y mensaje antes de enviar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-09a | Revisión opcional por miembros del estudio antes de enviar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-10 | Vencimiento elegido por el solicitante | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-11 | Recordatorios automáticos y a pedido | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-12 | Borradores | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-13 | Enlace personal en el mensaje, sin cuenta | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-14 | Identidad comprobada antes de ver el documento | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-15 | Ver todo, descargar y recorrer los campos pendientes | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-16 | Firma digital (archivo, token o firma remota) o electrónica (botón) | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-17 | Rechazar con motivo | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-18 | En orden, cada uno recibe al firmar el anterior | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-19 | Estados del pedido, con «En revisión» | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-20 | Rechazo o vencimiento: se cancela, se avisa, se puede reenviar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-21 | El solicitante puede cancelar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-22 | Al completarse, todos reciben el documento firmado y la constancia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-23 | Qué dice la constancia | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-24 | Registro de eventos que no se puede borrar | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-25 | Huella del documento firmado | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-26 | Firma digital válida: certificado vigente, verificable y de certificador licenciado | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-27 | La firma digital equivale a la de puño y letra y presume autoría e integridad | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-28 | La firma electrónica se prueba si se la desconoce: la constancia junta esa prueba | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-29 | El solicitante ve qué vale cada firma | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RF-30 | La firma remota es firma digital, con posibles aranceles | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-01 | Celular y computadora | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-02 | Solo ven el documento quienes corresponde | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-03 | Enlace imposible de adivinar, que vence con el pedido | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |
| RNF-04 | Textos claros para quien no es abogado | [001-pedido-de-firma](001-pedido-de-firma/spec.md) |

### 002 · Inicio y documentos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-31 | Inicio muestra un saludo con el nombre y la fecha, y cuatro números: esperando mi acción,… | [002-documentos](002-documentos/spec.md) |
| RF-32 | Inicio lista lo que requiere atención del abogado, ordenado por urgencia, con acceso… | [002-documentos](002-documentos/spec.md) |
| RF-33 | Inicio muestra los documentos recientes, los próximos vencimientos y la actividad reciente… | [002-documentos](002-documentos/spec.md) |
| RF-34 | La lista de documentos muestra, por documento: nombre, etiquetas, cliente, estado, última… | [002-documentos](002-documentos/spec.md) |
| RF-35 | La lista se filtra por estado (todos, esperando mi acción, esperando a otros, completados,… | [002-documentos](002-documentos/spec.md) |
| RF-36 | Un buscador en todas las pantallas encuentra documentos, clientes y plantillas por nombre | [002-documentos](002-documentos/spec.md) |
| RF-37 | El detalle de un documento muestra el nombre, el estado, el tipo, el cliente, el… | [002-documentos](002-documentos/spec.md) |
| RF-38 | Desde el detalle se puede recordar, descargar, archivar, cancelar el proceso de firma y… | [002-documentos](002-documentos/spec.md) |
| RF-38a | El editor cambia todo lo referente a la firma de un pedido: los destinatarios, el orden, el… | [002-documentos](002-documentos/spec.md) |
| RF-39 | Un documento se puede archivar y desarchivar; archivado no aparece en «Todos» | [002-documentos](002-documentos/spec.md) |
| RF-40 | Cada documento tiene uno o más firmantes y un responsable del estudio; el cliente y las… | [002-documentos](002-documentos/spec.md) |
| RNF-05 | Inicio, la lista y el detalle se usan completos en el celular y en la computadora | [002-documentos](002-documentos/spec.md) |

### 003 · Plantillas y documentos desde cero

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-41 | Hay plantillas del estudio, con nombre, categoría, texto, datos variables y, opcionalmente,… | [003-plantillas](003-plantillas/spec.md) |
| RF-42 | Usar una plantilla pide completar sus datos variables y arma el documento del pedido sin… | [003-plantillas](003-plantillas/spec.md) |
| RF-43 | Las plantillas se listan con su categoría, cuándo y quién la usó por última vez; se filtran… | [003-plantillas](003-plantillas/spec.md) |
| RF-44 | El solicitante crea, edita y borra plantillas | [003-plantillas](003-plantillas/spec.md) |
| RF-44a | El producto trae modelos base, que cualquier estudio usa o copia para hacer su plantilla:… | [003-plantillas](003-plantillas/spec.md) |
| RF-45 | Se puede redactar un documento desde cero en el producto, con formato básico (títulos,… | [003-plantillas](003-plantillas/spec.md) |
| RNF-06 | Usar una plantilla funciona en el celular y en la computadora | [003-plantillas](003-plantillas/spec.md) |

### 004 · Clientes y contactos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-46 | Hay contactos de dos clases: personas y organizaciones | [004-contactos](004-contactos/spec.md) |
| RF-47 | De una persona se guarda nombre, apellido y correo; y, si se tienen, celular, DNI, CUIT o… | [004-contactos](004-contactos/spec.md) |
| RF-48 | La lista de contactos muestra, de cada uno, cuántos documentos tiene asociados y cuántos… | [004-contactos](004-contactos/spec.md) |
| RF-49 | Al cargar destinatarios en un pedido se sugieren los contactos guardados | [004-contactos](004-contactos/spec.md) |
| RF-50 | Los contactos se crean, editan y borran | [004-contactos](004-contactos/spec.md) |
| RNF-07 | Los datos de los contactos son datos personales: se guardan solo los necesarios, ciertos y… | [004-contactos](004-contactos/spec.md) |

### 005 · Tareas y vencimientos

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-51 | Una tarea tiene título, fecha, tipo (revisión, seguimiento, vencimiento), prioridad,… | [005-tareas](005-tareas/spec.md) |
| RF-52 | Las tareas se ven en lista o en calendario, y se filtran en mis tareas, asignadas por mí y… | [005-tareas](005-tareas/spec.md) |
| RF-53 | Las tareas se crean, editan, completan y borran | [005-tareas](005-tareas/spec.md) |
| RF-54 | El menú muestra cuántas tareas pendientes tiene el abogado | [005-tareas](005-tareas/spec.md) |
| RNF-08 | Las tareas se usan completas en el celular y en la computadora | [005-tareas](005-tareas/spec.md) |

### 006 · Historial y auditoría

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-55 | El historial muestra los eventos de la capacidad 001 y los del estudio (descargas, cambios… | [006-actividad](006-actividad/spec.md) |
| RF-56 | Se filtra por período, por participante y por acción | [006-actividad](006-actividad/spec.md) |
| RF-57 | Se exporta lo filtrado, en CSV | [006-actividad](006-actividad/spec.md) |
| RNF-09 | Nadie puede borrar ni cambiar un evento, tampoco un administrador | [006-actividad](006-actividad/spec.md) |

### 007 · Cuentas, equipo y configuración

| ID | Requerimiento | Especificación |
|---|---|---|
| RF-58 | El registro es libre | [007-configuracion](007-configuracion/spec.md) |
| RF-59 | Cualquier miembro del estudio invita a otros por correo y les quita el acceso | [007-configuracion](007-configuracion/spec.md) |
| RF-60 | La seguridad y autenticación del estudio se configura: métodos de acceso y políticas | [007-configuracion](007-configuracion/spec.md) |
| RF-61 | Cada usuario elige qué avisos recibe | [007-configuracion](007-configuracion/spec.md) |
| RF-62 | El estudio fija las preferencias de los documentos: formato de fecha, recordatorios y… | [007-configuracion](007-configuracion/spec.md) |
| RF-63 | El estudio guarda sus datos: nombre, logo e información de contacto | [007-configuracion](007-configuracion/spec.md) |
| RF-64 | El producto no se conecta con otros servicios, salvo los mínimos necesarios para funcionar:… | [007-configuracion](007-configuracion/spec.md) |
| RNF-10 | Las contraseñas no se guardan en claro y los intentos de ingreso fallidos se limitan | [007-configuracion](007-configuracion/spec.md) |
