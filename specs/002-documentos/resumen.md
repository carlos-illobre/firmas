# Resumen: Inicio y documentos

Inicio ordena el trabajo del día; la lista y el detalle siguen cada pedido de la capacidad 001. Detalle en [spec.md](spec.md).

## Requerimientos

| ID | En una línea |
|---|---|
| RF-31 | Inicio muestra un saludo con el nombre y la fecha, y cuatro números: esperando mi acción,… |
| RF-32 | Inicio lista lo que requiere atención del abogado, ordenado por urgencia, con acceso… |
| RF-33 | Inicio muestra los documentos recientes, los próximos vencimientos y la actividad reciente… |
| RF-34 | La lista de documentos muestra, por documento: nombre, etiquetas, cliente, estado, última… |
| RF-35 | La lista se filtra por estado (todos, esperando mi acción, esperando a otros, completados,… |
| RF-36 | Un buscador en todas las pantallas encuentra documentos, clientes y plantillas por nombre |
| RF-37 | El detalle de un documento muestra el nombre, el estado, el tipo, el cliente, el… |
| RF-38 | Desde el detalle se puede recordar, descargar, archivar, cancelar el proceso de firma y… |
| RF-38a | El editor cambia todo lo referente a la firma de un pedido: los destinatarios, el orden, el… |
| RF-39 | Un documento se puede archivar y desarchivar; archivado no aparece en «Todos» |
| RF-40 | Cada documento tiene uno o más firmantes y un responsable del estudio; el cliente y las… |
| RNF-05 | Inicio, la lista y el detalle se usan completos en el celular y en la computadora |

## Lo que más pesa

- Inicio cuenta y lista lo que requiere atención.
- La lista filtra por estado y por cliente; el buscador está en todas las pantallas.
- Archivar saca un documento de «Todos».
- El cliente es opcional; los firmantes, no.
- El editor cambia lo de la firma, salvo lo de quien ya firmó.

## Decisiones de Carlos

18, 30 y 31 de [decisiones-de-negocio.md](../../docs/decisiones-de-negocio.md).

## Estado de la especificación

Aprobada por Carlos el 2026-10-15, con sus supuestos (decisión 39).
