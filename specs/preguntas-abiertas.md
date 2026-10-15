# Preguntas abiertas

Lo que hay que decidir antes de escribir la primera especificación. Salieron el 2026-10-15,
al crear el proyecto: de lo que Carlos pidió («un clon de DocuSign enfocado en el mercado
argentino, con foco en abogados») no sale ninguna regla más, así que cada vacío quedó como
pregunta.

Solo Carlos las puede contestar. Cada respuesta se anota con su fecha en
[docs/decisiones-de-negocio.md](../docs/decisiones-de-negocio.md) y en la especificación
que toca, y la pregunta se borra de acá. Las normas que se nombran son para orientar la
pregunta, no reglas: la regla se escribe con la norma verificada (constitución, principio II).

## El valor de la firma

Decidido: quien tiene certificado de firma digital lo ingresa y firma con él; quien no,
firma con firma electrónica (decisión 5).

1. Para la firma digital: ¿el certificado se ingresa como archivo, se usa con el token del
   firmante o se conecta con la Plataforma de Firma Digital Remota? ¿Se aceptan los tres?
2. ¿Hay documentos que el producto no debe aceptar porque la ley exige otra forma (por
   ejemplo, los que requieren escritura pública)? ¿Se avisa o se bloquea?

## Para quién y para qué

Decidido: los firmantes no necesitan cuenta; firman desde el correo (decisión 12).

3. ¿Se firman escritos para presentar en un expediente judicial electrónico (PJN, SCBA u
   otras jurisdicciones)? ¿Se integra con esos sistemas o el abogado sube el documento él?
4. ¿Qué tiene que tener que no tenga DocuSign para que un abogado argentino lo elija, además
   de ser más lindo y más usable?

## Identidad y prueba

Decidido: para la firma electrónica están todas las formas de comprobar la identidad
(decisión 13).

5. ¿Quién elige la forma de comprobar la identidad: quien envía, para cada firmante, o el
   firmante?
6. ¿Qué tiene que decir la constancia de lo que pasó (quién, cuándo, desde dónde, qué
   versión del documento) y para qué se usa: para presentarla en un juicio?
7. ¿Cuánto tiempo se guardan los documentos firmados y las constancias, y quién puede
   pedirlos después?

## Recorrido

Decidido: PDF o Word, que se convierte a PDF (decisión 14); el orden de firma lo elige quien
envía (decisión 15); si alguien rechaza o el pedido vence, se cancela, se avisa y se puede
reenviar (decisión 17).

8. ¿Quién elige el canal del pedido de firma, y entre cuáles: correo, WhatsApp, SMS? El
   correo, ¿va siempre?
9. ¿Cuánto tarda en vencer un pedido? ¿Lo elige quien envía? ¿Hay recordatorios
   automáticos, como los que muestra la maqueta?

## Negocio

Decidido: por ahora nadie paga (decisión 6).

10. Cuando se cobre, ¿cómo: por documento, por mes, por usuario? ¿En pesos? ¿Con factura
    electrónica? ¿Hay un plan gratis?
11. ¿El nombre del producto es «Firmas» o es solo el del repositorio?
12. ¿Hay un primer estudio o abogado que lo pruebe? ¿Quién valida que lo jurídico está bien?

## Fechas

Decidido: no hay fecha límite (decisión 9), y la primera versión tiene todas las pantallas de
las maquetas (decisión 18).
