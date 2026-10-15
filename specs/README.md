# Especificaciones de Firmas

La entrada al proyecto: de qué se trata y dónde está escrito cada requerimiento. Con lo que
hay en esta carpeta, alguien que nunca vio el código tiene que poder construir de nuevo una
aplicación que cumpla todos los requerimientos, funcionales y no funcionales.

**Acá no se dice si algo está hecho.** Eso depende del código de hoy y vive en
[proyecto/estado.yml](../proyecto/estado.yml).

## De qué se trata

Firma de documentos para abogados en la Argentina: un producto como DocuSign, pensado para
el mercado argentino y para el trabajo de un estudio jurídico. Qué es y para quién, en
[docs/PRODUCTO.md](../docs/PRODUCTO.md).

## Cómo está organizado

| Dónde | Qué tiene |
|---|---|
| [La constitución](../.specify/memory/constitution.md) | Lo que no se negocia y el flujo de trabajo |
| `001` en adelante | Una por capacidad: `resumen.md`, `spec.md`, `ux.md` y, donde hay datos, `data-model.md` |
| [preguntas-abiertas.md](preguntas-abiertas.md) | Lo que todavía no está decidido |

## Requerimientos

Todavía ninguno. Salen del paso 1 de la primera capacidad, con las respuestas de Carlos a
las [preguntas abiertas](preguntas-abiertas.md). Cada uno se agrega acá en una tabla
`| ID | Requerimiento | Especificación |`, agrupado por capacidad.
