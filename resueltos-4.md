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


<!--En principio se muestran ejercicios sobre cuerpos finitos y sobre los racionales y reales. Puedes cambiar esta opción marcando o desmarcando la siguiente casilla.<br>
<input type="checkbox" id="casilla_cf" value="cfon" checked onclick="CF();"> Mostrar ejercicios sobre cuerpos finitos. -->


<article>
En $\mathbb{R}^4$ con el producto escalar usual se consideran los subespacios:
$$
U\equiv \left\{ \begin{aligned}
x+t&=0,\\
y+z&=0,\\
x-y-z+t&=0.
\end{aligned}\right. 
\qquad  W=\mathcal{L}((1,0,0,1),(0,0,1,-1)).$$ 

<ol type="a">
<li>Calcula una base ortogonal de cada uno de ellos.</li>
<li>Prueba que $U$ y $W$ son complementarios, pero que $U^{\perp}\not = W$.</li>
<li>Para el vector $v=(1,-1,1,1)$ calcula $p_{U}(v)$ y $p_{U^{\perp}}(v)$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular una base ortogonal.<br>
Para calcular una base ortogonal de $U$ empezamos simplificando las ecuaciones cartesianas y obteniendo una base:
$$U\equiv \left\{ \begin{array}{rl}
x+t&=0,\\
y+z&=0,\\
x-y-z+t&=0.
\end{array}\right. \sim_f U\equiv \left\{ \begin{array}{rl}
x+t&=0,\\
y+z&=0.\\
\end{array}\right.
$$ Podemos calcular una base usando como parámetros a $x$ e $y$: $\{ (1,0,0,-1),(0,1,-1,0)\}$; además esta base resulta ser ortogonal.<br>
Para $W$ ya tenemos un sistema de generadores y observamos que son linealmente independientes; pero no son ortogonales, así que utilizamos el método de Gram-Schimdt partiendo de estos vectores:
$$\begin{array}{l}
u_1=(1,0,0,1),\\
u_2=(0,0,1,-1),
\end{array}\hspace{1cm}
\begin{array}{l}
e_1=(1,0,0,1),\\
e_2=(0,0,1,-1)+\lambda_{2,1}(1,0,0,1).
\end{array}$$
Calculamos $$\lambda_{2,1}=-\frac{\langle(0,0,1,-1),(1,0,0,1)\rangle}{\langle(1,0,0,1),(1,0,0,1)\rangle}=-\frac{-1}{2}=\frac{1}{2}.$$
Así que la base ortogonal de $W$ que obtenemos es:
$$\{(1,0,0,1),(1/2,0,1,-1/2)\}.$$
</li>

<li>Probar que $U$ y $W$ son complementarios, pero que $U^{\perp}\not = W$.<br>
Son complementarios si $U+W=\mathbb{R}^4$ y $U\cap W=\{ 0 \}$. Calculamos $U+W$ reuniendo bases:
$$\begin{pmatrix}
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
\end{pmatrix}.$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix([[1,0,1,0],[0,1,0,0],[0,-1,0,1],[-1,0,1,-1]])
show(A,"~",((A.T).rref()).T)
</script>
</div>

y obtenemos que $U+W=\mathbb{R}^4$ puesto que obtenemos la base canónica. Ahora usando la fórmula de las dimensiones 
$$\operatorname{dim}(U) + \operatorname{dim}(W) = \operatorname{dim}(U+W)+ \operatorname{dim}(U\cap W)$$
obtenemos que $\operatorname{dim}(U\cap W)=0$ y por tanto $U\cap W=\{ 0 \}$.
Sin embargo, como $\langle (1,0,0,-1),(0,0,1,-1)\rangle =1$ y $(1,0,0,-1)\in U$ y $(0,0,1,-1)\in W$, entonces $W\not = U^{\perp}$.</li>

<li>Calcular $p_{U}(v)$ y $p_{U^{\perp}}(v)$.<br>
De la base de $U$ obtenemos las cartesianas de $U^{\perp}$ que son:
$$U^{\perp}\equiv \left\{ \begin{array}{rl}
x-t&=0,\\
y-z&=0.\\
\end{array}\right.$$
Escribimos ahora $v=p_{U}(v)+p_{U^{\perp}}$ usando 4 incógnitas 
$$(1,-1,1,1)=(\alpha, \beta, \gamma, \delta)+ (1-\alpha, -1-\beta,1-\gamma, 1-\delta)$$ e imponemos las condiciones de que el primero cumpla las cartesianas de $U$ y el segundo las de $U^{\perp}$ y resolvemos:
$$\begin{array}{r}
\alpha +\delta = 0,\\
-\alpha + \delta = 0,\\
\beta + \gamma = 0,\\
-1-\beta -1+ \gamma = 0,
\end{array}$$
y resulta $\alpha= 0, \beta=-1, \gamma = 1, \delta= 0$, así que:
$$p_U(1,-1,1,1)=(0,-1,1,0); \, \, p_{U^{\perp}}(1,-1,1,1)=(1,0,0,1).$$ </li>

</ol>
</details>
</article>

<article>
<ol type="a">
<li>En $\mathbb{R}^{3}$, dado el subespacio $U\equiv \left\{ \begin{array}{l}
x+y=0,\\
x+z=0.
\end{array}\right.$ y considerando el producto escalar usual, calcula $p_{U^{\perp}}(0,1,2)$. </li>
<li>En el espacio vectorial $V$, $B=\{ e_1,e_2\}$ es una base. Calcula las coordenadas respecto de la base  $B'=\{e_1+e_2, 2e_1-e_2\}$ del vector $v=(1,-1)_{B}$.</li>
<li>Consideramos en $\mathbb{R}^{2}$ el producto escalar que tiene, respecto de la base canónica, matriz de Gram (o matriz métrica)
$\begin{pmatrix}
1 & 1 \\
1 & 2
\end{pmatrix}$. Calcula una base de $\mathbb{R}^{2}$ respecto de la cual la matriz de Gram de este producto escalar sea $I_2$.</li>
<li>Determina, en función de  $b$, la signatura de la forma cuadrática $\phi:\mathbb{R}^{2} \to \mathbb{R}$ dada por 
$$\phi(x,y)= bxy.$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular $p_{U^{\perp}}(0,1,2)$.<br>
Una base de $U$ es $\{(1,-1,-1)\}$ y por tanto $U^{\perp}\equiv x-y-z=0$, descomponemos
$$(0,1,2)=(a,b,c)+(-a,1-b,2-c),$$
e imponemos al primer vector que esté en $U$ y al segundo que esté en $W$:
$$\left\{ \begin{array}{l}
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
\end{array}\right. $$
Así $p_{U^{\perp}}(0,1,2)=(1,0,1)$.
</li>

<li>Calcular las coordenadas respecto de la base  $B'$ del vector $v$.<br>
Como $B'=\{(1,1)_B, (2,-1)_B\}$, planteamos 
$$(1,-1)_B=a(1,1)_B+b(2,-1)_B$$
y resolvemos 
$$\left\{ \begin{array}{l}
a+2b=1,\\
a-b=-1.
\end{array}\right.\sim_f  \left\{ \begin{array}{l}
a=-1/3,\\
b=2/3.
\end{array}\right.$$
Luego $v=(-1/3,2/3)_{B'}$.
</li>

<li>Calcular una base de $\mathbb{R}^{2}$ respecto de la cual la matriz de Gram sea $I_2$.<br>
Que la matriz de Gram sea la identidad significa que la base sea ortonormal. En primer lugar, aplicamos Gram-Schmidt para calcular una base ortogonal. Partimos por ejemplo de la base canónica:
$$u_1=(1,0), u_2=(0,1).$$
Entonces $e_1=(1,0)$ y $e_2=(0,1)+\lambda_{21}(1,0)$ donde 
$$\lambda_{21}=-\frac{\langle u_2,e_1\rangle }{\langle e_1,e_1\rangle }=-\frac{1}{1}=-1,$$
donde los datos se han recogido de la matriz de Gram respecto de $B_c$. 
Por tanto una base ortogonal es $\{(1,0),(-1,1)\}$, el primero tiene norma 1, calculamos la del segundo:
$$\begin{pmatrix}
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
\end{pmatrix}=1$$
Así que esta base es ortonormal. 
</li>

<li>Determinar, en función de  $b$, la signatura de la forma cuadrática $\phi$.<br>
La matriz asociada a la forma cuadrática es 
$$\begin{pmatrix}
0 & b/2\\
b/2 & 0
\end{pmatrix}$$
que podemos diagonalizar por congruencia
$$\begin{pmatrix}
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
\end{pmatrix}$$
Si $b=0$ la signatura es $(0,0)$; si $b\not = 0$ la signatura es $(1,1)$.<br>
También pueden calcularse los valores propios que son 
$$\lambda= \pm (b/4)$$ y queda el mismo resultado, por supuesto.</li>
</ol>

</details>
</article>

<article>

En el espacio vectorial $\mathcal{P}_3(\mathbb{R})$ de los polinomios de grado menor o igual que tres se considera  el subespacio $U$ generado por $x$ y $x^3$ y el producto escalar dado por:
$$
\langle p(x),q(x)\rangle = \int_{-1}^1 p(x)\cdot q(x) dx.
$$

<ol type="a">
<li>Determinar una base ortogonal de $U$.</li>
<li>Determinar una base de su complementario, $U^{\perp}$.</li>
<li>Determinar la proyección sobre $U$ del vector  $1+x$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Determinar una base ortogonal de $U$.<br>
Como $\{ x, x^3\}$ es base, y $\langle x,x^3 \rangle =\int_{-1}^1 x^4dx= \left. x^5\right]_{-1}^1=2/5$
por lo que no es ortogonal. Usamos el algoritmo de Gram-Schmidt para calcular una:

$$\begin{array}{lr}
e_1=x, & \\
e_2=x^3+\lambda_{21}x,& \lambda_{21}= \frac{- \langle x,x^3\rangle}{\langle x,x\rangle}.\\
\end{array}$$
Calculamos $\langle x,x\rangle =\int_{-1}^1 x^2dx= \left. x^3\right]_{-1}^1=2/3$ luego
una base ortogonal de $U$ es $\{x,x^3-3/5x\}$.</li>

<li>Determinar una base de su complementario, $U^{\perp}$.<br>
Podemos observar que $\langle 1,x\rangle =\langle 1,x^3\rangle =0$ y $\langle x^2,x\rangle =\langle x^2,x^3\rangle =0$ por lo que $\{1,x^2\}$ es una base de $U^{\perp}$, ya que este subespacio debe tener dimensión dos.</li>

<li>Determinar la proyección sobre $U$ del vector  $1+x$.<br>
Puesto que tenemos bases sencillas de $U$ y de $U^{\perp}$ podemos expresar el polinomio dado como combinación lineal de todos ellos:
$$1+x=\alpha_1\cdot x +  \alpha_2\cdot x^3 + \alpha_3\cdot 1 +\alpha_4\cdot x^2$$
donde los dos primeros sumandos nos dan la proyección sobre $U$ y los dos últimos la proyección sobre $U^{\perp}$. Es inmediato que $\alpha_1=1$, $\alpha_2=0$, $\alpha_3=1$ y $\alpha_4=0$. Por tanto 
$$p_U (1+x)=x.$$</li>
</ol>

</details>
</article>

<article>

En $\mathbb{R}^{3}$ se consideran el producto escalar cuya matriz de Gram respecto de la base canónica es 
$$
\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}
$$
y los subespacios
$U=L((1,1,2),(2,1,1))$ y $W=L((1,a,1))$, siendo $a$ un parámetro.

<ol type="a">
<li>Determinar bases de $U+W$ y $U \cap W$ en función de $a$.</li>
<li>Calcular el complemento ortogonal de $U$.</li>
<li>Determinar la proyección sobre $U$ del vector $(5,-3,4)$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Determinar bases de $U+W$ y $U \cap W$ en función de $a$.<br>

Los sistemas de generadores dados de $U$ y $W$ son bases, así que $\operatorname{dim}(U)=2$ y $\operatorname{dim}(W)=1$ para todos los valores de $a$. Un sistema de generadores de $U+W$ se obtiene al reuinir bases de ambos, comprobaremos para qué valores de $a$ son linealmente independientes:
$$\left|\begin{array}{ccc}
1 & 2 & 1\\
1 & 1 & a\\
2 & 1 & 1
\end{array}\right|=\left|\begin{array}{ccc}
1 & 0 & 0\\
1 & -1 & a-1\\
2 & -3 & -1
\end{array}\right|=1+3(a-1)=3a-2.
$$
Si $a=2/3$ la dimensión de $U+W$ es dos y por tanto $U+W=U$, o lo que es lo mismo, $W\subset U$, así que una base es, por ejemplo, $\{ (1,1,2),(2,1,1)\}$, o también su base más sencilla que es $\{(1,0,-1),(0,1,3)\}$. Por tanto $U\cap W=W$ y una base es $\{(1,a,1)\}$. <br>

Si $a\not = 2/3$ entonces $\operatorname{dim}(U+W)=3$ y por tanto $U+W=\mathbb{R}^{3}$ y una base es la canónica. Por la fórmula de las dimensiones $\operatorname{dim}(U\cap W) + \operatorname{dim}(U+W)= d\operatorname{dim}(U) + \operatorname{dim}(W)$ y por tanto $U\cap W=\{0\}$ que no tiene base.
</li>

<li>Calcular el complemento ortogonal de $U$.<br>

Por cada vector de la base de $U$ obtenemos una cartesiana de $U^{\perp}$ imponiendo que el producto escalar sea cero (usamos la base más sencilla, aunque sirve cualquier otra):
$$(1,0,-1)\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}=0, \, \, \text{obteniendo   } \,  x+y-z=0;$$
$$(0,1,3)\begin{pmatrix}
1 & 1 & 0\\
1 & 2 & 0\\
0 & 0 & 1
\end{pmatrix}\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}=0, \, \, \text{obteniendo   } \,  x+2y+3z=0.$$
Así que 
$$U^{\perp}\equiv \left\{\begin{array}{r}
x+y-z=0,\\
x+2y+3z=0.
\end{array}\right. \sim \left\{\begin{array}{r}
x-5z=0,\\
y+4z=0.
\end{array}\right. 
$$
Y una base es $\{ (5,-4,1)\}$.
</li>

<li>Determinar la proyección sobre $U$ del vector $(5,-3,4)$.<br>

Como sabemos una base (ortogonal, puesto que tiene un solo vector) de $U^{\perp}$ calculamos 
$$p_{U^{\perp}}(5,-3,4)=\frac{\langle(5,-3,4)(5,-4,1)\rangle}{\langle(5,-4,1)(5,-4,1)\rangle}(5,-4,1)= \frac{18}{18}(5,-4,1)=(5,-4,1).$$
Luego
$$p_U(5,-3,4)=(5,-3,4)-p_{U^{\perp}}(5,-3,4)=(5,-3,4)-(5,-4,1)=(0,1,3).$$

</li>
</ol>
</details>
</article>

<article>

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

<details>
<summary>Solución</summary>

La matriz $A$ es simétrica y el Teorema espectral afirma que toda matriz simétrica y real es diagonali-zable, por tanto $A$ lo es.
Nos piden una diagonalización por semejanza ortogonal, aí que tenemos que calcular en primer lugar los valores propios: 
$$\begin{align*}
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
$$D=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1& 0 & 0\\
0 & 0 & 3 & 0\\
0 & 0 & 0 & 3
\end{pmatrix},$$
y por tanto la signatura de $A$ es $(4,0)$, por tanto definida positiva.<br>
Calculamos ahora los subespacios propios y elgimos una base ortonormal de cada uno.<br>

<strong>$V_{\lambda=1}$</strong>
$$(A-1\cdot I)=\begin{pmatrix}
1 & 0 & 0 & -1\\
0 & 1 & -1 & 0 \\
0 & -1 & 1 & 0 \\
-1 & 0 & 0 & 1
\end{pmatrix},
$$  nos da como cartesianas $\left\{\begin{array}{l}
x-t=0\\
y-z=0
\end{array}\right.$  y una base ortogonal es $\{(1,0,0,1),(0,1,1,0)\}$.<br>

<strong>$V_{\lambda=3}$</strong>
$$(A-1\cdot I)=\begin{pmatrix}
-1 & 0 & 0 & -1\\
0 & -1 & -1 & 0 \\
0 & -1 & -1 & 0 \\
-1 & 0 & 0 & -1
\end{pmatrix},
$$  nos da como cartesianas $\left\{\begin{array}{l}
x+t=0\\
y+z=0
\end{array}\right.$  y una base ortogonal es $\{(1,0,0,-1),(0,1,-1,0)\}$.<br>
Dividiendo cada vector por su norma obtenemos una base ortonormal de vectores propios, lo que nos da la matriz ortogonal $P$:
$$P=\begin{pmatrix}
1/\sqrt{2} & 0 & 0 & 1/\sqrt{2}\\
0 & 1/\sqrt{2} & 1/\sqrt{2} & 0\\
0 & 1/\sqrt{2} & -1/\sqrt{2} & 0\\
1/\sqrt{2} & 0 & 0 & -1/\sqrt{2}\\
\end{pmatrix}.$$

</details>
</article>

<article>

En $\mathbb{R}^3$ consideramos el producto escalar que, respecto de la base canónica, tiene matriz de Gram
 $$G= \left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right).$$

<ol type="a">
<li>Calcula una base ortogonal de este espacio vectorial.</li>
<li>Calcula $U^{\perp}$ para el subespacio
 $$U\equiv \left\{ \begin{array}{r}
 x+y+z=0,\\
 x-z=0.
 \end{array}\right.$$</li>
<li>Calcula $p_U(1,1,1)$ y $p_{U^{\perp}}(1,1,1)$.</li>
<li>Determina para qué valores de $a$ la fórmula
$$f(x,y,z)=x^2+2axy+2xz+2ay^2+(a+1)z^2,$$
define una forma cuadrática definida positiva.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular una base ortogonal de este espacio vectorial.<br>
Partimos de la base canónica de $\mathbb{R}^{3}$ y aplicamos Gram-Schmidt: $\{u_1=(1,0,0), u_2=(0,1,0),  u_3=(0,0,1)\}$,
$$e_1=u_1=(1,0,0),$$
$e_2=u_2+\lambda_{21}e_1,$ necesitamos calcular
$$\lambda_{21}=\frac{-\langle u_2,e_1\rangle}{\langle e_1,e_1\rangle}=\frac{-1}{1}=-1,$$
puesto que tanto numerador como denominador aparecen en la matriz de Gram. Así
$$e_2=(0,1,0)-(1,0,0)=(-1,1,0),$$
ahora
$e_3=u_3+\lambda_{31}e_1+\lambda_{32}e_2$, y de nuevo numerador y denominador de $\lambda_{31}$ aparecen en la matriz de Gram:
$$\lambda_{31}=\frac{-\langle u_3,e_1\rangle}{\langle e_1,e_1\rangle}=\frac{-1}{1}=-1,$$
pero los de $\lambda_{32}$ deben ser calculados:
$$\langle u_3,e_2\rangle(0\, 0\, 1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
-1 \\
1\\
0
\end{array}\right)=-1,$$
$$\langle e_2,e_2\rangle(-1\, 1\, 0)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
-1 \\
1\\
0
\end{array}\right)=2,$$
luego $\lambda_{32}=1/2$ y por tanto
$$e_3=(0,0,1)-(1,0,0)+1/2(-1,1,0)=(-3/2,1/2,1).$$
Luego una base ortogonal es
$$\{(1,0,0),(-1,1,0),(-3/2,1/2,1)\}.$$
</li>

<li>Calcular $U^{\perp}$. <br>
Calculamos en primer lugar una base de $U$, como $\operatorname{dim}(U)=3- \text{nº cartesianas}=1$ basta encontrar un vector que cumpla las cartesianas: $\{u=(1,-2,1)\}$.
Ahora imponemos la condición $\langle(1,-2,1),(x,y,z)\rangle=0$ que nos da la ecuación cartesiana de $U^{\perp}$:
$$(1\, -2\,\,  1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r}
x \\
y\\
z
\end{array}\right)=-5y+3z=0.$$</li>
<li>Calcula $p_U(1,1,1)$ y $p_{U^{\perp}}(1,1,1)$.<br>
Podemos usar la base ortogonal de $U$: $\{(1,-2,1)\}$ (que lo es por tener un solo vector) y la fórmula de los coeficientes de Fourier:
$$p_U(1,1,1)=\frac{\langle(1,1,1),(1,-2,1)\rangle}{\langle(1,-2,1),(1,-2,1)\rangle}(1,-2,1).$$
Calculamos los dos productos escalares y obtenemos
$$(1\, -2\,\,  1)\left(\begin{array}{rrr}
1 & 1 & 1\\
1 & 3 & 0\\
1 & 0 & 2
\end{array}\right)\left(\begin{array}{r|r}
1 & 1\\
1 & -2\\
1 & 1
\end{array}\right)=(-2|13),$$
$$p_U(1,1,1)=\frac{-2}{13}(1,-2,1)=(-2/13, 4/13, -2/13),$$
$$p_{U^{\perp}}(1,1,1)=(1,1,1)-(-2/13, 4/13, -2/13)=(15/13, 9/13, 15/13).$$
</li>

<li>Determina para qué valores de $a$ $f$ es una forma cuadrática definida positiva.<br>
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
\end{array}\right)$$
Ahora intercambiamos las filas segunda y tercera y también las columnas segunda y tercera:
$$\left(\begin{array}{ccc}
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
\end{array}\right).$$
Luego será definida positiva cuando los tres elementos de la diagonal lo sean, es decir $a>0$ y $a(1-a)>0$ luego debe ser $0<a<1$.
</li>
</ol>
</details>
</article>

<article>

En $\mathcal{P}_2(\mathbb{R})$ consideramos el producto escalar dado por $$\langle p(x),q(x)\rangle=\int_0^1 p(x)q(x)dx.$$

<ol type="a">
<li>Calcula la matriz de Gram respecto de la base $\{1, 1-x, x^2\}$.</li>
<li>Calcula una base de $U=\{p(x)\in \mathcal{P}_2(\mathbb{R}) \text{ tal que } p(1)=p'(1)=0\}$.</li>
<li>Calcula las ecuaciones cartesianas del subespacio  $U^{\perp}$.</li>
<li>Calcula $p_U(1-2x^2)$ y $p_{U^{\perp}}(1-2x^2)$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular la matriz de Gram respecto de la base $\{1, 1-x, x^2\}$.
$$\langle 1,1\rangle=\int_0^1 1\cdot 1dx=\left. x \right]_0^1=1,$$
$$\langle 1,1-x\rangle=\int_0^1 1\cdot (1-x)dx=x-\left. \dfrac{1}{2}x^2\right]_0^1=\dfrac{1}{2},$$
$$\langle 1,x^2\rangle=\int_0^1 1\cdot x^2dx=\left. \dfrac{1}{3}x^3\right]_0^1=\dfrac{1}{3},$$
$$\langle 1-x,1-x\rangle=\int_0^1 (1-x)^2dx=\left. \dfrac{1}{3}(x-1)^3\right]_0^1=\dfrac{1}{3},$$
$$\langle 1-x,x^2\rangle=\int_0^1 (x^2-x^3)dx=\dfrac{1}{3}x^3-\left. \dfrac{1}{4}x^4\right]_0^1=\dfrac{1}{12},$$
$$\langle x^2,x^2\rangle=\int_0^1 x^4dx=\left. \dfrac{1}{5}x^5\right]_0^1=\dfrac{1}{5},$$
$$G_B=\left(
\begin{array}{ccc}
  1 & \frac{1}{2} & \frac{1}{3} \\
  \frac{1}{2} & \frac{1}{3} & \frac{1}{12} \\
  \frac{1}{3} & \frac{1}{12} & \frac{1}{5}\\
\end{array}\right).$$
</li>

<li>Calcular una base de $U$.<br>
$$p(x)=a_0+a_1x+a_2x^2=(a_0,a_1,a_2)_{B_S} \Rightarrow p(1)=a_0+a_1+a_2=0.$$
Por otro lado, $$p'(x)=a_1+2a_2x \Rightarrow p'(1)=a_1+2a_2=0.$$<br>
Luego unas ecuaciones cartesianas son $U\equiv \left\{\begin{array}{l} a_0+a_1+a_2=0, \\ a_1+2a_2=0. \end{array}\right.$<br>
Resolviendo, $$\left\{\begin{array}{l} a_1=-2a_2, \\ a_0-2a_2+a_2=0. \end{array}\right.\Rightarrow \left\{ \begin{array}{l} a_0=\lambda, \\ a_1=-2\lambda,\\ a_2=\lambda. \end{array} \right.$$
Por lo tanto, una base de $U$ es $\{(1,-2,1)_{B_{S}}\}=\{1-2x+x^2\}$. 
</li>

<li>Calcula las ecuaciones cartesianas del subespacio  $U^{\perp}$.<br>
Para usar la matriz de Gram para calcular el producto escalar, será necesario calcular la matriz de Gram con respecto a la base estándar, que no es la del apartado a). Algunos de los cálculos sí sirven: 
$$\langle 1,1\rangle=1,$$
$$\langle 1,x\rangle=\int_0^1 1\cdot (x)dx=\left. \dfrac{1}{2}x^2\right]_0^1=\dfrac{1}{2},$$
$$\langle 1,x^2\rangle=\dfrac{1}{3},$$
$$\langle x,x\rangle=\int_0^1 x^2dx=\left. \dfrac{1}{3}x^3\right]_0^1=\dfrac{1}{3},$$
$$\langle x,x^2\rangle=\int_0^1 x^3dx=\left. \dfrac{1}{4}x^4\right]_0^1=\dfrac{1}{4},$$
$$\langle x^2,x^2\rangle=\dfrac{1}{5},$$
$$G_{B_{S}}=\left(
\begin{array}{ccc}
1 & \frac{1}{2} & \frac{1}{3} \\
\frac{1}{2} & \frac{1}{3} & \frac{1}{4} \\
\frac{1}{3} & \frac{1}{4} & \frac{1}{5}\\
\end{array}
\right).$$
Ahora imponemos la condición  $$\langle(1,-2,1)_{B_{S}}, (a_0, a_1,a_2)\rangle=0,$$
$$(1,-2,1)\left(
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
\right)=0. $$          
Luego unas cartesianas son $\dfrac{1}{3}a_0+\dfrac{1}{12}a_1+\dfrac{1}{30}a_2=0$, o bien   
$U^{\perp}\equiv a_0+\dfrac{1}{4}a_1+\dfrac{1}{10}a_2=0$.
</li>

<li>Calcula $p_U(1-2x^2)$ y $p_{U^{\perp}}(1-2x^2)$.<br>
Como $\operatorname{dim}(U)=1$  es rápido calcular $p_U(1-2x^2)$ usando coeficientes de Fourier. Puesto que $\{ (1,-2,1)_{B_S} \}$ es un base ortogonal de $U$.
$$p_U((1,0,-2)_{B_S})=\dfrac{\langle(1,0,-2)_{B_S},(1,-2,1)_{B_S}\rangle}{\langle(1,-2,1)_{B_S},(1,-2,1)_{B_S}\rangle} (1,-2,1)_{B_S}.$$
Calculamos  $$(1,-2,1)\left(
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
\right)=\dfrac{4}{15}.$$
Luego $$p_U((1,0,-2)_{B_S})=\dfrac{\frac{1}{4}}{\frac{1}{5}}(1,-2,1)_{B_S}=\dfrac{20}{15}(1,-2,1)_{B_S}=(\dfrac{4}{3},\dfrac{-8}{3},\dfrac{4}{3})_{B_S},$$ y por lo tanto $$p_{U^{\perp}}((1,0,-2)_{B_S})=(1,0,-2)_{B_S}-(\dfrac{4}{3},\dfrac{-8}{3},\dfrac{4}{3})_{B_S}= (-\dfrac{1}{3},\dfrac{8}{3},\dfrac{-10}{3})_{B_S}.$$
Podemos comprobar el resultado:
$$\dfrac{-1}{3}+\dfrac{1}{4}\cdot\dfrac{8}{3}+\dfrac{1}{10}\cdot\dfrac{-10}{3}=-\dfrac{1}{3}+\dfrac{2}{3}-\dfrac{1}{3}=0.$$
</li>
</ol>

</details>
</article>

<article>

En $\mathcal{P}_3(\mathbb{R})$ se consideran los subespacios vectoriales:<br>
$$U=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=p(x) \}, W=\{p(x) \in \mathcal{P}_3(\mathbb{R}) | p(-x)=-p(x) \}.$$

<ol type="a">
<li>Comprobar que $\mathcal{P}_3(\mathbb{R})= U\oplus W$.</li>
<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.</li>
<li>Para el producto escalar dado por 
$$\langle p(x),q(x)\rangle= \int_{-1} ^1 p(x)q(x)dx.$$
calcular una base ortogonal de $U$.</li>
<li>Con el mismo producto escalar, calcular $W^{\perp}$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Comprobar que $\mathcal{P}_3(\mathbb{R})= U\oplus W$.<br>
Los polinomios que cumplen la condición de $U$ son los polinomios pares, es decir, aquellos en los que solo aparecen las potencias pares de la indeterminada, y los que pertenecen a $W$ son los impares. Podemos realizar estas operaciones sin más que usar las coordenadas respecto de la base estándar $B_s=\{1,x,x^2,x^3\}$:
$$p(x)=(a_0,a_1,a_2,a_3)_{B_s}=(a_0,-a_1,a_2,-a_3)_{B_s}=p(-x).$$
Así las cartesianas de $U$ son
$\left\{\begin{array}{l}
a_1=0,\\
a_3=0.
\end{array}\right.$ Y una base $\{1,x^2\}$.
$$p(x)=(a_0,a_1,a_2,a_3)_{B_s}=(-a_0,a_1,-a_2,a_3)_{B_s}=-p(-x),$$
nos da que las cartesianas de $W$ son $\left\{\begin{array}{l}
a_0=0,\\
a_2=0.
\end{array}\right.$  Y una base $\{x,x^3\}$.<br>
Así que un sistema de generadores de $U+W$ es $\{1,x,x^2,x^3\}$ con lo que $U+W=\mathcal{P}_3(\mathbb{R})$, y además de que porque estos polinomios son linealmente independientes, se puede razonar con la fórmula de las dimensiones que $U\cap W=0$, con lo que se obtiene $\mathcal{P}_3(\mathbb{R})= U\oplus W$.
</li>

<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.<br>
Es inmediato que 
$$3x^3+x-2= (-2) + (x+3x^3)$$
y el primer polinomio está en $U$ y el segundo en $W$.
</li>

<li>Para el producto escalar dado calcular una base ortogonal de $U$.<br>
Partimos de la base de $U$ obtenida $\{1,x^2\}$ y aplicamos Gram-Schimdt:
$$e_1=1,$$
$$e_2=x^2-\frac{\langle 1,x^2\rangle}{\langle 1,1\rangle}\cdot 1.$$
Calculamos
$\langle 1,1\rangle=\int_{-1} ^1 1\cdot 1 dx =  2,$ 
$\langle 1,x^2\rangle=\int_{-1} ^1 x^2dx = \frac{2}{3}.$
Así 
$e_2= x^2-\frac{1}{3}$  y la base ortogonal de $U$ obtenida es $\{1, x^2-\frac{1}{3}\}$.
</li>

<li>Calcular $W^{\perp}$.<br>
Dada la base de $W$, $\{x,x^3\}$ observamos que 
$$\langle x,1\rangle=\int_{-1} ^1 x\cdot 1 dx = 0,$$
$$\langle x,x^2\rangle=\int_{-1} ^1 x\cdot x^2 dx = 0,$$
$$\langle x^3,1\rangle=\int_{-1} ^1 x^3\cdot 1 dx = 0,$$
$$\langle x^3,x^2\rangle=\int_{-1} ^1 x^3\cdot x^2 dx = 0.$$
Así que $U=\mathcal{L}(1,x^2)$ es el subespacio ortogonal a $W$.
</li>
</ol>
</details>
</article>

<article>

En el espacio $\mathcal{P}_3(\mathbb{R})$ de los polinomios de grado menor o igual que tres, se consideran los subespacios
$$P=\{ p(x)\in \mathcal{P}_3(\mathbb{R}) |\,  p(x)=p(-x) \}$$
$$I=\{ p(x)\in \mathcal{P}_3(\mathbb{R}) |\, p(x)=-p(-x) \}$$
y el producto escalar
$$\langle p(x),q(x)\rangle = \int_{-1}^{1} p(x)q(x)dx $$

<ol type="a">
<li>Calcular bases de $P$ e $I$ y comprobar que $I$ y $P$ son complementarios.</li>
<li>Calcular  bases ortogonales de $P$ y de $I$.</li>
<li>¿Es $P$ el complemento ortogonal de $I$ respecto de este producto escalar?</li>
<li>Escribir la fórmula para calcular la proyección ortogonal de un polinomio genérico $p(x)=a_0 +a_1 x+a_2 x^2 +a_3 x^3$ sobre $P$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular bases de $P$ e $I$ y comprobar que $I$ y $P$ son complementarios.<br>
Para calcular la base de $P$ escribimos la condición $p(x)=p(-x)$ sobre un polinomio genérico, $p(x)=a_0+a_1 x+a_2 x^2 +a_3 x^3$:
$$a_0+a_1 x+a_2 x^2 +a_3 x^3=a_0-a_1 x+a_2 x^2 -a_3 x^3,$$
y nos queda $2a_1 x+ 2a_3x^3=0$, por tanto, para que este polinomio sea cero, deben ser cero ambos coeficientes:
$$a_1=0,\\
a_3=0,$$
que son las ecuaciones cartesianas del subespacio. Una base será $\{1,x^2\}$, o bien, utilizando coordenadas respecto 
de la base estándar $\{1,x,x^2,x^3\}$, $\{(1,0,0,0),(0,0,1,0)\}$.<br>
De la misma forma para calcular la base de $I$ escribimos la condición $p(x)=-p(-x)$ sobre un polinomio genérico, $p(x)=a_0+a_1 x+a_2 x^2 +a_3 x^3$:
$$a_0+a_1 x+a_2 x^2 +a_3 x^3=-(a_0-a_1 x+a_2 x^2 -a_3 x^3), $$
y nos queda $2a_0 + 2a_2x^2=0$, por tanto, para que este polinomio sea cero, deben ser cero ambos coeficientes:
$$a_0=0,\\
a_2=0,$$
que son las ecuaciones cartesianas del subespacio. Una base será $\{x,x^3\}$, o bien, utilizando coordenadas respecto 
de la base estándar $\{1,x,x^2,x^3\}$, $\{(0,1,0,0),(0,0,0,1)\}$.
</li>

<li>Calcular  bases ortogonales de $P$ y de $I$.<br>
Utilizando el método de Gram-Schmidt en ambos casos, sólo es necesario el cálculo de un vector.<br>
Comenzamos con $P$:
$$p_1(x)=1,\\
p_2 (x)= x^2 +\lambda \cdot 1,$$
Calculamos el valor de $\lambda$ para que $\langle p_1(x),p_2(x)\rangle=0$:
$$0= \int_{-1}^{1} p_1(x)p_2(x)dx = \int_{-1}^{1} 1\cdot(x^2+\lambda )dx = \left. \frac{x^3}{3}+ \lambda x \right]_{-1}^{1} = 
(1/3 +\lambda )-(-1/3-\lambda),
$$
y nos queda  $ 2(1/3 + \lambda)=0$ con lo que $\lambda = -1/3$. Así una base ortogonal de $P$ es $\{1, x^2-1/3 \}$.<br>
Ahora para  $I$:
$$p_1(x)=x,\\
p_2 (x)= x^3 +\lambda \cdot 1.$$
Calculamos el valor de $\lambda$ para que $\langle p_1(x),p_2(x)\rangle=0$:
$$0= \int_{-1}^{1} p_1(x)p_2(x)dx = \int_{-1}^{1} x\cdot(x^3+\lambda x )dx = \left. \frac{x^5}{5}+ \lambda \frac{x^3}{3} \right]_{-1}^{1} = 
(1/5 + (1/3)\lambda )-(-(1/5)-(1/3)\lambda),
$$
y nos queda $ 2(1/5 + (1/3)\lambda)=0$ con lo que $\lambda = -5/3$.Así una base ortogonal de $I$ es $\{x, x^3-(5/3)x \}$.
</li>

<li>¿Es $P$ el complemento ortogonal de $I$ respecto de este producto escalar?<br>
Sólo es necesario comprobar que cada uno de los vectores de una base de $P$ es ortogonal con todos los de una base de $I$.<br>
Usamos las bases calculadas en el apartado a):
$$\langle 1,x\rangle=\int_{-1}^{1} 1\cdot x dx =  \left. \frac{x^2}{2}\right]_{-1}^{1}=0$$
$$\langle 1,x^3\rangle=\int_{-1}^{1} 1\cdot x^3 dx =  \left. \frac{x^4}{4}\right]_{-1}^{1}=0$$
$$\langle x^2,x\rangle=\int_{-1}^{1} x^2\cdot x dx =  \left. \frac{x^4}{4}\right]_{-1}^{1}=0$$
$$\langle x^2,x^3\rangle=\int_{-1}^{1} x^2\cdot x^3 dx =  \left. \frac{x^6}{6}\right]_{-1}^{1}=0$$
</li>
<li>Escribir la fórmula para calcular la proyección ortogonal de un polinomio genérico $p(x)=a_0 +a_1 x+a_2 x^2 +a_3 x^3$ sobre $P$.<br>
Pueden usarse las cartesianas de $P$ y de su ortogonal que es $I$ para descomponer el vector genérico
$$(a_0,a_1,a_2,a_3)=(a,b,c,d)+(a_0 -a,a_1 -b, a_2 -c, a_3 -d).$$
Como el primer vector debe estar en $P$ se tiene $b=0$ y $d=0$. Como el segundo sumando debe estar en $I$ entonces $a_0-a=0$ y $a_2-c=0$.
Entonces se tiene que la proyección sobre $P$ es $(a_0,0,a_2,0)$ o bien $a_0+a_2x^2$.
</li>
</ol>
</details>
</article>

<article>

En $\mathbb{R}^{4}$ con el producto escalar usual se considera el subespacio
$$U= \mathcal{L} ((1,1,0,1)),$$
y el endomorfismo $f:\mathbb{R}^{4} \to \mathbb{R}^{4}$ dado por 
$$\begin{array}{rl}
f(1,-1,0,0)&=(1,-1,0,0),\\
f(1,0,0,-1)&=(1,0,0,-1),\\
f(0,0,1,0)&=(0,0,1,0),\\
f(1,1,0,1)&=(0,0,0,0).\\
\end{array}
$$

<ol type="a">
<li>Calcula la proyección ortogonal sobre $U$ de cada uno de los vectores de la base canónica.</li>
<li>Calcula la proyección ortogonal sobre $U^{\perp}$ de cada uno de los vectores de la base canónica.</li>
<li>Calcula la matriz asociada a $f$ respecto de la base $\overline{B}=\{(1,-1,0,0),(1,0,0,-1),(0,0,1,0),(1,1,0,1)\}$.</li>
<li>Calcula la matriz asociada al endomorfismo respecto de la base canónica.</li>
<li>Calcula bases del núcleo y la imagen de $f$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular la proyección ortogonal sobre $U$ de cada uno de los vectores de la base canónica.<br>
Como $U$ tiene dimensión 1, es fácil calcular la proyección usando los coeficientes de Fourier:
$$\begin{align*}
p_U (1,0,0,0)&=\frac{\langle(1,0,0,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3),\\
p_U (0,1,0,0)&=\frac{\langle(0,1,0,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3),\\
p_U (0,0,1,0)&=\frac{\langle(0,0,1,0),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=(0,0,0,0),\\
p_U (0,0,0,1)&=\frac{\langle(0,0,0,1),(1,1,0,1)\rangle}{\langle(1,1,0,1),(1,1,0,1)\rangle}(1,1,0,1)=\frac{1}{3}(1,1,0,1)=(1/3,1/3,0,1/3).\\
\end{align*}$$
</li>

<li>Calcular la proyección ortogonal sobre $U^{\perp}$ de cada uno de los vectores de la base canónica.<br>
$p_{U^{\perp}} (v)=v-p_U (v)$
$$\begin{align*}
p_{U^{\perp}}(1,0,0,0)&=(1,0,0,0)-(1/3,1/3,0,1/3)=(2/3, -1/3,0, -1/3),\\
p_{U^{\perp}}(0,1,0,0)&=(0,1,0,0)-(1/3,1/3,0,1/3)=(-1/3, 2/3,0, -1/3),\\
p_{U^{\perp}}(0,0,1,0)&=(0,0,1,0)-(0,0,0,0)=(0,0,1,0),\\
p_{U^{\perp}}(0,0,0,1)&=(0,0,0,1)-(1/3,1/3,0,1/3)=(-1/3, -1/3,0, 2/3).\\
\end{align*}$$
</li>

<li>Calcular la matriz asociada a $f$ respecto de la base $\overline{B}$.<br>
Tenemos calculadas las imágenes de los vectores de $\overline{B}$, así que sólo tenemos que calcular sus coordenadas respecto de $\overline{B}$, que son inmediatas
$$\begin{array}{rll}
f(1,-1,0,0)&=(1,-1,0,0)&=(1,0,0,0)_{\overline{B}},\\
f(1,0,0,-1)&=(1,0,0,-1)&=(0,1,0,0)_{\overline{B}},\\
f(0,0,1,0)&=(0,0,1,0)&=(0,0,1,0)_{\overline{B}},\\
f(1,1,0,1)&=(0,0,0,0)&=(0,0,0,0)_{\overline{B}}.\\
\end{array}$$
Así que 
$$\mathcal{M}(f,\overline{B})=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 &  0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 
\end{pmatrix}.$$
</li>

<li>Calcular la matriz asociada al endomorfismo respecto de la base canónica.<br>
$f$ es la proyección ortogonal sobre $U^{\perp}$, por lo que 
 $$\mathcal{M}(f,B_c)=\begin{pmatrix}
2/3 & -1/3 & 0 & -1/3\\
-1/3 & 2/3 &  0 & -1/3\\
0 & 0 & 1 & 0\\
-1/3 & -1/3 & 0 & 2/3 
\end{pmatrix}.$$
</li>

<li>Calcular bases del núcleo y la imagen de $f$.<br>
Como $\operatorname{dim}(\operatorname{Im}(f))=\operatorname{rg}(\mathcal{M}(f,\overline{B}))=3$ entonces una base de la imagen son los tres primeros vectores de la base $\overline{B}$, es decir, $\operatorname{Im}(f)=U^{\perp}$.
Así $\operatorname{dim}(\operatorname{ker}(f))=1$ y como $f(1,1,0,1)=(0,0,0,0)$, entonces una base de $\operatorname{ker}(f)$ es $\{(1,1,0,1)\}$, con lo que $\operatorname{ker}(f)=U$. 
</li>
</ol>
</details>
</article>