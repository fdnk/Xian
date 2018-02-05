---
title: Matriz de Proyección
date: 2018-02-03 06:24:00 -0300
tags: intermedio borrador
layout: post
---

En este post espero poder explicar de forma bastante amena y conceptual, como hallar la matriz en base canónica de una proyección ortogonal, sin irme de los conceptos que se ven actualmente en la materia.

## Proyección Ortogonal
**Alcance:** Vamos a trabajar en el espacio vectorial $$\VV=\RR[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \trans{y} x$$.


Para evitar complejidad adicional, vamos partir de suponer que disponemos de $$B$$ que es una base ortogonal del subespacio $$\ss{S} \subset \VV$$ sobre el cual queremos proyectar ortogonalmente. Llamemos $$B=\{v_1, v_2, \cdots, v_k\}$$ BOG de $$\ss{S}$$.

La "fórmula de la proyección" nos permite escribirla como:

$$\proy{S}{x} = \frac{\inner{v_1}{x}} {\inner{v_1}{v_1}} v_1 + \frac{\inner{v_2}{x}} {\inner{v_2}{v_2}} v_2 + \cdots + \frac{\inner{v_k}{x}}{\inner{v_k}{v_k}} v_k$$

Lo primero que vamos a hacer es normalizar la base. Vamos a trabajar sobre la base $$B'=\{u_1, u_2, \cdots, u_k\}$$ de $$\ss{S}$$. Para ello, tomamos $$u_j \eqdef \frac{1}{\norm{v_j}} \, v_j$$

Usando esta base de $$\ss{S}$$, la expresión queda más compacta:

$$\proy{S}{x} = \inner{u_1}{x} u_1 + \inner{u_2}{x} u_2 + \cdots + \inner{u_k}{x} u_k$$

Queda claro que  $$\inner{u_j}{x} \in \RR$$, es decir, los productos internos son simplemente números reales; así la expesión anterior es una combinación lineal de los vectores $$u_j$$, y procedemos a expresarla matricialmente:

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \mtx{ \inner{u_1}{x} \\ \inner{u_2}{x} \\ \vdots \\ \inner{u_k}{x} }$$

{% capture nota_cl %}
Al multiplicar una matriz a derecha por un vector, estamos haciendo combinaciones lineales de sus columnas.
<br/>
Ejemplo: Consideremos el producto $$Ax = \mtx{1 & 4 \\ 0 & -1 \\ 1 & 2} \mtx{2 \\ -1} =\mtx{-2 \\ 1 \\ 0}$$.
<br/>
Esto puede interpretarse como la combinación lineal de las columnas de $$A$$ según los coeficientes del vector $$x$$:
<br/>
$$Ax = \mtx{1 & 4 \\ 0 & -1 \\ 1 & 2} \mtx{2 \\ -1} = 2\mtx{1 \\ 0 \\ 1} + (-1) \mtx{4 \\  -1 \\  2} = \mtx{-2 \\ 1 \\ 0}$$.
<br/>
<br/>
En el desarrollo anterior, realizamos el camino inverso, escribiendo la combinación lineal como el producto de una matriz cuyas columnas son los vectores $$u_1 \cdots u_k$$ multiplicada  por un  vector con los coeficientes de la combinación lineal original.
{% endcapture %}

{% include collapsable.html  content=nota_cl title="Me perdí" %}

Por otra parte, voy a escribir el producto interno canónico $$\inner{u_k}{x}$$ como  $$\trans{u_k} x$$ (que recordemos, no es más que una forma de escribir un número):

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \mtx{ \trans{u_1} x \\ \trans{u_2} x \\ \vdots \\ \trans{u_k} x } $$

Finalmente, notemos que el vector de productos internos puede escribirse como un producto matricial:

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \mtx{ \trans{u_1} \\ \trans{u_2} \\ \vdots \\ \trans{u_k} } x $$

{% capture nota_factor_comun %}
Recien vimos el hecho de multiplicar una matriz a derecha por un vector como una combinación lineal de sus columnas. Eso es cierto, pero hay otro enfoque complementario (*que es la forma de multiplicar del CBC*):
<br/>
Al multiplicar una matriz por un vector a derecha, estamos haciendo un **producto interno *canonico*** entre cada una de las filas y el vector. Con el mismo ejemplo de la nota anterior:

$$Ax = \mtx{1 & 4 \\ 0 & -1 \\ 1 & 2} \mtx{2 \\ -1} = 
	\mtx{
		\inner{\mtx{1 \\ 4}}{\mtx{2\\-1}}	\\
		\inner{\mtx{0 \\-1}}{\mtx{2\\-1}}	\\
		\inner{\mtx{1 \\ 2}}{\mtx{2\\-1}}	}
	= \mtx{-2 \\ 1 \\ 0}$$.

{% endcapture %}

{% include collapsable.html  content=nota_factor_comun title="No, no saque la x como factor común... es álgebra de matrices" %}

Donde la última matriz, puede escribirse "sacando el transpuesto para afuera":

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \trans{ \mtx{u_1 & u_2 & \cdots & u_k} } x $$

Llamando a la matriz $$U \eqdef \mtx{u_1 & u_2 & \cdots & u_k}$$ llegamos a la expresión final:

$$\proy{S}{x} = U\trans{U} x $$

Concluímos entonces que:

$$[\mathcal{P}_{S}]_E = U\trans{U} $$

## Y qué pasa si estoy usando otro producto interno
Esto no vale, campeón.

Bueno... casí.

## ¿No hay una demostración formal? Mi hermano es matemático y me mira feo
Respecto a tu hermano que estudió en Exactas, mucho me temo que es un caso perdido (?), pero podemos analizar si realmente esta matriz hace lo que se supone que tiene que hacer...


## ¿Y la matriz de Haussh... Household... ¡la de refexión!?
Obtener la matriz de Householder (o de reflexión) es algo que se deduce rápidamente habiendo llegado aquí. Como no podía ser de otra forma en este blog, arrancamos con un dibujito.
