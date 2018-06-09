---
title: Hallando preimágenes
date: 2018-01-13 15:50:00 -0300
layout: post
tags: inicial TL
---

Una transformación lineal mapea los elementos de su dominio en elementos de su imagen. Aquí, pretendemos hacer el camino inverso: Dado un vector de la imágen de la transformación lineal, hallar todos los vectores del dominio que son mapeados allí al transformarlos. 

$$
\newcommand{\Trx}[1]{T\left( #1 \right)}
$$

# Aclaración respecto a espacios de dimensión finita
En este artículo vamos a trabajar con una tranformación lineal $$T:\VV \rightarrow \WW$$, y consideramos que $$\VV$$ es un espacio de dimensión finita, y por ende, podemos decir que existen bases de dicho espacio.

Este caso es el más simple para analizar, y el que utilizamos hasta el cansancio en la materia. Sin embargo, sobre todo cuando trabajamos en espacios de funciones como $$\Cf[1]$$ o similares, no podemos asumir que existe una base de dicho espacio, ni mucho menos calcularla.

# Forma general
Sea $$B=\{v_1, \ldots, v_k\}$$ una base de $$\VV$$, sobre la cual tenemos definida la transformación lineal $$T:\VV \rightarrow \WW$$ por:

$$
\begin{align}
	T(v_1)&=w_1  \nonumber \\
	&\vdots \label{eq:T} \\
	T(v_k)&=w_k \nonumber 
\end{align}
$$

Donde $$w_1, \ldots, w_k \in \WW$$, pero tengamos en cuenta que no necesariamente son una base de $$\WW$$ (esto pasaría sólo si $$T$$ fuese un epimorfismo).

**Problema**: Dado un vector $$y\in\WW$$ hallar todos los $$x\in\VV$$ tales que $$T(x)=y \tag{I}\label{eq:preimagen_y}$$.

Dado que tenemos una base de $$\VV$$, podemos escribir:

$$ x = \alpha_1 v_1 + \ldots + \alpha_k v_k $$

Ahora, reemplazo x en la ecuación \eqref{eq:preimagen_y}:

$$ T(\alpha_1 v_1 + \ldots + \alpha_k v_k) = y $$

Y como $$T$$ es una transformación lineal:

$$ \alpha_1 T(v_1) + \ldots + \alpha_k T(v_k) = y $$

Reemplazando $$T(v_i)$$ por las imagenes correspondientes, según mi definición \eqref{eq:T}:

$$ \begin{align} \alpha_1 w_1 + \ldots + \alpha_k w_k &= y \label{eq:cl_y} \end{align}$$ 

Llegamos así a escribir a $$y$$ como combinación lineal del conjunto de generadores de la imagen de $$T$$: $$\{w_1, \ldots, w_k\}$$.

*Nota*: Como ya sabrán, por sus conocimientos de espacios vectoriales, dicha combinación lineal puede ser única o no, dependiendo si el conjunto $$\{w_1, \ldots, w_k\}$$ es o no linealmente independiente.

No resta más que despejar las constantes $$\alpha_1, \ldots, \alpha_k$$ que satisfagan la ecuación \eqref{eq:cl_y}. Con dichos juegos de constantes, rearmamos la preimagenes correspondientes (el vector $$x$$):

$$x = \alpha_1 v_1 + \ldots + \alpha_k v_k$$

## Notación
Dada $$T:\VV \rightarrow \WW$$, llamanos $$T^{-1}(y)$$ al **conjunto** dado por: $$\{x\in \VV: T(x)=y\}$$. Equivalenemente, decimos que $$x$$ es la preimagen de $$y$$ a través de $$T$$.

## Ejemplo
Sea $$T:\RR[3] \rightarrow \RR[2 \times 2]$$, hallar $$T^{-1}\left( \mtx{3 & 5 \\ 0 & -1}\right)$$, donde:

$$\begin{align*}
	\Trx{\trans{\mtx{1 & 1 & 0}} } &= \mtx{1 & 2 \\ 0 & 0}\\
	\Trx{\trans{\mtx{0 & 1 & 0}} } &= \mtx{0 & 1 \\ 0 & 1}\\
	\Trx{\trans{\mtx{1 & 0 & 1}} } &= \mtx{2 & 2 \\ 0 & -2}\\
\end{align*}$$




**Resolución**: Debemos hallar los vectores $$x \in \RR[3]$$ tales que $$T(x) = \mtx{3 & 5 \\ 0 & -1} $$.

Como el conjunto $$B=\left\{\mtx{1\\1\\0}, \mtx{0\\1\\0}, \mtx{1\\0\\1} \right\} $$
es base de $$\RR[3]$$ *(verificarlo)*,  la transformación lineal queda unívocamente definida.


Como $$B$$ es base de $$\RR[3]$$, puedo escribir el vector $$x$$ como combinación lineal de sus elementos:

$$x = \alpha_1 \mtx{1\\1\\0} + \alpha_2 \mtx{0\\1\\0} + \alpha_3 \mtx{1\\0\\1} $$

Aplico la transformación lineal:

$$T(x) =  \Trx{ \alpha_1 \mtx{1\\1\\0} + \alpha_2 \mtx{0\\1\\0} + \alpha_3 \mtx{1\\0\\1} } $$

Como $$T$$ es transformación lineal:

$$T(x) =  \alpha_1 \Trx{\mtx{1\\1\\0}} + \alpha_2 \Trx{\mtx{0\\1\\0}} + \alpha_3 \Trx{\mtx{1\\0\\1}} $$

Reemplazando cada imagen, y como $$T(x)=\mtx{3 & 5 \\ 0 & -1}$$:

$$\mtx{3 & 5 \\ 0 & -1} =  \alpha_1  \mtx{1 & 2 \\ 0 & 0} + \alpha_2 \mtx{0 & 1 \\ 0 & 1} + \alpha_3 \mtx{2 & 2 \\ 0 & -2}$$


Lo cual da el sistema:

$$
\left \{
	\begin{align}
		 \alpha_1 & &           &+& 2\alpha_3 &= 3 \nonumber\\
		2\alpha_1 &+& 1\alpha_2 &+& 2\alpha_3 &= 5 \label{eq:sistema_eq_ejemplo}\\
		          & & 1\alpha_2 &-&2\alpha_3 &= -1 \nonumber
	\end{align}
\right.
$$

De donde se despeja: $$\alpha_1=2-\alpha_2,\;  \alpha_3=(1+\alpha_2)/2,\;   \alpha_2 \in \RR$$

Con dichos valores, recomponemos el vector $$x$$:
 
$$x = (2-\alpha_2) \mtx{1\\1\\0} + \alpha_2 \mtx{0\\1\\0} + (1+\alpha_2)/2 \mtx{1\\0\\1},\, \alpha_2 \in \RR$$

Reordenando y utilizando la notación de $$T^{-1}$$ obtenemos finalmente:

$$T^{-1}\left( \mtx{3 & 5\\0 & -1} \right) = \lambda \mtx{-1/2\\0\\1/2} + \mtx{5/2\\2\\1/2},\; \lambda \in \RR$$

# Relación entre espacio nulo y nucleo de la TL
En el ejemplo anterior, el vector $$\trans{ \mtx{-1/2 &0&1/2} }$$ es también la solución del sistema homogéneo asociado al sistema de ecuaciones \eqref{eq:sistema_eq_ejemplo}, o visto de otra forma, el generador del espacio nulo de la matriz asociada al sistema.

Este vector, es también el generador del núcleo de la tranformación lineal. Es fácil darse cuenta que si $$x$$ es **una** preimagen de $$y$$ por $$T$$ (esto es, si $$T(x)=y$$), al sumarle algo del núcleo de la tranformación, obtenemos otra preimagen de $$y$$. Es decir, si $$\eta$$ pertenece al núcleo de $$T$$, luego $$x+k \eta$$ es preimagen de $$y$$, pues $$T(x+k \eta) = T(x)+ k T(\eta) = y + k 0_{\RR[3]} = y$$

Esta es una relación importante que queda a cuenta del lector profundizar.
 