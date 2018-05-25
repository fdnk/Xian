# Acerca del blog
Blog para poner cosas interesantes sobre la materia [Álgebra II-61.08/81.02](http://materias.fi.uba.ar/6108/) de [FIUBA](http://web.fi.uba.ar).

# Cosas técnicas
Utilicé el template de Xian, el readme original puede encontrarse en ``Xian.md`` y realice algunas modificaciones:

  - Fix para poder trabajar con rutas relativas. Tomado de
      https://ricostacruz.com/til/relative-paths-in-jekyll
  - Agregado MatJax CDN
  - Agregados tags: http://longqian.me/2017/02/09/github-jekyll-tag/
  - Agregado Accordion -- modificado de https://www.w3schools.com/howto/howto_js_accordion.asp

# Accordion
Para evitar que demostraciones o explicaciones tediosas molesten a la lectura, estas se esconden en un accordion con un
título descriptivo, el cual las muestra al hacer click en él.

Para crear un accordion, hacer algo así:
```
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
```

No es lo mejor del mundo, pero funciona.

# Blockquotes de colores
Se definieron las clases `.teorema`, `.success`, `.warning` y `.note`, cada cual con un color característico.

Para utilizar una de estas clases en un bloquote, hacer por ejemplo:

```
> Texto del bloquote
{:.warning}
```

# Labels para las ecuaciones
Se puede poner un label de la forma usual en LaTeX, por ejemplo:
```
$$
\begin{align}
	T(v_1)&=w_1  \nonumber \\
	&\vdots \label{eq:T} \\
	T(v_k)&=w_k \nonumber 
\end{align}
$$
```

Para las ecuaciones que no están dentro de un align, es necesario definir un tag (o ponerlas en un align o equation):
```
[...] tales que $$T(x)=y \tag{I}\label{eq:preimagen_y}$$
```

Para referenciar dichos labels, la forma es: 
```
Ahora, reemplazo x en la ecuación \eqref{eq:preimagen_y}:
```

Más info en: http://mathjax.readthedocs.io/en/latest/tex.html#automatic-equation-numbering
(La configuración de mathjax está en `_includes/scripts.html`).
