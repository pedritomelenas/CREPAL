---
title: Aplicaciones lineales
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

Se muestran ejercicios sobre cuerpos finitos y sobre los racionales y reales. Puedes cambiar esta opción marcando o desmarcando la siguiente casilla.<br>
<input type="checkbox" id="casilla_cf" value="cfon" checked onclick="CF();"> Mostrar ejercicios sobre cuerpos finitos. 



<article class="cf" style="display:block;">
Determina cuáles de las siguientes aplicaciones son lineales:

<ol type="a">
<li>La aplicación $f:(\mathbb{Z}_3)^2 \rightarrow (\mathbb{Z}_3)^2$, $f(x,y)=(x+1,y+2)$.</li>
<li>La aplicación $f:V \rightarrow V'$, $f(v)=0$.</li>
<li>La aplicación $f:\mathbb{R} \rightarrow \mathbb{R}$, $f(r)=r^2$.</li>
<li>La aplicación $f:(\mathbb{Z}_7)^3 \rightarrow (\mathbb{Z}_7)^2$, $f(x,y,z)=(x+y+z,28x+92z)$.</li>

</ol>
<details>
<summary>Solución</summary>

<ol type="a">
<li>La aplicación $f:(\mathbb{Z}_3)^2 \rightarrow (\mathbb{Z}_3)^2$, $f(x,y)=(x+1,y+2)$.<br>

No es aplicación lineal. Basta tomar $u=(1,0)$ y $a=2$ y comprobar que no se cumple la segunda propiedad:
$$f(au)=f(2,0)=(0,2),$$
mientras que, 
$$af(u)=2(2,2)=(1,1).$$</li>

<li>La aplicación $f:V \rightarrow V'$, $f(v)=0$.<br>

Es aplicación lineal:<br>
Para cualesquiera $u,v$ se tiene $f(u+v)=0=0+0=f(u)+f(v)$.<br>
Para todo $u$ y todo $a$ se verifica $f(au)=0=a\cdot 0=af(u)$.</li>

<li>La aplicación $f:\mathbb{R} \rightarrow \mathbb{R}$, $f(r)=r^2$.<br>

No es lineal, tomamos $u=1$ y $a=2$ y comprobamos que no se cumple la segunda propiedad de aplicación lineal:
$$af(u)=2\cdot 1^2,$$
$$f(au)=f(2)=2^2.$$</li>

<li>La aplicación $f:(\mathbb{Z}_7)^3 \rightarrow (\mathbb{Z}_7)^2$, $f(x,y,z)=(x+y+z,28x+92z)$.<br>

Es aplicación lineal. Cada componente de la imagen se calcula como una combinación lineal de las componentes del vector inicial.</li>

</ol>
</details>
</article>

<article>
Prueba que la siguiente aplicación es lineal y calcula la matriz asociada considerando las bases estándar en cada espacio vectorial.
$$D:\mathbb{R}_3[x] \to \mathbb{R}_3[x] \text{ dada por } D(p(x))=p'(x).$$

<details>
<summary>Solución</summary>

Es conocido que la derivada tiene las propiedades:

<ol type="a">
<li>La derivada de una suma es la suma de las derivadas.<br>
Es decir, dadas dos funciones (derivables, y los polinomios lo son) $f$ y $g$ se verifica
$$D(f+g)=D(f)+D(g),$$
que es la primera propiedad que debe verificar una aplicación lineal. Hay que tener cuidado porque aquí $f$ y $g$ son los vectores y $D$ es la aplicación.</li>
<li>La derivada de una constante por una función es la constante por la derivada de la función.<br>
Es deir, dadas $f$ (derivable) y $a\in \mathbb{R}$ entonces
$$D(af)=aD(f),$$
que es la segunda propiedad de aplicación lineal.</li>
</ol>

Calculemos ahora la matriz asociada a $D$ utilizando la base de $\mathbb{R}_3[x]$ (el conjunto de los polinomios con coeficientes en $\mathbb{R}$ de grado menor o igual que tres), $B_s=\{1,x,x^2,x^3\}$ en el espacio inicial y en el final, puesto que son el mismo:
$$D(1)=0=(0,0,0,0)_{B_s},$$
donde el primer cero representa a la derivada del polinomio constante igual a uno, que es el polinomio constante igual a cero, cuyas coordenadas en la base $B_s$ son $(0,0,0,0)$.
Procedemos de la misma forma con los otros tres vectores de la base:
$$\begin{array}{l}
D(x)=1=(1,0,0,0)_{B_s},\\
D(x^2)=2x=(0,2,0,0)_{B_s},\\
D(x^3)=3x^2=(0,0,3,0)_{B_s}.
\end{array}
$$
Así que la matriz asociada resulta de poner estas coordenadas por columnas:
$$M_{B_sB_s}(D)=\begin{pmatrix}
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
0 & 0 & 0 & 3\\
0 & 0 & 0 & 0 
\end{pmatrix}.$$

</details>
</article>

<article class="cf" style="display:block;">

Se considera la matriz sobre $\mathbb{Z}_5$: 
$$A=\begin{pmatrix}
1 & 2 & 0\\
2 & 1 & 0\\
1 & 4 & 2
\end{pmatrix}.$$

<ol type="a">
<li>Diagonaliza la matriz $A$.</li>
<li>Calcula la matriz $A^{123}$.</li>
<li>Diagonaliza la matriz $A^{-1}$.</li>

</ol>
<details>
<summary>Solución</summary>
<ol type="a">

<li>Diagonalizar la matriz $A$.<br>
En primer lugar calculamos el polinomio característico para determinar los valores propios y sus multiplicidades algebraicas:
$$|A-\lambda I|=\begin{vmatrix}
1-\lambda & 2 & 0\\
2 & 1-\lambda & 0\\
1 & 4 & 2-\lambda
\end{vmatrix}=(2-\lambda)\begin{vmatrix}
1-\lambda & 2 \\
2 & 1-\lambda \\
\end{vmatrix}= (2- \lambda)[(1-\lambda)^2-4]=(2-\lambda)(\lambda^2+3\lambda+2).$$
Las raíces de $\lambda^2+3\lambda+2$ en $\mathbb{Z}_5$ son $3$ y $4$, que son simples, luego los valores propios son $2$, $3$, $4$ con multiplicidades algebraicas $1$ para cada uno.<br>


Ahora debemos calcular cada uno de los subespacios propios:<br>

<strong>$V_{\lambda=2}$</strong> 
 
$$A-2I=\begin{pmatrix}
4 & 2 & 0\\
2 & 4 & 0\\
1 & 4 & 0
\end{pmatrix}.$$
Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=2}$ a partir de $(A-2I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:
$$A-2I=\begin{pmatrix}
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
\end{pmatrix}.$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(5),[[4,2,0],[2,4,0],[1,4,0]])
show(A,"~",A.rref())
</script>
</div>

Entonces nos quedan las cartesianas
$$\boxed{\begin{array}{l} x=0,\\ y=0. \end{array} }$$
Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 1 y una base es $\{(0,0,1)\}$.<br>

<strong>$V_{\lambda=3}$</strong> 
 
$$A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}.$$
Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=3}$ a partir de $(A-3I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:
$$A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 4 & 0\\
0 & 0 & 1\\
0 & 0 & 0\\
\end{pmatrix}.$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(5),[[3,2,0],[2,3,0],[1,4,4]])
show(A,"~",A.rref())
</script>
</div>

Entonces nos quedan las cartesianas
$$\boxed{\begin{array}{l} x+4y=0,\\ z=0. \end{array} }$$
Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=3}$) es 1 y una base es $\{(1,1,0)\}$.<br>

<strong>$V_{\lambda=4}$</strong> 
 
$$A-4I=\begin{pmatrix}
2 & 2 & 0\\
2 & 2 & 0\\
1 & 4 & 3
\end{pmatrix}.$$
Para calcular unas ecuaciones cartesianas más sencillas de $V_{\lambda=3}$ a partir de $(A-4I)X=0$ hacemos operaciones elementales por filas en la matriz anterior:
$$A-3I=\begin{pmatrix}
3 & 2 & 0\\
2 & 3 & 0\\
1 & 4 & 4
\end{pmatrix}\sim_{f} \begin{pmatrix}
1 & 0 & 4\\
0 & 1 & 1\\
0 & 0 & 0\\
\end{pmatrix}.$$
Entonces nos quedan las cartesianas
$$\boxed{\begin{array}{l} x+4z=0,\\ y=0. \end{array} }$$
Como el espacio $(\mathbb{Z}_{5})^3$ tiene dimensión tres y el subespacio tiene dos ecuaciones cartesianas, entonces 
la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=3}$) es 1 y una base es $\{(1,4,1)\}$.<br>

Por último, una vez comprobada que la multiplicidad algebraica y geométrica coinciden para cada valor propio escribimos las matriz diagonal $D$ (con los valores propios en la diagonal) y la matriz $P$ (con los vectores propios por columnas) cuidando de que el orden en el que se escriben los valores propios en $D$ corresponda con el orden de los vectores propios asociados en $P$:
$$D=\begin{pmatrix}
2 & 0 & 0\\
0 & 3 & 0\\
0 & 0 & 4
\end{pmatrix}, \hspace{2cm}  P=\begin{pmatrix}
0 & 1 & 1\\
0 & 1 & 4\\
1 & 0 & 1
\end{pmatrix}.$$
</li>

<li>Calcular la matriz $A^{123}$.<br>

Para calcular $A^{123}$ utilizamos la diagonalización que acabamos de realizar para la que se cumple $D=P^{-1}AP$.
Despejando $A$ tendremos $$A=PDP^{-1},$$ y podemos observar que en el producto
$$A^{123}= (PDP^{-1})(PDP^{-1})\cdots (PDP^{-1})$$
los productos $P^{-1}P=I$, y por tanto queda
$$A^{123}=PD^{123}P^{-1}.$$
Además el cálculo de las potencias de una matriz diagonal es muy sencillo, puesto que consiste en elevar a dicha potencia cada uno de los elementos de la diagonal, es decir:
$$D^{123}=\begin{pmatrix}
2^{123} & 0 & 0\\
0 & 3^{123} & 0\\
0 & 0 & 4^{123}
\end{pmatrix}.$$
Se trata entonces de calcular dichas potencias en $\mathbb{Z}_5$, para lo que utilizaremos el Teorema pequeño de Fermat: $a^4=1$ en $\mathbb{Z}_5$.<br>
Como $123=30\cdot 4+3$, entonces $2^{123}=(2^4)^30\cdot 2^3=2^3=3$. Por otro lado, $3^{123}=(3^4)^30\cdot 3^3=3^3=2$ y $4^{123}=(4^4)^30\cdot 4^3=4^3=4$.<br>
Así que 

$$D^{123}=\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 4
\end{pmatrix}.$$
Solo queda calcular $P^{-1}$ y realizar el producto $PD^{123}P^{-1}$.
$$\begin{align*}
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
\end{align*}$$
Por último:
$$A^{123}=\begin{pmatrix}
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
\end{pmatrix}.$$</li>

<li>Diagonalizar la matriz $A^{-1}$.<br>

Para diagonalizar $A^{-1}$ basta observar que como $D=P^{-1}AP$ entonces $D^{-1}=P^{-1}A^{-1}P$, luego la matriz diagonal será $D^{-1}$:
$$D^{-1}=\begin{pmatrix}
2^{-1} & 0 & 0\\
0 & 3^{-1} & 0\\
0 & 0 & 4^{-1}
\end{pmatrix}=\begin{pmatrix}
3 & 0 & 0\\
0 & 2 & 0\\
0 & 0 & 4
\end{pmatrix},$$ 
y la matriz de paso es la misma, $P$.</li>

</ol>
</details>
</article>

<article>
Sea la matriz 
$$
A=\left(\begin{array}{cccc}
 1 & a & 2 & -1\\
0 & 1 & 3 & 4\\
 0 & 0 & 2 & b\\
 0 & 0 & 0 & 2\\
\end{array}
\right)
.$$
Estudiar para qué valores de los parámetros $a$ y $b$ es
diagonalizable.

<details>
<summary>Solución</summary>

Necesitamos calcular los valores propios y sus multiplicidades algebraica y geométrica.
Los valores propios son fáciles:
$$
|A-\lambda I|=\left|\begin{array}{cccc}
 1-\lambda & a & 2 & -1\\
0 & 1-\lambda & 3 & 4\\
 0 & 0 & 2-\lambda & b\\
 0 & 0 & 0 & 2-\lambda\\
\end{array}
\right|=(1-\lambda)^2(2-\lambda)^2.$$
Los valores propios son $1$ y $2$ con multiplicidades algebraicas $2$ para cada uno.<br>

<strong>$V_{\lambda=1}$</strong> 
$$
A-I=\left(\begin{array}{cccc}
 0 & a & 2 & -1\\
0 & 0 & 3 & 4\\
 0 & 0 & 1 & b\\
 0 & 0 & 0 & 1\\
\end{array}
\right).
$$
Para que tenga rango dos (y por tanto la dimensión de $V_{\lambda=1}$ sea también dos) debe ser $a=0$.<br>

<strong>$V_{\lambda=2}$</strong> 
$$
A-2I=\left(\begin{array}{cccc}
 -1 & a & 2 & -1\\
0 & -1 & 3 & 4\\
 0 & 0 & 0 & b\\
 0 & 0 & 0 & 0\\
\end{array}
\right).
$$
Para que tenga rango dos (y por tanto la dimensión de $V_{\lambda=2}$ sea también dos) debe ser $b=0$.<br>

Concluimos que solo es diagonalizable en el caso $a=b=0$.

</details>
</article>

<article class="cf" style="display:block;">
Sea $f:(\mathbb{Z}_{13})^3 \longrightarrow  (\mathbb{Z}_{13})^3 $ la aplicación lineal dada
por:
$$f(x,y,z)=(7x+12y+4z, x+6y+3z, 5x+6y+12z).$$
<ol type="a">
<li>Halla la matriz de $f$ en la base canónica (llamémosla $A$).</li>
<li>Estudia si $f$ es diagonalizable, y en caso afirmativo halla una base de vectores propios.</li>
<li>Calcula $A^{2431}$.</li>
<li>Calcula $f^{2432}(1,2,3)$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Hallar la matriz de $f$ en la base canónica.<br>

Para calcular la matriz asociada calculamos las imágenes de los vectores de la base canónica:
$$\begin{array}{l}
f(1,0,0)=(7,1,5),\\
f(0,1,0)=(12,6,6),\\
f(0,0,1)=(4,3,12).
\end{array}$$
Podemos, por simplificar cálculos posteriores, sustituir que $12=-1$ en $\mathbb{Z}_{13}$, y nos queda la matriz
$$A=M_{B_c}(f)=\begin{pmatrix}
7 & -1 & 4\\
1 & 6 & 3\\
5 & 6 &-1
\end{pmatrix}.$$</li>

<li>Estudiar si $f$ es diagonalizable, y hallar una base de vectores propios.<br>

Calculamos los valores propios, mediante la ecuación característica:
$$\begin{align*}
\left| \begin{array}{ccc}
7-\lambda & -1 & 4\\
1 & 6-\lambda & 3\\
5 & 6 &-1-\lambda
\end{array}\right| & 
=(7-\lambda)(6-\lambda)(-1-\lambda)-2-2-7(6-\lambda)-5(7-\lambda)+(-1-\lambda)\\ &
=-\lambda^3-\lambda^2+8\lambda -7.
\end{align*}$$
Calculamos las raíces de este polinomio (lo cual es laborioso) y  obtenemos que son $\lambda=5$ con multiplicidad algebraica 1 y $\lambda=-3(=10)$ con multiplicidad algebraica 2.<br>

Debemos calcular la multiplicidad geométrica de $\lambda=-3$ para poder decidir si es o no diagonalizable. Para ello calculamos el subespacio propio correspondiente:
$$(A+3I)=\begin{pmatrix}
10 & -1 & 4\\
1 & 9 & 3\\
5 & 6 & 2
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 9 & 3\\
0 & 0 & 0\\
0 & 0 & 0\\
\end{pmatrix}.$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(13),[[10,-1,4],[1,9,3],[5,6,2]])
show(A,"~",A.rref())
</script>
</div>

Luego nos queda una única ecuación cartesiana que es $x+9y+3z=0$ y por tanto la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 2, así que la matriz es diagonalizable.<br>
Calculamos una base de  $V_{\lambda=-3}$:
$$\{ (4,1,0),(10,0,1) \}.$$

Necesitamos también una base de $V_{\lambda=5}$:
 $$(A-5I)=\begin{pmatrix}
2 & -1 & 4\\
1 & 1 & 3\\
5 & 6 & -6
\end{pmatrix}\sim_f 
\begin{pmatrix}
1 & 0 & -2\\
0 & 1 & 5\\
0 & 0 & 0\\
\end{pmatrix}.$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(13),[[2,-1,4],[1,1,3],[5,6,-6]])
show(A,"~",A.rref())
</script>
</div>

Nos quedan las ecuaciones $V_{\lambda=5}\equiv \boxed{\begin{array}{l}
x-2z=0,\\
y+5z=0.\end{array} }$ y una base es $\{(2,-5,1)\}$.<br>
Luego la solución al problema de diagonalización es:
$$ D=\left(\begin{array}{ccc}
5 & 0 & 0\\
0 & 10 & 0\\
0 & 0 &  10
\end{array}\right)=\left(\begin{array}{ccc}
5 & 0 & 0\\
0 & -3 & 0\\
0 & 0 & -3
\end{array}\right), \hspace{1cm}  P=\left(\begin{array}{ccc}
2 & 4 & 10\\
-5 & 1 & 0\\
1 & 0 &  1
\end{array}\right).$$</li>

<li>Calcular $A^{2431}$.<br>
Para calcular la potencia pedida utilizamos la diagonalización:
$$D=P^{-1}AP \text{ o bien }  A=PDP^{-1},$$
que nos permite deducir que
$$A^{2431}=PD^{2431}P^{-1}.$$
Calculamos 
$$D^{2431}=\left(\begin{array}{ccc}
5^{2431} & 0 & 0\\
0 & 10^{2431} & 0\\
0 & 0 &  10^{2431}
\end{array}\right),$$
para lo que hemos realizado los cálculos $5^{703}, 10^{703}$ en $\mathbb{Z}_{13}$ mediante el Teorema pequeño de Fermat: $a^{12}=1$ en $\mathbb{Z}_{13}$. Obtenemos así $5^{2431}=5^{202\cdot 12+7}=5^7=8$ y además $10^{2431}=10^{202\cdot 12+7}=10^7= 10$. Y obtenemos
$$D^{2431}=\left(\begin{array}{ccc}
8 & 0 & 0\\
0 & 10 & 0\\
0 & 0 &  10
\end{array}\right).$$
Necesitamos también $P^{-1}$:
$$\begin{align*}
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
$$A^{2431}=PD^{2431}P^{-1}=\left(\begin{array}{ccc}
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
\end{array}\right).$$</li>

<li>Calcula $f^{2432}(1,2,3)$.<br>

Basta realizar la operación $f^{2432}(1,2,3)=A^{2431}(1,2,3)^T$.</li>

</ol>
</details>
</article>

<article class="cf" style="display:block;">
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

<details>
<summary>Solución</summary>

<ol type="a">
<li>Hallar la matriz de $f$ en la base canónica.<br>
Calculamos las imágenes de los vectores de la base canónica:
$$\begin{array}{l}
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
\end{array}\right).$$</li>

<li>Estudiar si $f$ es diagonalizable y hallar una base de vectores propios.<br>
Calculamos los valores propios y sus multiplicidades algebraica y geométrica:
$$|A-\lambda I|=\left| \begin{array}{ccc}
-\lambda & 0 & 4\\
2 & 2-\lambda & 1\\
 1 & 0 & -\lambda\\
\end{array}\right|=(2-\lambda)[(-\lambda)^2-4)]=(2-\lambda)(\lambda^2-4).$$
Las raíces de $\lambda^2-4=0$ son $\lambda=2$ y $\lambda=3(=-2)$ en $\mathbb{Z}_5$. Así el valor propio $\lambda=2$ tiene multiplicidad algebraica 2 y $\lambda=3$ tiene multiplicidad algebraica 1.<br>
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
\end{array}\right).$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(5),[[-2,0,4],[2,0,1],[1,0,-2]])
show(A,"~",A.rref())
</script>
</div>

Luego nos queda una única ecuación cartesiana que es $x-2z=0$ y por tanto la multiplicidad geométrica (esto es, la dimensión de $V_{\lambda=2}$) es 2, así que la matriz es diagonalizable.<br>
Calculamos una base de  $V_{\lambda=2}$:
$\{ (0,1,0),(2,0,1) \}$.<br>
Nos queda calcular una base de $V_{\lambda=3}$:
$$A-3I=
\left(\begin{array}{rrr}
-3 & 0 & 4\\
2 & -1 & 1\\
 1 & 0 & -3\\
\end{array}\right)\sim_f 
\left(\begin{array}{rrr}
 1 & 0 & -3\\
 0 & 1 & 3\\
0 & 0 & 0\\
\end{array}\right).$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix(GF(5),[[-3,0,4],[2,-1,1],[1,0,-3]])
show(A,"~",A.rref())
</script>
</div>

Nos quedan las ecuaciones$V_{\lambda=3}\equiv \boxed{\begin{array}{l}
x-3z=0,\\
y+3z=0.\end{array} }$. Además una base es $\{(3,2,1)\}$.<br>
Luego la solución al problema de diagonalización es:
$$D=\left(\begin{array}{rrr}
2 & 0 & 0\\
0 & 2 & 0\\
 0 & 0 & 3\\
\end{array}\right), \hspace{1cm}
 P= \left(\begin{array}{rrr}
0 & 2 & 3\\
1 & 0 & 2\\
 0 & 1 & 1\\
\end{array}\right).$$</li>

<li>Calcular $A^{703}$.<br>
Para calcular la potencia pedida utilizamos la diagonalización:
$$D=P^{-1}AP \text{ o bien }  A=PDP^{-1},$$
que nos permite deducir que
$$A^{703}=PD^{703}P^{-1}.$$
Calculamos 
$$D^{703}=\left(\begin{array}{ccc}
2^{703} & 0 & 0\\
0 & 2^{703} & 0\\
0 & 0 &  3^{703}
\end{array}\right),$$
para lo que realizamos los cálculos en $\mathbb{Z}_5$, mediante el uso del Teorema pequeño de Fermat: $2^{703}=2^{175\cdot 4+3}=2^3= 3$, y también $3^{703}=3^{175\cdot 4+3}=3^3= 2$. Obtenemos así:
$$D^{703}=\left(\begin{array}{ccc}
3 & 0 & 0\\
0 & 3 & 0\\
0 & 0 &  2
\end{array}\right).$$
También necesitamos calcular $P^{-1}$:
$$(P|I)= \left(\begin{array}{ccc|ccc}
0 & 2 & 3 & 1 & 0 & 0\\
1 & 0 & 2 & 0 & 1 & 0\\
 0 & 1 & 1 & 0 & 0 & 1\\
\end{array}\right)\sim_f \left(\begin{array}{ccc|ccc}
1 & 0 & 0 & 3 & 1 & 4\\
0 & 1 & 0 & 4 & 0 & 3\\
 0 & 0 & 1 & 1 & 0 & 3\\
\end{array}\right)=(I|P^{-1}).$$
Luego 
$$A^{703}=PD^{703}P^{-1}=\left(\begin{array}{rrr}
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
\end{array}\right).$$</li>

<li>Hallar $f^{703}(1,2,3)$.<br>
Basta realizar la operación 
$$f^{703}(1,2,3)=A^{703}(1,2,3)^T=
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
\end{array}\right).$$</li>

</ol>
</details>
</article>

<article>
Sea $f:U+W=\mathbb{R}^3 \to U+W=\mathbb{R}^4$ la aplicación lineal que, respecto de las bases canónicas, viene dada por la matriz
$$A=\begin{pmatrix}
1 & -1 & 0\\
1 & 2 & 1 \\
0 & 1 & 1 \\
1 & 1 & 1
\end{pmatrix}
$$

<ol type="a">
<li>Determina la base más sencilla de $\operatorname{Im}(f)$ y unas ecuaciones cartesianas del $\operatorname{ker}(f)$.</li>
<li>Determina para qué valores de $a$ el vector $(a,1,a,a)$ pertenece a $\operatorname{Im}(f)$.</li>
<li>Calcula la matriz asociada a $f$ respecto de las bases $\overline{B}$ de $\mathbb{R}^3$ y $B_c$ de $\mathbb{R}^4$, siendo
$$\overline{B}=\{ (1,-1,-1),(0,1,1),(0,0,1)\}.$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Determinar la base más sencilla de $\operatorname{Im}(f)$ y unas ecuaciones cartesianas del $\operatorname{ker}(f)$.<br>
Para calcular la base más sencilla de la Imagen realizamos operaciones elementales por columnas hasta obtener la forma de Hermite por columnas:
$$ \begin{pmatrix}
1 & -1 & 0\\
1 & 2 & 1 \\
0 & 1 & 1 \\
1 & 1 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0\\
1 & 3 & 1 \\
0 & 1 & 1 \\
1 & 2 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0\\
0 & 1& 0 \\
-1 & 1 & -2 \\
0 & 1 & -1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0\\
0 & 1& 0 \\
0 & 0 & 1 \\
1/2 & 1/2 & 1/2
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix([[1,-1,0],[1,2,1],[0,1,1],[1,1,1]])
show(A,"~",((A.T).rref()).T)
</script>
</div>

Luego la base más sencilla de $\operatorname{Im}(f) $ es $\{(1,0,0,1/2),(0,1,0,1/2),(0,0,1,1/2)\}$.<br>
Para obtener las cartesianas del núcleo imponemos $AX=0$:
$$\operatorname{ker}(f)\equiv \left\{ \begin{array}{rl}
x-y&=0,\\
x+2y+z&=0,\\
y+z&=0,\\
x+y+z&=0.
\end{array}\right. \sim_f \left\{ \begin{array}{rl}
x-y&=0,\\
y+z&=0,\\
x&=0.
\end{array}\right. \sim_f \left\{ \begin{array}{rl}
x&=0,\\
y&=0,\\
z&=0.
\end{array}\right. $$ 
</li>

<li>Determinar para qué valores de $a$ el vector $(a,1,a,a)$ pertenece a $\operatorname{Im}(f)$.<br>
Para que $(a,1,a,a)\in \operatorname{Im}(f)$ tiene que ser combinación lineal de los vectores de una base, por ejemplo la más sencilla que hemos calculado, luego el rango de la matriz que forman los cuatro vectores debe ser tres, y por tanto el determinante siguiente debe ser cero:
$$\left|\begin{array}{cccc}
1 & 0 & 0 & a \\
0 & 1 & 0 & 1\\
0 & 0 & 1 & a\\
1/2 & 1/2 & 1/2 & a
\end{array}\right|=\left|\begin{array}{cccc}
1 & 0 & 0 & a \\
0 & 1 & 0 & 0\\
0 & 0 & 1 & a\\
1/2 & 1/2 & 1/2 & a-1/2
\end{array}\right|= \left|\begin{array}{ccc}
1 &  0 & a \\
0 &  1 & a\\
1/2  & 1/2 & a-1/2
\end{array}\right|=\frac{1}{2}(a-1)-\frac{1}{2}a=-\frac{1}{2}.$$
Como siempre es distinto de cero, este vector no está en la imagen de $f$ para ningún valor de $a$.
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases $\overline{B}$ de $\mathbb{R}^3$ y $B_c$ de $\mathbb{R}^4$.<br>
Usamos el "método de los cuatro pasos", comenzando calculando la imagen de los vectores de la base $\overline{B}$ multiplicando por la matriz $A$ cada uno de los vectores:
$$ \begin{pmatrix}
1 & -1 & 0\\
1 & 2 & 1\\
0 & 1 & 1\\
1 & 1 & 1
\end{pmatrix}\begin{pmatrix}
1\\ -1\\ -1
\end{pmatrix}=  \begin{pmatrix}
2\\ -2\\ -2 \\ -1
\end{pmatrix}$$
con lo que $f(1,-1,-1)=(2,-2,-2,-1)$, del mismo modo $f(0,1,1)=(-1,3,2,2)$, $f(0,0,1)=(0,1,1,1)$; como se obtienen las coordenadas en la base canónica solo queda escribirlos por columnas:
$$M(f,\overline{B}, B_c)=\begin{pmatrix}
2 & -1 & 0\\
-2 & 3 & 1\\
-2 & 2 & 1\\
-1 & 2 & 1
\end{pmatrix}.$$
</li>

</ol>
</details>
</article>

<article>
Sea $f:\mathbb{R}^{4} \to \mathbb{R}^{3}$ la aplicación lineal que, respecto de las bases canónicas, viene dada por la matriz
$$A=\begin{pmatrix}
1 & 1 & 0 & 1\\
-1 & 2 & 1 & 1\\
-1 & 2 & 1 & 1
\end{pmatrix}
$$

<ol type="a">
<li>Calcula una base de la imagen de $f$ y determina para qué valores de $a$ el vector $(a,1-a,a)$ pertenece a dicha imagen.</li>
<li>Decide de qué tipo es $f$ (inyectiva, sobreyectiva, biyectiva o ninguna de las anteriores).</li>
<li>Calcula la matriz asociada a $f$ respecto de las bases $B_c$ de $\mathbb{R}^{4}$ y $\overline{B}$ de $\mathbb{R}^{3}$ siendo
$$\overline{B}=\{ (1,-1,-1),(0,1,1),(0,0,1)\}.$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular una base de la imagen de $f$ y determinar para qué valores de $a$ el vector $(a,1-a,a)$ pertenece a dicha imagen.<br>
$$A=\begin{pmatrix}
1 & 1 & 0 & 1\\
-1 & 2 & 1 & 1\\
-1 & 2 & 1 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
-1 & 3 & 1 & 2\\
-1 & 3 & 1 & 2
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 1 & 0 & 0
\end{pmatrix}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

<div class="sage">
<script type="text/x-sage">
A=matrix([[1,1,0,1],[-1,2,1,1],[-1,2,1,1]])
show(A,"~",((A.T).rref()).T)
</script>
</div>

Así que la base de $Im(f)$ que obtenemos es $\{ (1,0,0),(0,1,1)\}$.<br>
Para que $(a,1-a,a)\in Im(f)$ debe ser combinación lineal de estos vectores y por tanto el determinante de la matriz 
$$\begin{pmatrix}
1 & 0 & a\\
0 & 1 & 1-a\\
0 & 1 & a
\end{pmatrix}$$
debe ser $0$, así que debe ser $a-(1-a)=0$. Por tanto este vector está en la imagen para $a=1/2$ y no está en el resto de casos.
</li>

<li>Decidir de qué tipo es $f$.<br>
Como $\operatorname{dim}(\operatorname{Im}(f))=2\not = \operatorname{dim}(\mathbb{R}^{3})$, entonces no es sobreyectiva.
Usando la fórmula de las dimensiones:
$$\operatorname{dim}(\mathbb{R}^{4})= \operatorname{dim}(\operatorname{ker}(f)) + \operatorname{dim}(\operatorname{Im}(f))$$
obtenemos que $\operatorname{dim}(\operatorname{ker}(f))=2$ y por tanto como $\operatorname{ker}(f)\not = \{0\}$, entonces tampoco es inyectiva.
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases $B_c$ de $\mathbb{R}^{4}$ y $\overline{B}$ de $\mathbb{R}^{3}$.<br>
Como de los datos del problema obtenemos
$$\begin{array}{rl}
f(1,0,0,0)=&(1,-1,-1),\\
f(0,1,0,0)=&(1,2,2),\\
f(0,0,1,0)=&(0,1,1),\\
f(0,0,0,1)=&(1,1,1).
\end{array}$$
Solo hay que calcular las coordenadas de estos vectores respecto de $\overline{B}$
$$\begin{array}{rl}
f(1,0,0,0)=&(1,0,0)_{\overline{B}},\\
f(0,1,0,0)=&(1,3,0)_{\overline{B}},\\
f(0,0,1,0)=&(0,1,0)_{\overline{B}},\\
f(0,0,0,1)=&(1,2,0)_{\overline{B}},
\end{array}$$
y por tanto, 
$$\mathcal{M}(f,B_c,\overline{B})= \begin{pmatrix}
1 & 1 & 0 & 1\\
0 & 3 & 1 & 2\\
0 & 0 & 0 & 0
\end{pmatrix}.$$
</li>
</ol>

</details>
</article>

<article>
Dada la aplicación lineal $f$ que verifica:
$$\begin{array}{c}
 f(-1,-1,1)=(0,0,0,0),\\
 f(1,1,0)=(2,1,1,2),\\
 f(0,1,1)=(3,1,2,3).\\
\end{array}
$$

<ol type="a">
<li>Calcula la matriz asociada respecto de las bases canónicas.</li>
<li>Calcula la matriz asociada respecto de las bases
$$B=\{(1,1,0),(0,1,1),(-1,-1,1)\},$$
$$B'=\{(1,0,1,1),(0,1,-1,0),(0,0,1,1),(0,0,0,1)\}.$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular la matriz asociada respecto de las bases canónicas.<br>
La matriz asociada respecto de las bases canónicas se obtiene al calcular
$$\begin{array}{c}
 f(1,0,0)=(\_,\_,\_,\_)_{B_c},\\
 f(0,1,0)=(\_,\_,\_,\_)_{B_c},\\
 f(0,0,1)=(\_,\_,\_,\_)_{B_c}.\\
\end{array}
$$
Estos vectores de $\mathbb{R}^{4}$ escritos por columnas forman la matriz que nos piden.
Para calcular cada uno de ellos usaremos los datos del problema y que $f$ es una aplicación lineal. Por ejemplo,
como 
$$f(0,0,1)=f((-1,-1,1)+(1,1,0)),$$
entonces, usando que $f$ es lineal en el segundo elemento de la igualdad nos dará
$$f(0,0,1)=f(-1,-1,1)+f(1,1,0),$$
y como esos datos los proporciona el enunciado, tenemos
$$f(0,0,1)=(0,0,0,0)+(2,1,1,2)=(2,1,1,2).$$
Así obtendríamos una de las columnas de la matriz. Este procedimiento puede automatizarse escribiendo una matriz formada por dos bloques:
$$\left( \begin{array}{rrr}
          -1 & 1 & 0\\
          -1 & 1 & 1\\
           1 & 0 & 1\\
\hline 
           0 & 2 & 3\\
           0 & 1 & 1\\
           0 & 1 & 2\\
           0 & 2 & 3
         \end{array} \right),
$$
en la que en cada columna se ha escrito un vector del primer espacio y debajo su imagen. Realizando operaciones elementales por columnas hasta obtener en el bloque superior la base canónica abajo obtendremos las imágenes de los vectores de la base canónica.
 $$\left( \begin{array}{rrr}
          -1 & 1 & 0\\
          -1 & 1 & 1\\
           1 & 0 & 1\\
\hline 
           0 & 2 & 3\\
           0 & 1 & 1\\
           0 & 1 & 2\\
           0 & 2 & 3
         \end{array} \right) \sim_{c}
\left( \begin{array}{rrr}
          1 & 0 & 0\\
          0 & 1 & 0\\
          0 & 0 & 1\\
\hline 
           1 & 1 & 2\\
           1 & 0 & 1\\
           0 & 1 & 1\\
           1 & 1 & 2
         \end{array} \right).
$$
El bloque inferior es la matriz asociada a $f$ respecto de las bases canónicas.
$$
\mathcal{M}(f,B_{c},B_{c})=\left( \begin{array}{rrr}
           1 & 1 & 2\\
           1 & 0 & 1\\
           0 & 1 & 1\\
           1 & 1 & 2
         \end{array} \right).
$$

Otra forma de resolver este ejercicio es la siguiente. Recoredemos que
$$\begin{array}{c}
 f(1,1,0)=(2,1,1,2),\\
 f(0,1,1)=(3,1,2,3),\\
 f(-1,-1,1)=(0,0,0,0).\\
\end{array}
$$
es decir, las imágenes de los vectores de la base $B$ escritos por sus coordenadas en $B_c$ de $\mathbb{R}^4$, y por tanto escritos por columnas nos dan la matriz $\mathcal{M}(f,B,B_c)$. 
Llamémosle 
$$C=\mathcal{M}(f,B,B_c)=
\left( \begin{array}{rrr}
           2 & 3 & 0\\
           1 & 1 & 0\\
           1 & 2 & 0\\
           2 & 3 & 0 
                    \end{array} \right).$$

Tenemos el diagrama:

$$
\begin{array}{llcr}
     &                       &         C              & \\
 f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{4}_{B_{c}}   \\
    &                       &                        &                     \\
    &   \downarrow_{P}&              & \updownarrow_{I} \\
    &                        &         ?             &                   \\
f: & \mathbb{R}^{3}_{B_c}     & \longrightarrow        &\mathbb{R}^{4}_{B_c}   \\
\end{array}
$$

y por tanto la matriz $\mathcal{M}(f,B_c,B_c)=I C P^{-1}=CP^{-1}=A$.<br>

También puede usarse esta matriz $C$ para obtener la solución del segundo apartado, en este caso siguiendo el diagrama:

$$
\begin{array}{llcr}
     &                       &         C              & \\
 f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{4}_{B_{c}}   \\
    &                       &                        &                     \\
    &   \updownarrow_{I}&              & \uparrow_{Q} \\
    &                        &         ?             &                   \\
f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{4}_{B'}   \\
\end{array}
$$
</li>

<li>Calcula la matriz asociada respecto de las bases B y B'.<br>
Una vez que es conocida la matriz asociada a una aplicación lineal respecto de dos bases, por ejemplo 
$\mathcal{M}(f,B_{c},B_{c})$, podemos dibujar un esquema en el que se reflejan los cambios de base a realizar en cada uno de los espacios:

$$
\begin{array}{llcr}
     &                       &         A              & \\
 f: & \mathbb{R}^{3}_{B_{c}}     & \longrightarrow        &\mathbb{R}^{4}_{B_{c}}   \\
    &                       &                        &                     \\
    &   \uparrow_P&              & \uparrow_{Q} \\
    &                        &         ?             &                   \\
f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{4}_{B'}   \\
\end{array}
$$

El cambio de base de $B$ a $B_c$ en $\mathbb{R}^3$ tiene matriz asociada 
$$P=\left( \begin{array}{rrr}
           1 & 0 & -1\\
           1 & 1 & -1\\
           0 & 1 & 1\\
                    \end{array} \right).
$$
El cambio de base de $B'$ a $B_c$ en $\mathbb{R}^4$ tiene matriz asociada 
$$Q=\left( \begin{array}{rrrr}
           1 & 0 & 0 & 0\\
           0 & 1 & 0 & 0\\
           1 & -1 & 1 & 0\\
           1 & 0 & 1 & 1
                    \end{array} \right).$$
Para realizar el recorrido desde $\mathbb{R}^3_{B}$ a $\mathbb{R}^4_{B'}$ tenemos que multiplicar un vector primero por $P$, luego por $A$ y por último por $Q^{-1}$. Es decir, puesto que el vector se escribe a la derecha por columnas tendremos la fórmula

$$Y'=Q^{-1} A P X,$$
y por tanto $\mathcal{M}(f,B,B')=Q^{-1} A P$. </li>
</ol>
</details>
</article>

<article>

Una aplicación lineal $f:\mathbb{R}^3 \longrightarrow \mathbb{R}^4 $ viene dada por:
$$\begin{array}{c}
 f(1,0,1)=(1+a,1,1,1-a),\\
 f(1,1,1)=(1,1+a,1-a,1),\\
 f(0,1,1)=(1,a,a,1).\\
\end{array}
$$

<ol type="a">
<li>Estudia las dimensiones del núcleo y la imagen de $f$ según los valores del parámetro $a$.</li>
<li>Calcula la matriz asociada a $f$ respecto de las bases canónicas de $\mathbb{R}^3$ y $\mathbb{R}^4$.</li>
<li>¿Para qué valores de $a$ el vector $(1,a,1+a,1)$ está en la imagen de $f$?</li>
<li>¿Para qué valores de $a$ el vector $(1,-1,0)$ está en el núcleo de $f$?</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Estudiar las dimensiones del núcleo y la imagen de $f$ según los valores del parámetro $a$.<br>
Para estudiar las dimensiones del núcleo y la imagen tenemos que calcular el rango de una matriz asociada a $f$, y es indiferente respecto de qué bases esté considerada. Lo más inmediato es utilizar como base de $\mathbb{R}^3$ la base $B=\{(1,0,1),(1,1,1),(0,1,1)\}$ puesto que conocemos sus imágenes, y como base de $\mathbb{R}^4$ la base canónica, pues las imágenes que conocemos están dadas respecto de ella (al no hacerse mención en la expresión  a la base usada se trata de las componentes del vector). Así que usamos los datos del enunciado y tenemos
$$C=\mathcal{M}(f,B,B_c)=
\left( \begin{array}{ccc}
           1+a & 1 & 1\\
           1 & 1+a & a\\
           1 & 1-a & a\\
           1-a & 1 & 1 
                    \end{array} \right),$$
de la que tenemos que estudiar el rango. Como el máximo posible es tres, entonces elegimos un menor de orden tres, por ejemplo:
$$\left| \begin{array}{ccc}
           1 & 1+a & a\\
           1 & 1-a & a\\
           1-a & 1 & 1 
                    \end{array} \right|= \left| \begin{array}{ccc}
           1 & 1+a & a\\
           0 & -2a & 0\\
           1-a & 1 & 1 
                    \end{array} \right|= (-2a)(1-a+a^2).$$
Como $a^2-a+1$ es siempre distinto de cero (la ecuación correspondiente no tiene raices reales), entonces este determinante sólo es cero cuando $a=0$. Por tanto, cuando $a\not = 0$, el rango de la matriz es tres. En el caso $a=0$  sustituyendo en la matriz es fácil observar que el rango es dos. <br>
Resumiendo lo que hemos obtenido:<br>
Si $a\not = 0$ la dimensión de la imagen de $f$ es tres y el núcleo es trivial.<br>
Si $a = 0$ la dimensión de la imagen de $f$ es dos y el núcleo tiene dimensión uno.<br>
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases canónicas de $\mathbb{R}^3$ y $\mathbb{R}^4$.<br>
De los datos del enunciado, procediendo como en el ejercicio anterior, podemos obtener las imágenes de los vectores de la base canónica de $\mathbb{R}^3$:
$$\left( \begin{array}{ccc}
          1 & 1 & 0\\
          0 & 1 & 1\\
          1 & 1 & 1\\
\hline 
            1+a & 1 & 1\\
           1 & 1+a & a\\
           1 & 1-a & a\\
           1-a & 1 & 1 
         \end{array} \right) \sim_{c}
\left( \begin{array}{ccc}
          1 & 0 & 0\\
          0 & 1 & 0\\
          0 & 0 & 1\\
\hline 
           0 & -a & 1+a\\
           1 & a & 0\\
           1-2a & -a & 2a\\
           0 & a & 1-a
         \end{array} \right),
$$
y por tanto 
$$A=\mathcal{M}(f,B_c,B_c)=
\left( \begin{array}{ccc}
           0 & -a & 1+a\\
           1 & a & 0\\
           1-2a & -a & 2a\\
           0 & a & 1-a
                    \end{array} \right).$$
</li>

<li>¿Para qué valores de $a$ el vector $(1,a,1+a,1)$ está en la imagen de $f$?<br>
Las columnas de una matriz asociada a $f$ nos da un sistema de generadores de $Im(f)$, para probar que un vector pertenece al subespacio generado por un conjunto de vectores tenemos que ver si es combinación lineal de ellos, o lo que es lo mismo, que al añadir ese vector el rango de la matriz no cambia. Podemos usar por ejemplo la matriz $C$ (o también $A$, puesto que ambas están referidas a la base canónica de $\mathbb{R}^4$):
$$\left( \begin{array}{ccc|c}
           1+a & 1 & 1 & 1\\
           1 & 1+a & a & a\\
           1 & 1-a & a & 1+a\\
           1-a & 1 & 1 & 1 
                    \end{array} \right).$$
Si a la última columna le restamos la tercera y desarrollamos el determinante por la cuarta columna queda:
$$\left| \begin{array}{cccc}
           1+a & 1 & 1 & 0\\
           1 & 1+a & a & 0\\
           1 & 1-a & a & 1\\
           1-a & 1 & 1 & 0 
                    \end{array} \right|=\left| \begin{array}{ccc}
           1+a & 1 & 1 \\
           1 & 1+a & a \\
          1-a & 1 & 1  
                    \end{array} \right|=\left| \begin{array}{ccc}
           1+a & 1 & 1 \\
           1 & 1+a & a \\
          -2a & 0 & 0  
                    \end{array} \right|=-2a.$$
Cuando $a\not = 0$, el rango de $C$ era tres, y el rango al añadir el vector es cuatro, luego el vector no pertenece a la imagen.<br>
En el caso $a=0$ el rango de $C$ es dos y al añadir el vector $(1,0,1,1)$ el rango aumenta a tres, así que no pertenece a la imagen.</li>

<li>¿Para qué valores de $a$ el vector $(1,-1,0)$ está en el núcleo de $f$?<br>
En el caso $a\not =0$ el núcleo se reduce al vector $(0,0,0)$,
así que el vector dado no pertenece al núcleo. <br>
En el caso $a=0$ podemos calcular la imagen del vector $(1,-1,0)$, para lo que tenemos que usar la matriz asociada a $f$ respecto de la base canónica de $\mathbb{R}^3$, es decir $A$:
$$f(1,-1,0)=A\left( \begin{array}{r}
                     1\\
-1\\
0
                    \end{array}\right)=\left( \begin{array}{ccc}
           0 & 0 & 1\\
           1 & 0 & 0\\
           1 & 0 & 0\\
           0 & 0 & 1
                    \end{array} \right)\left( \begin{array}{r}
                     1\\
-1\\
0
                    \end{array}\right)=\left( \begin{array}{r}
                     0\\
1\\
1\\
0
                    \end{array}\right)
$$
y como no es el vector nulo, no pertenece al núcleo tampoco en este caso.</li>
</ol>
</details>
</article>

<article>

Se considera la aplicación lineal
$$
F: \mathcal{P}_3(\mathbb{R}) \longrightarrow \mathcal{M}_2(\mathbb{R})
$$
determinada por:
$$
{\small
\begin{array}{rcl}
F(1-x) & = & \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix}, \\
F(1+x) & = & \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}, \\
F(x^2+x^3) & = & \begin{pmatrix} 2 & 0 \\ 0 & 2 \end{pmatrix}, \\
F(x^2-x^3) & = & \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}, \\
\end{array}
}
$$


<ol type="a">
<li>Determinar la matriz asociada a $F$ respecto de las respectivas bases estándar y	el valor de $F(p(x))$ para un polinomio 
$p(x)=a_0+a_1 x+ a_2 x^2 +a_3 x^3\in \mathcal{P}_3(\mathbb{R})$.</li>
<li>Determinar la matriz asociada a $F$ respecto de las bases
$\overline{B}=\{1+x, 1-x, x^2+x^3, x^2-x^3 \}$ de $\mathcal{P}_3(\mathbb{R})$ y 
$\overline{B'}=\biggl\{
\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix},
\begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix},
\begin{pmatrix} 1 & 1 \\ 2 & 3 \end{pmatrix},
\begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}
\biggr\}$ de $\mathcal{M}_2(\mathbb{R})$.</li>
<li>Determinar bases del núcleo y la imagen de $F$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Determinar la matriz asociada a $F$ respecto de las respectivas bases estándar y	el valor de $F(p(x))$.<br>
Para determinar la matriz asociada solo tenemos que escribir las imágenes de $1,x,x^2,x^3$ en función de la base estándar de $\mathcal{M}_2(\mathbb{R})$ y colocarlos por columnas.
Usando los datos dados:

$$F(1)=\frac{1}{2}(F(1+x)+F(1-x))=\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}=(1,1,1,1)_{B_{sm}},$$

$$F(x)=\frac{1}{2}(F(1+x)-F(1-x))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}},$$

$$F(x^2)=\frac{1}{2}(F(x^2+x^3)+F(x^2-x^3))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}},$$

$$F(x^3)=\frac{1}{2}(F(x^2+x^3)-F(x^2-x^3))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}}.$$

Así,
$$M(F,B_{sp},B_{sm})=\left(\begin{array}{llll}
1 & 1 & 1 & 1\\
1 & 0 & 0 & 0\\
1 & 0 & 0 & 0\\
1 & 1 & 1 & 1
\end{array}\right)=A.$$ 
Dado un polinomio $p(x)=a_0+a_1x+a_2x^2+a_3x^3=(a_0,a_1,a_2,a_3)_{B_{sp}}$ calculamos
$$F(p(x))=A\left( \begin{array}{l}
a_0\\
a_1\\
a_2\\
a_3
\end{array}\right)=\left( \begin{array}{c}
a_0+a_1+a_2+a_3\\
a_0\\
a_0\\
a_0+a_1+a_2+a_3
\end{array}\right)_{B_{sm}}.$$
Así que
$$F(p(x))=\left( \begin{array}{cc}
a_0+a_1+a_2+a_3 &
a_0\\
a_0&
a_0+a_1+a_2+a_3
\end{array}\right)=
\left( \begin{array}{cl}
p(1) &
p(0)\\
p(0)&
p(1)
\end{array}\right).
$$</li>

<li>Determinar la matriz asociada a $F$ respecto de las bases $\overline{B}$ y $\overline{B'}$.<br>
Expresamos las imágenes de los vectores de $\overline{B}$ y obtenemos (es muy fácil en este caso) sus coordenadas respecto de $\overline{B'}$:
$$
{\small
\begin{array}{rcll}
F(1+x) & = & \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix} 
& = (2,-1,0,0)_{\overline{B'}},\\
F(1-x) & = & \begin{pmatrix} 0 & 1 \\ 1 & 0 \end{pmatrix} 
& = (0,1,0,0)_{\overline{B'}},\\
F(x^2+x^3) & = & \begin{pmatrix} 2 & 0 \\ 0 & 2 \end{pmatrix} 
& = (2,-2,0,0)_{\overline{B'}},\\
F(x^2-x^3) & = & \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix} 
& = (0,0,0,0)_{\overline{B'}}.\\
\end{array}
}
$$
Así,
$$M(F,\overline{B},\overline{B'})=
\left(\begin{array}{rrrr}
2  & 0 & 2 & 0\\
-1 & 1 & -2 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
\end{array}\right)=C.$$

Alternativamente, de los datos de las bases dadas tenemos que 
$$
P=\left(\begin{array}{rrrr}
 1 & 1 & 0 & 0 \\
 1 & -1 & 0 & 0 \\
 0 & 0 & 1 & 1 \\
 0 & 0 & 1 & -1
 \end{array} \right)  
 \mbox{ y    }\;\; 
 Q=\begin{pmatrix}
 1 & 0 & 1 & 1 \\
 1 & 1 & 1 & 2 \\
 1 & 1 & 2 & 3 \\
 1 & 0 & 3 & 4
 \end{pmatrix} 
$$ 
son las matrices de cambio de base de $\overline{B}$ a $B_{sp}$ y de $\overline{B'}$ a $B_{sm}$ respectivamente. 

Entonces $M(F,\overline{B}, \overline{B'})=Q^{-1}AP$

Calculamos 
$$Q^{-1}=\left(\begin{array}{rrrr}
1 & 1 & -1 & 0 \\
0 & -1 & 2 & -1 \\
1 & -3 & 3 & -1 \\
-1 & 2 & -2 & 1
\end{array}\right).
$$
Y finalmente,
$$ 
M(F,\overline{B}, \overline{B'})
=
Q^{-1}AP
=
\left(\begin{array}{cccc}
2  & 0 & 2 & 0\\
-1 & 1 & -2 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
\end{array}\right)=C.
$$</li>

<li>Determinar bases del núcleo y la imagen de $F$.<br>
Como $\operatorname{rg}(A)=\operatorname{rg}(C)=2$, entonces $\operatorname{dim}(\operatorname{Im}(F))=2$ y $\operatorname{dim}(\operatorname{ker}(F))=2$. Una base de la  imagen (obtenida por operaciones elementales en las columnas de $A$) puede ser: 
$$\left\{\begin{pmatrix}
1 & 0 \\ 
0 & 1 
\end{pmatrix}, 
\begin{pmatrix} 0 & 1 \\ 
1 & 0 
\end{pmatrix}\right\}=\left\{(1,0,0,1)_{B_{sm}},(0,1,1,0)_{B_{sm}}\right\}.$$

También observando $A$ obtenemos que $F(x-x^2)=F(x-x^3)=0$ y por tanto una base del núcleo puede ser: 
$$\{ x-x^2, x-x^3\}=\{(0,1,-1,0)_{B_{sp}},(0,1,0,-1)_{B_{sp}} \}.$$

</li>
</ol>
</details>
</article>

<article>

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

<details>
<summary>Solución</summary>

<ol type="a">
<li>Estudiar qué condición han de cumplir los parámetros $a$ y $b$ para que $A$ sea diagonalizable.<br>
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
Nos da las ecuaciones $y=0; t=0$ y por tanto tiene dimensión dos, así que como no coincide con la multiplicidad algebraica, entonces no es diagonalizable.<br>

Si $a\not =b$, hay dos valores propios $\lambda=a$ con multiplicidad algebraica dos y $\lambda=b$ también con multiplicidad algebraica dos.<br>
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
Nos da las ecuaciones $(a-b)x+y=0$, $(a-b)z+t=0$ y por tanto tiene dimensión dos, así que coincide con la multiplicidad algebraica. Por tanto en este caso la matriz si es diagonalizable.
</li>

<li>Para los valores $a=1$, $b=-1$ determinar su forma diagonal $D$ y una matriz de paso $P$.<br>
Utilizando los cálculos del segundo caso del apartado anterior  tenemos que 
$$V_{\lambda=1}\equiv \left\{ \begin{array}{l}
y=0,\\
t=0.
\end{array}\right.$$
Y una base es $\{(1,0,0,0),(0,0,1,0)\}$. 
$$V_{\lambda= -1}\equiv \left\{ \begin{array}{l}
2x+y=0,\\
2z+t=0.
\end{array}\right.$$
Y una base es $\{(1,-2,0,0),(0,0,1,-2)\}$. <br>
Por tanto, 
$$D=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & -1 & 0\\
0 & 0 & 0 & -1
\end{pmatrix}, \hspace{1cm} P=\begin{pmatrix}
1 & 0 & 1 & 0\\
0 & 0 & -2 & 0\\
0 & 1 & 0 & 1\\
0 & 0 & 0 & -2
\end{pmatrix}.$$</li>
</ol>

</details>
</article>

<article>

<ol type="a">
<li>Dado el endomorfismo de $\mathbb{R}^3$ que viene dado por
 $$\begin{array}{ll}
 f(1,1,-1)&=(1,1,1),\\
 f(1,-1,1)&=(1,1,0),\\
 f(-1,1,1)&=(1,0,0).
 \end{array}$$
 Calcula la matriz asociada a $f$ respecto de la base
 $B'=\{(1,1,-1),(1,-1,1),(-1,1,1)\}$</li>
<li>Dada la matriz $$A=\left(
\begin{array}{rrr}
  1 & a & a \\
  -1 & 1 & -1 \\
  1 &0  & 2 \\
\end{array}
\right).
$$
Estudia para qué valores de $a\in\mathbb{R}$  es diagonalizable y para aquellos que lo sea obtén $D$ diagonal y $P$ regular tales que $D=P^{-1}AP$.</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular la matriz asociada a $f$ respecto de la base $B'$
Observamos que nos dan las imágenes de los vectores de la base $B'$, pero estas vienen dadas por sus coordenadas en la base canónica y debemos calcular las coordenadas también en la base $B'$. Por tanto necesitamos la matriz de cambio de base de $B_c$ a $B'$, que es la inversa de la matriz
$$P=\left(\begin{array}{rrr}
  1 & 1 & -1 \\
  1 & -1 & 1 \\
  -1 & 1  & 1 \\
\end{array}
\right).
 $$
 La calculamos:
 $$\begin{align*}
 \left(\begin{array}{rrr|ccc}
    1 & 1 & -1 & 1 & 0 & 0 \\
    1 & -1 & 1 & 0 & 1 & 0\\
    -1 & 1  & 1 & 0 & 0 & 1\\
  \end{array}
\right)&\sim_f
\left(\begin{array}{rrr|rrr}
    1 & 1 & -1 & 1 & 0 & 0 \\
    0 & -2 & 2 & -1 & 1 & 0\\
    0 & 2  & 0 & 1 & 0 & 1\\
  \end{array}
\right)\\
 &\sim_f \left(\begin{array}{rrr|rrr}
    1 & 1 & -1 & 1 & 0 & 0 \\
    0 & 2  & 0 & 1 & 0 & 1\\
    0 & 0  & 2 & 0 & 1 & 1\\
  \end{array}
\right)\sim_f
\left(\begin{array}{rrr|ccc}
    1 & 0 & 0 & 1/2 & 1/2 & 0 \\
    0 & 1  & 0 & 1/2 & 0 & 1/2\\
    0 & 0  & 1 & 0 & 1/2 & 1/2\\
  \end{array}
\right),\end{align*}$$
y ahora calculamos las coordenadas de $(1,1,1),(1,1,0),(1,0,0)$ respecto de $B'$:
$$\left(\begin{array}{ccc}
  1/2 & 1/2 & 0 \\
  1/2 & 0 & 1/2\\
  0 & 1/2 & 1/2\\
  \end{array}
\right)\left(\begin{array}{rrr}
  1 & 1 & 1 \\
  1 & 1 & 0\\
  1 & 0 & 0\\
  \end{array}
\right)=  \left(\begin{array}{ccc}
  1 & 1 & 1/2 \\
  1 & 1/2 & 1/2\\
  1 & 1/2 & 0\\
  \end{array}\right).$$
Como
$$\begin{array}{ll}
 f(1,1,-1)&=(1,1,1)_{B'},\\
 f(1,-1,1)&=(1,1/2,1/2)_{B'},\\
 f(-1,1,1)&=(1/2,1/2,0)_{B'},
 \end{array}$$
la matriz asociada a $f$ respecto de $B'$ es
$$C=\left(\begin{array}{ccc}
1 & 1 & 1/2 \\
1 & 1/2 & 1/2\\
1 & 1/2 & 0\\
\end{array}\right).$$
</li>

<li>Estudiar para qué valores de $a\in\mathbb{R}$  es diagonalizable y obtener $D$ y $P$.<br>
En primer lugar calculamos los valores propios:
 $$|A-\lambda I|=\left|\begin{array}{ccc}
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
=(2-\lambda)(1-\lambda)^2,$$
 luego los valores propios son $\lambda=1$ con multiplicidad algebraica dos, y $\lambda=2$ con multiplicidad algebraica uno, y por tanto su multilicidad geométrica también es uno. Es necesario establecer para qué casos la multiplicidad geométrica de $\lambda=1$ es dos para que sea diagonalizable.<br>
 <strong>$V_{\lambda=1}$:</strong>
 $$\left(\begin{array}{ccc}
 0 & a & a \\
 -1 & 0 & -1 \\
  1 &0  & 1 \\
\end{array}\right)\sim_f \left(\begin{array}{ccc}
 1 &0  & 1 \\
 0 & a & a \\
 0 & 0 & 0 \\
 \end{array}\right).$$
 Si $a\not =0$ serían dos ecuaciones cartesianas y $\operatorname{dim}(V_{\lambda=1})=1$, luego solo es diagonalizable para $a=0$. En ese caso la cartesiana  de este subespacio propio es $x+z=0$ y por tanto una base es $\{(1,0,-1),(0,1,0)\}$.<br>
<strong>$V_{\lambda=2}$:</strong>
 $$\left(\begin{array}{ccc}
 -1 & 0 & 0 \\
 -1 & -1 & -1 \\
  1 &0  & 0 \\
\end{array}\right)\sim_f \left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 1 \\
  0 &0  & 0 \\
\end{array}\right),$$
que tiene cartesianas $\left\{\begin{array}{l} x=0,\\ y+z=0.\end{array}\right.$ Así una base es $\{(0,1,-1)\}$.
Por tanto
$$D=\left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 0 \\
  0 &0  & 2 \\
\end{array}\right), \hspace{1cm} P=\left(\begin{array}{ccc}
 1 & 0 & 0 \\
 0 & 1 & 1 \\
 -1 &0  & -1 \\
\end{array}\right).$$
</li>
</ol>
</details>
</article>

<article>
Dado el endomorfismo de $\mathbb{R}^3$ que, respecto de la base canónica, viene dado por la matriz
 $$\left(
\begin{array}{rrr}
  1 & a & a \\
  -1 & 1 & -1 \\
  1 &0  & 2 \\
\end{array}
\right).
$$

<ol type="a">
<li>Calcula las dimensiones del núcleo y la imagen para todos los valores reales de $a$.</li>
<li>¿Para qué valores de $a$ es una aplicación lineal biyectiva?</li>
<li>Calcula la matriz asociada a este endomorfismo respecto de la base
$$ B= \{ (1,0,-1), (1,1,-1),(0,1,-1)\}.$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular las dimensiones del núcleo y la imagen para todos los valores reales de $a$.<br>
Puesto que  $\operatorname{dim}(\operatorname{Im}(f))=\operatorname{rg}(A)$, calculamos el rango de $A$.
$$\left(
    \begin{array}{ccc}
      1 & a & a \\
      -1 & 1 & -1 \\
      1 & 0 & 2 \\
    \end{array}
  \right)\sim_f \left(
    \begin{array}{ccc}
      1 & a & a \\
      0 & 1+a & a-1 \\
      0 & -a & 2-a \\
    \end{array}
  \right)\sim_f \left(
    \begin{array}{ccc}
      1 & a & a \\
      0 & 1 & 1 \\
      0 & -a & 2-a \\
    \end{array}
  \right)\sim_f\left(
    \begin{array}{ccc}
      1 & 0 & 0 \\
      0 & 1 & 1 \\
      0 & 0 & 2 \\
    \end{array}
  \right),
$$
luego el $\operatorname{rg}(A)=3$ para cualquier valor de $a$. También lo podemos hacer por determinantes:

$$\left|
    \begin{array}{ccc}
      1 & a & a \\
      -1 & 1 & -1 \\
      1 & 0 & 2 \\
    \end{array}
  \right|=\left|
    \begin{array}{ccc}
      1 & a & a \\
      0 & 1+a & a-1 \\
      0 & -a & 2-a \\
    \end{array}
  \right| = (1+a)(2-a)-(-a)(a-1)=2+2a-a-a^2-(a-a^2)=2.$$

Por lo tanto $\operatorname{dim}(\operatorname{Im}(f))=3$ para todos los valores de $a$ y como $$\operatorname{dim}(\operatorname{ker}(f))+\operatorname{dim}(\operatorname{Im}(f))=\operatorname{dim}(\mathbb{R}^3),$$  entonces $\operatorname{dim}(\operatorname{ker}(f))=0$  para todos los valores de $a$.
</li>

<li>¿Para qué valores de $a$ es una aplicación lineal biyectiva?<br>
Como $\operatorname{ker}(f)=\{0\}$, la aplicación siempre es inyectiva, y como la $\operatorname{dim}(\operatorname{Im}(f))=\operatorname{dim}(\mathbb{R}^3)$, siempre es sobreyectiva, así que es biyectiva para todos los valores de $a$.
</li>

<li>Calcular la matriz asociada a este endomorfismo respecto de la base $B$.<br>
Como conocemos los vectores de $B$ por sus coordenadas en $B_c$, la matriz $P$ viene dada por esas coordenadas.
 $$P=\left(
  \begin{array}{ccc}
   1 & 1 & 0 \\
    0 & 1 & 1 \\
   -1 & -1 & -1 \\
\end{array}
\right),$$
 
luego $$??=P^{-1}\cdot A\cdot P.$$
Calculamos $P^{-1}$:

$$\left(
    \begin{array}{ccc|ccc}
      1& 1 & 0 & 1 & 0 & 0 \\
      0 & 1 & 1 & 0 & 1 & 0 \\
      -1 & -1 & -1 & 0 & 0 & 1 \\
    \end{array}
  \right)\sim_f \left(
    \begin{array}{ccc|ccc}
      1& 1 & 0 & 1 & 0 & 0 \\
      0 & 1 & 1 & 0 & 1 & 0 \\
      0 & 0 & 1 & -1 & 0 & -1 \\
    \end{array}
  \right) \sim_f \left(
    \begin{array}{ccc|ccc}
      1& 0 & 0 & 0 & -1 & -1 \\
      0 & 1 & 0 & 1 & 1 & 1 \\
      0 & 0 & 1 & -1 & 0 & -1 \\
    \end{array}
  \right).
$$
Podemos comprobar el resultado:

$$\left(
\begin{array}{ccc}
1 & 1 & 0 \\
0 & 1 & 1 \\
-1 & -1 & -1 \\
\end{array}
\right) \left(
\begin{array}{ccc}
0 & -1 & -1 \\
1 & 1 & 1 \\
-1 & 0 & -1 \\
\end{array}
\right) =\left(
\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{array}
\right),$$
$$\mathcal{M}(f,B)=P^{-1}\cdot A\cdot P =\left(
\begin{array}{ccc}
  1 & 0 & 0 \\
  -a & 1 & 0 \\
  a & 0 & 2\\
\end{array}
\right).
$$
</li>
</ol>
</details>
</article>

<article>

Se considera el endomorfismo $f: \mathcal{M}_2(\mathbb{R}) \longrightarrow\mathcal{M}_2(\mathbb{R})$
dado por:
$$
f\begin{pmatrix} a & b \\ c & d \end{pmatrix} = \begin{pmatrix} a+b & a-b\\ c-d & c-d \end{pmatrix}.
$$

<ol type="a">
<li>Determinar la matriz asociada a $f$ respecto de la base estándar $B_s$ de $\mathcal{M}_2(\mathbb{R})$.</li>
<li>Determinar la matriz asociada a $f$ respecto de la base de $\mathcal{M}_2(\mathbb{R})$:
$$B' = \left\{\begin{pmatrix} 1 & 0 \\ 1 & 0 \end{pmatrix}, \begin{pmatrix} 1 & 0 \\ -1 & 0 \end{pmatrix},
\begin{pmatrix}0 & 1 \\ 0 & 1 \end{pmatrix}, \begin{pmatrix}0 & 1 \\ 0 & -1 \end{pmatrix}\right\}.$$</li>
<li>Determinar bases de  $Ker(f)$, $Im(f)$, $Ker(f)\cap Im(f)$ y $Ker(f)+ Im(f)$.</li>
<li>Determinar una base $B$ de $\mathcal{M}_2(\mathbb{R})$ de forma que la matriz asociada a $f$ respecto de las bases $B_s$ y $B$ sea
$$
H=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 0 & 0 & 0
\end{pmatrix}.
$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Determinar la matriz asociada a $f$ respecto de la base $B_s$.<br>

\begin{alignat}{4}
   f\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} &= \begin{pmatrix} 1 & 1\\ 0 & 0 \end{pmatrix}=(1,1,0,0)_{B_s},\qquad & f\begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix} &= \begin{pmatrix} 1 & -1\\ 0 & 0 \end{pmatrix}=(1,-1,0,0)_{B_s},\\
   f\begin{pmatrix} 0 & 0 \\ 1 & 0 \end{pmatrix} &= \begin{pmatrix} 0 & 0\\ 1 & 1 \end{pmatrix}=(0,0,1,1)_{B_s},\qquad & f\begin{pmatrix} 0 & 0 \\ 0 & 1 \end{pmatrix} &= \begin{pmatrix} 0 & 0\\ -1 & -1 \end{pmatrix}=(0,0,-1,-1)_{B_s}. 
    \notag
\end{alignat}

Así, la matriz asociada respecto de $B_s$ es
$$
A=\begin{pmatrix}
1 & 1 & 0 & 0\\
1 & -1 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 0 & 1 & -1
\end{pmatrix}.
$$
</li>

<li>Determinar la matriz asociada a $f$ respecto de la base B'.<br>
Puede construirse el diagrama correspondiente y tendremos que 
$$\mathcal{M}(f,B')= P^{-1}AP,$$ siendo $P$ la matriz de cambio de base de $B'$ a $B_s$:
$$
P=\begin{pmatrix}
1 & 1 & 0 & 0\\
0 & 0 & 1 & 1\\
1 & -1 & 0 & 0\\
0 & 0 & 1 & -1
\end{pmatrix},
$$
o también puede realizarse el mismo procedimiento que en el apartado anterior, teniendo en cuenta que ahora las imágenes hay que expresarlas en función de $B'$:

\begin{alignat}{4}
  f\begin{pmatrix} 1 & 0 \\ 1 & 0 \end{pmatrix} &= \begin{pmatrix} 1 & 1\\ 1 & 1 \end{pmatrix}=(1,0,1,0)_{B'},\qquad & f\begin{pmatrix} 1 & 0 \\ -1 & 0 \end{pmatrix} &= \begin{pmatrix} 1 & 1\\ -1 & -1 \end{pmatrix}=(0,1,0,1)_{B'},\\
  f\begin{pmatrix} 0 & 1 \\ 0 & 1 \end{pmatrix} &= \begin{pmatrix} 1 & -1\\ -1 & -1 \end{pmatrix}=(0,1,-1,0)_{B'},\qquad & f\begin{pmatrix} 0 & 1 \\ 0 & -1 \end{pmatrix} &= \begin{pmatrix} 1 & -1\\ 1 & 1 \end{pmatrix}=(1,0,0,-1)_{B'}. 
  \notag
\end{alignat}

con lo que la matriz pedida es 
$$
\begin{pmatrix}
1 & 0 & 0 & 1\\
0 & 1 & 1 & 0\\
1 & 0 & -1 & 0\\
0 & 1 &  0& -1
\end{pmatrix}.
$$
</li>

<li>Determinar bases de  $\operatorname{ker}(f)$, $\operatorname{Im}(f)$, $\operatorname{ker}(f)\cap \operatorname{Im}(f)$ y $\operatorname{ker}(f)+ \operatorname{Im}(f)$.<br>
Usando la matriz $A$, que usa coordenadas respecto de la base estándar, calculamos bases del núcleo y la imagen:
$$
\left(\frac{A}{I}\right)=\begin{pmatrix}
1 & 1 & 0 & 0\\
1 & -1 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 0 & 1 & -1\\
\hline
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
\end{pmatrix} \sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
1 & -2 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 1 & 0\\
\hline
1 & -1 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 1\\
\end{pmatrix}  \sim_c \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 1 & 0\\
\hline
1/2 & 1/2 & 0 & 0\\
1/2 & -1/2 & 0 & 0\\
0 & 0 & 1 & 1\\
0 & 0 & 0 & 1\\
\end{pmatrix}, 
$$
y obtenemos que una base de $\operatorname{Im}(f)$ es $\{(1,0,0,0)_{B_s},(0,1,0,0)_{B_s},(0,0,1,1)_{B_s}\}$ y una base de $\operatorname{ker}(f)$  es $\{ (0,0,1,1)_{B_s}\}$ con lo que es evidente que $\operatorname{ker}(f)\subset \operatorname{Im}(f)$ y por tanto $\operatorname{ker}(f)+\operatorname{Im}(f)=\operatorname{Im}(f)$ y $\operatorname{ker}(f)\cap \operatorname{Im}(f)=\operatorname{ker}(f)$.
</li>

<li>Determinar una base $B$ de $\mathcal{M}_2(\mathbb{R})$ de forma que la matriz asociada a $f$ respecto de las bases $B_s$ y $B$ sea $H$.<br>
Como nos piden que la base solo cambie en el segundo espacio, basta observar que se trata de que las coordenadas de las matrices calculadas en el primer apartado sean:

$$\begin{pmatrix} 1 & 1\\ 0 & 0 \end{pmatrix}=(1,0,0,0)_{B} 
\hspace{0.5cm} 
\begin{pmatrix} 1 & -1\\ 0 & 0 \end{pmatrix}=(0,1,0,0)_{B}
\hspace{0.5cm} 
\begin{pmatrix} 0 & 0\\ 1 & 1 \end{pmatrix}=(0,0,1,0)_{B} 
$$
Así que están determinados los tres vectores de la base $B$. Para completar la base puede elegirse cualquier matriz linealmente independiente con las tres anteriores, por ejemplo podemos tomar:

$$ \left\{ \begin{pmatrix} 1 & 1\\ 0 & 0 \end{pmatrix},\, 
\begin{pmatrix} 1 & -1\\ 0 & 0 \end{pmatrix},\,
\begin{pmatrix} 0 & 0\\ 1 & 1 \end{pmatrix},\, 
\begin{pmatrix} 0 & 0\\ 0 & 1 \end{pmatrix} \right\}.$$
</li>
</ol>
</details>
</article>

<article>

Se considera la aplicación lineal $D:\mathcal{P}_4(\mathbb{R}) \longrightarrow \mathcal{P}_3(\mathbb{R})$ dada por $D(p(x))=p'(x)$.

<ol type="a">
<li>Calcular el núcleo de $D$.</li>
<li>Determinar la matriz asociada respecto de las bases $B_{s,4}=\{1,x,x^2,x^3, x^4\}$ de $\mathcal{P}_4(\mathbb{R})$ y $B_{s,3}=\{1,x,x^2,x^3\}$ de $\mathcal{P}_3(\mathbb{R})$.</li>
<li>Determinar bases $B$ de $\mathcal{P}_4(\mathbb{R})$ y $B'$ de $\mathcal{P}_3(\mathbb{R})$ de forma que la matriz asociada a $D$ respecto de estas bases sea:
$$
M_{BB'}(D)=\begin{pmatrix}
1 & 0 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
\end{pmatrix}.
$$</li>
</ol>

<details>
<summary>Solución</summary>

<ol type="a">
<li>Calcular el núcleo de $D$.<br>
El núcleo de una aplicación lineal son los vectores cuya imagen vale cero, en este caso los polinomios cuya imagen por $D$, es decir, su derivada, vale cero. Es claro que tales polinomios son los polinomios constantes, por tanto el núcleo está formado por los polinomios constantes.
</li>

<li>Determinar la matriz asociada respecto de las bases $B_{s,4}$ y $B_{s,3}$.<br>
Para calcular dicha matriz calculamos las imágenes de los vectores de la base $B_{s,4}$ y los escribimos usando coordenadas respecto de $B_{s,3}$:
$$\begin{array}{l}
D(1)=0=(0,0,0,0)_{B_{s,3}},\\ 
D(x)=1=(1,0,0,0)_{B_{s,3}},\\ 
D(x^2)=2x=(0,2,0,0)_{B_{s,3}},\\
D(x^3)=3x^2=(0,0,3,0)_{B_{s,3}},\\
D(x^4)=4x^3=(0,0,0,4)_{B_{s,3}}.\\ 
\end{array}.$$
Así la matriz pedida es
$$A=\begin{pmatrix}
0 & 1 & 0 & 0 & 0\\
0 & 0 & 2 & 0 & 0\\
0 & 0 & 0 & 3 & 0\\
  0 & 0 & 0 & 0 & 4\\ 
\end{pmatrix}.$$
</li>

<li>Determinar bases $B$ y $B'$ de forma que la matriz asociada a $D$ respecto de estas bases sea $M_{BB'}(D)$.<br>
 Es bastante fácil comprobar que la forma de Hermite por columnas de la matriz $A$ anterior es exactamente la que se da en este apartado. Por tanto existe una matriz regular $P$ tal que $AP= M_{BB'}(D)$. En un diagrama de cambio de base obtendríamos que solo es necesario realizar un cambio de base en el primer espacio para que la matriz asociada a $D$ sea la dada. Además esa nueva base $B$ viene dada por las columnas de $P$, mientras que en el segundo espacio no es necesario cambiar de base.<br>
 Calculamos una matriz $P$ (la solución no es única) que verifique $AP=M_{BB'}(D)$:
 $$A=\begin{pmatrix}
 0 & 1 & 0 & 0 & 0\\
 0 & 0 & 2 & 0 & 0\\
  0 & 0 & 0 & 3 & 0\\
   0 & 0 & 0 & 0 & 4\\ 
   \hline
   1 & 0 & 0 & 0 & 0\\
   0 & 1 & 0 & 0 & 0\\
 0 & 0 & 1 & 0 & 0\\
  0 & 0 & 0 & 1 & 0\\
   0 & 0 & 0 & 0 & 1\\ 
    \end{pmatrix}\sim_c \begin{pmatrix}
 1 & 0 & 0 & 0 & 0\\
 0 & 1 & 0 & 0 & 0\\
  0 & 0 & 1 & 0 & 0\\
   0 & 0 & 0 & 1& 0\\ 
   \hline
   0 & 0 & 0 & 0 & 1\\
   1 & 0 & 0 & 0 & 0\\
 0 & 1/2 & 0 & 0 & 0\\
  0 & 0 & 1/3 & 0 & 0\\
   0 & 0 & 0 & 1/4 & 0\\ 
    \end{pmatrix}.$$
Así tenemos que $B'=B_{s,3}$ y $B=\{x, x^2/2, x^3/3, x^4/4, 1\}$. 
</li>
</ol>
</details>
</article>

<article>
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

<details>
<summary>Solución</summary>

<ol type="a">
<li>Estudiar para qué valores del parámetro $a$ es $A$ diagonalizable.<br>
Calculamos la ecuación característica:
$$\begin{align*}|A-\lambda I|&= \left|\begin{array}{ccc}
a+1-\lambda & 0 &0 \\ 1 & 1-\lambda & -1 \\ 1 &-1 & 1-\lambda
\end{array}\right|= (a+1-\lambda)[(1-\lambda)^2-1]\\
&=(a+1-\lambda)(\lambda^2-2\lambda)=\lambda(a+1-\lambda)(\lambda-2).
\end{align*}$$
Cuando $a+1\not = 0,2$ entonces aparecen tres valores propios distintos, cada uno con multiplicidad algebraica 1 y por tanto la geométrica también es 1, con lo que la matriz es diagonalizable.<br> 
Quedan por estudiar dos casos:<br> 
<strong>Cuando $a=-1$:</strong> <br> 
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
nos da dos ecuaciones cartesianas y por tanto $m_g(\lambda=0)= \operatorname{dim}(V_{\lambda=0})=1$ y por tanto en este caso no es diagonalizable.<br> 
<strong>Cuando $a=1$: </strong><br> 
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
nos da una ecuación cartesiana y por tanto $m_g(\lambda=2)= \operatorname{dim}(V_{\lambda=0})=2$ y por tanto en este caso sí es diagonalizable.
</li>

<li>Para el valor $a=0$ determinar su forma diagonal $D$ y una matriz de paso $P$ de forma que $D=P^{-1}\cdot A \cdot P$.<br>
Para el caso $a=0$ tenemos los valores propios $0,1$ y $2$ que serán los elementos de la matriz diagonal. Calculamos bases de cada uno de los subespacios propios:<br> 
<strong>$\lambda=0$:</strong><br> 
$$\begin{pmatrix}
1 & 0 &0 \\ 1 & 1 & -1 \\ 1 &-1 & 1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &0 \\ 0 & 1 & -1 \\ 0 &0 & 0
\end{pmatrix},$$
nos da unas ecuaciones cartesianas y por tanto una base es $\{(0,1,1)\}$.<br> 
<strong>$\lambda=1$:</strong><br> 
$$\begin{pmatrix}
0 & 0 &0 \\ 1 & 0 & -1 \\ 1 &-1 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &-1 \\ 0 & 1 & -1 \\ 0 &0 & 0
\end{pmatrix},$$
nos da unas ecuaciones cartesianas y una base es $\{(1,1,1)\}$.<br> 
<strong>$\lambda=2$:</strong><br> 
$$\begin{pmatrix}
-1 & 0 &0 \\ 1 & -1 & -1 \\ 1 &-1 & -1
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 &0 \\ 0 & 1 & 1 \\ 0 &0 & 0
\end{pmatrix},$$
nos da unas ecuaciones cartesianas y  una base es $\{(0,1,-1)\}$.<br> 
Como solución, por ejemplo, podemos tomar
$$D=\begin{pmatrix}
0 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 2
\end{pmatrix} \hspace{2cm} P=\begin{pmatrix}
0 & 1 & 0\\
1 & 1 & 1\\
1 & 1 & -1
\end{pmatrix}. $$
</li>
</ol>
</details>
</article>


<article>
Se considera la aplicación lineal
$$
f: \mathcal{M}_2(\mathbb{R}) \longrightarrow \mathcal{M}_2(\mathbb{R}) 
$$
definida por:
$$
f\left( \begin{pmatrix} a & b \\ c & d\end{pmatrix}\right) = 
\begin{pmatrix} a+d & b+c \\ b-c & a+d\end{pmatrix}
$$
Determinar la matriz asociada a $f$ respecto a la base estándard de $\mathcal{M}_2(\mathbb{R})$ y determinar bases de $\operatorname{ker}(f)$ e $\operatorname{Im}(f)$. ¿Es $f$ inyectiva? ¿Es $f$ sobreyectiva?
<details>
<summary>Solución</summary>

La base estándar que vamos a usar en  $\mathcal{M}_2(\mathbb{R})$ es
$$ B_s= \left\{  \left( \begin{array}{rr}
1 & 0 \\
0 & 0 \\
\end{array} \right), \, \left( \begin{array}{rr}
0 & 1 \\
0 & 0 \\
\end{array} \right), \, \left( \begin{array}{rr}
0 & 0 \\
1 & 0 \\
\end{array} \right), \, \left( \begin{array}{rr}
0 & 0 \\
0 & 1 \\
\end{array} \right) \right\}.$$  
Calculamos la imagen por $f$ de cada uno de estos vectores y la escribimos en función de $B_s$. 
$$f(\left( \begin{array}{rr}
1 & 0 \\
0 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
1 & 0 \\
0 & 1 \\
\end{array} \right)=(1,0,0,1)_{B_{s}}, $$
$$f(\left( \begin{array}{rr}
0 & 1 \\
0 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
0 & 1 \\
1 & 0 \\
\end{array} \right)=(0,1,1,0)_{B_{s}}, $$
$$f(\left( \begin{array}{rr}
0 & 0 \\
1 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
0 & 1 \\
-1 & 0 \\
\end{array} \right)=(0,1,-1,0)_{B_{s}}, $$
$$f(\left( \begin{array}{rr}
0 & 0 \\
0 & 1 \\
\end{array} \right) )= \left( \begin{array}{rr}
1 & 0 \\
0 & 1 \\
\end{array} \right)=(1,0,0,1)_{B_{s}}. $$

La matriz asociada resulta de poner estos cuatro vectores por columnas:

$$ A= \left( \begin{array}{rrrr}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 0 \\
0 & 1 & -1 & 0\\
1 & 0 & 0 & 1  
\end{array} \right). $$
Para calcular simultáneamente una base del núcleo y una de la imagen añadimos la identidad bajo $A$ y hacemos operaciones elementales por columnas:
$$ \left( \begin{array}{rrrr}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 0 \\
0 & 1 & -1 & 0\\
1 & 0 & 0 & 1  \\
\hline
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1  \\
\end{array} \right)  \sim_{c}\left( \begin{array}{rrrr}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 1 & -2 & 0\\
1 & 0 & 0 & 0  \\
\hline
1 & 0 & 0 & -1 \\
0 & 1 & -1 & 0 \\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1  \\
\end{array} \right)
\sim_{c}\left( \begin{array}{rrr|r}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0\\
1 & 0 & 0 & 0  \\
\hline
1 & 0 & 0 & -1 \\
0 & 1/2 & 1/2 & 0 \\
0 & 1/2 & -1/2 & 0\\
0 & 0 & 0 & 1  \\
\end{array} \right).
$$
Así tenemos que una base de la imagen es $\{(1,0,0,1),(0,1,0,0),(0,0,1,0)\}$ y una base del núcleo es $\{(-1,0,0,1)\}$.
Puesto que la dimensión de la imagen es tres, no es sobreyectiva. Como la dimensión del núcleo es uno, no es inyectiva.

</details>
</article>

