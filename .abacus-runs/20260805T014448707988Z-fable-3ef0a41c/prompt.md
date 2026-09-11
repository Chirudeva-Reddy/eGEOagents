# TAREA: Análisis honesto de visibilidad + estrategia de expansión para E-GEO (egeoagents)

Escribe el documento AHORA en la ruta exacta de salida indicada abajo usando tus herramientas de archivo. No planees en voz alta. No busques en la web (los datos ya están verificados e incluidos). Puedes LEER el repo local (cwd) para precisión técnica: README.md, USAGE.md, docs/, GEO-SYSTEM-BLUEPRINT.md.

Idioma del documento: español (México, tono directo, profesional, sin relleno). Extensión objetivo: 2,500–3,500 palabras.

## RUTA DE SALIDA (obligatoria, escribe el archivo completo aquí)

/home/hermes-2/Sync/mkt/egeo-expansion/2026-08-05-analisis-visibilidad-y-expansion.md

## QUÉ ES E-GEO (hechos verificados)

- Repo: github.com/mverab/eGEOagents — 147⭐, 42 forks, default branch main, muy activo (último push 2026-08-05).
- Toolkit open-source de Generative Engine Optimization (GEO) y Answer Engine Optimization (AEO): optimiza contenido para rankear/citarse en ChatGPT, Perplexity, Gemini y Claude. Basado en investigación peer-reviewed (arXiv:2511.20867).
- v2.0: CLI standalone `egeo`, runtime adapter layer, integración Claude Code, MCP server, modo `geo-loop` (loops continuos de GEO sobre workspace persistente, PR #13), evaluation harness reproducible, quality gates, soporte llms.txt, schema markup.
- Topics de GitHub ya optimizados (20 topics: aeo, ai-seo, geo, llm-seo, llms-txt, mcp, perplexity, chatgpt, gemini, claude, cli, python, etc.). Descripción del repo ya reescrita con keywords.
- README ya optimizado para AI search (PR #12, merged 2026-07-01).
- Existe docs/ con 5 archivos markdown (getting-started, how-it-works, evaluation, faq, skills-sh-playbook) PERO NO hay sitio de documentación renderizado/indexable. El campo `homepage` del repo apunta al propio GitHub, no a un sitio.
- Existe playbook para listing en skills.sh (docs/skills-sh-playbook.md).

## MEDICIÓN FRESCA DE VISIBILIDAD (2026-08-05, Perplexity Sonar API vía AIsa)

Query: "What are the best open-source generative engine optimization (GEO) tools on GitHub in 2026?"

Resultado: **E-GEO NO APARECE** (igual que en la medición del 2026-07-01, a pesar de la optimización de topics/README).

Ranking devuelto por Perplexity (fuente principal: LibHunt + roundups):

1. geo-optimizer-skill (Auriti-Labs) — 617⭐ según LibHunt. CLI + Python lib + MCP + integración Astro, scoring 0-100 con 47 métodos.
2. izak-fisher/generative-engine-optimization-tools — ~102⭐ (awesome list, exact-name match).
3. geo-lint — 37⭐.
4. xanlens — 29⭐.
5. AutoGEO (cxcscmu/AutoGEO) — repo académico.
6. open-geo — 17⭐.
7. amplifying-ai/awesome-generative-engine-optimization — 469⭐ (hub curado; Perplexity lo cita como autoridad).
8. GEO-optim/GEO — 314⭐ (repo del paper original arXiv:2311.09735).
9. getcito (ai-search-guru) — 154⭐, activo.
10. jerrytregno/Top-10-Generative-Engine-Optimization — directorio.

Otro competidor medido: AI2HU/gego — 83⭐ ("GEO tracker que agenda prompts en múltiples LLMs").

**Dato escandaloso:** E-GEO tiene 147⭐ — más que geo-lint (37), xanlens (29), open-geo (17), gego (83) e izak-fisher (102) — y aun así no es citado. El gap NO es de estrellas; es de señales externas de autoridad.

## HISTORIAL DE OPTIMIZACIÓN (ya ejecutado)

2026-07-01: topics 11→20, descripción reescrita, README GEO-optimizado (PR #12 merged). PR #66 para listar E-GEO en amplifying-ai/awesome-generative-engine-optimization fue **CERRADO SIN MERGE** (sin comentarios del maintainer) — el backlink de autoridad nunca se materializó. Nadie reintentó ni buscó listas alternativas.

## ECOSISTEMA DEL OWNER (contexto para la estrategia)

- Owner: Vera Badías / Appsclavitud — creador de contenido AI en español: YouTube @AppsclavitudPodcast (8.4k), TikTok 17k, IG 15.5k, FB 43k, X @Appsclavitud 1.1k, comunidad Skool Cofrad.IA ($19/mes, ~88 miembros). Newsletter semanal.
- Ya existe `verabadias-geo-revenue-loop` (~/Sync/mkt/): estrategia GEO/SEO con "GEO pack por oferta" (entidad canónica, queries, answer block 50-170 palabras, tabla de pricing con fecha, FAQ con objeciones reales, schema Product/SoftwareApplication/FAQ, prueba first-party) y loop DISCOVER→VERIFY→CLASSIFY→FIX→GEO-PACK→DISTRIBUTE→MEASURE→SCALE.
- Patrón probado en SlashStack (slashstack.dev): una página SEO por PR con TDD, review independiente, deploy + verificación en Google Search Console. Ese mismo loop agéntico de SEO/GEO se quiere replicar para E-GEO.
- Acceso a API de Perplexity vía AIsa (medición recurrente de ranking real disponible como loop automatizable).
- Hermes Agent (el sistema que ejecuta estos loops) con cron jobs, delegación a modelos, etc.

## ENTREGABLE: estructura obligatoria del documento

1. **Diagnóstico honesto de visibilidad** — dónde está E-GEO hoy, con los datos de arriba. Sin optimismo artificial: por qué 147⭐ no bastan; qué señal exacta le falta (citabilidad externa, no metadata interna).
2. **Análisis comparativo de competidores** — tabla + análisis: qué hace geo-optimizer-skill para tener 617⭐ y presencia en LibHunt; qué rol juegan las awesome-lists y los repos de papers; qué tienen los que aparecen que E-GEO no (presencia en directorios/listas externos, artículos de terceros, sitio propio indexable, mentions en blogs de SEO).
3. **Sitio de documentación indexable** — recomendación concreta de stack (evalúa Astro Starlight vs MkDocs Material vs Docusaurus y elige UNO con justificación para un repo Python/CLI), dominio (evalúa egeoagents.dev vs docs bajo dominio existente del owner), arquitectura de información, y qué contenido mínimo debe tener para rankear (getting started, CLI reference, comparativas "E-GEO vs X", páginas de concepto GEO/AEO, llms.txt del propio sitio).
4. **Estrategia SEO + GEO del sitio** — keywords objetivo (en-global primero), estructura de clusters, schema markup, GEO pack del producto siguiendo el patrón del revenue-loop del owner, y plan de indexación (GSC, sitemap, Bing).
5. **Loops agénticos de crecimiento** — diseña los loops automatizables concretos: (a) loop de medición Perplexity/AI-search con AIsa (query set fijo, tracking semanal de presencia, alertas); (b) loop de backlinks/autoridad (awesome-lists alternativas, LibHunt, directorios de herramientas AI, reintento del awesome-geo PR o fork propio); (c) loop de contenido (Dev.to, Hashnode, HN, Reddit r/SEO r/artificial, comparativas); (d) loop de distribución owned (YouTube del owner, newsletter, Skool, X). Para cada loop: frecuencia, input, output, KPI y gate de escalado.
6. **Monetización** — evalúa honestamente para ESTE proyecto: GitHub Sponsors, Open Core (features pro), hosted SaaS/dashboard, servicios/consulting GEO, sponsorships de la audiencia del owner. Recomienda un modelo híbrido concreto con secuencia (qué primero, qué gate lo desbloquea) y qué NO hacer todavía. Considera que el owner ya monetiza audiencia y tiene infraestructura de Stripe/Gumroad.
7. **Roadmap 30/60/90 días** — acciones ordenadas por impacto/esfuerzo, cada una con criterio de éxito medible. Incluye quick wins de la primera semana.

## REGLAS

- Español México, directo, cero relleno corporativo ("En el acelerado mundo de...", "Es importante destacar...").
- Números solo de los datos verificados arriba o del repo local. No inventes estrellas, tráfico ni métricas.
- Cada recomendación debe ser ejecutable por un sistema agéntico (no "haz marketing de contenidos" genérico — especifica el loop, la herramienta y la métrica).
- Si un dato te falta, dilo explícitamente en vez de asumirlo.
