# Atlas de Malacandra

Atlas 3D interactivo (Three.js r128, un solo archivo: `malacandra.html`) de *Más allá del planeta silencioso*, primer libro de la Trilogía Cósmica de C. S. Lewis. El lector elige su capítulo y el atlas revela solo hasta ahí.

## Reglas del proyecto

- **Sin spoilers.** La página contiene todo el primer libro (22 capítulos), pero solo revela hasta el capítulo que el lector elige en el selector. Todo contenido nuevo lleva su capítulo (`from`) y nunca menciona algo posterior. En el chat, los commits y los PR no describas nada posterior al capítulo que el usuario dice llevar (pregúntalo; la última vez iba en el 15). El usuario aceptó que el código fuente contiene spoilers.
- **Delegación.** Planea con el modelo principal y ejecuta los cambios amplios con un subagente Opus en esfuerzo medio. El modelo principal revisa capturas e integra. Los ajustes pequeños se hacen directo, sin delegar.
- **Idioma y tono.** Todo el texto de la página va en español, frases cortas, sin rayas largas. Explica desde primeros principios (por qué el aire se junta abajo, por qué todo es alto y delgado).
- **Fidelidad.** Las descripciones se basan en el texto de Lewis, parafraseadas, sin citas largas.

## Notas técnicas

- `malacandra.html` es un fragmento sin doctype ni head: se publica como artefacto de Claude (https://claude.ai/artifact/GqVeAjihf5xZrhFa8NPHcq) y la plataforma lo envuelve. Republicar desde la misma ruta conserva la URL.
- `index.html` es solo un envoltorio para GitHub Pages: descarga `malacandra.html` y lo escribe dentro de un documento con doctype y viewport. Los cambios de contenido van siempre en `malacandra.html`.
- Scripts externos solo desde cdnjs y jsDelivr, con versión exacta.
- En la sesión en la nube los CDN están bloqueados. Para probar: `npm pack three@0.128.0`, y en Playwright interceptar las URLs de `three.min.js` y `OrbitControls.js` para servir las copias locales. Lanzar Chromium con `--use-gl=swiftshader --enable-unsafe-swiftshader`.
- Estructura: `CH` es el capítulo visible. `PLACES` y `FOLK` son ítems `{ id, from, scene?, v:[versiones con su from] }`; `ver(item)` da la versión vigente. Los objetos 3D se registran con `gate(obj, from, to)` o dentro de `layerAt(from, to)`, y `applyChapter()` aplica todo. Hay tres escenas bajo "El mundo" (`tierra`, `cielo`, `mal`) más la galería.
- Ganchos de prueba en `window.__atlas`: `setChapter(n)`, `setScene(id)`, `setMode('world'|'gal')`, `select(id)`, `stats()`, `cam()`, `look(p, t)`.
- Los planes de contenido por capítulo se escriben fuera del repo y se pasan directo al subagente.
