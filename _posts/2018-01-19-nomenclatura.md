---
title: Nomenclatura
date: 2018-01-19 05:30:00 -0300
layout: post
tags: inicial
---

En estos artículos utilizo la misma notación que en la materia Álgebra II, a excepción tal vez del producto interno, que me gusta usar los piquitos. 

## Números
  - $$\NN$$ conjunto de los [números naturales](https://es.wikipedia.org/wiki/N%C3%BAmero_natural): $$\{1, 2, 3, \ldots \}$$
  - $$\ZZ$$ conjunto de los [números enteros](https://es.wikipedia.org/wiki/N%C3%BAmero_entero): $$\{\ldots, -2, -1 0, 1, 2, 3, \ldots \}$$
  - $$\QQ$$ conjunto de los [números racionales](https://es.wikipedia.org/wiki/N%C3%BAmero_racional): $$x \in \QQ \iff x=a/b, \, a,b \in \ZZ$$
  - $$\RR$$ conjunto de los [números reales](https://es.wikipedia.org/wiki/N%C3%BAmero_real).
  - $$\CC$$ conjunto de los [números complejos](https://es.wikipedia.org/wiki/N%C3%BAmero_complejo).

## Funciones
  - $$\PP[n]$$ conjunto de los polinomios de grado a lo sumo $$n$$ (incluyendo al polinomio nulo) (generalmente a coef. reales). 
  - $$\Cf[n]$$ conjunto de las funciones cuya derivada n--ésima existe y es contínua.


## Genéricos
  - $$\KK$$ un [cuerpo](https://es.wikipedia.org/wiki/Cuerpo_(matem%C3%A1ticas)), aquí es siempre $$\KK=\RR$$ ó $$\CC$$. 
  - $$\VV$$ y $$\WW$$ denotan por lo general un [espacio vectorial](https://es.wikipedia.org/wiki/Espacio_vectorial)

## Operaciones, operadores y transformaciones
  - $$\conj{x}$$ denota el complejo--conjugado del número, vector o matriz $$x$$. Es decir, $$\conj{x}=\Re{x}-i\,\Im{x}$$.
  - $$\trans{A}$$ denota la transpuesta de la matriz $$A$$. Es decir, si $$A=[a_{ij}],\, \trans{A} = [a_{ji}]$$
  - $$\herm{A}$$ denota la transpuesta hermítica de la matriz $$A$$. Es decir, si $$A=[a_{ij}],\, \herm{A} = [\conj{a}_{ji}] = \trans{\conj{A}}$$
  - $$\proy{S}{x}$$ es la [proyección ortogonal](https://en.wikipedia.org/wiki/Projection_(linear_algebra)) de $$x$$ sobre el subespacio $$S$$.
  - $$\inner{\cdot}{\cdot}$$ denota un [producto interno](https://es.wikipedia.org/wiki/Producto_escalar).
  - $$\norm{x}$$ denota la norma del vector x. Salvo aclaración explícita, se considera inducida por el PI utilizado. Es decir: $$\norm{x} = \sqrt{\inner{x}{x}}$$.
  - $$\norm{x}_p, \, p \in \RR$$ denota la norma p del vector x, es decir: $$\norm{x}_p = \sqrt[p]{\abs{x_1}^p + \cdots + \abs{x_n}^p}$$.
  - $$\norm{x}_{\inf}$$ denota la norma infinito de x, esto es, el módulo de mayor de sus componentes en módulo: $$\norm{x}_{\inf} = \argmax{i} \abs{x_i}$$.
  - $$\penrose{A}$$ es la [pseudoinversa de Moore--Penrose](https://en.wikipedia.org/wiki/Moore%E2%80%93Penrose_inverse) de $$A$$. 

## Espacios Vectoriales
  - $$\gen{B}$$ es el [subespacio generado](https://en.wikipedia.org/wiki/Generator_(mathematics)) por los vectores del conjunto $$B$$.
  - $$\dim{S}$$ es la [dimensión](https://es.wikipedia.org/wiki/Dimensi%C3%B3n_de_un_espacio_vectorial) del subespacio $$S$$, cuando sea finita.
  - $$\ortog{S}$$ denota el [complemento ortogonal](https://en.wikipedia.org/wiki/Orthogonal_complement) del subespacio $$S$$.
  
## Espacios Fundamentales
  - $$\col{A}$$ es el espacio columna de $$A$$. Es decir, el subespacio generado por las columnas de $$A$$.
  - $$\fil{A}$$ es el espacio fila de $$A$$. Es decir, el subespacio generado por las filas de $$A$$ (siempre como vectores columna). Es decir: $$\fil{A} \eqdef \col{\trans{A}}$$
  - $$\nul{A}$$ es el espacio nulo de $$A \in \RR[n \times m]$$. Es decir, $$\nul{A}=\left\{x\in \RR[m] : Ax = 0_\RR[n] \right\}$$.
  
## Transformaciones Lineales
  - $$\nu{T}$$ es el núcleo de la tranformación lineal $$T:\VV \rightarrow \WW$$. Es decir: $$\{ x \in \VV : T(x)=0_\WW \}$$
  - $$\im{T}$$ es la imagen de la tranformación lineal $$T:\VV \rightarrow \WW$$. Es decir: $$\{ w \in \WW /\, \exists v \in \VV : T(v)=w \}$$