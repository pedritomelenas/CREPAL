---
title: Espacios vectoriales
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

<input type="checkbox" id="casilla_cf" value="cfon" checked onclick="CF();"> Mostrar ejercicios sobre cuerpos finitos. 

::::: {#exr-1 .avanzado}

En $\mathbb{R}^4$ se considera el conjunto 

$$
\{(b,0,a,b),(0,a,1+a,0),(0,1,1+a,0),(0,1+a,2+2a,1-a)\}.
$$

¿Cuál es el número máximo de vectores linealmente independientes que puede contener dicho conjunto, según los valores de a y b?

:::: {.callout collapse="true" title="Solución"}

Para determinar si los vectores son linealmente independientes o linealmente dependientes construimos la matriz cuyas columnas son esos vectores, a continuación calculamos su rango y lo comparamos con el número de vectores. Se tiene que los vectores son linealmente independientes si y sólo si $\operatorname{rg}(A)$ coincide con el número de vectores (o de columnas) y en otro caso son linealmente dependientes.


La matriz que se forma es:

$$
A=\left( \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & a & 1 & 1+a\\
a & 1+a& 1+a & 2+2a\\
b & 0 & 0 & 1-a
\end{array}\right).
$$

Puesto que es cuadrada de orden cuatro, entonces tendrá rango cuatro exactamente cuando el determinante sea distinto de cero. Lo calculamos:

$$
|A|=\left| \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & a & 1 & 1+a\\
a & 1+a& 1+a & 2+2a\\
b & 0 & 0 & 1-a
\end{array}\right|= \left| \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & a-1 & 1 & 1+a\\
a & 0 & 1+a & 2+2a\\
b & 0 & 0 & 1-a
\end{array}\right|= b(a-1)(1+a)(1-a).
$$

Luego si $b\not = 0$ y $a\not\in\{-1,1\}$, el rango es cuatro y los vectores son linealmente independientes.

Para estudiar todos los casos podemos representarlos en una tabla de doble entrada e iremos calculando cada uno de ellos.
El primero que completamos es el caso que acabamos de obtener, si $b\not = 0, a\not = \pm 1$ el rango es cuatro. En los demás uno o los dos parámetros toman valores concretos, por lo que es más fácil su estudio. La solución es:

<table border="1">
  <tr>
    <td></td>
    <td>$a=1$</td>
    <td>$a=-1$</td>
    <td>$a\not = \pm 1$</td>
  </tr>
  <tr>
    <td>$b=0$</td>
    <td>rango 2</td>
    <td>rango 3</td>
    <td>rango 3</td>
  </tr>
  <tr>
    <td>$b\not =0$</td>
    <td>rango 2</td>
    <td>rango 3</td>
    <td>rango 4</td>
  </tr>
</table>

Veamos el caso $b\not = 0,\, a=1$:

$$
A=\left( \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & 1 & 1 & 2\\
1 & 2 & 2 & 4\\
b & 0 & 0 & 0
\end{array}\right)\sim_c \left( \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
1 & 2 & 0 & 0\\
b & 0 & 0 & 0
\end{array}\right)
$$

y es inmediato que el rango es dos. 

Para el caso $b\not = 0,\, a=-1$:

$$
A=\left( \begin{array}{cccc}
b & 0 & 0 & 0\\
0 & -1 & 1 & 0\\
-1 & 0 & 0 & 0\\
b & 0 & 0 & 2
\end{array}\right)\sim_f \left( \begin{array}{cccc}
1 & 0 & 0 & -2\\
0 & -1 & 1 & 0\\
-1 & 0 & 0 & 0\\
b & 0 & 0 & 2
\end{array}\right)\sim_f \left( \begin{array}{cccc}
1 & 0 & 0 & -2\\
0 & -1 & 1 & 0\\
0 & 0 & 0 & -2\\
0 & 0 & 0 & 2+2b
\end{array}\right)\sim_f \left( \begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & -1 & 1 & 0\\
0 & 0 & 0 & -2\\
0 & 0 & 0 & 0
\end{array}\right)
$$

y por tanto el rango es 3. 

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
var('b')
A=matrix([[b,0,0,0],[0,-1,1,0],[-1,0,0,0],[b,0,0,2]])
A.echelon_form()
</script>
:::

Para el caso $b=0,\, a\not =-1,1$ distinguimos dos posibilidades:
<ul>$a=0$:

$$
A=\left( \begin{array}{cccc}
0 & 0 & 0 & 0\\
0 & 0 & 1 & 1\\
0 & 1 & 1 & 2\\
0 & 0 & 0 & 1
\end{array}\right)\sim_f \left( \begin{array}{cccc}
0 & 1 & 1 & 2\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left( \begin{array}{cccc}
0 & 1 & 0 & 1\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left( \begin{array}{cccc}
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)
$$
que tiene rango 3. 
</ul>

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[0,0,0,0],[0,0,1,1],[0,1,1,2],[0,0,0,1]])
A.echelon_form()
</script>
:::

<ul>$a\not =0$:

$$
A=\left( \begin{array}{cccc}
0 & 0 & 0 & 0\\
0 & a & 1 & 1+a\\
a & 1+a & 1+a & 2+2a\\
0 & 0 & 0 & 1-a
\end{array}\right)\sim_f \left( \begin{array}{cccc}
a & 1+a & 1+a & 2+2a\\
0 & a & 1 & 1+a\\
0 & 0 & 0 & 1-a\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left( \begin{array}{cccc}
1 & \frac{1+a}{a} & \frac{1+a}{a} & \frac{2+2a}{a}\\
0 & 1 & \frac{1}{a} & \frac{1+a}{a}\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left( \begin{array}{cccc}
1 & 0 & \frac{1+a}{a}-\frac{1+a}{a^2} & 0\\
0 & 1 & \frac{1}{a} & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)
$$

que de nuevo tiene rango 3. 
</ul>

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
var('a')
A=matrix([[0,0,0,0],[0,a,1,1+a],[a,1+a,1+a,2+2*a],[0,0,0,1-a]])
A.echelon_form()
</script>
:::

Para los casos restantes, podemos utilizar directamente <code>sage</code> para calcular el rango:

<ul> $a=1, \; b=0$ </ul>

::: {.sage}
<script type="text/x-sage">
A=matrix([[0,0,0,0],[0,1,1,2],[1,2, 2,4],[0,0,0,0]])
show(html(f"${latex(A.T)}$ tiene rango ${A.rank()}$"))
</script>
:::

<ul> $a=-1, \; b=0$ </ul>

::: {.sage}
<script type="text/x-sage">
A=matrix([[0,0,0,0],[0,-1,1,0],[-1,0,0,0],[0,0,0,2]])
show(html(f"${latex(A.T)}$ tiene rango ${A.rank()}$"))
</script>
:::
::::
:::::

::::: {#exr-2 .medio}

En el conjunto de polinomios de $\mathbb{R}[x]$ con grado menor o igual que dos, estudia si el siguiente conjunto de vectores es
linealmente independiente o linealmente dependiente (se recomienda usar coordenadas en las bases más adecuadas).



$$
\{ 1+2x+3x^{2},\; 1-x+x^{2},\; 1+x-x^{2},\; x+2x^{2} \}.
$$


:::: {.callout collapse="true" title="Solución"}

Utilizaremos la base más sencilla que conozcamos del espacio vectorial para obtener coordenadas de los vectores y aplicar el criterio conocido.

Podemos utilizar la base $B=\{1,x,x^2\}$ en la que resulta muy sencillo escribir las coordenadas de los vectores:

$$
\begin{array}{rl}
1+2x+3x^{2}&=(1,2,3)_B,\\
1-x+x^{2}&=(1,-1,1)_B,\\
1+x-x^{2}&=(1,1,-1)_B,\\
x+2x^{2}&=(0,1,2)_B.
\end{array}
$$

Ahora escribimos las coordenadas por columnas en una matriz y calculamos el rango:

$$
\left(\begin{array}{rrrr}
1 & 1 & 1 & 0\\
2 & -1 & 1 & 1\\
3 & 1 & -1 & 2
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
2 & -3 & -1 & 1\\
3 & -2 & -4 & 2
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
2 & 1 & 0 & -3\\
3 & 2 & -2 & -2
\end{array}\right),
$$

que tiene rango tres (las tres primeras columnas forman una submatriz con determinante distinto de cero). Los cuatro vectores son linealmente dependientes.

Realmente no era necesario el cálculo del rango, puesto que no podía ser en ningún caso mayor que tres. Podíamos haber utilizado que como la dimensión del espacio es tres, el máximo número de vectores linealmente independientes en este espacio vectorial es también tres.

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,2,3],[1,-1,1],[1,1,-1],[0,1,2]])
show(html(f"${latex(A.T)}$ tiene rango ${A.rank()}$"))
</script>
:::
::::
:::::

::::: {#exr-3 .cuerpo_finito-medio}

Estudia si los siguientes conjuntos de vectores son
linealmente independientes o linealmente dependientes (se recomienda usar coordenadas en las bases más adecuadas).

<ol type="a">

<li>En el conjunto de polinomios de $\mathbb{Z}_3[x]$ con grado menor o igual que tres:

$$
\{2x, x^3-3, 1+x -4x^3, x^3 + 18x -9\}.
$$ 

</li>

<li>En $\mathcal{M}_{2}(\mathbb{Z}_7)$: 

$$
\left\{ \begin{pmatrix} 1 & -1 \\ 0 & 6
\end{pmatrix}, \begin{pmatrix} -1 & 0 \\ 3 & 1 \end{pmatrix},
\begin{pmatrix} 1 & 1 \\ -1 & 2 \end{pmatrix}, \begin{pmatrix}
0 & 1 \\ 1 & 0 \end{pmatrix}\right\}.
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

En cada caso utilizaremos la base más sencilla que conozcamos del espacio vectorial para obtener coordenadas de los vectores y aplicar el criterio conocido.

<ol type="a">

<li>En este caso, utilizamos la base $B=\{1,x,x^2,x^3\}$ y de nuevo escribimos los vectores por sus coordenadas:

$$
\begin{array}{rl}
2x&=(0,2,0,0)_B,\\
x^3-3&=(0,0,0,1)_B,\\
 1+x-4x^{3}&=(1,1,0,2)_B,\\
 x^{3}+18x-9&=(0,0,0,1)_B.
\end{array}
$$

Hemos tenido en cuenta que los coeficientes están en $\mathbb{Z}_3$ y por tanto $-3=0,-4=2,18=0,9=0$. En este caso observamos que se repite el mismo vector $(0,0,0,1)_B$, si lo consideramos dos veces el conjunto sería linealmente dependientes, pero como es un conjunto observamos que en realidad lo forman de tres vectores.
Escribimos la matriz

$$
\left(\begin{array}{rrr}
0 & 0 & 1 \\
2 & 0 & 1 \\
0 & 0 & 0 \\
0 & 1 & 2
\end{array}\right)\sim_c \left(\begin{array}{rrr}
0 & 0 & 1 \\
1 & 0 & 0 \\
0 & 0 & 0 \\
0 & 1 & 0
\end{array}\right)
$$

que tiene rango tres y los tres vectores son linealmente independientes.</li>

<li>En $\mathcal{M}_{2}(\mathbb{Z}_7)$ una base sencilla es

$$
\left\{ \begin{pmatrix}
1 & 0 \\ 0 & 0 \\
\end{pmatrix}, \begin{pmatrix}
0 & 1 \\ 0 & 0 \\
\end{pmatrix}, \begin{pmatrix}
0 & 0 \\ 1 & 0 \\
\end{pmatrix},\begin{pmatrix}
0 & 0 \\ 0 & 1 \\
\end{pmatrix}\right\}.
$$

Escribimos cada una de las matrices por sus coordenadas en esta base:

$$
\begin{pmatrix} 1 & -1 \\ 0 & 6
\end{pmatrix}=(1,-1,0,6)_B,
$$

$$
\begin{pmatrix} -1 & 0 \\ 3 & 1 \end{pmatrix}=(-1,0,3,1)_B,
$$

$$
\begin{pmatrix} 1 & 1 \\ -1 & 2 \end{pmatrix}=(1,1,-1,2)_B,
$$

$$
\begin{pmatrix}
0 & 1 \\ 1 & 0 \end{pmatrix}=(0,1,1,0)_B.
$$

Calculamos el rango de la matriz que forman (los coeficientes están en $\mathbb{Z}_7$):

$$
\left(\begin{array}{rrrr}
1 & -1 & 1 & 0\\
-1 & 0 & 1 & 1\\
0 & 3 & -1 & 1 \\
6 & 1 & 2 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
-1 & -1 & 2 & 1\\
0 & 3 & -1 & 1 \\
6 & 0 & 2 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
1 & 1 & 4 & 4 \\
6 & 0 & 2 & 0
\end{array}\right)
$$

que tiene determinante distinto de cero y por tanto rango cuatro, así que los vectores son linealmente independientes.

Comprobemos el resultado obtenido con <code>sage</code>.</li>

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,-1,0,6],[-1,0,3,1],[1,1,-1,2],[0,1,1,0]])
show(html(f"${latex(A.T)}$ tiene rango ${A.rank()}$"))
</script>
:::

</ol>
::::
:::::

::::: {#exr-4 .medio}

Calcula las matrices de cambio de base para las bases de $\mathbb{R}^{3}$:

$$
B=\{(4,0,7);\ (2,1,1);\ (3,1,3)\},\quad B'=\{(1,0,2);\ (4,1,5);\ (1,0,3)\}.
$$

:::: {.callout collapse="true" title="Solución"}

Este ejercicio puede realizarse por varios métodos. Explicaremos dos de ellos.

**Método 1**

Para calcular la matriz de cambio de base de $B$ a $B'$ necesitamos como datos los vectores que forman $B$ escritos por sus coordenadas en $B'$. Nos planteamos entonces calcular $\alpha, \beta, \gamma$ tales que:
$$(4,0,7)=\alpha (1,0,2)+\beta (4,1,5)+\gamma (1,0,3)$$
y por tanto tenemos que resolver el sistema con matriz ampliada:

$$
\left( \begin{array}{rrr|r}
1 & 4 & 1 & 4\\
0 & 1 & 0 & 0\\
2 & 5 & 3 & 7
\end{array} \right).
$$

Para el siguiente vector de $B$ tenemos que resolver 

$$
(2,1,1)=\alpha (1,0,2)+\beta (4,1,5)+\gamma (1,0,3)
$$

con matriz ampliada:

$$
\left( \begin{array}{rrr|r}
1 & 4 & 1 & 2\\
0 & 1 & 0 & 1\\
2 & 5 & 3 & 1
\end{array} \right).
$$

Observamos que ambos sistemas tienen la misma matriz de coeficientes, y también el tercer sistema que debemos resolver, solo cambian las columnas de términos independientes. Podemos resolver los tres sistemas simultáneamente escribiendo

$$
\left( \begin{array}{rrr|rrr}
1 & 4 & 1 & 4 & 2 & 3\\
0 & 1 & 0 & 0 & 1 & 1\\
2 & 5 & 3 & 7 & 1 & 3
\end{array} \right)\sim_f \left( \begin{array}{rrr|rrr}
1 & 0 & 0 & 5 & -2 & -1\\
0 & 1 & 0 & 0 & 1 & 1\\
0 & 0 & 1 & -1 & 0 & 0
\end{array} \right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,4,1],[0,1,0],[2,5,3]])
B=matrix([[4,2,3],[0,1,1],[7,1,3]]) 
AB=A.augment(B,subdivide=True) #matriz aumentada
show(AB,"~",AB.rref())
</script>
:::

La matriz de cambio de base de $B$ a $B'$ es entonces 

$$
M_{BB'}=\left( \begin{array}{rrr}
 5 & -2 & -1\\
 0 & 1 & 1\\
 -1 & 0 & 0
\end{array} \right).
$$

**Método 2**

Considerando la base canónica en $\mathbb{R}^3$: $B_c=\{(1,0,0),(0,1,0),(0,0,1)\}$ es muy fácil calcular

$$
M_{BB_c}=P=\left( \begin{array}{rrr}
4 & 2 & 3 \\
0 & 1 & 1 \\
7 & 1 & 3 
\end{array} \right)
$$

y 

$$
M_{B'B_c}=Q=\left( \begin{array}{rrr}
1 & 4 & 1 \\
0 & 1 & 0 \\
2 & 5 & 3 
\end{array} \right).
$$

Entonces, $X_c=PX$, $X_c=QX'$ donde $X,X',X_c$ representan a las coordenadas de $\overrightarrow{x}$ en las bases $B,B'$ y $B_c$, respectivamente.
Igualando las dos fórmulas

$$
QX'=PX
$$

y despejando $X'=Q^{-1}PX$, por lo que la matriz $M_{BB'}=Q^{-1}P$.


Si observamos el método anterior, hemos calculado precisamente $Q^{-1}P$ utilizando operaciones elementales.

La matriz $M_{B'B}=(Q^{-1}P)^{-1}=P^{-1}Q$.

::::
:::::

::::: {#exr-5 .basico}

En un espacio vectorial sobre $\mathbb{R}$, tenemos unos vectores $e_{1},e_{2},\dots ,e_{n},\, x$ cuyas coordenadas en una cierta base vienen dadas a continuación. Comprueba que $\{e_{1},e_{2},\dots,e_{n}\}$ es una base en cada uno de los casos, y halla las coordenadas del vector $x$ en dicha base. 

<ol type="a">
<li>
$$
\left.
\begin{array}{c}
e_{1}=(1,0,1)\\
e_{2}=(1,2,2)\\
e_{3}=(0,1,1)
\end{array}
\right\}\quad x=(1,0,2).
$$
</li>
<li>
$$
\left.
\begin{array}{l}
e_{1}=(1,1,1,1)\\
e_{2}=(0,1,1,1)\\
e_{3}=(0,0,1,1)\\
e_{4}=(0,0,0,1)
\end{array}
\right\}\quad x=(1,0,1,0).
$$
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Para comprobar que los vectores $\{e_1,e_2,e_3\}$ forman base es suficiente probar que son linealmente independientes, puesto que son tres que es la dimensión del espacio vectorial. Calculamos el rango de la matriz que forman:

$$
\begin{pmatrix}
1 & 1 & 0\\
0 & 2 & 1\\
1 & 2 & 1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 1 & 0\\
0 & 2 & 1\\
0 & 1 & 1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 & -1\\
0 & 1 & 1\\
0 & 0 & -1
\end{pmatrix}.
$$

Como tiene rango tres, son linealmente independientes y por tanto base.

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,0,1],[1,2,2],[0,1,1]])
show(html(f"${latex(A.T)}$ tiene rango ${A.rank()}$"))
</script>
:::

Para calcular las coordenadas de $x$ en esta base planteamos
$$(1,0,2)=\alpha (1,0,1)+\beta (1,2,2)+\gamma (0,1,1)$$
que nos da el sistema

$$
\left\{\begin{aligned}
\alpha+\beta &= 1,\\
2\beta+\gamma &= 0,\\
\alpha+2\beta+\gamma&=2.
\end{aligned}\right.
$$

Observamos la matriz ampliada y las columnas de la matriz de coeficientes son los vectores de la base, mientras que la de términos independientes es el vector que queremos escribir por coordenadas en esta base:

$$
\left( \begin{array}{rrr|r}
1 & 1 & 0 & 1\\
0 & 2 & 1 & 0\\
1 & 2 & 1 & 2
\end{array} \right).
$$

Recordaremos esta relación para la próxima vez que realicemos este tipo de cálculos. Resolvemos:

$$
\left( \begin{array}{rrr|r}
1 & 1 & 0 & 1\\
0 & 2 & 1 & 0\\
1 & 2 & 1 & 2
\end{array} \right)\sim_f  \left( \begin{array}{rrr|r}
1 & 1 & 0 & 1\\
0 & 2 & 1 & 0\\
0 & 1 & 1 & 1
\end{array} \right)\sim_f \left( \begin{array}{rrr|r}
1 & 0 & -1 & 0\\
0 & 1 & 1 & 1\\
0 & 0 & -1 & -2
\end{array} \right)\sim_f \left( \begin{array}{rrr|r}
1 & 0 & 0 & 2\\
0 & 1 & 0 & -1\\
0 & 0 & 1 & 2
\end{array} \right).
$$

Luego $x=(2,-1,2)_B$.


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,1,0],[0,2,1],[1,2,1]])
b=vector([1,0,2]) 
Ab=A.augment(b,subdivide=True) 
show(Ab,"~",Ab.rref())
</script>
:::
</li>

<li>Procedemos del mismo modo sin repetir los razonamientos, puesto que son idénticos al apartado anterior.

$$
\left( \begin{array}{rrrr|r}
1 & 1 & 1 & 1 & 1\\
0 & 1 & 1 & 1 & 0 \\
0 & 0 & 1 & 1 & 1\\
0 & 0 & 0 & 1 & 0
\end{array} \right)\sim_f \left( \begin{array}{rrrr|r}
1 & 0 & 0 & 0 & 1\\
0 & 1 & 0 & 0 & -1 \\
0 & 0 & 1 & 0 & 1\\
0 & 0 & 0 & 1 & 0
\end{array} \right)
$$

luego son base (la matriz de coeficientes tiene rango cuatro) y $x=(1,-1,1,0)_B$.

Comprobemos el resultado obtenido con <code>sage</code>.

:::{.sage}
<script type="text/x-sage">
A=matrix([[1,1,1,1],[0,1,1,1],[0,0,1,1],[0,0,0,1]])
b=vector([1,0,1,0]) 
Ab=A.augment(b,subdivide=True) 
show(Ab,"~",Ab.rref())
</script>
:::
</li>

</ol>
::::
:::::

::::: {#exr-6 .basico}

Completa $\{(1,1,0),(2,1,1)\}$ a una base de $\mathbb{Q}^3$.

:::: {.callout collapse="true" title="Solución"}

Comenzamos observando que los dos vectores son linealmente independientes (no son múltiplo uno del otro). Se trata de añadir vectores a los dados hasta obtener una base de $\mathbb{Q}^3$, como $\dim(\mathbb{Q}^3)=3$ en cualquier base debe haber tres vectores, con lo que en este caso habrá que añadir un vector. Se puede realizar de infinitas formas, la única condición es que los tres vectores sean linealmente independientes; se aconseja hacerlo de modo que esta condición sea fácil de comprobar.
Partimos de la matriz

$$
\begin{pmatrix}
1 & 2 & \_\\
1 & 1 & \_\\
0 & 1 & \_
\end{pmatrix}
$$ 

y si añadimos una columna sencilla, por ejemplo

$$
\begin{pmatrix}
1 & 2 & 1\\
1 & 1 & 0\\
0 & 1 & 0
\end{pmatrix}
$$

comprobar que el determinante es distinto de cero es muy fácil. Entonces hemos completado con el vector $(1,0,0)$. También valdría añadir $(0,0,1)$:

$$
\begin{pmatrix}
1 & 2 & 0\\
1 & 1 & 0\\
0 & 1 & 1
\end{pmatrix}.
$$

::::
:::::

::::: {#exr-7 .cuerpo_finito-medio}

Determina si los siguientes conjuntos de vectores generan al
espacio vectorial dado.

<ol type="a">
<li>En el conjunto de polinomios de $\mathbb{Z}_5[x]$ de grado menor o igual a dos: $\{1+4x, 3+4x^2\}$.</li>
<li>En el conjunto de polinomios de $\mathbb{Z}_5[x]$ de grado menor o igual a dos: $\{1+4x, 3+4x^2, x\}$.</li>
<li>En $\mathcal{M}_{2}(\mathbb{Z}_7)$: $\left\{ \begin{pmatrix} 1 & 0 \\ 1 & 0
\end{pmatrix}, \begin{pmatrix} 1 & 2 \\ 0 & 0 \end{pmatrix},
\begin{pmatrix} 4 & 6 \\ 3 & 0 \end{pmatrix}, \begin{pmatrix} 5
& 5 \\ 6 & 0 \end{pmatrix}\right\}$.</li>

</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Como la dimensión de este espacio es tres, cualquier conjunto de generadores tiene que tener al menos tres vectores. Así que en este caso la respuesta es negativa.</li>
<li>Estamos en el mismo espacio vectorial y ahora sí tenemos tres vectores. Serán sistema de generadores si y solo si son base, lo que equivale a que sean linealmente independientes. Escribimos sus coordenadas en $B_s=\{1,x,x^2\}$ y calculamos el rango de la matriz que forman:

$$
1+4x=(1,4,0)_{B_s},
$$

$$
3+4x^2=(2,0,4)_{B_s},
$$

$$
x=(0,1,0)_{B_S},
$$

$$
\begin{pmatrix}
1 & 2 & 0\\
4 & 0 & 1\\
0 & 4 & 0
\end{pmatrix}.
$$

Esta matriz tiene determinante $(-1)(4)=-4$ y por tanto son sistema de generadores.</li>

<li>En este caso tenemos cuatro vectores y $\dim(\mathcal{M}_{2}(\mathbb{Z}_7))=4$, así que razonamos como antes, esta vez usando coordenadas en la base estándar

$$
B_s=\left\{ \begin{pmatrix}
1 & 0 \\ 0 & 0 \\
\end{pmatrix}, \begin{pmatrix}
0 & 1 \\ 0 & 0 \\
\end{pmatrix}, \begin{pmatrix}
0 & 0 \\ 1 & 0 \\
\end{pmatrix},\begin{pmatrix}
0 & 0 \\ 0 & 1 \\
\end{pmatrix}\right\},
$$

$$  
\begin{pmatrix} 1 & 0 \\ 1 & 0 \end{pmatrix}=(1,0,1,0)_{B_s},
$$

$$
\begin{pmatrix} 1 & 2 \\ 0 & 0 \end{pmatrix}=(1,2,0,0)_{B_s},
$$

$$
\begin{pmatrix} 4 & 6 \\ 3 & 0 \end{pmatrix}=(4,6,3,0)_{B_s},
$$

$$
\begin{pmatrix} 5 & 5 \\ 6 & 0 \end{pmatrix}=(5,5,6,0)_{B_s}.
$$

Y ahora calculamos el rango de la matriz que forman:

$$
\begin{pmatrix}
1 & 1 & 4 & 5\\
0 & 2 & 6 & 5\\
1 & 0 & 3 & 6\\
0 & 0 & 0 & 0
\end{pmatrix}
$$

que como tiene una fila entera de ceros tiene rango menor que cuatro, luego no son sistema de generadores.</li>

</ol>
::::
:::::


::::: {#exr-8 .cuerpo_finito-basico}

Sea $V = \mathbb{Z}_3^4$ y sean los subespacios vectoriales

$$
U = \left\{(x,y,z,t) \in V ~\left|~
\begin{aligned}
x-y-z &= 0 \\
t &= 0
\end{aligned} \right. \right\}, \qquad W = \langle
(1,1,1,1), (0,1,0,1) \rangle.
$$

<ol type="a">
<li>¿Cuántos elementos hay en $W$?</li>
<li>Calcula unas ecuaciones paramétricas de $U$ y unas ecuaciones cartesianas (o implícitas) de $W$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>$W = \langle (1,1,1,1), (0,1,0,1) \rangle$.
En primer lugar calculamos la base más sencilla y con ella escribimos las paramétricas:

$$
\begin{pmatrix}
1 & 0\\
1 & 1 \\
1 & 0\\
1 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0\\
0 & 1 \\
1 & 0\\
0 & 1
\end{pmatrix},
$$

luego

$$
W \equiv \left\{ \begin{array}{l}
x=1\cdot \lambda_1 + 0\cdot \lambda_2, \\
y=0\cdot \lambda_1 + 1\cdot \lambda_2,\\
z=1\cdot \lambda_1 + 0\cdot \lambda_2,\\
t=0\cdot \lambda_1 + 1\cdot \lambda_2,\\
\end{array}\right.  \lambda_1,\lambda_2\in \mathbb{Z}_3.
$$

Como aparecen 2 parámetros que pueden tomar valores en $\mathbb{Z}_3$, en total hay $3\cdot 3=9$ vectores distintos en $W$.

También se puede razonar sin necesidad de calcular las paramétricas, comprobando que la dimensión de $W$ es dos, simplemente probando que los dos generadores son linealmente independientes.</li>

<li>Paramétricas de $U$.
Para ello resolvemos el sistema que forman las ecuaciones cartesianas, que en este caso ya es escalonado reducido; depende de dos parámetros (las incógnitas $y$ y $z$ son libres):

$$ 
U\equiv  \left\{ \begin{array}{l}
x=\lambda_1 + \lambda_2, \\
y=\lambda_1, \\
z=\lambda_2,\\
t=0.\\
\end{array}\right.
$$

O también,

$$
\left\{ \begin{array}{l}
x=1\cdot \lambda_1 +1\cdot \lambda_2,\\
y=1\cdot \lambda_1 + 0\cdot \lambda_2,\\
z=0\cdot \lambda_1 + 1\cdot \lambda_2,\\
t=0\cdot \lambda_1 + 0\cdot \lambda_2.\\
\end{array}\right. 
$$

Además obtenemos que  una base es:
$$
\{ (1,1,0,0), (1,0,1,0) \}.
$$

</li>

<li>Cartesianas de $W$.
Puesto que ya tenemos las ecuaciones paramétricas de $W$ podemos calcular unas ecuaciones cartesianas eliminando parámetros:
despejamos los dos parámetros $\lambda_1=x$ (en la primera ecuación), $\lambda_2= y$ (en la segunda ecuación), uno en una ecuación paramétrica en la que aparece y sustituimos en las otras dos ecuaciones:

$$
W\equiv \left\{ \begin{array}{r}
x-z=0,\\
y-t=0.
\end{array}\right.
$$

Ha sido tan sencillo porque las ecuaciones paramétricas de las que partimos son las más sencillas (hemos usado la base más sencilla).
También podría procederse formando la matriz

$$
\begin{pmatrix}
x & 1 & 0\\
y & 0 & 1\\
z & 1 & 0\\
t & 0 & 1
\end{pmatrix}
$$ 

e imponiendo que su rango debe ser dos, con lo que hay que elegir dos menores de orden tres que al igualarlos a cero nos den dos ecuaciones que no sean múltiplo una de la otra. Este procedimiento es en general mucho más laborioso.</li>

</ol>
::::
:::::

::::: {#exr-9 .basico}

Para cada uno de los siguientes subespacios de $\mathbb{R}^{4}$ calcula unas ecuaciones paramétricas y unas cartesianas.

<ol type="a">

<li>$U=\{(a,b,-b,a) : a,b\in \mathbb{R} \}$, $W=\{(a,b,0,c) : a,b,c\in \mathbb{R}\}$.</li>

<li>$U\equiv \left\{
\begin{array}{lcrrr}
x_{1} &=& \lambda,\\
x_{2} &=& 0,\\
x_{3} &=& \lambda & +\mu,\\
x_{4} &=& \lambda & +\mu & +\gamma,\\
\end{array}
\right.$
$W\equiv \left\{
\begin{array}{lcrrr}
x_{1} &=& \lambda & +\mu &+\gamma,\\
x_{2} &=& \lambda & +\mu,\\
x_{3} &=& 0,\\
x_{4} &=& \lambda.\\
\end{array}
\right.$</li>

<li>$U=\langle(1,1,0,0), (0,1,1,0), (0,0,1,1)\rangle$, $W\equiv \left\{
\begin{array}{lcrrr}
x_{1} &+x_{2}& & -x_{4} &=0,\\
      & x_{2}&+x_{3}&   &=0,\\
x_{1}&-x_{2}&-x_{3}&-x_{4}&=0.\\
\end{array}
\right.
$</li>

</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Observemos la información que tenemos sobre los vectores que están en $U$: llamamos $(x_1,x_2,x_3,x_4)$ a las coordenadas de un vector de $\mathbb{R}^4$ y para que pertenezca a $U$ se tiene que cumplir:

$$
U\equiv \left\{
\begin{array}{lcrr}
x_{1} &=& a,\\
x_{2} &=& b,\\
x_{3} &=& -b,\\
x_{4} &=& a.\\
\end{array}
\right.
$$

Donde $a$, $b$ son parámetros. Así tenemos unas ecuaciones paramétricas de $U$. Para calcular cartesianas podemos eliminar parámetros, que en este caso es muy sencillo:

$$ 
U\equiv  \left\{ \begin{array}{l}
x_1-x_4=0,\\
x_2+x_3=0.
\end{array}\right. 
$$

También estas ecuaciones podían deducirse de la descripción del conjunto $U$.

De la misma forma, en el caso de $W$ podemos escribir unas paramétricas directamente:

$$
W\equiv \left\{
\begin{array}{lcrr}
x_{1} &=& a,\\
x_{2} &=& b,\\
x_{3} &=& 0,\\
x_{4} &=& c.\\
\end{array}
\right.
$$

Donde $a$, $b$ son parámetros. Como los vectores que acompañan a cada parámetro son linealmente independientes (esos vectores son  $\{(1,0,0,0),(0,1,0,0),(0,0,0,1)\}$) 
entonces la dimensión de $W$ es tres y debe tener una ecuación cartesiana (puesto que la dimensión de $W$ es la dimensión del total menos el número de ecuaciones cartesianas), así que con encontrar una hemos terminado. Observando las paramétricas descubrimos que la tercera ecuación ($x_3=0$) ya es una cartesiana puesto que en ella no aparece ningún parámetro, así que 

$$
W\equiv x_3=0.
$$ 

</li>

<li>Para el caso de $U$, puesto que nos dan unas ecuaciones paramétricas,  podemos usar un argumento idéntico al anterior: los vectores del sistema de generadores que aparecen en las paramétricas que nos dan son linealmente independientes (hay que comprobarlo, claro). En este caso esos vectores son $\{(1,0,1,1),(0,0,1,1),(0,0,0,1)\}$.
Utilizando de nuevo el argumento de antes, necesitamos solo una ecuación cartesiana y la segunda, $x_2=0$, ya lo es, luego 

$$
U\equiv x_2=0.
$$

Para $W$ el mismo razonamiento nos da que $$W\equiv x_3=0.$$ 
</li>

<li>Para $U$ en primer lugar calculamos la base más sencilla:

$$
\begin{pmatrix}
1 & 0 & 0 \\
1 & 1 & 0\\
0 & 1 & 1\\
0 & 0 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0\\
0 & 0 & 1\\
1 & -1 & 1
\end{pmatrix}
$$ 

y con ellas escribimos unas paramétricas:

$$
U\equiv \left\{
\begin{array}{lclr}
x_{1} &=& \lambda_1,\\
x_{2} &=& \lambda_2,\\
x_{3} &=& \lambda_3,\\
x_{4} &=& \lambda_1 -\lambda_2 +\lambda_3.\\
\end{array}
\right.
$$

usando las tres primeras para eliminar parámetros nos queda 

$$
U\equiv x_4=x_1-x_2+x_3,
$$

o bien, 
$$
U\equiv x_1-x_2+x_3-x_4=0.
$$

De $W$ nos dan unas ecuanciones cartesianas y para encontrar unas paramétricas solo hay que resolver el sistema:

$$
\left(\begin{array}{rrrr}
1 & 1 & 0 & -1\\
0 & 1 & 1 & 0\\
1 & -1 & -1 & -1
\end{array}\right)\sim_f \left(\begin{array}{rrrr}
1 & 0 & 0 & -1\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,1,0,-1],[0,1,1,0],[1,-1,-1,-1]])
show(A,"~",A.rref())
</script>
:::

Así obtenemos que $x_4$ actúa como parámetro mientras que las otras tres incógnitas están despejadas:

$$
W\equiv \left\{
\begin{array}{lcrrr}
x_{1} &=& \lambda,\\
x_{2} &=& 0,\\
x_{3} &=& 0,\\
x_{4} &=& 0.\\
\end{array}
\right.
$$

son unas ecuaciones paramétricas de $W$.</li>

</ol>
::::
:::::


::::: {#exr-10 .cuerpo_finito-basico}

<ol type="a">
<li>Calcula las coordenadas del vector $v=(1,1)_B$ respecto de $B'$ siendo
$B=\{(1,1),(1,2)\}$ y $B'=\{(2,1),(0,1)\}$, en el espacio vectorial $\mathbb{Z}_3^2$.</li>
<li>En el espacio vectorial $\mathbb{Z}_3^3$ se considera el plano generado por los vectores $u=(1,2,1)$ y $v=(1,1,2)$. Calcula una ecuación cartesiana de dicho plano.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Debemos calcular en primer lugar las coordenadas de $v$ en la base canónica:

$$
v=(1,1)_B=1\cdot (1,1)+1\cdot (1,2)=(2,0)
$$

y ahora planteamos el sistema:

$$
v=(2,0)=\alpha (2,1)+\beta (0,1)=(\alpha,\beta)_{B'}
$$

que resolvemos:

$$
\left(\begin{array}{cc|c}
2 & 0 & 2\\
1 & 1 & 0
\end{array}\right)\sim_f \left(\begin{array}{cc|c}
1 & 0 & 1\\
0 & 1 & 2
\end{array}\right),
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(3),[[2,0],[1,1]])
b=vector(GF(3),[2,0]) 
Ab=A.augment(b,subdivide=True) 
show(Ab,"~",Ab.rref())
</script>
:::

Luego $v=(1,2)_{B'}$.</li>

<li>Como nos dan un sistema de generadores del subespacio podemos buscar la base más sencilla

$$
\begin{pmatrix}
 1 & 1 \\
 2 & 1 \\
 1 & 2 \\
  \end{pmatrix}\sim_c \begin{pmatrix}
 1 & 0 \\
 0 & 1 \\
 0 & 2 \\
  \end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(3),[[1,1],[2,1],[1,2]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Y con esta base escribimos las ecuaciones paramétricas más sencillas:

$$
\pi\equiv \left\{
\begin{array}{lcrrr}
x &=& \lambda_1,\\
y &=& \lambda_2,\\
z &=& 2\lambda_2.\\
\end{array}
\right.
$$

Eliminando los dos parámetros nos queda 
$$
\pi \equiv 2y-z=0.
$$
</li>
</ol>
::::
:::::

::::: {#exr-11 .basico}

En $\mathbb{R}^4$ consideramos los subespacios

$$
U\equiv \left\{ \begin{array}{l}
x+y+z=0,\\
t=0.\\
\end{array}\right.  \hspace{.5cm} W=\mathcal{L}\{(0,1,1,1),(0,1,-1,1),(-2,1,1,0)\}.
$$

Calcula la base más sencilla de $U$ y unas cartesianas de $W$.

:::: {.callout collapse="true" title="Solución"}

Para calcular la base más sencilla de $U$, de las ecuaciones cartesianas obtendremos unas paramétricas resolviendo el sistema. De estas paramétricas obtenemos una base desde la que calcular la base más sencilla.


Resolver las cartesianas es inmediato puesto que ya es un sistema escalonado reducido, $y$, $z$ actúan como parámetros, luego nos queda:

$$
U\equiv \left\{
\begin{array}{lcrrr}
x &=& -\lambda_1-\lambda_2,\\
y &=& \lambda_1,\\
z &=& \lambda_2,\\
t &=& 0.\\
\end{array}
\right.
$$

Con lo que obtenemos la base de $U$, $\{ (-1,1,0,0),(-1,0,1,0)\}$. Ahora calculamos la base más sencilla a partir de la forma de Hermite por columnas:

$$
\begin{pmatrix}
 -1 & -1  \\
 1 & 0 \\
 0 & -1  \\
 0 & 0 
  \end{pmatrix}\sim_c \begin{pmatrix}
 1 & 0  \\
 0 & 1 \\
 1 & 1  \\
 0 & 0 
  \end{pmatrix},
$$

luego la base más sencilla de $U$ es 

$$ 
\{(1,0,1,0),(0,1,1,0)\}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[-1,-1],[1,0],[0,-1],[0,0]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Para calcular las cartesianas de $W$ procedemos en primer lugar a calcular la base más sencilla:

$$
\begin{pmatrix}
0 & 0 & -2  \\
1 & 1 & 1\\
1 & -1 & 1 \\
1 & 1 & 0 
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0  \\
0 & 1 & 0\\
0 & 0 & 1 \\
1/2 & 1 & 0 
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[0,0,-2],[1,1,1],[1,-1,1],[1,1,0]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Y escribimos las paramétricas:

$$
W\equiv \left\{
\begin{array}{lclrr}
x &=& \lambda_1,\\
y &=& \lambda_2,\\
z &=& \lambda_3,\\
t &=& \frac{1}{2}\lambda_1+\lambda_2.\\
\end{array}
\right.
$$

Eliminando los tres parámetros y reordenando la ecuación restante nos queda

$$
W\equiv x+2y-2t=0.
$$ 
::::
:::::

:::::{#exr-12 .avanzado}

Para los subespacios de $\mathcal{M}_2(\mathbb{R})$ siguientes:

$$
U=\left\{ A\in  \mathcal{M}_2(\mathbb{R}) \mbox{ tal que } A=A^t\right\},
$$

$$
W=\left\{ A\in  \mathcal{M}_2(\mathbb{R})\mbox{ tal que } A=-A^t\right\}.
$$

<ol type="a">
<li>Calcula la dimensión y una base de cada uno de ellos.</li>
<li>Calcula, respecto de la base estándar

$$
B_s=\left\{ \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}; \begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix};\begin{pmatrix}
0 & 0 \\
1 & 0
\end{pmatrix};\begin{pmatrix}
0 & 0 \\
0 & 1
\end{pmatrix}\right\},
$$

unas ecuaciones cartesianas de $U$ y $W$.</li>

<li>Prueba que $\mathcal{M}_2(\mathbb{R})=U\oplus W$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Calcular la dimensión y una base de cada uno de ellos.

$U$ está formado por las matrices simétricas de orden 2, que tienen la forma

$$
\begin{pmatrix}
a & b \\
b & c
\end{pmatrix}.
$$

Una base de este subespacio es

$$
\left\{ \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}, \begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}, \begin{pmatrix}
0 & 0 \\
0 & 1
\end{pmatrix} \right\} 
$$

y por tanto $\dim(U)=3$.

$W$ está formado por las matrices antisimétricas de orden dos que tienen la forma 

$$
\begin{pmatrix}
0 & b \\
-b & 0
\end{pmatrix}.
$$

Una base de este subespacio es

$$
\left\{ \begin{pmatrix}
0 & 1 \\
-1 & 0
\end{pmatrix}\right\}
$$ 

y por tanto $\dim(W)=1$.
</li>

<li>Calcular unas ecuaciones cartesianas de $U$ y $W$.

Dada una matriz de orden $2$

$$
\begin{pmatrix}
x & y \\
z & t
\end{pmatrix}=(x,y,z,t)_{B_s}.
$$

Entonces 

$$
U\equiv \left\{ \begin{array}{l}
x=a,\\
y=b,\\
z=b,\\
t=c.
\end{array} \right.
$$ 

y la cartesiana es $U\equiv y-z=0$.

Por otro lado,

$$
W\equiv  \left\{ \begin{array}{l}
x=0,\\
y=b,\\
z=-b,\\
t=0.
\end{array} \right.
$$ 

y por tanto unas cartesianas son 

$$
W\equiv  \left\{ \begin{array}{l}
x=0,\\
y+z=0,\\
t=0.
\end{array} \right.
$$ 
</li>

<li>Probar que $\mathcal{M}_2(\mathbb{R})=U\oplus W$.

Calculamos $U\cap W$ reuniendo cartesianas:

$$
U\cap W\equiv  \left\{ \begin{array}{l}
x=0,\\
y+z=0,\\
y-z=0,\\
t=0.
\end{array} \right. \sim_f  \left\{ \begin{array}{l}
x=0,\\
y=0,\\
z=0,\\
t=0.
\end{array} \right.
$$ 

Por tanto $U\cap W=\{0 \}$.

Por la fórmula de las dimensiones,

$$
\dim(U) +  \dim(W)= \dim(U\cap W) + \dim(U+W),
$$

deducimos que $\dim(U+W)=4=\dim(\mathcal{M}_2(\mathbb{R}))$ y por tanto $U+W=\mathcal{M}_2(\mathbb{R})$.
</li>
</ol>

::::
:::::


::::: {#exr-13 .medio}

En el espacio $\mathcal{M}_2(\mathbb{R})$ se consideran los subespacios

$$
U=\mathcal{L}\Biggl(\biggl\{\begin{pmatrix}
1 & 2 \\ 0 & 0
\end{pmatrix}, \begin{pmatrix}
1& 0 \\ 0 & 2\\
\end{pmatrix}, \begin{pmatrix}
2  & a \\ 0 & a 
\end{pmatrix}\biggr\}\Biggr),
$$

y $W$ con ecuaciones cartesianas respecto de la base estándar:

$$
W\equiv 2x-y-t=0.
$$

<ol type="a">
<li>Calcular la base más sencilla de $W$.</li>
<li>Calcular la dimensión de $U$ según los valores de $a$.</li>
<li>Probar que cuando $a=2$ se tiene que $U \subseteq W$.</li>
<li>Calcular unas ecuaciones cartesianas de $U \cap W$ para $a\not = 2$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular la base más sencilla de $W$.

De la cartesiana $2x-y-t=0$ obtenemos la reducida: $x-\frac{1}{2} y-\frac{1}{2}t=0$.

Asignando parámetros a las incógnitas secundarias ($y, z$, $t$) y despejando la principal obtenemos
las paramétricas:

$$
\left\{\begin{array}{ll}
x=&\frac{1}{2}\lambda_1 + \frac{1}{2}\lambda_3,\\
y=&\lambda_1,\\
z=&\lambda_2,\\
t=&\lambda_3,\\
\end{array}\right.
$$ 

y por tanto una base es 
$\{(\frac{1}{2},1,0,0)_{B_{s}},(0,0,1,0)_{B_{s}},
(\frac{1}{2},0,0,1)_{B_{s}}\}$.

Para obtener la base más sencilla escalonamos la matriz que se obtiene al escribir las coordenadas de estos vectores por columnas:

$$
\begin{pmatrix}
\frac{1}{2} & 0 & \frac{1}{2}\\
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1\\
\end{pmatrix}
\sim_c
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1\\
2 & -1 & 0\\
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1/2,0,1/2],[1,0,0],[0,1,0],[0,0,1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Así pues, la base más sencilla es:

$$
\left\{
\begin{pmatrix} 1 & 0 \\ 0 & 2 \end{pmatrix},
\begin{pmatrix}
0 & 1 \\ 0 & -1
\end{pmatrix},
\begin{pmatrix}
0 & 0 \\ 1 & 0
\end{pmatrix}
\right\}.
$$

</li>

<li>Calcular la dimensión de $U$ según los valores de $a$.

Escribimos los vectores por sus coordenadas en la base $B_{s}$ y calculamos el rango de la matriz que forman:

$$
\left(\begin{array}{lll}
1 & 1 & 2\\
2 & 0 & a\\
0 & 0 & 0\\
0 & 2 & a
\end{array}\right).
$$ 

Como tiene una fila de ceros, el único menor de orden tres que puede ser no nulo es 

$$
\left|\begin{array}{lll}
1 & 1 & 2\\
2 & 0 & a\\
0 & 2 & a
\end{array}\right|=8-2a-2a=8-4a,
$$ 

así que si $a\not = 2$ el rango es tres y $\dim(U)=3$ y si $a=2$ el rango es dos y $\dim(U)=2$.</li>

<li>Probar que cuando $a=2$ se tiene que $U \subseteq W$.

Hemos visto que para $a=2$ la dimensión de $U$ es dos y por tanto los dos primeros vectores son base de $U$, además cada uno de ellos verifica la ecuación de $W$:

$$
2\cdot 1-2-0=0 
$$

$$ 
2\cdot 1-0-2=0,
$$

así que $U\subseteq W$.</li>

<li>Calcular unas ecuaciones cartesianas de $U \cap W$ para $a\not = 2$.

Si $a\not = 2$ la dimensión de $U$ es tres y unas paramétricas son:

$$
\left\{\begin{array}{ll}
x=&\lambda_1+ \lambda_2+2\lambda_3,\\
y=&2\lambda_1+a\lambda_3,\\
z=&0,\\
t=&2\lambda_2+a\lambda_3.\\
\end{array}\right.
$$ 

Y como solo necesitamos una cartesiana, entonces $z=0$ es la ecuación cartesiana de $U$.

Por tanto,

$$
U\cap W\equiv \left\{ \begin{array}{r}
2x-y-t=0,\\
z=0.
\end{array}\right..
$$
</li>
</ol>
::::
:::::

::::: {#exr-14 .avanzado}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
a & -1 & 1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)
$$

<ol type="a">
<li>Se considera el subespacio $U$ de $\mathbb{R}^4$ con ecuaciones cartesianas $AX=0$. Calcula la base más sencilla de $U$ según los valores de $a$.</li>
<li>Para el subespacio $W$ de $\mathbb{R}^4$ generado por las columnas de $A$ calcula unas ecuaciones cartesianas según los valores de $a$.</li>
<li> Calcula las dimensiones de $U\cap W$ y $U + W$ según los valores de $a$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Calcular la base más sencilla de $U$ según los valores de $a$.

Puesto que se trata del sistema $AX=0$, podemos transformarlo en el sistema escalonado reducido equivalente utilizando operaciones elementales por filas sobre $A$.

En primer lugar distinguimos el caso $a=0$ en el que el elemento en la posición $(1,1)$ no es pivote:

$$
A= \left(\begin{array}{rrrr}
0 & -1 & 1 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_f \left(\begin{array}{rrrr}
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right).
$$

En este caso obtenemos que las ecuaciones cartesianas más sencillas de $U$ son

$$
U\equiv \left\{ \begin{array}{c}
y=0,\\
z=0,\\
t=0.
\end{array} \right. 
$$

Por tanto, $\dim(U)=1$ y la base más sencilla es $\{(1,0,0,0)\}$.

Si $a\not = 0$ entonces

$$
A\sim_f \left(\begin{array}{rrrr}
1 & -1/a & 1/a & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & 0 & 1
\end{array}\right),
$$

y de nuevo distinguimos el caso $a=-1$ cuando no hay pivote en la segunda fila y nos queda

$$
A\sim_f \left(\begin{array}{rrrr}
1 & 1 & -1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{array}\right),
$$

con lo que las cartesianas de $U$ quedan:

$$
U\equiv \left\{ \begin{array}{c}
x+y-z=0,\\
t=0.
\end{array} \right. 
$$

Por tanto, $\dim(U)=2$ y una base sería $\{(1,-1,0,0),(1,0,1,0)\}$, realizando operaciones elementales nos queda que la base más sencilla es  $\{(1,0,1,0),(0,1,1,0)\}$.

Por último, si $a\not = 0,-1$ entonces

$$
A\sim_f \left(\begin{array}{rrrr}
1 & -1/a & 1/a & 0\\
0 & 0 & 1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & -1/a & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right).
$$

En este caso obtenemos que las ecuaciones cartesianas más sencillas de $U$ son

$$
U\equiv \left\{ \begin{array}{c}
x-\frac{1}{a}y=0,\\
z=0,\\
t=0.
\end{array} \right. 
$$

Por tanto $\dim(U)=1$ y la base más sencilla es $\{(1,a,0,0)\}$.
</li>

<li>Calcular unas ecuaciones cartesianas según los valores de $a$.

Ya hemos visto que el rango de $A$ depende de $a$: es tres si $a\not =-1$ y dos cuando $a=-1$. Así que tenemos ya la dimensión de $W$, que coincide con el rango de $A$.

Para $a=-1$:

$$
A= \left(\begin{array}{rrrr}
-1 & -1 & 1 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
0 & 1 & 0 & 0
\end{array}\right).
$$

Es claro que unas cartesianas de $W$ son:

$$
W\equiv \left\{ \begin{array}{c}
y=0,\\
z=0.
\end{array} \right. 
$$

Cuando $a\neq -1$

$$
A= \left(\begin{array}{rrrr}
a & -1 & 1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & a+1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0
\end{array}\right),
$$
y unas cartesianas son:

$$
W\equiv y-z=0.
$$

</li>

<li> Calcular las dimensiones de $U\cap W$ y $U + W$ según los valores de $a$.

Podemos calcular la dimensión de la suma y usar después la fórmula de las dimensiones para obtener la de la intersección. Para ello en cada caso reunimos bases de $U$ y $W$ y calculamos el rango de la matriz que forman, lo que nos da la dimensión de $U+W$:

**Si $a=0$**

$$\left(\begin{array}{r|rrr}
1 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{r|rrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0
\end{array}\right),
$$

entonces $\dim(U+W)=3$.


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,0,1,0],[0,0,1,0],[0,0,1,0],[0,0,0,1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

**Si $a=-1$**

$$
\left(\begin{array}{rr|rr}
1 & 0 & 1 & 0\\
0 & 1 & 0 & 0\\
1 & 1 & 0 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{r|rrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right),
$$

entonces $\dim(U+W)=4$.


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,0,1,0],[0,1,0,0],[1,1,0,0],[0,0,0,1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

**Si $a\not =0,-1$**

$$
\left(\begin{array}{r|rrr}
1 & 1 & 0 & 0\\
a & 0 & 1 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{r|rrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{array}\right),
$$

entonces $\dim(U+W)=4$.

Así que usando $\dim(U) +\dim(W)=\dim(U+W)+ \dim(U\cap W)$ obtenemos:


Si $a=0$, $\dim(U)=1$, $\dim(W)=3$, $\dim(U+W)=3$ y $\dim(U\cap W)=1$.

Si $a=-1$, $\dim(U)=2$, $\dim(W)=2$, $\dim(U+W)=4$ y $\dim(U\cap W)=0$.

Si $a\not =0,-1$, $\dim(U)=1$, $\dim(W)=3$, $\dim(U+W)=4$ y $\dim(U\cap W)=0$.
</li>
</ol>
::::
:::::

::::: {#exr-15 .basico-cuestion}

¿Para qué valores de $a$ son linealmente independientes los vectores $\{ (1,1,1), (-1,2,a), (1, 4, a^2)\}?$


:::: {.callout collapse="true" title="Solución"}

Serán linealmente independientes cuando el rango de la matriz que forman sea 3, lo que ocurre en este caso cuando el determinante de la matriz que forman sea distinto de $0$:

$$
\left| \begin{array}{rrr}
1 & -1 & 1\\
1 & 2 & 4\\
1 & a & a^2
\end{array}\right|=\left| \begin{array}{rrr}
1 & 0 & 0\\
1 & 3 & 3\\
1 & a+1 & a^2-1
\end{array}\right|= \left| \begin{array}{rr}
3 & 3\\
a+1 & a^2-1
\end{array}\right|=3(a^2-1-a-1)=3(a-2)(a+1)
$$

Así que son linealmente independientes para todos los valores reales excepto para $a=2$ y $a=-1$.
::::
:::::

::::: {#exr-16 .basico}

En $\mathbb{R}^{2}$ conocemos la base $B=\{ (1,1),(2,-1)\}$ y que la matriz de cambio de base de $B$ a $B'$ es $P=\begin{pmatrix}
1 &  2\\
2/3  & 1/3\\
\end{pmatrix}$. Calcula $B'$. 


:::: {.callout collapse="true" title="Solución"}

Los vectores de $B'$ escritos en la base canónica forman (por columnas) la matriz de cambio de base de $B'$ a $B_c$, así que calcularemos esta matriz para obtenerlos.
Como la matriz de cambio de base de $B'$ a $B$ es la inversa de $P$ y la de $B$ a $B_c$ es $Q=\begin{pmatrix}
1 & 2\\ 1 &-1\\
\end{pmatrix}$, entonces la matriz que buscamos es 
$Q\cdot P^{-1}$. Calculamos $P^{-1}$:

$$
\left| \begin{array}{rrr}
1 & -1 & 1\\
1 & 2 & 4\\
1 & a & a^2
\end{array}\right|=\left| \begin{array}{rrr}
1 & 0 & 0\\
1 & 3 & 3\\
1 & a+1 & a^2-1
\end{array}\right|= \left| \begin{array}{rr}
3 & 3\\
a+1 & a^2-1
\end{array}\right|=3(a^2-1-a-1)=3(a-2)(a+1)
$$

$$
Q\cdot P^{-1}=\begin{pmatrix}
1 & 2\\ 1 & -1 
\end{pmatrix}\begin{pmatrix}
-1/3 & 2\\
2/3 & -1
\end{pmatrix}=\begin{pmatrix}
1 & 0\\ -1 & 3
\end{pmatrix}
$$

luego $B'=\{ (1,-1), (0,3)\}$.

::::
:::::

::::: {#exr-17 .basico}

En el espacio vectorial $V$, $B=\{ e_1,e_2\}$ es una base. Calcula las coordenadas respecto de la base  $B'=\{e_1+e_2, 2e_1-e_2\}$ del vector $v=(1,-1)_{B}$.


:::: {.callout collapse="true" title="Solución"}

Como $B'=\{(1,1)_B, (2,-1)_B\}$, planteamos 

$$
(1,-1)_B=a(1,1)_B+b(2,-1)_B
$$

y resolvemos 

$$
\left\{ \begin{array}{l}
a+2b=1\\
a-b=-1
\end{array}\right.\sim_f  \left\{ \begin{array}{l}
a=-1/3\\
b=2/3
\end{array}\right.
$$

luego $v=(-1/3,2/3)_{B'}$.

::::
:::::

::::: {#exr-18 .basico}

Calcular la matriz de cambio de base de $B$ a $B'$ siendo

$$
B=\{ (1,1), (-1,1)\}
$$

$$
B'=\{ (1,2), (-1,2)\}
$$

:::: {.callout collapse="true" title="Solución"}

LLamemos 
$P=\left( \begin{array}{rr}
1 & -1 \\
1 & 1 \\
\end{array} \right)$ a la matriz de cambio de base de $B$ a la base canónica, y
$Q=\left( \begin{array}{rr}
1 & -1 \\
2 & 2 \\
\end{array} \right)$ a la matriz de cambio de base de $B'$ a la canónica.
$$
B \longrightarrow^{P}  B_c \longleftarrow^{Q} B'
$$
entonces la matriz de cambio de base de $B$ a $B'$ será $Q^{-1}\cdot P$.

Calculamos $Q^{-1}$:

$$
\left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
2 & 2 & 0 & 1\\
\end{array} \right)\sim_{f} \left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
0 & 4 & -2 & 1\\
\end{array} \right)\sim_{f}
$$

$$
\left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
0 & 1 & -2/4 & 1/4\\
\end{array} \right)
\sim_{f} \left( \begin{array}{rr|rr}
1 & 0& 1/2 & 1/4 \\
0 & 1 & -1/2 & 1/4\\
\end{array} \right)
$$

Así

$$
Q^{-1} \cdot P= \left( \begin{array}{rr}
1/2 & 1/4 \\
-1/2 & 1/4\\
\end{array} \right)\left( \begin{array}{rr}
1 & -1 \\
1 & 1 \\
\end{array} \right)=\left( \begin{array}{rr}
3/4 & -1/4 \\
-1/4 & 3/4 \\
\end{array} \right)
$$

::::
:::::

::::: {#exr-19 .basico}

Calcular las cartesianas más sencillas del subespacio de $\mathbb{R}^4$ generado por
los vectores 

$$
\{(1,1,1,0),(1,-2,1,0),(2,-1,2,0)\}
$$

:::: {.callout collapse="true" title="Solución"}

En primer lugar calculamos la base m\'{a}s sencilla a partir del sistema de generadores dado:

$$
\begin{pmatrix}
1 & 1 & 2 \\
1 & -2 & -1 \\
1 & 1 & 2 \\
0 & 0 & 0
\end{pmatrix}\sim_{c} \begin{pmatrix}
1 & 0 & 0 \\
1 & -3 & -3 \\
1 & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}\sim_{c}
\begin{pmatrix}
1 & 0 & 0 \\
1 & 1 & 0 \\
1 & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}\sim_{c}
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
1 & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}
$$

Así que la base más sencilla es $\{ (1,0,1,0),(0,1,0,0)\}$ a partir de la que escribimos las ecuaciones paramétricas:

$$
\begin{array}{rll}
x= 1\cdot \lambda + 0 \cdot \mu\\
y= 0\cdot \lambda + 1 \cdot \mu\\
z= 1\cdot \lambda + 0 \cdot \mu\\
t= 0\cdot \lambda + 0 \cdot \mu\\
\end{array}
$$

que nos permite obtener las cartesianas

$$
\begin{array}{rl}
x -z =0\\
t= 0\\
\end{array}
$$


::::
:::::

::::: {#exr-20 .cuerpo-finito-avanzado}

En el espacio vectorial $(\mathbb{Z}_5)^4$ se consideran los subespacios:

$$
U=\mathcal{L}((1,1,2,0), (2,1,1,0))
$$

$$
W=\mathcal{L}((2,a,2,0), (0,0,0,1))
$$

siendo $a$ un parámetro. En función de $a$ determinar la dimensión y bases escalonadas de los subespacios $U$, $W$, $U+W$ y $U\cap W$.

:::: {.callout collapse="true" title="Solución"}

Para obtener una base escalonada de $U$ escalonamos por columnas a partir del sistema de generadores dado:

$$
\begin{pmatrix}
1 & 2 \\
1 & 1 \\
2 & 1 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
1 & 4 \\
2 & 2 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
1 & 1 \\
2 & 3 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
0 & 1 \\
4 & 3 \\
0 & 0
\end{pmatrix}
$$

Y obtenemos la base $\{ (1,0,4,0), (0,1,3,0)\}$ y $dim(U)=2$.

De igual manera, para $W$:

$$
\begin{pmatrix}
2 & 0 \\
a & 0 \\
2 & 0 \\
0 & 1
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
3a & 0 \\
1 & 0 \\
0 & 1
\end{pmatrix}
$$

obtenemos la base escalonada $\{ (1,3a,1,0), (0,0,0,1)\}$ y $dim(W)=2$.

Un sistema de generadores de $U+W$ se obtiene uniendo las bases de $U$ y $W$:  
$\mathcal{L}((1,0,4,0), (0,1,3,0), (1,3a,1,0), (0,0,0,1))$.

y se tiene que la dimensión de $U+W$ coincide con el rango de la matriz:

$$
\begin{pmatrix}
1 & 0 & 1 & 0 \\
0 & 1 & 3a & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

cuyo determinante es:

$$
\left| 
\begin{array}{cccc}
1 & 0 & 1 & 0 \\
0 & 1 & 3a & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{array}\right|
=
\left| 
\begin{array}{ccc}
1 & 0 & 1  \\
0 & 1 & 3a \\
4 & 3 & 1  \\
\end{array}\right|
= 1-4-9a = a+2
$$

Luego tenemos dos casos:
<ol type='i'>
<li>Si $a\not = 3$ entonces $dim(U+W)=4$ y en consecuencia $U+W=(\mathbb{Z}_5)^4$ y una base escalonada es la canónica: $\{(1,0,0,0), (0,1,0,0), (0,0,1,0), (0,0,0,1)\}$

Además, en este caso, usando la fórmula de las dimensiones: $dim(U\cap W)= dim(U)+dim(W)-dim(U+W)=2+2-4=0$, luego $U\cap W=0$ y no tiene base (o tiene como base al conjunto vacío $\emptyset$).
</li>

<li>Si $a=3$, entonces obtenemos una base escalonada de $U+W$:

$$
\begin{pmatrix}
1 & 0 & 1 & 0 \\
0 & 1 & 4 & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}\sim_c\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 4 & 0 \\
4 & 3 & 2 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}\sim_c\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
4 & 3 & 0 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}\sim_c\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
4 & 3 & 0 & 0 \\
0 & 0 & 1 & 0
\end{pmatrix} 
$$
 
que es $\{ (1,0,4,0), (0,1,3,0), (0,0,0,1)\}$ y $dim(U+W)=3$.

Usando la fórmula de las dimensiones, en este caso se tiene $dim(U\cap W)= dim(U)+dim(W)-dim(U+W)=2+2-3=1$.

Para determinar la intersección, hemos de obtener unas ecuaciones cartesianas de $U$ y de $W$:

De la base escalonada de $U$ obtenemos las ecuaciones paramétricas

$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & \mu \\ 
z & = & 4\l+3\mu\\
t & = & 0\\
\end{array}
\right.
$$ 

y de aquí, por eliminación de parámetros, las ecuaciones cartesianas:

$$
\left\{
\begin{array}{rcl}
x +2y+z& = & 0 \\
t & = & 0\\
\end{array}
\right.
$$ 

De igual manera, para $W$:

$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & 4\l \\ 
z & = & \l\\
t & = & \mu\\
\end{array}
\right.
$$ 

$$
\left\{
\begin{array}{rcl}
x +4z& = & 0 \\
y+z & = & 0\\
\end{array}
\right.
$$ 

Unimos ambas cartesianas y escalonamos el sistema resultante:

$$
\left\{
\begin{array}{rcl}
x +2y+z& = & 0 \\
t & = & 0\\
x +4z& = & 0 \\
y+z & = & 0\\
\end{array}
\right.
$$ 

$$
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
1 & 0 & 4 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 3 & 3 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 0 & 4 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
\end{array} \right)
$$

Unas ecuaciones cartesianas de $U\cap W$ son:

$$
\left\{
\begin{array}{rcl}
x +4z& = & 0 \\
y+z & = & 0\\
t & = & 0\\
\end{array}
\right.
$$ 

Pasamos a paramétricas resolviendo el sistema:

$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & 4\l\\
z & = & \l\\
t & = & 0\\
\end{array}
\right.
$$ 

y finalmente, obtenemos la base de $U\cap W$: $\{ (1,4,1,0)\}$

</li>
</ol>
::::
:::::

::::: {#exr-21 .avanzado}

Dada la matriz:

$$
A=\begin{pmatrix}
1 & a & -1&a-1\\
0 & a-1 & -1& 0\\
1 & 1 & a+1& a-1\\
2 & a+1 & a& 3a-1
\end{pmatrix} 
$$ 

se consideran los subespacios $U\subseteq\mathbb{R}^4$ generado por las columnas de $A$ y $W\subseteq\mathbb{R}^4$ cuyas ecuaciones cartesianas son $AX=0$.
<ol type='a'> 

<li> Calcula las dimensiones de $U$ y de $W$ según los valores $a$.</li>

<li> Calcula unas ecuaciones cartesianas de $U$ según los valores de $a$. Calcula las dimensiones de $U\cap W$ y $U+W$ según los valores de $a$. </li>

</ol>

:::: {.callout collapse="true" title="Solución"}
<ol type='a'> 
<li> 

Puesto que $U$ está generado por las columnas de $A$, $dim \, U=rg(A)$; 
y como las cartesianas de $W$ vienen dadas por las filas de $A$ entonces 
$dim\, W=dim \, \mathbb{R}^4-\mbox{'nº cartesianas'}= 4-rg(A)$ es claro que tenemos que calcular $rg(A)$ según los valores de $a$. Para ello, como es cuadrada, calculamos en primer lugar el determinante:

$$
|A|= \left|\begin{array}{cccc}
1 & a & -1&a-1\\
0 & a-1 & -1& 0\\
1 & 1 & a+1& a-1\\
2 & a+1 & a& 3a-1
 \end{array}\right|=\left|\begin{array}{cccc}
1 & a & -1&a-1\\
0 & a-1 & -1& 0\\
0 & 1-a & a+2& 0\\
2 & a+1 & a& 3a-1
 \end{array}\right|=\left|\begin{array}{cccc}
1 & a & -1&a-1\\
0 & a-1 & -1& 0\\
0 & 0 & a+1& 0\\
2 & a+1 & a& 3a-1 \end{array}\right|
$$

para lo que hemos realizado operaciones elementales por filas de tipo 3 ($F_3-F_1\rightarrow F_3$ y $F_3-F_2\rightarrow F_3$). Ahora desarrollamos por la tercera fila:

$$
|A|= (a+1)\left|\begin{array}{ccc}
1 & a & a-1\\
0 & a-1 &  0\\
2 & a+1 & 3a-1 \end{array}\right|=(a+1)(a-1)\left|\begin{array}{cc}
1 &  a-1\\
2 &  3a-1 \end{array}\right|=(a+1)^2(a-1)
$$

Así que para $a\not = 1,-1$, $rg(A)=4$. Veamos qué ocurre para los casos particulares:

Si $a=1$ (sustituyendo en la matriz) calculamos la forma de Hermite por columnas (lo que nos dará la base más sencilla de $U$):

$$
A=\begin{pmatrix}
1 & 1 & -1&0\\
0 & 0 & -1& 0\\
1 & 1 & 2& 0\\
2 & 2 & 1& 2
\end{pmatrix}\sim_c  \begin{pmatrix}
1 & 0 & 0&0\\
0 & 0 & -1& 0\\
1 & 0 & 3& 0\\
0 & 0 & 0& 1
\end{pmatrix}\sim_c  \begin{pmatrix}
1 & 0 & 0&0\\
0 & 1 & 0& 0\\
1 & -3 & 0& 0\\
0 & 0 & 1& 0
\end{pmatrix}
$$

Así que $rg(A)=3$ y la base más sencilla de $U$ es $\{ (1,0,1,0),(0,1,-3,0),(0,0,0,1)\}$.

Lo mismo para $a=-1$:

$$
A=\begin{pmatrix}
1 & -1 & -1&-2\\
0 & -2 & -1& 0\\
1 & 1 & 0& -2\\
2 & 0 & -1& -4
\end{pmatrix} \sim_c \begin{pmatrix}
1 & 0 & 0&0\\
0 & -2 & -1& 0\\
1 & 2 & 1& 0\\
2 & 2 & 1& 0
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0&0\\
0 & 1 & 0& 0\\
1 & -1 & 0& 0\\
2 & -1 & 0& 0
\end{pmatrix}
$$ 

Así que $rg(A)=2$ y la base más sencilla de $U$ es $\{ (1,0,1,2),(0,1,-1,-1)\}$.

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$rg(A)$</TH><TH>$dim\; U$</TH><TH>$dim\; W$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a\not = 1,-1$</TH><TD>4</TD><TD>4</TD><TD>0</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = 1$</TH><TD>3</TD><TD>3</TD><TD>1</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = -1$</TH><TD>2</TD><TD>2</TD><TD>2</TD>
</TR>
</TABLE>
</CENTER>

</li>

<li> Calculamos las cartesianas de $U$ en cada caso: 
<ul>
<li>

$\boxed{a\not = 1,-1}$: 
Como $dim \, U=4$ entonces $U=\mathbb{R}^{4}$ y no hay cartesianas (los vectores de $\mathbb{R}^{4}$ no tienen que cumplir ninguna condición extra para pertenecer a $U$).
</li>
<li>

$\boxed{a=1}$ Tenemos la base más sencilla que hemos calculado antes y, por tanto, unas paramétricas:

$$
U\equiv \left\{ \begin{array}{l}
x=\lambda_1\\
y=\lambda_2\\
z=\lambda_1-3\lambda_2\\
t=\lambda_3
\end{array}\right.
$$

de las que obtenemos, eliminando parámetros,  la cartesiana  $U\equiv \boxed{ x-3y-z=0}$
</li>
<li>

$\boxed{a=-1}$ Tenemos la base más sencilla que hemos calculado antes y, por tanto, unas paramétricas:

$$
U\equiv \left\{ \begin{array}{l}
x=\lambda_1\\
y=\lambda_2\\
z=\lambda_1-\lambda_2\\
t=2\lambda_1-\lambda_2
\end{array}\right.
$$

de las que obtenemos, eliminando parámetros,  las cartesianas  $U\equiv \boxed{ \begin{array}{r} x-y-z=0\\ 2x-y-t=0\end{array} }$
</li>
</ul>

Para calcular $dim\, U+W$ y $dim\, U\cap W$ calularemos $U\cap W$ (porque ya tenemos las cartesianas de $U$ y las de $W$, aunque estas últimas sin simplificar) y después usaremos la fórmula de las dimensiones.

$\boxed{a\not = 1,-1}$ Como $U=\mathbb{R}^4$ y $W=\{0\}$, entonces $U\cap W=\{0\}$.

$\boxed{a = 1}$ Las filas de $A$ son los coeficientes de las cartesianas de $W$, le añadimos la fila de la cartesiana de $U$:

$$
\begin{pmatrix}
1 & 1 & -1&0\\
0 & 0 & -1& 0\\
1 & 1 & 2& 0\\
2 & 2 & 1& 2\\
\hline
1 & -3 & -1 & 0
\end{pmatrix}\sim_f  \begin{pmatrix}
1 & 1 & 0&0\\
0 & 0 & 1& 0\\
1 & 1 & 0& 0\\
2 & 2 & 0& 2\\
1 & -3 & 0 & 0
\end{pmatrix}\sim_f  \begin{pmatrix}
1 & 1 & 0&0\\
0 & 0 & 1& 0\\
0 & 0 & 0& 0\\
0 & 0 & 0& 1\\
0 & -4 & 0 & 0
\end{pmatrix}\sim_f \sim_f  \begin{pmatrix}
1 & 0 & 0&0\\
0 & 1 & 0& 0\\
0 & 0 & 1& 0\\
0 & 0 & 0& 1\\
0 & 0 & 0 & 0
\end{pmatrix}
$$

Luego las cartesianas de $U\cap W$ son 

$U\cap W\equiv \boxed{ \begin{array}{r} x=0\\ y=0 \\ z=0 \\ t=0\end{array} }$

y por tanto $U\cap W=\{0\}$ con lo que $dim\, U\cap W=0$. 

$\boxed{a = -1}$ Las filas de $A$ son los coeficientes de las cartesianas de $W$, le añadimos las dos filas de las cartesianas de $U$:

$$
\begin{pmatrix}
1 & -1 & -1&-2\\
0 & -2 & -1& 0\\
1 & 1 & 0& -2\\
2 & 0 & -1& -4\\
1 & -1 & -1& 0\\
2 & -1 & 0 & -1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & -1 & -1&-2\\
0 & -2 & -1& 0\\
0 & 2 & 1& 0\\
0 & 2 & 1& 4\\
0 & 0 & 0& 2\\
0 & 1 & 2 & 4
\end{pmatrix}\sim_f \begin{pmatrix}
1 & -1 & -1&0\\
0 & 0 & 0& 0\\
0 & 2 & 1& 0\\
0 & 0 & 0& 0\\
0 & 0 & 0& 1\\
0 & 1 & 2 & 0
\end{pmatrix}\sim_f\begin{pmatrix}
1 & 0 & -1/2&0\\
0 & 1 & 1/2& 0\\
0 & 0 & 3/2 & 0\\
0 & 0 & 0& 1\\
0 & 0 & 0& 0\\
0 & 0 & 0& 0\\
\end{pmatrix}
$$

que tiene 4 pivotes y por tanto de nuevo $U\cap W=\{0\}$.

Ahora resumimos y aplicamos la fórmula de las dimensiones para calcular las dimensiones que faltan:

$$
\boxed{dim\, U +dim\, W= dim\, U\cap W + dim\, U+W}
$$

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$dim\; U$</TH><TH>$dim\; W$</TH><TH>$dim\; U\cap W$</TH><TH>$dim\; U+W$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a\not = 1,-1$</TH><TD>4</TD><TD>0</TD><TD>0</TD><TD>4</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = 1$</TH><TD>3</TD><TD>1</TD><TD>0</TD><TD>4</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = -1$</TH><TD>2</TD><TD>2</TD><TD>0</TD><TD>4</TD>
</TR>
</TABLE>
</CENTER>

</li>
</ol>

::::
:::::

::::: {#exr-22 .basico}

En $\mathbb{R}^4$ se consideran los subespacios 

$$
U\equiv x+y+z=0\; \mbox{ y } W\equiv \left\{ \begin{array}{l} 
x=0\\
y-z=0
\end{array}\right.
$$

<ol type='a'>
<li>Calcula las bases más sencillas de $U$ y $W$.</li>
<li>Calcula $U+W$ y $U\cap W$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>

$dim\, U= dim \mathbb{R}^4-\mbox{'nº cartesianas'}=4-1=3$, así que una base está formada por 3 soluciones de la ecuación (en $\mathbb{R}^4$, por tanto hay 4 incógnitas) que sean linealmente independientes, por ejemplo:

$$
\{(1,-1,0,0),(1,0,-1,0),(0,0,0,1)\}
$$

Para calcular la base más sencilla reducimos por columnas la matriz que forman estos vectores:

$$
\left(\begin{array}{rrr}
\boxed{1} & 1 & 0 \\
-1 & 0 & 0\\
0 & -1 & 0\\
0 & 0 & 1 
\end{array}\right)\sim_c \left(\begin{array}{rrr}
\boxed{1} & 0 & 0 \\
-1 & \boxed{1} & 0\\
0 & -1 & 0\\
0 & 0 & 1 
\end{array}\right)\sim_c \left(\begin{array}{rrr}
\boxed{1} & 0 & 0 \\
0 & \boxed{1} & 0\\
-1 & -1 & 0\\
0 & 0 & \boxed{1} 
\end{array}\right)
$$

luego la base más sencilla para $U$ es 

$$
\{(1,0,-1,0),(0,1,-1,0),(0,0,0,1)\}
$$

Del mismo modo procedemos para $W$ que tiene $dim \, W=4-2=2$; una base es 

$$
\{(0,1,1,0),(0,0,0,1)\}
$$ 
que ya es la base más sencilla.
</li>
<li> 
Para calcular una base de $U+W$ reunimos bases de ambos y reducimos para obtener la base más sencilla:

$$
\left(\begin{array}{rrr|rr}
\boxed{1} & 0 & 0 & 0 & 0\\
0 & \boxed{1} & 0 & 1 & 0\\
-1 & -1 & 0& 1 & 0\\
0 & 0 & \boxed{1} & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 0\\
0 & \boxed{1} & 0 & 0 & 0\\
-1 & -1 & 0& 2 & 0\\
0 & 0 & \boxed{1} & 0 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 0\\
0 & \boxed{1} & 0 & 0 & 0\\
0 & 0 & \boxed{1}& 0 & 0\\
0 & 0 & 0 & \boxed{1} & 0
\end{array}\right)
$$

Así que $U+W=\mathbb{R}^4$.
Para obtener unas ecuaciones cartesianas de $U\cap W$ reunimos las de ambos y reducimos el sistema:

$$
U\cap W\equiv \left\{ \begin{array}{l} 
x+y+z=0\\
x=0\\
y-z=0
\end{array}\right. \sim_f  \left\{ \begin{array}{l} 
x=0\\
y=0\\
z=0
\end{array}\right.
$$

que tiene por tanto dimensión 1.
</li>
</ol>

::::
:::::

::::: {#exr-23 .avanzado}

Se consideran los subespacios vectoriales de $\mathbb{R}^4$, que dependen del parámetro $a \in \mathbb{R}$:

$$
U=\mathcal{L}\{ (1,0,1,1),(0,a,1,2),(a,0,1,-3)\}
$$

$$
W=\{(x,y,z,t)\in \mathbb{R}^4 / x+ay-z-t=0; x+ay-z+t=0\}
$$

Se pide:

<ol type='a'>
<li>Hallar, en función de $a$, una base y la dimensión de $U$ y de $W$.</li>
<li>Calcular, en función de $a$, la dimensión de $U+W$ y la de $U\cap W$.</li>
<li>Para $a=1$ calcula una base de $W\cap U$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>
Para $U$ observamos si el sistema de generadores proporcionado es base:

$$
\left(\begin{array}{ccc}
1 & 0 & a\\  
0 & a &  0\\  
1 & 1 & 1\\  
1 & 2 & -3
  \end{array}
\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & a & 0\\  
1 & 1 & 1-a\\  
1 & 2 & -3-a
  \end{array}
\right) 
$$

Si $a\not= 0,1$ entonces aparecen 3 pivotes y por tanto los 3 vectores son linealmente independientes y $dim\, U=3$. Estudiamos los casos particulares:

$\boxed{a=0}$

$\left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & 0 & 0\\  
1 & 1 & 1\\  
1 & 2 & -3
\end{array}
\right)\sim_c  \left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & 0 & 0\\  
0 & 1 & 0\\  
-1 & 2 & -5
\end{array}
\right)\sim_c  \left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & 0 & 0\\  
0 & 1 & 0\\  
0 & 0 & 1
\end{array}
\right)
$ también son linealmente independientes y $dim\, U=3$.

$\boxed{a=1}$

$\left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & 1 & 0\\  
1 & 1 & 0\\  
1 & 2 & -4
\end{array}
\right)\sim_c\left(\begin{array}{ccc}
1 & 0 & 0\\  
0 & 1 & 0\\  
1 & 1 & 0\\  
0 & 0 & 1
\end{array}
\right)$ también son linealmente independientes y $dim\, U=3$.

Así que para todo valor de $a$ el sistema generador dado es base de $U$.
Para $W$ observamos sus ecuaciones cartesianas y utilizamos que $$dim\, W= dim\, \mathbb{R}^4 -\mbox{nº cartesianas}$$ pero observando que sea el número mínimo de cartesianas, así que reducimos la matriz de coeficientes del sistema:

$$
\left( \begin{array}{rrrr}
1 & a & -1 & -1\\
1 & a & -1 & 1
\end{array}\right) \sim_f \left( \begin{array}{rrrr}
1 & a & -1 & -1\\
0 & 0 & 0 & 1
\end{array}\right)\sim_f \left( \begin{array}{rrrr}
1 & a & -1 & 0\\
0 & 0 & 0 & 1
\end{array}\right)
$$  

que tiene rango 2 independientemente del valor de $a$, así que $dim\, W= dim\, \mathbb{R}^4 -2=2$. Además, de las cartesianas
$W\equiv \left\{ \begin{array}{rr}
x+ay-z&=0\\
&t=0
\end{array}\right.$ obtenemos unas paramétricas:
$W\equiv \left\{ \begin{array}{rl}
x=&-a\lambda_1+\lambda_2\\
y=&\lambda_1\\
z=&\lambda_2\\
t=&0\\
\end{array}\right.$ y una base de $W$ es $\{(-a,1,0,0),(1,0,1,0)\}$.
</li>

<li> 
Como tenemos bases de ambos subespacios es más fácil calcular $U+W$ para el que un sistema de generadores se obtiene reuniendo bases de ambos subespacios:

$$
\left(\begin{array}{rrr|rr}
1 & 0 & 0 & -a & 1\\  
0 & a & 0 & 1 & 0\\  
1 & 1 & 1-a & 0 & 1\\  
1 & 2 & -3-a & 0 & 0
\end{array}
\right) \sim_c \left(\begin{array}{rrrrr}
1 & 0 & 0 & -a & 0\\  
0 & a & 0 & 1 & 0\\  
1 & 1 & 1-a & 0 & 0\\  
0 & 0 & 0 & 0 & \boxed{1}
\end{array}
\right)\sim_c \left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 0\\  
0 & a & 0 & \boxed{1} & 0\\  
1 & 1 & 1-a & a & 0\\  
0 & 0 & 0 & 0 & \boxed{1}
\end{array}
\right)
$$

Observamos que si $a\not = 1$ hay 4 pivotes y entonces $dim\, U+W=4$, es decir, $U+W=\mathbb{R}^4$. Veamos qué ocurre en el caso $a=1$:

$$
\sim_c \left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 0\\  
0 & \boxed{1} & 0 & 1 & 0\\  
1 & 1 & 0 & 1 & 0\\  
0 & 0 & 0 & 0 & \boxed{1}
\end{array}
\right)\sim_c \left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 0\\  
0 & \boxed{1} & 0 & 0 & 0\\  
1 & 1 & 0 & 0 & 0\\  
0 & 0 & \boxed{1}& 0 & 0
\end{array}
\right)
$$

En este caso $dim\, U+W=3$, y por tanto, como $U\subseteq U+W$ y tienen la misma dimensión $U+W=U$.
Para calcular la $dim\, U \cap W$
usamos la fórmula de las dimensiones y los resultados obtenidos:
<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$dim\; U$</TH><TH>$dim\; W$</TH><TH>$dim\; U+W$</TH><TH>$dim\; U\cap W$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a\not = 1$</TH><TD>3</TD><TD>2</TD><TD>4</TD><TD>$\boxed{1}$</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = 1$</TH><TD>3</TD><TD>2</TD><TD>3</TD><TD>$\boxed{2}$</TD>
</TR>
</TABLE>
</CENTER>
</li>

<li> 
Para $a=1$ como $U+W=U$ entonces $U\cap W=W$ y una base ha sido obtenida en el primer apartado:

$$
\{ (-1,1,0,0),(1,0,1,0)\}
$$
</li>
</ol>

::::
:::::

::::: {#exr-24 .medio}
En $\mathcal{P}^2(\mathbb{R})$, el espacio de los polinomios de grado menos o igual que 2 con coeficientes reales, se consideran los subespacios

$$
U_1=\{ p(x)\in \mathcal{P}^2(\mathbb{R}) / xp'(x)=p(x)\}
$$

$$
U_2=\{ p(x)\in \mathcal{P}^2(\mathbb{R}) / p(x)=p(-x)\}
$$

Calcula dimensión, base y unas cartesianas (respecto de la base estándar $B_s=\{1,x,x^2\}$) de cada uno de ellos. Prueba que $U_1$ y $U_2$ son complementarios.  

:::: {.callout collapse="true" title="Solución"}

Como $p(x)=a_0+a_1x+a_2x^2=(a_0,a_1,a_2)_{B_s}$

y $xp'(x)=x(a_1+2a_2x)=a_1x+2a_2x^2=(0,a_1,2a_2)_{B_s}$
Entonces unas cartesianas de $U_1$ son:

$$
\left\{ \begin{array}{l} 
a_0=0\\
a_1=a_1\\
a_2=2a_2
\end{array}\right. \sim \left\{ \begin{array}{l} 
a_0=0\\
a_2=0
\end{array}\right.
$$

y tiene $dim\, U_1=3-\mbox{ nº cart.}=3-2=1$.

Ahora $p(-x)=a_0-a_1x+a_2x^2=(a_0,-a_1,a_2)_{B_s}$
luego unas cartesianas de $U_2$ son:

$$
\left\{ \begin{array}{l} 
a_0=a_0\\
a_1=-a_1\\
a_2=a_2
\end{array}\right. \sim \left\{ 
\begin{array}{l} 
a_1=0\\
\end{array}\right.
$$

y tiene $dim\, U_2=3-\mbox{ nº cart.}=3-1=2$
Para ver que son complementarios calculamos su intersección, reuniendo cartesianas:

$$
U_1 \cap U_2\equiv
\left\{ \begin{array}{l} 
a_0=0\\
a_2=0\\
a_1=0
\end{array}\right.
$$

y por tanto $U_1\cap U_2=\{0\}$.
Ahora, para probar que $U_1+U_2=\mathbb{R}^{3}$ basta usar la fórmula de las dimensiones:

$$
dim\, U_1\, +\, dim\, U_2 \,=\, dim\, (U_1\cap U_2)\, +\, dim\, (U_1+U_2)
$$

nos queda que $dim\, U_1+U_2=3$. Así que son complementarios.

::::
:::::

::::: {#exr-25 .avanzado}
En $\mathbb{R}^4$ se consideran los subespacios

$$
U\equiv \left\{ \begin{array}{l} 
x+y+z=0\\
(a+1)y+(a+1)t=0\\
-x+ay+(a-1)z+at=0
\end{array}\right.
$$

$$
W=\mathcal{L}((1,1,1,0),(0,a+1,0,a+1),(-1,a,a-1,a))
$$

<ol type='a'> 

<li> Calcula las dimensiones de $U$ y de $W$ según los valores $a$.</li>

<li> Calcula la base más sencilla de $W$ según los valores de $a$. </li>

<li> Para $a=1$ calcula $U+W$ y $U\cap W$. </li>

</ol>

:::: {.callout collapse="true" title="Solución"}
<ol type='a'> 
<li> 
Como de $U$ tenemos unas ecuaciones cartesianas, utilizamos la fórmula $dim\, U=dim\ \mathbb{R}^4 -\mbox{\it nº cart}$ por lo que necesitamos determinar el nº de cartesianas, es decir, el rango de la matriz de coeficientes del sistema:

$$
\left(\begin{array}{cccc}
1 & 1 & 1 & 0\\
0 & a+1 & 0 & a+1\\
-1 & a & a-1 & a
\end{array}\right)\sim_f \left(\begin{array}{cccc}
1 & 1 & 1 & 0\\
0 & a+1 & 0 & a+1\\
0 & a+1 & a & a
\end{array}\right)\sim_f \left(\begin{array}{cccc}
1 & 1 & 1 & 0\\
0 & a+1 & 0 & a+1\\
0 & 0 & a & -1
\end{array}\right)\sim_f
$$

que tiene rango 3 si $a\not = -1$ y rango 2 si $a=-1$. 
Para $W$ estudiamos cuántos vectores del sistema de generadores son linealmente independientes, para lo que hay que calcular el rango de la matriz:

$$
\left(\begin{array}{ccc}
1 & 0 & -1 \\
1 & a+1 & a\\
1 & 0 & a-1\\
0 & a+1 & a 
\end{array}\right)
$$

que es la traspuesta de la anterior. Por tanto se tiene

<ul>
  <li> Si $\boxed{a=-1}$ $dim\, U= 2$ y $dim\, W=2$. </li>

  <li> Si $\boxed{a\not=-1}$ $dim\, U= 1$ y $dim\, W=3$. </li>
</ul>

</li>
<li>
Realmente hay que calcular la forma de Hermite por columnas de la matriz formada por el sistema de generadores.
Aprovechamos las operaciones elementales que hicimos en el apartado anterior:

$$
\left(\begin{array}{ccc}
1 & 0 & -1 \\
1 & a+1 & a\\
1 & 0 & a-1\\
0 & a+1 & a 
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0 \\
1 & a+1 & 0\\
1 & 0 & a\\
0 & a+1 & -1 
\end{array}\right)
$$

Cuando $a=-1$ 

$$
\left(\begin{array}{ccc}
1 & 0 & 0 \\
1 & 0 & 0\\
1 & 0 & -1\\
0 & 0 & -1 
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0 \\
1 & 0 & 0\\
0 & 1 & 0\\
-1 & 1 & 0 
\end{array}\right)
$$

luego la base más sencilla es $\{(1,1,0,-1), (0,0,1,1) \}$.
Si $a\not = -1$ 

$$
\sim_c \left(\begin{array}{ccc}
1 & 0 & 0 \\
1 & 1 & 0\\
1 & 0 & a\\
0 & 1 & -1 
\end{array}\right)\sim_c \left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0\\
1 & 0 & a\\
-1 & 1 & -1 
\end{array}\right)
$$

y hay que distinguir dos casos: 

<ul>
  <li> Si $\boxed{a=0}$ la base más sencilla es $\{(1,0,1,0), (0,1,0,0),(0,0,0,1)\}$; </li>

  <li> Si $\boxed{a\not =-1,0}$ la base más sencilla es $\{(1,0,0,(1-a)/a),(0,1,0,1),(0,0,1,-1/a)\}$.  </li>
</ul>

</li>
<li>
Para $a=1$ ya tenemos la base más sencilla de $W$: $\{(1,0,0,0),(0,1,0,1),(0,0,1,-1)\}$. Podemos calcular unas cartesianas escribiendo primero unas paramétricas:

$$
W=\left\{ \begin{array}{ll}
x= & \lambda_1\\
y= & \lambda_2\\
z= & \lambda_3\\
t= &  \lambda_2-\lambda_3\\
\end{array}\right.
$$

que nos da la cartesiana $y-z-t=0$. Reuniendo las cartesianas de ambos subespacios:

$$
U\cap W\equiv \left\{ \begin{array}{l} 
x+y+z=0\\
2y+2t=0\\
z-t=0\\
y-z-t=0
\end{array}\right. \sim \left\{ \begin{array}{l} 
x+y+z=0\\
y+t=0\\
z-t=0\\
y-2t=0
\end{array}\right.\sim \left\{ \begin{array}{l} 
x=0\\
y=0\\
z=0\\
t=0
\end{array}\right.
$$

con lo que $U\cap W=\{0\}$. 

Ahora, usando la fórmula de las dimensiones

$$
dim\, U+dim\, W= dim\, U+W \,+ dim\, U\cap W
$$

obtenemos que $dim\, U+W=4$ y, por tanto, $U+W= \mathbb{R}^4$.
</li>
</ol>

::::
:::::

::::: {#exr-26 .cuerpo_finito-medio}
En el espacio vectorial $(\mathbb{Z}_5)^4$ se consideran los subespacios:

$$
U=\mathcal{L}((1,1,2,0), (2,1,1,0))
$$

$$
W=\mathcal{L}((2,a,2,0), (0,0,0,1))
$$

siendo $a$ un parámetro.  
En función de $a$ determinar la dimensión y bases escalonadas de los subespacios $U$, $W$, $U+W$ y $U\cap W$.

:::: {.callout collapse="true" title="Solución"}

Para obtener una base escalonada de $U$ escalonamos por columnas a partir del sistema de generadores dado:

$$
\begin{pmatrix}
1 & 2 \\
1 & 1 \\
2 & 1 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
1 & 4 \\
2 & 2 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
1 & 1 \\
2 & 3 \\
0 & 0
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
0 & 1 \\
4 & 3 \\
0 & 0
\end{pmatrix}
$$

Y obtenemos la base $\{ (1,0,4,0), (0,1,3,0)\}$ y $dim(U)=2$.

De igual manera, para $W$:

$$
\begin{pmatrix}
2 & 0 \\
a & 0 \\
2 & 0 \\
0 & 1
\end{pmatrix}
\sim_c 
\begin{pmatrix}
1 & 0 \\
3a & 0 \\
1 & 0 \\
0 & 1
\end{pmatrix}
$$

obtenemos la base escalonada $\{ (1,3a,1,0), (0,0,0,1)\}$ y $dim(W)=2$.

Un sistema de generadores de $U+W$ se obtiene uniendo las bases de $U$ y $W$:  
$\{ (1,0,4,0), (0,1,3,0), (1,3a,1,0), (0,0,0,1)\}$.

y se tiene que la dimensión de $U+W$ coincide con el rango de la matriz:

$$
\begin{pmatrix}
1 & 0 & 1 & 0 \\
0 & 1 & 3a & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

cuyo determinante es:

$$
\left| 
\begin{array}{cccc}
1 & 0 & 1 & 0 \\
0 & 1 & 3a & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{array}\right|
=
\left| 
\begin{array}{ccc}
1 & 0 & 1  \\
0 & 1 & 3a \\
4 & 3 & 1  \\
\end{array}\right|
= 1-4-9a = a+2
$$

Luego tenemos dos casos:
<ul> 
<li> 
<b>Caso 1. </b>Si $a\neq3$ entonces $dim(U+W)=4$ y en consecuencia $U+W=(\mathbb{Z}_5)^4$ y una base escalonada es la canónica: $\{(1,0,0,0), (0,1,0,0), (0,0,1,0), (0,0,0,1)\}$  
Además, en este caso, usando la fórmula de las dimensiones: $dim(U\cap W)= dim(U)+dim(W)-dim(U+W)=2+2-4=0$, luego $U\cap W=0$ y no tiene base (o tiene como base al conjunto vacío $\emptyset$).

</li>
<li> 
<b>Caso 2. </b>Si $a=3$, entonces obtenemos una base escalonada de $U+W$:

$$
\begin{pmatrix}
1 & 0 & 1 & 0 \\
0 & 1 & 4 & 0 \\
4 & 3 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
\sim_c
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 4 & 0 \\
4 & 3 & 2 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
\sim_c
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
4 & 3 & 0 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix} 
\sim_c
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
4 & 3 & 0 & 0 \\
0 & 0 & 1 & 0
\end{pmatrix} 
$$

que es $\{ (1,0,4,0), (0,1,3,0), (0,0,0,1)\}$ y $dim(U+W)=3$.

Usando la fórmula de las dimensiones, en este caso se tiene $dim(U\cap W)= dim(U)+dim(W)-dim(U+W)=2+2-3=1$.

Para determinar la intersección, hemos de obtener unas ecuaciones cartesianas de $U$ y
de $W$:

de la base escalonada de $U$ obtenemos las ecuaciones paramétricas
$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & \mu \\ 
z & = & 4\l+3\mu\\
t & = & 0\\
\end{array}
\right.
$$ 
y de aqui, por eliminación de parámetros, las ecuaciones cartesinas:

$$
\left\{
\begin{array}{rcl}
x +2y+z& = & 0 \\
t & = & 0\\
\end{array}
\right.
$$ 
De igual manera, para $W$:
$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & 4\l \\ 
z & = & \l\\
t & = & \mu\\
\end{array}
\right.
$$ 

$$
\left\{
\begin{array}{rcl}
x +4z& = & 0 \\
y+z & = & 0\\
\end{array}
\right.
$$ 
Unimos ambas cartesianas y escalonamos el sistema resultante:

$$
\left\{
\begin{array}{rcl}
x +2y+z& = & 0 \\
t & = & 0\\
x +4z& = & 0 \\
y+z & = & 0\\
\end{array}
\right.
$$ 

$$
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
1 & 0 & 4 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 3 & 3 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 2 & 1 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
\end{array} \right)
\sim_f
\left(  \begin{array}{cccc|c}
1 & 0 & 4 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 \\
\end{array} \right)
$$

Unas ecuaciones cartesianas de $U\cap W$ son:
$$
\left\{
\begin{array}{rcl}
x +4z& = & 0 \\
y+z & = & 0\\
t & = & 0\\
\end{array}
\right.
$$ 

Pasamos a paramétricas resolviendo el sistema:

$$
\left\{
\begin{array}{rcl}
x & = & \l \\
y & = & 4\l\\
z & = & \l\\
t & = & 0\\
\end{array}
\right.
$$ 
y finalmente, obtenemos la base de $U\cap W$: $\{ (1,4,1,0)\}$
</li>
</ul>

::::
:::::

::::: {#exr-27 .basico} 

En el espacio vectorial $V$, $B=\{ e_1,e_2\}$ es una base. Calcula las coordenadas respecto de la base  $B'=\{e_1+e_2, 2e_1-e_2\}$ del vector $v=(1,-1)_{B}$.


:::: {.callout collapse="true" title="Solución"}

Como $B'=\{(1,1)_B, (2,-1)_B\}$, planteamos 

$$
(1,-1)_B=a(1,1)_B+b(2,-1)_B
$$

y resolvemos 

$$
\left\{ \begin{array}{l}
a+2b=1,\\
a-b=-1.
\end{array}\right.\sim_f  \left\{ \begin{array}{l}
a=-1/3,\\
b=2/3.
\end{array}\right.
$$

Luego $v=(-1/3,2/3)_{B'}$.

::::
:::::

::::: {#exr-28 .medio} 

En $\mathcal{P}_3(\mathbb{R})$ se consideran los subespacios vectoriales:

$$
U=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=p(x) \}, W=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=-p(x) \}.
$$

Comprobar que $\mathcal{P}_3(\mathbb{R})= U\oplus W$.

:::: {.callout collapse="true" title="Solución"}

Los polinomios que cumplen la condición de $U$ son los polinomios pares, es decir, aquellos en los que solo aparecen las potencias pares de la indeterminada, y los que pertenecen a $W$ son los impares. Podemos realizar estas operaciones sin más que usar las coordenadas respecto de la base estándar $B_s=\{1,x,x^2,x^3\}$:

$$
p(x)=(a_0,a_1,a_2,a_3)_{B_s}=(a_0,-a_1,a_2,-a_3)_{B_s}=p(-x).
$$

Así las cartesianas de $U$ son
$\left\{\begin{array}{l}
a_1=0,\\
a_3=0.
\end{array}\right.$ Y una base $\{1,x^2\}$.

$$
p(x)=(a_0,a_1,a_2,a_3)_{B_s}=(-a_0,a_1,-a_2,a_3)_{B_s}=-p(-x),
$$

nos da que las cartesianas de $W$ son $\left\{\begin{array}{l}
a_0=0,\\
a_2=0.
\end{array}\right.$  Y una base $\{x,x^3\}$.

Así que un sistema de generadores de $U+W$ es $\{1,x,x^2,x^3\}$ con lo que $U+W=\mathcal{P}_3(\mathbb{R})$, y además de que porque estos polinomios son linealmente independientes, se puede razonar con la fórmula de las dimensiones que $U\cap W=0$, con lo que se obtiene $\mathcal{P}_3(\mathbb{R})= U\oplus W$.
</li>

<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.

Es inmediato que 

$$
3x^3+x-2= (-2) + (x+3x^3)
$$

y el primer polinomio está en $U$ y el segundo en $W$.

::::
:::::