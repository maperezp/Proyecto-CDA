# Resumen técnico del notebook `04_Clustering.ipynb`

## Objetivo
El cuaderno construye una segmentación no supervisada de pacientes trasplantados utilizando su perfil clínico pre y perioperatorio. Se busca identificar patrones homogéneos que faciliten la caracterización temprana de riesgo de infección post-trasplante.

## Flujo de trabajo
1. **Ingesta y limpieza inicial:** Se carga `../data/Base_infecciones_POPTH_nuevo_modelado.xlsx`, se remueven identificadores personales (`Código anonimizado`, `#Paciente_Tx`, `Año_Tx`) y campos temporales (`Fecha_Tx`, `Fecha_Control/Muerte`, etc.) por no aportar al clustering.
2. **Depuración por calidad de datos:** Los marcadores de ausencia (`DESCONOCIDO`, `-1`, `-1.0`) se convierten en `NaN` y se descartan las variables con más de 60 % de nulos. Se eliminan medidas de desenlace tardío (`SOBREVIDA_*`, `Vivo_Hoy`, `Retrasplante`, métricas de estancia post-Tx, inmunosupresión posterior) para concentrarse en atributos disponibles al momento del alta temprana.
3. **Filtrado por completitud y tipado:** Se conservan únicamente filas completas y se fuerzan tipos: columnas numéricas a formato flotante y categóricas a `string`, preparando el dataset para los transformadores de `scikit-learn`.
4. **Pipeline de preprocesamiento:**
   - Numéricas → `StandardScaler` para igualar escalas, dado que K-Means depende de distancias euclidianas.
   - Categóricas → `OrdinalEncoder` (ordenamiento arbitrario pero estable) que habilita el uso conjunto con numéricas dentro de `ColumnTransformer`.
5. **Selección del número de clusters:**
   - Se transforma una única vez el dataset preprocesado y se itera `k ∈ [2, 9]`, calculando `silhouette_score` sobre el espacio escalado.
   - Se replica el análisis en el subespacio de 2 componentes principales (PCA) para validar la estabilidad de `k`. El mejor desempeño se obtiene en `k = 5`.
6. **Modelado y proyección:**
   - Se ajusta `KMeans(n_clusters=5, random_state=42)` sobre los datos preprocesados.
   - Se aplica `PCA` (2 componentes) únicamente para visualización y diagnóstico, reportando proporción de varianza explicada y cargas (loadings) por variable.
   - Se grafican los clusters en el plano PCA para inspección manual.
7. **Análisis de clústeres:**
   - Se reintegra el label de cluster a la tabla original y se calculan medias/medianas por grupo.
   - Se obtiene un z-score por variable y cluster respecto a la media global para identificar atributos sobre- o sub-representados; se listan las 10 mayores desviaciones positivas y negativas por cluster junto con el tamaño muestral.
8. **Persistencia:** Se encapsula el flujo completo (`preprocessor` + `PCA` + `KMeans`) en un `Pipeline` y se almacena en `../models/kmeans_pipeline.pkl` mediante `joblib`, habilitando su reutilización sin reejecutar el notebook.

## Consideraciones
- El modelo asume que tras eliminar columnas con >60 % de nulos, el dataset restante es suficientemente representativo; no se realiza imputación posterior.
- La codificación ordinal para categorías implica una métrica arbitraria; se seleccionó por simplicidad, pero puede reemplazarse por `OneHotEncoder` si se requieren distancias más fieles.
- La selección de `k` se basa exclusivamente en la métrica de silueta; incorporar métricas adicionales (Calinski-Harabasz, Davies-Bouldin) podría reforzar la elección.
- Las métricas descriptivas por cluster dependen de la cobertura de `df_predictions`; filas descartadas por `dropna()` no participan en el análisis.
