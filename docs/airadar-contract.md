# Contrato diario de AI Radar

Versión: `1.0.0`. Esquema: [airadar-daily.schema.json](../schemas/airadar-daily.schema.json), JSON Schema 2020-12.

## Ubicación y fechas

Guarda cada búsqueda diaria en `data/searches/YYYY-MM-DD.json`, con UTF-8 y dos espacios de indentación. `date` es la fecha de búsqueda en `America/Bogota`; `source.published_date` es la fecha de publicación o actualización de cada noticia. No reemplaces un registro existente sin revisar su contenido. La carpeta de búsquedas está excluida de Git.

## Campos obligatorios

- `schema_version`, `date`, `timezone`, `language`: versión y contexto del registro.
- `search`: petición original, método, consultas ejecutadas y notas sobre selección o acceso.
- `signals`: una o más señales; el archivo de esta búsqueda contiene cinco.
- Cada señal incluye `id` estable, `title`, `category`, `source`, `evidence`, `impact`, `action` y `status`.
- `source`: nombre, URL HTTPS, fecha, tipo primario/secundario y acceso por página completa o extracto del buscador.
- `evidence`: resumen factual, limitaciones y nivel de verificación.
- `impact`: nivel `alto`, `medio` o `bajo` y justificación editorial.
- `action`: acción concreta y ejecución `pendiente`, `en_curso`, `completada` o `descartada`.

## Verificación y estados

`fuente_consultada` indica acceso al texto o extracto; no implica validación independiente. `corroborada` requiere confirmación en otra fuente independiente y `reproducida` una comprobación propia documentada. Registra esa evidencia en el resumen y las notas.

El estado editorial puede ser `revisar_prioridad`, `candidato_prueba`, `seguir_investigacion`, `revision_programada`, `monitorear` o `descartada`. Es independiente de la ejecución de la acción.

## Validación

Valida el JSON contra el esquema con un validador compatible con JSON Schema 2020-12 que compruebe formatos. Además, verifica fechas reales, IDs únicos por registro, coincidencia entre el nombre del archivo y `date`, y ausencia de publicaciones posteriores a la búsqueda. No atribuyas pruebas ejecutadas ni confianza numérica sin evidencia. Las versiones incompatibles requieren actualizar `schema_version`.
