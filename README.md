# Atlas de Malacandra

Escena 3D interactiva del mundo y los habitantes de *Más allá del planeta silencioso*, el primer libro de la Trilogía Cósmica de C. S. Lewis.

**Tú eliges en qué capítulo vas** (1 a 22) y el atlas muestra solo lo que Ransom sabe en ese punto. Al avanzar, el mapa crece, aparecen lugares y criaturas, y las fichas cambian de nombre y de texto. Avanzar más allá de lo leído pide confirmación, para no arruinarte el libro.

## Qué hay

- **Selector de capítulo**, recordado en el navegador. Un punto dorado marca lo nuevo de cada capítulo y un marcador indica dónde está Ransom.
- **El mundo**, en varias escenas que se desbloquean con la lectura. Cada lugar tiene una ficha con su descripción y sus capítulos.
- **Los habitantes**, en fila y a escala real con una regla en metros. Lo que el lector aún no ha visto aparece como silueta o no aparece.
- Aviso: el código fuente contiene todo el libro. Si no quieres spoilers, usa la página y no leas `malacandra.html`.

## Cómo está hecho

Toda la escena vive en un solo archivo, `malacandra.html`:

| Parte | Tecnología |
| --- | --- |
| Estructura y panel | HTML y CSS a mano, sin framework |
| Escena 3D | [Three.js](https://threejs.org) r128 (WebGL), cargado desde CDN |
| Cámara | `OrbitControls` de Three.js |
| Relieve | Función de altura con ruido procedural, calculada al cargar |
| Modelos | Geometría primitiva (esferas, conos, cilindros, sólidos de revolución) armada por código |
| Bosque, agujas, masas rosadas | Mallas instanciadas (`InstancedMesh`) |
| Etiquetas | Botones HTML proyectados desde coordenadas 3D |

No hay paso de compilación, ni dependencias que instalar, ni archivos de modelos o texturas. Todo se genera en el navegador.

## Notas

- `malacandra.html` es un fragmento sin `<!doctype>` ni `<head>`, porque se publica como artefacto de Claude y la plataforma le agrega ese envoltorio.
- `index.html` descarga ese fragmento y lo envuelve en un documento completo. Es la página de entrada en GitHub Pages. Necesita servirse por http, no abrirse como archivo. Para verla en tu máquina: `python3 -m http.server` y abre `http://localhost:8000`.
- Las figuras son una interpretación de las descripciones del libro, no ilustraciones oficiales.
- Los textos se escribieron de memoria. Alguna referencia de capítulo puede estar corrida por uno.
