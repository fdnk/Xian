---
title: Proyecciones por pedazos
date: 2017-12-15 06:24:00 -0300
tags: intermedio
layout: post
---
Este es un ejercicio de final. Nos pide "extender una proyección" de forma tal que proyecte en un subespacio "más grande". Hay varias formas de encarar el ejercicio, pero analizando con cuidado, podemos llegar a conclusiones muy interesantes en el proceso.

$$
\newcommand{\inner}[2]{ \left \langle {#1}, {#2}  \right \rangle }
\newcommand{\gen}[1]{\text{gen}\left\{#1\right\} }
\newcommand{\Real}{\mathbb{R}}
\newcommand{\mtx}[1]{ 

	\begin{bmatrix}
		#1
	\end{bmatrix}

}
\newcommand{\Amatrix}{\frac{1}{6} 
\mtx{
5 & 2 & 1 & 0\\
2 & 2 & -2 & 0\\
1 & -2 & 5 & 0\\
0 & 0 & 0 & 0
}}
$$

Sea $$h:^4 \Real\rightarrow \Real^4$$ tal que $$h(x)=A x$$ para $$A=\Amatrix$$

Considerando que $$h$$ es la proyección ortogonal sobre cierto subespacio
$$W$$ de $$\Real^4$$, defina $$f:\Real^4 \rightarrow \Real^4$$
tal que sea la proyección ortogonal sobre 
$$U = W + \gen{ \mtx{0\\-1\\-1\\0} }$$.


# Solución rápida
Observamos que la tercer columna de $$A$$ es combinación lineal de las primeras dos: $$A_3=A_1-2 A_2$$. Por otro lado, las dos primeras columnas son linealmente independientes entre sí ya que no son múltiplos.

Obtenemos entonces $$col(A) = \gen{ \mtx{5\\2\\1\\0}, \mtx{2\\2\\-2\\0} }$$

El espacio $$W$$ donde proyecta la transformación lineal $$h$$ no es otra cosa que $$col(A)$$, ya que es la imagen de la transformación lineal. Por lo tanto, resulta que $$U = \gen{ \mtx{5\\2\\1\\0}, \mtx{2\\2\\-2\\0} } + \gen{ \mtx{0\\-1\\-1\\0} }$$. Observamos que estos tres generadores son li (verificarlo), por lo cual $$dim(U)=3$$.

En lugar de hacer Gram-Schmidt para obtener una base ortogonal de $$U$$, podemos proyectar sobre $$U^{\perp}$$ que al tener dimensión 1, no necesito hallar una BOG.

Vemos que todos los generadores de $$U$$ poseen un 0 en la última componente, por lo cual, $$\mtx{0&0&0&1}^T \in U^{\perp}$$ y como $$dim(U^{\perp}=4-3=1$$ es base del subespacio. Luego

$$P_{U^{\perp}} (x) = \inner{ \mtx{0\\0\\0\\1}}{x} \mtx{0\\0\\0\\1} = \mtx{0\\0\\0\\x_4} $$

Y usando que $$x=P_U(x) + P_{U^{\perp}}(x)$$:

$$P_{U} (x) = x-\inner{ \mtx{0\\0\\0\\1}}{x} \mtx{0\\0\\0\\1} = \mtx{x_1\\x_2\\x_3\\x_4}-\mtx{0\\0\\0\\x_4}=\mtx{x_1\\x_2\\x_3\\0} $$

# Camino interesante
En el caso anterior abusamos de encontrar las cosas "a ojo", aquí vamos a analizar una solución más general (si se quiere) que puede ayudar si no corremos con tantas ventajas como el caso anterior.


Llamemos $$S=\gen{ \mtx{0\\-1\\-1\\0} }$$, y $$W=col(A)$$ por lo dicho anteriormente, donde $$dim(W)=2$$. Debemos hallar $$P_{W+S}(x)$$, donde llamamos $$U=W+S$$. Podemos demostrar que $$P_{A+B}(x) = P_{A}(x) + P_{B}(x)$$ en el caso que $$A \perp B$$. Este es el hecho por el cual, en la fórmula de la proyección, podemos sumar las proyecciones sobre cada uno de los elementos de la base ortogonal de $$T$$, $$\{t_1, \ldots, t_k\}$$:

$$P_T(x) = \frac{\inner{t_1}{x}} {\inner{t_1}{t_1}} + \ldots + \frac{\inner{t_k}{x}}{\inner{t_k}{t_k}}$$

Por lo tanto, si $$S$$ fuese un subespacio ortogonal a $$W$$, la solución sería simplemente sumar ambas proyecciones; como podemos verificar, este no es el caso.
Sin embargo, es un problema similar al que nos topamos al querer proyectar sobre un espacio del cual tenemos una base que no es ortogonal. ¿Qué hacemos entonces? Sí, Gram-Schmidt (cuando no podemos huír de él).

El proceso de Gram-Schmidt consiste en, a cada nuevo vector a agregar a la BOG, restarle la proyección sobre esta. O visto de otra forma, antes de agregar un vector a la BOG, se toma la proyección sobre el complemento ortogonal de ésta, y ese es el vector que se agrega, ya que es ortogonal a el resto de los elementosde la base.

Dicho con cuentitas, si $$\{v_1, \ldots, v_k\}$$ es la base a ortogonalizar, tomamos primero $$B_1=\{v_1\}$$, el cual es una BOG. Ahora, agregamos a esta base $$u_2 = P_{B_1^\perp} (v_2)$$, obteniendo así la BOG $$B_2=\{v_1, u_2\}$$. Luego agregamos $$u_3 = P_{B_2^\perp} (v_3)$$ y continuamos extendiendo la base hasta agregar todos los vectores faltantes.

## Resolviendo el ejercicio
Imaginemos que disponemos de una BOG de $$U$$: $$\{u_1, u_2, u_3\}$$. La fórmula de proyección quedaría:

$$P_U(x) = \frac{\inner{u_1}{x}} {\inner{u_1}{u_1}} + \frac{\inner{u_2}{x}} {\inner{u_2}{u_2}}  + \frac{\inner{u_3}{x}}{\inner{u_3}{u_3}}$$

Supongamos tambien que $$\{u_1, u_2\}$$ es una BOG de $$W$$. Podríamos decir que:

$$P_W(x) = \frac{\inner{u_1}{x}} {\inner{u_1}{u_1}} + \frac{\inner{u_2}{x}} {\inner{u_2}{u_2}}$$

Donde $$P_W(x)$$ no es otra cosa que la proyección que nos dan: $$h(x)$$. Reemplazando estos dos términos en la fórmula de proyección sobre $$U$$ tenemos:

$$P_U(x) = h(x) + \frac{\inner{u_3}{x}}{\inner{u_3}{u_3}}$$


Imaginar eso casí resolvió el problema, solo faltaría hallar $$u_3$$ que complete la base y sea ortogonal al conjunto $$\{u_1, u_2\}$$, que son una BOG de $$W$$. Para ello, vamos a definir $$u_3 = P_{W^\perp}\left(\mtx{0\\-1\\-1\\0}\right)$$, que es la proyección del generador de $$S$$ que faltaba.

Dicha proyección la podemos calcular en base a la proyección sobre $$W$$, dada por $$h(x)$$:

$$
\begin{align*}%*
u_3 &= \mtx{0\\-1\\-1\\0} - P_W\left(\mtx{0\\-1\\-1\\0}\right)\\
u_3 &= \mtx{0\\-1\\-1\\0} - h\left(\mtx{0\\-1\\-1\\0}\right)\\
u_3 &= \mtx{0\\-1\\-1\\0} - \mtx{-1/2\\0\\-1/2\\0}= \mtx{1/2\\-1\\-1/2\\0}
\end{align*}%*
$$

Finalmente, reemplazamos:

$$
\newcommand{\UUt}{\frac{1}{4}\mtx{
   1 & -2 & -1 &  0\\
  -2 &  4 &  2 &  0\\
  -1 &  2 &  1 &  0\\
   0 &  0 &  0 &  0 }}
   
\begin{align*}%*
P_U(x) 	&= h(x) + \frac{\inner{u_3}{x}}{\inner{u_3}{u_3}}\\
		&= h(x) + \frac{1}{\inner{u_3}{u_3}} (u_3^T {x}) u_3 \tag{def. PIC}\\
		&= h(x) + \frac{1}{\inner{u_3}{u_3}} u_3 (u_3^T {x}) \tag{nota I}\\
		&= h(x) + \frac{1}{\inner{u_3}{u_3}} (u_3 u_3^T) {x} \tag{nota II}\\
		&= A x + \frac{1}{\inner{u_3}{u_3}} (u_3 u_3^T) {x} \tag{def h(x)}\\
		&= \left(A + \frac{1}{\inner{u_3}{u_3}} (u_3 u_3^T)\right) x \\
		&= \left(\Amatrix + \frac{2}{3} \UUt \right) x \\
		&= \mtx{1&0&0&0\\0&1&0&0\\0&0&1&0\\0&0&0&0} x\\
		&= \mtx{x_1\\x_2\\x_3\\0}
\end{align*}%*
$$

  - *Nota I*: Como $$(u_3^T {x})\in \Real$$ puedo conmutar en el producto matricial.
  - *Nota II*: Puedo asociar de esa forma el producto para obtener la matriz $$u_3 u_3^T$$ y despejar $$x$$.

El proceso anterior puede parecer bastante confuso, pero no es más que una forma algebráicamente elegante de llegar al resultado. El lector puede resolverlo a su manera llegando al mismo resultado en más o menos pasos. 
