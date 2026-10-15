# ADR-006: Mensajería, identidad y certificado de aplicación

**Estado**: Aceptado en parte (2026-10-15): lo de la primera versión está decidido; el resto queda para la segunda · **Fecha**: 2026-10-15

## Contexto

La primera versión manda pedidos por correo o WhatsApp (decisión 26), comprueba la identidad
por correo, SMS, WhatsApp, foto del DNI o RENAPER (decisión 13), y firma electrónicamente con
un certificado de aplicación (ADR-002). Precios consultados el 2026-10-15; cambian seguido.

## Correo

| Opción | Costo |
|---|---|
| **Amazon SES** (región de la UE) | US$ 0,10 cada 1.000 correos |
| Resend | Gratis hasta 3.000 por mes; después, desde US$ 20 por mes |

Recomendación: **Amazon SES**, el más barato a cualquier volumen.

## WhatsApp y SMS

| Opción | Costo por mensaje a la Argentina |
|---|---|
| **WhatsApp por la API de Meta, directa** | Unos US$ 0,026 por mensaje de utilidad o de código (tarifa de Meta para la Argentina desde julio de 2026, según tablas de terceros; la lista oficial cambia seguido) |
| WhatsApp por Twilio | Lo mismo más US$ 0,005 de Twilio |
| **SMS por Twilio** | US$ 0,1034 por mensaje (twilio.com/en-us/sms/pricing/ar) |

Recomendación: WhatsApp por la API de Meta directa, y SMS por Twilio. Con 100 pedidos por
mes, cada uno con dos firmantes, un recordatorio y un código, el gasto ronda US$ 10 a 25
según cuánto se use el SMS. El SMS cuesta unas cuatro veces más que el WhatsApp.

## Validación contra RENAPER

RENAPER valida la identidad de empresas privadas mediante convenio y cobra un canon por
consulta, que no publica (noticias oficiales de RENAPER y ENACOM, septiembre de 2024). Hay
dos caminos:

| Opción | Costo | Notas |
|---|---|---|
| Convenio directo con RENAPER | Canon por consulta, a pedir | Trámite largo; exige cumplir la ley 25.326 |
| **Un proveedor ya conectado** (por ejemplo VU Security, MetaMap o Truora) | Por consulta, a cotizar; suelen cobrar además un mínimo mensual | Más rápido de integrar |

Recomendación: cotizar con dos proveedores antes de elegir. Mientras tanto, la validación
contra RENAPER puede quedar como la última tarea de la capacidad 001.

## Certificado de aplicación para la firma electrónica

| Opción | Costo | Qué vale |
|---|---|---|
| **Certificado de aplicación de un certificador licenciado** | A cotizar: lo venden certificadores privados licenciados | Presunción de que el documento proviene del titular del certificado (ley 25.506, art. 10) |
| Certificado propio, sin certificador licenciado | Gratis | La firma electrónica vale igual como tal (ley 25.506, art. 5), sin esa presunción |

Recomendación: empezar con un certificado propio y pasar al licenciado antes del
lanzamiento, cuando se sepa el costo.

## Decisión

Carlos decidió que la primera versión no use proveedores pagos (decisión 42):

- **Correo**: Amazon SES, en una región de la Unión Europea (ADR-005).
- **Certificado de aplicación**: uno propio, sin certificador licenciado. Pasar a uno
  licenciado es una decisión de Carlos antes del lanzamiento.
- **WhatsApp, SMS y RENAPER**: no entran en la primera versión. Las opciones y los costos de
  arriba quedan para cuando se especifique la segunda.
