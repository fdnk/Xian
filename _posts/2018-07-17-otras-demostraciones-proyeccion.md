---
title: Otras Demostraciones de la Matriz de Proyección
date: 2018-07-17 22:36:00 -0300
tags: intermedio proyecciones PI
layout: post
---
En este post menciono el resto de las demostraciones que encontré o se me ocurrieron para obtener la matriz de la transformación lineal que proyecta sobre un subespacio $$S \subset \KK[n]$$.

**Indice**
  - [Demostración "oficial" usando cuadrados mínimos](otras-demostraciones-proyeccion.html#usando-cuadrados-mínimos)
  - [Diagonalizando la matriz unitariamente (fácil y rápido usando autovectores)](otras-demostraciones-proyeccion.html#demostración-vía-diagonalización-unitaria)
  - [Usando sólo Transformaciones Lineales (lindo porque trabajo con matrices por bloques)](otras-demostraciones-proyeccion.html#demostración-vía-transformaciones-lineales)
  - [Demostración teórica para dimensión 1 (muy conceptual)](otras-demostraciones-proyeccion.html#demostración-teórica-particular-en-dimensión-1)
  - [Demostración teórica general (cuando querés hacer todo de la forma más difícil y oscura posible)](otras-demostraciones-proyeccion.html#demostración-teórica-caso-general)
  
**La demostración más interesante (para mí)**
  - [Armar la matriz jugando con la fórmula de proyección]({{ site.baseurl }}{% post_url 2018-02-03-proyeccion %})

# Usando Cuadrados Mínimos
Agarrarse de acá para demostrar esto es como usar un cañon para matar un mosquito (¿cómo le apuntas?) pero lo voy a mencionar por completitud, ya que es la demostración "oficial".

La siguiente deducción que se puede encontrar en la página 97 del [apunte de Muszkats y Pustilnik](http://materias.fi.uba.ar/6108/libro.html), nombrado Teorema 3.19 (revisión del 2 de abril del 2017), dentro del tema de Cuadrados Mínimos (ya que tenían el cañon, lo usaron --y es genial también--).

> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Partimos de un sistema $$Ax = b$$ que no necesariamente tiene solución, y planteamos la solución por cuadrados mínimos, que desemboca en resolver $$A\hat{x} = \proy{S}{b}$$. La solución de este problema viene dado mediante las ecuaciones normales: $$(\herm{A}A)\hat{x} = \herm{A}b$$

En este marco teórico, tomemos $$b\in\CC[n]$$ un vector cualquera y una matriz $$A\in \CC[n \times k]$$ tal que en sus columnas posee una BON de un subespacio $$S\subset\CC[n]$$ de dimensión $$k$$. En este caso el $$\hat{x}\in\CC[k]$$ no nos interesa.

Por un lado, tenemos que $$\herm{A}A = I_k$$. Esto nos conduce a:

$$\hat{x} = \herm{A}b$$

Ahora metemos eso de vuelta en la ecuación original:

$$\begin{align*}
A\hat{x} = \proy{S}{b} \\
A\herm{A}b = \proy{S}{b}
\end{align*}$$

Como esta expresión vale $$\forall b \in \CC[n]$$, signfica que si $$A$$ posee en sus columnas una BON de $$S$$ entonces:

$$[\mathcal{P}_S]_E = A\herm{A} $$

$$\qed$$

# Demostración vía diagonalización unitaria
Podemos obtener la matriz $$[\mathcal{P}_{S}]_E$$ analizando sus autovectores y autovalores. Una demostración utilizando sólo los temas de transformaciones lineales y producto interno [se puede encontrar acá](otras-demostraciones-proyeccion.html#demostración-vía-transformaciones-lineales).

> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Sabemos que $$\forall x \in S: \proy{S}{x} = x \then x \in S_{\lambda=1}$$

Y que además: $$\forall x \in \ortog{S}: \proy{S}{x} = \vec{0} = 0x \then x \in S_{\lambda=0}$$

Llamemos $$\{u_1, \cdots, u_k\}$$ BON de $$S$$ y $$\{w_{k+1}, \cdots, w_n\}$$ BON de $$\ortog{S}$$.

Como $$\VV = S \bigoplus \ortog{S}$$ podemos obtener una BON de $$\VV$$ uniendo una BON de $$S$$ con una de $$\ortog{S}$$. Esta resulta una base ortonormal formada por autovectores de $$[\mathcal{P}_{S}]_E$$. Por ende podemos descomponer unitariamente a la matriz en $$\CC[n](\CC)$$ como:

$$\begin{align}
[\mathcal{P}_{S}]_E &= P D \herm{P} \\
[\mathcal{P}_{S}]_E &= \mtx{u_1, \cdots, u_k, w_{k+1}, \cdots, w_n} \mtx{
1 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
\vdots&\vdots& &\vdots&     \vdots & \vdots &   & \vdots \\
0 & 0 & \cdots & 1 &             0 & 0 & \cdots & 0 \\
0 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\
\vdots&\vdots& &\vdots&     \vdots & \vdots &   & \vdots \\
0 & 0 & \cdots & 0 &             0 & 0 & \cdots & 0 \\ } \mtx{\herm{u_1}\\ \vdots \\ \herm{u_k}\\ \herm{w_{k+1}} \\ \vdots \\ \herm{w_n} }
\end{align}$$

(Los detalles de cómo hacer ese producto matricial en forma de matrices por bloques se pueden ver [en la siguiente demostración](otras-demostraciones-proyeccion.html#demostración-vía-transformaciones-lineales).)

Vemos que los $$k$$ primeros vectores de $$P$$, los que generan $$S$$, quedan multiplicados por unos; mientras que aquellos que generan $$\ortog{S}$$ quedan multiplicados por ceros. Podemos eliminar todos los vectores que se anulan, quedando:

$$[\mathcal{P}_{S}]_E = \mtx{u_1, \cdots, u_k} I_k \mtx{\herm{u_1}\\ \vdots \\ \herm{u_k}}$$

(Si se te complica cazar la idea, [acá lo explico más detenidamente](otras-demostraciones-proyeccion.html#demostración-vía-transformaciones-lineales).)

Ahora llamando $$U = \mtx{u_1, \cdots, u_k}$$ llegamos a expresión:

$$[\mathcal{P}{S}]_E = U \herm{U}$$

$$\qed$$

# Demostración vía transformaciones lineales
No es necesario utilizar conceptos de autovectores y autovalores para obtener la expresión, podemos hacer lo mismo utilizando sólo conceptos de transformaciones lineales, analizando la matriz de la transformación en una base particular.

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

$$\qed$$

> Concuerdo que esta demostración es un quilombo tremendo, pero me sirve de ejemplo para mostrar cómo operar con matrices con bloques --es la principal razón por la cual me molesté en escribir esto, porque es bonita... o al menos tiene linda peronalidad (?).
{:.note}


# Demostración Teórica Particular en dimensión 1
Esta es una demostración sencilla para cuando $$S = \gen{w}$$, es decir, cuando $$S$$ es un espacio de dimensión 1. Después podemos externder el razonamiento a un caso más general.

> Vamos a trabajar en el espacio vectorial $$\VV=\CC[n]$$, con el producto interno canónico, definido como $$\inner{x}{y} \eqdef \herm{y} x$$.
{:.note}

Sea $$S = \gen{w}$$, y pidamos ademas que $$ \norm{w}=1 $$.

Sabemos que $$\proy{S}{x}$$ es una transformación lineal. Por lo tanto, como $$\VV = S \bigoplus \ortog{S}$$, alcanza con verificar que $$\proy{S}{S}=S$$ y $$\proy{S}{\ortog{S}} = \{\vec{0}\}$$

Sea $$ s \in S \then  \exists k \in \CC : s = k u$$.

Luego $$w\herm{w} s = w \herm{w} k w = k w (\herm{w}w) = kw \norm{w}^2 = kw = s$$

Por otro lado, sea $$u \in \ortog{S}$$, es decir, $$u \perp w $$.

Entonces $$w\herm{w} u = w (\inner{w}{u}) = w(0) = \vec{0}$$

Por lo tanto, podemos concluir que $$P_S(x) = w\herm{w} x$$, y por ende, $$[P_S]_E = w\herm{w}$$.

$$\qed$$

# Demostración Teórica (caso general)
En esta demostración vamos a limitarnos a ver que $$U\herm{U}$$ es justamente $$[\mathcal{P}_S]_E$$, verificando que hace lo que tiene que hacer, pero tener idea de dónde salió. Vamos a extender el razonamiento anterior utlizando muchas cuentas.

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
  - Consideramos el producto $$\herm{U}u_i$$ como el producto escalar entre cada una de las columnas de $$U$$ con el vector $$u_i$$. Ya que éstas son BON, dicho producto vale 0 para todas las columnas excepto aquella que contiene $$u_i$$, en cuyo caso vale 1 (si no te queda claro, [echale un vistazo a esto]({{ site.baseurl }}{% post_url 2018-02-03-proyeccion%}#deducción-constructiva)).
  - Consideramos el producto de $$U$$ con el vector que tiene un 1 en la posición i-ésima como la combinación lineal de las columnas de $$U$$ con los coeficientes del vector, resultando $$1 u_i$$ por lo anteriormente dicho.

Cumplida esta parte, resta analizar el complemento ortogonal. Sea $$w \in \ortog{S}$$, es decir, $$w \perp u_i, \, i=1,\cdots,k $$.

Entonces $$\herm{U} w = \vec{0}$$ pues $$w$$ es ortogonal a las columnas de $$U$$. Y por lo tanto, $$U\herm{U} w = \vec{0}\, \forall w \in \ortog{S}$$.

Por lo expuesto, podemos concluir que $$P_S(x) = w\herm{w} x$$, y por ende, $$[P_S]_E = w\herm{w}$$.

$$\qed$$

