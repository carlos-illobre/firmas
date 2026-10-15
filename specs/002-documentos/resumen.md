# Resumen: Inicio y documentos

Inicio ordena el trabajo del día; la lista y el detalle siguen cada pedido de la capacidad 001. Detalle en [spec.md](spec.md).

## Requerimientos

| ID | En una línea |
|---|---|
| RF-26 | Inicio muestra un saludo con el nombre y la fecha, y cuatro números: esperando mi acción,… |
| RF-27 | Inicio lista lo que requiere atención del abogado, ordenado por urgencia, con acceso… |
| RF-28 | Inicio muestra los documentos recientes, los próximos vencimientos y la actividad reciente… |
| RF-29 | La lista de documentos muestra, por documento: nombre, etiquetas, cliente, estado, última… |
| RF-30 | La lista se filtra por estado (todos, esperando mi acción, esperando a otros, completados,… |
| RF-31 | Un buscador en todas las pantallas encuentra documentos, clientes y plantillas por nombre |
| RF-32 | El detalle de un documento muestra el nombre, el estado, el tipo, el cliente, el… |
| RF-33 | Desde el detalle se puede recordar, descargar, archivar y cancelar el proceso de firma |
| RF-34 | Un documento se puede archivar y desarchivar; archivado no aparece en «Todos» |
| RF-35 | Cada documento tiene un cliente, un responsable del estudio y etiquetas opcionales |
| RNF-05 | Inicio, la lista y el detalle se usan completos en el celular y en la computadora |

## Lo que más pesa

- Inicio cuenta y lista lo que requiere atención.
- La lista filtra por estado y por cliente; el buscador está en todas las pantallas.
- Archivar saca un documento de «Todos».

## Decisiones de Carlos

18 de [decisiones-de-negocio.md](../../docs/decisiones-de-negocio.md).

## Lo que frena la aprobación

- Las preguntas de esta capacidad en [preguntas-abiertas.md](../preguntas-abiertas.md).
