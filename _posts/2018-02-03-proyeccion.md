---
title: Matriz de Proyección
date: 2018-02-03 06:24:00 -0300
tags: intermedio proyecciones PI
layout: post
---

En la materia y en los apuntes, se menciona un método "sencillo" para armar una matriz de proyección en base canónica con PIC en $$\CC^n$$.
Sin embargo, en ningún lugar se demuestra ni explica este resultado --muy utilizado en resueltos pero rara vez comprendido--.

El resultado se puede enunciar así:

> Sea $$\VV=\CC[n]$$ con el PIC, y sea $$U$$ una matriz que tiene por columnas una BON de $${S} \subset \CC[n]$$. La matriz en base canónica de la proyección ortogonal sobre $${S}$$ es: $$[\mathcal{P}_{S}]_E = U\herm{U} $$
{:.teorema}

# Demostración
Si bien rara vez se demuestra este resultado en la cursada, estas abundan y las hay para todos los gustos.

En lo personal, me encanta la segunda demostración ya que fue la primera que descubrí y es muy intuitiva, y hace gala del álgebra matricial de forma muy sencilla pero potente. Sin embargo, por motivos didácticos (tal vez) vamos a empezar demostrando un caso particular que luego retomaremos al final en su forma completa.

## Demostración Teórica Particular en dimensión 1
> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

En esta primera parte, vamos a analizar el caso particular cuando $$S = \gen{w}$$, es decir, cuando $$S$$ es un espacio de dimensión 1. Pidamos ademas que $$ \norm{w}=1 $$.

Sabemos que $$\proy{S}{x}$$ es una transformación lineal. Por lo tanto, como $$\VV = S \bigoplus \ortog{S}$$, alcanza con verificar que $$\proy{S}{S}=S$$ y $$\proy{S}{\ortog{S}} = \{\vec{0}\}$$

Sea $$ s \in S \then  \exists k \in \CC : s = k u$$.

Luego $$w\herm{w} s = w \herm{w} k w = k w (\herm{w}w) = kw \norm{w}^2 = kw = s$$

Por otro lado, sea $$u \in \ortog{S}$$, es decir, $$u \perp w $$.

Entonces $$w\herm{w} u = w (\inner{w}{u}) = w(0) = \vec{0}$$

Por lo tanto, podemos concluir que $$P_S(x) = w\herm{w} x$$, y por ende, $$[P_S]_E = w\herm{w}$$.


## Deducción constructiva
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

Definiendo a la matriz $$U \eqdef \mtx{u_1 & u_2 & \cdots & u_k}$$, tenemos entonces que su hermítica es la matriz $$\herm{U} = \mtx{ \herm{u_1} \\ \herm{u_2} \\ \vdots \\ \herm{u_k} }$$

Reemplanzando por $$U$$ y $$\herm{U} $$ se llega a la expresion:
		
$$\proy{S}{x} = U\herm{U} x $$

Concluímos entonces que:

$$[\mathcal{P}_{S}]_E = U\herm{U} $$

### Explicación del funcionamiento
Al hacer $$U\herm{U} x$$, lo que estamos haciendo es:
  - Obtener cada una de las proyecciones de $$x$$ sobre los elementos $$u_i$$ (haciendo $$\herm{U}x$$, analizar la similitud evidente con $$\inner{u_i}{x} = \herm{u_i} x$$).
  - Armar la combinación lineal con los elementos de la base de $$S$$, los $$\{u_1, \cdots, u_k\}$$.
  
Si bien hay muchísimas otras formas de interpretar $$U\herm{U} x$$, esta resume la línea de la demostración, la cual no es más que una vuelta de tuerca de la fórmula de proyección común y silvestre.

## Demostración Teórica (caso general)
La demostración anterior es rigurosa y "correcta" matemáticamente hablando, por lo cual no habría necesidad de decir más.
Sin embargo, ahora que aprendimos a operar con matrices un poquito mejor, estamos en condiciones de generalizar la primer demostración para un subespacio $$S$$ de dimensión finita arbitraria.

(En mi opinión, noten que esta demostración es más "pobre", en el sentido que demuestra que $$U\herm{U}$$ es la matriz de proyección en cuestión, pero no explica de dónde salió ni permite hacer un razonamiento geométrico, ni obtener un panorama general, que como ingenieros nos gustaría visualizar).


> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Sabemos que $$\proy{S}{x}$$ es una transformación lineal. Por lo tanto, como $$\VV = S \bigoplus \ortog{S}$$, alcanza con verificar que $$\proy{S}{S}=S$$ y $$\proy{S}{\ortog{S}} = \{\vec{0}\}$$

Sea $$B' = \{u_1, \cdots, u_k\}$$ BON de $$S \subset \CC[n]$$. Y sea $$U=\mtx{u_1 & \cdots & u_k}$$ la matriz que tiene dichos vectores por columnas.

Sea $$s \in S \then  \exists r_i \in \CC, i=1,\cdots,k : s = r_1 u_1 + r_2 u_2 + \cdots + r_k u_k$$.

Luego:

$$\begin{align*}
	U\herm{U} s &= U \herm{U} \left(r_1 u_1 + r_2 u_2 + \cdots + r_k u_k\right) \\
				&= U \herm{U} r_1 u_1 + U \herm{U} r_2 u_2 + \cdots + U \herm{U} r_k u_k \\
				&= r_1 U \left(\herm{U} u_1\right) + r_1 U \left(\herm{U} u_1\right) + \cdots + r_k U \left(\herm{U} u_k\right) \\
				&= r_1 U \mtx{1\\0\\\vdots\\0} + r_2 U \mtx{0\\1\\ \vdots\\0} + \cdots + r_k U \mtx{0\\0\\ \vdots\\1} \\
				&= r_1 u_1 + r_2 u_2 + \cdots + r_k u_k \\
				&= s
\end{align*}$$

Donde hicimos varias cosas:
  - Distribuimos el producto $$U\herm{U}$$ sobre los términos la combinación lineal.
  - Asociamos los escalares $$r_i$$ fuera del producto de matrices, y asociamos el producto $$U\herm{U}u_i$$ como $$U(\herm{U}u_i)$$
  - Consideramos el producto $$\herm{U}u_i$$ como el producto escalar entre cada una de las columnas de $$U$$ con el vector $$u_i$$. Ya que éstas son BON, dicho producto vale 0 para todas las columnas excepto aquella que contiene $$u_i$$, en cuyo caso vale 1.
  - Consideramos el producto de $$U$$ con el vector que tiene un 1 en la posición i-ésima como la combinación lineal de las columnas de $$U$$ con los coeficientes del vector, resultando $$1 u_i$$ por lo anteriormente dicho.

Cumplida esta parte, resta analizar el complemento ortogonal. Sea $$w \in \ortog{S}$$, es decir, $$w \perp u_i, \, i=1,\cdots,k $$.

Entonces $$\herm{U} w = \vec{0}$$ pues $$w$$ es ortogonal a las columnas de $$U$$. Y por lo tanto, $$U\herm{U} w = \vec{0} \forall w \in \ortog{S}$$.

Por lo expuesto, podemos concluir que $$P_S(x) = w\herm{w} x$$, y por ende, $$[P_S]_E = w\herm{w}$$.


## Demostración vía transformaciones lineales
Si lo anterior no fue suficiente aún hay resta otra demostración posible, relacionada con la matriz de transformación lineal en una base particular (*spoiler*: la base en que queda diagonal --sí, la de autovectores, pero ¿qué es eso?--).



> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Sea $$D=\{u_1, u_2, \cdots, u_k, w_{k+1}, w_{k+2}, \cdots, w_{n}\}$$ BON de $$\CC[n]$$. Donde $$B'=\{u_1, u_2, \cdots, u_k\}$$ BON de $${S}$$, y $$C=\{w_{k+1}, w_{k+2}, \cdots, u_{n}\}$$ BON de $$\ortog{S}$$.

Vamos a analizar por un momento, cómo queda $$[P_S]_D$$:

$$\begin{align*}
	\proy{S}{u_1} = u_1 \\
	\proy{S}{u_2} = u_2 \\
	\vdots \\
	\proy{S}{u_k} = u_k \\
	\proy{S}{w_{k+1}} = \vec{0} \\
	\proy{S}{w_{k+2}} = \vec{0} \\
	\vdots \\
	\proy{S}{w_{n}} = \vec{0} \\
\end{align*}$$

Por lo tanto, resulta:

$$ [P_S]_D = \mtx{
1 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
\vdots&\vdots& &\vdots&     \vdots & \vdots &   & \vdots \\
0 & 0 & \cdots & 1 &             0 & 0 & \cdots & 0 \\
0 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
\vdots&\vdots& &\vdots&     \vdots & \vdots &   & \vdots \\
0 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\ } $$

La cual podemos escribir de forma compacta como la matriz en bloques:

$$ [P_S]_D = \left[\begin{array}{c|c}
	I_{k} & O_{k\times (n-k)} \\
	\hline
	O_{(n-k)\times k} & O_{n-k}
\end{array}\right] $$

Donde $$I_k$$ es la matriz identidad de $$k\times k$$ y $$O_{n-k}$$ es la matriz nula de $$(n-k)\times (n-k)$$.

Ahora multiplicamos por los cambios de base correspondientes para obtener la matriz de $$[P_S]_E$$:

$$[P_S]_E = C_{DE}\, [P_S]_D\, C_{ED} $$

Donde por definición: $$C_{DE} = [u_1, u_2, \cdots, u_k, w_{k+1}, w_{k+2}, \cdots, w_{n}]$$ y $$C_{ED} = C_{DE}^{-1}$$.

Pero como las columnas de $$C_{DE}$$ son BON de $$\CC[n]$$ es fácil verificar que $$C_{DE}\, \herm{C_{DE}} = I_n$$ y $$\herm{C_{DE}}\, C_{DE} = I_n$$ (solo basta ver el producto matricial como los productos internos de las columnas).

Dado lo anterior, podemos concluir que $$C_{DE}^{-1} = \herm{C_{DE}}$$. Las matrices que cumplen con esta propiedad se llaman "Hermíticas" --como la banda, pero con "í"--. En el caso particular que las matrices fuesen reales, es decir: $$C_{DE}^{-1} = \trans{C_{DE}}$$ se la llama "Matriz Ortogonal" (pero todo esto se ve bien en la guía 5).


Dicho esto, podemos reescribir la relación anterior como:

$$[P_S]_E = C_{DE}\, [P_S]_D\, \herm{C_{DE}} $$

A fin de evitar más líos, voy a definir las matrices $$U \in \CC[n\times k]$$ y $$W \in \CC[n\times (n-k)]$$ como:

$$\begin{align*}
	U &\eqdef \mtx{u_1 & u_2 & \cdots & u_k} \\
	W &\eqdef \mtx{w_{k+1} & w_{k+2} & \cdots & w_n}
\end{align*}$$

Lo cual permite escribir:

$$\begin{align*} C_{DE} &= \left[\begin{array}{c|c}
	U & W
\end{array}\right] \end{align*}$$

Ahora podemos hacer alarde de que sabemos multiplicar matrices por bloque. Si no sabéis, es muy fácil: Simplemente hay que multiplicar los bloques de las matrices como si fuesen escalares, teniendo el cuidado de armar bloques de dimensiones consistentes a la hora de multiplicar. Veamos:

$$\begin{align*}
	[P_S]_E &= C_{DE} \, [P_S]_D \, \herm{C_{DE}} \\
			&=
%(2)%% PRODUCTO 3 Matrices
	\left[\begin{array}{c|c}
		U & W
	\end{array}\right]
% por
	\left[\begin{array}{c|c}
		I_{k} & O_{k\times (n-k)} \\
		\hline
		O_{(n-k)\times k} & O_{n-k}
	\end{array}\right]
% por
	\mtx{\herm{U} \\ \hline \herm{W}} \\ %LINE END
				&= 
%(3)%% PRODUCTO 2 Matrices
	\left[\begin{array}{c|c}
		U & W
	\end{array}\right]
% por
	\left[\begin{array}
		I_{k}\herm{U} + O_{k\times (n-k)} \herm{W}\\
		\hline
		O_{(n-k)\times k}\herm{U} + O_{n-k} \herm{W}
	\end{array}\right] \\ %LINE END
				&= 
%(4)%% PRODUCTO 2 Matrices				
	\left[\begin{array}{c|c}
		U & W
	\end{array}\right]
% por
	\mtx{
		\herm{U}\\
		\hline
		O_{(n-k)\times n}
		}
	\\ %LINE END
				&=	U \herm{U} + W O_{(n-k)\times n} \\
				&=U \herm{U}
\end{align*}$$


> Concuerdo que esta demostración es un quilombo tremendo, pero me sirve de ejemplo para mostrar cómo operar con matrices con bloques --es la principal razón por la cual me molesté en escribir esto, porque es bonita... o al menos tiene linda peronalidad (?).
{:.note}

# Todo muy lindo, pero qué pasa si estoy usando otro producto interno
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


# ¿Y la matriz de Haussh... Household... ¡la de refexión!?
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

