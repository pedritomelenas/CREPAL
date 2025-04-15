---
title: Diagonalización por semejanza
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

<!-- por ahora todos medios, cambiar luego
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_basico" value="basicoon" checked onclick="mostrar();"> Básicos </button> 
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_medio" value="medioon" checked onclick="mostrar();"> Dificultad media </button>
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_avanzado" value="avanzadon" checked onclick="mostrar();"> Avanzados. </button>
-->

::::: {#exr-1 .medio}

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

::::: {#exr-2 .cuerpo_finito-medio}

Se considera la matriz sobre $\mathbb{Z}_5$: 

$$
A=\begin{pmatrix}
1 & 2 & 0\\
2 & 1 & 0\\
1 & 4 & 2
\end{pmatrix}.
$$

<ol type="a">
<li>Diagonaliza la matriz $A$.</li>
<li>Calcula la matriz $A^{123}$.</li>
<li>Diagonaliza la matriz $A^{-1}$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li>Diagonalizar la matriz $A$.

En primer lugar calculamos el polinomio característico para determinar los valores propios y sus multiplicidades algebraicas:

$$
|A-\lambda I|=\begin{vmatrix}
1-\lambda & 2 & 0\\
2 & 1-\lambda & 0\\
1 & 4 & 2-\lambda
\end{vmatrix}=(2-\lambda)\begin{vmatrix}
1-\lambda & 2 \\
2 & 1-\lambda \\
\end{vmatrix}= (2- \lambda)[(1-\lambda)^2-4]=(2-\lambda)(\lambda^2+3\lambda+2).
$$

Las raíces de $\lambda^2+3\lambda+2$ en $\mathbb{Z}_5$ son $3$ y $4$, que son simples, luego los valores propios son $2$, $3$, $4$ con multiplicidades algebraicas $1$ para cada uno.


Ahora debemos calcular cada uno de los subespacios propios.

**$V_{\lambda=2}$**
 
$$
A-2I=\begin{pmatrix}
4 & 2 & 0\\
2 & 4 & 0\\
1 & 4 & 0
\end{pmatrix}.
$$

Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=2}$ a partir de $(A-2I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:

$$
A-2I=\begin{pmatrix}
4 & 2 & 0\\
2 & 4 & 0\\
1 & 4 & 0
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 4 & 0\\
4 & 2 & 0\\
2 & 4 & 0\\
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 0\\
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[4,2,0],[2,4,0],[1,4,0]])
show(A,"~",A.rref())
</script>
:::

Entonces nos quedan las cartesianas

$$
\boxed{\begin{array}{l} x=0,\\ y=0. \end{array} }
$$

Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 1 y una base es $\{(0,0,1)\}.$

**$V_{\lambda=3}$**
 
$$
A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}.
$$

Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=3}$ a partir de $(A-3I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:

$$
A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 4 & 0\\
0 & 0 & 1\\
0 & 0 & 0\\
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[3,2,0],[2,3,0],[1,4,4]])
show(A,"~",A.rref())
</script>
:::

Entonces nos quedan las cartesianas

$$
\boxed{\begin{array}{l} x+4y=0,\\ z=0. \end{array} }
$$

Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=3}$) es 1 y una base es $\{(1,1,0)\}.$

**$V_{\lambda=4}$**
 
$$
A-4I=\begin{pmatrix}
2 & 2 & 0\\
2 & 2 & 0\\
1 & 4 & 3
\end{pmatrix}.
$$

Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=3}$ a partir de $(A-4I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:

$$
A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 0 & 4\\
0 & 1 & 1\\
0 & 0 & 0\\
\end{pmatrix}.
$$

Entonces nos quedan las cartesianas

$$
\boxed{\begin{array}{l} x+4z=0,\\ y=0. \end{array} }
$$

Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=3}$) es 1 y una base es $\{(1,4,1)\}.$

Por último, una vez comprobada que la multiplicidad algebraica y geométrica coinciden para cada valor propio escribimos las matriz diagonal $D$ (con los valores propios en la diagonal) y la matriz $P$ (con los vectores propios por columnas) cuidando de que el orden en el que se escriben los valores propios en $D$ corresponda con el orden de los vectores propios asociados en $P$:

$$
D=\begin{pmatrix}
2 & 0 & 0\\
0 & 3 & 0\\
0 & 0 & 4
\end{pmatrix}, \hspace{2cm}  P=\begin{pmatrix}
0 & 1 & 1\\
0 & 1 & 4\\
1 & 0 & 1
\end{pmatrix}.
$$
</li>

<li>Calcular la matriz $A^{123}$.

Para calcular $A^{123}$ utilizamos la diagonalización que acabamos de realizar para la que se cumple $D=P^{-1}AP.$
Despejando $A$ tendremos $$A=PDP^{-1},$$ y podemos observar que en el producto

$$
A^{123}= (PDP^{-1})(PDP^{-1})\cdots (PDP^{-1})
$$

los productos $P^{-1}P=I$, y por tanto queda

$$
A^{123}=PD^{123}P^{-1}.
$$

Además el cálculo de las potencias de una matriz diagonal es muy sencillo, puesto que consiste en elevar a dicha potencia cada uno de los elementos de la diagonal, es decir:

$$
D^{123}=\begin{pmatrix}
2^{123} & 0 & 0\\
0 & 3^{123} & 0\\
0 & 0 & 4^{123}
\end{pmatrix}.
$$

Se trata entonces de calcular dichas potencias en $\mathbb{Z}_5$, para lo que utilizaremos el Teorema pequeño de Fermat: $a^4=1$ en $\mathbb{Z}_5.$

Como $123=30\cdot 4+3$, entonces $2^{123}=(2^4)^30\cdot 2^3=2^3=3.$ Por otro lado, $3^{123}=(3^4)^30\cdot 3^3=3^3=2$ y $4^{123}=(4^4)^30\cdot 4^3=4^3=4.$

Así que 

$$
D^{123}=\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 4
\end{pmatrix}.
$$

Solo queda calcular $P^{-1}$ y realizar el producto $PD^{123}P^{-1}.$

$$
\begin{align*}
(P|I) & =\left(\begin{array}{ccc|ccc}
0 & 1 & 1 & 1 & 0 & 0\\
0 & 1 & 4 & 0 & 1 & 0\\
1 & 0 & 1 & 0 & 0 & 1
\end{array}\right)\sim_f \left(\begin{array}{ccc|ccc}
1 & 0 & 1 & 0 & 0 & 1\\
0 & 1 & 1 & 1 & 0 & 0\\
0 & 1 & 4 & 0 & 1 & 0\\
\end{array}\right)\sim_f  \left(\begin{array}{ccc|ccc}
1 & 0 & 1 & 0 & 0 & 1\\
0 & 1 & 1 & 1 & 0 & 0\\
0 & 0 & 3 & 4 & 1 & 0\\
\end{array}\right) \\ &
\sim_f  \left(\begin{array}{ccc|ccc}
1 & 0 & 1 & 0 & 0 & 1\\
0 & 1 & 1 & 1 & 0 & 0\\
0 & 0 & 1 & 3 & 2 & 0\\
\end{array}\right)\sim_f \left(\begin{array}{ccc|ccc}
1 & 0 & 0 & 2 & 3 & 1\\
0 & 1 & 0 & 3 & 3 & 0\\
0 & 0 & 1 & 3 & 2 & 0\\
\end{array}\right)=(I|P^{-1}).
\end{align*}
$$

Por último:

$$
A^{123}=\begin{pmatrix}
0 & 1 & 1\\
0 & 1 & 4\\
1 & 0 & 1
\end{pmatrix}\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 4
\end{pmatrix}\begin{pmatrix}
2 & 3 & 1\\
3 & 3 & 0\\
3 & 2 & 0
\end{pmatrix}=\begin{pmatrix}
3 & 4 & 0\\
4 & 3 & 0\\
3 & 2 & 3
\end{pmatrix}.
$$

</li>

<li>Diagonalizar la matriz $A^{-1}$.

Para diagonalizar $A^{-1}$ basta observar que como $D=P^{-1}AP$ entonces $D^{-1}=P^{-1}A^{-1}P$, luego la matriz diagonal será $D^{-1}$:

$$
D^{-1}=\begin{pmatrix}
2^{-1} & 0 & 0\\
0 & 3^{-1} & 0\\
0 & 0 & 4^{-1}
\end{pmatrix}=\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 4
\end{pmatrix},
$$ 

y la matriz de paso es la misma, $P$.
</li>
</ol>

::::
:::::

::::: {#exr-3 .medio}

Sea la matriz 
$$
A=\left(\begin{array}{cccc}
 1 & a & 2 & -1\\
0 & 1 & 3 & 4\\
 0 & 0 & 2 & b\\
 0 & 0 & 0 & 2\\
\end{array}
\right).
$$

Estudiar para qué valores de los parámetros $a$ y $b$ es diagonalizable.

:::: {.callout collapse="true" title="Solución"}

Necesitamos calcular los valores propios y sus multiplicidades algebraica y geométrica.
Los valores propios son fáciles:

$$
|A-\lambda I|=\left|\begin{array}{cccc}
 1-\lambda & a & 2 & -1\\
0 & 1-\lambda & 3 & 4\\
 0 & 0 & 2-\lambda & b\\
 0 & 0 & 0 & 2-\lambda\\
\end{array}
\right|=(1-\lambda)^2(2-\lambda)^2.
$$

Los valores propios son $1$ y $2$ con multiplicidades algebraicas $2$ para cada uno.

**$V_{\lambda=1}$**

$$
A-I=\left(\begin{array}{cccc}
 0 & a & 2 & -1\\
0 & 0 & 3 & 4\\
 0 & 0 & 1 & b\\
 0 & 0 & 0 & 1\\
\end{array}
\right).
$$

Para que tenga rango dos (y por tanto la dimensión de $V_{\lambda=1}$ sea también dos) debe ser $a=0.$

**$V_{\lambda=2}$**

$$
A-2I=\left(\begin{array}{cccc}
 -1 & a & 2 & -1\\
0 & -1 & 3 & 4\\
 0 & 0 & 0 & b\\
 0 & 0 & 0 & 0\\
\end{array}
\right).
$$

Para que tenga rango dos (y por tanto la dimensión de $V_{\lambda=2}$ sea también dos) debe ser $b=0.$

Concluimos que solo es diagonalizable en el caso $a=b=0.$

::::
:::::

::::: {#exr-4 .cuerpo_finito}

Sea $f:(\mathbb{Z}_{13})^3 \longrightarrow  (\mathbb{Z}_{13})^3$ la aplicación lineal dada
por:

$$
f(x,y,z)=(7x+12y+4z, x+6y+3z, 5x+6y+12z).
$$

<ol type="a">
<li>Halla la matriz de $f$ en la base canónica (llamémosla $A$).</li>
<li>Estudia si $f$ es diagonalizable, y en caso afirmativo halla una base de vectores propios.</li>
<li>Calcula $A^{2431}$.</li>
<li>Calcula $f^{2432}(1,2,3)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Hallar la matriz de $f$ en la base canónica.

Para calcular la matriz asociada calculamos las imágenes de los vectores de la base canónica:

$$
\begin{array}{l}
f(1,0,0)=(7,1,5),\\
f(0,1,0)=(12,6,6),\\
f(0,0,1)=(4,3,12).
\end{array}
$$

Podemos, por simplificar cálculos posteriores, sustituir que $12=-1$ en $\mathbb{Z}_{13}$, y nos queda la matriz

$$
A=M_{B_c}(f)=\begin{pmatrix}
7 & -1 & 4\\
1 & 6 & 3\\
5 & 6 &-1
\end{pmatrix}.
$$

</li>

<li>Estudiar si $f$ es diagonalizable, y hallar una base de vectores propios.

Calculamos los valores propios, mediante la ecuación característica:

$$
\begin{align*}
\left| \begin{array}{ccc}
7-\lambda & -1 & 4\\
1 & 6-\lambda & 3\\
5 & 6 &-1-\lambda
\end{array}\right| & 
=(7-\lambda)(6-\lambda)(-1-\lambda)-2-2-7(6-\lambda)-5(7-\lambda)+(-1-\lambda)\\ &
=-\lambda^3-\lambda^2+8\lambda -7.
\end{align*}
$$


Calculamos las raíces de este polinomio (lo cual es laborioso) y  obtenemos que son $\lambda=5$ con multiplicidad algebraica 1 y $\lambda=-3(=10)$ con multiplicidad algebraica 2.

Debemos calcular la multiplicidad geométrica de $\lambda=-3$ para poder decidir si es o no diagonalizable. Para ello calculamos el subespacio propio correspondiente:

$$
(A+3I)=\begin{pmatrix}
10 & -1 & 4\\
1 & 9 & 3\\
5 & 6 & 2
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 9 & 3\\
0 & 0 & 0\\
0 & 0 & 0\\
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(13),[[10,-1,4],[1,9,3],[5,6,2]])
show(A,"~",A.rref())
</script>
:::

Luego nos queda una única ecuación cartesiana que es $x+9y+3z=0$ y por tanto la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 2, así que la matriz es diagonalizable.
Calculamos una base de  $V_{\lambda=-3}$:

$$
\{ (4,1,0),(10,0,1) \}.
$$

Necesitamos también una base de $V_{\lambda=5}$:

$$
(A-5I)=\begin{pmatrix}
2 & -1 & 4\\
1 & 1 & 3\\
5 & 6 & -6
\end{pmatrix}\sim_f 
\begin{pmatrix}
1 & 0 & -2\\
0 & 1 & 5\\
0 & 0 & 0\\
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(13),[[2,-1,4],[1,1,3],[5,6,-6]])
show(A,"~",A.rref())
</script>
:::

Nos quedan las ecuaciones $V_{\lambda=5}\equiv \boxed{\begin{array}{l}
x-2z=0,\\
y+5z=0.\end{array} }$ y una base es $\{(2,-5,1)\}$.

Luego la solución al problema de diagonalización es:

$$
D=\left(\begin{array}{ccc}
5 & 0 & 0\\
0 & 10 & 0\\
0 & 0 &  10
\end{array}\right)=\left(\begin{array}{ccc}
5 & 0 & 0\\
0 & -3 & 0\\
0 & 0 & -3
\end{array}\right), \hspace{1em}  P=\left(\begin{array}{ccc}
2 & 4 & 10\\
-5 & 1 & 0\\
1 & 0 &  1
\end{array}\right).
$$

</li>

<li>Calcular $A^{2431}$.

Para calcular la potencia pedida utilizamos la diagonalización:

$$
D=P^{-1}AP \text{ o bien }  A=PDP^{-1},
$$

que nos permite deducir que

$$
A^{2431}=PD^{2431}P^{-1}.
$$

Calculamos 

$$
D^{2431}=\left(\begin{array}{ccc}
5^{2431} & 0 & 0\\
0 & 10^{2431} & 0\\
0 & 0 &  10^{2431}
\end{array}\right),
$$

para lo que hemos realizado los cálculos $5^{703}, 10^{703}$ en $\mathbb{Z}_{13}$ mediante el Teorema pequeño de Fermat: $a^{12}=1$ en $\mathbb{Z}_{13}$. Obtenemos así $5^{2431}=5^{202\cdot 12+7}=5^7=8$ y además $10^{2431}=10^{202\cdot 12+7}=10^7= 10$. Y obtenemos

$$
D^{2431}=\left(\begin{array}{ccc}
8 & 0 & 0\\
0 & 10 & 0\\
0 & 0 &  10
\end{array}\right).
$$

Necesitamos también $P^{-1}$:

$$
\begin{align*}
(P|I) & =\left(\begin{array}{ccc|ccc}
2 & 4 & 10 & 1 & 0 & 0\\
-5 & 1 & 0 & 0 & 1 & 0\\
1 & 0 &  1 & 0 & 0 & 1
\end{array}\right)\sim_f\left(\begin{array}{ccc|ccc}
1 & 0 &  1 & 0 & 0 & 1\\
0 & 4 & 8 & 1 & 0 & -2\\
0 & 1 & 5 & 0 & 1 & 5\\
\end{array}\right) \\ &
\sim_f \left(\begin{array}{ccc|ccc}
1 & 0 &  1 & 0 & 0 & 1\\
0 & 1 & 5 & 0 & 1 & 5\\
0 & 0 & 1 & 1 & -4 & 4\\
\end{array}\right)\sim_f
\left(\begin{array}{ccc|ccc}
1 & 0 &  0 & -1 & 4 & -3\\
0 & 1 & 0 & -5 & -5 & -2\\
0 & 0 & 1 & 1 & -4 & 4\\
\end{array}\right).\end{align*}
$$

Luego 

$$
A^{2431}=PD^{2431}P^{-1}=\left(\begin{array}{ccc}
2 & 4 & 10\\
-5 & 1 & 0\\
1 & 0 &  1
\end{array}\right)\left(\begin{array}{ccc}
8 & 0 & 0\\
0 & 10 & 0\\
0 & 0 &  10
\end{array}\right)\left(\begin{array}{ccc}
 -1 & 4 & -3\\
-5 & -5 & -2\\
 1 & -4 & 4\\
\end{array}\right).
$$
</li>

<li>Calcula $f^{2432}(1,2,3)$.

Basta realizar la operación $f^{2432}(1,2,3)=A^{2432}(1,2,3)^T=A^{2431}A(1,2,3)^T$.</li>

</ol>

::::
:::::


::::: {#exr-5 .cuerpo_finito-medio}

Sea $f:(\mathbb{Z}_{5})^3\longrightarrow (\mathbb{Z}_{5})^3$ la
aplicación lineal dada por:

$$
f(x,y,z)=(4z,2x+2y+z,x)
$$

<ol type="a">
<li>Halla la matriz de $f$ en la base canónica (llamémosla $A$).</li>
<li>Estudia si $f$ es diagonalizable, y en caso afirmativo halla una base de vectores propios.</li>
<li>Calcula $A^{703}$.</li>
<li>Halla $f^{704}(1,2,3)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Hallar la matriz de $f$ en la base canónica.

Calculamos las imágenes de los vectores de la base canónica:

$$
\begin{array}{l}
f(1,0,0)=(0,2,1),\\
f(0,1,0)=(0,2,0),\\
f(0,0,1)=(4,1,0).
\end{array}$$
Así la matriz es 
$$A=M_{B_c}(f)=
\left(\begin{array}{ccc}
0 & 0 & 4\\
2 & 2 & 1\\
 1 & 0 & 0\\
\end{array}\right).
$$
</li>

<li>Estudiar si $f$ es diagonalizable y hallar una base de vectores propios.

Calculamos los valores propios y sus multiplicidades algebraica y geométrica:

$$
|A-\lambda I|=\left| \begin{array}{ccc}
-\lambda & 0 & 4\\
2 & 2-\lambda & 1\\
 1 & 0 & -\lambda\\
\end{array}\right|=(2-\lambda)[(-\lambda)^2-4)]=(2-\lambda)(\lambda^2-4).
$$

Las raíces de $\lambda^2-4=0$ son $\lambda=2$ y $\lambda=3(=-2)$ en $\mathbb{Z}_5$. Así el valor propio $\lambda=2$ tiene multiplicidad algebraica 2 y $\lambda=3$ tiene multiplicidad algebraica 1.

Calculamos $V_{\lambda=2}$:

$$
A-2I =
\left(\begin{array}{ccc}
-2 & 0 & 4\\
2 & 0 & 1\\
 1 & 0 & -2\\
\end{array}\right)\sim_f \left(\begin{array}{ccc}
 1 & 0 & -2\\
0 & 0 & 0\\
0 & 0 & 0\\
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[-2,0,4],[2,0,1],[1,0,-2]])
show(A,"~",A.rref())
</script>
:::

Luego nos queda una única ecuación cartesiana que es $x-2z=0$ y por tanto la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 2, así que la matriz es diagonalizable.

Calculamos una base de  $V_{\lambda=2}$:
$\{ (0,1,0),(2,0,1) \}$.

Nos queda calcular una base de $V_{\lambda=3}$:

$$
A-3I=
\left(\begin{array}{rrr}
-3 & 0 & 4\\
2 & -1 & 1\\
 1 & 0 & -3\\
\end{array}\right)\sim_f 
\left(\begin{array}{rrr}
 1 & 0 & -3\\
 0 & 1 & 3\\
0 & 0 & 0\\
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[-3,0,4],[2,-1,1],[1,0,-3]])
show(A,"~",A.rref())
</script>
:::

Nos quedan las ecuaciones $V_{\lambda=3}\equiv \boxed{\begin{array}{l}
x-3z=0,\\
y+3z=0.\end{array} }$. Además una base es $\{(3,2,1)\}$.

Luego la solución al problema de diagonalización es:

$$
D=\left(\begin{array}{rrr}
2 & 0 & 0\\
0 & 2 & 0\\
 0 & 0 & 3\\
\end{array}\right), \hspace{1em}
 P= \left(\begin{array}{rrr}
0 & 2 & 3\\
1 & 0 & 2\\
 0 & 1 & 1\\
\end{array}\right).
$$
</li>

<li>Calcular $A^{703}$.

Para calcular la potencia pedida utilizamos la diagonalización:

$$
D=P^{-1}AP \text{ o bien }  A=PDP^{-1},
$$

que nos permite deducir que

$$
A^{703}=PD^{703}P^{-1}.
$$

Calculamos 

$$
D^{703}=\left(\begin{array}{ccc}
2^{703} & 0 & 0\\
0 & 2^{703} & 0\\
0 & 0 &  3^{703}
\end{array}\right),
$$

para lo que realizamos los cálculos en $\mathbb{Z}_5$, mediante el uso del Teorema pequeño de Fermat: $2^{703}=2^{175\cdot 4+3}=2^3= 3$, y también $3^{703}=3^{175\cdot 4+3}=3^3= 2$. Obtenemos así:

$$
D^{703}=\left(\begin{array}{ccc}
3 & 0 & 0\\
0 & 3 & 0\\
0 & 0 &  2
\end{array}\right).
$$

También necesitamos calcular $P^{-1}$:

$$
(P|I)= \left(\begin{array}{ccc|ccc}
0 & 2 & 3 & 1 & 0 & 0\\
1 & 0 & 2 & 0 & 1 & 0\\
 0 & 1 & 1 & 0 & 0 & 1\\
\end{array}\right)\sim_f \left(\begin{array}{ccc|ccc}
1 & 0 & 0 & 3 & 1 & 4\\
0 & 1 & 0 & 4 & 0 & 3\\
 0 & 0 & 1 & 1 & 0 & 3\\
\end{array}\right)=(I|P^{-1}).
$$

Luego 

$$
A^{703}=PD^{703}P^{-1}=\left(\begin{array}{rrr}
0 & 2 & 3\\
1 & 0 & 2\\
 0 & 1 & 1\\
\end{array}\right)\left(\begin{array}{ccc}
3 & 0 & 0\\
0 & 3 & 0\\
0 & 0 &  2
\end{array}\right)\left(\begin{array}{ccc}
 3 & 1 & 4\\
 4 & 0 & 3\\
1 & 0 & 3\\
\end{array}\right)=\left(\begin{array}{rrr}
0 & 0 & 1\\
0 & 3 & 4\\
 4 & 0 & 0\\
\end{array}\right).
$$
</li>

<li>Hallar $f^{703}(1,2,3)$.

Basta realizar la operación 

$$
f^{703}(1,2,3)=A^{703}(1,2,3)^T=
\left(\begin{array}{rrr}
0 & 0 & 1\\
0 & 3 & 4\\
 4 & 0 & 0\\
\end{array}\right)
\left(\begin{array}{rrr}
1\\
2\\
3\\
\end{array}\right)=
\left(\begin{array}{rrr}
3\\
18\\
4\\
\end{array}\right).
$$
</li>

</ol>
::::
:::::

::::: {#exr-6 .medio}

Se considera la matriz:

$$
A=\begin{pmatrix}
a & 1 & 0 & 0 \\
0 & b & 0 & 0 \\
0 & 0 & a & 1 \\
0 & 0 & 0 & b
\end{pmatrix}.
$$

<ol type="a">
<li>Estudiar qué condición han de cumplir los parámetros $a$ y $b$ para que $A$ sea diagonalizable.</li>
<li>Para los valores $a=1$, $b=-1$ determinar su forma diagonal $D$ y una matriz de paso $P$ de forma que $D=P^{-1}\cdot A \cdot P$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Estudiar qué condición han de cumplir los parámetros $a$ y $b$ para que $A$ sea diagonalizable.

En primer lugar calculamos los valores propios y sus multiplicidades algebraicas

$$
|A-\lambda I|=\left| \begin{array}{cccc}
a-\lambda & 1 & 0 & 0 \\
0 & b-\lambda & 0 & 0 \\
0 & 0 & a-\lambda & 1 \\
0 & 0 & 0 & b-\lambda
\end{array}\right|= (a-\lambda)^2 (b-\lambda)^2.
$$

Si $a=b$, hay un solo valor propio $\lambda=a$ con multiplicidad algebraica cuatro. Calculamos su multiplicidad geométrica:

$$
V_{\lambda=a}\equiv \begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{pmatrix}\begin{pmatrix}
x\\ y\\ z\\t
\end{pmatrix}= \begin{pmatrix}
0 \\ 0 \\0 \\0
\end{pmatrix}.
$$

Nos da las ecuaciones $y=0; t=0$ y por tanto tiene dimensión dos, así que como no coincide con la multiplicidad algebraica, entonces no es diagonalizable.

Si $a\not =b$, hay dos valores propios $\lambda=a$ con multiplicidad algebraica dos y $\lambda=b$ también con multiplicidad algebraica dos.

Calculamos su multiplicidad geométrica:

$$
V_{\lambda=a}\equiv \begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & b-a & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & b-a
\end{pmatrix}\begin{pmatrix}
x\\ y\\ z\\ t
\end{pmatrix}= \begin{pmatrix}
0 \\ 0 \\0 \\0
\end{pmatrix}.
$$

Nos da las ecuaciones $y=0$, $t=0$ y por tanto tiene dimensión dos, así que coincide con la multiplicidad algebraica.

$$
V_{\lambda=b}\equiv \begin{pmatrix}
 a-b & 1 & 0 & 0 \\
 0 & 0 & 0 & 0 \\
 0 & 0 & a-b & 1 \\
 0 & 0 & 0 & 0
 \end{pmatrix}\begin{pmatrix}
 x\\ y\\ z\\t
 \end{pmatrix}= \begin{pmatrix}
 0 \\ 0 \\0 \\0
 \end{pmatrix}.
$$

Nos da las ecuaciones $(a-b)x+y=0$, $(a-b)z+t=0$ y por tanto tiene dimensión dos, así que coincide con la multiplicidad algebraica. Por tanto en este caso la matriz sí es diagonalizable.
</li>

<li>Para los valores $a=1$, $b=-1$ determinar su forma diagonal $D$ y una matriz de paso $P$.

Utilizando los cálculos del segundo caso del apartado anterior  tenemos que 

$$
V_{\lambda=1}\equiv \left\{ \begin{array}{l}
y=0,\\
t=0.
\end{array}\right.
$$

Y una base es $\{(1,0,0,0),(0,0,1,0)\}$. 

$$
V_{\lambda= -1}\equiv \left\{ \begin{array}{l}
2x+y=0,\\
2z+t=0.
\end{array}\right.
$$

Y una base es $\{(1,-2,0,0),(0,0,1,-2)\}$. 

Por tanto, 

$$
D=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & -1 & 0\\
0 & 0 & 0 & -1
\end{pmatrix}, \hspace{1em} P=\begin{pmatrix}
1 & 0 & 1 & 0\\
0 & 0 & -2 & 0\\
0 & 1 & 0 & 1\\
0 & 0 & 0 & -2
\end{pmatrix}.
$$

</li>
</ol>

::::
:::::

::::: {#exr-7 .medio}
Se considera la matriz:

$$
A=\begin{pmatrix}
a+1 & 0 &0 \\ 1 & 1 & -1 \\ 1 &-1 & 1
\end{pmatrix}
$$

<ol type="a">
<li>Estudiar para qué valores del parámetro $a$ es $A$ diagonalizable.</li>
<li>Para el valor $a=0$ determinar su forma diagonal $D$ y una matriz de paso $P$ de forma que $D=P^{-1}\cdot A \cdot P$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Estudiar para qué valores del parámetro $a$ es $A$ diagonalizable.

Calculamos la ecuación característica:

$$
\begin{align*}|A-\lambda I|&= \left|\begin{array}{ccc}
a+1-\lambda & 0 &0 \\ 1 & 1-\lambda & -1 \\ 1 &-1 & 1-\lambda
\end{array}\right|= (a+1-\lambda)[(1-\lambda)^2-1]\\
&=(a+1-\lambda)(\lambda^2-2\lambda)=\lambda(a+1-\lambda)(\lambda-2).
\end{align*}
$$

Cuando $a+1\not = 0,2$ entonces aparecen tres valores propios distintos, cada uno con multiplicidad algebraica 1 y por tanto la geométrica también es 1, con lo que la matriz es diagonalizable. 

Quedan por estudiar dos casos:

**Cuando $a=-1$:**

Nos queda que el valor propio $\lambda=0$ tiene multiplicidad algebraica 2 y por tanto hay que calcular su multiplicidad geométrica.

$$
V_{\lambda=0}\equiv \begin{pmatrix}
0 & 0 &0 \\ 1 & 1 & -1 \\ 1 &-1 & 1
\end{pmatrix}\begin{pmatrix}
x \\
y\\
z\\
\end{pmatrix}= \begin{pmatrix}
0\\ 0 \\0
\end{pmatrix},
$$ 

nos da dos ecuaciones cartesianas y por tanto $m_g(\lambda=0)= \dim(V_{\lambda=0})=1$ y por tanto en este caso no es diagonalizable.

**Cuando $a=1$:**

Tendremos que el valor propio $\lambda=2$ tiene multiplicidad algebraica 2 y por tanto hay que calcular su multiplicidad geométrica.

$$
V_{\lambda=2}\equiv \begin{pmatrix}
0 & 0 &0 \\ 1 & -1 & -1 \\ 1 &-1 & -1
\end{pmatrix}\begin{pmatrix}
x \\
y\\
z\\
\end{pmatrix}= \begin{pmatrix}
0\\ 0 \\0
\end{pmatrix},
$$ 

nos da una ecuación cartesiana y por tanto $m_g(\lambda=2)= \dim(V_{\lambda=0})=2$ y por tanto en este caso sí es diagonalizable.
</li>

<li>Para el valor $a=0$ determinar su forma diagonal $D$ y una matriz de paso $P$ de forma que $D=P^{-1}\cdot A \cdot P$.

Para el caso $a=0$ tenemos los valores propios $0,1$ y $2$ que serán los elementos de la matriz diagonal. Calculamos bases de cada uno de los subespacios propios:

**$\lambda=0$:**

$$
\begin{pmatrix}
1 & 0 &0 \\ 1 & 1 & -1 \\ 1 &-1 & 1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &0 \\ 0 & 1 & -1 \\ 0 &0 & 0
\end{pmatrix},
$$

nos da unas ecuaciones cartesianas y por tanto una base es $\{(0,1,1)\}$.

**$\lambda=1$:**

$$
\begin{pmatrix}
0 & 0 &0 \\ 1 & 0 & -1 \\ 1 &-1 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &-1 \\ 0 & 1 & -1 \\ 0 &0 & 0
\end{pmatrix},
$$

nos da unas ecuaciones cartesianas y una base es $\{(1,1,1)\}$. 

**$\lambda=2$:**

$$
\begin{pmatrix}
-1 & 0 &0 \\ 1 & -1 & -1 \\ 1 &-1 & -1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &0 \\ 0 & 1 & 1 \\ 0 &0 & 0
\end{pmatrix},
$$

nos da unas ecuaciones cartesianas y  una base es $\{(0,1,-1)\}$.<br> 
Como solución, por ejemplo, podemos tomar

$$
D=\begin{pmatrix}
0 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 2
\end{pmatrix} \hspace{2cm} P=\begin{pmatrix}
0 & 1 & 0\\
1 & 1 & 1\\
1 & 1 & -1
\end{pmatrix}. 
$$
</li>
</ol>

::::
:::::

:::::{#exr-8 .medio}

Dada la matriz 

$$
A=\left(
\begin{array}{rrr}
1 & a & a \\
-1 & 1 & -1 \\
1 &0  & 2 \\
\end{array}
\right).
$$

Estudia para qué valores de $a\in\mathbb{R}$  es diagonalizable y para aquellos que lo sea obtén $D$ diagonal y $P$ regular tales que $D=P^{-1}AP$.

:::: {.callout collapse="true" title="Solución"}

En primer lugar calculamos los valores propios:

$$
|A-\lambda I|=\left|\begin{array}{ccc}
 1-\lambda & a & a \\
 -1 & 1-\lambda & -1 \\
  1 &0  & 2-\lambda \\
\end{array}\right|= \left|\begin{array}{ccc}
 1-\lambda & a & 0 \\
 -1 & 1-\lambda & -2+\lambda \\
  1 &0  & 2-\lambda \\
\end{array}\right|=\left|\begin{array}{ccc}
 1-\lambda & a & 0 \\
 0 & 1-\lambda & 0 \\
  1 &0  & 2-\lambda \\
\end{array}\right|
=(2-\lambda)(1-\lambda)^2,
$$

luego los valores propios son $\lambda=1$ con multiplicidad algebraica dos, y $\lambda=2$ con multiplicidad algebraica uno, y por tanto su multilicidad geométrica también es uno. Es necesario establecer para qué casos la multiplicidad geométrica de $\lambda=1$ es dos para que sea diagonalizable.

**$V_{\lambda=1}$:**

$$
\left(\begin{array}{ccc}
 0 & a & a \\
 -1 & 0 & -1 \\
  1 &0  & 1 \\
\end{array}\right)\sim_f \left(\begin{array}{ccc}
 1 &0  & 1 \\
 0 & a & a \\
 0 & 0 & 0 \\
 \end{array}\right).
$$

Si $a\not =0$ serían dos ecuaciones cartesianas y $\dim(V_{\lambda=1})=1$, luego solo es diagonalizable para $a=0$. En ese caso la cartesiana  de este subespacio propio es $x+z=0$ y por tanto una base es $\{(1,0,-1),(0,1,0)\}$.

**$V_{\lambda=2}$:**

$$
\left(\begin{array}{ccc}
 -1 & 0 & 0 \\
 -1 & -1 & -1 \\
  1 &0  & 0 \\
\end{array}\right)\sim_f \left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 1 \\
  0 &0  & 0 \\
\end{array}\right),
$$

que tiene cartesianas $\left\{\begin{array}{l} x=0,\\ y+z=0.\end{array}\right.$ Así una base es $\{(0,1,-1)\}$. Por tanto

$$
D=\left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 0 \\
  0 &0  & 2 \\
\end{array}\right), \hspace{1em} P=\left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 1 \\
 -1 &0  & -1 \\
\end{array}\right).
$$

::::
:::::

:::::{#exr-9 .basico}

Dadas las matrices

$$
A= \left(\begin{array}{rrr}
1 & 1 & 0\\
0 & 0 & 0\\
0 & 1 & 0
\end{array}\right)\hspace{2cm}  B= \left(\begin{array}{rrr}
1 & 1 & 0\\
1 & 0 & 0\\
1 & 1 & 0
\end{array}\right)
$$

¿Existe $P$ regular tal que $P^{-1}AP=B$?

:::: {.callout collapse="true" title="Solución"}

Si calculamos los valores propios de ambas:

$$
|A-\lambda I|= \left|\begin{array}{rrr}
1- \lambda & 1 & 0\\
0 & -\lambda & 0\\
0 & 1 & -\lambda
\end{array}\right|=(1-\lambda)(-\lambda)^2
$$

$$
|B-\lambda I|= \left|\begin{array}{rrr}
1-\lambda & 1 & 0\\
1 & -\lambda & 0\\
1 & 1 & -\lambda
\end{array}\right|=(-\lambda)(\lambda^2-\lambda-1)
$$

Como los conjuntos de valores propios de ambas son distintos, entonces no pueden ser semejantes.

::::
:::::

:::::{#exr-11 .basico}

Dada la matriz

$$
A= \left(\begin{array}{rrr}
2 & 0 & 2\\
0 & 1 & 0\\
2 & 0 & -1
\end{array}\right)
$$

¿Existe $P$ regular tal que $P^{-1}AP=I_3$?

:::: {.callout collapse="true" title="Solución"}

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
\right|= 
$$

$$
=(1-\lambda)(-(2-\lambda)(1+\lambda)-4)=(1-\lambda)(2+\lambda)(3-\lambda)
$$

Como los valores propios de $A$ son 1, -2 y 3, su forma diagonal (si fuera diagonalizable) no puede ser $I_3$, por lo tanto, {\bf no } existe $P$ regular tal que  $P^{-1}AP=I_3$

::::
:::::

:::::{#exr-12 .medio}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
1 & 1 & 1 & 1\\
1 & 1 & -1 & -1\\
1 & -1 & 1 & -1\\
1 & -1 & -1 & 1
\end{array}\right)
$$

<ol type='a'>
<li>Demuestra que es diagonalizable por semejanza.</li>
<li>Calcula una matriz diagonal $D$ y una matriz regular $P$ tales que $D=P^{-1}AP$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>

<li> Puesto que esta matriz es simétrica podemos utilizar el resultado que dice que toda matriz simétrica y real es diagonalizable por semejanza ortogonal (Teorema Espectral). En cualquier caso tenemos que calcular los valores propios y los subespacios propios en el siguiente apartado, que también se pueden utilizar para justificar este. 

</li>
<li> Para obtener los valores propios tenemos que resolver $|A-\lambda I|=0$.  

$$
|A-\lambda I|=\left|\begin{array}{cccc}
1-\lambda& 1 & 1 & 1\\
1 & 1-\lambda& -1 & -1\\
1 & -1 & 1-\lambda& -1\\
1 & -1 & -1 & 1-\lambda
\end{array}\right|= \left|\begin{array}{cccc}
1-\lambda& 1 & 1 & 1\\
2-\lambda& 2-\lambda& 0 & 0\\
0 & -2+\lambda& 2-\lambda & 0\\
0 & 0 & -2+\lambda& 2-\lambda
\end{array}\right|
$$

ahora desarrollamos por la primera fila, aunque aparecen 4 menores de orden 3 son muy sencillos (se ha tenido en cuenta que $-2+\lambda=-(2-\lambda)$)
$$
|A|=(1-a)\left|\begin{array}{ccc}
2-\lambda& 0 & 0\\
-2+\lambda& 2-\lambda & 0\\
0 & -2+\lambda& 2-\lambda
\end{array}\right|-\left|\begin{array}{ccc}
2-\lambda & 0 & 0\\
0  & 2-\lambda & 0\\
0  & -2+\lambda& 2-\lambda
\end{array}\right|+\left|\begin{array}{ccc}
2-\lambda& 2-\lambda & 0\\
0 & -2+\lambda& 0\\
0 & 0 &  2-\lambda
\end{array}\right|-
$$

$$
\left|\begin{array}{ccc}
2-\lambda& 2-\lambda& 0 \\
0 & -2+\lambda& 2-a\\
0 & 0 & -2+\lambda\end{array}\right|=(1-\lambda)(2-\lambda)^3- (2-\lambda)^3-(2-\lambda)^3-(2-\lambda)^3=\boxed{(2-\lambda)^3(-2-\lambda)}
$$

$$
|A-\lambda I|=(2-\lambda)^3(-2-\lambda)
$$

que tiene por raíces a $\lambda =2$ con multiplicidad algebraica 3 y $\lambda=-2$ con multiplicidad algebraica 1.

$\boxed{V_{\lambda=2}}$ tiene por cartesianas
$(A-2I)X=0$, realizamos operaciones elementales por filas en la matriz de coeficientes para obtener un sistema equivalente

$$
A-2I =\left(\begin{array}{cccc}
-1 & 1 & 1 & 1\\
1 & -1 & -1 & -1\\
1 & -1 & -1& -1\\
1 & -1 & -1 & -1
\end{array}\right)\sim_f \left(\begin{array}{cccc}
\boxed{1} & -1 & -1 & -1\\
0 & 0 & 0 & 0\\
0 & 0 & 0& 0\\
0 & 0 & 0 & 0
\end{array}\right)
$$ 

y por tanto $V_{\lambda=2}\equiv \boxed{x-y-z-t=0}$ que tiene $m.g.= dim\, V_{\lambda=2}=4-1=3$. Una base de este subespacio es

$$
\{(1,1,0,0),(1,0,1,0),(1,0,0,1)\}
$$

$\boxed{V_{\lambda=-2}}$ tiene por cartesianas
$(A+2I)X=0$, y calculando la forma escalonada reducida por filas de $A+2I$:
 

$$
A+2I=
\left(\begin{array}{cccc}
3 & 1 & 1 & 1\\
1 & 3 & -1 & -1\\
1 & -1 & 3 & -1\\
1 & -1 & -1 & 3
\end{array}\right)\sim_f \left(\begin{array}{cccc}
1 & -1 & -1 & 3\\
0 & 4 & 0 & -4\\
0 & 0 & 4& -4\\
0 & 4 & 4 & -8
\end{array}\right)\sim_f \left(\begin{array}{cccc}
\boxed{1} & 0 & 0 & 1\\
0 & \boxed{1} & 0 & -1\\
0 & 0 & \boxed{1}& -1\\
0 & 0 & 0 & 0
\end{array}\right)
$$ 

y por tanto

$$
V_{\lambda=-2}\equiv  \left\{ \begin{array}{l} 
x+t=0\\
y-t=0\\
z-t=0
\end{array}\right. 
$$ 

que tiene $m.g.= dim\, V_{\lambda=-2}=4-3=1$. Una base de este subespacio es 

$$ 
\{(-1,1,1,1)\}
$$

Así que 

$$
D=\left(\begin{array}{cccr}
\boxed{2} & 0 & 0 & 0\\
0 & \boxed{2} & 0 & 0\\
0 & 0 & \boxed{2}& 0\\
0 & 0 & 0 & \boxed{-2}
\end{array}\right) \hspace{2cm}  P=\left(\begin{array}{rrrr}
1 & 1 & 1 & -1\\
1 & 0 & 0 & 1\\
0 & 1 & 0& 1\\
0 & 0 & 1 & 1
\end{array}\right)
$$

</li>
</ol>

::::
:::::

:::::{#exr-13 .medio}

En $\mathbb{R}^{4}$ se considera el endomorfismo dado por
$$
f(x,y,z,t)=(3x-y,-x+3y,3z+t,z+3t)
$$

¿Es diagonalizable por semejanza este endomorfismo?

:::: {.callout collapse="true" title="Solución"}

Calculamos la matriz asociada respecto de la base canónica:
$$
\begin{array}{l}
f(1,0,0,0)=(3,-1,0,0)\\
f(0,1,0,0)=(-1, 3, 0,0)\\
f(0,0,1,0)=(0,0,3,1)\\
f(0,0,0,1)=(0,0,1,3)
\end{array}
$$

por lo que 

$$
M(f,B_c)=\begin{pmatrix}
3 & -1 & 0 & 0\\
-1 & 3 & 0 & 0\\
0 & 0 & 3 & 1\\
0 & 0 & 1 & 3
\end{pmatrix}
$$

Como la matriz es simétrica y real, por el Teorema Espectral, es diagonalizable por semejanza (por semejanza ortogonal).
También pueden calcularse los valores propios y sus multipliciades algebraica y geométrica, se obtiene:

(llamaremos $A$ a la matriz para simplificar la notación)

$$
|A-\lambda I|=\left|\begin{array}{cccc}
3-\lambda & -1 & 0 & 0\\
-1 & 3-\lambda & 0 & 0\\
0 & 0 & 3-\lambda & 1\\
0 & 0 & 1 & 3-\lambda
\end{array}\right|=
$$

(desarrollando por la primera columna)

$$
=(3-\lambda)\left|\begin{array}{ccc}
3-\lambda & 0 & 0\\
0 & 3-\lambda & 1\\
0 & 1 & 3-\lambda
\end{array}\right|+ (-1)^{2+1}(-1)\left|\begin{array}{ccc}
-1 & 0 & 0\\
0 & 3-\lambda & 1\\
0 & 1 & 3-\lambda
\end{array}\right|=
$$

$$= (3-\lambda)^2\left|\begin{array}{cc}
3-\lambda & 1\\
1 & 3-\lambda
\end{array}\right|+ (-1)\left|\begin{array}{cc}
3-\lambda & 1\\
1 & 3-\lambda
\end{array}\right|=
$$

$$
= ((3-\lambda)^2 -1)^2 = (\lambda^2-6\lambda+8)^2=(\lambda-4)^2(\lambda-2)^2 
$$

Para calcular las multiplicidades geométricas de cada valor propio utilizamos la fórmula  
$$
m.g. (\lambda)= dim \, \mathbb{R}^4 - rg(A-\lambda I)
$$

Calculamos $rg(A-\lambda I)$ para $\lambda=2$ y $\lambda=4$

$$
rg(A-2I)=rg\begin{pmatrix}
1 & -1 & 0 & 0\\
-1 & 1 & 0 & 0\\
0 & 0 & 1 & 1\\
0 & 0 & 1 & 1
\end{pmatrix}=2
$$

$$
rg(A-4I)=rg\begin{pmatrix}
-1 & -1 & 0 & 0\\
-1 & -1 & 0 & 0\\
0 & 0 & -1 & 1\\
0 & 0 & 1 & -1
\end{pmatrix}=2
$$

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$m.a.$</TH><TH>$m.g.$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 2$</TH><TD>2</TD><TD>2</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 4$</TH><TD>2</TD><TD>2</TD>
</TR>
</TABLE>
</CENTER>

Como la suma de las multiplicidades algebraicas es 4 y cada una coincide con la correspondiente geométrica, la matriz es diagonalizable por semejanza.

::::
:::::

:::::{#exr-14 .medio}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
3 & 1 & -3 & 3\\
1 & 3 & -3 & 3\\
1 & 1 & -1 & 3\\
1 & 1 & 1 & 1
\end{array}\right)
$$

<ol type='a'>
<li>Demuestra que es diagonalizable por semejanza.</li>
<li>Calcula una matriz diagonal $D$ y una matriz regular $P$ tales que $D=P^{-1}AP$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li> Calculamos los valores propios y sus multiplicidades algebraicas:

$$
|A-\lambda I|= \left|\begin{array}{cccc}
3-\lambda  & 1 & -3 & 3\\
1 & 3-\lambda  & -3 & 3\\
1 & 1 & -1-\lambda  & 3\\
1 & 1 & 1 & 1-\lambda 
\end{array}\right|= (C_4+C_3\rightarrow C_4)=  \left|\begin{array}{cccc}
3-\lambda  & 1 & -3 & 0\\
1 & 3-\lambda  & -3 & 0\\
1 & 1 & -1-\lambda  & 2-\lambda\\
1 & 1 & 1 & 2-\lambda 
\end{array}\right|=
$$

$$
=(F_3-F_4\rightarrow F_3)=\left|\begin{array}{cccc}
3-\lambda  & 1 & -3 & 0\\
1 & 3-\lambda  & -3 & 0\\
0 & 0 & -2-\lambda  & 0\\
1 & 1 & 1 & 2-\lambda 
\end{array}\right|=(2-\lambda)(-2-\lambda)\left|\begin{array}{cc}
3-\lambda  & 1 \\
1 & 3-\lambda \\
\end{array}\right|=
$$

$$
=(2-\lambda)(-2-\lambda)(\lambda^2-6\lambda+8)=(2-\lambda)^2(-2-\lambda)(4-\lambda)=0
$$

Luego tenemos la tabla

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$m.a.$</TH><TH>$m.g.$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 2$</TH><TD>2</TD><TD>?</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = -2$</TH><TD>1</TD><TD>1</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 4$</TH><TD>1</TD><TD>1</TD>
</TR>
</TABLE>
</CENTER>

Así que para comprobar que es diagonalizable debemos calcular la multiplicidad geométrica para $\lambda=2$.
$\boxed{V_{\lambda=2}}$

$$
A-2I= \left(\begin{array}{rrrr}
1 & 1 & -3 & 3\\
1 & 1 & -3 & 3\\
1 & 1 & -3 & 3\\
1 & 1 & 1 & -1
\end{array}\right)
$$

como las tres primeras filas son iguales, es inmediato que tiene rango 2, luego tiene 2 ecuaciones cartesianas y, por tanto, dimensión 2. Así que, en efecto, es diagonalizable.
También podemos hacer operaciones elementales por filas:

$$
A-2\lambda= \left(\begin{array}{rrrr}
1 & 1 & -3 & 3\\
1 & 1 & -3 & 3\\
1 & 1 & -3 & 3\\
1 & 1 & 1 & -1
\end{array}\right)\sim_f   \left(\begin{array}{rrrr}
1 & 1 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
\end{array}\right)
$$

para obtener las ecuaciones cartesianas que vamos a usar en el siguiente apartado: 

$$
V_{\lambda=2}\equiv \left\{ \begin{array}{l} 
x+y=0\\
z-t=0
\end{array}\right.
$$

</li>
<li> La matriz diagonal está formada por los valores propios, cada uno tantas veces como indica su multiplicidad aritmética. Vamos a calcular una base de cada uno de los subespacios propios:

Para 
$$
V_{\lambda=2}\equiv \left\{ \begin{array}{l} 
x+y=0\\
z-t=0
\end{array}\right.
$$

una base puede ser $\{(1,-1,0,0),(0,0,1,1)\}$.
Calculamos $\boxed{V_{\lambda=-2}}$:

$$
A+2I= \left(\begin{array}{rrrr}
5 & 1 & -3 & 3\\
1 & 5 & -3 & 3\\
1 & 1 & 1 & 3\\
1 & 1 & 1 & 3
\end{array}\right)\sim_f \left(\begin{array}{rrrr}
1 & 1 & 1 & 3\\
0 & -4 & -8 & -12\\
0 & 4 & -4 & 0\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f \left(\begin{array}{rrrr}
1 & 0 & 0 & 1\\
0 & 1 & 0 & 1\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 0
\end{array}\right)
$$

luego unas ecuaciones cartesianas son:

$$
V_{\lambda=-2}\equiv \left\{ \begin{array}{l} 
x+t=0\\
y+t=0\\
z+t=0
\end{array}\right.
$$

y una base $\{(1,1,1,-1)\}$.
Calculamos $\boxed{V_{\lambda=4}}$:

$$
A-4I= \left(\begin{array}{rrrr}
-1 & 1 & -3 & 3\\
1 & -1 & -3 & 3\\
1 & 1 & -5 & 3\\
1 & 1 & 1 & -3
\end{array}\right)\sim_f \left(\begin{array}{rrrr}
1 & 0 & 0 & -1\\
0 & 1 & 0 & -1\\
0 & 0 & 1 & -1\\
0 & 0 & 0 & 0
\end{array}\right)
$$

luego unas ecuaciones cartesianas son:

$$
V_{\lambda=4}\equiv \left\{ \begin{array}{l} 
x-t=0\\
y-t=0\\
z-t=0
\end{array}\right.
$$

y una base $\{(1,1,1,1)\}$.
Así que 

$$
D=\left(\begin{array}{rrrr}
2 & 0 & 0 & 0\\
0 & 2 & 0 & 0\\
0 & 0 & -2 & 0\\
0 & 0 & 0 & 4
\end{array}\right); \hspace{1cm}  P=\left(\begin{array}{rrrr}
1 & 0 & 1 & 1\\
-1 & 0 & 1 & 1\\
0 & 1 & 1 & 1\\
0 & 1 & -1 & 1
\end{array}\right)
$$

</li>
</ol>

::::
:::::

:::::{#exr-15 .medio}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
0 & 0 & 1 & 0\\
0 & 2 & 0 & -1\\
1 & 0 & 0 & 0\\
0 & 0 & 0 & 1
\end{array}\right)
$$

<ol type='a'>
<li>Demuestra que es diagonalizable por semejanza.</li>
<li>Calcula una matriz diagonal $D$ y una matriz regular $P$ tales que $D=P^{-1}AP$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li> En primer lugar calculamos los valores propios y sus multiplicidades algebraicas:

$$
|A-\lambda I|= \left|\begin{array}{rrrr}
-\lambda & 0 & 1 & 0\\
0 & 2-\lambda & 0 & -1\\
1 & 0 & -\lambda & 0\\
0 & 0 & 0 & 1-\lambda
\end{array}\right|=(1-\lambda)\left|\begin{array}{rrrr}
-\lambda & 0 & 1 \\
0 & 2-\lambda & 0 \\
1 & 0 & -\lambda \\
\end{array}\right|=(1-\lambda)(2-\lambda)\left|\begin{array}{rrrr}
-\lambda & 1 \\
1 & -\lambda \\
\end{array}\right|=
$$

$$
=(1-\lambda)(2-\lambda)(\lambda^2-1)=-(1-\lambda)^2(2-\lambda)(1+\lambda)
$$

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$m.a.$</TH><TH>$m.g.$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 1$</TH><TD>2</TD><TD>?</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = 2$</TH><TD>1</TD><TD>1</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$\lambda = -1$</TH><TD>1</TD><TD>1</TD>
</TR>
</TABLE>
</CENTER>

donde se ha usado $1\leq m.g.\leq m.a.$; nos queda comprobar la multiplicidad geométrica de $\lambda=1$.

$\boxed{V_{\lambda=1}}$
$$
A-I= \left(\begin{array}{rrrr}
-1 & 0 & 1 & 0\\
0 & 1 & 0 & -1\\
1 & 0 & -1 & 0\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & 0 & -1 & 0\\
0 & 1 & 0 & -1\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0
\end{array}\right)
$$

Por tanto $V_{\lambda=1}\equiv \left\{ \begin{array}{l}
x-z=0\\
y-t=0
\end{array}\right.$ y por tanto la dimensión es $4-nº catesianas= 2=m.g.$, con lo que la matriz es diagonalizable.

</li>
<li> Necesitamos calcular bases de cada subespacio propio para obtener la matriz $P$:

$\boxed{V_{\lambda=1}}$ tiene base $\{(1,0,1,0),(0,1,0,1)\}$ (que se obtiene de las ecuaciones cartesianas ya calculadas)


$\boxed{V_{\lambda=2}}$

$$
A-2I= \left(\begin{array}{rrrr}
-2 & 0 & 1 & 0\\
0 & 0 & 0 & -1\\
1 & 0 & -2 & 0\\
0 & 0 & 0 & -1
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & 0 & -2 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & -3 & 0\\
0 & 0 & 0 & 0
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 0 &1 & 0\\
0 & 0 & 0& 1\\
0 & 0 & 0 & 0
\end{array}\right)
$$

$V_{\lambda=2}\equiv \left\{ \begin{array}{l}
x=0\\
z=0\\
t=0\end{array}\right.$ y una base es $\{(0,1,0,0)\}$.

$\boxed{V_{\lambda=-1}}$
$$
A-2I= \left(\begin{array}{rrrr}
1 & 0 & 1 & 0\\
0 & 3 & 0 & -1\\
1 & 0 & 1 & 0\\
0 & 0 & 0 & 2
\end{array}\right)\sim_f  \left(\begin{array}{rrrr}
1 & 0 & 1 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0
\end{array}\right)
$$

$V_{\lambda=-1}\equiv \left\{ \begin{array}{l}
x+z=0\\
y=0\\
t=0\end{array}\right.$ y una base es $\{(1,0,-1,0)\}$.

Luego
$$
D=\left(\begin{array}{rrrr}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
0 & 0 & 0 & -1
\end{array}\right)\hspace{2cm}  P=\left(\begin{array}{rrrr}
1 & 0 & 0  & 1\\
0 & 1 & 1 & 0\\
1 & 0 & 0 & -1\\
0 & 1 & 0 & 0
\end{array}\right)
$$

</li>
</ol>

::::
:::::

:::::{#exr-16 .medio}

Se considera la matriz:
$$
A=\begin{pmatrix}
2 & 1 & 0 & 0 \\
0 & 2 & 1 & 0\\
0 & 1 & 2 & 0 \\
0 & 0 & 1 & 2\\
\end{pmatrix}
\in \mathfrak{M}_4(\mathbb{R})
$$

Probar que $A$ es diagonalizable y determinar $D$ diagonal y $P$ invertible de forma que $D=P^{-1}·A·P$

:::: {.callout collapse="true" title="Solución"}

Calculamos el polinomio característico de $A$:
$$
p(\lambda)= det(A-\lambda I)= 
\left| 
\begin{array}{cccc}
2-\lambda & 1 & 0 & 0 \\
0 & 2-\lambda  & 1 & 0\\
0 & 1 & 2-\lambda & 0\\
0 & 0 & 1 & 2-\lambda  
\end{array}\right|
=
(2-\lambda)\cdot\left| 
\begin{array}{cccc}
2-\lambda  & 1 & 0\\
1 & 2-\lambda & 0\\
 0 & 1 & 2-\lambda 
\end{array}\right|
=
$$

$$
=(2-\lambda)^2\cdot\left| 
\begin{array}{cccc}
2-\lambda & 1 \\
1 & 2-\lambda \\
\end{array}\right|=(2-\lambda)^2\cdot [(2-\lambda)^2-1]=
(2-\lambda)^2\cdot [\lambda^2-4\lambda+3]=
(2-\lambda)^2\cdot (1-\lambda)\cdot (3-\lambda)
$$

Así pues los autovalores de $A$ y sus multiplicidades algebraicas son:

<div class="table_2col">
<CENTER>
<table>
    <thead>
        <tr>
            <td>$\lambda_1= 1$</td>
            <td>$\alpha_1=1$</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$\lambda_1= 2$</td>
            <td>$\alpha_1=2$</td>
        </tr>
        <tr>
            <td>$\lambda_1= 3$</td>
            <td>$\alpha_1=1$</td>
        </tr>
    </tbody>
</table>
</CENTER>
</div>

Calculemos las multiplicidades geométricas. Puesto que para cada $i$ se verifica $1\leq d_i \leq \alpha_i$, se deduce que $d_1=1$ y $d_3=1$. 

$$
d_2= 4 -rg(A-2\cdot I)=
4-rg\begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\end{pmatrix}
= 4-2=2
$$

Así pues, tenemos:

<div class="table_3col">
<CENTER>
<table>
    <thead>
        <tr>
            <td>$\lambda_1= 1$</td>
            <td>$\alpha_1=1$</td>
            <td>$d_1=1$</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>$\lambda_1= 2$</td>
            <td>$\alpha_1=2$</td>
            <td>$d_2=2$</td>
        </tr>
        <tr>
            <td>$\lambda_1= 3$</td>
            <td>$\alpha_1=1$</td>
            <td>$d_3=1$</td>
        </tr>
    </tbody>
</table>
</CENTER>
</div>

y la matriz es diagonalizable, ya que coinciden las multiplicidades geométricas con las algebraicas y la forma diagonal de $A$ es la matriz: 
$$
D=\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 2 & 0 & 0\\
0 & 0 & 2 & 0 \\
0 & 0 & 0 & 3
\end{pmatrix}
$$

Calculemos ahora bases de los subespacios propios:

$$
V_{\lambda_1}=Ker(A-I)=
Ker\begin{pmatrix}
1 & 1 & 0 & 0 \\
0 & 1 & 1 & 0 \\
0 & 1 & 1 & 0 \\
0 & 0 & 1 & 1 \\
\end{pmatrix}
$$
$$
\left(\begin{array}{cccc}
1 & 1 & 0 & 0 \\
0 & 1 & 1 & 0 \\
0 & 1 & 1 & 0 \\
0 & 0 & 1 & 1 \\  \hline
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 \\
\end{array}\right)
\sim_c
\left(\begin{array}{ccc|c}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\ \hline
1 & -1 & 1 & 1 \\
0 & 1 & -1 & -1 \\
0 & 0 & 1 & 1 \\
0 & 0 & 0 & -1 \\
\end{array}\right)
$$
y una base de $V_{\lambda_1}$ es $\{(1,-1,1,-1)\}$

De igual manera:
$$
V_{\lambda_2}=Ker(A-2\cdot I)=
Ker\begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\end{pmatrix}
$$
y una base de $V_{\lambda_2}$ es $\{(1,0,0,0),(0,0,0,1)\}$

$$
V_{\lambda_3}=Ker(A-3\cdot I)=
Ker\begin{pmatrix}
-1 & 1 & 0 & 0 \\
0 & -1 & 1 & 0 \\
0 & 1 & -1 & 0 \\
0 & 0 & 1 & -1 \\
\end{pmatrix}
$$
y una base de $V_{\lambda_3}$ es $\{(1,1,1,1)\}$

Y la matriz de paso $P$ es la matriz de cambio de base de la base de vectores propios obtenida: 
$\overline{B}=\{(1,-1,1,-1), (1,0,0,0),(0,0,0,1),(1,1,1,1)\}$ a la canónica. 

$$
P=\begin{pmatrix}
1  & 1 & 0 & 1 \\
-1 & 0 & 0 & 1\\
1  & 0 & 0 & 1 \\
-1 & 0 & 1 & 1
\end{pmatrix}
$$

::::
:::::