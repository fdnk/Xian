---
title: Resolviendo Ecuaciones de Recurrencia
date: 2018-05-30 17:41:00 -0300
layout: post
tags: intermedio autovectores
---

Una aplicación de los autovectores de $$A^k$$ es la de resolver una ecuación de recurrencia lineal.

# Conejos y Fibonacci
Fibonacci presento en 1202 la solución al siguiente problema:
> Cierto hombre tenía una pareja de conejos en un lugar cerrado y deseaba saber cuántos se podrían reproducir en un año a partir de la pareja inicial, teniendo en cuenta que de forma natural tienen una pareja en un mes, y que a partir del segundo se empiezan a reproducir.

La cantidad de parejas de conejos en cada mes, se puede describir por la variable $$F_n$$ bajo las condiciones:
$$\begin{align*}
F_0 &= 0\\
F_1 &= 1\\
F_{n+1} &= F_n + F_{n-1}
\end{align*}$$

Partiendo de las condiciones iniciales, se calcula que $$F_2 = F_1+F_0 = 1+0 = 1$$. Luego, $$F_3 = F_2+F_1 = 1+1 = 2$$. Después $$F_4 = F_3+F_2 = 2+1 = 3$$, $$F_4 = F_3+F_2 = 3+2 = 5$$, etc.

El problema es que para calcular $$F_k$$ necesito comenzar a calcular $$F_2, F_3, \cdots, F_k$$. Queremos hallar de ser posible, una fórmula cerrada para hallar $$F_k$$ sin necesidad de calcular todas las anteriores.

## Planteo Algebráico
La ecuación $$F_{n+1} = F_n + F_{n-1}$$ puede escribirse de forma matricial como:

$$ \mtx{F_{n+1}} = \mtx{1 & 1} \mtx{F_n \\ F_{n-1}}$$

A fin de obtener un sistema cuadrado, vamos a agregar una segunda ecuación trivial que no modifica al sistema: $$F_n = F_n$$.

$$ \mtx{F_{n+1} \\ F_n} = \mtx{1 & 1 \\ 1 & 0} \mtx{F_n \\ F_{n-1}}$$

Vemos entonces que, dado un vector $$\mtx{F_n \\ F_{n-1}}$$ que contenga la cantidad actual de conejos, y la cantidad de conejos del mes pasado, es posible calcular el vector $$ \mtx{F_{n+1} \\ F_n}$$ que contiene la cantidad de conejos en el mes próximo, y en el actual.

Vemos que si iniciamos con el vector de las condiciones iniciales: $$ \trans{\mtx{1 & 0}} $$ al multiplicar por la matriz, obtenemos el vector  $$ \trans{\mtx{1 & 1}} $$, y si repetimos, se obtienen los vectores $$ \trans{\mtx{2 & 1}} $$,  $$ \trans{\mtx{3 & 2}} $$,  $$ \trans{\mtx{5 & 2}} $$, etc.

De esta forma, en la primer componente del vector siempre podemos ver la cantidad de conejos en el "mes actual", seguido por la cantidad del mes anterior.

Podemos calcular entonces: $$ \mtx{F_2 \\ F_1} = \mtx{1 & 1 \\ 1& 0} \mtx{F_1 \\ F_0}$$

Aún más: $$ \mtx{F_3 \\ F_2} = \mtx{1 & 1 \\ 1& 0} \mtx{F_2 \\ F_1} = \mtx{1 & 1 \\ 1 &0} \mtx{1 & 1 \\ 1& 0} \mtx{F_1 \\ F_0} $$

Es decir: $$ \mtx{F_3 \\ F_2} = \mtx{1 & 1 \\ 1& 0}^2 \mtx{F_1 \\ F_0} $$


Entonces por inducción, podemos decir que:

$$ \mtx{F_{n+1} \\ F_n} = \mtx{1 & 1 \\ 1 &0}^n \mtx{F_1 \\ F_0}$$


## Solución
Tomando $$A = \mtx{1 & 1 \\ 1 &0}$$ tenemos que los autovalores son $$\lambda_1 = \frac{1+\sqrt{5}}{2}$$ y $$\lambda_2 = \frac{1-\sqrt{5}}{2}$$, con $$v_1 = \mtx{\frac{1+\sqrt{5}}{2} \\ 1}$$ y $$v_2 = \mtx{\frac{1-\sqrt{5}}{2} \\ 1}$$. Lo cual nos permite escribir:

$$A = \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1} \mtx{\frac{1+\sqrt{5}}{2} & 0 \\ 0 & \frac{1-\sqrt{5}}{2}} \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1}^{-1}$$

Por lo tanto:

$$A^n = \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1} \mtx{\frac{1+\sqrt{5}}{2} & 0 \\ 0 & \frac{1-\sqrt{5}}{2}}^n \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1}^{-1}$$


Para simplificar, podemos escribir:

$$\begin{align*}
F_{n+1} &= \mtx{1 & 0} \mtx{F_{n+1} \\ F_n}\\
		&= \mtx{1 & 0} \mtx{1 & 1 \\ 1 & 0}^n \mtx{F_1 \\ F_0}\\
		&= \mtx{1 & 0} \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1} \mtx{\frac{1+\sqrt{5}}{2} & 0 \\ 0 & \frac{1-\sqrt{5}}{2}}^n \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2} \\ 1 & 1}^{-1} \mtx{1 \\ 0}\\
		&= \mtx{\frac{1+\sqrt{5}}{2} & \frac{1-\sqrt{5}}{2}} \mtx{\frac{1+\sqrt{5}}{2} & 0 \\ 0 & \frac{1-\sqrt{5}}{2}}^n \left( \frac{1}{10}\mtx{2\sqrt{5} & 5-\sqrt{5} \\ -2\sqrt{5} & 5+\sqrt{5}} \right) \mtx{1 \\ 0}\\
		&= \mtx{\left(\frac{1+\sqrt{5}}{2}\right)^{n+1} & \left(\frac{1-\sqrt{5}}{2}\right)^{n+1} } \frac{1}{10}\mtx{2\sqrt{5}\\ -2\sqrt{5}}\\
		&= \frac{\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}-\left(\frac{1-\sqrt{5}}{2}\right)^{n+1}}{\sqrt{5}}
\end{align*}$$

En conclusión, podemos decir que:

$$ F_k = \frac{\left(\frac{1+\sqrt{5}}{2}\right)^{k}-\left(\frac{1-\sqrt{5}}{2}\right)^{k}}{\sqrt{5}}, \quad k \in \NN $$

# Caso general

Sea una ecuación de recurrencia lineal de grado $$n$$: $$x_{n+1} = a_n x_n + a_{n-1} x_{n-1} + \cdots + a_1 x_1 $$

Se procede a armar el vector con los últimos n valores: $$X_n = \mtx{x_n \\ x_{n-1} \\ \vdots \\ x_1}$$

La evolución del vector $$X_n$$ está dada por el sistema:

$$\mtx{x_{n+1} \\ x_n \\ \vdots  \\ x_2} = \mtx{
	a_n & a_{n-1}  & \cdots & a_2 & a_1   \\
	1   &  0       & \cdots & 0   & 0  \\
 \vdots &  \vdots  & \,     & \vdots & \vdots \\
	0   &  0       & \cdots  & 1      &  0  }
 \mtx{x_n \\ x_{n-1}  \\ \vdots \\ x_1}$$

Lo cual se puede escribir abreviadamente como:

$$X_{n+1} = \left[\begin{array}{c|c}
	\begin{matrix}a_n & a_{n-1} & \cdots & a_1 \end{matrix} & a_0 \\
	\hline
	I_n & 0
\end{array}\right] X_n$$

Para simplificar la notación, vamos a llamar:

$$ \Phi = \left[\begin{array}{c|c}
	\begin{matrix}a_n & a_{n-1} & \cdots & a_1 \end{matrix} & a_0 \\
	\hline
	I_n & 0
\end{array}\right] $$

Mediante inducción, se llega a la expresión:
$$X_{n+1} = \Phi^n X_1$$

Donde $$X_1$$ es el vector con las condiciones iniciales.

Si $$\Phi$$ resulta diagonalizable, llamando $$\Phi = P \Lambda P^{-1}$$  podemos calcular fácilmente:

$$ \Phi^n = P \Lambda^n P^{-1} $$

Y para recuperar sólamente el elemento $$x_{n+1}$$ del vector, podemos escribir el producto:

$$ x_{n+1} = \mtx{1 & 0 & \cdots & 0} X_{n+1} $$


Finalmente, bajo la condición de $$\Phi$$ diagonalizable llegamos a la expresión:

$$ x_{n+1} = \mtx{1 & 0 & \cdots & 0} P \Phi^n P^{-1} X_1 $$

# Comentarios Finales
Logramos resolver una ecuación en recurrencia utilizando nuestro bagage de Álgebra Lineal, y es lindo, pero estos problemas también tienen otra solución tal vez más obvia desde el punto de vista de la Matemática Discreta. De todas formas, ambos enfoques se complementan muy bien.
