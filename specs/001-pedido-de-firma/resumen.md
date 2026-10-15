# Resumen: pedido de firma

Un solicitante del estudio prepara un documento, carga a los destinatarios, ubica los campos y
lo envía; cada firmante firma desde el mensaje, sin cuenta, con firma digital o electrónica;
al terminar quedan el documento firmado y la constancia. Detalle en [spec.md](spec.md).

## Requerimientos

| ID | En una línea |
|---|---|
| RF-01 | Se empieza subiendo un archivo, con una plantilla o desde cero |
| RF-02 | PDF o Word de hasta 50 MB; el Word se convierte a PDF y se firma el PDF |
| RF-02a | Cartel si el contrato exige escritura pública; el solicitante decide |
| RF-03 | Destinatarios con nombre, correo y teléfono; firman o reciben copia |
| RF-04 | Orden de firma: uno después del otro o todos a la vez |
| RF-05 | Una o dos formas de identidad por firmante: correo, SMS, WhatsApp, DNI o RENAPER |
| RF-06 | Canal por destinatario: correo o WhatsApp |
| RF-07 | Campos ubicados en el documento, con el color de cada firmante |
| RF-08 | Cada firmante, al menos un campo de firma |
| RF-09 | Resumen y mensaje antes de enviar |
| RF-09a | Revisión opcional por miembros del estudio antes de enviar |
| RF-10 | Vencimiento elegido por el solicitante |
| RF-11 | Recordatorios automáticos y a pedido |
| RF-12 | Borradores |
| RF-13 | Enlace personal en el mensaje, sin cuenta |
| RF-14 | Identidad comprobada antes de ver el documento |
| RF-15 | Ver todo, descargar y recorrer los campos pendientes |
| RF-16 | Firma digital (archivo, token o firma remota) o electrónica (botón) |
| RF-17 | Rechazar con motivo |
| RF-18 | En orden, cada uno recibe al firmar el anterior |
| RF-19 | Estados del pedido, con «En revisión» |
| RF-20 | Rechazo o vencimiento: se cancela, se avisa, se puede reenviar |
| RF-21 | El solicitante puede cancelar |
| RF-22 | Al completarse, todos reciben el documento firmado y la constancia |
| RF-23 | Qué dice la constancia |
| RF-24 | Registro de eventos que no se puede borrar |
| RF-25 | Huella del documento firmado |
| RF-26 | Firma digital válida: certificado vigente, verificable y de certificador licenciado |
| RF-27 | La firma digital equivale a la de puño y letra y presume autoría e integridad |
| RF-28 | La firma electrónica se prueba si se la desconoce: la constancia junta esa prueba |
| RF-29 | El solicitante ve qué vale cada firma |
| RF-30 | La firma remota es firma digital, con posibles aranceles |
| RNF-01 | Celular y computadora |
| RNF-02 | Solo ven el documento quienes corresponde |
| RNF-03 | Enlace imposible de adivinar, que vence con el pedido |
| RNF-04 | Textos claros para quien no es abogado |

## Lo que más pesa

- El firmante no necesita cuenta y firma desde el mensaje.
- El solicitante decide todo por firmante: orden, canal y una o dos formas de identidad.
- Los dos roles son solicitante y firmante.
- Rechazo o vencimiento cancelan el pedido; no se retoma, se reenvía uno nuevo.
- Cada regla jurídica cita su norma (ley 25.506, Código Civil y Comercial, decreto
  182/2019); los contratos que exigen escritura pública no se otorgan con el producto.

## Decisiones de Carlos

5, 7, 8, 11 a 17, 19 a 29 y 36 de [decisiones-de-negocio.md](../../docs/decisiones-de-negocio.md).

## Lo que frena la aprobación

Nada: espera la aprobación de Carlos. Un supuesto nuevo, sobre cuánto se guardan los
documentos, está marcado en la especificación.
