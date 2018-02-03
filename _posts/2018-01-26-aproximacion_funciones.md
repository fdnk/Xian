---
title: Aproximación de funciones
date: 2018-01-26 11:42:00 -0300
layout: post
tag: intermedio
---

Una práctica común en ingeniería es la de aproximar funciones por otras más simples. El objeto no es --como podríamos pensar-- el de poder calcular un conseno o un logaritmo mediante un cálculo cerrado mediante un polinomio o similar. Muchas veces se desea obtener un modelo sencillo que explique fenómenos complejos, y es justamente en la sencillez del modelo donde radica su potencia.

Un caso interesante de analizar es el de diseño de filtros FIR. Dicho de una manera muy sencilla, consiste en encontrar los coeficientes de la combinación lineal de una señal (una función del tiempo) con sus valor en instantes anteriores para eliminar ruidos que pudiesen estar presentes en ella, u obtener información importante sobre ella.
(Escribir bien esto, es una idea)

Por ejemplo, al utilizar un ecualizador digital: tenemos una respuesta en frecuencia deseada, y queremos obtener los mejor coeficientes del filtro para que la respuesta obtenida sea la ``más parecida posible'' al caso ideal.

# Ajuste de funciones

Dada una función $$g(x)$$, queremos hallar una función $$f(x)$$ que sea lo ``más parecida posible'' a $$g(x)$$. Lo primiero que es necesario es definir cuál va a ser el critero de optimalidad, es decir, cual es el criterio para decir cuán parecidas son dos funciones.

### Diferencia

Un criterio sencillo sería utilizar la distancia entre ambas funciones punto a punto: $$|f(x)-g(x)|$$. Para que esta idea funcione, tendríamos que definir un intervalo en el cual queremos medir cuan similares son.

$$L = \max_{a \leq x \leq b} |f(x)-g(x)|$$

En este caso, $$L$$ es la máxima distancia entre ambas funciones, en el intervalo $$[a,b]$$.


Podemos considerar la distancia máxima en el intervalo, para tener una cota estricta, o tener un promedio de la distancia en todo el intervalo. Podemos extender el concepto de promedio a un intervalo continuo convirtiendo la suma en una integral:

$$L_1 = \int_a^b \left| f(x) - g(x) \right| dx  $$

Si bien $$L_1$$ es más representativa de lo que pasa (en promedio) en todo el intevalo, nada nos dice que en un punto ambas funciones puedan ser completamente distintas y bastante similares en el resto.


### Media cuadrática

Sin embargo, la forma predilecta para medir cuán parecidas son dos funciones es la media cuadrática (Root Squeare Mean, o RMS):

$$L_2 = \frac{1}{b-a} \sqrt{  \int_a^b \left( f(x) - g(x) \right)^2 dx}  $$

Parece medio extraño el hecho de elevar al cuadrado, integrar y tomar la raiz cuadrada, pero notemos que la función es similar a la del módulo: al elevar al cuadrado estamos integrando algo siempre positivo, y luego se toma la raíz para --de alguna forma-- contrarrestar el efecto. Al hacer esto y dividir por el largo del intervalo, vemos que la unidad resultante es la misma que la de $$f$$ y $$g$$, al igual que en el caso anterior.

### Un poco de rigurisad matemática, por favor

Vemos que tanto $$L_1$$ como $$L_2$$ es el resultado de aplicar las siguientes normas a la función de error $$e(x)=f(x)-g(x)$$:

$$ \mathcal{L}_1 (f) =  \int_a^b \left| f(x) \right| dx  $$
$$ \mathcal{L}_2 (f) =  \frac{1}{b-a} \sqrt{  \int_a^b \left( f(x)  \right)^2 dx } $$


El intervalo $$[a,b]$$ en el cual se va a trabajar debe definirse, y suele tener relación con el dominio práctico de las funciones consideradas (no tanto el matemático).

Un concepto importante de una norma, es que la norma vale 0 solamente para el vector nulo (función nula en este caso). Nuestra primera aproximación, la diferencia máxima entre las funciones en el intervalo, también cumple los axiomas de una norma.

#### Relación con un PI
Al ver productos internos, definimos el concepto de norma inducida. Esto es, dado un producto interno arbitrario $$\inner{\cdot}{\cdot} en un espacio vectorial $$\VV$$ con producto interno, la función $$h: \VV \rightarrow {\RR}_{\ge 0}$$ definida por $$h(f) = \sqrt{ \inner{f}{f} }$$ es una norma.

La gran ventaja que tenemos al trabajar con normas inducidas es que tenemos toda la maquinaria de soporte del Álgebra Lineal a nuestro favor. Otra gran ventaja, es que las normas inducidas son muy prácticas en la vida real. Por ejemplo, la ``energía'' de una señal, como el sonido, las vibraciones, o los campos electromagnéticos, son descriptas mediante una norma inducida por el producto interno canónico.

Sin embargo, no todas las normas son inducidas. En este caso, $$\mathcal{L}_1$$ es una norma que no proviene de ningún producto interno, mucho menos $$L$$. Aún así, es posible trabajar con ellas, aunque es más fastidioso.





## Minimización del error

Acá iba a utilizar derivadas para minimizar la función error.

# To Do
  - Mostrar que el error es la integral entre ambas funciones. Comparar con el ECM, que es la integral del cuadrado del error.
  - Proyectar un seno sobre el espacio de los polinomios
  - Dividir de forma leíble





