# ADR-002: Cómo se firma el PDF

**Estado**: Aceptado · **Fecha**: 2026-10-15 · **Paso 3 de 001-pedido-de-firma**

## Contexto

Un mismo PDF puede llevar firmas digitales (certificado del firmante: archivo, token o
Firma Digital Remota, decisión 19) y firmas electrónicas (botón, decisión 12), en cualquier
orden. Una firma digital deja de verificar si el PDF cambia después de firmarse (ley 25.506,
art. 2: la verificación tiene que «detectar cualquier alteración»). Además:

- **La Plataforma de Firma Digital Remota no ofrece una interfaz para otras aplicaciones.**
  Su Política Única de Certificación v2.0 (AC MODERNIZACIÓN-PFDR, consultada el 2026-10-15)
  describe la firma dentro de su propia aplicación: el titular sube el PDF a
  `firmar.gob.ar/firmador` y lo baja firmado.
- **Un navegador no puede usar un token criptográfico** sin un programa instalado en la
  computadora del firmante.

## Opciones consideradas

1. **Estampar las firmas electrónicas como dibujo en las páginas.** Simple, pero cambia el
   contenido: rompe toda firma digital anterior. Descartada.
2. **Todas las firmas como firmas PAdES agregadas en actualizaciones incrementales.** Cada
   firma, digital o electrónica, se agrega al final del PDF sin tocar lo anterior; un PDF
   admite muchas firmas así y cada una sigue verificando.
3. **Integrarse con la Firma Digital Remota por API.** No hay una API pública para terceros.

## Decisión

La opción 2:

- **Antes de la primera firma**, el PDF se prepara una sola vez: campos de firma de todos
  los firmantes ya ubicados (los de la capacidad 001), y su huella SHA-256 guardada.
- **Firma electrónica**: el producto agrega una firma PAdES con **su certificado de
  aplicación** en nombre del firmante, con la apariencia de su nombre escrito, y anota en la
  firma y en la constancia quién firmó y cómo se comprobó su identidad. El certificado de
  aplicación lo emite un certificador; cuál, es la decisión de ADR-006.
- **Firma digital con archivo .p12 o .pfx**: la firma se calcula **en el navegador** del
  firmante; el archivo y su contraseña nunca salen de su dispositivo.
- **Firma digital con token o con la Firma Digital Remota**: el firmante baja el PDF
  preparado, lo firma con su programa o en `firmar.gob.ar/firmador`, y lo sube. El producto
  acepta el PDF solo si (a) lo firmado es exactamente el PDF que bajó más una firma nueva,
  (b) la firma verifica, (c) el certificado está vigente, no está revocado y encadena a la
  AC Raíz de la República Argentina (ley 25.506, arts. 9, 14 y 15).
- Cada firma lleva un **sello de tiempo** RFC 3161, para fijar cuándo se firmó.
- **Verificar** (RF-25 y la página de verificación) es recalcular la huella y verificar cada
  firma del PDF.

## Consecuencias

- Positivas: un PDF firmado se puede verificar con cualquier lector de PDF, sin el producto.
- Negativas: con token y con la Firma Digital Remota el firmante hace un paso fuera del
  producto (bajar, firmar, subir). **Esto cambia la maqueta aprobada `firmante-firmar`**, que
  mostraba un ingreso con CUIL y contraseña: se le consulta a Carlos (decisión 41 lo dejó
  para este paso).
- No cambia: lo que dice la especificación sobre qué vale cada firma.

## Cuándo revisarla

Si la Firma Digital Remota publica una interfaz para aplicaciones de terceros.

## Referencias

- Ley 25.506, arts. 2, 9, 10, 14 y 15.
- Política Única de Certificación v2.0 AC MODERNIZACIÓN-PFDR,
  <https://www.argentina.gob.ar/sites/default/files/anexo_1_resol_13_2018_sma_puc_v2.pdf>.
- ETSI EN 319 142 (PAdES).
