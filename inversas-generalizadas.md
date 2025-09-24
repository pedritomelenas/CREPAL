---
title: Inversas generalizadas
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

*Matrices de rango pleno por filas por columnas. Inversas por la izquierda/ por la derecha de una matriz. Cálculo de inversas por la izquierda/ por la derecha. Factorización de rango pleno de una matriz. Cálculo de la inversa de Moore-Penrose de una matriz (o inversa generalizada). Solución de norma mínima de un sistema compatible indeterminado. Solución mínimo-cuadrática de un sistema. Valores singulares.*


<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_basico" value="basicoon" checked onclick="mostrar();"> Básicos </button> 
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_medio" value="medioon" checked onclick="mostrar();"> Dificultad media </button>
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_avanzado" value="avanzadon" checked onclick="mostrar();"> Avanzados. </button>


<script>
comprueba_asignatura();
window.addEventListener("load", function(){
   mostrar();
});

$('#titulacion').on('hide.bs.dropdown', ({ clickEvent }) => {
  if (clickEvent?.target) {
    if (['fisica','matematicas','telecomunicaciones','estadistica'].includes($(clickEvent.target).data('titulo'))){
      casilla_cf.checked = false;
    }else{
      casilla_cf.checked = true;
    }
    mostrar();
  }
})
</script>

::::: {#exr-1 .basico}

Estudia si estas matrices tienen inversa a izquierda o a derecha o ninguna de ellas. 
$$A_1=\left( \begin{array}{rrr}
1 & 2 & 3\\
2 & 1 & 0\\
0 & 3 & 6
\end{array}\right);  \hspace{1cm}
A_2= \left( \begin{array}{rr}
1 & 2 \\
2 & 1 \\
3 & 3 
\end{array}\right);  \hspace{1cm}
A_3=\left( \begin{array}{rrrrr}
1 & 2 & 3 & 4 & 5\\
5 & 4 & 3 & 2 & 1\\
2 & 4 & 6 & 8 & 10
\end{array}\right)
$$


:::: {.callout collapse="true" title="Solución"}

Una matriz tiene inversa a izquierda si, y solo si, es de rango pleno por columnas (es decir, su rango coincide con el número de columnas) y tiene inversa a derecha si, y solo si, es de rango pleno por filas. 
Calculamos los rangos de cada una de las matrices:

$$
A_1=\left( \begin{array}{rrr}
1 & 2 & 3\\
2 & 1 & 0\\
0 & 3 & 6
\end{array}\right)\sim_f \left( \begin{array}{rrr}
\boxed{1} & 2 & 3\\
0 & -3 & -6\\
0 & 3 & 6
\end{array}\right)\sim_f \left( \begin{array}{rrr}
\boxed{1} & 2 & 3\\
0 &\boxed{1} & 2\\
0 & 0 & 0
\end{array}\right)
$$

y obtenemos que $rg(A_1)=2$ luego $A_1$ no tiene ni inversa a izquierda ni a derecha.

$$
A_2= \left( \begin{array}{rr}
1 & 2 \\
2 & 1 \\
3 & 3 
\end{array}\right)\sim_c \left( \begin{array}{rr}
\boxed{1} & 0 \\
2 & -3 \\
3 & -3 
\end{array}\right)\sim_c \left( \begin{array}{rr}
\boxed{1} & 0 \\
2 & \boxed{1} \\
3 & 1 
\end{array}\right)
$$

y como $rg(A_2)=2=\mbox{ nº de columnas}$, entonces $A_2$ es de rango pleno por columnas y, por tanto, tiene inversa a izquierda. 

$$
A_3=\left( \begin{array}{rrrrr}
1 & 2 & 3 & 4 & 5\\
5 & 4 & 3 & 2 & 1\\
2 & 4 & 6 & 8 & 11
\end{array}\right)\sim_f \left( \begin{array}{rrrrr}
\boxed{1} & 2 & 3 & 4 & 5\\
0 & -6 & -12 & -18 & -24\\
0 & 0 & 0 & 0 & \boxed{1}
\end{array}\right)\sim_f \left( \begin{array}{rrrrr}
\boxed{1} & 2 & 3 & 4 & 5\\
0 & \boxed{1} & 2 & 3 & 4\\
0 & 0 & 0 & 0 & \boxed{1}
\end{array}\right)
$$

y obtenemos que $rg(A_3)=3=\mbox{ nº de filas}$, así que $A_3$ es de rango pleno por filas y, por tanto, tiene inversa a derecha. 

::::
:::::

::::: {#exr-2 .basico}

Calcula una inversa a izquierda de la matriz

$$
\left( \begin{array}{rrr}
1 & 2 & 3 \\
5 & 4 & 0 \\
2 & 4 & 1 \\
1 & 0 & 1 
\end{array}\right)
$$


:::: {.callout collapse="true" title="Solución"}

En primer lugar comprobamos que existe, calculando el rango de la matriz:

$$
\left( \begin{array}{rrr}
1 & 2 & 3 \\
5 & 4 & 0 \\
2 & 4 & 1 \\
1 & 0 & 1 
\end{array}\right)\sim_c \left( \begin{array}{rrr}
\boxed{1} & 0 & 0 \\
5 & -6 & -15 \\
2 & 0 & -5 \\
1 & -2 & -2 
\end{array}\right)\sim_f \left( \begin{array}{rrr}
\boxed{1} & 0 & 0 \\
0 & -6 & -15 \\
0 & 0 & \boxed{1} \\
0 & -2 & -2 
\end{array}\right)\sim_f \left( \begin{array}{rrr}
\boxed{1} & 0 & 0 \\
0 & \boxed{1} & 0 \\
0 & 0 & \boxed{1} \\
0 & 0 & 0 
\end{array}\right)
$$

<b>Observación:</b> hemos utilizado tanto operaciones por columnas como por filas, para obtener los pivotes rápidamente.

Como en efecto el rango coincide con el número de columnas la matriz tiene inversa a izquierda. Para calcularla se puede proceder de dos formas distintas:

<ol type="1">
<li> Calculando una matriz de paso a forma escalonada reducida por filas de la que extraeremos una inversa a izquierda. En este caso se obtiene una inversa a izquierda que no necesariamente cumple las condiciones de Moore-Penrose:

$$
\left( \begin{array}{rrr|cccc}
1 & 2 & 3 & 1 & 0 & 0 & 0\\
5 & 4 & 0 & 0 & 1 & 0 & 0\\
2 & 4 & 1 & 0 & 0 & 1 & 0\\
1 & 0 & 1 & 0 & 0 & 0 & 1
\end{array}\right)\sim_f 
\left( \begin{array}{rrr|rrrr}
\boxed{1} & 2 & 3 & 1 & 0 & 0 & 0\\
0 & -6 & -15 & -5 & 1 & 0 & 0\\
0 & 0 & -5 & -2 & 0 & 1 & 0\\
0 & -2 & -2 & -1 & 0 & 0 & 1
\end{array}\right)
\sim_f 
$$

$$
\left( \begin{array}{rrr|rrrr}
\boxed{1} & 2 & 3 & 1 & 0 & 0 & 0\\
0 & -6 & -15 & -5 & 1 & 0 & 0\\
0 & 0 & \boxed{1} & 2/5 & 0 & -1/5 & 0\\
0 & -2 & 0 & -1/5 & 0 & -2/5 & 1
\end{array}\right)\sim_f 
\left( \begin{array}{rrr|rrrr}
\boxed{1} & 2 & 3 & 1 & 0 & 0 & 0\\
0 & -6 & -15 & -5 & 1 & 0 & 0\\
0 & 0 & \boxed{1} & 2/5 & 0 & -1/5 & 0\\
0 & \boxed{1} & 0 & 1/10 & 0 & 1/5 & -1/2
\end{array}\right)
\sim_f 
$$

$$
\left( \begin{array}{rrr|rrrr}
\boxed{1} & 0 & 3 & 4/5 & 0 & -2/5 & 1\\
0 & \boxed{1} & 0 & 1/10 & 0 & 1/5 & -1/2\\
0 & 0 & \boxed{1} & 2/5 & 0 & -1/5 & 0\\
0 & -6 & -15 & -5 & 1 & 0 & 0\\
\end{array}\right)\sim_f
\left( \begin{array}{rrr|rrrr}
\boxed{1} & 0 & 0 & -2/5 & 0 & 1/5 & 1\\
0 & \boxed{1} & 0 & 1/10 & 0 & 1/5 & -1/2\\
0 & 0 & \boxed{1} & 2/5 & 0 & -1/5 & 0\\
0 & -6 & -15 & -5 & 1 & 0 & 0\\
\end{array}\right)=(F|Q)
$$

<b> Observación:</b> aunque no hemos terminado el proceso tenemos una matriz $Q$ tal que $$QA=F$$ y como las 3 primeras filas de $F$ forman una matriz identidad entonces las 3 primeras filas de $Q$ forman una inversa a izquierda de $A$. 
Comprobamos el resultado:

$$
\left( \begin{array}{rrrr}
-2/5 & 0 & 1/5 & 1\\
1/10 & 0 & 1/5 & -1/2\\
2/5 & 0 & -1/5 & 0\\
\end{array}\right)\left( \begin{array}{rrr}
1 & 2 & 3 \\
5 & 4 & 0 \\
2 & 4 & 1 \\
1 & 0 & 1 
\end{array}\right)=
\left( \begin{array}{rrr}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{array}\right)
$$
</li>

<li> Utilizando que la inversa a izquierda que cumple las condiciones de Moore-Penrose viene dada por la fórmula:

$$A^L = (A^t A)^{-1}A^t$$

En primer lugar calculamos la inversa de $A^tA$:

$$
\left(\begin{array}{rrr|rrr}
30 &  30  &  5 & 1 & 0 & 0\\
30 &  36  & 10 & 0 & 1 & 0\\
5 &  10  & 10 & 0 & 0 & 1
\end{array}\right) \sim_f 
\left(\begin{array}{rrr|rrr}
6 &  6  &  1 & 1/5 & 0 & 0\\
0 &  6  & 5 & -1 & 1 & 0\\
5 &  10  & 10 & 0 & 0 & 1
\end{array}\right)
$$

$$\sim_f \left(\begin{array}{rrr|rrr}
1 &  -4  &  -9 & 1/5 & 0 & -1\\
0 &  6  & 5 & -1 & 1 & 0\\
5 &  10  & 10 & 0 & 0 & 1
\end{array}\right)\sim_f 
\left(\begin{array}{rrr|rrr}
1 &  -4  &  -9 & 1/5 & 0 & -1\\
0 &  6  & 5 & -1 & 1 & 0\\
0 &  30  & 55 & -1 & 0 & 6
\end{array}\right)
$$

$$
\sim_f \left(\begin{array}{rrr|rrr}
1 &  -4  &  -9 & 1/5 & 0 & -1\\
0 &  6  & 5 & -1 & 1 & 0\\
0 &  0  & 30 & 4 & -5 & 6
\end{array}\right) \sim_f \left(\begin{array}{rrr|rrr}
1 &  -4  &  -9 & 1/5 & 0 & -1\\
0 &  1  & 5/6 & -1/6 & 1/6 & 0\\
0 &  0  & 1 & 2/15 & -1/6 & 1/5
\end{array}\right) 
$$

$$
\sim_f \left(\begin{array}{rrr|rrr}
1 &  0  &   -17/3 & -7/15 &  2/3 & -1\\
0 &  1  & 5/6 & -1/6 & 1/6 & 0\\
0 &  0  & 1 & 4/25 & -1/5 & 6/25
\end{array}\right) 
\sim_f \left(\begin{array}{rrr|rrr}
1 &  0  &   0 &   13/45  & -5/18 & 2/15\\
0 &  1  &  0 &   -5/18   &   11/36 & -1/6\\
0 &  0  & 1 & 4/25 & -1/5 & 6/25
\end{array}\right) 
$$

Luego 

$$
(A^tA)^{-1}=  \left(\begin{array}{rrr}
13/45  & -5/18 & 2/15\\
-5/18   &   11/36 & -1/6\\
4/25 & -1/5 & 6/25
\end{array}\right)
$$

y nos queda multiplicar por $A^t$ a la derecha:

$$
A^L = \left(\begin{array}{rrr}
2/15 & 1/3 &  -2/5\\
-1/6  &  -1/6 &  1/2\\
2/5  &    0  &  -1/5 
\end{array}\right)
$$
</li>
</ol>

<b>Observación:</b> ambos resultados son diferentes debido a la no unicidad para la existencia de inversa a izquierda.

::::
:::::

::::: {#exr-3 .basico}

Calcula una inversa a derecha de la matriz

$$
\left( \begin{array}{rrrr}
1 & 2 & 3 & 4 \\
5 & 4 & 3 & 2 \\
2 & 4 & 6 & 1 
\end{array}\right)
$$


:::: {.callout collapse="true" title="Solución"}

Si calculamos la forma escalonada reducida por columnas de esta matriz (en este caso mediante un software adecuado) junto con una matriz de paso obtenemos

$$
\left( \begin{array}{rrrr}
1 & 2 & 3 & 4 \\
5 & 4 & 3 & 2 \\
2 & 4 & 6 & 1 \\
\hline
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
\end{array}\right)\sim_c
\left( \begin{array}{rrrr}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
\hline
0 & 0 & 0 & 1\\
-3/14 & 1/2 & -1/7 & -2\\
 2/21 &-1/3 &  2/7 &  1\\
  2/7 &   0 & -1/7 &0 
\end{array}\right)
$$
 
De donde una inversa a derecha es 

$$
A^{R}=
\left( \begin{array}{rrr}
0 & 0 & 0 \\
-3/14 & 1/2 & -1/7 \\
2/21 &-1/3 &  2/7 \\
2/7 &   0 & -1/7  
\end{array}\right)
$$

También puede calcularse una mediante la fórmula 

$$A^R= A^{t}(AA^{t})^{-1}$$

que es además la inversa de Moore-Penrose de la matriz $A$.

::::
:::::

::::: {#exr-4 .basico}

Calcula una factorización de rango pleno de las matrices 
$$
A=\left( \begin{array}{rr}
6 & 9 \\
10 & 15 \\
\end{array}\right); \hspace{1cm}
B=\left( \begin{array}{rrr}
2 & 1 & 5 \\
-1 & 1 & 3 \\
\end{array}\right)
$$


:::: {.callout collapse="true" title="Solución"}

Comenzamos calculando la forma escalonada reducida por filas de $A$ y una matriz de paso $Q$:
$$
\left( \begin{array}{rr|rr}
6 & 9 & 1 & 0\\
10 & 15 & 0 & 1\\
\end{array}\right)\sim_f
\left( \begin{array}{rr|rr}
2 & 3 & 1/3 & 0\\
2 & 3 & 0 & 1/5\\
\end{array}\right)
\sim_f
\left( \begin{array}{rr|rr}
2 & 3 & 1/3 & 0\\
0 & 0 & -1/3 & 1/5\\
\end{array}\right)\sim_f
\left( \begin{array}{rr|rr}
1 & 3/2 & 1/6 & 0\\
0 & 0 & -1/3 & 1/5\\
\end{array}\right)
$$

Calculamos la inversa de la matriz de paso:
$$\left( \begin{array}{rr|rr}
1/6 & 0 & 1 & 0\\
-1/3 & 1/5 & 0 & 1\\
\end{array}\right)\sim_f
\left( \begin{array}{rr|rr}
1 & 0 & 6 & 0\\
-1 & 3/5 & 0 & 3\\
\end{array}\right)\sim_f
\left( \begin{array}{rr|rr}
1 & 0 & 6 & 0\\
0 & 1 & 10 & 5\\
\end{array}\right)
$$

Tenemos que 
$$
\left( \begin{array}{rr}
6 & 9\\
10 & 15\\
\end{array}\right)=Q^{-1}H=\left( \begin{array}{r|r}
6 & 0\\
10 & 5\\
\end{array}\right)
\left( \begin{array}{rr}
1 & 3/2 \\
\hline
0 & 0  \\
\end{array}\right)
$$

De donde obtenemos que una descomposición de rango pleno es:
$$
\left( \begin{array}{rr}
6 & 9\\
10 & 15\\
\end{array}\right)=\left( \begin{array}{r}
6 \\
10 \\
\end{array}\right)
\left( \begin{array}{rr}
1 & 3/2 \\
\end{array}\right)
$$

Procedemos del mismo modo para $B$:
$$
\left( \begin{array}{rrr|rr}
2 & 1 & 5 & 1& 0\\
-1 & 1 & 3 & 0 & 1\\
\end{array}\right)\sim_f
\left( \begin{array}{rrr|rr}
\boxed{1} & -1 & -3 & 0 & -1\\
2 & 1 & 5 & 1& 0\\
\end{array}\right)\sim_f
\left( \begin{array}{rrr|rr}
\boxed{1} & -1 & -3 & 0 & -1\\
0 & 3 & 11 & 1 & 2\\
\end{array}\right)
$$

$$
\sim_f
\left( \begin{array}{rrr|rr}
\boxed{1} & -1 & -3 & 0 & -1\\
0 & 3 & 11 & 1 & 2\\
\end{array}\right)\sim_f
\left( \begin{array}{rrr|rr}
\boxed{1} & -1 & -3 & 0 & -1\\
0 & \boxed{1}& 11/3 & 1/3 & 2/3\\
\end{array}\right)
\sim_f
\left( \begin{array}{rrr|rr}
\boxed{1} & 0 & 2/3 & 1/3 & -1/3\\
0 & \boxed{1}& 11/3 & 1/3 & 2/3\\
\end{array}\right)
$$

Calculamos ahora la inversa de la matriz de paso (se omite el proceso):

$$
Q^{-1}= \left( \begin{array}{rr}
1/3 & 1/3\\
-1/3 & 2/3\\
\end{array}\right)
$$

y obtenemos que 

$$
A=\left( \begin{array}{rrr}
2 & 1 & 5 \\
-1 & 1 & 3 \\
\end{array}\right)=Q^{-1}H= \left( \begin{array}{rr}
1/3 & 1/3\\
-1/3 & 2/3\\
\end{array}\right)\left( \begin{array}{rrr}
1 & 0 & 2/3 \\
0 & 1 & 11/3 \\
\end{array}\right)
$$

que es una descomposición de rango pleno.

::::
:::::

::::: {#exr-5 .basico}

Sea el sistema de ecuaciones lineales 
$$
\begin{pmatrix}
1 & 0\\
1 & 1\\
1 & 2\\
1 & 3
\end{pmatrix}
\begin{pmatrix}
x\\
y
\end{pmatrix}=
\left(
\begin{array}{rr}
2\\
-1\\
1\\
-2
\end{array}
\right)
$$

<ol type="a">
<li> Prueba que $A$ es de rango pleno por columnas.</li>
<li> Encuentra la única solución mínimo-cuadrática del sistema.</li>
</ol>


:::: {.callout collapse="true" title="Solución"}

<ol type="a">

<li> Observando la matriz $A$ obtenemos que tiene dos pivotes
$$
\begin{pmatrix}
\boxed{1} & 0\\
1 &     \boxed{1}\\
1 & 2\\
1 & 3
\end{pmatrix}
$$

así que su rango es 2 que coincide con el número de columnas, por tanto es de rango pleno por columnas. 
</li>
<li> Puesto que $A$ es de rango pleno por columnas existe una única solución mínimo-cuadrática. Para calcularla podemos usar la fórmula 
$$
X=A^{L}B\quad   \mbox{con } A^{L}=(A^tA)^{-1}A^t
$$

(o bien resolver el sistema compatible $A^tAX=A^tB$).
<b> Observación:</b> en este caso no es válida una inversa por la izquierda cualquiera, debe cumplir las condiciones de la inversa de Moore-Penrose.

$$
A^tA= \begin{pmatrix}
1 & 1 & 1 & 1\\
0 & 1 & 2 & 3\\
\end{pmatrix} \begin{pmatrix}
1 & 0\\
1 & 1\\
1 & 2\\
1 & 3
\end{pmatrix}= \begin{pmatrix}
4 & 6\\
6 & 14\\
\end{pmatrix}
$$

que tiene por inversa

$$
(A^tA)^{-1}= \left( \begin{array}{rrrr}
7/10 & -3/10\\
-3/10 & 1/5\\
\end{array}\right)
$$ 

Por tanto 

$$
A^{L}= (A^tA)^{-1}A^t=  \left( \begin{array}{rrrr}
7/10 & -3/10\\
-3/10 & 1/5\\
\end{array}\right) \begin{pmatrix}
1 & 1 & 1 & 1\\
0 & 1 & 2 & 3\\
\end{pmatrix}=   \left( \begin{array}{rrrr}
7/10 & 2/5 & 1/10 & -1/5\\
-3/10 & -1/10 & 1/10 & 3/10\\
\end{array}\right)
$$ 

Luego la solución mínimo cuadrática es 
$$
X=A^{L}B= \left( \begin{array}{rrrr}
7/10 & 2/5 & 1/10 & -1/5\\
-3/10 & -1/10 & 1/10 & 3/10\\
\end{array}\right) \left(\begin{array}{rr}
2\\
-1\\
1\\
-2
\end{array}\right)
= \left(\begin{array}{rr}
3/2\\
-1\\
\end{array}
\right)
$$ 

</li>
</ol>

::::
:::::

::::: {#exr-6 .basico}

Sea el sistema de ecuaciones lineales 
$$
\begin{pmatrix}0 & 1 & 2\\1 & 1 & 1\end{pmatrix}    
\begin{pmatrix}
x\\
y\\
z
\end{pmatrix}=
\left(
\begin{array}{rr}
2\\
-1
\end{array}
\right).
$$

<ol type="a">
<li> Demuestra que $A$ es de rango pleno for filas.</li>
<li> Encuentra la solución de norma mínima del sistema.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Para comprobar que la matriz de coeficientes es de rango pleno por filas observamos que el menor de orden 2 formado por las dos primeras columnas es distinto de 0, con lo que el rango es 2 y coincide con el número de filas.

</li>
<li> Como la matriz de coeficientes es de rango pleno por filas (y por tanto el sistema de ecuaciones es compatible) la solución de norma mínima viene dado por:
$$X=A^{R}B$$

Calculamos entonces la inversa a derecha de $A$ que es también su inversa de Moore-Penrose (no es válida cualquier otra inversa a derecha) $A^R=A^t (AA^t)^{-1}$:

$$
AA^t=\begin{pmatrix}0 & 1 & 2\\1 & 1 & 1\end{pmatrix}
\begin{pmatrix}0 & 1 \\1 & 1 \\ 2 & 1\end{pmatrix}= \left( \begin{array}{rr}
5& 3 \\
3 & 3 \\
\end{array}\right)\, (AA^t)^{-1}= \left( \begin{array}{rr}
1/2 & -1/2 \\
-1/2 & 5/6 \\
\end{array}\right)
$$

$$
A^{R}= \begin{pmatrix}0 & 1 \\1 & 1 \\ 2 & 1\end{pmatrix}\left( \begin{array}{rr}
1/2 & -1/2 \\
-1/2 & 5/6 \\
\end{array}\right)= \left( \begin{array}{rr}
-1/2 & 5/6 \\
0 & 1/3\\
1/2 & -1/6 \\
\end{array}\right)
$$

Por último, para calcular la solución de norma mínima multiplicamos por la columna de términos independientes:

$$
X= A^{R}B=\left( \begin{array}{rr}
-1 & 1 \\
1 & 0 \\
0 & 0 
\end{array}\right)\left( \begin{array}{r}
2\\
-1\\
\end{array}\right)=  \left( \begin{array}{r}
-11/6\\
-1/3\\
7/6
\end{array}\right)
$$   

</li>
</ol>

::::
:::::

::::: {#exr-7 .medio}

Sea $A\in \mathcal{M}_{4\times 3}(\mathbb{R})$ la matriz
$$
A=\left(
\begin{array}{rrr}
-1 & 0 & 1\\-1 & 1 & 1\\-1 & 3 & 1\\1 & -2 & -1
\end{array}
\right).
$$

<ol type="a">
<li> Encuentra una descomposición de rango pleno de $A$.</li>
<li> Calcula $A^\dagger$, la inversa generalizada de $A$.</li>
<li> Para $b=(1,1,1,1)$, calcula la solución mínimo cuadrática de norma mínima del sistema $Ax=b$.</li>
</ol>


:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Para calcular la descomposición de rango pleno de $A$, calculamos su forma escalonada por filas $H$ y una matriz de paso $P$ tales que $PA=H$.
Para ello, le añadimos a $A$ a la derecha la matriz identidad y calculamos una forma escalonada de esa matriz:
$$
\left(\begin{array}{rrr|rrrr}
-1 & 0 & 1 & 1 & 0 & 0 & 0\\
-1 & 1 & 1 & 0 & 1 & 0 & 0\\
-1 & 3 & 1 & 0 & 0 & 1 & 0\\
1 & -2 & -1 & 0 & 0 & 0 & 1
\end{array}\right) \sim_f 
\left(\begin{array}{rrr|rrrr}
1 & 0 & -1 & 0 & 0 & 2 & 3\\
0 & 1 & 0 & 0 & 0 & 1 & 1\\
0 & 0 & 0 & 1 & 0 & 2 & 3\\
0 & 0 & 0 & 0 & 1 & 1 & 2
\end{array}\right).
$$

Tenemos por tanto que
$$
H=\left(\begin{array}{rrr}
1 & 0 & -1\\0 & 1 & 0\\0 & 0 & 0\\0 & 0 & 0
\end{array}\right), \hspace{1cm} 
P=\left(\begin{matrix}0 & 0 & 2 & 3\\0 & 0 & 1 & 1\\1 & 0 & 2 & 3\\0 & 1 & 1 & 2\end{matrix}\right).
$$

Tomamos como $F$ la matriz formada por las dos filas no nulas de $H$, y por tanto
es la matriz compuesta por las dos primeras columnas de $P^{-1}$:
$$
P^{-1}=\left(\begin{array}{rrrr}-1 & 0 & 1 & 0\\-1 & 1 & 0 & 1\\-1 & 3 & 0 & 0\\1 & -2 & 0 & 0\end{array}\right),
\ F=\left(\begin{array}{rrr} 1 & 0 & -1 \\0 & 1 & 0 \end{array}\right),\ 
C=\left(\begin{array}{rr}-1 & 0\\-1 & 1\\-1 & 3\\1 & -2\end{array}\right)
$$

De esta forma tenemos  $A=CF$, con $C$ de rango pleno por columnas y $F$ de rango pleno por filas.

</li>
<li> Sabemos que $A^\dagger=F^D C^I$, con $F^D= F^t(F F^t)^{-1}$ y $C^I=(C^tC)^{-1}C^t$:

$$
F^D=\left(\begin{array}{rr}\frac{1}{2} & 0\\0 & 1\\- \frac{1}{2} & 0\end{array}\right), 
\ C^I=\left(\begin{array}{rrrr}- \frac{7}{10} & - \frac{2}{5} & \frac{1}{5} & \frac{1}{10}\\- \frac{3}{10} & - \frac{1}{10} & \frac{3}{10} & - \frac{1}{10}\end{array}\right),
\ A^\dagger= \left(\begin{array}{rrrr}- \frac{7}{20} & - \frac{1}{5} & \frac{1}{10} & \frac{1}{20}\\- \frac{3}{10} & - \frac{1}{10} & \frac{3}{10} & - \frac{1}{10}\\\frac{7}{20} & \frac{1}{5} & - \frac{1}{10} & - \frac{1}{20}\end{array}\right)
$$

</li>

<li> La solución mínimo cuadrática de norma mínima de $AX=b$ viene dada por  $A^\dagger b=(-2/5,-1/5,2/5)$ </li>
</ol>


::::
:::::

::::: {#exr-8 .medio}

Sea $A\in \mathcal{M}_{4\times 3}(\mathbb{R})$ la matriz
$$
A=\left(
\begin{array}{rrr}
1 & 1 & -1\\1 & 3 & -1\\1 & 0 & -1\\-1 & -2 & 1
\end{array}
\right).
$$

<ol type="a">
<li> Encuentra los valores singulares de $A$.</li>
<li> Encuentra una descomposición de rango pleno de $A$.</li>
<li> Calcula $A^\dagger$, la inversa generalizada de $A$.</li>
<li> Para $b=(1,2,3,4)^t$, calcula la solución mínimo cuadrática de norma mínima del sistema $Ax=b$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Los valores singulares son las raíces cuadradas de los valores propios de la matriz $AA^t$ (o de su traspuesta, $A^tA$). 
$$
AA^{t}= \left( \begin{array}{rrrr}
3 & 5 & 2  & -4\\
5 & 11& 2  & -8\\
2 &  2& 2  & -2\\
-4& -8& -2 & 6
\end{array}\right)
$$

El cálculo de los valores propios es laborioso, así que puede realizarse usando un software adecuado, de esta forma hemos obtenido que son $20$, $2$ (ambos con multiplicidad algebraica 1) y $0$ con multiplicidad algebraica 2 (pueden comprobarse estos resultados mediante el cálculo del rango de $AA^t-\lambda I$ para cada uno de los valores propios).
Por tanto los valores singulares son $2\sqrt{5}$, $\sqrt{2}$ y $0$.

</li>
<li> Para la descomposición de rango pleno calculamos $H$ la forma escalonada reducida de $A$ y una matriz de paso $P$ de forma que $AP=H$:

$$
\left(
\begin{array}{rrr|rrrr}
1 & 1 & -1& 1 & 0 & 0& 0\\
1 & 3 & -1& 0 & 1 & 0 & 0\\
1 & 0 & -1& 0 & 0 & 1& 0\\
-1 & -2 & 1& 0 & 0 & 0 & 1
\end{array}\right)\sim_f 
\left(
\begin{array}{rrr|rrrr}
1 & 0 & -1& 0 & 0 & 1& 0\\
0 & 1 & 0& 0 & 0 & -1/2 & -1/2\\
0 & 0 & 0& 1 & 0 & -1/2& 1/2\\
0 & 0 & 0& 0 & 1 & 1/2 & 3/2
\end{array}\right)
$$

Tomamos como $F$ (de rango pleno por filas) las dos primeras filas de $H$ y como $C$ las 2 primeras columnas de $P^{-1}$ (que es de rango pleno por columnas). Así tendremos que $A=CF$:

$$
P^{-1}=  \left( \begin{array}{rrrr}
1 & 1 & 1 & 0\\
1 & 3 & 0 & 1\\
1 & 0 & 0 & 0\\
-1 &-2 & 0 & 0
\end{array}\right)\, 
F= \left( \begin{array}{rrr}
1 & 0 & -1\\
0 & 1 & 0 \\
\end{array}\right)\,
C= \left( \begin{array}{rr}
1 & 1 \\
1 & 3 \\
1 & 0 \\
-1 &-2 
\end{array}\right)\,
$$

</li>
<li> Sabemos que $A^\dagger=F^R C^L$.
Realizamos el cálculo de $F^R=F^t(FF^t)^{-1}$ y obtenemos:

$$F^D=\left(\begin{array}{rr}\frac{1}{2} & 0\\0 & 1\\- \frac{1}{2} & 0\end{array}\right)$$

Procedemos al cálculo de $C^L=(C^tC)^{-1}C^t$:

$$
C^tC=\left( \begin{array}{rrrr}
1 & 1 &  1 & -1 \\
1 & 3 & 0 & -2 \\
\end{array}\right) \left( \begin{array}{rr}
1 & 1 \\
1 & 3 \\
1 & 0 \\
-1 &-2 
\end{array}\right)
=\left( \begin{array}{rr}
4 & 6\\
6 & 14
\end{array}\right);\,  (C^tC)^{-1}= \left( \begin{array}{rr}
-7/10 & -3/10\\
-3/10 & 1/5
\end{array}\right)
$$

luego 

$$
C^L= \left( \begin{array}{rr}
-7/10 & -3/10\\
-3/10 & 1/5
\end{array}\right)\left( \begin{array}{rrrr}
1 & 1 &  1 & -1 \\
1 & 3 & 0 & -2 \\
\end{array}\right) = \left( \begin{array}{rrrr}
2/5    &   -1/5  &     7/10   &   -1/10\\
-1/10  &     3/10  &   -3/10  &    -1/10
\end{array}\right)
$$

Por último calculamos  $A^\dagger=F^R C^L$ y obtenemos

$$
A^\dagger=\left(\begin{array}{rr}\frac{1}{2} & 0\\0 & 1\\- \frac{1}{2} & 0\end{array}\right)
\left( \begin{array}{rrrr}
2/5    &   -1/5  &     7/10   &   -1/10\\
-1/10  &     3/10  &   -3/10  &    -1/10
\end{array}\right) = \left( \begin{array}{rrrr}
1/5  &    -1/10  &     7/20    &  -1/20\\
-1/10  &     3/10  &    -3/10    &  -1/10\\
-1/5  &     1/10  &    -7/20    &   1/20
\end{array}\right)
$$

</li>
<li> La solución mínimo cuadrática de norma mínima del sistema viene dada por $X=A^\dagger b$:

$$
X= \left( \begin{array}{rrrr}
1/5  &    -1/10  &     7/20    &  -1/20\\
-1/10  &     3/10  &    -3/10    &  -1/10\\
-1/5  &     1/10  &    -7/20    &   1/20
\end{array}\right)\begin{pmatrix}
1\\
2\\
3\\
4
\end{pmatrix}= \left( \begin{array}{r}
17/20\\
-4/5\\
-17/20
\end{array}\right)
$$

</li>
</ol>

::::
:::::