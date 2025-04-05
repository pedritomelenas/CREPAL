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

<input type="checkbox" id="casilla_cf" value="cfon" checked onclick="CF();"> Mostrar ejercicios sobre cuerpos finitos. 


::::: {#exr-1 .basico}

Determina cuáles de las siguientes aplicaciones son lineales:

<ol type="a">
<li class="cuerpo_finito">La aplicación $f:(\mathbb{Z}_3)^2 \rightarrow (\mathbb{Z}_3)^2$, $f(x,y)=(x+1,y+2)$.</li>
<li>La aplicación $f:V \rightarrow V'$, $f(v)=0$.</li>
<li>La aplicación $f:\mathbb{R} \rightarrow \mathbb{R}$, $f(r)=r^2$.</li>
<li class="cuerpo_finito">La aplicación $f:(\mathbb{Z}_7)^3 \rightarrow (\mathbb{Z}_7)^2$, $f(x,y,z)=(x+y+z,28x+92z)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li class="cuerpo_finito">La aplicación $f:(\mathbb{Z}_3)^2 \rightarrow (\mathbb{Z}_3)^2$, $f(x,y)=(x+1,y+2)$.

No es aplicación lineal. Basta tomar $u=(1,0)$ y $a=2$ y comprobar que no se cumple la segunda propiedad:

$$
f(au)=f(2,0)=(0,2),
$$

mientras que, 

$$
af(u)=2(2,2)=(1,1).
$$

</li>

<li>La aplicación $f:V \rightarrow V'$, $f(v)=0$.

Es aplicación lineal:

Para cualesquiera $u,v$ se tiene $f(u+v)=0=0+0=f(u)+f(v)$.

Para todo $u$ y todo $a$ se verifica $f(au)=0=a\cdot 0=af(u)$.
</li>

<li>
La aplicación $f:\mathbb{R} \rightarrow \mathbb{R}$, $f(r)=r^2$.

No es lineal, tomamos $u=1$ y $a=2$ y comprobamos que no se cumple la segunda propiedad de aplicación lineal:

$$
af(u)=2\cdot 1^2,
$$

$$
f(au)=f(2)=2^2.
$$
</li>

<li class="cuerpo_finito">La aplicación $f:(\mathbb{Z}_7)^3 \rightarrow (\mathbb{Z}_7)^2$, $f(x,y,z)=(x+y+z,28x+92z)$.

Es aplicación lineal. Cada componente de la imagen se calcula como una combinación lineal de las componentes del vector inicial.
</li>

</ol>
::::
:::::

::::: {#exr-2 .medio}

Prueba que la siguiente aplicación es lineal y calcula la matriz asociada considerando las bases estándar en cada espacio vectorial.
$$D:\mathbb{R}_3[x] \to \mathbb{R}_3[x] \text{ dada por } D(p(x))=p'(x).$$

:::: {.callout collapse="true" title="Solución"}

Es conocido que la derivada tiene las propiedades:

- La derivada de una suma es la suma de las derivadas.

Es decir, dadas dos funciones (derivables, y los polinomios lo son) $f$ y $g$ se verifica

$$
D(f+g)=D(f)+D(g),
$$

  que es la primera propiedad que debe verificar una aplicación lineal. Hay que tener cuidado porque aquí $f$ y $g$ son los vectores y $D$ es la aplicación.

- La derivada de una constante por una función es la constante por la derivada de la función.

Es decir, dadas $f$ (derivable) y $a\in \mathbb{R}$ entonces

$$
D(af)=aD(f),
$$
que es la segunda propiedad de aplicación lineal.

Calculemos ahora la matriz asociada a $D$ utilizando la base de $\mathbb{R}_3[x]$ (el conjunto de los polinomios con coeficientes en $\mathbb{R}$ de grado menor o igual que tres), $B_s=\{1,x,x^2,x^3\}$ en el espacio inicial y en el final, puesto que son el mismo:

$$
D(1)=0=(0,0,0,0)_{B_s},
$$

donde el primer cero representa a la derivada del polinomio constante igual a uno, que es el polinomio constante igual a cero, cuyas coordenadas en la base $B_s$ son $(0,0,0,0).$
Procedemos de la misma forma con los otros tres vectores de la base:

$$
\begin{array}{l}
D(x)=1=(1,0,0,0)_{B_s},\\
D(x^2)=2x=(0,2,0,0)_{B_s},\\
D(x^3)=3x^2=(0,0,3,0)_{B_s}.
\end{array}
$$

Así que la matriz asociada resulta de poner estas coordenadas por columnas:

$$
M_{B_sB_s}(D)=\begin{pmatrix}
0 & 1 & 0 & 0\\
0 & 0 & 2 & 0\\
0 & 0 & 0 & 3\\
0 & 0 & 0 & 0 
\end{pmatrix}.
$$

::::
:::::

::::: {#exr-3 .medio}

Sea $f:\mathbb{R}^3 \longrightarrow \mathbb{R}^4$ la aplicación lineal que, respecto de las bases canónicas, viene dada por la matriz

$$
A=\begin{pmatrix}
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

$$
\overline{B}=\{ (1,-1,-1),(0,1,1),(0,0,1)\}.
$$
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar la base más sencilla de $\operatorname{Im}(f)$ y unas ecuaciones cartesianas del $\operatorname{ker}(f)$.

Para calcular la base más sencilla de la Imagen realizamos operaciones elementales por columnas hasta obtener la forma de Hermite por columnas:

$$ 
\begin{pmatrix}
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

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,-1,0],[1,2,1],[0,1,1],[1,1,1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Luego la base más sencilla de $\operatorname{Im}(f) $ es $\{(1,0,0,1/2),(0,1,0,1/2),(0,0,1,1/2)\}$.

Para obtener las cartesianas del núcleo imponemos $AX=0$:

$$
\operatorname{ker}(f)\equiv \left\{ \begin{array}{rl}
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
\end{array}\right. 
$$ 

</li>

<li>Determinar para qué valores de $a$ el vector $(a,1,a,a)$ pertenece a $\operatorname{Im}(f)$.

Para que $(a,1,a,a)\in \operatorname{Im}(f)$ tiene que ser combinación lineal de los vectores de una base, por ejemplo la más sencilla que hemos calculado, luego el rango de la matriz que forman los cuatro vectores debe ser tres, y por tanto el determinante siguiente debe ser cero:

$$
\left|\begin{array}{cccc}
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
\end{array}\right|=\frac{1}{2}(a-1)-\frac{1}{2}a=-\frac{1}{2}.
$$

Como siempre es distinto de cero, este vector no está en la imagen de $f$ para ningún valor de $a$.
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases $\overline{B}$ de $\mathbb{R}^3$ y $B_c$ de $\mathbb{R}^4$.

Usamos el "método de los cuatro pasos", comenzando calculando la imagen de los vectores de la base $\overline{B}$ multiplicando por la matriz $A$ cada uno de los vectores:

$$ 
\begin{pmatrix}
1 & -1 & 0\\
1 & 2 & 1\\
0 & 1 & 1\\
1 & 1 & 1
\end{pmatrix}\begin{pmatrix}
1\\ -1\\ -1
\end{pmatrix}=  \begin{pmatrix}
2\\ -2\\ -2 \\ -1
\end{pmatrix}
$$

con lo que $f(1,-1,-1)=(2,-2,-2,-1)$, del mismo modo $f(0,1,1)=(-1,3,2,2)$, $f(0,0,1)=(0,1,1,1)$; como se obtienen las coordenadas en la base canónica solo queda escribirlos por columnas:

$$
M(f,\overline{B}, B_c)=\begin{pmatrix}
2 & -1 & 0\\
-2 & 3 & 1\\
-2 & 2 & 1\\
-1 & 2 & 1
\end{pmatrix}.
$$
</li>

</ol>
::::
:::::

::::: {#exr-4 .medio}

Sea $f:\mathbb{R}^{4} \to \mathbb{R}^{3}$ la aplicación lineal que, respecto de las bases canónicas, viene dada por la matriz

$$
A=\begin{pmatrix}
1 & 1 & 0 & 1\\
-1 & 2 & 1 & 1\\
-1 & 2 & 1 & 1
\end{pmatrix}
$$

<ol type="a">
<li>Calcula una base de la imagen de $f$ y determina para qué valores de $a$ el vector $(a,1-a,a)$ pertenece a dicha imagen.</li>
<li>Decide de qué tipo es $f$ (inyectiva, sobreyectiva, biyectiva o ninguna de las anteriores).</li>
<li>Calcula la matriz asociada a $f$ respecto de las bases $B_c$ de $\mathbb{R}^{4}$ y $\overline{B}$ de $\mathbb{R}^{3}$ siendo

$$
\overline{B}=\{ (1,-1,-1),(0,1,1),(0,0,1)\}.
$$
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular una base de la imagen de $f$ y determinar para qué valores de $a$ el vector $(a,1-a,a)$ pertenece a dicha imagen.

$$
A=\begin{pmatrix}
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

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,1,0,1],[-1,2,1,1],[-1,2,1,1]])
show(A,"~",((A.T).rref()).T)
</script>
:::

Así que la base de $Im(f)$ que obtenemos es $\{ (1,0,0),(0,1,1)\}$.

Para que $(a,1-a,a)\in Im(f)$ debe ser combinación lineal de estos vectores y por tanto el determinante de la matriz 

$$
\begin{pmatrix}
1 & 0 & a\\
0 & 1 & 1-a\\
0 & 1 & a
\end{pmatrix}
$$
debe ser $0$, así que debe ser $a-(1-a)=0$. Por tanto este vector está en la imagen para $a=1/2$ y no está en el resto de casos.
</li>

<li>Decidir de qué tipo es $f$.

Como $\dim(\operatorname{Im}(f))=2\not = \dim(\mathbb{R}^{3})$, entonces no es sobreyectiva.
Usando la fórmula de las dimensiones:

$$
\dim(\mathbb{R}^{4})= \dim(\operatorname{ker}(f)) + \dim(\operatorname{Im}(f))
$$

obtenemos que $\dim(\operatorname{ker}(f))=2$ y por tanto como $\operatorname{ker}(f)\not = \{0\}$, entonces tampoco es inyectiva.
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases $B_c$ de $\mathbb{R}^{4}$ y $\overline{B}$ de $\mathbb{R}^{3}$.

Como de los datos del problema obtenemos

$$
\begin{array}{rl}
f(1,0,0,0)=&(1,-1,-1),\\
f(0,1,0,0)=&(1,2,2),\\
f(0,0,1,0)=&(0,1,1),\\
f(0,0,0,1)=&(1,1,1).
\end{array}
$$

Solo hay que calcular las coordenadas de estos vectores respecto de $\overline{B}$

$$
\begin{array}{rl}
f(1,0,0,0)=&(1,0,0)_{\overline{B}},\\
f(0,1,0,0)=&(1,3,0)_{\overline{B}},\\
f(0,0,1,0)=&(0,1,0)_{\overline{B}},\\
f(0,0,0,1)=&(1,2,0)_{\overline{B}},
\end{array}
$$

y por tanto, 

$$
\mathcal{M}(f,B_c,\overline{B})= \begin{pmatrix}
1 & 1 & 0 & 1\\
0 & 3 & 1 & 2\\
0 & 0 & 0 & 0
\end{pmatrix}.
$$
</li>
</ol>
::::
:::::

::::: {#exr-5 .medio}
Dada la aplicación lineal $f$ que verifica:

$$
\begin{array}{c}
 f(-1,-1,1)=(0,0,0,0),\\
 f(1,1,0)=(2,1,1,2),\\
 f(0,1,1)=(3,1,2,3).\\
\end{array}
$$

<ol type="a">
<li>Calcula la matriz asociada respecto de las bases canónicas.</li>
<li>Calcula la matriz asociada respecto de las bases

$$
B=\{(1,1,0),(0,1,1),(-1,-1,1)\},
$$

$$
B'=\{(1,0,1,1),(0,1,-1,0),(0,0,1,1),(0,0,0,1)\}.
$$
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular la matriz asociada respecto de las bases canónicas.

La matriz asociada respecto de las bases canónicas se obtiene al calcular

$$
\begin{array}{c}
 f(1,0,0)=(\_,\_,\_,\_)_{B_c},\\
 f(0,1,0)=(\_,\_,\_,\_)_{B_c},\\
 f(0,0,1)=(\_,\_,\_,\_)_{B_c}.\\
\end{array}
$$

Estos vectores de $\mathbb{R}^{4}$ escritos por columnas forman la matriz que nos piden.
Para calcular cada uno de ellos usaremos los datos del problema y que $f$ es una aplicación lineal. Por ejemplo,
como 

$$
f(0,0,1)=f((-1,-1,1)+(1,1,0)),
$$

entonces, usando que $f$ es lineal en el segundo elemento de la igualdad nos dará

$$
f(0,0,1)=f(-1,-1,1)+f(1,1,0),
$$

y como esos datos los proporciona el enunciado, tenemos

$$
f(0,0,1)=(0,0,0,0)+(2,1,1,2)=(2,1,1,2).
$$

Así obtendríamos una de las columnas de la matriz. Este procedimiento puede automatizarse escribiendo una matriz formada por dos bloques:

$$
\left( \begin{array}{rrr}
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

$$
\left( \begin{array}{rrr}
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

$$
\begin{array}{c}
 f(1,1,0)=(2,1,1,2),\\
 f(0,1,1)=(3,1,2,3),\\
 f(-1,-1,1)=(0,0,0,0).\\
\end{array}
$$

es decir, las imágenes de los vectores de la base $B$ escritos por sus coordenadas en $B_c$ de $\mathbb{R}^4$, y por tanto escritos por columnas nos dan la matriz $\mathcal{M}(f,B,B_c)$. 
Llamémosle 

$$C=\mathcal{M}(f,B,B_c)=
\left( 
  \begin{array}{rrr}
           2 & 3 & 0\\
           1 & 1 & 0\\
           1 & 2 & 0\\
           2 & 3 & 0 
  \end{array} 
\right).
$$

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

y por tanto la matriz $\mathcal{M}(f,B_c,B_c)=I C P^{-1}=CP^{-1}=A$.


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

<li>Calcula la matriz asociada respecto de las bases B y B'.

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

$$
P=\left( \begin{array}{rrr}
           1 & 0 & -1\\
           1 & 1 & -1\\
           0 & 1 & 1\\
                    \end{array} \right).
$$

El cambio de base de $B'$ a $B_c$ en $\mathbb{R}^4$ tiene matriz asociada 

$$
Q=\left( \begin{array}{rrrr}
           1 & 0 & 0 & 0\\
           0 & 1 & 0 & 0\\
           1 & -1 & 1 & 0\\
           1 & 0 & 1 & 1
                    \end{array} \right).
$$

Para realizar el recorrido desde $\mathbb{R}^3_{B}$ a 
$\mathbb{R}^4_{B'}$ tenemos que multiplicar un vector primero por $P$, luego por $A$ y por último por $Q^{-1}$. Es decir, puesto que el vector se escribe a la derecha por columnas tendremos la fórmula

$$
Y'=Q^{-1} A P X,
$$

y por tanto $\mathcal{M}(f,B,B')=Q^{-1} A P$. </li>
</ol>
::::
:::::


::::: {#exr-6 .avanzado}

Una aplicación lineal $f\colon \mathbb{R}^3 \to \mathbb{R}^4$ viene dada por:

$$
\begin{array}{c}
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

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Estudiar las dimensiones del núcleo y la imagen de $f$ según los valores del parámetro $a$.

Para estudiar las dimensiones del núcleo y la imagen tenemos que calcular el rango de una matriz asociada a $f$, y es indiferente respecto de qué bases esté considerada. Lo más inmediato es utilizar como base de $\mathbb{R}^3$ la base $B=\{(1,0,1),(1,1,1),(0,1,1)\}$ puesto que conocemos sus imágenes, y como base de $\mathbb{R}^4$ la base canónica, pues las imágenes que conocemos están dadas respecto de ella (al no hacerse mención en la expresión  a la base usada se trata de las componentes del vector). Así que usamos los datos del enunciado y tenemos

$$
C=\mathcal{M}(f,B,B_c)=
\left( \begin{array}{ccc}
           1+a & 1 & 1\\
           1 & 1+a & a\\
           1 & 1-a & a\\
           1-a & 1 & 1 
       \end{array} \right),
$$

de la que tenemos que estudiar el rango. Como el máximo posible es tres, entonces elegimos un menor de orden tres, por ejemplo:

$$
\left| \begin{array}{ccc}
           1 & 1+a & a\\
           1 & 1-a & a\\
           1-a & 1 & 1 
                    \end{array} \right|= \left| \begin{array}{ccc}
           1 & 1+a & a\\
           0 & -2a & 0\\
           1-a & 1 & 1 
                    \end{array} \right|= (-2a)(1-a+a^2).
$$

Como $a^2-a+1$ es siempre distinto de cero (la ecuación correspondiente no tiene raices reales), entonces este determinante sólo es cero cuando $a=0$. Por tanto, cuando $a\not = 0$, el rango de la matriz es tres. En el caso $a=0$  sustituyendo en la matriz es fácil observar que el rango es dos. 

Resumiendo lo que hemos obtenido:

Si $a\not = 0$ la dimensión de la imagen de $f$ es tres y el núcleo es trivial.

Si $a = 0$ la dimensión de la imagen de $f$ es dos y el núcleo tiene dimensión uno.
</li>

<li>Calcular la matriz asociada a $f$ respecto de las bases canónicas de $\mathbb{R}^3$ y $\mathbb{R}^4$.

De los datos del enunciado, procediendo como en el ejercicio anterior, podemos obtener las imágenes de los vectores de la base canónica de $\mathbb{R}^3$:

$$
\left( \begin{array}{ccc}
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

$$
A=\mathcal{M}(f,B_c,B_c)=
\left( \begin{array}{ccc}
           0 & -a & 1+a\\
           1 & a & 0\\
           1-2a & -a & 2a\\
           0 & a & 1-a
                    \end{array} \right).
$$
</li>

<li>¿Para qué valores de $a$ el vector $(1,a,1+a,1)$ está en la imagen de $f$?

Las columnas de una matriz asociada a $f$ nos da un sistema de generadores de $Im(f)$, para probar que un vector pertenece al subespacio generado por un conjunto de vectores tenemos que ver si es combinación lineal de ellos, o lo que es lo mismo, que al añadir ese vector el rango de la matriz no cambia. Podemos usar por ejemplo la matriz $C$ (o también $A$, puesto que ambas están referidas a la base canónica de $\mathbb{R}^4$):

$$
\left( \begin{array}{ccc|c}
           1+a & 1 & 1 & 1\\
           1 & 1+a & a & a\\
           1 & 1-a & a & 1+a\\
           1-a & 1 & 1 & 1 
                    \end{array} \right).
$$

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
                    \end{array} \right|=-2a.
$$

Cuando $a\not = 0$, el rango de $C$ era tres, y el rango al añadir el vector es cuatro, luego el vector no pertenece a la imagen.

En el caso $a=0$ el rango de $C$ es dos y al añadir el vector $(1,0,1,1)$ el rango aumenta a tres, así que no pertenece a la imagen.
</li>

<li>¿Para qué valores de $a$ el vector $(1,-1,0)$ está en el núcleo de $f$?

En el caso $a\not =0$ el núcleo se reduce al vector $(0,0,0)$,
así que el vector dado no pertenece al núcleo. 

En el caso $a=0$ podemos calcular la imagen del vector $(1,-1,0)$, para lo que tenemos que usar la matriz asociada a $f$ respecto de la base canónica de $\mathbb{R}^3$, es decir $A$:

$$
f(1,-1,0)=A\left( \begin{array}{r}
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
::::
:::::

::::: {#exr-7 .avanzado}

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

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar la matriz asociada a $F$ respecto de las respectivas bases estándar y	el valor de $F(p(x))$.

Para determinar la matriz asociada solo tenemos que escribir las imágenes de $1,x,x^2,x^3$ en función de la base estándar de $\mathcal{M}_2(\mathbb{R})$ y colocarlos por columnas.
Usando los datos dados:

$$
F(1)=\frac{1}{2}(F(1+x)+F(1-x))=\begin{pmatrix} 1 & 1 \\ 1 & 1 \end{pmatrix}=(1,1,1,1)_{B_{sm}},
$$

$$
F(x)=\frac{1}{2}(F(1+x)-F(1-x))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}},
$$

$$
F(x^2)=\frac{1}{2}(F(x^2+x^3)+F(x^2-x^3))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}},
$$

$$
F(x^3)=\frac{1}{2}(F(x^2+x^3)-F(x^2-x^3))=\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}=(1,0,0,1)_{B_{sm}}.
$$

Así,
$$M(F,B_{sp},B_{sm})=\left(\begin{array}{llll}
1 & 1 & 1 & 1\\
1 & 0 & 0 & 0\\
1 & 0 & 0 & 0\\
1 & 1 & 1 & 1
\end{array}\right)=A.
$$ 

Dado un polinomio $p(x)=a_0+a_1x+a_2x^2+a_3x^3=(a_0,a_1,a_2,a_3)_{B_{sp}}$ calculamos

$$
F(p(x))=A\left( \begin{array}{l}
a_0\\
a_1\\
a_2\\
a_3
\end{array}\right)=\left( \begin{array}{c}
a_0+a_1+a_2+a_3\\
a_0\\
a_0\\
a_0+a_1+a_2+a_3
\end{array}\right)_{B_{sm}}.
$$

Así que

$$
F(p(x))=\left( \begin{array}{cc}
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
$$
</li>

<li>Determinar la matriz asociada a $F$ respecto de las bases $\overline{B}$ y $\overline{B'}$.

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

$$
M(F,\overline{B},\overline{B'})=
\left(\begin{array}{rrrr}
2  & 0 & 2 & 0\\
-1 & 1 & -2 & 0\\
0 & 0 & 0 & 0\\
0 & 0 & 0 & 0\\
\end{array}\right)=C.
$$

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

$$
Q^{-1}=\left(\begin{array}{rrrr}
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
$$
</li>

<li>Determinar bases del núcleo y la imagen de $F$.

Como $\operatorname{rg}(A)=\operatorname{rg}(C)=2$, entonces $\dim(\operatorname{Im}(F))=2$ y $\dim(\operatorname{ker}(F))=2$. Una base de la  imagen (obtenida por operaciones elementales en las columnas de $A$) puede ser: 

$$
\left\{\begin{pmatrix}
1 & 0 \\ 
0 & 1 
\end{pmatrix}, 
\begin{pmatrix} 0 & 1 \\ 
1 & 0 
\end{pmatrix}\right\}=\left\{(1,0,0,1)_{B_{sm}},(0,1,1,0)_{B_{sm}}\right\}.
$$

También observando $A$ obtenemos que $F(x-x^2)=F(x-x^3)=0$ y por tanto una base del núcleo puede ser: 

$$
\{ x-x^2, x-x^3\}=\{(0,1,-1,0)_{B_{sp}},(0,1,0,-1)_{B_{sp}} \}.
$$

</li>
</ol>

::::
:::::

:::::{#exr-8 .medio}

Dado el endomorfismo de $\mathbb{R}^3$ que viene dado por

$$
\begin{align*}
f(1,1,-1)&=(1,1,1),\\
f(1,-1,1)&=(1,1,0),\\
f(-1,1,1)&=(1,0,0).
\end{align*}
$$

Calcula la matriz asociada a $f$ respecto de la base
$B'=\{(1,1,-1),(1,-1,1),(-1,1,1)\}$

:::: {.callout collapse="true" title="Solución"}

Calcular la matriz asociada a $f$ respecto de la base $B'$
Observamos que nos dan las imágenes de los vectores de la base $B'$, pero estas vienen dadas por sus coordenadas en la base canónica y debemos calcular las coordenadas también en la base $B'$. Por tanto necesitamos la matriz de cambio de base de $B_c$ a $B'$, que es la inversa de la matriz

$$
P=\left(\begin{array}{rrr}
  1 & 1 & -1 \\
  1 & -1 & 1 \\
  -1 & 1  & 1 \\
\end{array}
\right).
$$

La calculamos:

$$
\begin{align*}
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
\right),\end{align*}
$$

y ahora calculamos las coordenadas de $(1,1,1),(1,1,0),(1,0,0)$ respecto de $B'$:

$$
\left(\begin{array}{ccc}
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
\end{array}\right).
$$

Como

$$
\begin{array}{ll}
f(1,1,-1)&=(1,1,1)_{B'},\\
f(1,-1,1)&=(1,1/2,1/2)_{B'},\\
f(-1,1,1)&=(1/2,1/2,0)_{B'},
\end{array}
$$

la matriz asociada a $f$ respecto de $B'$ es

$$
C=\left(\begin{array}{ccc}
1 & 1 & 1/2 \\
1 & 1/2 & 1/2\\
1 & 1/2 & 0\\
\end{array}\right).
$$

::::
:::::

::::: {#exr-9 .medio}

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

$$ 
B= \{ (1,0,-1), (1,1,-1),(0,1,-1)\}.
$$
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular las dimensiones del núcleo y la imagen para todos los valores reales de $a$.

Puesto que  $\dim(\operatorname{Im}(f))=\operatorname{rg}(A)$, calculamos el rango de $A$.

$$
\left(
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

$$
\left|
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
  \right| = (1+a)(2-a)-(-a)(a-1)=2+2a-a-a^2-(a-a^2)=2.
$$

Por lo tanto $\dim(\operatorname{Im}(f))=3$ para todos los valores de $a$ y como 

$$
\dim(\operatorname{ker}(f))+\dim(\operatorname{Im}(f))=\dim(\mathbb{R}^3),
$$  

entonces $\dim(\operatorname{ker}(f))=0$  para todos los valores de $a$.
</li>

<li>¿Para qué valores de $a$ es una aplicación lineal biyectiva?

Como $\operatorname{ker}(f)=\{0\}$, la aplicación siempre es inyectiva, y como la $\dim(\operatorname{Im}(f))=\dim(\mathbb{R}^3)$, siempre es sobreyectiva, así que es biyectiva para todos los valores de $a$.
</li>

<li>Calcular la matriz asociada a este endomorfismo respecto de la base $B$.

Como conocemos los vectores de $B$ por sus coordenadas en $B_c$, la matriz $P$ viene dada por esas coordenadas.
 
$$
P=\left(
  \begin{array}{ccc}
   1 & 1 & 0 \\
    0 & 1 & 1 \\
   -1 & -1 & -1 \\
\end{array}
\right),
$$
 
luego 

$$
??=P^{-1}\cdot A\cdot P.
$$

Calculamos $P^{-1}$:

$$
\left(
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

$$
\left(
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
\right),
$$

$$
\mathcal{M}(f,B)=P^{-1}\cdot A\cdot P =\left(
\begin{array}{ccc}
  1 & 0 & 0 \\
  -a & 1 & 0 \\
  a & 0 & 2\\
\end{array}
\right).
$$

</li>
</ol>
::::
:::::


::::: {#exr-10 .avanzado}

Se considera el endomorfismo $f: \mathcal{M}_2(\mathbb{R}) \longrightarrow\mathcal{M}_2(\mathbb{R})$
dado por:

$$
f\begin{pmatrix} a & b \\ c & d \end{pmatrix} = \begin{pmatrix} a+b & a-b\\ c-d & c-d \end{pmatrix}.
$$

<ol type="a">
<li>Determinar la matriz asociada a $f$ respecto de la base estándar $B_s$ de $\mathcal{M}_2(\mathbb{R})$.</li>

<li>Determinar la matriz asociada a $f$ respecto de la base de $\mathcal{M}_2(\mathbb{R})$:

$$
B' = \left\{\begin{pmatrix} 1 & 0 \\ 1 & 0 \end{pmatrix}, \begin{pmatrix} 1 & 0 \\ -1 & 0 \end{pmatrix},
\begin{pmatrix}0 & 1 \\ 0 & 1 \end{pmatrix}, \begin{pmatrix}0 & 1 \\ 0 & -1 \end{pmatrix}\right\}.
$$
</li>

<li>Determinar bases de  $Ker(f)$, $Im(f)$, $Ker(f)\cap Im(f)$ y $Ker(f)+ Im(f)$.</li>

<li>Determinar una base $B$ de $\mathcal{M}_2(\mathbb{R})$ de forma que la matriz asociada a $f$ respecto de las bases $B_s$ y $B$ sea

$$
H=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & -1\\
0 & 0 & 0 & 0
\end{pmatrix}.
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar la matriz asociada a $f$ respecto de la base $B_s$.


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

<li>Determinar la matriz asociada a $f$ respecto de la base B'.

Puede construirse el diagrama correspondiente y tendremos que 
$$
\mathcal{M}(f,B')= P^{-1}AP,
$$ 

siendo $P$ la matriz de cambio de base de $B'$ a $B_s$:

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

<li>Determinar bases de  $\operatorname{ker}(f)$, $\operatorname{Im}(f)$, $\operatorname{ker}(f)\cap \operatorname{Im}(f)$ y $\operatorname{ker}(f)+ \operatorname{Im}(f)$.

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

<li>Determinar una base $B$ de $\mathcal{M}_2(\mathbb{R})$ de forma que la matriz asociada a $f$ respecto de las bases $B_s$ y $B$ sea $H$.

Como nos piden que la base solo cambie en el segundo espacio, basta observar que se trata de que las coordenadas de las matrices calculadas en el primer apartado sean:

$$
\begin{pmatrix} 1 & 1\\ 0 & 0 \end{pmatrix}=(1,0,0,0)_{B} 
\hspace{0.5cm} 
\begin{pmatrix} 1 & -1\\ 0 & 0 \end{pmatrix}=(0,1,0,0)_{B}
\hspace{0.5cm} 
\begin{pmatrix} 0 & 0\\ 1 & 1 \end{pmatrix}=(0,0,1,0)_{B} 
$$

Así que están determinados los tres vectores de la base $B$. Para completar la base puede elegirse cualquier matriz linealmente independiente con las tres anteriores, por ejemplo podemos tomar:

$$ \left\{ \begin{pmatrix} 1 & 1\\ 0 & 0 \end{pmatrix},\, 
\begin{pmatrix} 1 & -1\\ 0 & 0 \end{pmatrix},\,
\begin{pmatrix} 0 & 0\\ 1 & 1 \end{pmatrix},\, 
\begin{pmatrix} 0 & 0\\ 0 & 1 \end{pmatrix} \right\}.
$$

</li>
</ol>
::::
:::::

::::: {#exr-11 .avanzado}

Se considera la aplicación lineal $D:\mathcal{P}_4(\mathbb{R}) \to \mathcal{P}_3(\mathbb{R})$ dada por $D(p(x))=p'(x)$.

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
$$

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular el núcleo de $D$.

El núcleo de una aplicación lineal son los vectores cuya imagen vale cero, en este caso los polinomios cuya imagen por $D$, es decir, su derivada, vale cero. Es claro que tales polinomios son los polinomios constantes, por tanto el núcleo está formado por los polinomios constantes.
</li>

<li>Determinar la matriz asociada respecto de las bases $B_{s,4}$ y $B_{s,3}$.

Para calcular dicha matriz calculamos las imágenes de los vectores de la base $B_{s,4}$ y los escribimos usando coordenadas respecto de $B_{s,3}$:

$$
\begin{array}{l}
D(1)=0=(0,0,0,0)_{B_{s,3}},\\ 
D(x)=1=(1,0,0,0)_{B_{s,3}},\\ 
D(x^2)=2x=(0,2,0,0)_{B_{s,3}},\\
D(x^3)=3x^2=(0,0,3,0)_{B_{s,3}},\\
D(x^4)=4x^3=(0,0,0,4)_{B_{s,3}}.\\ 
\end{array}.
$$

Así la matriz pedida es

$$
A=\begin{pmatrix}
0 & 1 & 0 & 0 & 0\\
0 & 0 & 2 & 0 & 0\\
0 & 0 & 0 & 3 & 0\\
  0 & 0 & 0 & 0 & 4\\ 
\end{pmatrix}.
$$

</li>

<li>Determinar bases $B$ y $B'$ de forma que la matriz asociada a $D$ respecto de estas bases sea $M_{BB'}(D)$.

Es bastante fácil comprobar que la forma de Hermite por columnas de la matriz $A$ anterior es exactamente la que se da en este apartado. Por tanto existe una matriz regular $P$ tal que $AP= M_{BB'}(D)$. En un diagrama de cambio de base obtendríamos que solo es necesario realizar un cambio de base en el primer espacio para que la matriz asociada a $D$ sea la dada.
Además esa nueva base $B$ viene dada por las columnas de $P$, mientras que en el segundo espacio no es necesario cambiar de base. 

Calculamos una matriz $P$ (la solución no es única) que verifique $AP=M_{BB'}(D)$:

$$
A=\begin{pmatrix}
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
    \end{pmatrix}.
$$

Así tenemos que $B'=B_{s,3}$ y $B=\{x, x^2/2, x^3/3, x^4/4, 1\}$. 
</li>
</ol>

::::
:::::

::::: {#exr-12 .medio}
Se considera la aplicación lineal

$$
f: \mathcal{M}_2(\mathbb{R}) \to \mathcal{M}_2(\mathbb{R}) 
$$

definida por:

$$
f\left( \begin{pmatrix} a & b \\ c & d\end{pmatrix}\right) = 
\begin{pmatrix} a+d & b+c \\ b-c & a+d\end{pmatrix}
$$

Determinar la matriz asociada a $f$ respecto a la base estándard de $\mathcal{M}_2(\mathbb{R})$ y determinar bases de $\operatorname{ker}(f)$ e $\operatorname{Im}(f)$. ¿Es $f$ inyectiva? ¿Es $f$ sobreyectiva?

:::: {.callout collapse="true" title="Solución"}

La base estándar que vamos a usar en  $\mathcal{M}_2(\mathbb{R})$ es

$$ 
B_s= \left\{  \left( \begin{array}{rr}
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
\end{array} \right) \right\}.
$$  

Calculamos la imagen por $f$ de cada uno de estos vectores y la escribimos en función de $B_s$. 

$$
f(\left( \begin{array}{rr}
1 & 0 \\
0 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
1 & 0 \\
0 & 1 \\
\end{array} \right)=(1,0,0,1)_{B_{s}}, 
$$

$$
f(\left( \begin{array}{rr}
0 & 1 \\
0 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
0 & 1 \\
1 & 0 \\
\end{array} \right)=(0,1,1,0)_{B_{s}}, 
$$

$$
f(\left( \begin{array}{rr}
0 & 0 \\
1 & 0 \\
\end{array} \right) )= \left( \begin{array}{rr}
0 & 1 \\
-1 & 0 \\
\end{array} \right)=(0,1,-1,0)_{B_{s}}, 
$$

$$
f(\left( \begin{array}{rr}
0 & 0 \\
0 & 1 \\
\end{array} \right) )= \left( \begin{array}{rr}
1 & 0 \\
0 & 1 \\
\end{array} \right)=(1,0,0,1)_{B_{s}}. 
$$

La matriz asociada resulta de poner estos cuatro vectores por columnas:

$$ 
A= \left( \begin{array}{rrrr}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 0 \\
0 & 1 & -1 & 0\\
1 & 0 & 0 & 1  
\end{array} \right). 
$$

Para calcular simultáneamente una base del núcleo y una de la imagen añadimos la identidad bajo $A$ y hacemos operaciones elementales por columnas:

$$ 
\left( \begin{array}{rrrr}
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
::::
:::::

::::: {#exr-13 .medio}

Se considera el endomorfismo $f:\mathbb{R}^{4} \to \mathbb{R}^{4}$ dado por 

$$
\begin{array}{rl}
f(1,-1,0,0)&=(1,-1,0,0),\\
f(1,0,0,-1)&=(1,0,0,-1),\\
f(0,0,1,0)&=(0,0,1,0),\\
f(1,1,0,1)&=(0,0,0,0).\\
\end{array}
$$

<ol type="a">
<li>Calcula la matriz asociada a $f$ respecto de la base $\overline{B}=\{(1,-1,0,0),(1,0,0,-1),(0,0,1,0),(1,1,0,1)\}$.</li>

<li>Calcula la matriz asociada al endomorfismo respecto de la base canónica.</li>

<li>Calcula bases del núcleo y la imagen de $f$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular la matriz asociada a $f$ respecto de la base $\overline{B}$.

Tenemos calculadas las imágenes de los vectores de $\overline{B}$, así que sólo tenemos que calcular sus coordenadas respecto de $\overline{B}$, que son inmediatas

$$
\begin{array}{rll}
f(1,-1,0,0)&=(1,-1,0,0)&=(1,0,0,0)_{\overline{B}},\\
f(1,0,0,-1)&=(1,0,0,-1)&=(0,1,0,0)_{\overline{B}},\\
f(0,0,1,0)&=(0,0,1,0)&=(0,0,1,0)_{\overline{B}},\\
f(1,1,0,1)&=(0,0,0,0)&=(0,0,0,0)_{\overline{B}}.\\
\end{array}
$$

Así que 

$$
\mathcal{M}(f,\overline{B})=\begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 &  0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 0 
\end{pmatrix}.
$$

</li>

<li>Calcular la matriz asociada al endomorfismo respecto de la base canónica.

$f$ es la proyección ortogonal sobre $U^{\perp}$, por lo que 

$$
\mathcal{M}(f,B_c)=\begin{pmatrix}
2/3 & -1/3 & 0 & -1/3\\
-1/3 & 2/3 &  0 & -1/3\\
0 & 0 & 1 & 0\\
-1/3 & -1/3 & 0 & 2/3 
\end{pmatrix}.
$$

</li>

<li>Calcular bases del núcleo y la imagen de $f$.

Como $\operatorname{dim}(\operatorname{Im}(f))=\operatorname{rg}(\mathcal{M}(f,\overline{B}))=3$ entonces una base de la imagen son los tres primeros vectores de la base $\overline{B}$, es decir, $\operatorname{Im}(f)=U^{\perp}$.
Así $\operatorname{dim}(\operatorname{ker}(f))=1$ y como $f(1,1,0,1)=(0,0,0,0)$, entonces una base de $\operatorname{ker}(f)$ es $\{(1,1,0,1)\}$, con lo que $\operatorname{ker}(f)=U$. 
</li>
</ol>

::::
:::::

::::: {#exr-14 .cuerpo-finito-medio}

De una aplicación lineal $f:(\mathbb{Z}_5)^2 \longrightarrow (\mathbb{Z}_5)^3$ se sabe que $f(1,2)=(1,0,1)$ y $f(2,1)=(0,1,0)$ Determinar razonadamente el valor de $f(x,y)$.

:::: {.callout collapse="true" title="Solución"}

Buscamos la matriz de la aplicación lineal respecto de las bases canónicas de cada uno de los espacios vectoriales. 

Se consideran las bases: \\ $B_c=\{ (1,0), (0,1)\}$ y $\overline{B}=\{(1,2), (2,1)\}$ de $(\mathbb{Z}_5)^2$ \\  $B_c^{3}=\{(1,0,0),(0,1,0), (0,0,1)\}$ de $(\mathbb{Z}_5)^3$.

Si denotamos:

$P$ a la matriz de cambio de base de $\overline{B}$ a $B_c$,  

$A=\mathcal{M}_{B,B_c^{3}}(f)$, 

$C=\mathcal{M}_{\overline{B},B_c^{3}}(f)$

Se tiene que:

$$
P=\begin{pmatrix}
1 & 2 \\ 2 & 1
\end{pmatrix}
; \;
C=\begin{pmatrix}
1 & 0\\ 0 & 1 \\ 1 & 0
\end{pmatrix}
$$

y que 
$C= A \cdot P$, con lo cual 
$A= C \cdot P^{-1}$

Se calcula la inversa de $P$:

$$
\left(\begin{array}{cc|cc}
1 & 2 & 1 & 0 \\
2 & 1 & 0 & 1 \\
\end{array}
\right)
\sim_f
\left(\begin{array}{cc|cc}
1 & 2 & 1 & 0 \\
0 & 2 & 3 & 1 \\
\end{array}
\right)
\sim_f
\left(\begin{array}{cc|cc}
1 & 2 & 1 & 0 \\
0 & 1 & 4 & 3 \\
\end{array}
\right)
\sim_f
\left(\begin{array}{cc|cc}
1 & 2 & 3 & 4 \\
0 & 1 & 4 & 3 \\
\end{array}
\right)
$$

$$
P^{-1}=\begin{pmatrix}
3 & 4 \\ 4 & 3
\end{pmatrix}
$$

$$
A= C \cdot P^{-1}=
\begin{pmatrix}
1 & 0\\ 0 & 1 \\ 1 & 0
\end{pmatrix} 
\cdot 
\begin{pmatrix}
3 & 4 \\ 4 & 3
\end{pmatrix}=
\begin{pmatrix}
3 & 4\\ 4 & 3 \\ 3 & 4
\end{pmatrix}
$$

Ahora, puesto que $A$ es la matriz respecto de la bases canónicas, la imagen de un vector $(x,y)$ se obtiene multiplicando por $A$:

$$
\begin{pmatrix}
3 & 4\\ 4 & 3 \\ 3 & 4
\end{pmatrix}
\cdot
\begin{pmatrix}
x \\ y
\end{pmatrix}
=
\begin{pmatrix}
3x+4y \\ 4x+3y \\ 3x+4y
\end{pmatrix}
$$

$$
f(x,y)=(3x+4y, 4x+3y, 3x+4y)
$$

::::
:::::

::::: {#exr-15 .basico}

Calcula una base del núcleo del endomorfismo de $\mathbb{R}^{3}$ con matriz asociada, respecto de la base canónica,

$$
A=\left(\begin{array}{rrr}
1  & 1 & 1\\
-1 & 1 & 3\\
1 & 1 & 1
\end{array}\right)
$$

:::: {.callout collapse="true" title="Solución"}

$$
A\sim_f \left(\begin{array}{rrr}
1  & 1 & 1\\
0 & 2 & 4\\
0 & 0 & 0
\end{array}\right)\sim_f \left(\begin{array}{rrr}
1  & 0 & -1\\
0 & 1 & 2\\
0 & 0 & 0
\end{array}\right)
$$

Esto nos permite tener unas cartesianas del núcleo ($AX=0$) más sencillas:

$$
N(f)\equiv \left\{ \begin{array}{l}
x-z=0\\
y+2z=0\\
\end{array}\right.
$$ 

y una base es $\{(1,-2,1)\}$.

::::
:::::

::::: {#exr-16 .basico}

Dada la aplicación lineal $f:\mathbb{R}^3\longrightarrow \mathbb{R}^4$ definida por $$f(x,y,z)=(x+y,x+y+z, y+z, x+z)$$ determina si es inyectiva, sobreyectiva, biyectiva o ninguna de ellas.

:::: {.callout collapse="true" title="Solución"}

La matriz asociada en la base canónica es

$$
\begin{pmatrix}
1 & 1 & 0 \\
1 & 1 & 1\\
0 & 1 & 1\\
1 & 0 & 1
\end{pmatrix}
$$

Calculamos el rango

$$
\begin{pmatrix}
1 & 1 & 0 \\
1 & 1 & 1\\
0 & 1 & 1\\
1 & 0 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
\boxed{1} & 0 & 0 \\
1 & 0 & 1\\
0 & 1 & 1\\
1 & -1 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
\boxed{1} & 0 & 0 \\
0 & \boxed{1} & 0\\
-1 & 1 & \boxed{1}\\
0 & 1 & -1
\end{pmatrix}
$$

es y por tanto $dim\, Im(f)=3\not = dim\, \mathbb{R}^{4}$ y no es sobreyectiva. Por la fórmula de las dimensiones

$$
dim\, N(f)+ dim\, Im(f)=dim\, \mathbb{R}^{3}
$$

y por tanto $N(f)=\{0\}$ por lo que sí es inyectiva. 

::::
:::::

::::: {#exr-17 .basico}

Dada la aplicación lineal $f:\mathbb{R}^{4}\longrightarrow \mathbb{R}^{3}$ definida por 

$$
f(x,y,z,t)=(x+y+z+t,y+z+t,z+t)
$$ 

determina si es inyectiva, sobreyectiva, biyectiva o ninguna de ellas. 

:::: {.callout collapse="true" title="Solución"}

La matriz asociada a $f$ respecto de las bases canónicas es

$$
\left(\begin{array}{cccc}
1 & 1 & 1 & 1\\
0 & 1 & 1 & 1\\
0 & 0 & 1 & 1
\end{array}\right)
$$

y como su rango es $3$ entonces $dim\, Im(f)=3=dim\, \mathbb{R}^3$ y por tanto {\bf es sobreyectiva}. Como $dim\, N(f)+ dim\, Im(f)=dim \, \mathbb{R}^4$ entonces $dim\, N(f)=1$ así que <b>f no es inyectiva</b>. Por tanto <b>f no es biyectiva</b>. 

::::
:::::

::::: {#exr-18 .medio}

De una aplicación lineal $f:\mathbb{R}^{3}\longrightarrow \mathbb{R}^{4}$ se sabe que 
$f(5,1,1)=f(1,5,1)=f(1,1,5)=(5,5,5,5)$. Determinar bases del núcleo y la imagen de $f$.

:::: {.callout collapse="true" title="Solución"}

La imagen de $f$ está generada por $\{(5,5,5,5)\}$ así que este vector es una base de $Im(f)$ ( o también $\{(1,1,1,1)\}$). Así que $Im(f)$ tiene dimensión 1. Por la fórmula de las dimensiones ($dim\, N(f)+ dim\, Im(f)= dim\, V$) la dimensión del núcleo es 2. 

Como $f(5,1,1)-f(1,5,1)=f(4,-4,0)=(0,0,0,0)$ y $f(5,1,1)-f(1,1,5)=f(4,0,-4)=(0,0,0,0)$ entonces $\{(4,-4,0),(4,0,-4)\}$ es una base del núcleo.

::::
:::::

::::: {#exr-19 .basico}

De un endomorfismo $f:\mathbb{R}^3 \longrightarrow \mathbb{R}^3$ se sabe que 
$f(1,2,3)=(1,2,3)$, $f(0,1,2)=(1,2,3)$ y $dim(Im(f))=2$. Determinar una base de $Ker(f)$.

:::: {.callout collapse="true" title="Solución"}

Usando la fórmula de las dimensiones para aplicaciones lineales se tiene que la dimensión de $Ker(f)=1$ (puesto que $dim \, Ker(f) + dim\, Im(f)= 3$) y basta con encontrar un vector no nulo cuya imagen valga $(0,0,0)$. Pero es evidente de los datos que 

$$
f(1,1,1)=f(1,2,3)-f(0,1,2)=(0,0,0)
$$

así que $(1,1,1)\in Ker(f)$ y así tenemos una base $\{(1,1,1)\}$ 

::::
:::::

::::: {#exr-20 .basico}

Razonar que la aplicación $G: \mathcal{M}_2(\mathbb{R})  \longrightarrow \mathcal{M}_2(\mathbb{R})$
definida por: 

$$
G\biggl(\begin{pmatrix} a & b \\ c & d \end{pmatrix}\biggr)=\begin{pmatrix} a\cdot b & 0 \\ c & d \end{pmatrix}
$$

no es lineal.

:::: {.callout collapse="true" title="Solución"}

Calculamos

$$
G\biggl(\begin{pmatrix} 
1 & 0 \\ 
0 & 0 
\end{pmatrix}\biggr)=\begin{pmatrix} 
0 & 0 \\ 
0 & 0 
\end{pmatrix}; G\biggl(\begin{pmatrix} 
0 & 1 \\ 
0 & 0 
\end{pmatrix}\biggr)=\begin{pmatrix} 
0 & 0 \\ 
0 & 0 
\end{pmatrix}
$$

Sin embargo la imagen de la suma de estas matrices es

$$
G\biggl(\begin{pmatrix} 
1 & 1 \\ 
0 & 0 
\end{pmatrix}\biggr)=\begin{pmatrix} 
1 & 0 \\ 
0 & 0 
\end{pmatrix}\not = G\biggl(\begin{pmatrix} 
1 & 0 \\ 
0 & 0 
\end{pmatrix}\biggr)+G\biggl(\begin{pmatrix} 
0 & 1 \\ 
0 & 0 
\end{pmatrix}\biggr)
$$

::::
:::::

::::: {#exr-21 .basico}

En $\mathbb{R}^{4}$ se considera el endomorfismo dado por

$$
f(x,y,z,t)=(3x-y,-x+3y,3z+t,z+3t)
$$

<ol type="a">
<li>Calcula las dimensiones del núcleo y la imagen de $f$ dando bases de ambos. </li>
<li>Calcula la matriz asociada a $f$ respecto de la base canónica. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>
Es fácil calcular las ecuaciones cartesianas del núcleo, imponiendo la condición $f(x,y,z,t)=(0,0,0,0)$.

$$
N(f)\equiv \left\{\begin{array}{rlc}
3x-y& &=0\\
-x+3y& & =0\\
&3z+t&=0\\
&z+3t&=0
\end{array}\right. \sim_f  \left\{\begin{array}{ccccr}
x & & & &=0\\
&y& & & =0\\
& & &z&=0\\
& & & &t=0
\end{array}\right.
$$

Luego $N(f)=\{0\}$ y no tiene base. Por la fórmula de las dimensiones

$$
dim\, N(f) + dim\, Im(f)= dim\, \mathbb{R}^{4}
$$

obtenemos que $dim\, Im(f)=4$ y por tanto $Im(f)=\mathbb{R}^{4}$ y una base es la canónica, por ejemplo.
</li>
<li>
Calculamos

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

</li>
</ol>

::::
:::::

::::: {#exr-22 .medio}

En $\mathbb{R}^{3}$ se considera el endomorfismo dado por 

$$
\begin{array}{rcl}
f(1,0,1) & = & (0, 1, 1) \\
f(1,1,1) & = & (1,0, 2)\\
f(0,1,1) & = & (0,-1,-1)
\end{array}
$$

<ol type="a">
<li>Calcula las dimensiones del núcleo y la imagen de $f$ dando bases de ambos. </li>
<li>Calcula la matriz asociada a $f$ respecto de la base canónica. </li>
<li>Calcula la matriz de este endomorfismo respecto de la base 

$$
B=\{(1,0,1),(1,1,1),(0,1,1)\}
$$ 

</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>
Utilizamos operaciones elementales por columnas para la siguiente matriz que forman los datos:

$$
\begin{pmatrix}
f(v)\\
\uparrow\\
v
\end{pmatrix}=\left(\begin{array}{rrr}
0 & 1 & 0 \\
1 & 0 & -1\\
1 & 2 & -1\\
\hline
1 & 1 & 0\\
0 & 1 & 1\\
1 & 1 & 1
\end{array}\right)\sim_c \left(\begin{array}{rrr}
0 & 1 & 0 \\
1 & 0 & 0\\
1 & 2 & 0\\
\hline
1 & 1 & 1\\
0 & 1 & 1\\
1 & 1 & 2
\end{array}\right)\sim_c \left(\begin{array}{rr|r}
1 & 0 & 0 \\
0 & 1 & 0\\
2 & 1 & 0\\
\hline
1 & 1 & 1\\
1 & 0 & 1\\
1 & 1 & 2
\end{array}\right)
$$

Luego $dim\, Im(f)=2$ y la base más sencilla es 

$$
\{ (1,0,2),(0,1,1)\}
$$

y $dim\, N(f)=1$ y una base es

$$
\{(1,1,2)\}
$$

</li>
<li>
Como tenemos que calcular las imágenes de los vectores de la base canónica a partir de los datos procedemos de forma similar, pero ahora escribiendo arriba los vectores y abajo sus imágenes:

$$
\begin{pmatrix}
v\\
\downarrow \\
f(v)
\end{pmatrix}=\left(\begin{array}{rrr}
1 & 1 & 0\\
0 & 1 & 1\\
1 & 1 & 1\\
\hline
0 & 1 & 0 \\
1 & 0 & -1\\
1 & 2 & -1\\
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 1\\
1 & 0 & 1\\
\hline
0 & 1 & 0 \\
1 & -1 & -1\\
1 & 1 & -1\\
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0\\
1 & 0 & 1\\
\hline
0 & 1 & -1 \\
1 & -1 & 0\\
1 & 1 & -2\\
\end{array}\right)\sim_c \left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1\\
\hline
1 & 1 & -1 \\
1 & -1 & 0\\
3 & 1 & -2\\
\end{array}\right)
$$

Luego 

$$
M(f,B_c)=\left(\begin{array}{rrr}
1 & 1 & -1 \\
1 & -1 & 0\\
3 & 1 & -2\\
\end{array}\right)
$$

</li>
<li>
(Aplicando la definición de matriz asociada) Como conocemos las imágenes de los vectores de $B$, aunque por sus coordenadas respecto de la base canónica, solo nos falta calcular sus coordenadas respecto de $B$. Pero es inmediato que  $(0,1,1)=(0,0,1)_B$ y $(0,-1,-1)=(0,0,-1)_B$ solo nos falta calcular las coordenadas de $(1,0,2)$ respecto de $B$:

$$
(1,0,2)=\alpha (1,0,1)+\beta (1,1,1)+\gamma (0,1,1)
$$

que nos da el sistema

$$
\left. \begin{array}{l}
\alpha + \beta=1\\ 
\beta+\gamma=0\\
\alpha+\beta+\gamma=2
\end{array}\right\} \sim_f \left. \begin{array}{l}
\alpha =2\\ 
\beta=-1\\
\gamma=1
\end{array}\right\}
$$

luego $f(1,1,1)=(1,0,2)=(2,-1,1)_B$. Ahora tenemos todos los datos necesarios:

$$
\begin{array}{rcl}
f(1,0,1) & = & (0, 0, 1)_B \\
f(1,1,1) & = & (2,-1, 1)_B\\
f(0,1,1) & = & (0,0,-1)_B
\end{array}
$$ 

y por tanto

$$
M(f,B)=\left(\begin{array}{rrr}
0 & 2 & 0 \\
0& -1 & 0\\
1 & 1 & -1\\
\end{array}\right)
$$

</li>
</ol>

::::
:::::

::::: {#exr-23 .avanzado}

Dada la aplicación lineal $f: \mathbb{R}^{3} \longrightarrow \mathbb{R}^4$ que, respecto de las bases canónicas respectivas, tiene matriz asociada

$$
A= \left(\begin{array}{ccc}
1 & 0 & -1\\
1 & a & a-1 \\
1 & 0 & a-2\\
0 & a & a-1 
\end{array}\right)
$$

se pide:

<ol type="a">
<li>Calcula las dimensiones del núcleo y la imagen de $f$ según los valores de $a$. </li>
<li>Para $a=0$ calcula bases del núcleo y la imagen. </li>
<li>Para $a=1$ calcula la matriz asociada a $f$ respecto de la bases  
$B=\{(0,0,-1),(1,0,1),(-1,1,-1)\}$ de $\mathbb{R}^{3}$ y $B_c$ de $\mathbb{R}^4$. </li>
<li>Para $a=1$ calcula bases de $\mathbb{R}^3$ y $\mathbb{R}^4$ de forma que la matriz asociada a $f$ sea 

$$
E= \left(\begin{array}{ccc}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1\\
0 & 0 & 0 
\end{array}\right)
$$ 
</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>
Es necesario calcular el rango de la matriz $A$ que es la dimensión de la imagen de $f$:

$$
A= \left(\begin{array}{ccc}
\boxed{1}  & 0 & -1\\
1 & a & a-1 \\
1 & 0 & a-2\\
0 & a & a-1 
\end{array}\right)\sim_f \left(\begin{array}{ccc}
\boxed{1} & 0 & -1\\
0 & a & a \\
0 & 0 & a-1\\
0 & a & a-1 
\end{array}\right)\sim_f \left(\begin{array}{ccc}
\boxed{1} & 0 & -1\\
0 & a & a \\
0 & 0 & a-1\\
0 & 0 & -1 
\end{array}\right)\sim_f \left(\begin{array}{ccc}
\boxed{1} & 0 & 0\\
0 & a & 0 \\
0 & 0 & \boxed{1}\\
0 & 0 & 0
\end{array}\right)
$$

En la segunda fila hay pivote siempre que $a\not = 0$, así que el rango es $3$ cuando $a\not =0$ y $2$ cuando $a=0$. 
Usando la fórmula $dim\, N(f)+dim\, Im(f)=dim \, V$, tenemos

<CENTER>
<TABLE BORDER>       
<TR>
<TD><TH>$dim\, N(f)$</TH><TH>$dim\, Im(f)$</TH></TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a = 0$</TH><TD>1</TD><TD>2</TD>
</TR>

<TR ALIGN=CENTER>    
<TH>$a\not = 0$</TH><TD>0</TD><TD>3</TD>
</TR>
</TABLE>
</CENTER>
</li>
<li>
Podemos usar el método que nos da, al mismo tiempo, ambas bases:

$$
\left(\begin{array}{c}
A\\
\hline
I
\end{array}\right)= \left(\begin{array}{rrr}
\boxed{1} & 0 & -1\\
1 & 0 & -1 \\
1 & 0 & -2\\
0 & 0 & -1 \\
\hline
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1
\end{array}\right)\sim_c \left(\begin{array}{rrr}
\boxed{1} & 0 & 0\\
1 & 0 & 0 \\
1 & 0 & -1\\
0 & 0 & -1 \\
\hline
1 & 0 & 1\\
0 & 1 & 0\\
0 & 0 & 1
\end{array}\right)\sim_c 
\left(\begin{array}{rrr}
\boxed{1} & 0 & 0\\
1 & 0 & 0 \\
1 & \boxed{1} & 0\\
0 & 1 & 0 \\
\hline
1 & -1 & 0\\
0 & 0 & 1\\
0 & -1 & 0
\end{array}\right)\sim_c 
\left(\begin{array}{rr|r}
1 & 0 & 0\\
1 & 0 & 0 \\
0 & 1 & 0\\
-1 & 1 & 0 \\
\hline
2 & -1 & 0\\
0 & 0 & 1\\
1 & -1 & 0
\end{array}\right)
$$

Así que una base de la $Im(f)$ es $\{(1,1,0,-1),(0,0,1,1)\}$ y una base del $N(f)$ es $\{(0,1,0)\}$.
</li>
<li>
Usando el método de los 4 pasos, necesitamos calcular:

$$
\begin{array}{l}
f(0,0,-1)=\\
f(1,0,1)=\\
f(-1,1,-1)=
\end{array}
$$

para ello usamos la expresión matricial de la aplicación respecto de la base canónica ($Y_{B_{c}}=AX_{B_c}$):

$$
\left(\begin{array}{rrr}
1 & 0 & -1\\
1 & 1 & 0 \\
1 & 0 & -1\\
0 & 1 & 0 
\end{array}\right) \left(\begin{array}{r}
0 \\
0 \\
-1\\
\end{array}\right)= \left(\begin{array}{r}
1 \\
0 \\
1\\
0\\
\end{array}\right); 
\hspace{0.5cm} \left(\begin{array}{rrr}
1 & 0 & -1\\
1 & 1 & 0 \\
1 & 0 & -1\\
0 & 1 & 0 
\end{array}\right) \left(\begin{array}{r}
1 \\
0 \\
1\\
\end{array}\right)= \left(\begin{array}{r}
0 \\
1 \\
0\\
0\\
\end{array}\right)  
$$

$$
\left(\begin{array}{rrr}
1 & 0 & -1\\
1 & 1 & 0 \\
1 & 0 & -1\\
0 & 1 & 0 
\end{array}\right) \left(\begin{array}{r}
-1 \\
1 \\
-1\\
\end{array}\right)= \left(\begin{array}{r}
0 \\
0 \\
0\\
1\\
\end{array}\right)
$$

Así que 

$$
\begin{array}{l}
f(0,0,-1)=(1,0,1,0)\\
f(1,0,1)=(0,1,0,0)\\
f(-1,1,-1)=(0,0,0,1)
\end{array}
$$

que ya son coordenadas en la base canónica de $\mathbb{R}^{4}$, luego solo nos queda el paso 4:

$$
\mathcal{M}(f,B,B_c)=\left(\begin{array}{rrr}
1 & 0 & 0\\
0 & 1 & 0 \\
1 & 0 & 0\\
0 & 0 & 1 
\end{array}\right)
$$
</li>
<li>
Elegimos una base cualquiera del primer espacio, por ejemplo la canónica:
$B_1=B_c=\{(1,0,0),(0,1,0),(0,0,1)\}$. 
Ahora calculamos sus imágenes (son las columnas de la matriz A):

$$
\begin{array}{l}
f(1,0,0)=(1,1,1,0)\\
f(0,1,0)=(0,1,0,1)\\
f(0,0,1)=(-1,0,-1,0)
\end{array}
$$

Elegimos la base de $\mathbb{R}^4$ que tiene como los primeros vectores a esos 3 y añadimos uno más, con la única condición de que sean base:
$$
B_2=\{(1,1,1,0), (0,1,0,1),(-1,0,-1,0),(0,0,1,0)\}
$$

y usando el método de los 4 pasos se comprueba que efectivamente $\mathcal{M}(f,B_1,B_2)=C$.
</li>
</ol>

::::
:::::

::::: {#exr-24 .medio}

Dado el endomorfismo $f: \mathbb{R}^{3} \longrightarrow \mathbb{R}^3$ dado por
$$
\begin{array}{l}
f(1,1,0)=(1,0,-1)\\
f(1,0,1)=(1,-1,0)\\
f(0,1,1)=(0,1,1)
\end{array}
$$

<ol type="a">
<li>Calcula la matriz de $f$ respecto de la base canónica. </li>
<li>Determina si este endomorfismo es inyectivo, sobreyectivo, biyectivo o ninguna de estas cosas. </li>
<li>Calcula la matriz de $f$ respecto de la base 

$$
B=\{(1,1,0),(1,0,1),(0,1,1)\}
$$
</li>
<li>Calcula un vector cuya imagen por $f$ sea $(0,1,-1)$. </li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>
Necesitamos calcular las imágenes de los vectores de la base canónica; para ello usamos la siguiente forma:

$$
\left[ \begin{array}{c}
v\\
\hline
f(v)
\end{array}\right]
= \left(\begin{array}{rrr}
1 & 1 & 0 \\
1 & 0 & 1 \\
0 & 1 & 1  \\
\hline
1 & 1 & 0 \\
0 & -1 & 1 \\
-1 & 0 & 1  \\
\end{array}\right)\sim_c  \left(\begin{array}{rrr}
1 & 0 & 0 \\
1 & -1 & 1 \\
0 & 1 & 1  \\
\hline
1 & 0 & 0 \\
0 & -1 & 1 \\
-1 & 1 & 1  \\
\end{array}\right)\sim_c  \left(\begin{array}{rrr}
1 & 0 & 0 \\
0 & 1 & 0 \\
1 & -1 & 2  \\
\hline
1 & 0 & 0 \\
-1 & 1 & 0 \\
0 & -1 & 2  \\
\end{array}\right)
$$

$$
\sim_c  \left(\begin{array}{rrr}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1  \\
\hline
1 & 0 & 0 \\
-1 & 1 & 0 \\
-1 & 0 & 1  \\
\end{array}\right)
$$

por tanto 

$$
M(f,B_c)= \left(\begin{array}{rrr}
1 & 0 & 0 \\
-1 & 1 & 0 \\
-1 & 0 & 1  \\
\end{array}\right)
$$

</li>
<li>
Es inmediato que el rango de la matriz asociada es 3, así que $dim\, Im(f)=3=dim\, \mathbb{R}^{3}$ y por tanto es sobreyectiva. Además como $dim\ N(f)+dim\ Im(f)= dim \, \mathbb{R}^{3}$ entonces $dim\, N(f)=0$ y también es inyectiva. Se trata entonces de una aplicación <b> biyectiva</b>.
</li>
<li>
Puede realizarse mediante el método de los 4 pasos, solo habría que calcular, en el paso 3, las coordenadas respecto de $B$. También puede plantearse el diagrama 
 
$$
\begin{array}{llcr}
     &                       &         C              & \\
 f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{3}_{B_{c}}   \\
    &                       &                        &                     \\
    &   \uparrow_I&              & \uparrow_{P} \\
    &                        &         P^{-1}C             &                   \\
f: & \mathbb{R}^{3}_{B}     & \longrightarrow        &\mathbb{R}^{3}_{B}   \\
\end{array}
$$ 

siendo 
$$
C= \left(\begin{array}{rrr}
1 & 1 & 0 \\
0 & -1 & 1 \\
-1 & 0 & 1  \\
\end{array}\right)$$
Calculamos $P^{-1}$:
$$ \left(\begin{array}{rrr|rrr}
1 & 1 & 0 & 1 & 0 & 0 \\
1 & 0 & 1& 0 & 1 & 0 \\
0 & 1 & 1 & 0 & 0 & 1 \\
\end{array}\right)\sim_f  \left(\begin{array}{rrr|rrr}
1 & 1 & 0 & 1 & 0 & 0 \\
0 & -1 & 1& -1 & 1 & 0 \\
0 & 0 & 2 & -1 & 1 & 1 \\
\end{array}\right)\sim_f \left(\begin{array}{rrr|rrr}
1 & 1 & 0 & 1 & 0 & 0 \\
0 & 1 & 0& 1/2 & -1/2 & 1/2 \\
0 & 0 & 1 & -1/2 & 1/2 & 1/2 \\
\end{array}\right)
$$

$$
\sim_f \left(\begin{array}{rrr|rrr}
1 & 0 & 0 & 1/2 & 1/2 & -1/2 \\
0 & 1 & 0& 1/2 & -1/2 & 1/2 \\
0 & 0 & 1 & -1/2 & 1/2 & 1/2 \\
\end{array}\right)
$$

Por tanto 
$$ 
M(f,B)= \left(\begin{array}{rrr}
1/2 & 1/2 & -1/2 \\
1/2 & -1/2 & 1/2 \\
-1/2 & 1/2 & 1/2 \\
\end{array}\right)\left(\begin{array}{rrr}
1 & 1 & 0 \\
0 & -1 & 1 \\
-1 & 0 & 1  \\
\end{array}\right)= \left(\begin{array}{rrr}
1 & 0 & 0 \\
0 & 1 & 0 \\
-1 & -1 & 1  \\
\end{array}\right)
$$

</li>
<li>
Planteamos el sistema

$$
\left(\begin{array}{rrr}
1 & 0 & 0 \\
-1 & 1 & 0 \\
-1 & 0 & 1  \\
\end{array}\right) \left(\begin{array}{c}
x\\
y \\
z \\
\end{array}\right)= \left(\begin{array}{c}
0\\
1 \\
-1 \\
\end{array}\right)
$$

y resolviéndolo

$$
x=0; y=1; z=-1
$$

luego un tal vector es $(0,1,-1)$.
</li>
</ol>

::::
:::::