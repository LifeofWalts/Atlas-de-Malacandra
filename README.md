# Atlas de Malacandra

Escena 3D interactiva del mundo y los habitantes de *Más allá del planeta silencioso*, el primer libro de la Trilogía Cósmica de C. S. Lewis.

Se construye de a poco, al ritmo de la lectura. **Hoy cubre hasta el capítulo 15** y no adelanta nada de lo que viene después.

## Qué hay

- **El mundo**: el harandra (meseta fría, casi sin aire) cortado por un handramit (cañón con agua tibia, bosque púrpura y vida). Incluye la nave y la cabaña, la aldea de los hrossa, la caza del hnakra, el rebaño de los sorns y la torre de Augray con su camino. El cielo se oscurece al subir la cámara.
- **Los habitantes**: hross, sorn, eldil, hnakra, Ransom, Weston y Devine, en fila y a escala real con una regla en metros. Los pfifltriggi son solo una silueta porque el lector aún no los ha visto.
- Cada lugar y cada criatura tiene una ficha con su descripción y los capítulos donde aparece.

## Cómo está hecho

Todo vive en un solo archivo, `malacandra.html`:

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
- Las figuras son una interpretación de las descripciones del libro, no ilustraciones oficiales.
- Los textos se escribieron de memoria. Alguna referencia de capítulo puede estar corrida por uno.
