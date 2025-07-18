---
title: Espacio euclídeo
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

*Espacios vectoriales euclídeos. Productos escalares. Matriz de Gram respecto de una base.  Norma y ángulo. Bases ortogonales. Método de Gram-Schmidt. Subespacio ortogonal a uno dado. Coeficientes de Fourier. Proyección ortogonal de un vector sobre un subespacio. Teorema espectral. Diagonalización por semejanza ortogonal de matrices simétricas reales.*

<!--<input type="checkbox" id="casilla_cf" value="cfon" checked onclick="CF();"> Mostrar ejercicios sobre cuerpos finitos. -->

<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_basico" value="basicoon" checked onclick="mostrar();"> Básicos </button> 
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_medio" value="medioon" checked onclick="mostrar();"> Dificultad media </button>
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_avanzado" value="avanzadon" checked onclick="mostrar();"> Avanzados. </button>


::::: {#exr-1 .medio}

En $\mathbb{R}^4$ con el producto escalar usual se consideran los subespacios:

$$
U\equiv \left\{ \begin{aligned}
x+t&=0,\\
y+z&=0,\\
x-y-z+t&=0.
\end{aligned}\right. 
\qquad  W=\mathcal{L}((1,0,0,1),(0,0,1,-1)).
$$ 

<ol type="a">
<li>Calcula una base ortogonal de cada uno de ellos.</li>
<li>Prueba que $U$ y $W$ son complementarios, pero que $U^{\perp}\not = W$.</li>
<li>Para el vector $v=(1,-1,1,1)$ calcula $p_{U}(v)$ y $p_{U^{\perp}}(v)$.</li>
</ol>


:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular una base ortogonal.

Para calcular una base ortogonal de $U$ empezamos simplificando las ecuaciones cartesianas y obteniendo una base:

$$
U\equiv \left\{ \begin{array}{rl}
x+t&=0,\\
y+z&=0,\\
x-y-z+t&=0.
\end{array}\right. \sim_f U\equiv \left\{ \begin{array}{rl}
x+t&=0,\\
y+z&=0.\\
\end{array}\right.
$$ 

Podemos calcular una base usando como parámetros a $x$ e $y$: $\{ (1,0,0,-1),(0,1,-1,0)\}$; además esta base resulta ser ortogonal.

Para $W$ ya tenemos un sistema de generadores y observamos que son linealmente independientes; pero no son ortogonales, así que utilizamos el método de Gram-Schimdt partiendo de estos vectores:

$$
\begin{array}{l}
u_1=(1,0,0,1),\\
u_2=(0,0,1,-1),
\end{array}\hspace{1cm}
\begin{array}{l}
e_1=(1,0,0,1),\\
e_2=(0,0,1,-1)+\lambda_{2,1}(1,0,0,1).
\end{array}
$$

Calculamos 

$$
\lambda_{2,1}=-\frac{\langle(0,0,1,-1),(1,0,0,1)\rangle}{\langle(1,0,0,1),(1,0,0,1)\rangle}=-\frac{-1}{2}=\frac{1}{2}
$$

Así que la base ortogonal de $W$ que obtenemos es:

$$
\{(1,0,0,1),(1/2,0,1,-1/2)\}.
$$

</li>

<li>Probar que $U$ y $W$ son complementarios, pero que $U^{\perp}\not = W$.

Son complementarios si $U+W=\mathbb{R}^4$ y $U\cap W=\{ 0 \}$. Calculamos $U+W$ reuniendo bases:

$$
\begin{pmatrix}
1 & 0 & 1 & 0\\
0 & 1 & 0 & 0\\
0 & -1 & 0 & 1\\
-1 & 0 & 1 & -1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & -1 & 0 & 1\\
-1 & 0 & 2 & -1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & -1 & 0 & 1\\
0 & 0 & 1 & 0
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,0,1,0],[0,1,0,0],[0,-1,0,1],[-1,0,1,-1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

y obtenemos que $U+W=\mathbb{R}^4$ puesto que obtenemos la base canónica. Ahora usando la fórmula de las dimensiones

$$
\operatorname{dim}(U) + \operatorname{dim}(W) = \operatorname{dim}(U+W)+ \operatorname{dim}(U\cap W)
$$

obtenemos que $\operatorname{dim}(U\cap W)=0$ y por tanto $U\cap W=\{ 0 \}$.
Sin embargo, como $\langle (1,0,0,-1),(0,0,1,-1)\rangle =1$ y $(1,0,0,-1)\in U$ y $(0,0,1,-1)\in W$, entonces $W\not = U^{\perp}$.</li>

<li>Calcular $p_{U}(v)$ y $p_{U^{\perp}}(v)$.

De la base de $U$ obtenemos las cartesianas de $U^{\perp}$ que son:

$$
U^{\perp}\equiv \left\{ \begin{array}{rl}
x-t&=0,\\
y-z&=0.\\
\end{array}\right.
$$

Escribimos ahora $v=p_{U}(v)+p_{U^{\perp}}$ usando 4 incógnitas 

$$
(1,-1,1,1)=(\alpha, \beta, \gamma, \delta)+ (1-\alpha, -1-\beta,1-\gamma, 1-\delta)
$$ 

e imponemos las condiciones de que el primero cumpla las cartesianas de $U$ y el segundo las de $U^{\perp}$ y resolvemos:

$$
\begin{array}{r}
\alpha +\delta = 0,\\
-\alpha + \delta = 0,\\
\beta + \gamma = 0,\\
-1-\beta -1+ \gamma = 0,
\end{array}
$$

y resulta $\alpha= 0, \beta=-1, \gamma = 1, \delta= 0$, así que:

$$
p_U(1,-1,1,1)=(0,-1,1,0); \, \, p_{U^{\perp}}(1,-1,1,1)=(1,0,0,1).
$$ 

</li>
</ol>

::::
:::::

::::: {#exr-2 .basico}

En $\mathbb{R}^{3}$, dado el subespacio $U\equiv \left\{ \begin{array}{l}
x+y=0,\\
x+z=0.
\end{array}\right.$ y considerando el producto escalar usual, calcula $p_{U^{\perp}}(0,1,2)$. 


:::: {.callout collapse="true" title="Solución"}

Una base de $U$ es $\{(1,-1,-1)\}$ y por tanto $U^{\perp}\equiv x-y-z=0$, descomponemos

$$
(0,1,2)=(a,b,c)+(-a,1-b,2-c),
$$

e imponemos al primer vector que esté en $U$ y al segundo que esté en $W$:

$$
\left\{ \begin{array}{l}
a+b=0,\\
a+c=0,\\
-a-1+b-2+c=0.
\end{array}\right. \sim_f \left\{ \begin{array}{l}
b=-a,\\
c=-a,\\
-3a-3=0.
\end{array}\right. \sim_f \left\{ \begin{array}{l}
a=-1,\\
b=1,\\
c=1.
\end{array}\right. 
$$

Así $p_{U^{\perp}}(0,1,2)=(1,0,1)$.

::::
:::::


::::: {#exr-3 .medio}

Consideramos en $\mathbb{R}^{2}$ el producto escalar que tiene, respecto de la base canónica, matriz de Gram (o matriz métrica)
$\begin{pmatrix}
1 & 1 \\
1 & 2
\end{pmatrix}$. Calcula una base de $\mathbb{R}^{2}$ respecto de la cual la matriz de Gram de este producto escalar sea $I_2$.

:::: {.callout collapse="true" title="Solución"}

Que la matriz de Gram sea la identidad significa que la base es ortonormal. En primer lugar, aplicamos Gram-Schmidt para calcular una base ortogonal. Partimos por ejemplo de la base canónica:

$$
u_1=(1,0), u_2=(0,1).
$$

Entonces $e_1=(1,0)$ y $e_2=(0,1)+\lambda_{21}(1,0)$ donde 

$$
\lambda_{21}=-\frac{\langle u_2,e_1\rangle }{\langle e_1,e_1\rangle }=-\frac{1}{1}=-1,
$$

donde los datos se han recogido de la matriz de Gram respecto de $B_c$. 
Por tanto una base ortogonal es $\{(1,0),(-1,1)\}$, el primero tiene norma 1, calculamos la del segundo:

$$
\begin{pmatrix}
1 & 1
\end{pmatrix}\begin{pmatrix}
1 & 1 \\
1 & 2
\end{pmatrix}\begin{pmatrix}
-1\\
1
\end{pmatrix}=\begin{pmatrix}
0 & 1
\end{pmatrix} \begin{pmatrix}
-1\\
1
\end{pmatrix}=1.
$$

Así que esta base es ortonormal.

::::
:::::

::::: {#exr-4 .avanzado}

En el espacio vectorial $\mathcal{P}_3(\mathbb{R})$ de los polinomios de grado menor o igual que tres se considera  el subespacio $U$ generado por $x$ y $x^3$ y el producto escalar dado por:

$$
\langle p(x),q(x)\rangle = \int_{-1}^1 p(x)\cdot q(x) dx.
$$

<ol type="a">
<li>Determinar una base ortogonal de $U$.</li>
<li>Determinar una base de su complementario, $U^{\perp}$.</li>
<li>Determinar la proyección sobre $U$ del vector  $1+x$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Determinar una base ortogonal de $U$.

Como $\{ x, x^3\}$ es base, y $\langle x,x^3 \rangle =\int_{-1}^1 x^4dx= \left. x^5\right]_{-1}^1=2/5$
por lo que no es ortogonal. Usamos el algoritmo de Gram-Schmidt para calcular una:

$$
\begin{array}{lr}
e_1=x, & \\
e_2=x^3+\lambda_{21}x,& \lambda_{21}= \frac{- \langle x,x^3\rangle}{\langle x,x\rangle}.
\end{array}
$$

Calculamos $\langle x,x\rangle =\int_{-1}^1 x^2dx= \left. x^3\right]_{-1}^1=2/3$ luego
una base ortogonal de $U$ es $\{x,x^3-3/5x\}$.</li>

<li>Determinar una base de su complementario, $U^{\perp}$.

Podemos observar que $\langle 1,x\rangle =\langle 1,x^3\rangle =0$ y $\langle x^2,x\rangle =\langle x^2,x^3\rangle =0$ por lo que $\{1,x^2\}$ es una base de $U^{\perp}$, ya que este subespacio debe tener dimensión dos.</li>

<li>Determinar la proyección sobre $U$ del vector  $1+x$.

Puesto que tenemos bases sencillas de $U$ y de $U^{\perp}$ podemos expresar el polinomio dado como combinación lineal de todos ellos:

$$
1+x=\alpha_1\cdot x +  \alpha_2\cdot x^3 + \alpha_3\cdot 1 +\alpha_4\cdot x^2
$$

donde los dos primeros sumandos nos dan la proyección sobre $U$ y los dos últimos la proyección sobre $U^{\perp}$. Es inmediato que $\alpha_1=1$, $\alpha_2=0$, $\alpha_3=1$ y $\alpha_4=0$. Por tanto 

$$
p_U (1+x)=x.
$$

</li>
</ol>

::::
:::::


::::: {#exr-5 .medio}

En $\mathbb{R}^{3}$ se consideran el producto escalar cuya matriz de Gram respecto de la base canónica es 

$$
\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}
$$

y los subespacios $U=L((1,1,2),(2,1,1))$ y $W=L((1,a,1))$, siendo $a$ un parámetro.

<ol type="a">
<li>Determinar bases de $U+W$ y $U \cap W$ en función de $a$.</li>

<li>Calcular el complemento ortogonal de $U$.</li>

<li>Determinar la proyección sobre $U$ del vector $(5,-3,4)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar bases de $U+W$ y $U \cap W$ en función de $a$.

Los sistemas de generadores dados de $U$ y $W$ son bases, así que $\operatorname{dim}(U)=2$ y $\operatorname{dim}(W)=1$ para todos los valores de $a$. Un sistema de generadores de $U+W$ se obtiene al reuinir bases de ambos, comprobaremos para qué valores de $a$ son linealmente independientes:

$$
\left|\begin{array}{ccc}
1 & 2 & 1\\
1 & 1 & a\\
2 & 1 & 1
\end{array}\right|=\left|\begin{array}{ccc}
1 & 0 & 0\\
1 & -1 & a-1\\
2 & -3 & -1
\end{array}\right|=1+3(a-1)=3a-2.
$$

Si $a=2/3$ la dimensión de $U+W$ es dos y por tanto $U+W=U$, o lo que es lo mismo, $W\subset U$, así que una base es, por ejemplo, $\{ (1,1,2),(2,1,1)\}$, o también su base más sencilla que es $\{(1,0,-1),(0,1,3)\}$. Por tanto $U\cap W=W$ y una base es $\{(1,a,1)\}$. 


Si $a\not = 2/3$ entonces $\operatorname{dim}(U+W)=3$ y por tanto $U+W=\mathbb{R}^{3}$ y una base es la canónica. Por la fórmula de las dimensiones $\operatorname{dim}(U\cap W) + \operatorname{dim}(U+W)= d\operatorname{dim}(U) + \operatorname{dim}(W)$ y por tanto $U\cap W=\{0\}$ que no tiene base.
</li>

<li>Calcular el complemento ortogonal de $U$.

Por cada vector de la base de $U$ obtenemos una cartesiana de $U^{\perp}$ imponiendo que el producto escalar sea cero (usamos la base más sencilla, aunque sirve cualquier otra):

$$
(1,0,-1)\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}=0, \, \, \text{obteniendo   } \,  x+y-z=0;
$$

$$
(0,1,3)\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}=0, \, \, \text{obteniendo   } \,  x+2y+3z=0.
$$

Así que 

$$
U^{\perp}\equiv \left\{\begin{array}{r}
x+y-z=0,\\
x+2y+3z=0.
\end{array}\right. \sim \left\{\begin{array}{r}
x-5z=0,\\
y+4z=0.
\end{array}\right. 
$$

Y una base es $\{ (5,-4,1)\}$.
</li>

<li>Determinar la proyección sobre $U$ del vector $(5,-3,4)$.


Como sabemos una base (ortogonal, puesto que tiene un solo vector) de $U^{\perp}$ calculamos 

$$
p_{U^{\perp}}(5,-3,4)=\frac{\langle(5,-3,4)(5,-4,1)\rangle}{\langle(5,-4,1)(5,-4,1)\rangle}(5,-4,1)= \frac{18}{18}(5,-4,1)=(5,-4,1).
$$

Luego

$$
p_U(5,-3,4)=(5,-3,4)-p_{U^{\perp}}(5,-3,4)=(5,-3,4)-(5,-4,1)=(0,1,3).
$$

</li>
</ol>

::::
:::::

::::: {#exr-6 .medio}

En $\mathbb{R}^3$ consideramos el producto escalar que, respecto de la base canónica, tiene matriz de Gram

$$
G= \left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right).
$$

<ol type="a">
<li>Calcula una base ortogonal de este espacio vectorial.</li>

<li>Calcula $U^{\perp}$ para el subespacio

$$
U\equiv \left\{ \begin{array}{r}
 x+y+z=0,\\
 x-z=0.
\end{array}\right.
$$

</li>

<li>Calcula $p_U(1,1,1)$ y $p_{U^{\perp}}(1,1,1)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular una base ortogonal de este espacio vectorial.

Partimos de la base canónica de $\mathbb{R}^{3}$ y aplicamos Gram-Schmidt: $\{u_1=(1,0,0), u_2=(0,1,0),  u_3=(0,0,1)\}$,

$$
e_1=u_1=(1,0,0),
$$

$e_2=u_2+\lambda_{21}e_1,$ necesitamos calcular

$$
\lambda_{21}=\frac{-\langle u_2,e_1\rangle}{\langle e_1,e_1\rangle}=\frac{-1}{1}=-1,
$$

puesto que tanto numerador como denominador aparecen en la matriz de Gram. Así

$$
e_2=(0,1,0)-(1,0,0)=(-1,1,0),
$$

ahora
$e_3=u_3+\lambda_{31}e_1+\lambda_{32}e_2$, y de nuevo numerador y denominador de $\lambda_{31}$ aparecen en la matriz de Gram:

$$
\lambda_{31}=\frac{-\langle u_3,e_1\rangle}{\langle e_1,e_1\rangle}=\frac{-1}{1}=-1,
$$

pero los de $\lambda_{32}$ deben ser calculados:

$$
\langle u_3,e_2\rangle(0\, 0\, 1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
-1 \\
1\\
0
\end{array}\right)=-1,
$$

$$
\langle e_2,e_2\rangle(-1\, 1\, 0)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
-1 \\
1\\
0
\end{array}\right)=2,
$$

luego $\lambda_{32}=1/2$ y por tanto

$$
e_3=(0,0,1)-(1,0,0)+1/2(-1,1,0)=(-3/2,1/2,1).
$$

Luego una base ortogonal es

$$
\{(1,0,0),(-1,1,0),(-3/2,1/2,1)\}.
$$

</li>

<li>Calcular $U^{\perp}$. 

Calculamos en primer lugar una base de $U$, como $\operatorname{dim}(U)=3- \text{nº cartesianas}=1$ basta encontrar un vector que cumpla las cartesianas: $\{u=(1,-2,1)\}$.
Ahora imponemos la condición $\langle(1,-2,1),(x,y,z)\rangle=0$ que nos da la ecuación cartesiana de $U^{\perp}$:

$$
(1\, -2\,\,  1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
x \\
y\\
z
\end{array}\right)=-5y+3z=0.
$$
</li>

<li>Calcula $p_U(1,1,1)$ y $p_{U^{\perp}}(1,1,1)$.

Podemos usar la base ortogonal de $U$: $\{(1,-2,1)\}$ (que lo es por tener un solo vector) y la fórmula de los coeficientes de Fourier:

$$
p_U(1,1,1)=\frac{\langle(1,1,1),(1,-2,1)\rangle}{\langle(1,-2,1),(1,-2,1)\rangle}(1,-2,1).
$$

Calculamos los dos productos escalares y obtenemos

$$
(1\, -2\,\,  1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r|r}
1 & 1\\
1 & -2\\
1 & 1
\end{array}\right)=(-2|13),
$$

$$
p_U(1,1,1)=\frac{-2}{13}(1,-2,1)=(-2/13, 4/13, -2/13),
$$

$$
p_{U^{\perp}}(1,1,1)=(1,1,1)-(-2/13, 4/13, -2/13)=(15/13, 9/13, 15/13).
$$

</li>
</ol>

::::
:::::

::::: {#exr-7 .avanzado}

En $\mathcal{P}_2(\mathbb{R})$ consideramos el producto escalar dado por 

$$
\langle p(x),q(x)\rangle=\int_0^1 p(x)q(x)dx.
$$

<ol type="a">
<li>Calcula la matriz de Gram respecto de la base $\{1, 1-x, x^2\}$.</li>

<li>Calcula una base de $U=\{p(x)\in \mathcal{P}_2(\mathbb{R}) \text{ tal que } p(1)=p'(1)=0\}$.</li>

<li>Calcula las ecuaciones cartesianas del subespacio  $U^{\perp}$.</li>

<li>Calcula $p_U(1-2x^2)$ y $p_{U^{\perp}}(1-2x^2)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular la matriz de Gram respecto de la base $\{1, 1-x, x^2\}$.

$$
\langle 1,1\rangle=\int_0^1 1\cdot 1dx=\left. x \right]_0^1=1,

$$

$$
\langle 1,1-x\rangle=\int_0^1 1\cdot (1-x)dx=x-\left. \dfrac{1}{2}x^2\right]_0^1=\dfrac{1}{2},
$$

$$
\langle 1,x^2\rangle=\int_0^1 1\cdot x^2dx=\left. \dfrac{1}{3}x^3\right]_0^1=\dfrac{1}{3},
$$

$$
\langle 1-x,1-x\rangle=\int_0^1 (1-x)^2dx=\left. \dfrac{1}{3}(x-1)^3\right]_0^1=\dfrac{1}{3},
$$

$$
\langle 1-x,x^2\rangle=\int_0^1 (x^2-x^3)dx=\dfrac{1}{3}x^3-\left. \dfrac{1}{4}x^4\right]_0^1=\dfrac{1}{12},
$$

$$
\langle x^2,x^2\rangle=\int_0^1 x^4dx=\left. \dfrac{1}{5}x^5\right]_0^1=\dfrac{1}{5},
$$

$$
G_B=\left(
\begin{array}{ccc}
  1 & \frac{1}{2} & \frac{1}{3} \\
  \frac{1}{2} & \frac{1}{3} & \frac{1}{12} \\
  \frac{1}{3} & \frac{1}{12} & \frac{1}{5}\\
\end{array}\right).
$$

</li>

<li>Calcular una base de $U$.

$$
p(x)=a_0+a_1x+a_2x^2=(a_0,a_1,a_2)_{B_S} \Rightarrow p(1)=a_0+a_1+a_2=0.
$$

Por otro lado, $$p'(x)=a_1+2a_2x \Rightarrow p'(1)=a_1+2a_2=0.$$

Luego unas ecuaciones cartesianas son $U\equiv \left\{\begin{array}{l} a_0+a_1+a_2=0, \\ a_1+2a_2=0. \end{array}\right.$

Resolviendo, $$\left\{\begin{array}{l} a_1=-2a_2, \\ a_0-2a_2+a_2=0. \end{array}\right.\Rightarrow \left\{ \begin{array}{l} a_0=\lambda, \\ a_1=-2\lambda,\\ a_2=\lambda. \end{array} \right.$$
Por lo tanto, una base de $U$ es $\{(1,-2,1)_{B_{S}}\}=\{1-2x+x^2\}$. 
</li>

<li>Calcula las ecuaciones cartesianas del subespacio  $U^{\perp}$.

Para usar la matriz de Gram para calcular el producto escalar, será necesario calcular la matriz de Gram con respecto a la base estándar, que no es la del apartado a). Algunos de los cálculos sí sirven: 

$$
\langle 1,1\rangle=1,
$$

$$
\langle 1,x\rangle=\int_0^1 1\cdot (x)dx=\left. \dfrac{1}{2}x^2\right]_0^1=\dfrac{1}{2},
$$

$$
\langle 1,x^2\rangle=\dfrac{1}{3},
$$

$$
\langle x,x\rangle=\int_0^1 x^2dx=\left. \dfrac{1}{3}x^3\right]_0^1=\dfrac{1}{3},
$$

$$
\langle x,x^2\rangle=\int_0^1 x^3dx=\left. \dfrac{1}{4}x^4\right]_0^1=\dfrac{1}{4},
$$

$$
\langle x^2,x^2\rangle=\dfrac{1}{5},
$$

$$
G_{B_{S}}=\left(
\begin{array}{ccc}
1 & \frac{1}{2} & \frac{1}{3} \\
\frac{1}{2} & \frac{1}{3} & \frac{1}{4} \\
\frac{1}{3} & \frac{1}{4} & \frac{1}{5}\\
\end{array}
\right).
$$

Ahora imponemos la condición  

$$
\langle(1,-2,1)_{B_{S}}, (a_0, a_1,a_2)\rangle=0,
$$

$$
(1,-2,1)\left(
\begin{array}{ccc}
1 & \frac{1}{2} & \frac{1}{3} \\
\frac{1}{2} & \frac{1}{3} & \frac{1}{4} \\
\frac{1}{3} & \frac{1}{4} & \frac{1}{5}\\
\end{array}
\right) \left(
\begin{array}{c}
a_0 \\
a_1 \\
a_2 \\
\end{array}
\right)=0. 
$$          

Luego unas cartesianas son $\dfrac{1}{3}a_0+\dfrac{1}{12}a_1+\dfrac{1}{30}a_2=0$, o bien   
$U^{\perp}\equiv a_0+\dfrac{1}{4}a_1+\dfrac{1}{10}a_2=0$.
</li>

<li>Calcula $p_U(1-2x^2)$ y $p_{U^{\perp}}(1-2x^2)$.

Como $\operatorname{dim}(U)=1$  es rápido calcular $p_U(1-2x^2)$ usando coeficientes de Fourier. Puesto que $\{ (1,-2,1)_{B_S} \}$ es un base ortogonal de $U$.

$$
p_U((1,0,-2)_{B_S})=\dfrac{\langle(1,0,-2)_{B_S},(1,-2,1)_{B_S}\rangle}{\langle(1,-2,1)_{B_S},(1,-2,1)_{B_S}\rangle} (1,-2,1)_{B_S}.
$$

Calculamos  

$$
(1,-2,1)\left(
\begin{array}{ccc}
1 & \frac{1}{2} & \frac{1}{3} \\
\frac{1}{2} & \frac{1}{3} & \frac{1}{4} \\
\frac{1}{3} & \frac{1}{4} & \frac{1}{5}\\
\end{array}
\right) \left(
\begin{array}{c}
1 \\
-2 \\
1 \\
\end{array}
\right)=\dfrac{1}{5}; (1,-2,1)\left(
\begin{array}{ccc}
1 & \frac{1}{2} & \frac{1}{3} \\
\frac{1}{2} & \frac{1}{3} & \frac{1}{4} \\
\frac{1}{3} & \frac{1}{4} & \frac{1}{5}\\
\end{array}
\right) \left(
\begin{array}{c}
1 \\
0 \\
2 \\
\end{array}
\right)=\dfrac{4}{15}.
$$

Luego 

$$
p_U((1,0,-2)_{B_S})=\dfrac{\frac{1}{4}}{\frac{1}{5}}(1,-2,1)_{B_S}=\dfrac{20}{15}(1,-2,1)_{B_S}=(\dfrac{4}{3},\dfrac{-8}{3},\dfrac{4}{3})_{B_S},$$ y por lo tanto $$p_{U^{\perp}}((1,0,-2)_{B_S})=(1,0,-2)_{B_S}-(\dfrac{4}{3},\dfrac{-8}{3},\dfrac{4}{3})_{B_S}= (-\dfrac{1}{3},\dfrac{8}{3},\dfrac{-10}{3})_{B_S}.
$$

Podemos comprobar el resultado:

$$
\dfrac{-1}{3}+\dfrac{1}{4}\cdot\dfrac{8}{3}+\dfrac{1}{10}\cdot\dfrac{-10}{3}=-\dfrac{1}{3}+\dfrac{2}{3}-\dfrac{1}{3}=0.
$$

</li>
</ol>

::::
:::::


::::: {#exr-8 .avanzado}

En $\mathcal{P}_3(\mathbb{R})$ se consideran los subespacios vectoriales:

$$
U=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=p(x) \}, W=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=-p(x) \}.
$$

<ol type="a">
<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.</li>
<li>Para el producto escalar dado por 

$$
\langle p(x),q(x)\rangle= \int_{-1} ^1 p(x)q(x)dx.
$$

calcular una base ortogonal de $U$.</li>

<li>Con el mismo producto escalar, calcular $W^{\perp}$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Para el producto escalar dado calcular una base ortogonal de $U$.

Partimos de la base de $U$ obtenida $\{1,x^2\}$ y aplicamos Gram-Schimdt:

$$
e_1=1,
$$

$$
e_2=x^2-\frac{\langle 1,x^2\rangle}{\langle 1,1\rangle}\cdot 1.
$$

Calculamos
$\langle 1,1\rangle=\int_{-1} ^1 1\cdot 1 dx =  2,$ 
$\langle 1,x^2\rangle=\int_{-1} ^1 x^2dx = \frac{2}{3}.$
Así 
$e_2= x^2-\frac{1}{3}$  y la base ortogonal de $U$ obtenida es $\{1, x^2-\frac{1}{3}\}$.
</li>

<li>Calcular $W^{\perp}$.

Dada la base de $W$, $\{x,x^3\}$ observamos que 
$$
\langle x,1\rangle=\int_{-1} ^1 x\cdot 1 dx = 0,
$$

$$
\langle x,x^2\rangle=\int_{-1} ^1 x\cdot x^2 dx = 0,
$$

$$
\langle x^3,1\rangle=\int_{-1} ^1 x^3\cdot 1 dx = 0,
$$

$$
\langle x^3,x^2\rangle=\int_{-1} ^1 x^3\cdot x^2 dx = 0.
$$

Así que $U=\mathcal{L}(1,x^2)$ es el subespacio ortogonal a $W$.
</li>
</ol>

::::
:::::


::::: {#exr-9 .avanzado}

En el espacio $\mathcal{P}_3(\mathbb{R})$ de los polinomios de grado menor o igual que tres, se consideran los subespacios

$$
P=\{ p(x)\in \mathcal{P}_3(\mathbb{R}) |\,  p(x)=p(-x) \}
$$

$$
I=\{ p(x)\in \mathcal{P}_3(\mathbb{R}) |\, p(x)=-p(-x) \}
$$
y el producto escalar

$$
\langle p(x),q(x)\rangle = \int_{-1}^{1} p(x)q(x)dx. 
$$

<ol type="a">

<li>Calcular bases de $P$ e $I$ y comprobar que $I$ y $P$ son complementarios.</li>

<li>Calcular  bases ortogonales de $P$ y de $I$.</li>

<li>¿Es $P$ el complemento ortogonal de $I$ respecto de este producto escalar?</li>

<li>Escribir la fórmula para calcular la proyección ortogonal de un polinomio genérico $p(x)=a_0 +a_1 x+a_2 x^2 +a_3 x^3$ sobre $P$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Calcular bases de $P$ e $I$ y comprobar que $I$ y $P$ son complementarios.

Para calcular la base de $P$ escribimos la condición $p(x)=p(-x)$ sobre un polinomio genérico, $p(x)=a_0+a_1 x+a_2 x^2 +a_3 x^3$:

$$
a_0+a_1 x+a_2 x^2 +a_3 x^3=a_0-a_1 x+a_2 x^2 -a_3 x^3,
$$

y nos queda $2a_1 x+ 2a_3x^3=0$, por tanto, para que este polinomio sea cero, deben ser cero ambos coeficientes:

$$
a_1=0,\\
a_3=0,
$$

que son las ecuaciones cartesianas del subespacio. Una base será $\{1,x^2\}$, o bien, utilizando coordenadas respecto 
de la base estándar $\{1,x,x^2,x^3\}$, $\{(1,0,0,0),(0,0,1,0)\}$.

De la misma forma para calcular la base de $I$ escribimos la condición $p(x)=-p(-x)$ sobre un polinomio genérico, $p(x)=a_0+a_1 x+a_2 x^2 +a_3 x^3$:

$$
a_0+a_1 x+a_2 x^2 +a_3 x^3=-(a_0-a_1 x+a_2 x^2 -a_3 x^3), 
$$

y nos queda $2a_0 + 2a_2x^2=0$, por tanto, para que este polinomio sea cero, deben ser cero ambos coeficientes:

$$
a_0=0,\\
a_2=0,
$$

que son las ecuaciones cartesianas del subespacio. Una base será $\{x,x^3\}$, o bien, utilizando coordenadas respecto 
de la base estándar $\{1,x,x^2,x^3\}$, $\{(0,1,0,0),(0,0,0,1)\}$.
</li>

<li>Calcular  bases ortogonales de $P$ y de $I$.

Utilizando el método de Gram-Schmidt en ambos casos, sólo es necesario el cálculo de un vector.

Comenzamos con $P$:

$$
p_1(x)=1,\\
p_2 (x)= x^2 +\lambda \cdot 1,
$$

Calculamos el valor de $\lambda$ para que $\langle p_1(x),p_2(x)\rangle=0$:

$$
0= \int_{-1}^{1} p_1(x)p_2(x)dx = \int_{-1}^{1} 1\cdot(x^2+\lambda )dx = \left. \frac{x^3}{3}+ \lambda x \right]_{-1}^{1} = 
(1/3 +\lambda )-(-1/3-\lambda),
$$

y nos queda  $ 2(1/3 + \lambda)=0$ con lo que $\lambda = -1/3$. Así una base ortogonal de $P$ es $\{1, x^2-1/3 \}$.

Ahora para  $I$:

$$
p_1(x)=x,\\
p_2 (x)= x^3 +\lambda \cdot 1.
$$

Calculamos el valor de $\lambda$ para que $\langle p_1(x),p_2(x)\rangle=0$:

$$
0= \int_{-1}^{1} p_1(x)p_2(x)dx = \int_{-1}^{1} x\cdot(x^3+\lambda x )dx = \left. \frac{x^5}{5}+ \lambda \frac{x^3}{3} \right]_{-1}^{1} = 
(1/5 + (1/3)\lambda )-(-(1/5)-(1/3)\lambda),
$$

y nos queda $ 2(1/5 + (1/3)\lambda)=0$ con lo que $\lambda = -5/3$.Así una base ortogonal de $I$ es $\{x, x^3-(5/3)x \}$.
</li>

<li>¿Es $P$ el complemento ortogonal de $I$ respecto de este producto escalar?

Sólo es necesario comprobar que cada uno de los vectores de una base de $P$ es ortogonal con todos los de una base de $I$.

Usamos las bases calculadas en el apartado a):

$$
\langle 1,x\rangle=\int_{-1}^{1} 1\cdot x dx =  \left. \frac{x^2}{2}\right]_{-1}^{1}=0
$$

$$
\langle 1,x^3\rangle=\int_{-1}^{1} 1\cdot x^3 dx =  \left. \frac{x^4}{4}\right]_{-1}^{1}=0
$$

$$
\langle x^2,x\rangle=\int_{-1}^{1} x^2\cdot x dx =  \left. \frac{x^4}{4}\right]_{-1}^{1}=0
$$

$$
\langle x^2,x^3\rangle=\int_{-1}^{1} x^2\cdot x^3 dx =  \left. \frac{x^6}{6}\right]_{-1}^{1}=0
$$

</li>
<li>Escribir la fórmula para calcular la proyección ortogonal de un polinomio genérico $p(x)=a_0 +a_1 x+a_2 x^2 +a_3 x^3$ sobre $P$.

Pueden usarse las cartesianas de $P$ y de su ortogonal que es $I$ para descomponer el vector genérico

$$
(a_0,a_1,a_2,a_3)=(a,b,c,d)+(a_0 -a,a_1 -b, a_2 -c, a_3 -d).
$$

Como el primer vector debe estar en $P$ se tiene $b=0$ y $d=0$. Como el segundo sumando debe estar en $I$ entonces $a_0-a=0$ y $a_2-c=0$.
Entonces se tiene que la proyección sobre $P$ es $(a_0,0,a_2,0)$ o bien $a_0+a_2x^2$.
</li>
</ol>

::::
:::::

::::: {#exr-10 .medio}

En $\mathbb{R}^{4}$ con el producto escalar usual se considera el subespacio

$$
U= \mathcal{L} ((1,1,0,1)),
$$

<ol type="a">
<li>Calcula la proyección ortogonal sobre $U$ de cada uno de los vectores de la base canónica.</li>

<li>Calcula la proyección ortogonal sobre $U^{\perp}$ de cada uno de los vectores de la base canónica.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular la proyección ortogonal sobre $U$ de cada uno de los vectores de la base canónica.

Como $U$ tiene dimensión 1, es fácil calcular la proyección usando los coeficientes de Fourier:

$$
\begin{align*}
p_U (1,0,0,0)&=\frac{\langle(1,0,0,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3),\\
p_U (0,1,0,0)&=\frac{\langle(0,1,0,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3),\\
p_U (0,0,1,0)&=\frac{\langle(0,0,1,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=(0,0,0,0),\\
p_U (0,0,0,1)&=\frac{\langle(0,0,0,1),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3).\\
\end{align*}
$$

</li>

<li>Calcular la proyección ortogonal sobre $U^{\perp}$ de cada uno de los vectores de la base canónica.

$p_{U^{\perp}} (v)=v-p_U (v)$

$$
\begin{align*}
p_{U^{\perp}}(1,0,0,0)&=(1,0,0,0)-(1/3,1/3,0,1/3)=(2/3, -1/3,0, -1/3),\\
p_{U^{\perp}}(0,1,0,0)&=(0,1,0,0)-(1/3,1/3,0,1/3)=(-1/3, 2/3,0, -1/3),\\
p_{U^{\perp}}(0,0,1,0)&=(0,0,1,0)-(0,0,0,0)=(0,0,1,0),\\
p_{U^{\perp}}(0,0,0,1)&=(0,0,0,1)-(1/3,1/3,0,1/3)=(-1/3, -1/3,0, 2/3).\\
\end{align*}
$$

</li>
</ol>

::::
:::::

::::: {#exr-11 .basico}

Para el producto escalar en $\mathcal{P}^2(\mathbb{R})$ dado por 
$$
\langle p(x),q(x)\rangle =p(-2)q(-2)+p(0)q(0)+p(2)q(2)
$$

calcula la matriz de Gram respecto de la base $B=\{1,x,x^2\}$.


:::: {.callout collapse="true" title="Solución"}

La matriz de Gram contiene todos los productos de todos los vectores de la base dos a dos. Por ejemplo en la posición 11 está $\langle 1,1\rangle =1\cdot 1+1\cdot 1+1\cdot 1=3$, en la 12
$\langle 1,x\rangle =1\cdot (-2)+1\cdot 0+ 1\cdot 2=0$ y así hasta obtener todos los productos (solo hay que calcular 6 por ser la matriz de Gram simétrica)

$$
G=\left(\begin{array}{rrr}
3 & 0 & 8\\
0 & 8 & 0\\
8 & 0 & 32
\end{array}\right)
$$

::::
:::::

::::: {#exr-12 .basico}

Calcula la matriz de Gram del producto escalar en el espacio de las matrices simétricas de orden 2 dado por la fórmula:
$$
\langle A,B\rangle =traza(AB)
$$

respecto de la base $B= \left\{ \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}; \begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix};\begin{pmatrix}
0 & 0 \\
0 & 1
\end{pmatrix}\right\}$. 

:::: {.callout collapse="true" title="Solución"}

Para obtener la matriz de Gram calculamos el producto de cada dos matrices de la base:

$$\biggl \langle  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} ,\begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\biggr\rangle =traza\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\right)=traza\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} \right)=1
$$

$$
\biggl\langle  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} ,\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}\biggr\rangle =traza\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}\right)=traza\left(  \begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix} \right)=0
$$

del mismo modo se calculan los productos restantes y se obtiene

$$
G=\begin{pmatrix}
1 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 1\end{pmatrix}
$$

::::
:::::

::::: {#exr-13 .medio}

Consideramos en $\mathbb{R}^{2}$ el producto escalar que tiene, respecto de la base canónica, matriz de Gram (o matriz métrica)
$\begin{pmatrix}
1 & 1 \\
1 & 2
\end{pmatrix}$. Calcula una base de $\mathbb{R}^{2}$ respecto de la cual la matriz de Gram de este producto escalar sea $I_2$.

:::: {.callout collapse="true" title="Solución"}

Que la matriz de Gram sea la identidad significa que la base sea {\bf ortonormal}. En primer lugar aplicamos Gram-Schmidt para calcular una base ortogonal; partimos por ejemplo de la base canónica:
$$u_1=(1,0); u_2=(0,1)$$
Entonces $e_1=(1,0)$ y $e_2=(0,1)+\lambda_{21}(1,0)$ donde 

$\lambda_{21}= \frac{\langle u_2,e_1 \rangle}{\langle e_1,e_1\rangle}  =- \frac{1}{1} =-1$

donde los datos se han recogido de la matriz de Gram respecto de $B_c$. 
Por tanto una base ortogonal es $\{(1,0),(-1,1)\}$, el primero tiene norma 1, calculamos la del segundo:

$$
\begin{pmatrix}
1 & 1
\end{pmatrix}\begin{pmatrix}
1 & 1 \\
1 & 2
\end{pmatrix}\begin{pmatrix}
-1\\
1
\end{pmatrix}=\begin{pmatrix}
0 & 1
\end{pmatrix} \begin{pmatrix}
-1\\
1
\end{pmatrix}=1
$$

Así que esta base es ortonormal.

::::
:::::

::::: {#exr-14 .basico}

En $\mathbb{R}^{3}$, dado el subespacio $U\equiv \left\{ \begin{array}{l}
x+y=0\\
x+z=0
\end{array}\right.$ y considerando el producto escalar usual, calcula $p_{U^{\perp}}(0,1,2)$. 

:::: {.callout collapse="true" title="Solución"}

Una base de $U$ es $\{(1,-1,-1)\}$ y por tanto $U^{\perp}\equiv x-y-z=0$, descomponemos
$$
(0,1,2)=(a,b,c)+(-a,1-b,2-c)
$$

e imponemos al primer vector que esté en $U$ y al segundo que esté en $W$:

$$
\left\{ \begin{array}{l}
a+b=0\\
a+c=0\\
-a-1+b-2+c=0
\end{array}\right. \sim_f \left\{ \begin{array}{l}
b=-a\\
c=-a\\
-3a-3=0
\end{array}\right. \sim_f \left\{ \begin{array}{l}
a=-1\\
b=1\\
c=1
\end{array}\right. 
$$

luego $p_{U^{\perp}}(0,1,2)=(1,0,1)$.

::::
:::::

::::: {#exr-15 .medio}

Calcular una base ortogonal de $\mathbb{R}^2$ para el producto escalar que, respecto de la base canónica, tiene como matriz de Gram 
$$
G= \begin{pmatrix}
2 & -1 \\
-1 & 2
\end{pmatrix}
$$

:::: {.callout collapse="true" title="Solución"}

Partimos de la base canónica $B_c= \{ v_1=(1,0),(0,1)\}$ y aplicamos Gram-Schmidt:
$$
\begin{array}{l}
u_1=v_1=(1,0)\\
u_2=v_2+\lambda_{21} u_1=(0,1)+\lambda_{21}(1,0)\\
\end{array}
$$

Calulamos $\lambda_{21}$ usando la matriz de Gram dada:

$$
\lambda_{21}=-\frac{\langle (1,0),(0,1)\rangle }{\langle (1,0),(1,0)\rangle } = -(-1/2) =1/2
$$

y obtenemos
$$
\begin{array}{l}
u_2=(0,1)+\frac{1}{2}(1,0)=(\frac{1}{2},1)\\
\end{array}
$$

Luego una base ortogonal es $\{(1,0),(\frac{1}{2},1)\}$.

::::
:::::

::::: {#exr-16 .basico}

En $\mathbb{R}^4$ con el producto escalar usual se consideran los subespacios 

$$
U\equiv x+y+z=0\; \mbox{ y } W\equiv \left\{ \begin{array}{l} 
x=0\\
y-z=0
\end{array}\right.
$$

<ol type="a">
<li>Calcula unas cartesianas de los subespacios $U^{\perp}$ y $W^{\perp}$. </li>

<li>Calcula una base ortogonal de $U$. </li>

<li>Calcula $p_U(0,0,1,1)$ y $p_W(0,0,1,1)$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Puesto que el producto escalar es el usual, de las ecuaciones cartesianas obtenemos directamente  bases de los subespacios ortogonales cuyos vectores son los coeficientes de cada ecuación:

Base de $U^{\perp}=\{(1,1,1,0)\}$ 

Base de $W^{\perp}=\{ (1,0,0,0),(0,1,-1,0)\}$.

Pero también podemos proceder de este otro modo (que es general y puede usarse con cualquier producto escalar): 
<ul>
<li> calcular una base de $U$:

como $dim\, U= 4-\mbox{nº cart.}=4-1=3$, así que una base está formada por 3 soluciones de la ecuación (en $\mathbb{R}^4$, por tanto hay 4 incógnitas) que sean linealmente independientes, por ejemplo:
$$
\{(1,-1,0,0),(1,0,-1,0),(0,0,0,1)\}
$$

Para calcular la base más sencilla reducimos por columnas la matriz que forman estos vectores:
$$\left(\begin{array}{rrr}
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
</li>
<li> para cada uno de los vectores de una base de $U$ imponemos la condición:  
$\langle u,\overrightarrow{x}\rangle =0$ y así obtenemos las cartesianas de $U^{\perp}$: para $u_1=(1,0,-1,0)$  se obtiene $x-z=0$;

para $u_2=(0,1,-1,0)$  el resultado es  $y-z=0$;
y para $u_3=(0,0,0,1)$ aparece $t=0$.
Por tanto 

$$
U^{\perp} \equiv \left\{ \begin{array}{l} 
x-z=0\\
y-z=0\\
t=0
\end{array}\right. 
$$

Procediendo del mismo modo para $W$ obtenemos
$$
W^{\perp} \equiv \left\{ \begin{array}{l} 
y+z=0\\
t=0
\end{array}\right. 
$$
</li></ul>
</li>

<li>
Partimos de la base más sencilla (aunque se puede hacer desde una base cualquiera de $U$) y aplicamos Gram-Schmidt:
$$
\{u_1=(1,0,-1,0),u_2=(0,1,-1,0),u_3=(0,0,0,1)\}
$$

$e_1=(1,0,-1,0)$
 
$e_2=(0,1,-1,0)+\lambda_{21}(1,0,-1,0)=(0,1,-1,0)-\frac{1}{2}(1,0,-1,0)=(-1/2,1,-1/2,0)$

donde hemos calculado 

$$ 
\lambda_{21}= \frac{-\langle (0,1,-1,0),(1,0,-1,0)\rangle }{\langle (1,0,-1,0),(1,0,-1,0)\rangle }=\frac{-1}{2}
$$


Por último como $\langle (u_3,e_1\rangle =0$ y $\langle u_3,e_2\rangle =0$ entonces 
$e_3=(0,0,0,1)$. 
Una base ortogonal de $U$ es
$$  
\{(1,0,-1,0),(-1/2,1,-1/2,0),(0,0,0,1)\}
$$
</li>

<li>
$p_U(0,0,1,1)=(0,0,1,1)-p_{U^{\perp}}(0,0,1,1)$ puesto que $dim \, U^{\perp}=1$ y por tanto una base ortogonal de $U^{\perp}$ es $\{(1,1,1,0)\}$. Usando coeficientes de Fourier:

$$
p_{U^{\perp}}(0,0,1,1)=\frac{\langle (0,0,1,1),(1,1,1,0)\rangle }{\langle (1,1,1,0),(1,1,1,0)\rangle }(1,1,1,0)=\frac{1}{3}(1,1,1,0)
$$

por tanto 
$$
p_U(0,0,1,1)=(-1/3,-1/3,2/3,1)
$$

Usaremos cartesianas de $W$ y de $W^{\perp}$ para calcular 
$$
p_W (0,0,1,1)=(\alpha,\beta, \gamma,\delta)+(-\alpha,-\beta, 1-\gamma,1-\delta)
$$
imponemos que el primer vector esté en $W$ y que el segundo esté en $W^{\perp}$ y resolvemos el sistema:
$$
\left. \begin{array}{l}
\alpha=0\\
\beta- \gamma=0\\ 
-\beta+1-\gamma=0\\
1-\delta=0
\end{array}\right\} \sim_f \left. \begin{array}{l}
\alpha=0\\
\beta=1/2\\ 
\gamma=1/2\\
\delta=1
\end{array}\right\}
$$

luego $p_W(0,0,1,1)=(0,1/2,1/2,1)$.
</li>
</ol>

::::
:::::

::::: {#exr-17 .avanzado}

En $\mathbb{R}^3$ se considera el producto escalar dado por la fórmula:

$$
\langle(x_1,x_2,x_3),(y_1,y_2,y_3)\rangle = 
2x_1y_1-x_1y_2-x_1y_3-x_2y_1+2x_2y_2+x_2y_3-x_3y_1+x_3y_2+1x_3y_3
$$

<ol type="a">

<li>Calcula el coseno  del  ángulo entre los vectores $(1,0,0)$ y $(0,1,0)$. </li>
<li>Determina la matriz de Gram de este producto escalar respecto de la base canónica de $\mathbb{R}^3$. </li>
<li>Encuentra una base ortonormal de este espacio vectorial euclídeo. </li>
<li>Dado el subespacio $U\equiv \left\{ \begin{array}{c} x=0\\ y=0 \end{array}\right.$ determina $U^{\perp}$. </li>
<li>Calcula la proyección del vector $v=(1,0,0)$ sobre $U$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>

$$
cos\, \alpha =\frac{\langle (1,0,0),(0,1,0)\rangle }{||(1,0,0)||\cdot ||(0,1,0)||}=\frac{-1}{\sqrt{2}\sqrt{2}}=-1/2
$$

(estos productos escalares pueden calcularse directamente usando la fórmula proporcionada o bien después del apartado b)
</li>
<li>

$$
G=\left(\begin{array}{rrr}
2 & -1 & -1\\
-1& 2 & 1\\
-1 & 1 & 1
\end{array}\right)
$$
</li>
<li>
Puesto que la matriz de Gram respecto de $B_c$ no es la identidad, $B_c$ no es una base ortonormal, así que empleamos el método de Gram-Schmidt partiendo de $B_c$ para calcular una base ortogonal.

$e_1=(1,0,0)$

$e_2=(0,1,0)+\lambda_{21}(1,0,0)$ y calculamos  

$$
\lambda_{21}
=-\frac{ \langle (0,1,0),(1,0,0)\rangle  }{ \langle (1,0,0),(1,0,0)\rangle  } = - \frac{-1}{2}=\frac{1}{2}
$$

por tanto

$e_2=(1/2,1,0)$

$e_3=(0,0,1)+\lambda_{31}(1,0,0)+\lambda_{32}(1/2,1,0) =(1/3. -1/3,1)$

$$
\lambda_{31}
=-\frac{ \langle (0,0,1),(1,0,0)\rangle  }{ \langle (1,0,0),(1,0,0)\rangle } = 
-\frac{-1}{2}=\frac{1}{2}
$$

$$
\lambda_{32}
=-\frac{\langle (0,0,1),(1/2,1,0)\rangle }{\langle (1/2,1,0),(1/2,1,0)\rangle }=-\frac{1/2}{3/2}=-\frac{1}{3}
$$

Todos estos productos escalares se han calculado usando la matriz de Gram, por ejemplo:

$$
\langle (1/2,1,0),(1/2,1,0)\rangle =\begin{pmatrix}
1/2 & 1 & 0 
\end{pmatrix}\left(\begin{array}{rrr}
2 & -1 & -1\\
-1& 2 & 1\\
-1 & 1 & 1
\end{array}\right)\begin{pmatrix}
1/2\\
1\\
0
\end{pmatrix}= \begin{pmatrix}
0 & 3/2 & 1/2\\
\end{pmatrix}\begin{pmatrix}
1/2\\
1\\
0
\end{pmatrix}=3/2
$$

Una vez obtenida esta base ortogonal dividiendo cada vector por su norma tendremos la base ortonormal.
Tenemos calculadas $||e_1||=\sqrt{2}; ||e_2||=\sqrt{3/2}$ y calculamos $||e_3||$:

$$
||(1/3,-1/3,1)||^2=\begin{pmatrix}
1/3 & -1/3 & 1 
\end{pmatrix}\left(\begin{array}{rrr}
2 & -1 & -1\\
-1& 2 & 1\\
-1 & 1 & 1
\end{array}\right)\begin{pmatrix}
1/3\\
-1/3\\
1
\end{pmatrix}= \begin{pmatrix}
0 & 0 & 1/3\\
\end{pmatrix}\begin{pmatrix}
1/3\\
-1/3\\
1
\end{pmatrix}=1/3
$$

Así que una solución es

$$
B=\Bigl\{ \frac{1}{\sqrt{2}}(1,0,0), \frac{\sqrt{2}}{\sqrt{3}}(1/2, 1,0), \sqrt{3}(1/3,-1/3,1)\Bigr\}
$$
</li>
<li>
Una base de $U$ es $\{(0,0,1)\}$, luego $U^{\perp}$ tiene de ecuación cartesiana

$$
\langle (0,0,1),(x,y,z)\rangle =0
$$

usando la matriz de Gram para calcular el producto escalar nos queda:

$$
U^{\perp}\equiv \boxed{-x+y+z=0}
$$
</li>
<li>
Como $dim \, U =1$ la base que usamos en el apartado anterior es ortogonal y podemos usar la fórmula de los coeficientes de Fourier:

$$
p_U(1,0,0)=\frac{(1,0,0),(0,0,1)}{||(0,0,1)||^2}(0,0,1)=\frac{-1}{1}(0,0,1)=\boxed{(0,0,-1)}
$$
</li>
</ol>

::::
:::::

::::: {#exr-18 .basico}

En $\boxed{\mathbb{R}^4}$ calcula una base ortogonal de 

$$
W\equiv \left\{ \begin{array}{l} 
x+y-z=0
\end{array}\right.
$$

Obtén también $p_W(0,0,1,1)$.

:::: {.callout collapse="true" title="Solución"}

Calculamos $dim\, W= 4- \mbox{ nº cart.}=4-1=3$, así que una base de $W$ tiene 3 vectores. Calculamos una (puede hacerse calculando unas paramétricas, o bien eligiéndolos de un modo adecuado para que cumplan las ecuaciones y sean linealmente independientes):

$$
\{ u_1=(1,-1,0,0),u_2=(1,0,1,0),u_3=(0,0,0,1)\}
$$

Aplicamos Gram-Schmidt:

$$
e_1=(1,-1,0,0)
$$

$$
e_2=(1,0,1,0)+\lambda_{21}(1,-1,0,0)
$$

calculamos 

$$
\lambda_{21}=\frac{-\langle u_2,e_1\rangle }{\langle e_1,e_1\rangle }=\frac{-1}{2}
$$

luego 

$$
e_2=(1/2,1/2,1,0)
$$

Ahora, como $u_3$ ya es perpendicular con ambos, entonces es $e_3=u_3$ (si se hacen los cálculos $\lambda_{31}=0$ y $\lambda_{32}=0$).
Una base ortogonal es

$$
\{ e_1=(1,-1,0,0),e_2=(1/2,1/2,1,0),e_3=(0,0,0,1)\}
$$

Para calcular la proyección ortogonal podemos utilizar la fórmula con los coeficientes de Fourier respecto de la base ortogonal que acabamos de calcular. Llamamos $v=(0,0,1,1)$:

$$
p_W(v)=\frac{\langle v,e_1\rangle }{\langle e_1,e_1\rangle }e_1+\frac{\langle v,e_2\rangle }{\langle e_2,e_2\rangle }e_2+\frac{\langle v,e_3\rangle }{\langle e_3,e_3\rangle }e_3
$$

y haciendo los cálculos de los coeficientes:

$$
\frac{\langle v,e_1\rangle }{\langle e_1,e_1\rangle }=0;\,  \frac{\langle v,e_2\rangle }{\langle e_2,e_2\rangle }=\frac{1}{3/2}=2/3;\, \frac{\langle v,e_3\rangle }{\langle e_3,e_3\rangle }=\frac{1}{1}=1
$$

Luego

$$
p_W(0,0,1,1)=\frac{2}{3}(1/2,1/2,1,0)+1\cdot (0,0,0,1)=\boxed{(1/3,1/3,2/3,1)}
$$

::::
:::::

::::: {#exr-19 .medio}

En $\mathcal{P}^2(\mathbb{R})$, el espacio de los polinomios de grado menor o igual que 2 con coeficientes reales, se considera el producto escalar 

$$
\langle p(x),q(x)\rangle =p(-1)q(-1)+p(0)q(0)+p(1)q(1)
$$

<ol type="a">
<li>Calcula la matriz de Gram de este producto escalar respecto de la base $B_S=\{1,x,x^2\}$ </li>
<li>Calcula el subespacio ortogonal a

$$
U=\{ p(x)\in \mathcal{P}^2(\mathbb{R}) / p(0)=0\}
$$ 
</li>
<li>Calcula la proyección ortogonal del polinomio $1+x-x^2$ sobre $U$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>
Calculamos los productos escalares de todas las parejas de polinomios de $B_s$:

$\langle 1,1\rangle =1^2+1^2+1^2= 3; \,\langle 1,x\rangle =1\cdot(-1)+ 1\cdot 0 + 1\cdot 1=0;$

$\langle 1,x^2\rangle = 1\cdot (-1)^2+1\cdot 0^2+1\cdot 1^2=2; \, \langle x,x\rangle = (-1)^2+0^2+1^2=2;$

$ \langle x,x^2\rangle = (-1)\cdot(-1)^2+ 0\cdot 0^2 + 1\cdot 1^2=0; \, \langle x^2,x^2\rangle =((-1)^2)^2+ (0^2)^2+(1^2)^2=2$
 
con lo que la matriz de Gram queda:

$$
G= \left(\begin{array}{ccc}
3 & 0 & 2 \\
0 & 2 & 0\\
2 & 0 & 2\\
\end{array}\right)
$$
</li>
<li>
En primer lugar calculamos unas cartesianas de $U$:  

dado $p(x)=a_0+a_1x+a_2x^2=(a_0,a_1,a_2)_{B_s}$ que $p(0)=0$ significa que $a_0=0$.
Ahora una base de este subespacio es $\{(0,1,0)_{B_s}, (0,0,1)_{B_s}\}$ (o bien $\{x,x^2\}$).
Para obtener el ortogonal a $U$ imponemos que un vector genérico $(a_0,a_1,a_2)_{B_s}$ sea perpendicular a ambos vectores de la base:
$\langle (0,1,0)_{B_s}, (a_0,a_1,a_2)_{B_s}\rangle =0$  y $ \langle (0,0,1)_{B_s}, (a_0,a_1,a_2)_{B_s}\rangle =0$.
Calculamos los productos usando la matriz de Gram del apartado anterior:

$$
\left(\begin{array}{ccc}
0 & 1 & 0 \\
\end{array}\right)\left(\begin{array}{ccc}
3 & 0 & 2 \\
0 & 2 & 0\\
2 & 0 & 2\\
\end{array}\right)\left(\begin{array}{c}
a_0\\
a_1 \\
a_2 \\
\end{array}\right)= \left(\begin{array}{ccc}
0 & 2 & 0 \\
\end{array}\right)\left(\begin{array}{c}
a_0\\
a_1 \\
a_2 \\
\end{array}\right)=2a_1=0
$$

$$
\left(\begin{array}{ccc}
0 & 0 & 1 \\
\end{array}\right)\left(\begin{array}{ccc}
3 & 0 & 2 \\
0 & 2 & 0\\
2 & 0 & 2\\
\end{array}\right)\left(\begin{array}{c}
a_0\\
a_1 \\
a_2 \\
\end{array}\right)= \left(\begin{array}{ccc}
2 & 0 & 2 \\
\end{array}\right)\left(\begin{array}{c}
a_0\\
a_1 \\
a_2 \\
\end{array}\right)=2a_0+2a_2=0
$$

Con lo que unas cartesianas de $U^{\perp}$ son 

$$
U^{\perp}\equiv \left\{ \begin{array}{l} 
a_1=0\\
a_0+a_2=0
\end{array}\right.
$$
</li>
<li>
Puesto que tenemos cartesianas de $U$ y de $U^{\perp}$ podemos utilizar el método de escribir el vector como suma de 2:

$$
(1,1,-1)_{B_s}=(\alpha, \beta, \gamma)_{B_s}+(1-\alpha, 1-\beta, -1-\gamma)_{B_s}
$$

ahora $\alpha=0$ para que el primer vector esté en $U$ y $1-\beta=0; 1-\alpha-1-\gamma=0$ para que el segundo esté en $U^{\perp}$; resolviendo
$\alpha=0;\,  \beta=1; \, \gamma=0$  con lo que $p_U(1+x-x^2)=x$ 
</li>
</ol>

::::
:::::

<iframe src="/assets/autoevaluacion/AutoevaluacionEVE.html" style="border:none;" height="800" width="100%" title="Autoevaluación"></iframe>