# ADR-001: Stack de la aplicación

**Estado**: Aceptado · **Fecha**: 2026-10-15 · **Paso 3 de 001-pedido-de-firma**

## Contexto

Firmas es una aplicación web con dos clases de usuarios: el estudio, con cuenta, y los
firmantes, sin cuenta y casi siempre desde el celular. Hay trabajo en segundo plano
(recordatorios, vencimientos, conversiones de Word, envíos) y manejo de PDF y de
criptografía (firmas PAdES, huellas, verificación de certificados). El entorno de la nube ya
instala pnpm y Playwright (docs/operacion/sesiones-en-la-nube.md). La constitución pide no
construir nada «para después» (principio VII).

## Opciones consideradas

1. **TypeScript de punta a punta: Next.js (App Router) con PostgreSQL.** Una sola
   aplicación sirve las pantallas y la API; el mismo lenguaje en el navegador y en el
   servidor, lo que importa para firmar con el archivo del certificado en el navegador
   (ADR-002).
2. **API aparte (NestJS o Fastify) y una SPA en React.** Dos proyectos, dos despliegues y un
   contrato entre los dos para un solo equipo: más piezas sin una necesidad que las pida.
3. **Django o Rails.** Muy productivos para pantallas de administración, pero la firma en
   el navegador obliga a escribir igual la parte criptográfica en TypeScript: dos lenguajes.

## Decisión

La opción 1:

- **Node 22 LTS y TypeScript** en modo estricto, con **pnpm**.
- **Next.js** con App Router: pantallas renderizadas en el servidor y acciones del servidor;
  las pantallas del firmante también funcionan con conexión lenta.
- **PostgreSQL 16** con **Drizzle ORM** y migraciones versionadas.
- **pg-boss** para los trabajos en segundo plano, sobre la misma base: sin un servicio de
  colas aparte.
- **Almacenamiento de archivos compatible con S3** para los PDF, las fotos del DNI y las
  constancias, cifrados en reposo.
- Estilos con **CSS propio con los tokens del sistema visual**, sin librería de
  componentes; animaciones solo con `transform` y `opacity` (constitución, principio IV).

## Consecuencias

- Positivas: un lenguaje, un despliegue de la aplicación y un proceso de trabajos; la
  criptografía del navegador y del servidor comparte código.
- Negativas: Next.js cambia seguido; se fija la versión y se actualiza a propósito.
- No cambia: las especificaciones; si el stack se rehace, solo se reinicia
  `proyecto/estado.yml`.

## Cuándo revisarla

Si los trabajos en segundo plano superan lo que aguanta la base (miles por minuto), o si
aparece una aplicación nativa para celular.
