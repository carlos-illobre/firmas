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
firma con firma electrónica (decisión 5), de cualquiera de las tres formas (decisión 19).

1. ¿Hay documentos que el producto no debe aceptar porque la ley exige otra forma (por
   ejemplo, los que requieren escritura pública)? ¿Se avisa o se bloquea?

## Para quién y para qué

Decidido: los firmantes no necesitan cuenta; firman desde el correo (decisión 12).

2. ¿Se firman escritos para presentar en un expediente judicial electrónico (PJN, SCBA u
   otras jurisdicciones)? ¿Se integra con esos sistemas o el abogado sube el documento él?
3. ¿Qué tiene que tener que no tenga DocuSign para que un abogado argentino lo elija, además
   de ser más lindo y más usable?

## Identidad y prueba

Decidido: para la firma electrónica están todas las formas de comprobar la identidad
(decisión 13), y quien envía elige cuál para cada firmante (decisión 20). Al terminar
se genera una constancia para presentar en un juicio (decisión 23).

4. ¿Cuánto tiempo se guardan los documentos firmados y las constancias, y quién puede
   pedirlos después?

## Recorrido

Todo decidido: PDF o Word, que se convierte a PDF (decisión 14); el orden de firma lo elige
quien envía (decisión 15); si alguien rechaza o el pedido vence, se cancela, se avisa y se
puede reenviar (decisión 17). Quien envía elige el canal (decisión 21) y el vencimiento, y
hay recordatorios automáticos (decisión 22).

## Negocio

Decidido: por ahora nadie paga (decisión 6).

5. Cuando se cobre, ¿cómo: por documento, por mes, por usuario? ¿En pesos? ¿Con factura
   electrónica? ¿Hay un plan gratis?
6. ¿El nombre del producto es «Firmas» o es solo el del repositorio?
7. ¿Hay un primer estudio o abogado que lo pruebe? ¿Quién valida que lo jurídico está bien?

## Fechas

Decidido: no hay fecha límite (decisión 9), y la primera versión tiene todas las pantallas de
las maquetas (decisión 18).
