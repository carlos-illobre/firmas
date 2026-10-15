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

1. Los contratos que la ley obliga a hacer por escritura pública (por ejemplo, los de
   derechos reales sobre inmuebles, Código Civil y Comercial, art. 1017) no se pueden otorgar
   con el producto. ¿Se avisa al remitente, se bloquea, o no se hace nada?

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

## 001 · Pedido de firma

13. ¿Cuál es el tamaño y la cantidad de páginas máximas de un archivo?
14. Además del correo, ¿qué otros canales hay para mandar el pedido: WhatsApp, SMS, copiar el
    enlace?
15. ¿Se pueden pedir dos formas de identidad al mismo firmante, por ejemplo, correo y código
    por SMS?
16. La maqueta muestra «Revisar y aprobar», «Solicitada revisión interna» y «Comentario
    agregado». ¿Hay una revisión interna del estudio antes de enviar, y comentarios sobre el
    documento?
17. ¿Aprobás los supuestos de la especificación (sección «Assumptions»)? Tipos de campo,
    nombre escrito como firma electrónica, recordatorios cada tres días, avisos al
    remitente, enlace en vez de adjunto y sin delegar la firma.

## 002 · Inicio y documentos

18. En el detalle de un documento, ¿qué edita «Abrir editor»?
19. ¿Todo documento tiene un cliente, o puede no tenerlo?
20. ¿«Demorado» es lo que vence en los próximos tres días sin completarse, o otra cosa?

## 003 · Plantillas

21. ¿Quién puede crear y cambiar plantillas: cualquier miembro del estudio o solo el
    administrador?
22. ¿El producto trae modelos propios, o cada estudio carga los suyos?

## 004 · Contactos

23. Además de nombre, correo y teléfono, ¿qué datos se guardan: DNI, CUIT, domicilio?

## 005 · Tareas

24. La maqueta muestra «Contrato de locación vence en 7 días — Renovación no iniciada». ¿Un
    documento tiene fechas propias del contrato (vencimiento, renovación), distintas del
    vencimiento del pedido? ¿El producto crea tareas solo con esas fechas?

## 006 · Actividad

25. ¿En qué formato se exporta el registro: PDF, planilla, los dos?

## 007 · Configuración

26. ¿Qué roles hay en un estudio y qué puede hacer cada uno?
27. ¿Cómo se ingresa: correo y contraseña, con Google, con un segundo factor?
28. ¿Con qué herramientas se integra al principio, si con alguna?
29. ¿Cualquiera puede crear una cuenta, o se entra por invitación?
