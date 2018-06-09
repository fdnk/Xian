---
title: Matriz de Proyección
date: 2018-02-03 06:24:00 -0300
tags: intermedio proyecciones PI
layout: post
---

Hay una forma "fácil" de obtener una matriz de proyección en $$\CC[n]$$ con el PIC. Se menciona en el apunte de la materia y se usa extensivamente en los resueltos (los cuales no tendrían que usar), pero rara vez se explica.

A continuación voy a enunciar el resultado y proceder a explicarlo luego:

> Sea $$\VV=\CC[n]$$ con el PIC, y sea $$U$$ una matriz que tiene por columnas una BON de $${S} \subset \VV$$. La matriz de la proyección ortogonal sobre $${S}$$ es: $$[\mathcal{P}_{S}]_E = U\herm{U} $$
{:.teorema}

## Deducción de la matriz de proyección
> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Para evitar complejidad adicional, vamos partir de suponer que disponemos de $$B$$ que es una base ortogonal del subespacio $${S} \subset \VV$$ sobre el cual queremos proyectar ortogonalmente. Llamemos $$B=\{v_1, v_2, \cdots, v_k\}$$ BOG de $${S}$$.

La "fórmula de la proyección" nos permite escribirla como:

$$\proy{S}{x} = \frac{\inner{v_1}{x}} {\inner{v_1}{v_1}} v_1 + \frac{\inner{v_2}{x}} {\inner{v_2}{v_2}} v_2 + \cdots + \frac{\inner{v_k}{x}}{\inner{v_k}{v_k}} v_k$$

Lo primero que vamos a hacer es normalizar la base. Vamos a trabajar sobre la base $$B'=\{u_1, u_2, \cdots, u_k\}$$ de $${S}$$. Para ello, tomamos $$u_j \eqdef \frac{1}{\norm{v_j}} \, v_j$$

Usando esta base de $${S}$$, la formula de proyección queda más compacta:

$$\proy{S}{x} = \inner{u_1}{x} u_1 + \inner{u_2}{x} u_2 + \cdots + \inner{u_k}{x} u_k$$

Queda claro que  $$\inner{u_j}{x} \in \CC$$, es decir, los productos internos son simplemente números; así la expesión anterior es una combinación lineal de los vectores $$u_j$$, y procedemos a expresarla matricialmente:

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

Por otra parte, voy a escribir el producto interno canónico $$\inner{u_k}{x}$$ como  $$\herm{u_k} x$$ (que recordemos, no es más que una forma de escribir un número):

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \mtx{ \herm{u_1} x \\ \herm{u_2} x \\ \vdots \\ \herm{u_k} x } $$

Finalmente, notemos que el vector de productos internos puede escribirse como un producto matricial:

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \mtx{ \herm{u_1} \\ \herm{u_2} \\ \vdots \\ \herm{u_k} } x $$

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

{% include collapsable.html  content=nota_factor_comun title="Explicación de cómo salio esa x afuera" %}

Ahora simplemente puedo "sacar el hermítico" afuera de la matriz:

$$\proy{S}{x} = \mtx{u_1 & u_2 & \cdots & u_k}  \herm{ \mtx{u_1 & u_2 & \cdots & u_k} } x $$

Definiendo a la matriz $$U \eqdef \mtx{u_1 & u_2 & \cdots & u_k}$$ llegamos a la expresión final:

$$\proy{S}{x} = U\herm{U} x $$

Concluímos entonces que:

$$[\mathcal{P}_{S}]_E = U\herm{U} $$

## Y qué pasa si estoy usando otro producto interno
Esto no vale, campeón.

Bueno... casí. Hay algo que se llama "Matriz de Producto Interno (o Matriz de Gram)" que ya no se da en la materia, pero que permitiría llegar a una expresión similar para un PI arbitrario (seguramente la vieron en algún resuelto para hacer [productos internos especificados por una BON]({{ site.baseurl }}{% link _posts/2018-01-19-pi_bon.md %})  ).

Para este curso de álgebra, en el caso de tener un PI distinto del canónico, o coordenadas en alguna base distinta de la canónica, tendremos que obtener *la matriz en bases dadas de la transformación lineal que proyecta sobre el subespacio S*.

{% capture nota_cl %}
Sean $$C=\{c_1, c_2, \cdots, c_k\}$$ y $$D$$ bases de $$\VV$$. La matriz de proyección en bases $$C,D$$ sobre $$S\subset \VV$$ se obtiene como:
<br/>
<br/>
$$[P_S]_{CD} = \mtx{ [\proy{S}{c_1}]_D \quad [\proy{S}{c_2}]_D \quad \cdots \quad [\proy{S}{c_k}]_D  }$$
<br/>
<br/>
Esto no es más que la definición genérica de matriz de transformación lineal. Acá hay que armar la fórmula de proyección, proyectar los elementos de la base $$C$$ y escribir sus coordenadas de la base $$D$$ como columnas en la matriz. Tedioso tal vez, pero vale para cualquier PI y cualquier espacio, sean polinomios, exponenciales, o lo que fuese.
<br/>
<br/>
**Recuerden que a veces es más fácil proyectar sobre $$\ortog{S}$$ y obtener $$[P_S]_{CD} = C_{CD} - [P_{\ortog{S}}]_{CD}$$**
<br/>
(Antes solía haber una $$I$$ en esa fórmula, pero como las bases son distintas apareció la matriz de cambio de base. Tiene sentido, pues $$C_{CC} = I$$, y no aclaro más porque oscurece).
{% endcapture %}

{% include collapsable.html  content=nota_cl title="Cómo obtener la matriz de proyección en el caso general" %}

## ¿Y la matriz de Haussh... Household... ¡la de refexión!?
Obtener la matriz de Householder (o de reflexión) es algo que se deduce rápidamente habiendo llegado aquí.

La reflexión sobre un subespacio $${S}$$ se define como:

$$\mathcal{R}_S(x) = \proy{S}{x} - \proy{\ortog{S}}{x}$$

Podemos prescindir de la proyección sobre $$\ortog{S}$$ usando la siguente identidad:

$$\proy{\ortog{S}}{x} = x -  \proy{S}{x}$$

Quedando:

$$\mathcal{R}_S(x) = 2\proy{S}{x} - x$$

Lo cual podemos escribir matricialmente como:

$$[\mathcal{R}_S]_E = 2U\herm{U} - I$$

Que bueno... no es exactamente la forma de la matriz de Householder de la guia de ejercicios.


### Matriz de Householder - Reflexión por un plano
La idea geométrica tras la matriz de reflexión, es reflejar por un plano (que pasa por el origen).

Si estamos en $$\RR^3$$, un plano se describe fácilmente por su vector normal. O sea que, en lugar de tener
la matriz $$U$$ con los generadores del plano, vamos a tener un vector $$w$$ normal al plano, es decir, $$\ortog{S}=\gen{w}$$. **Vamos a pedir que $$||w||=1$$** para que sea BON de $$\ortog{S}$$.

Así que rescatamos la expresión de la reflexión, pero ahora escribiendo todo en base al complemento ortogonal de S:

$$\mathcal{R}_S(x) = x - 2\proy{\ortog{S}}{x}$$

Y como $$\{w\}$$ es BON de $$\ortog{S}$$:

$$[\mathcal{R}_S]_E = I - 2w\herm{w}$$

Que es la expresión usual para la matriz de Householder en nuestro curso.

> Es importante remarcar que si bien llegamos a dos expresiones distintas, la matriz es exactamente la misma en ambos casos.
{:.success}

