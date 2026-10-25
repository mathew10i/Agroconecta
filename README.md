# AgroConecta IA

Prototipo académico para ordenar oportunidades entre productores y compradores agrícolas mediante una red neuronal multicapa. El notebook integra limpieza, construcción de pares, preprocesamiento, entrenamiento, evaluación e interacción.

## Entrega de semanas 10 a 12

### Semana 10 Arquitectura y entorno

- Arquitectura seleccionada: MLP, adecuada para variables tabulares numéricas y categóricas.
- Entrada: 18 variables originales del par y 51 características después de `StandardScaler` y `OneHotEncoder`.
- Red: `Dense/Linear(32) → ReLU → Dropout → Dense/Linear(16) → ReLU → Dropout → salida binaria`.
- Implementación principal: TensorFlow/Keras.
- Contraste: PyTorch con la misma estructura 32-16-1.
- Entorno: Google Colab con Python, Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn, TensorFlow, PyTorch y Joblib.

No se seleccionaron CNN ni RNN porque el conjunto actual no contiene imágenes ni secuencias temporales como entradas principales.

### Semana 11 Entrenamiento y ajuste

| Configuración | División | Dropout | Épocas | Accuracy | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Keras base | 70/15/15 | 0,20 | 37 | 0,9656 | 0,9697 | 0,9585 | 0,9641 | 0,9962 | 0,9961 |
| Keras optimizada | 80/10/10 | 0,30 | 36 | 0,9800 | 0,9664 | 0,9931 | 0,9796 | 0,9991 | 0,9991 |
| Keras balanceada | 80/10/10 | 0,30 | 33 | 0,9800 | 0,9664 | 0,9931 | 0,9796 | 0,9980 | 0,9981 |
| PyTorch balanceada | 80/10/10 | 0,30 | 49 | 0,9767 | 0,9726 | 0,9793 | 0,9759 | 0,9969 | 0,9976 |

Los resultados demuestran que la red aprende la regla sintética de compatibilidad; no prueban ventas reales. La comparación entre Keras y PyTorch utiliza el mismo conjunto de prueba 80/10/10. La comparación entre la configuración base y la optimizada es descriptiva porque sus conjuntos de prueba son diferentes; no permite atribuir la variación exclusivamente al Dropout o al tamaño del entrenamiento.

### Semana 12 Validación y sostenibilidad

- La etiqueta está casi equilibrada: 3.102 pares negativos y 2.898 positivos.
- El preprocesador se ajusta solo con entrenamiento y se aplica a validación y prueba con `transform`.
- `EarlyStopping` controla el sobreajuste y restaura los mejores pesos.
- Accuracy se acompaña con Precision, Recall, F1, ROC-AUC, PR-AUC y matrices de confusión.
- Los identificadores se conservan para trazabilidad, pero no ingresan como predictores.

Limitaciones que deben acompañar cualquier demostración:

1. La etiqueta se deriva de una regla creada por el equipo, no de transacciones observadas.
2. Las distancias entre zonas son didácticas y no representan rutas viales ni costos reales.
3. Un productor o comprador puede aparecer en varios pares; una validación futura debe separar actores mediante grupos para medir generalización hacia participantes no vistos.
4. La selección del modelo debe repetirse sobre un único conjunto de prueba congelado y con varias semillas.
5. El puntaje expresa compatibilidad dentro del experimento, no probabilidad de venta.

## Ejecución en Google Colab

1. Abrir `AgroConecta_INTEGRADO.ipynb` en Colab.
2. Seleccionar un entorno con GPU si se desea acelerar PyTorch; CPU también es suficiente para el tamaño actual.
3. Ejecutar las celdas en orden.
4. Cargar el CSV sucio solicitado por el notebook.
5. Descargar el CSV limpio, volverlo a cargar cuando el flujo lo solicite y continuar.
6. Revisar tablas, curvas, matrices de confusión y archivos exportados antes de iniciar la interacción final.

La carga manual intermedia es deliberada: demuestra que el entrenamiento utiliza el CSV limpio exportado. El notebook no puede ejecutarse de forma autónoma desde un clon nuevo mientras ese CSV de entrada no se publique o se genere dentro del repositorio.

## Evidencias y artefactos

Al finalizar, el notebook genera el dataset limpio, diccionarios de variables, preprocesador, modelos Keras y PyTorch, métricas, pesos de clase, metadatos y un paquete ZIP de entrega.

El informe debe identificar la semilla 42, la versión del dataset, el umbral 0,50, el split aplicado y las versiones de las bibliotecas. Sin esos datos, las métricas no son auditables.

## Pertinencia social y territorial

AgroConecta puede reducir el tiempo empleado en buscar una contraparte y hacer visibles ofertas agrícolas que hoy circulan de forma fragmentada. El sistema no fija precios, certifica calidad, garantiza ventas ni sustituye la negociación. Una prueba territorial debe incorporar consentimiento, minimización de datos, protección de ubicaciones, canales asistidos para productores con baja conectividad y evaluación del desempeño por producto, zona y tipo de actor.

## Contenido del repositorio

- `AgroConecta_INTEGRADO.ipynb`: pipeline ejecutado y evidencia de entrenamiento.
- `CUESTIONARIO_SEMANAS_10_12.md`: diez preguntas con respuestas justificadas.
