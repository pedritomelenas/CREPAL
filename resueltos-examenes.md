---
title: Miscelánea
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


::::: {#exr-o1}

Dada la matriz

$$
A=\left(
\begin{array}{ccc}
0 & 0 & 1\\
0 & a & 0 \\
1 & 0 & 0 
\end{array}\right)
\hspace{1em} \mbox{ con } a\not = 0.
$$

<ol type="a">
<li>Calcula los valores propios y sus multiplicidades algebraicas en todos los casos posibles.</li>

<li>¿Para qué valores de $a$ es diagonalizable?</li>

<li>Para el caso $a=1$ comprueba que es diagonalizable por semejanza ortogonal y calcula $D$ diagonal y $P$ ortogonal (esto es, $P^t=P^{-1}$) tal que $D=P^tAP$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular los valores propios y sus multiplicidades algebraicas.

Calculamos los valores propios en función de $a$:

$$
|A-\lambda I|=\left|
\begin{array}{ccc}
-\lambda & 0 & 1\\
0 & a-\lambda & 0 \\
1 & 0 & -\lambda 
\end{array}\right|= (a-\lambda)\left|
\begin{array}{cc}
-\lambda &  1\\
1 &  -\lambda 
\end{array}\right|=(a-\lambda)(\lambda^2-1)=(a-\lambda)(\lambda-1)(\lambda +1).
$$

Así que cuando $a\not = \pm 1$ entonces hay tres valores propios distintos con multiplicidad algebraica 1. Pero si $a=1$ entonces hay dos valores propios, $\lambda=1$ con multiplicidad algebraica dos y $\lambda=-1$ con multiplicidad algebraica uno; y si $a=-1$ entonces hay dos valores propios, $\lambda=-1$ con multiplicidad algebraica dos y $\lambda=1$ con multiplicidad algebraica uno.
</li>

<li>¿Para qué valores de $a$ es diagonalizable?

Siempre es diagonalizable puesto que es simétrica.</li>

<li>Comprobar que es diagonalizable por semejanza ortogonal y calcular $D$ diagonal y $P$ ortogonal.

Como es simétrica es diagonalizable por semejanza ortogonal (Teorema espectral). Para $a=1$ ya tenemos los valores propios: $\lambda=1$ con multiplicidad algebraica dos y $\lambda=-1$ con multiplicidad algebraica uno, y nos queda calcular las bases ortonormales (para que $P$ sea ortogonal) de cada uno de los subespacios propios:

**$V_{1}$**

$$
\begin{pmatrix}
-1 & 0 & 1\\
0 & 0 & 0\\
1 & 0 & -1\\
\end{pmatrix}\begin{pmatrix}
x\\ y\\ z
\end{pmatrix}=  \begin{pmatrix}
0\\ 0\\ 0 
\end{pmatrix}
$$

nos da la ecuación $x-z=0$ y una base es $\{(1,0,1),(0,1,0)\}$ que es ortogonal, así que los dividimos por su norma: $\{(1/\sqrt{2},0,1/\sqrt{2}),(0,1,0)\}$.

**$V_{-1}$**

$$
\begin{pmatrix}
1 & 0 & 1\\
0 & 2 & 0\\
1 & 0 & 1\\
\end{pmatrix}\begin{pmatrix}
x\\ y\\ z
\end{pmatrix}=  \begin{pmatrix}
0\\ 0\\ 0 
\end{pmatrix}
$$

nos da las ecuaciones $x+z=0; y=0$ y una base es $\{(1,0,-1)\}$ que es ortogonal, así que lo dividimos por su norma: $\{(1/\sqrt{2},0,-1/\sqrt{2})\}$.

Tenemos entonces

$$
D=\begin{pmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & -1
\end{pmatrix},\hspace{2cm}  P=\begin{pmatrix}
1/\sqrt{2} & 0  & 1/\sqrt{2}\\
0 & 1 & 0 \\
1/\sqrt{2} & 0  & -1/\sqrt{2}\\
\end{pmatrix}.
$$

</li>

</ol>
::::
:::::

::::: {#exr-o2}

<ol type="a">
<li>Calcula la matriz de Gram del producto escalar en el espacio de las matrices simétricas de orden dos dado por la fórmula:

$$
\langle A,B\rangle=\operatorname{traza}(AB)
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
\end{pmatrix}\right\}$.</li>

<li>En $\mathbb{R}^2$ conocemos la base $B=\{ (1,1),(2,-1)\}$ y que la matriz de cambio de base de $B$ a $B'$ es $P=\begin{pmatrix}
1 &  2\\
2/3  & 1/3\\
\end{pmatrix}$. Calcula $B'$. </li>

<li>Calcula la signatura de la matriz $A=\begin{pmatrix}
0 & 0 & 1  \\
0 & b& 0\\
1 & 0 & 0
\end{pmatrix}$ según los valores de $b$.</li>
<li>De una aplicación lineal $f:\mathbb{R}^{n} \longrightarrow \mathbb{R}^{m}$ se conoce que es sobreyectiva. ¿Puedes deducir algo sobre los valores de $n$ y $m$? 
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcula la matriz de Gram.

Para obtener la matriz de Gram calculamos el producto de cada dos matrices de la base:

$$
\langle \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} ,\begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\rangle=\operatorname{traza}\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\right)=\operatorname{traza}\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} \right)=1,
$$

$$\langle \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} ,\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}\rangle=\operatorname{traza}\left(  \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix}\begin{pmatrix}
0 & 1 \\
1 & 0
\end{pmatrix}\right)=\operatorname{traza}\left(  \begin{pmatrix}
0 & 1 \\
0 & 0
\end{pmatrix} \right)=0,
$$

del mismo modo se obtienen los productos restantes y se obtiene

$$
G=\begin{pmatrix}
1 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 1\end{pmatrix}.
$$
</li>

<li>Calcula $B'$.

Los vectores de $B'$ escritos en la base canónica forman la matriz de cambio de base de $B'$ a $Bc$, así que calcularemos esta matriz para obtenerlos.
Como la matriz de cambio de base de $B'$ a $B$ es la inversa de $P$ y la de $B$ a $B_c$ es $Q=\begin{pmatrix}
1 & 2\\ 1 &-1\\
\end{pmatrix}$, entonces la matriz que buscamos es 
$Q\cdot P^{-1}$. Calculamos $P^{-1}$:

$$
\left(\begin{array}{cc|cc}
1 & 2 & 1 & 0\\
2/3 & 1/3 & 0 & 1
\end{array}\right)\sim_f \left(\begin{array}{cc|cc}
1 & 2 & 1 & 0\\
0 & -1 & -2/3 & 1
\end{array}\right)\sim_f \left(\begin{array}{cc|cc}
1 &0 & -1/3 & 2\\
0 & 1 & 2/3 & -1
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
P=matrix([[1,2],[2/3,1/3]])
I=matrix([[1,0],[0,1]]) 
PI=P.augment(I,subdivide=True) 
show(PI,"~",PI.rref())
</script>
:::

$$
Q\cdot P{-1}=\begin{pmatrix}
1 & 2\\ 1 & -1 
\end{pmatrix}\begin{pmatrix}
-1/3 & 2\\
2/3 & -1
\end{pmatrix}=\begin{pmatrix}
1 & 0\\ -1 & 3
\end{pmatrix},
$$

luego $B'=\{ (1,-1), (0,3)\}$.
</li>

<li>Calcular la signatura de la matriz $A$.

Para obtener su signatura debemos diagonalizarla, bien por congruencia o por semejanza ortogonal. Como es idéntica a la del problema 4 tenemos que sus valores propios son $1,-1$ y $b$, así que la signatura será:

$$
\begin{array}{lr}
\operatorname{sig}(A)=(2,1) & \mbox{ si }b>0,\\
\operatorname{sig}(A)=(1,1) & \mbox{ si }b=0,\\
\operatorname{sig}(A)=(1,2) & \mbox{ si }b<0.\\
\end{array}
$$

</li>

<li>¿Puedes deducir algo sobre los valores de $n$ y $m$?

Como es sobreyectiva $\dim(\operatorname{Im}(f))=m$ y por la fórmula de las dimensiones 

$$
\dim(\operatorname{ker}(f))+ \dim(\operatorname{Im}(f))=\dim(\mathbb{R}^{n})=n.$$
Así que $n=a+m$ siendo $a=\dim(\operatorname{ker}(f))$. Por tanto $$n\geq m.
$$

</li>

</ol>
::::
:::::

::::: {#exr-o3}

Dada la matriz

$$
A=\left(
\begin{array}{cccc}
-1 & -2 & 3 & 2\\
0 & 1 & 0 & 1\\
-2 & -2 & 4 & 2\\
0 & 0 & 0 & 2
\end{array}\right)
$$

<ol type="a">
<li>Calcula los valores propios y sus multiplicidades algebraicas.</li>

<li>Estudia si es diagonalizable y en caso afirmativo determinar su forma diagonal, $D$, y una matriz de paso, $P$, verificando que $D=P^{-1}AP$.</li>

<li>Razona si $A$ es o no diagonalizable por semejanza ortogonal.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular los valores propios y sus multiplicidades algebraicas.

Calculamos el polinomio característico:

$$
\begin{align*}
|A-\lambda I|=& 
\left|
\begin{array}{cccc}
-1-\lambda & -2 & 3 & 2\\
0 & 1-\lambda  & 0 & 1\\
-2 & -2 & 4-\lambda & 2\\
0 & 0 & 0 & 2-\lambda
\end{array}\right|= (2-\lambda)\left|
\begin{array}{ccc}
-1-\lambda & -2 & 3 \\
0 & 1-\lambda  & 0 \\
-2 & -2 & 4-\lambda \\
\end{array}\right|=(2-\lambda)(1-\lambda)\left|
\begin{array}{cc}
-1-\lambda  & 3 \\
-2 &  4-\lambda \\
\end{array}\right| \\
=&(2-\lambda)(1-\lambda)(\lambda^2-3\lambda +2)=(2-\lambda)^2(1-\lambda)^2
\end{align*}
$$

Así que hay dos valores propios $\lambda=1$ y $\lambda=2$, ambos con multiplicidad algebraica dos.
</li>

<li>Estudiar si es diagonalizable y en caso afirmativo determinar su forma diagonal, $D$, y una matriz de paso, $P$.

Para comprobar que es diagonalizable debemos calcular las multiplicidades geométricas, es decir, las dimensiones de los correspondientes subespacios propios:

$V_{1}$ tiene cartesianas dadas por las filas de 

$$
A-1\cdot I=\left(
\begin{array}{cccc}
-2 & -2 & 3 & 2\\
0 & 0 & 0 & 1\\
-2 & -2 & 3 & 2\\
0 & 0 & 0 & 1
\end{array}\right)\sim_f \left(
\begin{array}{cccc}
-2 & -2 & 3 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[-2,-2,3,2],[0,0,0,1],[-2,-2,3,2],[0,0,0,1]])
show(A,"~",A.rref())
</script>
:::

Como hay dos ecuaciones, $\dim(V_{1})=4-2=2$, unas cartesianas son

$$
V_{1}\equiv \left\{ \begin{array}{l}
2x+2y-3z=0,\\
t=0.
\end{array}\right.
$$

Y una base es por ejemplo $\{ (1,-1,0,0),(3,0,2,0)\}$.

$V_{2}$ tiene cartesianas dadas por las filas de 

$$
A-2\cdot I=\left(
\begin{array}{cccc}
-3 & -2 & 3 & 2\\
0 & -1 & 0 & 1\\
-2 & -2 & 2 & 2\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left(
\begin{array}{cccc}
1 & 1 & -1 & -1\\
0 & -1 & 0 & 1\\
0 & 1 & 0 & -1\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left(
\begin{array}{cccc}
1 & 0 & -1 & 0\\
0 & 1 & 0 & -1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[-3,-2,3,2],[0,-1,0,1],[-2,-2,2,2],[0,0,0,0]])
show(A,"~",A.rref())
</script>
:::

Como hay dos ecuaciones, $\dim(V_{2})=4-2=2$, unas cartesianas son

$$
V_{2}\equiv \left\{ \begin{array}{l}
x-z=0,\\
y-t=0.
\end{array}\right.
$$

Y una base es por ejemplo $\{ (1,0,1,0),(0,1,0,1)\}$.

Así concluimos que ambos valores propios tienen multiplicidad geométrica dos, y como coincide con sus multiplicidades algebraicas respectivas la matriz sí es diagonalizable.

$$
D=\begin{pmatrix}
 1 & 0 & 0 & 0\\
 0 & 1 & 0 & 0\\
 0 & 0 & 2 & 0 \\
 0 & 0 & 0 & 2
 \end{pmatrix}, \hspace{1em} P=\begin{pmatrix}
 1 & 3 & 1 & 0\\
 -1 & 0 & 0 & 1\\
 0 & 2 & 1 & 0 \\
 0 & 0 & 0 & 1
 \end{pmatrix}.
$$

</li>

<li>Razonar si $A$ es o no diagonalizable por semejanza ortogonal.

La matriz no es diagonalizable por semejanza ortogonal porque no es simétrica.
</li>
</ol>
::::
:::::

::::: {#exr-o4}

<ol type="a">
<li>Dadas las matrices $A=\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}$ y 
$B=\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}$, dar matrices regulares $P$ y $Q$ de forma que $Q\cdot A \cdot P = B$.</li>

<li>Determinar las coordenadas del vector $p(x)=1+x+x^2$ de $\mathcal{P}_2(\mathbb{R})$ respecto de la base $B'=\{1, 1-x, 1-x^2  \}$.</li>

<li>Razonar que la aplicación $G: \mathcal{M}_2(\mathbb{R})  \longrightarrow \mathcal{M}_2(\mathbb{R})$ definida por: 

$$
G\left(\begin{pmatrix} a & b \\ c & d \end{pmatrix}\right)=\begin{pmatrix} a\cdot b & 0 \\ c & d \end{pmatrix}
$$

no es lineal.</li>

<li>Calcular la signatura de la matriz simétrica 

$$
C=\begin{pmatrix}
5 & 2 \\ 2 & \frac{1}{2}
\end{pmatrix}.
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Dar matrices regulares $P$ y $Q$ de forma que $Q\cdot A \cdot P = B$.

$$
\left(\begin{array}{rcl}
A&|&I\\
\hline
I &| \\ \end{array} \right)=\left(\begin{array}{ll|ll}
 1 & 0 & 1 & 0\\ 
 0 & 0 & 0 & 1\\
 \hline
 1 & 0 & & \\
 0 & 1 & & \\
 \end{array}\right)\sim_f \left(\begin{array}{ll|ll}
 1 & 0 & 1 & 0\\ 
 1 & 0 & 1 & 1\\
 \hline
 1 & 0 & & \\
 0 & 1 & & \\
 \end{array}\right)\sim_c \left(\begin{array}{ll|ll}
 1 & 1 & 1 & 0\\ 
 1 & 1 & 1 & 1\\
 \hline
 1 & 1 & & \\
 0 & 1 & & \\
 \end{array}\right),
$$

luego 

$$
Q=\begin{pmatrix} 1 & 0 \\ 1 & 1 \end{pmatrix} \mbox{ y } P=\begin{pmatrix} 1 & 1 \\ 0 & 1 \end{pmatrix}.
$$

</li>

<li>Determinar las coordenadas del vector $p(x)$ respecto de la base $B'$.

Si denotamos $1+x+x^2=(\alpha_1, \alpha_2,\alpha_3)_{B'}$, tenemos:

$$
1+x+x^2=\alpha_1 \cdot  1 + \alpha_2 \cdot  (1-x)+\alpha_3 \cdot  (1-x^2)
= (\alpha_1+\alpha_2+\alpha_3) \cdot 1 - \alpha_2 \cdot x - \alpha_ 3 \cdot x^2,
$$

y resolviendo $\alpha_1+\alpha_2+\alpha_3=1$, $-\alpha_2=1$, $-\alpha_3=1$, nos queda que

$$
1+x+x^2=(3,-1,-1)_{B'}.
$$

Alternativamente, la matriz del cambio de $B'$ a $B_s$ es 
$P=\begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 0 \\ 0 & 0 &-1 \end{pmatrix}$, luego la matriz del cambio de $B_s$ a $B'$ es 

$$
P^{-1}=\begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 0 \\ 0 & 0 &-1 \end{pmatrix}.
$$

Puesto que $1+x+x^2=(1,1,1)_{B_s}$ obtenemos:

$$
\begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 0 \\ 0 & 0 &-1 \end{pmatrix}\cdot
\begin{pmatrix}
1 \\ 1 \\ 1
\end{pmatrix}
=
\begin{pmatrix}
3 \\ -1 \\ -1
\end{pmatrix}.
$$

</li>

<li>Razonar que la aplicación $G$ no es lineal.

Calculamos

$$
G\left(\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}\right)=\begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}, G\left(\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}\right)=\begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}
$$

Sin embargo la imagen de la suma de estas matrices es

$$
G\left(\begin{pmatrix} 1 & 1 \\ 0 & 0 \end{pmatrix}\right)=\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}\not = G\left(\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix}\right)+G\left(\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}\right).
$$

</li>

<li>Calcular la signatura de C.

Diagonalizamos por congruencia 

$$
C=\begin{pmatrix}
5 & 2 \\ 2 & \frac{1}{2}
\end{pmatrix}\sim_f \begin{pmatrix}
5 & 2 \\ 0 & -\frac{3}{10} 
\end{pmatrix}\sim_c \begin{pmatrix}
5 & 0 \\ 0 & -\frac{3}{10} \end{pmatrix},
$$

por lo que $\operatorname{sig}(C)=(1,1)$.</li>
</ol>
::::
:::::

::::: {#exr-o5}

<ol type="a">
<li>De una aplicación lineal $f:\mathbb{R}^{3}\longrightarrow \mathbb{R}^{4}$ se sabe que $f(5,1,1)=f(1,5,1)=f(1,1,5)=(5,5,5,5)$. Determinar bases del núcleo y la imagen de $f$.</li>

<li>Dar bases $B$ de $\mathbb{R}^{3}$ y 
$B'$ de $\mathbb{R}^{4}$ de forma que $\mathcal{M}_{B B'}(f)=\begin{pmatrix}
1 & 0 & 0 \\ 0 & 0 & 0 \\  0 & 0 & 0 \\  0 & 0 & 0 \\
\end{pmatrix}$.</li>

<li>Determinar, en función de  $b$ la signatura de la forma cuadrática

$$
\phi(x,y)= x^2+  y^2 + 2b x y.
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar bases del núcleo y la imagen de $f$.

La imagen de $f$ está generada por $\{(5,5,5,5)\}$ así que este vector es una base, o también $\{(1,1,1,1)\}$, que por tanto tiene dimensión uno. 

Como $f(5,1,1)-f(1,5,1)=f(4,-4,0)=(0,0,0,0)$ y $f(5,1,1)-f(1,1,5)=f(4,0,-4)=(0,0,0,0)$ entonces $\{(4,-4,0),(4,0,-4)\}$ es una base del núcleo (que tiene dimensión dos).
</li>

<li>Dar bases $B$ y $B'$.

Hay muchas soluciones, las condiciones son: la imagen del primer vector de $B$ es el primer vector de $B'$, los otros dos vectores de $B$ deben estar en el núcleo.  
</li>

<li>Determinar, en función de  $b$ la signatura de la forma cuadrática $\phi$.

La matriz asociada a la forma cuadrática es 

$$
A=\begin{pmatrix}
 1 & b\\
 b & 1
\end{pmatrix}.
$$

Diagonalizando por congruencia

$$
\begin{pmatrix}
 1 & b\\
 b & 1
\end{pmatrix}\sim_f\begin{pmatrix}
 1 & b\\
 0 & 1-b^2
\end{pmatrix}\sim_c \begin{pmatrix}
 1 & 0\\
 0 & 1-b^2
\end{pmatrix}.
$$ 

Como el segundo elemento de la diagonal se anula en $b=1$ y $b=-1$ la distinción de casos queda:

Si $b=\pm 1$ entonces $\operatorname{sig}(A)=(1,0)$.

Si $-1<b<1$ entonces $\operatorname{sig}(A)=(2,0)$.

Si $b<-1$ o $ b>1$ entonces $\operatorname{sig}(A)=(1,1)$.
</li>
</ol>
::::
:::::

::::: {#exr-o6}

Dadas las matrices

$$
A= \left(\begin{array}{rrr}
1 & 1 & 0\\
0 & 0 & 0\\
0 & 1 & 0
\end{array}\right),\hspace{2cm}  B= \left(\begin{array}{rrr}
1 & 1 & 0\\
1 & 0 & 0\\
1 & 1 & 0
\end{array}\right)
$$

<ol type="a">
<li>¿Existen $P, Q$ matrices regulares tales que $Q^{-1}AP=B$?</li>

<li>¿Existe $P$ regular tal que $AP=B$?</li>

<li>¿Existe $P$ regular tal que $PA=B$?</li>

<li>¿Existe $P$ regular tal que $P^{-1}AP=B$?</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>¿Existen $P, Q$ matrices regulares tales que $Q^{-1}AP=B$?

La pregunta es si las matrices son equivalentes, y esto ocurre si, y solo si, tienen el mismo rango. Es inmediato ver que ambas tienen rango 2, por tanto la respuesta es afirmativa.</li>

<li>¿Existe $P$ regular tal que $AP=B$?

En este caso nos preguntan si son equivalentes por columnas, si, y solo si, tienen la misma forma de Hermite por columnas. Calculamos en ambos casos:

$$
A= \left(\begin{array}{rrr}
1 & 1 & 0\\
0 & 0 & 0\\
0 & 1 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 0 & 0\\
0 & 1 & 0
\end{array}\right),
$$

$$
B= \left(\begin{array}{rrr}
1 & 1 & 0\\
1 & 0 & 0\\
1 & 1 & 0
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0\\
1 & 0 & 0
\end{array}\right),
$$

y como no son iguales la respuesta es negativa.</li>

<li>¿Existe $P$ regular tal que $PA=B$?

Ahora nos preguntan si son equivalentes por filas, para lo que calculamos sus formas de Hermite por filas y las comparamos:

$$
A= \left(\begin{array}{rrr}
1 & 1 & 0\\
0 & 0 & 0\\
0 & 1 & 0
\end{array}\right)\sim_f \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 0
\end{array}\right),
$$

$$
B= \left(\begin{array}{rrr}
1 & 1 & 0\\
1 & 0 & 0\\
1 & 1 & 0
\end{array}\right)\sim_f \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 0
\end{array}\right),
$$

como son iguales entonces la respuesta es afirmativa.</li>

<li>¿Existe $P$ regular tal que $P^{-1}AP=B$?

Si calculamos los valores propios de ambas:

$$
|A-\lambda I|= \left|\begin{array}{rrr}
1- \lambda & 1 & 0\\
0 & -\lambda & 0\\
0 & 1 & -\lambda
\end{array}\right|=(1-\lambda)(-\lambda)^2.
$$

Pero el valor propio $\lambda=0$ tiene multiplicidad geométrica uno, luego no es diagonalizable.

$$
|B-\lambda I|= \left|\begin{array}{rrr}
1-\lambda & 1 & 0\\
1 & -\lambda & 0\\
1 & 1 & -\lambda
\end{array}\right|=(-\lambda)(\lambda^2-\lambda-1),
$$

en este caso aparecen tres valores propios distintos $\{0, \frac{1+\sqrt{5}}{2}, \frac{1-\sqrt{5}}{2}\}$ y por tanto la matriz sí es diagonalizable. Entonces no puede existir una tal $P$, puesto que ello implicaría que $A$ sería también diagonalizable. También es suficiente comprobar que los valores propios son distintos y que $B$ es diagonalizable.
</li>
</ol>
::::
:::::

::::: {#exr-o7}

Dada la matriz
$$
A= \left(\begin{array}{rrr}
2 & 0 & 2\\
0 & 1 & 0\\
2 & 0 & -1
\end{array}\right).
$$

<ol type="a">
<li>¿Existen $P, Q$ matrices regulares tales que $Q^{-1}AP=I_3$?</li>

<li>¿Existe $P$ regular tal que $P^{-1}AP=I_3$?</li>

<li>¿Existe $P$ regular tal que $P^{t}AP=I_3$?</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>¿Existen $P, Q$ matrices regulares tales que $Q^{-1}AP=I_3$?

Existen $Q , P$ regulares si $A$ e $I$ son equivalentes, esto es, si tienen el mismo rango. Calculamos el rango de $A$.
Calculamos el determinante de $A$ desarrolando por el elemento 22,

$$
\det(A)=\left|
\begin{array}{ccc}
 2 & 0 & 2 \\
 0 & 1 & 0 \\
  2 & 0 & -1 \\
  \end{array}
   \right|=\left|
     \begin{array}{cc}
      2 & 2 \\
       2 & -1 \\
        \end{array}
  \right| =-6\neq 0.  
$$

Por lo tanto el rango es tres, al igual que el de $I_3$. Las matrices son equivalentes y por lo tanto \textbf{sí}  existen $P$ y $Q$ regulares tales que $Q^{-1}AP=I_3$.
</li>

<li>¿Existe $P$ regular tal que $P^{-1}AP=I_3$?

Que exista la matriz $P$ regular tal que $P^{-1}AP=I_3$ equivale a decir que $A$ es diagonalizable por semejanza y su forma diagonal es $I_3$. 

Calculamos los valores propios de $A$:

$$
\left|
  \begin{array}{ccc}
    2-\lambda & 0 & 2 \\
    0 & 1-\lambda & 0 \\
    2 & 0 & -1-\lambda \\
  \end{array}
\right|= (1-\lambda) \left|
     \begin{array}{cc}
      2 -\lambda& 2 \\
       2 & -1-\lambda \\
        \end{array}
  \right|= (1-\lambda)(-(2-\lambda)(1+\lambda)-4)=(1-\lambda)(2+\lambda)(3-\lambda).
$$

Como los valores propios de $A$ son 1, -2 y 3, su forma diagonal (si fuera diagonalizable) no puede ser $I_3$, por lo tanto, no existe $P$ regular tal que  $P^{-1}AP=I_3$
</li>

<li>¿Existe $P$ regular tal que $P^{t}AP=I_3$?

Si existiera una matriz $P$ cumpliendo la igualdad, estaríamos diciendo que $A$ es congruente con $I_3$ y por tanto su signatura  sería $(3,0)$, pero como los valores propios son  1, -2 y 3, su signatura es $(2,1)$, y por tanto no existe dicha matriz $P.$
</li>
</ol>
::::
:::::

::::: {#exr-o8}

Dada la matriz:

$$
A=\begin{pmatrix}
a & 0 & 0 & 0 \\
a & 2 & 2 & a \\
a & 2 & 2 & a \\
a & 0 & 0 & 0
\end{pmatrix}.
$$

<ol type="a">
<li>Estudiar para qué valores del parámetro $a$ es $A$ diagonalizable.</li>

<li>Para el valor $a=0$ la matriz $A$ es simétrica, determinar su forma diagonal $D$ así como una matriz ortogonal $P$ de forma que $D=P^{-1}\cdot  A\cdot P=P^{t}\cdot A\cdot P$.
¿Cuál es la signatura de $A$?</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Estudiar para qué valores del parámetro $a$ es $A$ diagonalizable.

Calculamos los valores propios y sus multiplicidades algebraicas:

$$
\begin{align*}
|A-\lambda I|&=\left|\begin{array}{cccc}
a-\lambda & 0 & 0 & 0 \\
a & 2-\lambda & 2 & a \\
a & 2 & 2-\lambda & a \\
a & 0 & 0 & -\lambda
\end{array}\right|=(a-\lambda)(-\lambda)\left|\begin{array}{cc}
2-\lambda & 2\\
2 & 2-\lambda
\end{array}\right|\\
&= (a-\lambda)(-\lambda)((2-\lambda)^2-4)=(a-\lambda)(-\lambda)(\lambda^2-4\lambda)=(a-\lambda)(-\lambda)^2(\lambda-4).
\end{align*}
$$

**Caso $a\not \in\{0,4\}$**

En este caso tenemos que para $\lambda=4$ o $\lambda=a$ ambas multiplicidades algebraicas y geométricas son 1 mientras que para $\lambda=0$
la multiplicidad algebraica es 2 y habría que estudiar la geométrica:

$$
A-0\cdot I=\begin{pmatrix}
a & 0 & 0 & 0 \\
a & 2 & 2 & a \\
a & 2 & 2 & a \\
a & 0 & 0 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
a & 0 & 0 & 0 \\
0 & 2 & 2 & a \\
0 & 2 & 2 & a \\
0 & 0 & 0 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
a & 0 & 0 & 0 \\
0 & 2 & 2 & a \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix},
$$

que tiene rango 2 ($a\not = 0$) y por tanto $m_g=\dim(V_{0})=4-2=2$. Así que en este caso la matriz es diagonalizable.

**Caso $a=0$**

En este caso la matriz es simétrica, y por tanto diagonalizable.

**Caso $a=4$**

Ahora tenemos que para $\lambda=0$ tanto su multiplicidad algebraica como geométrica es 2 (ha sido calculada cuando $a\not = 0$ en el primer caso) y para $\lambda=0$ la multiplicidad algebraica es 2 y debemos calcular la geométrica.

$$
A-4\cdot I=\begin{pmatrix}
0 & 0 & 0 & 0 \\
4 & -2 & 2 & 4 \\
4 & 2 & -2 & 4 \\
4 & 0 & 0 & 4
\end{pmatrix}\sim_f \begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & -1 & 1 & 0 \\
0 & 1 & -1 & 0 \\
1 & 0 & 0 & 1
\end{pmatrix},
$$

tiene rango 3, así que $m_g=\dim(V_{4})=4-3=1$. En este caso la matriz no es  diagonalizable.
</li>

<li>Para $a=0$ determinar su forma diagonal $D$ así como una matriz ortogonal $P$ de forma que $D=P^{-1}\cdot  A\cdot P=P^{t}\cdot A\cdot P$.
¿Cuál es la signatura de $A$?

Como tenemos calculados los valores propios y en este caso son $\lambda=0$, con multiplicidad algebraica $3$ y $\lambda=4,$, con multiplicidad algebraica $1$ entonces la signatura es $(1,0)$.

Para calcular la matriz ortogonal $P$ diagonalizamos por semejanza ortogonal:

$$
A-0\cdot I=\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 2 & 2 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix},
$$

y por tanto una base de $V_{0}$ es $\{(1,0,0,0),(0,1,-1,0),(0,0,0,1)\}$ que ya es ortogonal.

$$
A-4\cdot I=\begin{pmatrix}
-4 & 0 & 0 & 0 \\
0 & -2 & 2 & 0 \\
0 & 2 & -2 & 0 \\
0 & 0 & 0 & -4
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & -1 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{pmatrix},
$$ 

y por tanto una base de $V_{4}$ es $\{(0,1,1,0)\}$ que es obviamente ortogonal.

Así, una base ortonormal de $\mathbb{R}^{4}$ es 

$$
\{(1,0,0,0),(0,1/\sqrt{2},-1/\sqrt{2},0),(0,0,0,1),(0,1/\sqrt{2},1/\sqrt{2},0)\},
$$ 

y por tanto 

$$
P=\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1/\sqrt{2} & 0 & 1/\sqrt{2} \\
0 & -1/\sqrt{2} & 0 & 1/\sqrt{2} \\
0 & 0 & 1 & 0
\end{pmatrix}, \hspace{1em } D=\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 4
\end{pmatrix}.
$$

</li>
</ol>

::::
:::::

::::: {#exr-o8}

<ol type="a">
<li>En $\mathbb{R}^{8}$ consideramos dos subespacios $U$ y $W$, ambos de dimensión 5, ¿puede ser $U\cap W=0$? ¿Por qué?</li>

<li>Para la siguiente matriz determinar su signatura en función de $a$:

$$
\begin{pmatrix}
1 & 0 & 0\\
0 & 0 & a\\
0 & a & 0
\end{pmatrix}.
$$  

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>En $\mathbb{R}^{8}$ consideramos dos subespacios $U$ y $W$, ambos de dimensión 5, ¿puede ser $U\cap W=0$? ¿Por qué?

No puede ocurrir por la fórmula de las dimensiones:

$$
\dim(U) + \dim(W)= \dim(U+W) + \dim(U\cap W),
$$

así

$$
5 + 5 = \dim(U+W) + 0,
$$

y por tanto debería ser $\dim(U+W)=10$, lo que es imposible porque debe estar contenido en  $\mathbb{R}^{8}$ por lo que su dimensión es menor o igual que $8$.
</li>

<li>Determinar la signatura en función de $a$.

Pueden calcularse los valores propios:

$$
\left| \begin{array}{ccc}
1-\lambda & 0 & 0\\
0 &-\lambda & a\\
0 & a & -\lambda
\end{array}\right|= (1-\lambda)(\lambda^2 -a^2)=(1-\lambda)(\lambda -a)(\lambda +a).
$$  

Así los valores propios son $1, a, -a$ y la signatura es $(1,0)$ si $a=0$ y $(2,1)$ si $a\not =0$.
</li>
</ol>

::::
:::::

::::: {#exr-o10}

En el espacio vectorial $\mathcal{P}_4(\mathbb{R})$ de los polinomios de grado menor o igual que $4$ se consideran los subespacios:

$$
U=L(1+x^2, 1+x+x^2+x^3),\,\,\,\,\, W=L(1+x^4,x^2, 1+x+x^2).
$$

Y consideramos el producto escalar dado por:

$$
\langle p(x),q(x)\rangle=\int_{-1}^{1} p(x)\cdot q(x) dx.
$$ 

<ol type="a">
<li>Determinar bases de $U+W$ y $U\cap W$.</li>

<li>Calcular una base ortogonal de $U$.</li>

<li>Determinar la proyección sobre $U$ del vector $p(x)=1+x+x^2+x^3+x^4$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

En todo el ejercicio usaremos coordenadas respecto de la base estándar $B=\{1,x,x^2,x^3,x^4\}$.

<ol type="a">
<li>Determinar bases de $U+W$ y $U\cap W$.

En primer lugar calculamos las bases más sencillas de ambos subespacios:
$$
UP=\begin{pmatrix}
1 & 1\\
0 & 1\\
1 & 1\\
0 & 1\\
0 & 0
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0\\
0 & 1\\
1 & 0\\
0 & 1\\
0 & 0
\end{pmatrix},
$$

$$
WP=\begin{pmatrix}
1 & 0 & 1\\
0 & 0 & 1\\
0 & 1 & 1\\
0 & 0 & 0\\
1 & 0 & 0
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0\\
0 & 0 & 1\\
0 & 1 & 0\\
0 & 0 & 0\\
1 & 0 & -1
\end{pmatrix},
$$

y reuniendo ambas obtenemos un sistema de generadores de $U+W$:

$$
\begin{pmatrix}
1 & 0 &1 & 0 & 0\\
0 & 1 &0 & 0 & 1\\
1 & 0 &0 & 1 & 0\\
0 & 1 &0 & 0 & 0\\
0 & 0 &1 & 0 & -1
\end{pmatrix} \sim_c \begin{pmatrix}
1 & 0 &0 & 0 & 0\\
0 & 1 &0 & 0 & 0\\
0 & 0 &1 & 0 & 0\\
0 & 0 &0 & 1 & 0\\
0 & 0 &0 & 0 & 1
\end{pmatrix},
$$

con lo que obtenemos que $U+W= \mathcal{P}_4(\mathbb{R})$ y una base es, por ejemplo, la base estándar $B$. Usando la fórmula de las dimensiones 

$$ 
\dim(U)+ \dim(W) = \dim(U+W) + \dim(U \cap W),
$$

obtenemos que $\dim(U \cap W)=0$ y por tanto $U\cap W=0$ que no tiene base.  
</li>

<li>Calcular una base ortogonal de $U$.

Si calculamos la matriz de Gram de este producto escalar respecto de la base estándar $B$, obtenemos la matriz

$$
G=\begin{pmatrix}
2 & 0 & 2/3 & 0 & 2/5\\
0 & 2/3 & 0 & 2/5 & 0\\
2/3 & 0 & 2/5 & 0 & 2/7\\
0 & 2/5 & 0 & 2/7 & 0\\
2/5 & 0 & 2/7 & 0 & 2/9
\end{pmatrix},
$$

puesto que $\langle x^n,x^m\rangle=\int_{-1}^{1} x^{n+m}\cdot q(x) dx= \left. \frac{x^{n+m+1}}{n+m+1}\right]_{-1}^{1}$,  que es $0$ cuando $n+m+1$ es par y $\frac{2}{n+m+1}$ en otro caso.

Para la base más sencilla de $U$ obtenida en el apartado anterior se tiene que 

$$
\begin{pmatrix}
1 & 0 & 1 & 0 & 0
\end{pmatrix} G 
\begin{pmatrix}
0 \\ 1 \\ 0 \\ 1 \\ 0
\end{pmatrix}=0,
$$

con lo que dicha base es ortogonal.
</li>

<li>Determinar la proyección sobre $U$ del vector $p(x)=1+x+x^2+x^3+x^4$.

Para calcular la proyección usaremos la fórmula que hace uso de los coeficientes de Fourier respecto de la base ortogonal de $U$ obtenida en el apartado anterior: $\{u_1=(1,0,1,0,0)_B, u_2=(0,1,0,1,0)_B\}.$

$$
p_U (v)= \frac{\langle v,u_1\rangle}{\langle u_1,u_1\rangle}u_1+ \frac{\langle v,u_2\rangle}{\langle u_2,u_2\rangle}u_2,
$$

Haciendo uso de la matriz de Gram calculada en el apartado anterior tenemos:

$$
\begin{array}{l}
\langle v,u_1\rangle=464/105,\\
\langle v,u_2\rangle=184/105,\\
\langle u_1,u_1\rangle= 56/15,\\
\langle u_2,u_2\rangle= 184/105,\\
\end{array}
$$

y por tanto 

$$
p_U(v)= (58/49,1,58/49,1,0)_B.
$$

</li>
</ol>

::::
:::::

::::: {#exr-o11}

<ol type="a">
<li>Probar que si $V$ es un espacio vectorial de dimensión $n$, y $U$ y $W$ son dos subespacios distintos de $V$, ambos de dimensión $n-1$, entonces $\dim(U\cap W)=n-2$.</li>

<li>De un endomorfismo $f:\mathbb{R}^3 \longrightarrow \mathbb{R}^3$ se sabe que 
$f(1,2,3)=(1,2,3)$, $f(0,1,2)=(1,2,3)$ y $\dim(\operatorname{Im}(f))=2$. Determinar una base de $\operatorname{ker}(f)$.</li>

<li>Calcular la signatura de la matriz simétrica:

$$
A=\begin{pmatrix}
2 & 0 & -2 \\
0 & 1 & 3 \\
-2 & 3 & 2
\end{pmatrix}.
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Probar que si $V$ es un espacio vectorial de dimensión $n$, y $U$ y $W$ son dos subespacios distintos de $V$, ambos de dimensión $n-1$, entonces $\dim(U\cap W)=n-2$.

Si los dos subespacios son distintos, entonces $\dim(U+W) > \dim(U) =n-1$ y como no puede ser mayor (porque estamos en un espacio vectorial de dimensión $n$), entonces  $\dim(U+W) =n$. Usando la fórmula de las dimensiones se tiene

$$ 
\dim(U) + \dim(W) = \dim(U+W) +\dim(U\cap W),
$$

$$
n-1 + n-1 = n + (n-2),
$$
es decir, la única solución es $\dim(U\cap W)= n-2$.

</li>

<li>De un endomorfismo $f:\mathbb{R}^3 \longrightarrow \mathbb{R}^3$ se sabe que 
$f(1,2,3)=(1,2,3)$, $f(0,1,2)=(1,2,3)$ y $\dim(\operatorname{Im}(f))=2$. Determinar una base de $\operatorname{ker}(f)$.

Usando la fórmula de las dimensiones para aplicaciones lineales se tiene que la dimensión de $\operatorname{ker}=1$ (puesto que $\dim(\operatorname{ker}(f)) + \dim(\operatorname{Im}(f))= 3$) y basta con encontrar un vector no nulo cuya imagen valga $(0,0,0)$. Pero es evidente de los datos que 

$$
f(1,1,1)=f(1,2,3)-f(0,1,2)=(0,0,0),
$$

así que $(1,1,1)\in \operatorname{ker}(f)$ y así tenemos una base $\{(1,1,1)\}$.
</li>

<li>Calcular la signatura de la matriz simétrica $A$.

Diagonalizamos por congruencia:

$$
\begin{pmatrix}
2 & 0 & -2 \\
0 & 1 & 3 \\
-2 & 3 & 2
\end{pmatrix}\sim_f \begin{pmatrix}
2 & 0 & -2 \\
0 & 1 & 3 \\
0 & 3 & 0
\end{pmatrix}\sim_c \begin{pmatrix}
2 & 0 & 0 \\
0 & 1 & 3 \\
0 & 3 & 0
\end{pmatrix}\sim_f
\begin{pmatrix}
2 & 0 & 0 \\
0 & 1 & 3 \\
0 & 0 & -9
\end{pmatrix}\sim_C \begin{pmatrix}
2 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & -9
\end{pmatrix}.
$$

Así que en la diagonal hay dos elementos positivos y uno negativo, es decir, $\operatorname{sig}(A)=(2,1)$.
</li>
</ol>

::::
:::::

::::: {#exr-012}

<ol type="a">
<li>Razonar que si $A$ es una matriz cualquiera de orden $m\times n$, la matriz $A^{t} \cdot A$ es cuadrada y simétrica.</li>

<li>Calcular la matriz de cambio de base de $B$ a $B'$ siendo $B=\{ (1,1), (-1,1)\}$ y $B'=\{ (1,2), (-1,2)\}$.</li>

<li>Si $A$ es una matriz cuadrada con un único autovalor $\lambda_1=1$ y se sabe que $A$ es diagonalizable ¿qué se puede decir de $A$?</li>
<li>Calcular la signatura de 
$A= \left( \begin{array}{rr}
  a & 1 \\
  1 & -a \\
\end{array} \right)$ 
en función del parámetro $a$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Razonar que si $A$ es una matriz cualquiera de orden $m\times n$, la matriz $A^{t} \cdot A $ es cuadrada y simétrica.

Si $A$ tiene orden $n \times m$ entonces el producto $A^t \cdot A$ es de orden $m \times m$.

Para comprobar que es simétrica calculamos su traspuesta:

$$
(A^t \cdot A)^t = A^t \cdot (A^t)^t = A^t \cdot A,
$$

y como efectivamente coincide con ella, se tiene el resultado.
</li>

<li>Calcular la matriz de cambio de base de $B$ a $B'$.

LLamemos 
$P=\left( \begin{array}{rr}
1 & -1 \\
1 & 1 \\
\end{array} \right)$ que es la matriz de cambio de base de $B$ a la base canónica, y  
$Q=\left( \begin{array}{rr}
1 & -1 \\
2 & 2 \\
\end{array} \right)$ que es la matriz de cambio de base de $B'$ a la canónica. 
$$B \longrightarrow^{P}  B_c \longleftarrow^{Q} B',$$
entonces la matriz de cambio de base de $B$ a $B'$ es $Q^{-1}\cdot P$.

Calculamos $Q^{-1}$:

$$
\left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
2 & 2 & 0 & 1\\
\end{array} \right)\sim_{f} \left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
0 & 4 & -2 & 1\\
\end{array} \right)
\sim_{f} \left( \begin{array}{rr|rr}
1 & -1& 1 & 0 \\
0 & 1 & -2/4 & 1/4\\
\end{array} \right)
\sim_{f} \left( \begin{array}{rr|rr}
1 & 0& 1/2 & 1/4 \\
0 & 1 & -1/2 & 1/4\\
\end{array} \right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,-1,1,0],[2,2,0,1]])
show(A,"~",A.rref())
</script>
:::

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
\end{array} \right).
$$

</li>

<li>Si $A$ es una matriz cuadrada con un único autovalor $\lambda_1=1$ y se sabe que $A$ es diagonalizable ¿qué se puede decir de $A$?

Si $A$ es de orden digamos $n$, tiene como único valor propio $\lambda=1$ y es diagonalizable, entonces la multiplicidad 
algebraica y geométrica de $\lambda=1$ es $n$, y por tanto  $\dim(V_{ 1}) = n - \operatorname{rg}(A-I) = n$, es decir, $\operatorname{rg}(A-I)=0$ lo que indica que $A-I=0$ y por tanto $A$ es la matriz identidad.  
</li>

<li>Calcular la signatura de $A$ en función del parámetro $a$.
Diagonalizamos por congruencia la matriz:

$$
\left( \begin{array}{rr}
a & 1 \\
1 & -a \\
\end{array} \right), 
$$ 

pero para elegir el elemento en la posición $(1,1)$ como pivote necesitamos que sea $a\not = 0$, caso que estudiaremos aparte.

$$
\left( \begin{array}{rr}
a & 1 \\
1 & -a \\
\end{array} \right) \sim_{f} \left( \begin{array}{rr}
a & 1 \\
0 & -2a \\
\end{array} \right)\sim_{c} \left( \begin{array}{rr}
a & 0 \\
0 & -2a \\
\end{array} \right),
$$ 

que tiene signatura $(1,1)$.

Ahora, para $a=0$

$$
\left( \begin{array}{rr}
0 & 1 \\
1 & 0 \\
\end{array} \right) \sim_{f} \left( \begin{array}{rr}
1 & 1 \\
1 & 0 \\
\end{array} \right)\sim_{c} \left( \begin{array}{rr}
2 & 1 \\
1 & 0 \\
\end{array} \right)
\sim_{f} \left( \begin{array}{rr}
2 & 1 \\
0 & -1/2 \\
\end{array} \right)\sim_{c} \left( \begin{array}{rr}
2 & 0 \\
0 & -1/2 \\
\end{array} \right),
$$ 

con lo cual, en todos los casos $\operatorname{sig}(A)=(1,1)$.

También puede hacerse calculando los valores propios de la matriz:

$$
\left| \begin{array}{rr}
a-\lambda & 1 \\
1 & -a-\lambda \\
\end{array} \right|= (a-\lambda)(-a-\lambda)-1= \lambda^2 -1=0,
$$ 

que nos da como valores propios $\lambda=1$ y $\lambda=-1$, con lo que se tiene de nuevo $\operatorname{sig}(A)=(1,1)$.
</li>
</ol>

::::
:::::

::::: {#exr-o13}

En el espacio vectorial $\mathcal{M}_2(\mathbb{R})$ se consideran los subespacios

$$
U=\mathcal{L}\left( \left(
\begin{array}{cc}
1 & 0 \\
0& 1 \\
\end{array}
\right),
\left(
\begin{array}{cc}
1 & 0 \\
2 & a \\
\end{array}
\right) \right),
$$

$$
W=\mathcal{L}\left(
\left(
\begin{array}{cc}
a & 1 \\
2 & 0 \\
\end{array}
\right),
\left(
\begin{array}{cc}
1 & -1 \\
0 & 0 \\
\end{array}
\right) \right),
$$

y el producto escalar dado por

$$
\langle A,B\rangle=\operatorname{traza}(AB^t).
$$

<ol type="a">
<li>Calcula la base más sencilla de $U+W$ para todos los valores de $a$.</li>

<li>Calcula unas ecuaciones cartesianas de $U\cap W$ para todos los valores de $a$.</li>

<li>¿Son $U$ y $W$ complementarios para $a=1$?</li>

<li>Calcula una base ortogonal de $U$ para $a=1$.</li>

<li>Calcula una base del subespacio ortogonal a $W$ para $a=1$.</li>

<li>Calcula la proyección ortogonal sobre $W$ de la matriz
$A=\left(\begin{array}{cc}
1 & 2 \\
3 & 0 \\
\end{array}
\right)$
para $a=1$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcula la base más sencilla de $U+W$ para todos los valores de $a$.

Comenzamos calculando $U+W$ puesto que conocemos sistemas de generadores de ambos subespacios. Usaremos coordenadas respecto de la base $B_s$ habitual.

Reunimos los dos sistemas de generadores y hacemos operaciones elementales por columnas:

$$
\left(\begin{array}{cccc}
1 & 1 & a & 1\\
0 & 0 & 1 & -1\\
0 & 2 & 2 & 0\\
1 & a & 0 & 0\\
\end{array}\right)\sim_c \left(\begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 2 & 2 & 0\\
1 & a-1 & -a & -1\\
\end{array}\right)\sim_c \left(\begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 2 & 2\\
1 & 1 & a-1 & -a-1\\
\end{array}\right)\sim_c \left(\begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
1 & 1 & a-1 & -2a\\
\end{array}\right)
$$

Si $a\not = 0$, $\dim(U+W)=4$ y por tanto $U+W=\mathcal{M}_2(\mathbb{R})$ y la base más sencilla es $B_s$.

Si $a=0$ la base más sencilla son las columnas no nulas de la forma de Hermite por columnas de la matriz anterior 

$$
\left(\begin{array}{cccc}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
1 & 1 & -1 & 0\\
\end{array}\right)\sim
\left(\begin{array}{cccc}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
1 & 1 & -1/2 & 0\\
\end{array}\right)$$
$$\left\{ \left(\begin{array}{cc}
1 & 0 \\
0 & 1
\end{array}\right), \left(\begin{array}{cc}
0 & 1 \\
0 & 1
\end{array}\right),\left(\begin{array}{cc}
0 & 0 \\
1 & -1/2
\end{array}\right) \right\}.
$$ 
</li>

<li>Calcula unas ecuaciones cartesianas de $U\cap W$ para todos los valores de $a$.

Para calcular la intersección utilizamos en primer lugar la fórmula de las dimensiones 

$$
\dim(U)+ \dim(W)=\dim(U+W)+\dim(U\cap W).
$$

Como $\dim(U)+ \dim(W)=2+2=4$ (es inmediato de los datos), tenemos que para $a\not = 0$ $\dim(U\cap W)=0$ mientras que para $a=0$ $\dim(U\cap W)=1$.

Por tanto para $a\not = 0$ las ecuaciones cartesianas de $U\cap W$ son
\begin{equation}
U\cap W \equiv \left\{ \begin{array}{l}
x=0,\\
y=0,\\
z=0,\\
t=0.
\end{array}\right.
\end{equation}

Para $a=0$ calculamos unas cartesianas de $U$ y unas de $W$ y las reunimos. Para ello comenzamos desde la base más sencilla de cada subespacio para escribir las paramétricas y deducir después las cartesianas.
Para $U$:

$$
\left(\begin{array}{cc}
1 & 1 \\
0 & 0 \\
0 & 2 \\
1 & 0 \\
\end{array}\right)\sim_c \left(\begin{array}{cc}
1 & 0 \\
0 & 0 \\
0 & 2 \\
1 & -1 \\
\end{array}\right)\sim_c\left(\begin{array}{cc}
1 & 0 \\
0 & 0 \\
0 & 1 \\
1 & -1/2 \\
\end{array}\right).
$$

Luego unas paramétricas son 

$$
U=\left\{ \begin{array}{l}
x=\lambda_1,\\
y=0,\\
z=\lambda_2,\\
t=\lambda_1-\frac{1}{2}\lambda_2.
\end{array}\right.  \text{ Y así las cartesianas son } 
\left\{\begin{array}{l}
y=0,\\
2x-z-2t=0.
\end{array}\right.
$$

Para $W$:

$$\left(\begin{array}{cc}
0 & 1 \\
1 & -1 \\
2 & 0 \\
0 & 0 \\
\end{array}\right)\sim_c \left(\begin{array}{cc}
1 & 0 \\
0 & 1 \\
2 & 2 \\
0 & 0 \\
\end{array}\right).
$$

Luego unas paramétricas son 

$$
W=\left\{ \begin{array}{l}
x=\lambda_1,\\
y=\lambda_2,\\
z=2\lambda_1+2\lambda_2,\\
t=0.
\end{array}\right.  \text{ Y así las cartesianas son } 
\left\{\begin{array}{l}
2x+2y-z=0,\\
t=0.
\end{array}\right.
$$

Entonces

$$
U\cap W=\left\{ \begin{array}{l}
y=0,\\
2x-z-2t=0,\\
2x+2y-z=0,\\
t=0,
\end{array}\right. \sim_f  \left\{\begin{array}{l}
y=0,\\
2x-z=0.\\
t=0,
\end{array}\right.
$$

</li>

<li>¿Son $U$ y $W$ complementarios para $a=1$?

Sí, de hecho para $a\not = 0$, puesto que $U+W=\mathcal{M}_2(\mathbb{R})$ y $U\cap W=\{0\}$.
</li>

<li>Calcula una base ortogonal de $U$ para $a=1$.

Para calcular una base ortogonal calculemos en primer lugar una base de $U$ para $a=1$:

$$
\left(\begin{array}{cc}
1 & 1 \\
0 & 0 \\
0 & 2 \\
1 & 1 \\
\end{array}\right)\sim_c \left(\begin{array}{cc}
1 & 0 \\
0 & 0 \\
0 & 1 \\
1 & 0 \\
\end{array}\right).
$$

Ahora usamos el algoritmo de Gram-Schmidt para calcular una base ortogonal a partir de estos dos vectores

$$
u_1=\begin{pmatrix}
1 & 0\\
0 & 1
\end{pmatrix}, u_2=\begin{pmatrix}
0 & 0\\
1 & 0
\end{pmatrix}.
$$

Luego

$$e_1= \begin{pmatrix}
1 & 0\\
0 & 1
\end{pmatrix}, e_2=\begin{pmatrix}
0 & 0\\
1 & 0
\end{pmatrix}+\lambda_{21}\begin{pmatrix}
1 & 0\\
0 & 1
\end{pmatrix}.
$$

Calculamos 

$$
\lambda_{21}=\frac{-\langle u_{2},e_{1}\rangle}{||e_{1}||^2}.
$$

Empezamos por el numerador:
$$
\biggl\langle\begin{pmatrix}
0 & 0\\
1 & 0
\end{pmatrix}, \begin{pmatrix}
1 & 0\\
0 & 1
\end{pmatrix}\biggr\rangle=\operatorname{traza}\left(\begin{pmatrix}
0 & 0\\
1 & 0
\end{pmatrix}\cdot \begin{pmatrix}
1 & 0\\
0 & 1
\end{pmatrix}\right)= \operatorname{traza}\begin{pmatrix}
0 & 0\\
1 & 0
\end{pmatrix}=0.
$$

Luego $e_2=u_2$ y la base de partida ya es ortogonal.
También puede calcularse la matriz de Gram del producto escalar y usarla para hacer los productos utilizando coordenadas.
</li>

<li>Calcula una base del subespacio ortogonal a $W$ para $a=1$.

Para calcular las cartesianas del ortogonal de $W$ partimos de una base de $W$ ($a=1$):

$$
\left(\begin{array}{cc}
1 & 1 \\
1 & -1 \\
2 & 0 \\
0 & 0 \\
\end{array}\right)\sim_c \left(\begin{array}{cc}
1 & 0 \\
-1 & 2 \\
0 & 2 \\
0 & 0 \\
\end{array}\right) \sim_c \left(\begin{array}{cc}
1 & 0 \\
0 & 1 \\
1 & 1 \\
0 & 0 \\
\end{array}\right),
$$

y para cada uno imponemos la condición de que una matriz genérica sea ortogonal:
 
$$
\biggl\langle\begin{pmatrix}
1 & 0\\
1 & 0
\end{pmatrix}, \begin{pmatrix}
x & y\\
z & t
\end{pmatrix}\biggr\rangle=\operatorname{traza}\left(\begin{pmatrix}
1 & 0\\
1 & 0
\end{pmatrix}\cdot \begin{pmatrix}
x & z\\
y & t
\end{pmatrix}\right)= \operatorname{traza}\begin{pmatrix}
x & z\\
x & z
\end{pmatrix}=x+z=0,
$$

$$
\biggl\langle\begin{pmatrix}
0 & 1\\
1 & 0
\end{pmatrix}, \begin{pmatrix}
x & y\\
z & t
\end{pmatrix}\biggr\rangle=\operatorname{traza}\left(\begin{pmatrix}
0 & 1\\
1 & 0
\end{pmatrix}\cdot \begin{pmatrix}
x & z\\
y & t
\end{pmatrix}\right)= \operatorname{traza}\begin{pmatrix}
y & t\\
x & z
\end{pmatrix}=y+z=0.
$$

Luego 

$$
W^{\perp}\equiv \left\{\begin{array}{l}
x+z=0,\\
y+z=0.
\end{array}\right.
$$

</li>
<li>Calcula la proyección ortogonal sobre $W$ de la matriz $A$.

Calculamos unas cartesianas de $W$ para $a=1$ partiendo de la base más sencilla que ya tenemos del apartado anterior, primero poniendo las paramétricas:

$$
W=\left\{ \begin{array}{l}
x=\lambda_1,\\
y=\lambda_2,\\
z=\lambda_1+\lambda_2,\\
t=0.
\end{array}\right.  \text{ que nos dan las cartesianas } 
\left\{\begin{array}{l}
x+y-z=0,\\
t=0.
\end{array}\right.
$$

La matriz del enunciado cumple estas cartesianas, luego está en $W$.
Entonces, 

$$
p_W\left(\begin{pmatrix}
1 & 2\\
3 & 0
\end{pmatrix}\right)=\begin{pmatrix}
1 & 2\\
3 & 0
\end{pmatrix}.
$$

También puede emplearse cualquier otro método (descomponer en dos vectores uno de $W$ y otro de $W^{\perp}$, o usar coeficientes de Fourier).
</li>
</ol>

::::
:::::

::::: {#exr-o14}

De una aplicación lineal $f : (\mathbb{Z}_5)^3 \to (\mathbb{Z}_5)^3$ sabemos que:

<ul>
<li> $(2,3,1) \in N(f)$ </li>
<li> $(1,2,4)$ es vector propio del valor propio $2$ </li>
<li> $f(1,1,1)=(4,0,3)$ </li>
</ul>

<ol type="a">
<li> Calcula la matriz de $f$ en la base canónica.</li>
<li> Calcula las ecuaciones cartesianas del subespacio $\mathrm{Im}(f)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Sabemos que:
$$
f(2,3,1)=(0,0,0), \quad f(1,2,4)=(2,4,3), \quad f(1,1,1)=(4,0,3).
$$

La base
$$
B=\{(2,3,1), (1,2,4), (1,1,1)\}
$$
es una base de $(\mathbb{Z}_5)^3$, y queda totalmente determinada la aplicación $f$.

Así:
$$
M_{B,B_c}(f) =
\begin{pmatrix}
0 & 2 & 4 \\
0 & 4 & 0 \\
0 & 3 & 3
\end{pmatrix}.
$$

Para obtener $M_{B_c}(f)$ usamos:
$$
M_{B_c}(f) = M_{B,B_c}(f)\cdot M_{B_c \to B}.
$$

Calculando $M_{B_c \to B}=(M_{B \to B_c})^{-1}$, llegamos a:
$$
M_{B_c \to B} =
\begin{pmatrix}
2 & 2 & 1 \\
2 & 4 & 4 \\
0 & 2 & 4
\end{pmatrix}.
$$

Entonces:
$$
M_{B_c}(f) =
\begin{pmatrix}
0 & 2 & 4 \\
0 & 4 & 0 \\
0 & 3 & 3
\end{pmatrix}
\begin{pmatrix}
2 & 2 & 1 \\
2 & 4 & 4 \\
0 & 2 & 4
\end{pmatrix}
=
\begin{pmatrix}
4 & 1 & 4 \\
3 & 1 & 1 \\
1 & 3 & 4
\end{pmatrix}.
$$

</li>
<li>Partimos de un sistema de generadores con las imágenes de los vectores de $B$:
$$
\{(2,4,3),(4,0,3)\}.
$$

Tras reducción:
$$
\begin{pmatrix}
1 & 0 & 2 \\
0 & 1 & 1
\end{pmatrix},
$$

las ecuaciones paramétricas son:
$$
x=a, \quad y=b, \quad z=2a+b.
$$

De aquí obtenemos la ecuación cartesiana:
$$
z=2x+y \quad \Longleftrightarrow \quad 2x+y+4z=0 \ \ (\text{en } \mathbb{Z}_5).
$$

</li>
</ol>

::::
:::::