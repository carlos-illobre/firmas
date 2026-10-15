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

1. ¿Qué firma ofrece el producto: **firma electrónica** (la que vale como prueba, pero
   quien la invoca tiene que probar que es válida, ley 25.506, art. 5), **firma digital**
   (con certificado de un certificador licenciado, que el Código Civil y Comercial, art.
   288, equipara a la firma de puño y letra), o las dos según el documento?
2. Si hay firma digital: ¿el producto se integra con certificadores licenciados (por
   ejemplo, la Plataforma de Firma Digital Remota del Estado), pide ser uno, o el abogado
   firma con el token o certificado que ya tiene?
3. ¿Hay documentos que el producto no debe aceptar porque la ley exige otra forma (por
   ejemplo, los que requieren escritura pública)? ¿Se avisa o se bloquea?

## Para quién y para qué

4. ¿Quién es el cliente que paga: el abogado independiente, el estudio, o los dos?
5. ¿Quiénes firman: el abogado, su cliente, la contraparte, testigos? ¿Los que no son
   abogados necesitan cuenta?
6. ¿Qué documentos se firman primero? Por ejemplo: contratos, convenios de honorarios,
   acuerdos de mediación, cartas poder, escritos judiciales. ¿Cuál es el más importante
   para empezar?
7. ¿Se firman escritos para presentar en un expediente judicial electrónico (PJN, SCBA u
   otras jurisdicciones)? ¿Se integra con esos sistemas o el abogado sube el documento él?
8. ¿Qué tiene que tener que no tenga DocuSign para que un abogado argentino lo elija?

## Identidad y prueba

9. ¿Cómo se comprueba quién firma: correo, código por SMS o WhatsApp, foto del DNI,
   validación contra RENAPER, o depende del documento?
10. ¿Qué tiene que decir la constancia de lo que pasó (quién, cuándo, desde dónde, qué
    versión del documento) y para qué se usa: para presentarla en un juicio?
11. ¿Cuánto tiempo se guardan los documentos firmados y las constancias, y quién puede
    pedirlos después?

## Recorrido

12. ¿El documento se sube armado (PDF) o el producto también ayuda a redactarlo, con
    modelos?
13. ¿Hay orden de firma (uno después del otro) o todos firman a la vez?
14. ¿Cómo le llega el pedido de firma a cada uno: correo, WhatsApp, un enlace?
15. ¿Qué pasa si alguien rechaza firmar, o el pedido vence?

## Negocio

16. ¿Cómo se cobra: por documento, por mes, por usuario? ¿En pesos? ¿Con factura
    electrónica?
17. ¿Hay un plan gratis?
18. ¿El nombre del producto es «Firmas» o es solo el del repositorio?
19. ¿Hay un primer estudio o abogado que lo pruebe? ¿Quién valida que lo jurídico está bien?

## Fechas

20. ¿Para cuándo querés la primera versión, y qué tiene que tener como mínimo?
