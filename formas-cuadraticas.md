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

::::: {#exr-semejanza_ortogonal .medio}

Dada la matriz:

$$A=
\begin{pmatrix}
2 & 0 & 0 & -1\\
0 & 2 & -1 & 0 \\
0 & -1 & 2 & 0 \\
-1 & 0 & 0 & 2
\end{pmatrix}
$$

Razonar que es diagonalizable y determinar su forma diagonal y una matriz de paso, $P$, verificando que $P^{-1}=P^t$. ¿Cuál es la signatura de $A$?

:::: {.callout collapse="true" title="Solución"}

La matriz $A$ es simétrica y el Teorema espectral afirma que toda matriz simétrica y real es diagonalizable, por tanto $A$ lo es.
Nos piden una diagonalización por semejanza ortogonal, aí que tenemos que calcular en primer lugar los valores propios: 

$$
\begin{align*}
|A-\lambda I| & =\left|
\begin{array}{rrrr}
2-\lambda & 0 & 0 & -1\\
0 & 2-\lambda & -1 & 0 \\
0 & -1 & 2-\lambda & 0 \\
-1 & 0 & 0 & 2-\lambda
\end{array}\right|=(F_4+F_1\rightarrow F_4)=
\left|
\begin{array}{rrrr}
2-\lambda & 0 & 0 & -1\\
0 & 2-\lambda & -1 & 0 \\
0 & -1 & 2-\lambda & 0 \\
1-\lambda & 0 & 0 & 1-\lambda
\end{array}\right|\\
& =(C_1-C_4 \rightarrow C_1)= 
\left|\begin{array}{rrrr}
3-\lambda & 0 & 0 & -1\\
0 & 2-\lambda & -1 & 0 \\
0 & -1 & 2-\lambda & 0 \\
0 & 0 & 0 & 1-\lambda
\end{array}\right|=(3-\lambda)(1-\lambda)[(2-\lambda)^2-1]=(3-\lambda)^2(1-\lambda)^2.
\end{align*}
$$

Tenemos entonces los valores propios $\lambda=1$ y $\lambda=3$ ambos con multiplicidad algebraica dos. Tenemos entonces que la matriz diagonal semejante y congruente con $A$ es 

$$
D=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1& 0 & 0\\
0 & 0 & 3 & 0\\
0 & 0 & 0 & 3
\end{pmatrix},
$$

y por tanto la signatura de $A$ es $(4,0)$, por tanto definida positiva.

Calculamos ahora los subespacios propios y elegimos una base ortonormal de cada uno.


**$V_{\lambda=1}$**

$$
(A-1\cdot I)=\begin{pmatrix}
1 & 0 & 0 & -1\\
0 & 1 & -1 & 0 \\
0 & -1 & 1 & 0 \\
-1 & 0 & 0 & 1
\end{pmatrix},
$$  

nos da como cartesianas $\left\{\begin{array}{l}
x-t=0\\
y-z=0
\end{array}\right.$  y una base ortogonal es $\{(1,0,0,1),(0,1,1,0)\}$.


**$V_{\lambda=3}$**

$$
(A-1\cdot I)=\begin{pmatrix}
-1 & 0 & 0 & -1\\
0 & -1 & -1 & 0 \\
0 & -1 & -1 & 0 \\
-1 & 0 & 0 & -1
\end{pmatrix},
$$  

nos da como cartesianas $\left\{\begin{array}{l}
x+t=0\\
y+z=0
\end{array}\right.$  y una base ortogonal es $\{(1,0,0,-1),(0,1,-1,0)\}$.

Dividiendo cada vector por su norma obtenemos una base ortonormal de vectores propios, lo que nos da la matriz ortogonal $P$:

$$
P=\begin{pmatrix}
1/\sqrt{2} & 0 & 0 & 1/\sqrt{2}\\
0 & 1/\sqrt{2} & 1/\sqrt{2} & 0\\
0 & 1/\sqrt{2} & -1/\sqrt{2} & 0\\
1/\sqrt{2} & 0 & 0 & -1/\sqrt{2}\\
\end{pmatrix}.
$$

::::
:::::

::::: {#exr-3 .basico}

Calcula la signatura de la forma cuadrática definida por la matriz

$$
C=\left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 0 & -1\\
0 & -1 & -5
\end{array}\right)
$$

:::: {.callout collapse="true" title="Solución"}

Diagonalizamos por congruencia (realizando las mismas operaciones por filas que por columnas), por lo que necesitamos un pivote en la segunda fila

$$
C=\left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 0 & -1\\
0 & -1 & -5
\end{array}\right)\sim_f (F_2\leftrightarrow F_3) \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & -1 & -5\\
0 & 0 & -1
\end{array}\right)\sim_c (C_2\leftrightarrow C_3) \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & -5 & -1\\
0 & -1 & 0
\end{array}\right)
$$

y ahora usamos el $-5 $ para hacer cero en la posición 32:

$$
\sim_f \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & -5 & -1\\
0 & 0 & 1/5
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & -5 & 0\\
0 & 0 & 1/5
\end{array}\right)
$$

por tanto la signatura es $\boxed{(2,1)}$.

::::
:::::

::::: {#exr-4 .medio}

Clasifica, según los valores reales de $a$, la forma cuadrática definida por la matriz

$$
C=\left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & a\\
0 & a & -4
\end{array}\right)
$$

:::: {.callout collapse="true" title="Solución"}

Diagonalizamos por congruencia (con la única regla de usar las mismas operaciones elementales por filas que por columnas)

$$
C=\left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & a\\
0 & a & -4
\end{array}\right)\sim_f \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & a\\
0 & 0 & -4-a^2
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0a\\
0 & 0 & -4-a^2
\end{array}\right)
$$

Puesto que $-4-a^2$ es negativo para cualquier valor real de $a$, la signatura de la matriz es $(2,1)$ y por tanto es <b> no definida </b>.

::::
:::::

::::: {#exr-5 .medio}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
1 & 1 & 1 & 1\\
1 & 1 & -1 & -1\\
1 & -1 & 1 & -1\\
1 & -1 & -1 & 1
\end{array}\right)
$$

Calcula la signatura de la forma cuadrática definida por $A$.

:::: {.callout collapse="true" title="Solución"}

Diagonalizamos por congruencia:

$$
A= \left(\begin{array}{rrrr}
1 & 1 & 1 & 1\\
1 & 1 & -1 & -1\\
1 & -1 & 1 & -1\\
1 & -1 & -1 & 1
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & 1 & 1 & 1\\
0 & 0 & -2 & -2\\
0 & -2 & 0 & -2\\
0 & -2 & -2 & 0
\end{array}\right)\sim_c  \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 0 & -2 & -2\\
0 & -2 & 0 & -2\\
0 & -2 & -2 & 0
\end{array}\right)
$$

$$
\sim_f  \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & -2 & -2 & -4\\
0 & -2 & 0 & -2\\
0 & -2 & -2 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & -4 & -2 & -4\\
0 & -2 & 0 & -2\\
0 & -4 & -2 & 0
\end{array}\right)
$$

$$
\sim_f \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & -4 & -2 & -4\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 4
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & -4 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 4
\end{array}\right)
$$

y se obtiene que los signos de los elementos de la matriz diagonal son 3 positivos y 1 negativo. Entonces $sig(A)=(3,1)$.

::::
:::::

::::: {#exr-6 .basico}

Calcula la signatura de la forma cuadr{\'a}tica $\Phi: \mathbb{R}^3 \longrightarrow \mathbb{R}$ definida por:

$$
\Phi (x,y,z)= 5 x^2 + 3 y^2 + 2 z^2 - 2xy -4 xz
$$

:::: {.callout collapse="true" title="Solución"}

Escribimos la matriz simétrica asociada y la diagonalizamos por congruencia

$$
\begin{pmatrix}
5 & -1 & -2 \\
-1 & 3 & 0\\
-2 & 0 & 2\\
\end{pmatrix}\sim_f \begin{pmatrix}
-2 & 0 & 2\\
-1 & 3 & 0\\
5 & -1 & -2 \\
\end{pmatrix}\sim_c \begin{pmatrix}
2 & 0 & -2\\
0 & 3 & -1 \\
-2 & -1 & 5\\
\end{pmatrix}\sim_f \begin{pmatrix}
2 & 0 & -2\\
0 & 3 & -1 \\
0 & -1 & 3\\
\end{pmatrix}
$$

$$
\sim_c \begin{pmatrix}
2 & 0 & 0\\
0 & 3 & -1 \\
0 & -1 & 3\\
\end{pmatrix}\sim_f \begin{pmatrix}
2 & 0 & 0\\
0 & 3 & -1 \\
0 & 0 & 3-1/3\\
\end{pmatrix}\sim_c \begin{pmatrix}
2 & 0 & 0\\
0 & 3 & 0 \\
0 & 0 & 8/3\\
\end{pmatrix}
$$

luego $sig(A)=(3,0)$.

::::
:::::