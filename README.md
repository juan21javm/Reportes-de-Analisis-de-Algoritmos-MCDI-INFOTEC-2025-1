---
title: "Análisis de Algoritmos"
author: "Juan Antonio Velasquez Martinez"
date: "2025-02-02"
format: html
---

## INFOTEC "Centro de Investigación e Innovación en Tecnologías de la Información y Comunicación"

# Análisis de Algoritmos

## 1A. REPORTE ESCRITO: EXPERIMENTOS Y ANÁLISIS

## INTRODUCCIÓN

En la era digital actual, el big data ha emergido como un recurso invaluable para las organizaciones, permitiéndoles extraer, procesar y analizar datos significativos. El big data se caracteriza por sus 4 Vs: volumen, velocidad, variedad y veracidad. El volumen se refiere a la cantidad masiva de datos generados y almacenados; la velocidad, a la rapidez con la que se generan y procesan los datos; la variedad, a los diferentes tipos de datos (estructurados y no estructurados); y la veracidad, a la calidad y precisión de los datos. La capacidad de manejar y analizar estos grandes volúmenes de información de manera eficiente es crucial para aprovechar al máximo el potencial del big data. (Müller et al., 2016)

El análisis de big data permite a las organizaciones identificar patrones, predecir tendencias y optimizar procesos, lo que puede resultar en mejoras significativas en la eficiencia operativa y en la toma de decisiones estratégicas. Sin embargo, la manipulación de grandes volúmenes de datos presenta desafíos significativos en términos de infraestructura, almacenamiento, procesamiento y análisis. Los algoritmos eficientes son esenciales para manejar estos desafíos y garantizar que los sistemas de big data funcionen de manera óptima. (Manyika et al., 2011)

Este reporte se basa en comparar diferentes órdenes de crecimiento mediante simulaciones en un entorno de Jupyter. Se compararán los siguientes órdenes de crecimiento: O(1) vs O(log n), O(n) vs O(n log n), O(n²) vs O(n³), O(a\^n) vs O(n!), y O(n!) vs O(n\^n). Para cada comparación, se seleccionarán rangos adecuados de n para visualizar claramente las diferencias en los órdenes de crecimiento. Se crearán figuras para cada comparación y se discutirán las observaciones obtenidas. Además, se presentará una tabla con tiempos de ejecución simulados para algoritmos ficticios con los órdenes de crecimiento mencionados, utilizando diferentes tamaños de entrada n. Este análisis proporcionará una visión clara de cómo los diferentes órdenes de crecimiento afectan el rendimiento y su eficiencia.

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

## RESULTADOS

![](images/clipboard-2919343183.png)

Discusión de la Figura 1: El grafico muestra que la función constante O(1) permanece constante independientemente del tamaño de la entrada, mientras que O(logn) crece lentamente con el tamaño de la entrada. Por lo que un algoritmo con complejidad constante O(1) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad logarítmica O(logn).

![](images/clipboard-2385561962.png)

Discusión de la Figura 2: La función O(n) crece linealmente con el tamaño de entrada n. Mientras que la función O(n log n) crece más rápido que O(n), pero sigue siendo practico para valores moderados de n. Entonces, un algoritmo con complejidad lineal O(n) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad linealítmica O(nlogn).

![](images/clipboard-2666917706.png)

Discusión de la Figura 3: La función cuadrática O(nˆ2) crece más rápidamente que la lineal, pero la función cúbica O(nˆ3) crece aún más rápidamente. Por lo tanto, un algoritmo con complejidad cuadrática O(nˆ2) es más eficiente en términos de tiempo de ejecución en comparación con un algoritmo con complejidad cúbica O(nˆ3)

![Discusión de la Figura 4: El gráfico muestra la complejidad factorial de O(n!) que resulta en tiempos de ejecución mucho más alto que O(2ˆn) a medida que el tamaño de la entrada n aumenta. La complejidad factorial O(n!) crece mucho más rápido que la complejidad exponencial O(2ˆn), haciendo que los algoritmos con complejidad factorial sean prácticamente inutilizables para valores grandes de n.](images/clipboard-4113518922.png)

![](images/clipboard-3712726291.png)

Discusión de la Figura 5: El gráfico muestra como la función factorial O(n!) crece muy rápidamente, pero la función doble exponencial O(nˆn) crece más rapido a medida del tamaño de la entrada. Por lo tanto, los algoritmos con complejidad factorial y doble exponencial sean prácticamente inutilizables para valores grandes de n.
