---
title: Teléfonos y DVS (una DVS como banco de filtros)
date: 2018-02-08 01:42:00 -0300
layout: post
tags: avanzado borrador
---

Una de las formas que más me gusta ver una DVS es, como lo llamamos en Telecomunicaciones, un "banco de filtros". No voy a ahondar más en qué cosa es esa, solo tomo el nombre para el enfoque que voy a explicar.

## Analizando como un Banco de Filtros
Básicamente, la idea consiste en analizar $$Ax=U \Sigma \trans{V} x$$ como un producto interno, al asociar como $$Ax = U \Sigma (\trans{V} x)$$. ¿Dónde está el PI si V es una matriz? Bueno, se puede pensar que $$\trans{V} x$$ es un vector columna, donde en cada componente, está el producto interno entre cada fila de $$\trans{V}$$ con $$x$$. Es decir:

$$
\begin{align*}
\trans{V} x &= \mtx{ \trans{v_1} \\ \trans{v_2} \\ \vdots \\ \trans{v_n} } x\\
            &= \mtx{ \inner{v_1}{x} \\ \inner{v_2}{x} \\ \vdots \\ \inner{v_m}{x} }
\end{align*}
$$

Recordemos que los vectores $$v_i$$ que componen $$V$$ son un conjunto ortonormal. De esta forma, logramos "descomponer" $$x$$ en la componente correspondiente en cada dirección $$v_i$$.

```Poner dibujo de banco de filtros```

Una vez descompuesta $$x$$ de esta forma, procedemos a escalar cada componente por separado, según los elementos $\sigma_i$$ $de la diagonal de $$\Sigma$$. Vemos acá claramente, que si la matríz A posee un subespacio nulo no trivial, las últimas $$k$$ componentes corresponden a la proyección sobre el nulo, y son escaladas por 0 al multiplicarse por $$\Sigma$$, y por ende, esas componentes se pierden para siempre.

Asimismo, la matriz $$\Sigma$$ puede agregar más componentes nulas al vector si las dimensiones corresponden.

Una vez que tenemos el nuevo vector $$y = \Sigma \trans{V} x$$, con cada una de las componentes, se arma la combinación lineal de las columnas de U.
Tal vez fui demasiado rápido y no lo dejé ver.
Todos los vectores que impacten en la dirección $$v_i$$, se van a proyectar sobre $$v_1$$, luego se van a escalar por $$\sigma_1$$, y por último, se va a utilizar para escalar el vector $$u_1$$.

Notemos que si $$\Sigma$$ posee ceros en la diagonal, hay vectores de $$U$$ que nunca serán alcanzanzados por ningún $$x$$ que impacte. Por ello, los primeros $$r$$ vectoresde $$U$$ serán los que generen la imágen, donde $$r$$ es la cantidad de elementos no nulos en la diagonal de $$\Sigma$$.

Por otro lado, todo lo que impacte en los últimos elementos de $$\trans{V}$$, van a ser multiplicados por 0 cuando pasen por $$\Sigma$$. Por esta razón, los últimos $$n-r$$ vectores de $$\trans{V}$$ generan el nulo de A.

## ¿De donde viene el nombre?
El concepto de un banco de filtros creo que se originó en el campo de las telecomunicaciones. La idea es que una persona quiere llamar por teléfono. Al presionar un botón del telefono, se transmite un tono por la línea telefónica; cada tecla genera un tono de una frecuencia distinta. Del otro lado, en la central telefónica, deben analizar si el tono que reciben corresponde a un 1, un 7, un 0 ¡o a dos o más teclas juntas!

¿Cómo se resuelve tal dilema? Bueno, ayudándonos del álgebra lineal.

Por cuestiones tecnológicas, en los '70 era muy sencillo generar un tono senoidal, y sabemos que dos senos de frecuencias diferentes son linealmente independientes.

Generalmente, la señal que llega a la central telefónica no es exactamente la que se transmite, sino que capta interferencias y ruidos en el proceso. Por ejemplo, puede pasar algo así:

```poner dibujo de un seno y de un seno distorisionado```

La tarea de la central, entre otras, consiste en reconocer qué tono se emitió al recibir la señal B. Para ello, lo que hace es proyectarla sobre el conjunto de todas las señales correspondientes a cada dígito. Con un buen criterio, se puede decir que aquella componente a la que "más se parezca" es aquella que verdaderamente se quiso transmitir. Para ello, se realiza un producto interno entre un pedazo de la señal recibida con cada una de las muestras.

``` poner grafico de la proyección sobre cada todo del tono distorisionado```





## Comentario
Me gusta la idea de pensar que al hacer $$Ax$$, los vectores $$x$$ viajan a través de $$A$$, de derecha a izquierda, mientras van siendo transformados.
Sí, claro que puede verse como una rotación, un escalamiento, y otra rotación, pero considero que este enfoque alternativo es complementario a los vistos en la materia, y arroja un poquito más de luz a veces ;)



