# Parcial-1
Parcial imagenes
## Integrantes
Diego Jimenez
Olfred Carvajal
## Objetivos:

*Implementar un algoritmo de segmentación automática de lesiones cutáneas en imágenes dermatoscópicas.

*Usar un método de segmentación permitido en el parcial (clustering con K-means) sin apoyarse en segmentadores externos.

*Evaluar el desempeño del algoritmo mediante la métrica F1 Score, comparando los resultados obtenidos frente a las máscaras de referencia.

*Analizar estadísticamente los resultados (promedio y desviación estándar del F1 Score) para valorar la eficiencia del método.

## Procedimiento de creación del código:

El primer paso fue la eleccion del metodo para la segmetacion siendo este (Clustering por K-means) ya que :

-Permite clasificar los píxeles en grupos de colores (clusters), lo cual es útil ya que las lesiones suelen tener tonalidades más oscuras respecto al fondo de piel.

-Es más robusto que un umbral fijo, ya que se adapta a la distribución de colores de cada imagen.

El desrollo del algoritmo se divide en 7 pasos:

1) Lectura de imágenes: se cargaron todas las imágenes dermatoscópicas y sus segmentaciones ideales.

2) Transformación de datos: cada píxel se representó como un vector en el espacio RGB.

3) Aplicación de K-means (K=6): se agruparon los píxeles en 2 clusters (lesión y piel).

4) Se identifica el cluster más oscuro (valor mínimo en el canal L) como posible lesión.

5) Se genera una máscara binaria donde los píxeles del cluster elegido son 255 (blanco) y el resto 0 (negro).

6) Evaluación con F1 Score: cada máscara generada fue comparada con su segmentación ideal.

7) Registro de resultados: se generó una tabla con el F1 Score por imagen, promedio y desviación estándar.

Nota: Durante el desarrollo del código se empleó la ayuda de una inteligencia artificial (ChatGPT) para estructurar y depurar el algoritmo, aunque las pruebas y adaptaciones finales se realizaron en Google Colab.

## Diagrama de Flujo:
![](https://github.com/DAJO2/LAB2-/blob/main/DIEGOJIMENEZCONVOLUCION.png)
[!imagen diagrama de flujo.png]


## Análisis de resultados:

Tras aplicar el algoritmo de segmentación con K-means (K=2 en RGB) a las 35 imágenes dermatoscópicas, se obtuvieron los siguientes indicadores estadísticos:

Promedio del F1 Score: 0.8398

Desviación estándar: 0.1298

## *Interpretación del promedio*

El F1 Score promedio de 0.8398 indica que el algoritmo tuvo un desempeño bueno, ya que se acerca al valor ideal que seria  1.0. Esto significa que, en la mayoría de los casos, la segmentación logró un equilibrio aceptable entre la precisión (qué tan pocos falsos positivos se detectaron) y el recall (qué tanto de la lesión real se logró identificar).

,el método K-means fue capaz de distinguir  la lesión del fondo en la mayor parte de las imágenes, cumpliendo el objetivo principal.

## *Interpretación de la desviación estándar*

El valor de desviación estándar 0.1298 muestra el grado de variabilidad de los resultados con respecto al promedio.

Una desviación estándar baja (cercana a 0) significaría que casi todas las imágenes tuvieron resultados muy similares, con un rendimiento constante.

En este caso, el valor moderado (~0.13) indica que hay diferencias notables entre unas imágenes y otras:

Algunas alcanzaron F1 superiores a 0.90 (segmentación muy buena).

Otras bajaron hasta valores cercanos a 0.60 (segmentación deficiente).

Mostrando que el algoritmo en algunos casos no podia hacer una segmetacion precisa como las mostradas en la segmetacion ideal.

## *Causas de la variabilidad*

-Alta calidad de segmentación (F1 > 0.85): en imágenes con buen contraste entre la lesión y la piel.

-Calidad aceptable (0.65 < F1 < 0.85): ocurrió cuando el color del fondo tenía tonalidades similares a las de la lesión o existían sombras.

-Baja calidad (F1 < 0.65): se presentó en casos con bordes poco definidos o lesiones claras, donde el algoritmo confundió parte de la piel con la región de interés.

## Concluciones:
En conclucion se podria decir que los resultados estadísticos demuestran que el método de K-means en RGB es un buen metodo  en la mayoría de los casos, logrando un rendimiento muy bueno  en promedio. Sin embargo, la desviación estándar moderada advierte que su eficacia no es uniforme en todas las imágenes, lo que sugiere la necesidad de ajustes adicionales (ejemplo: K=3, preprocesamiento de contraste) para mejorar la estabilidad del algoritmo en escenarios más complejos.

link del drive 
https://colab.research.google.com/drive/1vCZRExY1MnwGJOemt7PK6SIYSndsfPRO?usp=sharing
