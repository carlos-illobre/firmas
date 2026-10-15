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

3. Los firmantes que no son abogados, ¿necesitan cuenta o firman desde un enlace?
4. ¿Se firman escritos para presentar en un expediente judicial electrónico (PJN, SCBA u
   otras jurisdicciones)? ¿Se integra con esos sistemas o el abogado sube el documento él?
5. ¿Qué tiene que tener que no tenga DocuSign para que un abogado argentino lo elija, además
   de ser más lindo y más usable?

## Identidad y prueba

6. ¿Cómo se comprueba quién firma con firma electrónica: correo, código por SMS o WhatsApp,
   foto del DNI, validación contra RENAPER, o depende del documento?
7. ¿Qué tiene que decir la constancia de lo que pasó (quién, cuándo, desde dónde, qué
   versión del documento) y para qué se usa: para presentarla en un juicio?
8. ¿Cuánto tiempo se guardan los documentos firmados y las constancias, y quién puede
   pedirlos después?

## Recorrido

9. Además de adjuntar el archivo, ¿el producto ayuda a redactar el documento, con modelos?
   ¿Qué formatos se aceptan: solo PDF, o también Word?
10. ¿Hay orden de firma (uno después del otro) o todos firman a la vez?
11. ¿Cómo le llega el pedido de firma a cada uno: correo, WhatsApp, un enlace?
12. ¿Qué pasa si alguien rechaza firmar, o el pedido vence?

## Negocio

Decidido: por ahora nadie paga (decisión 6).

13. Cuando se cobre, ¿cómo: por documento, por mes, por usuario? ¿En pesos? ¿Con factura
    electrónica? ¿Hay un plan gratis?
14. ¿El nombre del producto es «Firmas» o es solo el del repositorio?
15. ¿Hay un primer estudio o abogado que lo pruebe? ¿Quién valida que lo jurídico está bien?

## Fechas

Decidido: no hay fecha límite (decisión 9).

16. ¿Qué tiene que tener como mínimo la primera versión?
