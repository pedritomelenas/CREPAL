---
title: Formas cuadráticas y diagonalización por congruencia
lang: es
format:
   html:
    toc: false
    html-math-method: mathjax
    css: styles.css
    page-layout: full
    include-in-header: includes-header.html
---

<!-- LTeX: language=es-ES --->

<!--Se muestran ejercicios sobre cuerpos finitos y sobre los racionales y reales. Puedes cambiar esta opción marcando o desmarcando la siguiente casilla.<br>-->

::::: {#exr-1 .medio}

Determina, en función de  $b$, la signatura de la forma cuadrática $\phi:\mathbb{R}^{2} \to \mathbb{R}$ dada por 

$$
\phi(x,y)= bxy.
$$


:::: {.callout collapse="true" title="Solución"}

La matriz asociada a la forma cuadrática es 

$$
\begin{pmatrix}
0 & b/2\\
b/2 & 0
\end{pmatrix}
$$

que podemos diagonalizar por congruencia

$$
\begin{pmatrix}
0 & b/2\\
b/2 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
b/2 & b/2\\
b/2 & 0
\end{pmatrix}\sim_c\begin{pmatrix}
b & b/2\\
b/2 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
b & b/2\\
0 & -b/4
\end{pmatrix}\sim_c\begin{pmatrix}
b & 0\\
0 & -b/4
\end{pmatrix}.
$$

Si $b=0$ la signatura es $(0,0)$; si $b\not = 0$ la signatura es $(1,1)$.

También pueden calcularse los valores propios que son 

$$
\lambda= \pm (b/4)
$$ 
y queda el mismo resultado, por supuesto.

::::
:::::

::::: {#exr-2 .medio}

Determina para qué valores de $a$ la fórmula

$$
f(x,y,z)=x^2+2axy+2xz+2ay^2+(a+1)z^2,
$$

define una forma cuadrática definida positiva.

:::: {.callout collapse="true" title="Solución"}

Calculamos la matriz simétrica asociada a esta forma cuadrática y la diagonalizamos por congruencia para obtener su signatura:

$$\left(\begin{array}{ccc}
1 & a & 1\\
a & 2a & 0\\
1 & 0 & a+1
\end{array}\right)\sim_f \left(\begin{array}{ccc}
1 & a & 1\\
0 & 2a-a^2 & -a\\
0 & -a & a
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & 2a-a^2 & -a\\
0 & -a & a
\end{array}\right)
$$

Ahora intercambiamos las filas segunda y tercera y también las columnas segunda y tercera:

$$
\left(\begin{array}{ccc}
1 & 0 & 0\\
0 & 2a-a^2 & -a\\
0 & -a & a
\end{array}\right)
\sim_f \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & -a  & a\\
0 & 2a-a^2 & -a
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & a  & -a\\
0 & -a & 2a-a^2
\end{array}\right)\sim_f \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & a  & -a\\
0 & 0 & a-a^2
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & a  & 0\\
0 & 0 & a-a^2
\end{array}\right).
$$

Luego será definida positiva cuando los tres elementos de la diagonal lo sean, es decir $a>0$ y $a(1-a)>0$ luego debe ser $0<a<1$.

::::
:::::