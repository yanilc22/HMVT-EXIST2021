# HMVT-2026
Hybrid Multivector Text Representation for Digital Violence Detection.
Material suplementario para tesis doctoral y preparación de artículo científico
Estado: consolidación documental de experimentos; no es una nueva ejecución ni validación de métricas.
Resumen
Este repositorio organiza las implementaciones de clasificación de violencia digital y sexismo en publicaciones de X/Twitter asociadas con EXIST2021 que aparecen en seis cuadernos de trabajo. Se conservan los enfoques de clasificación binaria, clasificación multiclase, representaciones tradicionales, HMT/HMVT y sus variantes, optimizaciones y ablaciones, comparaciones estadísticas, evaluaciones con datos en inglés y estimación geolingüística cuando están implementadas en los originales.

La consolidación preserva las 70 implementaciones semánticamente distintas; elimina 30 ocurrencias redundantes y retira comentarios del código mediante análisis léxico, sin reescribir por iniciativa propia la lógica de los modelos. Las salidas embebidas se retiraron del maestro para que sea manejable; los originales siguen siendo el registro primario de ejecuciones previas.
Archivos del paquete
Archivo	Descripción
EXIST2021_MAESTRO_TESIS.ipynb	Notebook maestro, organizado por familias de experimentos, con 70 implementaciones únicas y procedencia por celda
CATALOGO_EXPERIMENTOS.csv	Índice trazable de ID, versiones, fuente, apariciones y estado sintáctico
README.md	Esta ficha metodológica y de reproducibilidad


Inventario de experimentos
Línea experimental	Implementaciones únicas
01. Clasificación binaria	7
02. Clasificación multiclase	32
03. HMVT y optimización avanzada	7
04. Experimentos en inglés	2
05. Geolingüística y análisis espacial	14
06. Reportes y visualización	8


Índice de versiones identificadas
Versión identificada	Experimentos que la mencionan
V1	EXP-001, EXP-002, EXP-003, EXP-004, EXP-005, EXP-007, EXP-008, EXP-009, EXP-010 … (58 apariciones)
V2	EXP-001, EXP-002, EXP-003, EXP-004, EXP-007, EXP-018, EXP-023, EXP-024, EXP-025 … (31 apariciones)
V3	EXP-001, EXP-002, EXP-003, EXP-004, EXP-006, EXP-007, EXP-022, EXP-023, EXP-024 … (32 apariciones)
V4	EXP-001, EXP-002, EXP-003, EXP-004, EXP-006, EXP-007, EXP-038, EXP-039, EXP-040 … (26 apariciones)
V5	EXP-038, EXP-039, EXP-040, EXP-041, EXP-042, EXP-047 (6 apariciones)
V6	EXP-006 (1 apariciones)
V6a	EXP-006, EXP-038, EXP-039, EXP-040, EXP-041, EXP-042, EXP-047 (7 apariciones)
V6b	EXP-006, EXP-038, EXP-039, EXP-040, EXP-041, EXP-042, EXP-047 (7 apariciones)
V6c	EXP-006, EXP-038, EXP-039, EXP-040, EXP-041, EXP-042, EXP-047 (7 apariciones)
V6d	EXP-006, EXP-038, EXP-039, EXP-040, EXP-041, EXP-042, EXP-047 (7 apariciones)
V7	EXP-045 (1 apariciones)
V8	EXP-046 (1 apariciones)


Este índice indica que la versión se menciona en el código y no certifica su implementación completa ni que todas las versiones se ejecuten por separado. Las variantes V6a, V6b, V6c y V6d se listan individualmente. Para citar una definición de modelo, consulte la celda correspondiente y su origen.
Fuentes primarias consolidadas
- Día_19_Octubre_2026.ipynb
- 21_Octubre.ipynb
- 27_Octubre.ipynb
- Reportes_tesis.ipynb
- Reportes_tesis (1).ipynb
- Untitled7.ipynb
Las celdas repetidas se identificaron comparando la estructura sintáctica de Python (AST), lo que permite eliminar copias que difieran solo en espacios o comentarios. Los experimentos con cambios efectivos de código se preservan, aunque sus objetivos o encabezados sean similares. Por ello, una misma etiqueta V1/V2/etc. puede aparecer en varias implementaciones distintas: no se sustituyeron versiones diferentes por la última.
Protocolo y variables de investigación
1. Objetivos de clasificación
Binaria: distingue publicaciones sin violencia/sexismo de las que presentan violencia/sexismo, según la definición de etiquetas utilizada por cada script original.
Multiclase reestructurada: clases 0 = No violencia, 1 = Misoginia, 2 = Acoso, 3 = Violencia sexual cuando el código trabaja con la taxonomía de cuatro clases del conjunto reestructurado.
Inglés: algunos scripts trabajan con el Task 1 o con una adaptación de etiquetas; no debe suponerse equivalencia automática con las cuatro clases en español.
Geolingüística: estimación por entidad federativa o región y visualización territorial según los datos, diccionarios y geometrías que cada script requiere.

Nota sobre el corpus: los cuadernos no implementan siempre la misma depuración, partición o tarea. El número de muestras y el significado de las etiquetas deben extraerse de los archivos efectivamente utilizados en cada ejecución. No debe identificarse una nueva ejecución de CV sobre TRAIN con un resultado publicado en TEST.
2. Representaciones
Los experimentos incluyen, según versión, TF-IDF, n-gramas, bolsa de palabras (BoW), embeddings preentrenados y representaciones HMT/HMVT con componentes léxicos, subléxicos, discursivos o geolingüísticos. Los nombres y arquitectura exacta de cada variante deben reportarse a partir del código de su experimento, evitando equiparar versiones distintas solo por su nombre. En los experimentos recientes, los embeddings se mantienen congelados y no reciben ajuste fino.
3. Algoritmos
En los scripts correspondientes se comparan regresión logística, k vecinos más cercanos, SVM, Naive Bayes, red neuronal MLP, XGBoost, Random Forest y árbol de decisión. No todos los scripts evalúan necesariamente todos los algoritmos; el catálogo conserva las distintas líneas experimentales sin completar resultados faltantes.
4. Evaluación
Según la implementación: particiones TRAIN/TEST, validación cruzada sobre TRAIN o validación anidada (folds externos e internos), análisis de ablación, matrices de confusión y pruebas de McNemar con ajustes múltiples. Para una comparación publicable:
1. Definir una sola versión del corpus, idioma, etiquetas y limpieza.
2. Usar las mismas particiones por modelo y representación. Ajustar vectorizadores, reducción de dimensión, selección de variables y sobremuestreo solo en entrenamiento.
3. Escoger hiperparámetros y ajustes por clase exclusivamente con validación interna.
4. Reportar Precision macro, Recall macro, F1-macro y Accuracy, además de métricas por clase (especialmente las minoritarias) y soporte.
5. Reportar variación entre folds, matrices de confusión basadas en predicciones fuera de entrenamiento y pruebas estadísticas cuando proceda.
6. No seleccionar la mejor variante a partir del conjunto TEST ni tratar como evidencia confirmatoria una selección realizada sobre los mismos folds externos.
7. Cuando los baselines no tengan ajuste y HMVT sí, describir la comparación como una comparación de sistemas/procedimientos, no como un efecto aislado atribuible solo a la representación.
Ejecución y reproducibilidad
1. Abrir EXIST2021_MAESTRO_TESIS.ipynb en Google Colab o Jupyter con Python 3.
2. Buscar en el catálogo el ID de experimento correspondiente al análisis que se quiera reproducir.
3. Ejecutar ese experimento de forma aislada, preferiblemente en un kernel nuevo. No ejecutar todas las celdas del maestro secuencialmente: son scripts alternativos y pueden redefinir variables o solicitar archivos distintos.
4. Proporcionar los archivos de datos solicitados por la implementación. Algunas celdas requieren CSV/TSV originales; otras, datos reestructurados o recursos geoespaciales.
5. Registrar versión de Python, librerías, semillas, hardware, fecha, partición efectiva y tamaño por clase.
6. Guardar los resultados completos y, para su publicación, asociarlos al ID del catálogo y al hash de implementación.
Dependencias frecuentes
numpy, pandas, scipy, scikit-learn, matplotlib, seaborn, xgboost, sentence-transformers; algunas implementaciones geográficas usan geopandas, shapely y utilidades cartográficas. Se conservan las importaciones originales: no se ha verificado que un único entorno ejecute las 70 variantes sin ajustes de compatibilidad.
Propuesta de redacción metodológica para el artículo
Se realizó un estudio comparativo de representaciones textuales tradicionales y representaciones HMT/HMVT para la detección y categorización de violencia digital en publicaciones de redes sociales. Se analizaron configuraciones binarias y multiclase, así como, en experimentos complementarios, características geolingüísticas. Los modelos comparados incluyeron clasificadores lineales, basados en vecinos, probabilísticos, redes neuronales, ensambles y árboles de decisión. La evaluación se articuló mediante las particiones y protocolos documentados en cada experimento; las comparaciones confirmatorias deben emplear particiones idénticas, selección de hiperparámetros sin fuga de información y métricas macro y por clase. Los estudios de ablación permiten examinar la contribución de los componentes de representación, y los contrastes estadísticos deben aplicarse a predicciones pareadas cuando estén disponibles.

Antes de enviar a revista: reemplazar la descripción genérica por el protocolo exacto de las ejecuciones seleccionadas, tamaños y distribución real de conjuntos, definición matemática de cada versión, tabla de hiperparámetros, F1 y desviaciones, intervalos o pruebas de significación e información suficiente para reproducirlas. No se han añadido cifras no verificadas.
Estructura sugerida de resultados de tesis/paper
- Tabla A: corpus, idioma, limpieza y distribución por clase.
- Tabla B: representación / versión / bloques y pesos utilizados.
- Tabla C: algoritmos, hiperparámetros, estrategia de balanceo y presupuesto de búsqueda.
- Tabla D: comparativa principal de Precision macro, Recall macro, F1-macro y Accuracy.
- Tabla E: precisión, recall, F1 y soporte por clase, con énfasis en Acoso y Violencia sexual.
- Tabla F: ablación de los bloques de HMT/HMVT y variaciones pareadas de F1.
- Figuras: matrices de confusión, preferiblemente con predicciones fuera de entrenamiento; mapas por región/entidad cuando aplique.
Alcance y precauciones
- 70 implementaciones distintas significa variantes de código, no necesariamente 70 experimentos estadísticamente independientes ni resultados publicables.
- Se identificaron 63 implementaciones con al menos una salida textual almacenada; estas salidas pueden proceder de ejecuciones distintas, tener formato parcial o mezclar protocolos.
- El código fue limpiado de comentarios y su sintaxis se revisó estáticamente. No se reentrenaron todos los modelos, ni se verificaron archivos de entrada externos, tiempos de ejecución, exactitud de etiquetas o convergencia de algoritmos.
- Algunos notebooks originales pueden incorporar advertencias sobre resultados exploratorios, sobreajuste o comparaciones no homogéneas. La consolidación no elimina esas limitaciones científicas.
Procedencia y trazabilidad
Cada experimento tiene identificador EXP-###, nombre de archivo y número de celda de origen (contado desde 1). Se conservaron las versiones de código con diferencias semánticas. Los notebooks de origen deben almacenarse como respaldo del proyecto de investigación y los resultados finales deben vincularse al experimento del catálogo que realmente los produjo.
