# ADR-005: Alojamiento y datos personales

**Estado**: Propuesto: espera la decisión de Carlos, porque tiene costo · **Fecha**: 2026-10-15

## Contexto

El producto guarda documentos amparados por el secreto profesional y datos personales
(nombres, correos, celulares, DNI, fotos del DNI). La ley 25.326 prohíbe transferir datos
personales a países que no proporcionen niveles de protección adecuados (art. 12). La
disposición DNPDP 60/2016, art. 3 (texto actualizado por la resolución AAIP 34/2019,
verificado el 2026-10-15 en argentina.gob.ar), considera adecuados a los Estados de la Unión
Europea y del Espacio Económico Europeo, el Reino Unido, Suiza, Uruguay, Canadá (sector
privado), Nueva Zelanda y otros; **no incluye a Estados Unidos ni a Brasil**. Para esos
países, la misma disposición aprueba cláusulas contractuales modelo que hay que firmar con
el proveedor. Hoy nadie paga (decisión 6), así que importa el costo.

Lo que hay que alojar (ADR-001 y ADR-003): la aplicación, el proceso de trabajos, Gotenberg,
PostgreSQL con copias de seguridad, y archivos compatibles con S3.

## Opciones

| Opción | Dónde | Costo aproximado por mes | Datos personales |
|---|---|---|---|
| A. Fly.io en Fráncfort o Ámsterdam, con su PostgreSQL administrada y Tigris para archivos | Unión Europea | US$ 45 a 60 | País adecuado: sin cláusulas |
| B. Fly.io en San Pablo | Brasil | US$ 50 a 70 | Hay que firmar cláusulas modelo |
| C. Un servidor propio en Hetzner (Alemania), con la base y las copias a cargo nuestro | Unión Europea | € 10 a 20 | País adecuado: sin cláusulas |
| D. AWS en San Pablo (sa-east-1) | Brasil | US$ 80 a 150 | Hay que firmar cláusulas modelo |

Fuentes de precios: fly.io/docs/about/pricing (una aplicación chica con PostgreSQL
administrada, unos US$ 44 por mes, más US$ 6,70 por la máquina de 1 GB de Gotenberg) y
hetzner.com/cloud, consultados el 2026-10-15. Desde la Argentina, Europa suma unos 200 ms
por pedido frente a San Pablo: se nota poco en estas pantallas.

## Recomendación

**A**: cumple la ley sin cláusulas, la base y las copias de seguridad las administra el
proveedor, y el costo es bajo. C es la más barata, pero deja en nuestras manos las copias de
seguridad y las actualizaciones de una base con documentos de clientes.

## Decisión

Pendiente de Carlos.
