# ADR-004: Pruebas y compuertas de calidad

**Estado**: Aceptado · **Fecha**: 2026-10-15 · **Paso 3 de 001-pedido-de-firma**

## Contexto

La constitución pide una prueba por escenario, escrita antes del código, y que la meta de
cobertura y las compuertas se fijen en un ADR antes del primer código (principio V).

## Decisión

- **Vitest** para las pruebas de unidad y de integración (con una PostgreSQL de prueba).
- **Playwright** para las pruebas de punta a punta, en computadora (1366 px) y en celular
  (390 px); las de pantalla comparan contra la maqueta aprobada con capturas.
- Cada prueba de escenario lleva el nombre del escenario en su título (`001-E08`).
- **Cobertura mínima de 80 % de líneas** en el código de dominio (reglas, firma, estados del
  pedido) y de 60 % en el resto. No se baja.
- Compuertas del CI, todas obligatorias: `tsc` estricto sin errores, ESLint sin errores,
  las pruebas, la cobertura, `tests/trazabilidad.mjs` y `tests/compuerta.mjs revisar`.
- Los PDF de prueba se generan en las pruebas con textos inventados (principio VI).

## Opciones consideradas

Jest en lugar de Vitest (más lento y peor con ESM); Cypress en lugar de Playwright
(Playwright ya está en el entorno y prueba varios navegadores).

## Cuándo revisarla

Si la cobertura de dominio se vuelve imposible de sostener por una razón que no sea falta de
pruebas.
