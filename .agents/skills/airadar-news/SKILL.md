---
name: airadar-news
description: Busca noticias recientes de inteligencia artificial, conviértelas en señales de AI Radar y guarda un JSON diario según el contrato del repositorio. Úsala cuando el usuario pida noticias, novedades o señales de IA en este proyecto, o solicite guardar una búsqueda existente.
---

# Noticias y señales de AI Radar

## Alcance

Entrega señales útiles para desarrolladores y creadores de productos, en español. Por defecto selecciona cinco noticias y guarda la búsqueda diaria; respeta cantidades, temas, fechas y restricciones indicadas por el usuario. Si solo pide guardar una búsqueda existente, conserva sus resultados y su fecha sin presentarla como una búsqueda nueva.

Antes de estructurar datos, lee [el contrato](../../../docs/airadar-contract.md) y [el esquema](../../../schemas/airadar-daily.schema.json) desde la raíz del repositorio. Si faltan, crea un contrato versionado que cubra fuente, evidencia, impacto, acción y estado; no inventes una CLI o integraciones como si existieran.

## Buscar y seleccionar

- Determina la fecha actual en `America/Bogota`. Para noticias recientes, comienza por los últimos siete días y amplía el periodo si faltan señales relevantes; informa del intervalo usado.
- Busca en internet y registra las consultas realmente ejecutadas. Prioriza anuncios oficiales, artículos científicos, documentación y reportes originales. Usa medios fiables para contexto y contraste.
- Comprueba fecha de publicación, fecha del acontecimiento y disponibilidad real. Una actualización de un estudio antiguo no convierte sus resultados en un descubrimiento nuevo.
- Agrupa coberturas del mismo acontecimiento en una señal. Selecciona por novedad, impacto, evidencia y posibilidad de actuar; distingue lanzamientos, versiones preliminares y promesas.
- Si no puedes reunir la cantidad solicitada con evidencia suficiente, entrega las verificadas y explica la limitación. No completes con rumores presentados como hechos.

## Estructurar las señales

Sigue los campos y enumeraciones del esquema vigente. Usa IDs descriptivos y estables; registra categoría, título, fuente y fecha.

En `evidence`, resume los hechos y sus límites. Identifica afirmaciones del proveedor, muestras pequeñas y resultados sin validar. Indica si consultaste la página completa o únicamente un extracto; no atribuyas al artículo completo lo que no leíste. `fuente_consultada` no equivale a corroboración independiente. Usa `corroborada` o `reproducida` solo con evidencia documentada.

En `impact`, justifica a quién afecta y por qué. En `action`, propone un siguiente paso concreto y conserva `pendiente` si no se ejecutó. El estado editorial clasifica qué hacer con la señal y es independiente del estado de ejecución. No inventes puntuaciones numéricas de confianza.

## Guardar y verificar

Guarda JSON UTF-8 con dos espacios en `data/searches/YYYY-MM-DD.json`. Incluye versión, fecha de búsqueda, zona horaria, idioma, petición original, método, consultas reales y notas. Explica en las notas el periodo usado, las restricciones y si se archivó una búsqueda anterior.

Si ya existe un registro diario, léelo primero: conserva sus señales y procedencia, añade solo acontecimientos distintos y registra consultas adicionales. No borres ni sustituyas silenciosamente resultados previos. Ante una corrección factual, conserva la explicación del cambio en las notas.

Valida contra JSON Schema 2020-12 con comprobación de formatos usando herramientas disponibles. Revisa además fechas reales, IDs únicos, coincidencia entre fecha y nombre del archivo y publicaciones no posteriores a la búsqueda. Si no hay validador, verifica explícitamente todas las restricciones usadas por el esquema y declara el alcance de esa comprobación; no afirmes una validación completa de JSON Schema.

## Entregar

Muestra las señales con fuente enlazada, evidencia, impacto, acción y estado; aclara que las valoraciones son editoriales. Enlaza el JSON guardado y resume la validación. Si la carpeta está ignorada por Git, indica que queda local. No publiques, hagas commits ni subas archivos a un remoto salvo que el usuario lo solicite.
