# Guía del repositorio

## Estructura y organización de módulos

AI Radar organiza noticias, herramientas, investigaciones, repositorios y lanzamientos de IA para ayudar a decidir qué probar. Actualmente contiene una plantilla inicial de Astro; las funciones del producto están pendientes.

- `src/pages/`: rutas basadas en archivos; `index.astro` muestra la bienvenida inicial.
- `src/components/`: componentes reutilizables de Astro, como `Welcome.astro`.
- `src/layouts/`: estructuras compartidas de páginas, como `Layout.astro`.
- `src/assets/`: imágenes y SVG importados; `public/`: archivos estáticos servidos directamente.
- `astro.config.mjs` y `tsconfig.json`: configuración del framework y TypeScript estricto.

Todavía no existe un directorio de pruebas. React, la CLI `airadar`, Vercel Functions y Supabase están previstos, pero no implementados.

## Comandos de desarrollo y compilación

Usa Node.js 22.12.0 o superior y pnpm. Conserva `pnpm-lock.yaml`.

- `pnpm install`: instala las dependencias.
- `pnpm exec astro dev --background`: inicia el servidor de desarrollo en segundo plano.
- `pnpm exec astro dev status`: consulta su estado.
- `pnpm exec astro dev logs`: muestra sus registros.
- `pnpm exec astro dev stop`: detiene el servidor.
- `pnpm build`: genera el sitio de producción en `dist/`.
- `pnpm preview`: permite revisar localmente la compilación de producción.

## Estilo de código y nombres

Sigue el estilo existente: tabulaciones en el marcado Astro, dos espacios en JSON, comillas simples en las importaciones JavaScript y punto y coma. Usa PascalCase para componentes y layouts, y nombres descriptivos para las rutas. Separa la lógica de dominio reutilizable de la presentación mediante módulos JavaScript. No hay formateador ni linter configurados.

## Pruebas y validación

No existe un comando de pruebas ni un umbral de cobertura. Ejecuta `pnpm build` antes de entregar cambios de código y revisa las páginas afectadas localmente. El README propone `node:test` para el dominio y Playwright para la interfaz. Al incorporarlos, usa nombres descriptivos `*.test.js` y documenta los comandos correspondientes.

## Commits y solicitudes de cambios

El historial solo contiene “Initial commit from Astro”; no existe una convención establecida. Escribe asuntos breves en imperativo. Mantén cada solicitud de cambios enfocada, explica el problema y el comportamiento resultante, enlaza incidencias relacionadas y describe la validación realizada. Incluye capturas cuando cambie la interfaz.

## Configuración e instrucciones para agentes

Mantén las credenciales y los datos locales generados fuera de Git. Comienza con datos de prueba antes de conectar servicios externos. Distingue las funciones implementadas de las previstas. Consulta las guías pertinentes en https://docs.astro.build antes de modificar rutas, componentes, estilos, colecciones de contenido o internacionalización.

## Noticias de inteligencia artificial

Cuando el usuario pida noticias, novedades o señales de IA en este proyecto, aplica la skill [airadar-news](.agents/skills/airadar-news/SKILL.md). Busca fuentes recientes, estructura las señales según el contrato y guarda el JSON diario. Para archivar una búsqueda existente, conserva su fecha y procedencia. Respeta cualquier restricción explícita del usuario.
