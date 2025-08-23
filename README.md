# Parcial-1
Parcial imagenes
## objetivos:

*Implementar un algoritmo de segmentación automática de lesiones cutáneas en imágenes dermatoscópicas.

*Usar un método de segmentación permitido en el parcial (clustering con K-means) sin apoyarse en segmentadores externos.

*Evaluar el desempeño del algoritmo mediante la métrica F1 Score, comparando los resultados obtenidos frente a las máscaras de referencia.

*Analizar estadísticamente los resultados (promedio y desviación estándar del F1 Score) para valorar la eficiencia del método.

## Procedimiento de creación del código:

El primer paso fue la eleccion del metodo para la segmetacion siendo este (Clustering por K-means) ya que nos ayuda a :

-Permite clasificar los píxeles en grupos de colores (clusters), lo cual es útil ya que las lesiones suelen tener tonalidades más oscuras respecto al fondo de piel.

-Es más robusto que un umbral fijo, ya que se adapta a la distribución de colores de cada imagen.

El desrollo del algoritmo se divide en 8 pasos:

1) Lectura de imágenes: se cargaron todas las imágenes dermatoscópicas y sus segmentaciones ideales.

2) Transformación de datos: cada píxel se representó como un vector en el espacio RGB.

3) Aplicación de K-means (K=2): se agruparon los píxeles en 2 clusters (lesión y piel).

4) Selección del cluster más oscuro: se asumió que la lesión corresponde al cluster con menor valor promedio de intensidad.

5) Máscara binaria: se generó una máscara donde la lesión es blanca y el fondo negro.

6) Post-procesamiento:

    -Operaciones morfológicas (apertura y cierre) para limpiar ruido y suavizar bordes.

    -Extracción del componente conectado más grande, considerando que la lesión es la región principal.

7) Evaluación con F1 Score: cada máscara generada fue comparada con su segmentación ideal.

8) Registro de resultados: se generó una tabla con el F1 Score por imagen, promedio y desviación estándar.

Nota: Durante el desarrollo del código se empleó la ayuda de una inteligencia artificial (ChatGPT) para estructurar y depurar el algoritmo, aunque las pruebas y adaptaciones finales se realizaron en Google Colab.

## Diagrama de Flujo:

[![flujo-kmeans.png](https://i.postimg.cc/BnzK3M4p/flujo-kmeans.png)](https://postimg.cc/5Xw0q5HQ)


## Análisis de resultados:


