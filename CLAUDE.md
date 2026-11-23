# Atlas de Malacandra

Escena 3D interactiva (Three.js r128, un solo archivo: `malacandra.html`) del mundo de la Trilogía Cósmica de C. S. Lewis. Crece al ritmo de lectura del usuario.

## Reglas del proyecto

- **Sin spoilers.** El contenido llega hasta el capítulo 15 del primer libro. Antes de agregar algo, pregunta en qué capítulo va el usuario y no muestres ni describas nada posterior. Lo que aún no ha visto se marca como bloqueado o silueta.
- **Delegación.** Planea con el modelo principal y ejecuta los cambios amplios con un subagente Opus en esfuerzo medio. El modelo principal revisa capturas e integra. Los ajustes pequeños se hacen directo, sin delegar.
- **Idioma y tono.** Todo el texto de la página va en español, frases cortas, sin rayas largas. Explica desde primeros principios (por qué el aire se junta abajo, por qué todo es alto y delgado).
- **Fidelidad.** Las descripciones se basan en el texto de Lewis, parafraseadas, sin citas largas.

## Notas técnicas

- `malacandra.html` es un fragmento sin doctype ni head: se publica como artefacto de Claude (https://claude.ai/artifact/GqVeAjihf5xZrhFa8NPHcq) y la plataforma lo envuelve. Republicar desde la misma ruta conserva la URL.
- Scripts externos solo desde cdnjs y jsDelivr, con versión exacta.
- En la sesión en la nube los CDN están bloqueados. Para probar: `npm pack three@0.128.0`, y en Playwright interceptar las URLs de `three.min.js` y `OrbitControls.js` para servir las copias locales. Lanzar Chromium con `--use-gl=swiftshader --enable-unsafe-swiftshader`.
- `window.__atlas.select(id)` y `window.__atlas.setMode('world'|'gal')` permiten mover la escena desde scripts de prueba.
