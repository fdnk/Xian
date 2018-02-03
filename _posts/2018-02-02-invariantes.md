---
title: Subespacios Invariantes
date: 2018-02-02 11:42:00 -0300
layout: post
tag: intermedio
---

Se dice que un subespacio $$\ss{S}$$ es invariante por A, o A-invariante, sii $$\forall x \in \ss{S},\, Ax \in \ss{S} $$.

Hay una relación directa entre los espacios invariantes por A y los autovectores de A. Vamos a analizarlo.

# Propiedades

## Todo autoespacio es un subespacio invariante
La demostración es trivial. Analicemos el caso más sencillo donde $$\ss{S} = \gen{v}$$, con $$ v \in \KK[n] / A v = \lambda v,\, \lambda \in \KK$$.
Sea $$x \in \ss{S}$$, luego $$x = k v, \, k\in \KK$$. Luego $$Ax = A(k v) = k (Av) = (k \lambda) v$$.

El caso más general, donde $$\ss{S} = \gen{v_1, \cdots, v_k}$$ se demuestra exactamente de la misma forma.

{% capture proof_1 %}

Sea $$A \in \KK[n \times n]$$ y sea $$\ss{S} \subseteq \KK[n]$$ un espacio A-invariante de dimensión $$k$$.

Tomemos $$x \in \ss{S}$$. Por ende $$x = \sum_{j=1}^{k} \alpha_j v_j, \, k_j\in \KK$$.

<br/>

Luego $$Ax = A\sum_{j=1}^{k} \alpha_j v_j = \sum_{j=1}^{k} \alpha_j A v_j = \sum_{j=1}^{k} (\alpha_j \lambda_j)  v_j$$.

$$\qed$$
{% endcapture %}

{% include collapsable.html  content=proof_1 %}

## Todo subespacio invariante de dimensión 1 es un autoespacio
Pensemos un poco. Si tengo un subespacio invariante de dimensión 1 esto es, una recta que pasa por el origen tal que al multiplicar cualquier punto por A, cae en la misma recta. Por ende, cumple la definición de autovector.

## Hay subespacios invariantes que son autoespacios, y otros que no

Pensemos en un autoespacio de dimensión 2 (que obviamente está asociado a un autovalor de multiplicidad geométrica 2). Vimos anteriormente que es un espacio invariante, por lo cual, tenemos un ejemplo de un espacio invariante que es autoespacio.

Ahora, consideremos el subespacio $$\ss{W} = \ss{S}_{\lambda_1} + \ss{S}_{\lambda_2}$$. Es facil verificar que es un espacio invariante, ya que podemos escribir cualquier $$x \in \ss{W}$$ de la forma $$x= w_1 + w_2$$ con $$w_1 \in \ss{S}_{\lambda_1}$$ y $$w_2 = \ss{S}_{\lambda_2}$$. Entonces $$Ax = A w_1 + A w_2 = \lambda_1 w_1 + \lambda_2 w_2$$ y por lo tanto, $$Ax \in \ss{W}$$.



## Toda suma de autoespacios, es un subespacio invariante
Hacer la demostración





