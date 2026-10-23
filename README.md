# ProteIA

Aprende Estructura y Función de las Proteínas practicando: secuencia, 3D, plegamiento, enzimas, examen y casos. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/proteia/

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23602305.svg)](https://doi.org/10.5281/zenodo.23602305)

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

Seis formas de practicar, todas accesibles sin clave de IA salvo donde se indica:

- **Secuencia (U1).** Para cualquier secuencia (código de una letra o FASTA), el código calcula masa media, composición, carga a cualquier pH y curva de carga, punto isoeléctrico, ε280 (con cistinas y con Cys reducidas), GRAVY, perfil de hidropatía de Kyte-Doolittle con segmentos transmembrana candidatos y rueda helicoidal con momento hidrofóbico. Un botón busca en el Protein Data Bank estructuras con secuencia parecida (práctica de identificación a partir de una secuencia parcial). Incluye un **reto de secuenciación** con fragmentos trípticos y quimotrípticos distintos por estudiante: cualquier secuencia que reproduzca los mismos fragmentos se da por buena, y **tarjetas de repaso** con repetición espaciada (30 del temario más las creadas desde los apuntes propios).
- **Estructura 3D (U2-U5).**
  - *Constructor φ/ψ:* construye una cadena con geometría estándar a partir de φ y ψ (o pulsando en el mapa) y el código mide residuos por vuelta, elevación, paso, sentido de la hélice, enlaces de hidrógeno i→i+3, i→i+4 e i→i+5 y choques estéricos. El fondo del mapa de Ramachandran se calcula en el navegador con un modelo de esferas duras. Seis retos (hélice α, 3₁₀, hebra β, poliprolina II, choque estérico, hélice levógira) los comprueba el código.
  - *Visor de estructuras* con 3Dmol.js: tres estructuras incluidas que funcionan sin red (1CRN, 1LCD con DNA, fibra amiloide 2BEG), una visita guiada de 21 entradas por unidad (mioglobina, hemoglobina, GCN4, GFP, barril TIM, porina, tripsina-BPTI, proteasa del VIH, dedos de zinc, modelos de AlphaFold…), cualquier código PDB, cualquier código UniProt (modelo de AlphaFold DB, coloreado por pLDDT) o un fichero `.pdb` propio. Sobre el fichero, el código calcula φ/ψ y el Ramachandran de la estructura (clic en un punto → residuo en 3D), estructura secundaria, puentes disulfuro (Sγ–Sγ) contrastados con SSBOND, puentes salinos, ligandos y residuos a menos de 4 Å, cadenas idénticas (estequiometría), interfaces entre cadenas, residuos que tocan el DNA y radio de giro; φ/ψ se exportan en CSV.
  - *Proteína problema:* preguntas sobre la estructura abierta (cadenas, disulfuros, % de hélice, ligandos, residuos con φ positivo, ácidos nucleicos) cuya respuesta calcula el código a partir del propio fichero; sirve con cualquier estructura.
- **Laboratorio numérico (U1, U5, U6).** Ocho tipos de problema con datos distintos por estudiante a partir de su nombre o código: carga y punto isoeléctrico, ε280 y Lambert-Beer, estabilidad por desnaturalización química (extrapolación lineal), desnaturalización térmica, análisis de valores Φ, Michaelis-Menten (ajuste de Lineweaver-Burk y kcat), inhibición competitiva (Ki) y unión cooperativa de Hill. La solución la calcula el código y, cuando la respuesta es incorrecta, se recalcula con los errores típicos declarados (olvidar los extremos, grados Celsius, log decimal, cociente invertido, n = 1…) para explicar el fallo.
- **Simulacro de examen.** 42 preguntas de teoría tipo test repartidas por las seis unidades, corregidas por el código con la clave, y seis preguntas cortas de desarrollo. **No pone nota ni aplica la penalización del examen real**: muestra aciertos, fallos, preguntas en blanco y la explicación de cada una; en el desarrollo, qué conceptos aparecen (sin IA) o un feedback detallado con IA.
- **Casos (U3-U6).** Seis casos (hemoglobina S, enzima termoestable, cuerpos de inclusión, tríada catalítica, hemoglobina fetal y 2,3-BPG, identificación de una secuencia parcial) con pistas graduadas, enlace a la estructura y un tutor socrático.
- **Mis apuntes** (con IA): preguntar a los apuntes propios o generar tarjetas, siempre con cita literal comprobada contra el material.
- **Progreso**: aciertos recientes por unidad, retos conseguidos y exportación a Word, CSV y JSON (e importación para continuar en otro ordenador).

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude. La clave se guarda solo en el navegador. No hace falta servidor. La IA solo comenta y pregunta: no calcula ni pone notas.

## Privacidad

Todo se procesa y se guarda en el navegador (IndexedDB): progreso, respuestas, apuntes y la clave de IA. Los cálculos de secuencia, geometría, Ramachandran, análisis de estructuras, laboratorio, la corrección del test y la verificación de las citas los hace el código, sin red.

Solo salen datos hacia el proveedor de IA si se usan las funciones con IA: las respuestas de desarrollo, los mensajes al tutor o los apuntes, con correos, documentos de identidad y teléfonos enmascarados y tras un aviso previo con una muestra de lo que sale. Al abrir una estructura en línea se descargan ficheros públicos de files.rcsb.org o alphafold.ebi.ac.uk, y la búsqueda por secuencia envía solo la secuencia a search.rcsb.org. El fichero JSON exportado no contiene la clave de API.

## Límites

- El contenido base (tarjetas, test, preguntas cortas, casos, visita guiada) es material de repaso elaborado a partir del temario de la guía docente: puede contener errores u omisiones. Mandan el profesorado, la guía docente y los guiones de prácticas.
- El mapa de Ramachandran de fondo es un modelo didáctico de esferas duras (límites de contacto de Ramachandran y Sasisekharan, con C…C relajado a 2,9 Å) sobre geometría estándar; los mapas estadísticos de estructuras reales son algo distintos. El constructor usa φ y ψ iguales en todos los residuos.
- La estructura secundaria procede de los registros HELIX/SHEET del fichero; si no los tiene, se estima por tramos de φ/ψ (no es DSSP). Los puentes salinos se detectan por distancia (≤ 4 Å) entre Asp/Glu y Lys/Arg.
- Solo se leen ficheros en formato PDB (primer modelo, primera conformación alternativa); las estructuras muy grandes que solo existen en mmCIF no se pueden abrir.
- El pI y la carga usan los pKa de referencia de EMBOSS: otras herramientas (p. ej., ProtParam) pueden dar valores algo distintos.
- El simulacro no pone nota ni reproduce la penalización del examen real, y no sustituye la corrección del profesorado. Si la IA cuela una calificación, el código la elimina.
- El feedback de la IA solo se muestra cuando su cita literal aparece de verdad en la respuesta del estudiante; lo que no se puede comprobar se marca como «sin cita verificada».
- El tutor de los casos no recibe la solución y el código filtra sus frases, pero el filtro es una lista de términos: puede dejar pasar una formulación inesperada.
- El visor 3D necesita WebGL. Las descargas del PDB, de AlphaFold DB y la búsqueda por secuencia dependen de esos servicios externos.

Probado con IA simulada de los tres proveedores (incluida una IA que inventa citas y cuela una nota), con el PDB, AlphaFold DB y la búsqueda por secuencia simulados, en español, inglés y portugués, en escritorio y móvil. Los cálculos estructurales se contrastaron con Biopython (φ/ψ de la crambina). No se ha probado con una clave de API real ni contra los servicios reales del PDB y AlphaFold DB.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche) y María Dolores Herranz López (Universidad Miguel Hernández de Elche).

Sigue el temario, las prácticas y el formato de examen de la guía docente 2026-2027 de Estructura y Función de las Proteínas (asignatura 1409, Grado en Biotecnología, UMH), cuya responsable es María Dolores Herranz López. Diseño basado en VirologIA y FarmacoforIA.

El visor 3D usa [3Dmol.js](https://3dmol.org) (Rego y Koes, 2015; licencia BSD-3-Clause), incluido en el fichero. Las estructuras 1CRN, 1LCD y 2BEG incluidas proceden del [Protein Data Bank](https://www.wwpdb.org) (datos de dominio público, CC0).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573) · María Dolores Herranz López [0000-0002-1819-7978](https://orcid.org/0000-0002-1819-7978)

## Cómo citar

Borrás Rocher, F. y Herranz López, M. D. (2026). *ProteIA* (v1.0.0) [Software]. DOI: [10.5281/zenodo.23602305](https://doi.org/10.5281/zenodo.23602305)

## Licencia

MIT. Véase [LICENSE](LICENSE). 3Dmol.js se distribuye bajo su propia licencia BSD-3-Clause.
