# ADR-003: Conversión de Word a PDF

**Estado**: Aceptado · **Fecha**: 2026-10-15 · **Paso 3 de 001-pedido-de-firma**

## Contexto

Un Word se convierte a PDF antes de enviarse, y lo que se firma es el PDF (decisión 14). La
redacción desde cero y las plantillas también terminan en PDF (capacidad 003).

## Opciones consideradas

1. **Gotenberg** (LibreOffice sin pantalla, como servicio HTTP en un contenedor aparte).
   Fiel con los Word comunes, gratuito y sin mandar el documento a terceros.
2. **Un servicio externo de conversión.** Más fiel con formatos raros, pero el documento,
   amparado por el secreto profesional, saldría a un tercero.
3. **Convertir dentro del proceso de Node.** No hay una librería que convierta Word con
   fidelidad.

## Decisión

Gotenberg, en un contenedor propio, sin acceso a internet, llamado por un trabajo en segundo
plano. El HTML de las plantillas y de «crear desde cero» se convierte con su motor de
Chromium.

## Consecuencias

- Positivas: el documento no sale de la infraestructura del producto.
- Negativas: un contenedor más para desplegar; algunos Word con fuentes raras se ven
  distinto, por eso el solicitante revisa el PDF antes de seguir (RF-02).

## Cuándo revisarla

Si las quejas por la conversión pasan de unas pocas por mes.
