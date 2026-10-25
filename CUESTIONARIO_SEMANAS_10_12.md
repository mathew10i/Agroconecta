# Cuestionario de aprendizaje de semanas 10 a 12

## Preguntas

1. ¿Por qué se seleccionó una MLP para AgroConecta?
   - A. Porque la entrada principal son imágenes.
   - B. Porque la entrada es un vector de variables tabulares.
   - C. Porque la tarea consiste en generar texto.
   - D. Porque el objetivo es pronosticar una secuencia meteorológica.

2. ¿Qué acción evita que el preprocesamiento use información del conjunto de prueba?
   - A. Ajustar `StandardScaler` y `OneHotEncoder` con todos los datos.
   - B. Aplicar `fit_transform` a entrenamiento y `transform` a validación y prueba.
   - C. Eliminar la validación.
   - D. Aumentar el número de épocas.

3. ¿Cuál es la función principal de Dropout?
   - A. Crear registros agrícolas nuevos.
   - B. Convertir categorías en números.
   - C. Regularizar la red desactivando unidades al azar durante el entrenamiento.
   - D. Sustituir la función de pérdida.

4. Si AgroConecta debe evitar que se oculten oportunidades compatibles, ¿qué métrica merece especial atención?
   - A. Recall.
   - B. Precision.
   - C. Número de épocas.
   - D. Tamaño del archivo del modelo.

5. ¿Por qué F1 es útil en este problema?
   - A. Porque mide el consumo eléctrico.
   - B. Porque combina Precision y Recall en una sola medida.
   - C. Porque reemplaza la matriz de confusión.
   - D. Porque convierte el puntaje en una venta confirmada.

6. ¿Qué significa un ROC-AUC alto en este experimento?
   - A. Que el modelo suele ordenar los positivos por encima de los negativos.
   - B. Que todas las recomendaciones terminarán en ventas.
   - C. Que no existen sesgos territoriales.
   - D. Que la etiqueta sintética se volvió real.

7. ¿Cuál es la principal limitación de las métricas reportadas?
   - A. Se calcularon sin una red neuronal.
   - B. Utilizan una etiqueta derivada de una regla sintética, no transacciones reales.
   - C. No incluyen ninguna variable territorial.
   - D. Solo se ejecutaron en una hoja de cálculo.

8. ¿Por qué no debe compararse de forma causal el modelo base 70/15/15 con el optimizado 80/10/10?
   - A. Porque usan lenguajes distintos.
   - B. Porque tienen conjuntos de prueba distintos y cambian más de un factor.
   - C. Porque F1 no admite comparación.
   - D. Porque ambos usan ReLU.

9. ¿Qué mejora metodológica evalúa mejor la generalización hacia actores nuevos?
   - A. Dividir los pares al azar sin conservar identificadores.
   - B. Separar entrenamiento y prueba por grupos de productores y compradores.
   - C. Entrenar con el conjunto de prueba.
   - D. Aumentar el umbral hasta 1,00.

10. ¿Qué práctica fortalece la sostenibilidad tecnológica del prototipo?
    - A. Guardar solo el archivo del modelo.
    - B. Versionar datos, código, preprocesador, modelo, métricas y condiciones del experimento.
    - C. Eliminar la documentación para reducir espacio.
    - D. Depender de una biblioteca privativa sin alternativa.

## Respuestas justificadas

1. **B.** Una MLP recibe vectores tabulares y aprende relaciones no lineales entre cantidades, precios, categorías y condiciones logísticas.
2. **B.** Los parámetros de escalado y las categorías se aprenden solo con entrenamiento; validación y prueba permanecen independientes.
3. **C.** Dropout reduce la dependencia de combinaciones fijas de neuronas y actúa como regularizador.
4. **A.** Recall mide qué proporción de los positivos reales fue encontrada y permite observar oportunidades omitidas.
5. **B.** F1 es la media armónica de Precision y Recall y penaliza configuraciones desequilibradas entre ambas.
6. **A.** ROC-AUC resume la capacidad de ordenar positivos por encima de negativos a través de distintos umbrales.
7. **B.** El modelo reproduce una regla conocida; su desempeño no acredita impacto comercial ni probabilidad real de venta.
8. **B.** Cambian el tamaño de los conjuntos y las observaciones evaluadas, además del Dropout. La diferencia no puede atribuirse a un único ajuste.
9. **B.** La separación por actores impide que una misma entidad aparezca en entrenamiento y prueba mediante pares diferentes.
10. **B.** La reproducibilidad exige conservar juntos los artefactos y el contexto que permite reconstruir y auditar el resultado.
