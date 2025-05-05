---
Title: "Análisis de Algoritmos"
Author: "Juan Antonio Velasquez Martinez"
Date: "2025-02-02"
Format: html
---

## INFOTEC "Centro de Investigación e Innovación en Tecnologías de la Información y Comunicación"

# Análisis de Algoritmos

## 1A. REPORTE ESCRITO: EXPERIMENTOS Y ANÁLISIS

## 1.1 INTRODUCCIÓN

En la era digital actual, el big data ha emergido como un recurso invaluable para las organizaciones, permitiéndoles extraer, procesar y analizar datos significativos. El big data se caracteriza por sus 4 Vs: volumen, velocidad, variedad y veracidad. El volumen se refiere a la cantidad masiva de datos generados y almacenados; la velocidad, a la rapidez con la que se generan y procesan los datos; la variedad, a los diferentes tipos de datos (estructurados y no estructurados); y la veracidad, a la calidad y precisión de los datos. La capacidad de manejar y analizar estos grandes volúmenes de información de manera eficiente es crucial para aprovechar al máximo el potencial del big data. (Müller et al., 2016)

La maniuplación grande de volúmenes de información, presenta desafíos por los costos de cómputo. Estos costos se refieren al gasto monetario, a los recursos computacionales necesarios, tiempo de procesamiento, memoria, almacenamiento, energía entre otros. A continuación se mostraran algunas de las implicaciones más importantes para la manipulación de grandes volúmenes de información.

El análisis de big data permite a las organizaciones identificar patrones, predecir tendencias y optimizar procesos, lo que puede resultar en mejoras significativas en la eficiencia operativa y en la toma de decisiones estratégicas. Sin embargo, la manipulación de grandes volúmenes de datos presenta desafíos significativos en términos de infraestructura, almacenamiento, procesamiento y análisis. Los algoritmos eficientes son esenciales para manejar estos desafíos y garantizar que los sistemas de big data funcionen de manera óptima. (Manyika et al., 2011)

Este reporte se basa en comparar diferentes órdenes de crecimiento mediante simulaciones en un entorno de Jupyter. Se compararán los siguientes órdenes de crecimiento: O(1) vs O(log n), O(n) vs O(n log n), O(n²) vs O(n³), O(a\^n) vs O(n!), y O(n!) vs O(n\^n). Para cada comparación, se seleccionarán rangos adecuados de n para visualizar claramente las diferencias en los órdenes de crecimiento. Se crearán figuras para cada comparación y se discutirán las observaciones obtenidas. Además, se presentará una tabla con tiempos de ejecución simulados para algoritmos ficticios con los órdenes de crecimiento mencionados, utilizando diferentes tamaños de entrada n. Este análisis proporcionará una visión clara de cómo los diferentes órdenes de crecimiento afectan el rendimiento y su eficiencia.
## 1.2 Código
## BIBLIOTECAS UTILIZADAS

```{python}
import numpy as np
import pandas as pd
import math
import matplotlib.pyplot as plt
```

## DEFINICIÓN DE LAS FUNCIONES DE LOS SIGUIENTES ÓRDENENES DE CRECIMIENTO

Funciones con las que vamos a comparar los siguientes órdenes de crecimiento.

```{python}
# Definir las funciones de crecimiento
def constant(n):
return 1

def logarithmic(n):
return np.log(n)

def linear(n):
return n

def linear_logarithmic(n):
return n * np.log(n)

def quadratic(n):
return n**2

def cubic(n):
return n**3

def exponential(n, a=2):
return a**n

def factorial(n):
return math.factorial(n)

def double_exponential(n):
return n**n
```

## FIGURAS DE COMPARACIÓN

**Nota:** Para cada una de las comparaciones, se eligieron rangos adecuados de n que permiten visualizar claramente las diferencias entre los órdenes de crecimiento.

```{python}
# Figura de Comparaciones de las Funciones de crecimiento
def plot_comparison(funcs, labels, title, x_range):
    plt.figure(figsize=(7, 5))
    for func, label in zip(funcs, labels):
        plt.plot(x_range, [func(x) / 1e9 for x in x_range], label=label)  # Convertir a segundos
    plt.xlabel('n')
    plt.ylabel('Tiempo (s)')
    plt.title(title)
    plt.legend()
    plt.yscale('log')
    plt.xscale('log')
    plt.grid(True)
    plt.show()

# Rango de valores para n
x_range_small = np.arange(1, 10)
x_range_medium = np.arange(1, 100)

# Comparación 1: O(1) vs O(log n)
plot_comparison([constant, logarithmic], ['O(1)', 'O(log n)'], 'Figura 1 - Comparación de O(1) con O(log n)', x_range_small)


# Comparación 1: O(1) vs O(logn)
plot_comparison([constant, logarithmic], ['O(1)', 'O(logn)'], 'Figura 1 -␣
,→Comparación de O(1) con O(logn)', x_range_small)

# Comparación 2: O(n) vs O(n log n)
plot_comparison([linear, linear_logarithmic], ['O(n)', 'O(n log n)'], 'Figura 2 - Comparación de O(n) con O(n log n)', x_range_medium)

# Comparación 3: O(n^2) vs O(n^3)
plot_comparison([quadratic, cubic], ['O(n^2)', 'O(n^3)'], 'Figura 3 - Comparación de O(n^2) con O(n^3)', x_range_medium)

# Comparación 4: O(a^n) vs O(n!)
plot_comparison([lambda n: exponential(n, 2), factorial], ['O(2^n)', 'O(n!)'], 'Figura 4 - Comparación de O(2^n) con O(n!)', x_range_small)

# Comparación 5: O(n!) vs O(n^n)
plot_comparison([factorial, double_exponential], ['O(n!)', 'O(n^n)'], 'Figura 5 - Comparación de O(n!) con O(n^n)', x_range_small)
```

## 1.3 RESULTADOS

## 1.3.1 Interpretaciíon de Gráficos

![image](https://github.com/user-attachments/assets/b131e63c-8989-4777-adb6-f5200cf4d928)

Discusión de la Figura 1: El grafico muestra que la función constante O(1) permanece constante independientemente del tamaño de la entrada, mientras que O(logn) crece lentamente con el tamaño de la entrada. Por lo que un algoritmo con complejidad constante O(1) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad logarítmica O(logn).

![image](https://github.com/user-attachments/assets/9f336519-0e71-49b4-baed-61f78388049c)

Discusión de la Figura 2: La función O(n) crece linealmente con el tamaño de entrada n. Mientras que la función O(n log n) crece más rápido que O(n), pero sigue siendo practico para valores moderados de n. Entonces, un algoritmo con complejidad lineal O(n) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad linealítmica O(nlogn).

![image](https://github.com/user-attachments/assets/f5f0020e-369c-4902-b4da-f4c7719bd25d)

Discusión de la Figura 3: La función cuadrática O(nˆ2) crece más rápidamente que la lineal, pero la función cúbica O(nˆ3) crece aún más rápidamente. Por lo tanto, un algoritmo con complejidad cuadrática O(nˆ2) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad cúbica O(nˆ3)

![image](https://github.com/user-attachments/assets/127e7a36-3cd4-4462-9614-89e21ad0740c)

Discusión de la Figura 4: El gráfico muestra la complejidad factorial de O(n!) que resulta en tiempos de ejecución mucho más alto que O(2ˆn) a medida que el tamaño de la entrada n aumenta. La complejidad factorial O(n!) crece mucho más rápido que la complejidad exponencial O(2ˆn), haciendo que los algoritmos con complejidad factorial sean prácticamente inutilizables para valores grandes de n.

![image](https://github.com/user-attachments/assets/94555c0f-2e07-41a8-bdbc-cc8332cb60d2)

Discusión de la Figura 5: El gráfico muestra como la función factorial O(n!) crece muy rápidamente, pero la función doble exponencial O(nˆn) crece más rapido a medida del tamaño de la entrada. Por lo tanto, los algoritmos con complejidad factorial y doble exponencial sean prácticamente inutilizables para valores grandes de n.

## 1.3.2 Interpretaciíon de Tabla
| n\      | O(1)       | O(log n)   | O(n)       | O(n log n) | O(n^2)     | O(n^3)     | O(2^n)     | O(n!)       | O(n^n)       |
|---------|------------|------------|------------|------------|------------|------------|------------|-------------|--------------|
| 100     | 1.00e-09   | 4.61e-09   | 1.00e-07   | 4.61e-07   | 1.00e-05   | 1.00e-03   | 1.27e+02    | 9.33e+157   | 9.99e+199   |
| 1000    | 1.00e-09   | 6.91e-09   | 1.00e-06   | 6.91e-06   | 1.00e-03   | 1.00e+00    | 1.07e+299   | Overflow     | Overflow     |
| 10000   | 1.00e-09   | 9.21e-09   | 1.00e-05   | 9.21e-05   | 1.00e-01   | 1.00e+03    | Overflow     | Overflow     | Overflow     |
| 100000  | 1.00e-09   | 1.15e-08   | 1.00e-04   | 1.15e-03   | 1.00e+01   | 1.00e+06    | Overflow     | Overflow     | Overflow     |

Como se muestra en la tabla, el tiempo de ejecución de O(1) no dependen del tamaño de n. Este mantiene un mismo valor, lo que idnica que el tiempo de ejecución no dependen del tamaño de n. Por otro lado O(logn) los valores aumentan lentamente a mediuda que n aumenta por lo que es consistenten con la naturaleza logaritmica. En O(n) los valores aumentan de forma lineal con n. En la tabla, los valores de O(nlogn) aumenta rápido que O(n), pero no tanto como O(nˆ2). Por otro lado tenemos O(nˆ2) donde sus valores aumentan rapidamente a medidca que incrementa los valores de n. En O(nˆ3) es relativamente lo mismo pero más rápido, aun en valores pequeños. Al ejecutar el código, muestra varios Overflow en la tabla, por lo que se desbordó la memoria y no fue capaz de obtener esos valores, esto se debe a que los valores de O(2ˆn), O(n!) y O(nˆn) para n grandes (como 10000 o 100000) son extremadamente grandes y exceden el límite de conversión de enteros a cadenas en Python.

## 1.3.3 IMPLICACIONES DE COSTOS DE CÓMPUTO NECESARIOS PARA MANIPULAR GRANDES VOLÚMENES DE INFORMACIÓN

Los costos de la infraestructura implica la manipulación de grandes volúmenes de datos que requierne una infrestructura robusta, esto incluye servidores potentes, almcanamiento masivo y redes de alta velocida, lo cual conlleva costos significativos de hardware, mantenimiento y energía. (Armbrust et al., 2010)

La energía es inplicación de los centros de datos que manejan grandes volúmenes de información ya que consumen enormes cantidades de energía, lo cual no solo aumenta los costos operativos, sino que también tiene implicaciones ambientales debido a las emisiones de carbono. (Baliga et al., 2011) 

Los costos de almacenamieto implica que los grandes vbolúmnews de almcanamiento de datos requiera solcuiones de de forma escalable y eficientes. Estos costos pueden ser significativos ya que requieren almacenamiento para la recuperación. Por otro lado tenemos los costos de procesamiento estos volúmenes de datos en tiempo real o cerca de tiempo real requiere de algoritmos eficientes y recursos de cómputo significativo. Los costos de procesamiento pueden ser altos, especialmente si se utilzian tecnologias como el aprendizaje automático y la inteligencia artificial. (Wang et al., 2015)

El manipular grandes volúmenes de información implica costos significativos en términos de infraestructura, energía, almacenamiento, procesamiento, seguridad y mantenimiento. Estos deben ser cuidadosamente considerados y gestionados para aegurar eficiencia y sostenibilidad de las soluciones de big data.
