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

*Espacios vectoriales. Dependencia e independencia lineal. Bases y coordenadas. Cambio de base. Subespacios vectoriales: bases, dimensión, ecuaciones paramétricas y cartesianas.  Operaciones con subespacios: suma, intersección. Fórmula de las dimensiones. Suma directa, subespacios complementarios.* 


<button class="btn btn-outline-secondary btn-sm dropdown-toggle mb-2" type="button" data-bs-toggle="dropdown" aria-expanded="false" id="titulacion">
  Titulación
</button>
<ul class="dropdown-menu">
  <li><a class="dropdown-item" data-titulo="estadistica" href="#">Estadística</a></li>
  <li><a class="dropdown-item" data-titulo="fisica" href="#">Física</a></li>
  <li><a class="dropdown-item" data-titulo="informatica" href="#">Informática</a></li>
  <li><a class="dropdown-item" data-titulo="matematicas" href="#">Matemáticas</a></li>
  <li><a class="dropdown-item" data-titulo="telecomunicaciones" href="#">Telecomunicaciones</a></li>
</ul>

<button id="opcion_cf" class="btn btn-outline-secondary btn-sm mb-2"> <input type="checkbox" id="casilla_cf" value="cuerpo_finitoon" checked onclick="mostrar();"> Cuerpos finitos </button>
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

::: {.callout-tip collapse="true" title="GLOSARIO" icon="false" .table_glossary}

<table>
    <thead>
        <tr>
            <th>Término</th>
            <th>Sinónimos / Abreviatura</th>
            <th>Definición / Referencias</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Combinación lineal de vectores</td>
            <td>c.l.</td>
            <td>Vector obtenido del conjunto inicial usando las operaciones del espacio vectorial.</td>
        </tr>
        <tr>
            <td>Vectores linealmente dependientes <br> Vectores linealmente independientes</td>
            <td>l.d.<br> <br>l.i.</td>
            <td><a href="https://www.ugr.es/~pedro/alem/vectores.pdf">Web del profesor Pedro García</a> <br> 
            <a href="https://www.ugr.es/~lmerino/2-1.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Base de un espacio vectorial</td>
            <td><br></td>
            <td><a href="https://es.wikipedia.org/wiki/Base_(%C3%A1lgebra)">Wikipedia: Base</a></td>
        </tr>
        <tr>
            <td>Dimensión de un espacio vectorial</td>
            <td>$dim V$</td>
            <td>Número de vectores que hay en cualquiera de sus bases (si existe alguna)</td>
        </tr>
        <tr>
            <td>Coordenadas de un vector respecto de una base</td>
            <td><br></td>
            <td><a href="https://www.ugr.es/~lmerino/2-1.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Ecuaciones del cambio de base</td>
            <td><br></td>
            <td><a href="https://www.ugr.es/~lmerino/2-2.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Subespacio vectorial</td>
            <td>Variedad lineal</td>
            <td><a href="https://es.wikipedia.org/wiki/Base_(%C3%A1lgebra)">Wikipedia: Subespacio vectorial</a></td>
        </tr>
        <tr>
            <td>Ecuaciones paramétricas de un subespacio</td>
            <td><br></td>
            <td><a href="https://www.ugr.es/~lmerino/2-3.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Ecuaciones cartesianas de un subespacio</td>
            <td>Ecuaciones implícitas</td>
            <td><a href="https://www.ugr.es/~lmerino/2-3.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Suma de dos subespacios</td>
            <td>$U+W$</td>
            <td>Menor subespacio que contiene a ambos <br> 
            <a href="https://www.ugr.es/~lmerino/2-4.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Intersección de dos subespacios</td>
            <td>$U\cap W$</td>
            <td>Conjunto de vectores que pertenecen simultáneamente a ambos subespacios <br> 
            <a href="https://www.ugr.es/~lmerino/2-4.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Suma directa de dos subespacios</td>
            <td>$U\oplus W$</td>
            <td>Suma de dos subespacios con intersección 0<br> 
            <a href="https://www.ugr.es/~lmerino/2-5.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
        <tr>
            <td>Subespacios complementarios</td>
            <td><br></td>
            <td>Aquellos que verifican que su suma es el espacio total y su intersección es 0<br> 
            <a href="https://www.ugr.es/~lmerino/2-4.html">Apuntes del profesor Luis Merino</a></td>
        </tr>
    </tbody>
</table>

:::

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

::: {.sage}
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
x & = & \lambda \\
y & = & \mu \\ 
z & = & 4\lambda+3\mu\\
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
x & = & \lambda \\
y & = & 4\lambda \\ 
z & = & \lambda\\
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
x & = & \lambda \\
y & = & 4\lambda\\
z & = & \lambda\\
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
x & = & \lambda \\
y & = & \mu \\ 
z & = & 4\lambda +3\mu\\
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
x & = & \lambda \\
y & = & 4\lambda \\ 
z & = & \lambda\\
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
x & = & \lambda \\
y & = & 4\lambda\\
z & = & \lambda\\
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
\end{array}\right.\sim_f \left\{ \begin{array}{l}
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

<ol type='a'>
<li>Comprobar que $\mathcal{P}_3(\mathbb{R})= U\oplus W$.</li>
<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Comprobar que $\mathcal{P}_3(\mathbb{R})= U\oplus W$.

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
\end{array}\right.$ Y una base $\{x,x^3\}$.

Así que un sistema de generadores de $U+W$ es $\{1,x,x^2,x^3\}$ con lo que $U+W=\mathcal{P}_3(\mathbb{R})$, y además de que porque estos polinomios son linealmente independientes, se puede razonar con la fórmula de las dimensiones que $U\cap W=0$, con lo que se obtiene $\mathcal{P}_3(\mathbb{R})= U\oplus W$.
</li>
<li>Descomponer el vector $3x^3+x-2$ como suma de un vector en $U$ y otro en $W$.

Es inmediato que 

$$
3x^3+x-2= (-2) + (x+3x^3)
$$

y el primer polinomio está en $U$ y el segundo en $W$.
</li>
</ol>

::::
:::::

::::: {#exr-29 .basico-cuerpo_finito} 

Sea $U$ el subespacio de $(\mathbb{Z}_2)^4$ generado por los vectores 

$$
(1,1,1,0), \quad (0,1,1,1), \quad (1,0,0,1),
$$

y $W$ el subespacio de $(\mathbb{Z}_2)^4$ definido por las ecuaciones:

$$
\begin{cases}
x+y+z=0 \\
z+t=0
\end{cases}
$$

Calcula las ecuaciones cartesianas y una base de $U+W$.

:::: {.callout collapse="true" title="Solución"}

En primer lugar, calculamos una base de $U$ a partir de sus generadores:

$$
\begin{pmatrix}
1 & 1 & 1 & 0 \\
0 & 1 & 1 & 1 \\
1 & 0 & 0 & 1
\end{pmatrix}
\overset{E_{31}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 1 & 1 & 0 \\
0 & 1 & 1 & 1 \\
0 & 1 & 1 & 1
\end{pmatrix}
\overset{E_{12}(1),\,E_{32}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 1 \\
0 & 0 & 0 & 0
\end{pmatrix}.
$$

De aquí resulta que:

$$
B_U = \{(1,0,0,1), (0,1,1,1)\}.
$$

En cuanto a $W$, su dimensión es $4-2=2$. Tomando valores particulares, obtenemos:

$$
B_W = \{(1,0,1,1), (0,1,1,1)\}.
$$

Unimos estas bases para formar un sistema de generadores de $U+W$:

$$
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 1 \\
1 & 0 & 1 & 1 \\
0 & 1 & 1 & 1
\end{pmatrix}
\overset{E_{31}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 1 \\
0 & 0 & 1 & 0 \\
0 & 1 & 1 & 1
\end{pmatrix}
\overset{E_{42}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 1 & 1 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
\overset{E_{23}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 0 & 1 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}.
$$

Así, una base de $U+W$ es:

$$
B_{U+W} = \{(1,0,0,1), (0,1,0,1), (0,0,1,0)\}.
$$

A partir de esta base, escribimos las ecuaciones paramétricas:

$$
x=a, \quad y=b, \quad z=c, \quad t=a+b.
$$

De aquí resulta la ecuación cartesiana:

$$
t = x+y \quad \Longleftrightarrow \quad x+y+t=0 \quad \text{en } \mathbb{Z}_2.
$$

::::
:::::

::::: {#exr-30 .basico-cuerpo_finito} 

Sean $U$ y $W$ los siguientes subespacios de $(\mathbb{Z}_3)^3$:
$$
U = L\{(1,2,1), (1,0,2)\}, 
\quad
W \equiv
\begin{cases}
2y+z=0 \\
x+y+2z=0
\end{cases}
$$

<ol type='a'>
<li> Calcula las ecuaciones cartesianas de $U$.</li>
<li> Calcula las ecuaciones cartesianas de $U+W$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Vamos a obtener una base de $U$ lo más sencilla posible. Partimos de la matriz:
$$
\begin{pmatrix}
1 & 2 & 1 \\
1 & 0 & 2
\end{pmatrix}
\overset{E_{21}(2)}{\longrightarrow}
\begin{pmatrix}
1 & 2 & 1 \\
0 & 1 & 1
\end{pmatrix}
\overset{E_{12}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 2 \\
0 & 1 & 1
\end{pmatrix}
$$

De aquí se obtiene que
$$
B_U = \{(1,0,2), (0,1,1)\}
$$
es una base de $U$. (También lo es $\{(1,2,1), (1,0,2)\}$, pero la elegida simplifica los cálculos).

Un vector $(x,y,z)$ pertenece a $U$ si:
$$
(x,y,z) = a(1,0,2) + b(0,1,1) \implies 
\begin{cases}
x = a \\
y = b \\
z = 2a+b
\end{cases}
$$
Por tanto, $z = 2x+y$. Es decir, $U$ queda definido por la ecuación cartesiana:
$$
x + 2y + z = 0 \quad \text{en } \mathbb{Z}_3.
$$

</li>
<li>Calculamos $U+W$. Como $W$ está definido por dos ecuaciones, su dimensión es $3-2=1$, por lo que una base de $W$ está formada por un vector.

Resolvemos el sistema:
$$
\begin{cases}
2y+z=0 \\
x+y+2z=0
\end{cases}
\quad \Longleftrightarrow \quad
\begin{pmatrix}
0 & 2 & 1 \\
1 & 1 & 2
\end{pmatrix}
\overset{E_{12}(1)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 \\
1 & 1 & 2
\end{pmatrix}
\overset{E_{21}(2)}{\longrightarrow}
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 2
\end{pmatrix}
$$

De aquí se deduce:
$$
W \equiv \{x=0, \; y+2z=0\}.
$$
Tomando $z=1$, se obtiene el vector $(0,1,1)$, por lo que:
$$
B_W = \{(0,1,1)\}.
$$

Como $(0,1,1) \in U$, se concluye que $W \subseteq U$. Entonces:
$$
U+W = U,
$$
y por tanto,
$$
U+W \equiv x+2y+z=0.
$$

</li>
</ol>

::::
:::::

::::: {#exr-31 .basico-cuerpo_finito} 

Sean 
$$
X_1 = \{(1,3,2), (3,4,3)\}, \quad 
X_2 = \{(1,1,3), (2,1,2), (3,1,1), (0,1,2)\}
$$
dos subconjuntos de $(\mathbb{Z}_5)^3$.

<ol type='a'>
<li> Comprueba que los vectores de $X_1$ son linealmente independientes y amplía este conjunto a una base de $(\mathbb{Z}_5)^3$ (llámala $B_1$).</li>
<li> Comprueba que los vectores de $X_2$ forman un sistema de generadores de $(\mathbb{Z}_5)^3$. Toma una base contenida en $X_2$ (llámala $B_2$).</li>
<li> Calcula la matriz del cambio de base de $B_1$ a $B_2$.</li>
<li> Sea $u$ el vector cuyas coordenadas en $B_1$ son $(1,1,1)$. ¿Cuál es $u$? ¿Cuáles son sus coordenadas en $B_2$?</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Para comprobar si los vectores de $X_1$ son linealmente independientes, formamos la matriz:
$$
\begin{pmatrix}
1 & 3 & 2 \\
3 & 4 & 3
\end{pmatrix}
$$
y verificamos que su rango coincide con el número de vectores.
$$
\det \begin{pmatrix}
3 & 2 \\ 4 & 3
\end{pmatrix}
= 9 - 8 = 1 \neq 0
$$
Por tanto, son linealmente independientes. Ampliamos con $(1,0,0)$:
$$
B_1 = \{(1,3,2), (3,4,3), (1,0,0)\}.
$$

</li>
<li>Consideramos la matriz con los vectores de $X_2$ como columnas:
$$
\begin{pmatrix}
1 & 2 & 3 & 0 \\
1 & 1 & 1 & 1 \\
3 & 2 & 1 & 2
\end{pmatrix}
$$
y tras operaciones elementales se obtiene rango 3. Así, $X_2$ es un sistema de generadores. Eliminando $(3,1,1)$ (que es combinación de los demás), obtenemos:
$$
B_2 = \{(1,1,3), (2,1,2), (0,1,2)\}.
$$

</li>
<li>La matriz de cambio de base es:
$$
M_{B_1 \to B_2} = 
\begin{pmatrix}
1 & 0 & 0 \\
0 & 4 & 3 \\
2 & 0 & 2
\end{pmatrix}.
$$

</li>
<li>El vector
$$
u = 1(1,3,2) + 1(3,4,3) + 1(1,0,0) = (0,2,0).
$$
Sus coordenadas en $B_2$ se obtienen:
$$
M_{B_1 \to B_2} \cdot 
\begin{pmatrix}
1 \\ 1 \\ 1
\end{pmatrix}
=
\begin{pmatrix}
1 \\ 2 \\ 4
\end{pmatrix}.
$$
Por tanto, en $B_2$ el vector $u$ tiene coordenadas $(1,2,4)$.

</li>
</ol>

::::
:::::

::::: {#exr-32 .basico-cuerpo_finito} 

Sean 
$$
B_1 = \{(2,3,4),\,(3,3,0),\,(2,4,0)\}, 
\quad 
B_2 = \{(1,1,1),\,(0,2,1),\,(3,1,4)\}
$$
dos bases de $(\mathbb{Z}_5)^3$.  

Calcula la matriz del cambio de base de $B_1$ a $B_2$.

:::: {.callout collapse="true" title="Solución"}

Sabemos que
$$
M_{B_1 \to B_2} = M_{B_c \to B_2}\, M_{B_1 \to B_c}.
$$

$$
M_{B_1 \to B_c} =
\begin{pmatrix}
2 & 3 & 2 \\
3 & 3 & 4 \\
4 & 0 & 0
\end{pmatrix},
\qquad
M_{B_c \to B_2} = (M_{B_2 \to B_c})^{-1} =
\begin{pmatrix}
1 & 0 & 3 \\
1 & 2 & 1 \\
1 & 1 & 4
\end{pmatrix}^{-1}
=
\begin{pmatrix}
3 & 2 & 1 \\
3 & 4 & 3 \\
1 & 1 & 3
\end{pmatrix}.
$$

Por tanto:
$$
M_{B_1 \to B_2} =
\begin{pmatrix}
3 & 2 & 1 \\
3 & 4 & 3 \\
1 & 1 & 3
\end{pmatrix}
\begin{pmatrix}
2 & 3 & 2 \\
3 & 3 & 4 \\
4 & 0 & 0
\end{pmatrix}
=
\begin{pmatrix}
1 & 0 & 4 \\
0 & 1 & 2 \\
2 & 1 & 1
\end{pmatrix}.
$$

<b> Otra forma de resolverlo</b>

Podemos calcular directamente las coordenadas de los vectores de $B_1$ en la base $B_2$.

$$
(2,3,4) = a(1,1,1) + b(0,2,1) + c(3,1,4).
$$
Resolviendo:
$$
\begin{cases}
a + 3c = 2, \\
a + 2b + c = 3, \\
a + b + 4c = 4,
\end{cases}
\quad \Rightarrow \quad a=1,\; b=0,\; c=2.
$$

Así, la primera columna de $M_{B_1 \to B_2}$ es $(1,0,2)^T$.  

De manera análoga, para $(3,3,0)$:
$$
(3,3,0) = a'(1,1,1) + b'(0,2,1) + c'(3,1,4),
$$
cuyo sistema
$$
\begin{cases}
a' + 3c' = 3, \\
a' + 2b' + c' = 3, \\
a' + b' + 4c' = 0
\end{cases}
$$
tiene solución $a'=0,\, b'=1,\, c'=1$.

Para $(2,4,0)$:
$$
(2,4,0) = a''(1,1,1) + b''(0,2,1) + c''(3,1,4),
$$
cuyo sistema
$$
\begin{cases}
a'' + 3c'' = 2, \\
a'' + 2b'' + c'' = 4, \\
a'' + b'' + 4c'' = 0
\end{cases}
$$
tiene solución $a''=4,\, b''=2,\, c''=1$.

Por tanto:
$$
M_{B_1 \to B_2} =
\begin{pmatrix}
1 & 0 & 4 \\
0 & 1 & 2 \\
2 & 1 & 1
\end{pmatrix}.
$$

::::
:::::

::::: {#exr-33 .basico} 

Sea $B=\{(1,1,-2) ;(3,1,2) ;(4,2,-1)\}$ un subconjunto de $\mathbb{Q}^{3}$ y sea $B_{c}$ la base canónica de dicho espacio vectorial.

<ol type='a'>
<li> Comprueba que B es una base.</li>
<li> Calcula las matrices del cambio de base de B a $\mathrm{B}_{\mathrm{c}}$ y de $\mathrm{B}_{\mathrm{c}}$ a B .</li>
<li> Calcula las coordenadas del vector $v=(3,-1,2)$ en la base $B$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Puesto que tenemos tres vectores en un espacio de dimensión 3 , lo que tenemos es que comprobar que estos tres vectores son linealmente independiente. Para esto, formamos una matriz con estos 3 vectores y comprobamos que su rango es igual a 3 . Esto lo comprobaremos calculando su determinante y viendo que es distinto de cero. Escribiremos los vectores por columnas.

$$
A=\left(\begin{array}{rrr}
1 & 3 & 4 \\
1 & 1 & 2 \\
-2 & 2 & -1
\end{array}\right)
$$

Su determinante vale:

$$
\operatorname{det}(A)=1 \cdot 1 \cdot(-1)+1 \cdot 2 \cdot 4+3 \cdot 2 \cdot(-2)-4 \cdot 1 \cdot(-2)-3 \cdot 1 \cdot(-1)-2 \cdot 2 \cdot 1=-1+8-12+8+3-4=2 \neq 0
$$

Al ser el determinante distinto de cero, el rango de $A$ vale 3 , luego los vectores de $B$ forman una base de $\mathbb{Q}^{3}$.

</li>
<li>Comenzamos con la matriz del cambio de base de B a $\mathrm{B}_{\mathrm{c}}$. Esta matriz es fácil de calcular, pues sus columnas son las coordenadas de los vectores de $B$ en la base canónica. Pero eso es justamente la matriz $A$ que hemos estudiado en el apartado anterior. Por tanto:

$$
M_{B \rightarrow B_{c}}=A
$$

La otra matriz que nos piden es la del cambio inverso. Esta matriz será entonces la inversa de $A$. Calculamos entonces $A^{-1}$.

$$
\left(\begin{array}{rrr|rrr}
1 & 3 & 4 & 1 & 0 & 0 \\
1 & 1 & 2 & 0 & 1 & 0 \\
-2 & 2 & -1 & 0 & 0 & 1
\end{array}\right) \xrightarrow{\mathrm{E}_{21}(-1)} \xrightarrow{\mathrm{E}_{31}(2)}\left(\begin{array}{rrr|rrr}
1 & 3 & 4 & 1 & 0 & 0 \\
0 & -2 & -2 & -1 & 1 & 0 \\
0 & 8 & 7 & 2 & 0 & 1
\end{array}\right) \xrightarrow{\mathrm{E}_{2}\left(\frac{-1}{2}\right)}\left(\begin{array}{lll|lll}
1 & 3 & 4 & 1 & 0 & 0 \\
0 & 1 & 1 & \frac{1}{2} & \frac{-1}{2} & 0 \\
0 & 8 & 7 & 2 & 0 & 1
\end{array}\right) \\
$$

$$
\xrightarrow{\mathrm{E}_{12}(-3)}\left(\begin{array}{ccc|ccc}
1 & 0 & 1 & \frac{-1}{2} & \frac{3}{2} & 0 \\
0 & 1 & 1 & \frac{1}{2} & \frac{-1}{2} & 0 \\
0 & 0 & -1 & -2 & 4 & 1
\end{array}\right) \xrightarrow{\mathrm{E}_{3(-1)}}\left(\begin{array}{ccc|ccc}
1 & 0 & 1 & \frac{-1}{2} & \frac{3}{2} & 0 \\
0 & 1 & 1 & \frac{1}{2} & \frac{-1}{2} & 0 \\
0 & 0 & 1 & 2 & -4 & -1
\end{array}\right) 
$$

$$
\xrightarrow{\mathrm{E}_{13}(-1)} \xrightarrow{\mathrm{E}_{23}(-1)}\left(\begin{array}{ccc|ccc}
1 & 0 & 0 & \frac{-5}{2} & \frac{11}{2} & 1 \\
0 & 1 & 0 & \frac{-3}{2} & \frac{7}{2} & 1 \\
0 & 0 & 1 & 2 & -4 & -1
\end{array}\right)
$$

Es decir:

$$
M_{B_{c} \rightarrow B}=A^{-1}=\left(\begin{array}{ccc}
\frac{-5}{2} & \frac{11}{2} & 1 \\
\frac{-3}{2} & \frac{7}{2} & 1 \\
2 & -4 & -1
\end{array}\right)=\frac{1}{2} \cdot\left(\begin{array}{rrr}
-5 & 11 & 2 \\
-3 & 7 & 2 \\
4 & -8 & -2
\end{array}\right)
$$

</li>
<li>Puesto que las coordenadas de $v$ en la base canónica son ( $3,-1,2$ ), para calcular sus coordenadas en $B$ únicamente hemos de multiplicar estas coordenadas por la matriz del cambio de base:

$$
(v)_{\mathrm{B}}=\mathrm{M}_{\mathrm{B}_{\mathrm{c}} \rightarrow \mathrm{~B}} \cdot(v)_{\mathrm{B}_{\mathrm{c}}}=\frac{1}{2} \cdot\left(\begin{array}{rrr}
-5 & 11 & 2 \\
-3 & 7 & 2 \\
4 & -8 & -2
\end{array}\right) \cdot\left(\begin{array}{r}
3 \\
-1 \\
2
\end{array}\right)=\frac{1}{2}\left(\begin{array}{r}
-22 \\
-12 \\
16
\end{array}\right)=\left(\begin{array}{r}
-11 \\
-6 \\
8
\end{array}\right)
$$

Es decir, las coordenadas de $v$ en la base $B$ son $(-11,-6,8)$, como podemos comprobar fácilmente:

$$
-11 \cdot(1,1,-2)-6 \cdot(3,1,2)+8 \cdot(4,2,-1)=(-11,-11,22)+(-18,-6,-12)+(32,16,-8)=(3,-1,2)=v
$$

</li>
</ol>

::::
:::::

::::: {#exr-34 .medio-cuerpo_finito} 

Sean $B_1 = \{(1,0,-1),\ (2,1,1),\ (0,1,1)\}$ un subconjunto de ${\mathbb Q}^3$ y sea $A = \left (\begin{array}{ccc} 1 & 1 & 1 \\ 1 & 2 & 2 \\ 1 & 2 & 3 \end{array}\right )\in M_3({\mathbb Q})$.

<ol type='a'>
<li> Comprueba que $B_1$ es una base de ${\mathbb Q}^3$ y que la matriz $A$ es regular.</li>
<li> Sea $B_2$ la base de ${\mathbb Q}^3$ para la que la matriz del cambio de base $B_1$ a $B_2$ es $A$. Calcula la base $B_2$.</li>
<li> Sea $u$ el vector cuyas coordenadas en $B_1$ son $(1,1,1)$. Calcula el vector $u$ y sus coordenadas en $B_2$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Para que $B_1$ sea una base, los vectores tienen que ser linealmente independientes, y para ello, el rango de la matriz $C =\left  (\begin{array}{rrr} 1 & 0 & -1 \\ 2 & 1 & 1 \\ 0 & 1 & 1 \end{array}\right )$ debe ser igual a $3$. Calculamos su determinante:

$$
\text{det}(C) = 1 + (-2) + 0 - 0 - 1 = -2 \neq 0.
$$

Lo que nos dice que el rango de $C$ es igual a $3$ y por tanto, $B_1$ es una base.

Para ver si la matriz $A$ es regular calculamos su determinante, y este vale $6 + 2 + 2 - 2 - 3 - 4 = 1 \neq 0$, por lo que la matriz $A$ es regular.

</li>
<li>Vamos a calcular $M_{B_2\rightarrow B_c}$, donde $B_c$ es la base canónica de ${\mathbb Q}^3$. Las columnas de esta matriz serán los vectores de $B_2$ (para ser más precisos, serán las coordenadas de los vectores de $B_2$ en la base canónica).


Se tiene que $M_{B_2 \rightarrow B_c} = M_{B_1\rightarrow B_c} \cdot M_{B_2\rightarrow B_1} =  M_{B_1\rightarrow B_c} \cdot
(M_{B_1\rightarrow B_2})^{-1}$.



Calculamos entonces $A^{-1}$.


$$
\begin{array}{l}
\qquad \quad\left (\begin{array}{rrrrrr}
1 & 1 & 1 & 1 & 0 & 0 \\ 1 & 2 & 2 & 0 & 1 & 0 \\ 1 & 2 & 3 & 0 & 0 & 1 \end{array}\right ) \stackrel{E_{21}(-1)}{\stackrel{E_{31}(-1)}{\longrightarrow}}
\left (\begin{array}{rrrrrr}
1 & 1 & 1 & 1 & 0 & 0 \\ 0 & 1 & 1 & -1 & 1 & 0 \\ 0 & 1 & 2 & -1 & 0 & 1 \end{array}\right ) \stackrel{E_{12}(-1)}{\stackrel{E_{32}(-1)}{\longrightarrow}} \\
\stackrel{E_{12}(-1)}{\stackrel{E_{32}(-1)}{\longrightarrow}} \left (\begin{array}{rrrrrr}
1 & 0 & 0 & 2 & -1 & 0 \\ 0 & 1 & 1 & -1 & 1 & 0 \\ 0 & 0 & 1 & 0 & -1 & 1 \end{array}\right ) \stackrel{E_{23}(-1)}{\longrightarrow}
\left (\begin{array}{rrrrrr}
1 & 0 & 0 & 2 & -1 & 0 \\ 0 & 1 & 0 & -1 & 2 & -1 \\ 0 & 0 & 1 & 0 & -1 & 1 \end{array}\right )
\end{array}$$


Y con esto, ya podemos calcular la matriz que nos piden:
$$
M_{B_2\rightarrow B_c} = \left (\begin{array}{rrr} 1 & 2 & 0 \\ 0 & 1 & 1 \\ -1 & 1 & 1 \end{array} \right ) \cdot \left  (\begin{array}{rrr} 2 & -1 & 0 \\ -1 & 2 & -1 \\ 0 & -1 & 1 \end{array}\right ) = \left (\begin{array}{rrr} 0 & 3 & -2 \\ -1 & 1 & 0 \\ -3 & 2 & 0 \end{array}\right ).$$


Por lo que $B_2 = \{(0,-1,-3),\ (3,1,2),\ (-2,0,0)\}$.


También se podría haber obtenido $B_2$ de la siguiente forma.

Sean ${\mathbf u}$, ${\mathbf v}$ y ${\mathbf w}$ los vectores de $B_2$. Del hecho de que $M_{B_1 \rightarrow B_2}=A$ sacamos que:

<ul>
<li> ${\mathbf u} + {\mathbf v} + {\mathbf w} = (1,0,-1)$ (pues las coordenadas del primer vector de $B_1$ en $B_2$ son $(1,1,1)$).</li>
<li> ${\mathbf u} + 2{\mathbf v} + 2{\mathbf w} = (2,1,1)$ (pues las coordenadas del segundo vector de $B_1$ en $B_2$ son $(1,2,2)$).</li>
<li> ${\mathbf u} + 2{\mathbf v} + 3{\mathbf w} = (0,1,1)$ (pues las coordenadas del tercer vector de $B_1$ en $B_2$ son $(1,2,3)$). </li>
</ul>

De aquí obtenemos que ${\mathbf w} = ({\mathbf u} + 2{\mathbf v} + 3{\mathbf w}) - ({\mathbf u} + 2{\mathbf v} + 2{\mathbf w}) = (0,1,1) - (2,1,1) = (-2,0,0)$.

También que ${\mathbf v} + {\mathbf w} = ({\mathbf u} + 2{\mathbf v} + 2{\mathbf w}) - ({\mathbf u} + {\mathbf v} + {\mathbf w}) = (2,1,1) - (1,0,-1) = (1,1,2)$.

Ahora, vemos que ${\mathbf v} = ({\mathbf v} + {\mathbf w}) - {\mathbf w} = (1,1,2) - (-2,0,0) = (3,1,2)$.

Y por último, ${\mathbf u} = ({\mathbf u} + {\mathbf v} + {\mathbf w}) - ({\mathbf v} + {\mathbf w}) = (1,0,-1) - (1,1,2) = (0,-1,-3)$.

</li>
<li>Dado que $u$ tiene coordenadas $(1,1,1)$ en $B_1$, se tiene que $u$ es la suma de los tres vectores de la base $B_1$, es decir, $u=(3,2,1)$.

Y puesto que tenemos la matriz del cambio de base de $B_1$ a $B_2$ (que es $A$) , solo hay que multiplicar esta matriz por las coordenadas del vector en $B_1$.

$$
(u)_{B_2} = M_{B_1\rightarrow B_2} \cdot (u)_{B_1} = \left (\begin{array}{rrr} 1 & 1 & 1 \\ 1 & 2 & 2 \\ 1 & 2 & 3 \end{array}\right ) \cdot \left (\begin{array}{r} 1 \\ 1 \\ 1 \end{array}\right ) = \left (\begin{array}{r} 3 \\ 5 \\ 6 \end{array}\right ).
$$

</li>
</ol>

::::
:::::

::::: {#exr-35 .medio-cuerpo_finito} 

Sea $A=\left (\begin{array}{ccc} 1 & 0 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{array}\right )\in M_3({\mathbb Z}_2)$ y sea $B_1=\{(1,1,0),\ (0,1,1), (1,1,1)\}$ un subconjunto de $({\mathbb Z}_2)^3$.


<ol type='a'>
<li> Comprueba que $B_1$ es una base de $({\mathbb Z}_2)^3$.</li>
<li> Sea $B_2$ una base tal que $M_{B_2\rightarrow B_1} = A$. Calcula la base $B_2$.</li>
<li> Calcula la matriz del cambio de base de $B_c$ a $B_1$, donde $B_c$ es la base canónica de $({\mathbb Z}_2)^3$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Para comprobar que $B_1$ es una base, formamos una matriz cuyas columnas (o filas) son las coordenadas de los vectores de $B_1$ en $B_c$ y calculamos el rango. Si el rango es $3$, $B_1$ será una base.

$$
C = \left (\begin{array}{ccc} 1 & 0 & 1 \\ 1 & 1 & 1 \\ 0 & 1 & 1 \end{array}\right );\ 
\text{rg}(C) = 3 \text{ pues } \text{det}(C) = 1 + 1 + 0 - 0 - 0 - 1 = 1\neq 0.
$$

</li>
<li>Calculamos $M_{B_2\rightarrow B_c}$. Sabemos que $M_{B_2\rightarrow B_c} = M_{B_1\rightarrow B_c}\cdot M_{B_2\rightarrow B_1} = C\cdot A$. Multiplicamos ambas matrices:
$$
M_{B_2\rightarrow B_c} = C\cdot A = \left (\begin{array}{ccc} 1 & 0 & 1 \\ 1 & 1 & 1 \\ 0 & 1 & 1 \end{array}\right )\cdot \left (\begin{array}{ccc} 1 & 0 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 1 \end{array}\right ) = \left (\begin{array}{ccc} 1 & 1 & 0 \\ 0 & 1 & 0 \\ 1 & 1 & 1 \end{array}\right ).$$

Los vectores de $B_2$ son las columnas de esta matriz. Es decir:
$$
B_2 = \{(1,0,1),\ (1,1,1),\ (0,0,1)\}.$$

También podríamos haber calculado $B_2$ como sigue:
Supongamos que $B_2=\{v_1,\ v_2,\ v_3\}$, y llamemos $u_1,u_2,u_3$ a los tres vectores de $B_1$. Entonces, el que la matriz de cambio de base de $B_2$ a $B_1$ nos dice que:

<ul>
<li> $v_1 = 1\cdot u_1 + 1\cdot u_2 + 0\cdot u_3 = (1,1,0) + (0,1,1) = (1,0,1)$. </li>
<li> $v_2 = 0\cdot u_1 + 0\cdot u_2 + 1\cdot u_3 = (1,1,1)$. </li>
<li> $v_3 = 1\cdot u_1 + 0\cdot u_2 + 1\cdot u_3 = (1,1,0) + (1,1,1) = (0,0,1)$. </li>
</ul>

Como vemos, coinciden.

</li>
<li>Tenemos que $M_{B_c\rightarrow B_1} = (M_{B_1\rightarrow B_c})^{-1} = C^{-1}$. Realizamos el cálculo:

$$\left (\begin{array}{ccc|ccc} 1 & 0 & 1 & 1 & 0 & 0 \\ 1 & 1 & 1 & 0 & 1 & 0 \\ 0 & 1 & 1 & 0 & 0 & 1 \end{array}\right ) \stackrel{E_{21}(1)}{\longrightarrow}
\left (\begin{array}{ccc|ccc} 1 & 0 & 1 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 1 & 0 \\ 0 & 1 & 1 & 0 & 0 & 1 \end{array}\right ) \stackrel{E_{32}(1)}{\longrightarrow}
\left (\begin{array}{ccc|ccc} 1 & 0 & 1 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 1 & 0 \\ 0 & 0 & 1 & 1 & 1 & 1 \end{array}\right ) \stackrel{E_{13}(1)}{\longrightarrow}
\left (\begin{array}{ccc|ccc} 1 & 0 & 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 & 1 & 0 \\ 0 & 0 & 1 & 1 & 1 & 1 \end{array}\right )$$

Luego $M_{B_c\rightarrow B_1} = \left (\begin{array}{ccc} 0 & 1 & 1 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \end{array}\right ).$

</li>
</ol>

::::
:::::

::::: {#exr-36 .basico-cuerpo_finito} 

En el espacio vectorial ( $\left.\mathbb{Z}_{5}\right)^{4}$ consideramos los subespacios vectoriales

$$
\begin{aligned}
U & =\langle(0,1,1,1),(2,0,2,0)\rangle=L[(0,1,1,1),(2,0,2,0)] \\
W & \equiv\left\{\begin{array}{c}
x+y+z+t=0 \\
2 x+y+2 t=0
\end{array}\right.
\end{aligned}
$$

Calcula unas ecuaciones cartesianas de $U+W$ y comprueba si $(1,2,2,2) \in U+W$.


:::: {.callout collapse="true" title="Solución"}

Puesto que nos piden calcular la suma de los subespacios necesitamos una base de cada uno de ellos (con un sistema de generadores bastaría). Una base de $U$ la tenemos, pues nos la da el enunciado. Dicha base es $B_{U}=\{(0,1,1,1) ;(2,0,2,0)\}$.

Calculamos entonces una base de $W$. Como tenemos las ecuaciones cartesianas, resolvemos el sistema que nos define $W$ :

$$
\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
2 & 1 & 0 & 2
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
0 & 4 & 3 & 0
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
0 & 1 & 2 & 0
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 0 & 4 & 1 \\
0 & 1 & 2 & 0
\end{array}\right)
$$

Es decir,

$$
W \equiv\left\{\begin{array} { r l } 
{ x } & { + 4 z + t = 0 } \\
{ } & { y + 2 z }
\end{array} \text { es decir, } W \equiv \left\{\begin{array}{rl}
x & =z+4 t \\
y & =3 z
\end{array}\right.\right.
$$

Dándole a $z$ y a $t$ los valores 10 y 0,1 obtenemos una base de $W: B_{W}=\{(1,3,1,0) ;(4,0,0,1)\}$.\\
Si ahora unimos las dos bases lo que obtenemos es un sistema de generadores de $U+W$. A partir de ellos vamos a obtener una base:

$$
\left(\begin{array}{llll}
0 & 1 & 1 & 1 \\
2 & 0 & 2 & 0 \\
1 & 3 & 1 & 0 \\
4 & 0 & 0 & 1
\end{array}\right) \xrightarrow{E_{13}}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
2 & 0 & 2 & 0 \\
0 & 1 & 1 & 1 \\
4 & 0 & 0 & 1
\end{array}\right) \xrightarrow{E_{21}(3)}{ }^{E_{14}(1)}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
0 & 4 & 0 & 0 \\
0 & 1 & 1 & 1 \\
0 & 3 & 1 & 1
\end{array}\right) \xrightarrow{E_{2(4)}}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 1 & 1 & 1 \\
0 & 3 & 1 & 1
\end{array}\right) $$
$$
\xrightarrow{\substack{E_{12}(2) \\
E_{32}(4) \\
E_{42}(2)}}\left(\begin{array}{llll}
1 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 1 \\
0 & 0 & 1 & 1
\end{array}\right) \xrightarrow{E_{13}(4)}\left(\begin{array}{llll}
1 & 0 & 0 & 4 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 1 \\
0 & 0 & 0 & 0
\end{array}\right)
$$

Y por tanto vemos que una base de $U+W$ es $B_{U+W}=\{(1,0,0,4) ;(0,1,0,0) ;(0,0,1,1)\}$.\\
Puesto que $\operatorname{dim}(U+W)=3$ y $U+W$ es subespacio de $\left(\mathbb{Z}_{5}\right)^{4}$, el subespacio $U+W$ viene dado por $4-3=1$ ecuación cartesiana. Para calcularla escribimos las ecuaciones paramétricas, y esto lo hacemos teniendo en cuenta que un vector $(x, y, z, t) \in U+W$ si, y sólo si, es combinación lineal de los vectores de la base. Por tanto, deben poder expresarse de la forma:

$$
(x, y, z, t)=a(1,0,0,4)+b(0,1,0,0)+c(0,0,1,1)
$$

o lo que es lo mismo:

$$
\begin{aligned}
x & =a \\
y & = b\\
z & =c \\
t & =4a+c
\end{aligned}
$$

Y aquí vemos que si $(x, y, z, t) \in U+W$ se tiene que $t=4 x+z$. Por tanto, $U+W \equiv x+4 z+t=0$. Y ya tenemos las ecuaciones cartesianas de $U+W$ (en este caso, la ecuación cartesiana).

Para comprobar si $(1,2,2,2) \in U+W$ basta comprobar si satisface la ecuación. Puesto que $1+4 \cdot 2+2=1 \neq 0$ dicho vector no pertenece a $U+W$.

::::
:::::

::::: {#exr-37 .basico} 

Sean $B_1 = \{(1,0,-1),\ (2,1,1),\ (0,1,1)\}$ y $B_2 = \{(1,0,1),\ (0,1,-1),\ (1,1,1)\}$ dos subconjuntos de ${\mathbb Q}^3$.


<ol type='a'>
<li> Comprueba que $B_1$ y $B_2$ son bases de ${\mathbb Q}^3$.</li>
<li> Calcula la matriz del cambio de base de $B_1$ a $B_2$.</li>
<li> Sea $u$ el vector cuyas coordenadas en $B_1$ son $(1,1,1)$. Calcula el vector $u$ y sus coordenadas en $B_2$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Para que $B_1$ sea una base de ${\mathbb Q}^3$ basta con que los tres vectores de $B_1$ sean linealmente independientes. Y para esto, basta ver que el rango de una matriz cuyas filas (o columnas) sean las coordenadas de estos vectores es igual a $3$. Formamos esa matriz

$$
\left (\begin{array}{rrr} 1 & 0 & -1 \\ 2 & 1 & 1 \\ 0 & 1 & 1 \end{array}\right )$$

Y vemos que su rango es igual a $3$, ya que su determinante es igual a $1-2+0-0-0-1=-2$, que es distitno de cero.

Para $B_2$ procedemos de igual forma:

$\text{det}\left (\begin{array}{rrr} 1 & 0 & 1 \\ 0 & 1 & -1 \\ 1 & 1 & 1 \end{array}\right ) = \text{det}\left (\begin{array}{rrr} 1 & 0 & 1 \\ 0 & 1 & -1 \\ 0 & 1 & 0 \end{array}\right ) = -\text{det}\left (\begin{array}{rr} 1 & 1 \\ 0 & -1 \end{array}\right ) = - (-1) = 1 \neq 0.$

</li>
<li>La matriz del cambio de base de $B_1$ a $B_2$ la podemos calcular como sigue:



$M_{B_1\rightarrow B_2} = M_{B_c\rightarrow B_2}\cdot M_{B_1\rightarrow B_c} = \left (M_{B_2\rightarrow B_c}\right )^{-1}\cdot M_{B_1\rightarrow B_c} =\left (\begin{array}{rrr} 1 & 0 & 1 \\ 0 & 1 & 1 \\ 1 & -1 & 1 \end{array}\right )^{-1} \cdot  \left (\begin{array}{rrr} 1 & 2 & 0 \\ 0 & 1 & 1 \\ -1 & 1 & 1 \end{array}\right )$



Para calcular esta matriz tenemos en cuenta que si $A$ y $C$ son dos matrices (con el mismo número de filas) y $A$ es regular, entonces si partimos de la matriz $(A|C)$, su forma escalonada reducida por filas es $(Id|A^{-1}\cdot C)$.



$$\begin{array}{l}
\quad \left ( \begin{array}{rrr|rrr} 1 & 0 & 1 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 1 & 1 \\ 1 & -1 & 1 & -1 & 1 & 1 \end{array}\right ) \stackrel{E_{31}(-1)}{\longrightarrow} \left ( \begin{array}{rrr|rrr} 1 & 0 & 1 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 1 & 1 \\ 0 & -1 & 0 & -2 & -1 & 1 \end{array}\right ) \\
\ \ \   \stackrel{E_{32}(1)}{\longrightarrow} \left ( \begin{array}{rrr|rrr} 1 & 0 & 1 & 1 & 2 & 0 \\ 0 & 1 & 1 & 0 & 1 & 1 \\ 0 & 0 & 1 & -2 & 0 & 2 \end{array}\right ) \stackrel{E_{13}(-1)}{\stackrel{E_{23}(-1)}{\longrightarrow}} \left ( \begin{array}{rrr|rrr} 1 & 0 & 0 & 3 & 2 & -2 \\ 0 & 1 & 0 & 2 & 1 & -1 \\ 0 & 0 & 1 & -2 & 0 & 2 \end{array}\right )
\end{array}$$


Así que $M_{B_1\rightarrow B_2} = \left (\begin{array}{rrr} 3 & 2 & -2 \\ 2 & 1 & -1 \\ -2 & 0 & 2 \end{array}\right )$.

También se podría haber calculado la inversa de $\left (\begin{array}{rrr} 1 & 0 & 1 \\ 0 & 1 & 1 \\ 1 & -1 & 1 \end{array}\right )$, que es igual a $\left (\begin{array}{rrr} 2 & -1 & -1 \\ 1 & 0 & -1 \\ -1 & 1 & 1 \end{array}\right )$ y multiplicarla por $\left (\begin{array}{rrr} 1 & 2 & 0 \\ 0 & 1 & 1 \\ -1 & 1 & 1 \end{array}\right )$.


</li>
<li>Puesto que el vector $u$ tiene coordenadas $(1,1,1)$ en la base $B_1$ tenemos que

$$u = 1\cdot (1,0,-1) + 1\cdot (2,1,1) + 1\cdot (0,1,1) = (3,2,1).$$

Para calcular sus coordenadas en la base $B_2$ utilizamos la matriz del cambio de base de $B_1$ a $B_2$:

$$
(u)_{B_2} = M_{B_1\rightarrow B_2}\cdot (u)_{B_1} = \left (\begin{array}{rrr} 3 & 2 & -2 \\ 2 & 1 & -1 \\ -2 & 0 & 2 \end{array}\right ) \cdot \left ( \begin{array}{r} 1 \\ 1 \\ 1 \end{array} \right ) = \left (\begin{array}{r} 3 \\ 2 \\ 0 \end{array}\right ).$$

</li>
</ol>

::::
:::::

::::: {#exr-38 .medio} 

Sean $B_1 = \{(1,1),\ (2,1)\}$ y $B_2 = \{(-1,5),\ (0,3)\}$ dos subconjuntos de ${\mathbb R}^2$.


<ol type='a'>
<li> Comprueba que son bases de ${\mathbb R}^2$.</li>
<li> Sea ${\mathbf u}$ el vector cuyas coordenadas en $B_2$ son $(2,3)$. Di cuál es el vector ${\mathbf u}$ y sus coordenadas en $B_1$.</li>
<li> Calcula todos los vectores que tienen las mismas coordenadas en $B_1$ y en $B_2$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Puesto que $\text{rg}\left (\begin{array}{rr} 1 & 2 \\ 1 & 1 \end{array}\right )=2$ y $\text{rg}\left (\begin{array}{rr} -1 & 0 \\ 5 & 3 \end{array}\right )=2$ tenemos que cada uno de los conjuntos forman una base de ${\mathbb R}^2$.

</li>
<li>Puesto que ${\mathbf u}$ tiene coordenadas $(2,3)$ en $B_2$ significa que ${\mathbf u} = 2\cdot (-1,5) + 3\cdot (0,3) = (-2,19)$.

Calculamos ahora las coordendas de ${\mathbf u}$ en $B_1$. Para eso, escribimos $(-2,19) = a\cdot (1,1) + b\cdot (2,1)$, lo que nos da el sistema:

$$\begin{array}{rrrrr} a & + & 2b & = & -2 \\ a & + & b & = & 19 \end{array}$$

Que tiene como solución $a=40$, $b=-21$. Esas son las coordenadas de ${\mathbf u}$ en $B_1$.

Para este último cálculo podemos calcular la matriz del cambio de base de $B_2$ a $B_1$:

$M_{B_2\rightarrow B_1} = M_{B_c \rightarrow B_1}\cdot M_{B_2\rightarrow B_c} = \left (\begin{array}{rr} 1 & 2 \\ 1 & 1 \end{array}\right )^{-1} \left (\begin{array}{rr} -1 & 0 \\ 5 & 3 \end{array}\right ) = \left (\begin{array}{rr} -1 & 2 \\ 1 & -1 \end{array}\right ) \left (\begin{array}{rr} -1 & 0 \\ 5 & 3 \end{array}\right ) =  \left (\begin{array}{rr} 11 & 6 \\ -6 & -3 \end{array}\right )$

Y ahora:

$$({\mathbf u})_{B_1} = M_{B_2\rightarrow B_1} \cdot ({\mathbf u})_{B_2} = \left (\begin{array}{rr} 11 & 6 \\ -6 & -3 \end{array}\right ) \cdot \left (\begin{array}{r} 2  \\ 3 \end{array}\right ) =  \left (\begin{array}{r} 40  \\ -21 \end{array}\right )$$

</li>
<li>Sea ${\mathbf v}$ un vector que tiene coordenadas $(a,b)$ en la base $B_1$ y las mismas coordenadas en la base $B_2$. Entonces:

$${\mathbf v} = a\cdot (1,1) + b\cdot (2,1) = a \cdot (-1,5) + b\cdot (0,3) \Longrightarrow a \cdot ((1,1)-(-1,5)) + b\cdot ((2,1)-(0,3)) = (0,0) $$

Esto da lugar al siguiente sistema de ecuaciones:

$$\begin{array}{rrrrr} 2a & + & 2b & = & 0 \\ -4a & - & 2b & = & 0 \end{array}$$

cuya única solución es $a=0$, $b=0$.

Por consiguiente, solo hay un vector que tenga las mismas coordenadas en $B_1$ y en $B_2$, y este es el vector $(0,0)$.

También podríamos haber resuelto este punto como sigue:

Si ${\mathbf v}$ es un vector cuyas coordenadas en $B_1$ y en $B_2$ son $(a,b)$, entonces:

$$
\left (\begin{array}{rr} 11 & 6 \\ -6 & -3 \end{array}\right ) \cdot \left (\begin{array}{r} a  \\ b \end{array}\right ) =  \left (\begin{array}{r} a \\ b \end{array}\right ) \Longrightarrow \left (\begin{array}{rr} 10 & 6 \\ -6 & -4 \end{array}\right ) \cdot \left (\begin{array}{r} a  \\ b \end{array}\right ) =  \left (\begin{array}{r} 0 \\ 0 \end{array}\right )
$$

Y la única solución de este sistema de ecuaciones es $a=b=0$.

</li>
</ol>

::::
:::::

::::: {#exr-39 .basico-cuerpo_finito} 

Sea $U$ el subespacio de $(\mathbb{Z}_5)^4$ generado por los vectores del conjunto $\{(0,3,0,1),(2,3,1,1),(2,1,1,2)\}$ y sea $W$ el subespacio vectorial de $(\mathbb{Z}_5)^4$ de ecuaciones

$$
W\equiv\left\{\begin{array}{rrrrrrrrr}
x &+& 3y &+& z & &  &=& 0\\
x &+ & 4y &+& 4z &+ &t  &=& 0 \\
3x & &  &+& z &+ &t  &=& 0
\end{array}\right.
$$


<ol type='a'>
<li> Calcula unas ecuaciones cartesianas (implícitas) del subespacio $U+W$.</li>
<li> Calcula una base del subespacio intersección.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type='a'>
<li>Para calcular unas ecuaciones del subespacio suma, vamos, en primer lugar, a calcular una base de este subespacio. Para esto, vamos a tomar un sistema de generadores de $U$ (aunque en el enuciado nos da uno, y ese nos valdría, vamos a reducirlo), un sistema de generadores de $W$ (para lo que tendremos que resolver el sistema de ecuaciones que define a este subespacio), los uniremos (tendremos así un sistema de generadores de $U+W$) y a partir de él calcularemos una base de este subespacio vectorial.

<ol type='i'>
<li>Comenzamos calculando una base de $U$ (aunque este paso no es necesario).

$$
{
\left ( \begin{array}{rrrr} 0 & 3 & 0 & 1 \\ 2 & 3 & 1 & 1 \\ 2 & 1 & 1 & 2 \end{array}\right ) \stackrel{E_{12}(3)}{\longrightarrow} \left ( \begin{array}{rrrr} 1 & 2 & 3 & 4 \\ 2 & 3 & 1 & 1 \\ 2 & 1 & 1 & 2 \end{array}\right ) \stackrel{E_{21}(3)}{\stackrel{E_{31}(3)}{\longrightarrow}}
\left ( \begin{array}{rrrr} 1 & 2 & 3 & 4 \\ 0 & 4 & 0 & 3 \\ 0 & 2 & 0 & 4 \end{array}\right ) \stackrel{E_{2}(4)}{\longrightarrow}
\left ( \begin{array}{rrrr} 1 & 2 & 3 & 4 \\ 0 & 1 & 0 & 2 \\ 0 & 2 & 0 & 4 \end{array}\right )}
$$

$$
{ 
\stackrel{E_{12}(3)}{\stackrel{E_{32}(3)}{\longrightarrow}}
\left ( \begin{array}{rrrr} 1 & 0 & 3 & 0 \\ 0 & 1 & 0 & 2 \\ 0 & 0 & 0 & 0 \end{array}\right )}
$$

Y tenemos que $B_U = \{(1,0,3,0),\ (0,1,0,2)\}$ es una base del subespacio $U$.

</li>
<li>Calculamos una base de $W$ (para lo cual resolvemos el sistema de ecuaciones). Escribimos la matriz de coeficientes del sistema y calculamos su forma escalonada reducida:

$\left (\begin{array}{rrrr} 1 & 3 & 1 & 0 \\ 1 & 4 & 4 & 1 \\ 3 & 0 & 1 & 1 \end{array}\right )\stackrel{E_{21}(4)}{\stackrel{E_{31}(2)}{\longrightarrow}}
\left (\begin{array}{rrrr} 1 & 3 & 1 & 0 \\ 0 & 1 & 3 & 1 \\ 0 & 1 & 3 & 1 \end{array}\right )\stackrel{E_{12}(2)}{\stackrel{E_{32}(4)}{\longrightarrow}}
\left (\begin{array}{rrrr} 1 & 0 & 2 & 2 \\ 0 & 1 & 3 & 1 \\ 0 & 0 & 0 & 0 \end{array}\right )$

Así que $W\equiv\left\{\begin{array}{rrrrrrrrr}
x & &  &+& 2z & + & 2t  &=& 0\ \\
& & y &+& 3z &+ &t  &=& 0. 
\end{array}\right.$
Despejamos $x$ e $y$:

$$
W\equiv\left\{\begin{array}{rrrrr}
x & = & 3z  &+& 3t \\
y & = & 2z &+& 4t  
\end{array}\right.
$$

Puesto que $W$ viene dado por $2$ ecuaciones tenemos que $\text{dim}(W) = 4 - 2 = 2$, y para obtener una base le damos a $z$ y $t$ los valores $z=1,\ t=0$ y $z=0,\ t=1$. $B_{W} = \{(3,2,1,0),\ (3,4,0,1)\}$.

</li>
<li> Calculamos una base de $U+W$. Para esto, unimos las bases de $U$ y de $W$ y reducimos:

$U+W = L[(1,0,3,0),\ (0,1,0,2),\ (3,2,1,0),\ (3,4,0,1)]$. Formamos una matriz con estos cuatro vectores y calculamos su forma escalonada reducida.

$\left ( \begin{array}{rrrr} 1 & 0 & 3 & 0 \\ 0 & 1 & 0 & 2 \\ 3 & 4 & 0 & 1 \\ 3 & 2 & 1 & 0 \end{array} \right )
\stackrel{E_{31}(2)}{\stackrel{E_{41}(2)}{\longrightarrow}}
\left ( \begin{array}{rrrr} 1 & 0 & 3 & 0 \\ 0 & 1 & 0 & 2 \\ 0 & 4 & 1 & 1 \\ 0 & 2 & 2 & 0 \end{array} \right )
\stackrel{E_{32}(1)}{\stackrel{E_{42}(3)}{\longrightarrow}}
\left ( \begin{array}{rrrr} 1 & 0 & 3 & 0 \\ 0 & 1 & 0 & 2 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 2 & 1 \end{array} \right )
\stackrel{E_{13}(2)}{\stackrel{E_{43}(3)}{\longrightarrow}}
\left ( \begin{array}{rrrr} 1 & 0 & 0 & 1 \\ 0 & 1 & 0 & 2 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 0 & 0 \end{array} \right )$

Y ya tenemos una base de $U+W$: $B_{U+W} = \{(1,0,0,1),\ (0,1,0,2),\ (0,0,1,3)\}$.

Por consiguiente, $\text{dim}(U+W) = 3$.
</li>
<li>A partir de la base obtenida escribimos las ecuaciones paramétricas de $U+W$ y de ahí, las ecuaciones cartesianas. Al ser $U+W$ un subespacio de dimensión $3$ el número de ecuaciones cartesianas es igual a $4-3=1$.

Un vector $(x,y,z,t)$ pertenece a $U+W$ si es combinación lineal de los vectores de $B_{U+W}$, es decir, es de la forma $(x,y,z,t) = a(1,0,0,1) + b(0,1,0,2) + c(0,0,1,3)$.

$\left. \begin{array}{rrrrrrr}
x & = & a & & & & \\
y & = & & & b & & \\
z & = & & & & & c \\
t & = & a & + & 2b & + & 3c \end{array} \right\} \Longrightarrow U+W \equiv t = x + 2y + 3z  \Longrightarrow U+W \equiv x + 2y + 3z + 4t = 0$

</li>
</ol>
Y con esto ya tenemos las ecuaciones cartesianas (en este caso la ecuación cartesiana) del subespacio $U+W$.

</li>
<li>Vamos ahora con una base del subespacio $U\cap W$. Ya hemos visto que $\text{dim}(U) = 2$, $\text{dim}(W) = 2$ y $\text{dim}(U+W) = 3$, así que $\text{dim}(U\cap W) = \text{dim}(U) + \text{dim}(W) - \text{dim}(U+W) = 2 + 2 - 3 = 1$.

Para calcular una base de este subespacio, vamos a unir las ecuaciones de $U$ y de $W$ y a resolver el sistema que nos resulte. Para eso, previamente calculamos las ecuaciones cartesianas de $U$.
<ol type='i'>
<li> Calculamos las ecuaciones cartesianas de $U$. Puesto que $\text{dim}(U) = 2$, el número de ecuaciones cartesianas de $U$ es $4-2=2$.

Partimos de la base que ya hemos calculado ($B_U = \{(1,0,3,0),\ (0,1,0,2)\}$) y con ella escribimos las ecuaciones paramétricas, y de ahí, eliminando los parámetros, obtendremos las ecuaciones cartesianas:

$\left. \begin{array}{rrr}
x & = & a \\  y & = & b \\ z & = & 3a \\ t & = & 2b \end{array}\right\} \Longrightarrow
U \equiv \left\{ \begin{array}{r} z = 3x \\ t = 2y \end{array}\right. \Longrightarrow \qquad U \equiv \left\{ \begin{array}{rrrrrrrrr} 2x & & & + & z & & & = & 0 \\ & & 3y & & & + & t & = & 0 \end{array}\right.$ 

</li>
<li>Juntamos las ecuaciones de $W$ (que ya hemos calculado), y las de $U$ (que acabamos de calcular), y de esta forma, tenemos unas ecuaciones de $U\cap W$. Resolvemos este sistema:

$\left (\begin{array}{rrrr} 1 & 0 & 2 & 2 \\ 0 & 1 & 3 & 1 \\ 2 & 0 & 1 & 0 \\ 0 & 3 & 0 & 1 \end{array}\right )
\stackrel{E_{32}(1)}{\stackrel{E_{42}(3)}{\longrightarrow}}
\left (\begin{array}{rrrr} 1 & 0 & 2 & 2 \\ 0 & 1 & 3 & 1 \\ 0 & 0 & 2 & 1 \\ 0 & 0 & 1 & 3 \end{array}\right )
\stackrel{E_{34}}{\longrightarrow}
\left (\begin{array}{rrrr} 1 & 0 & 2 & 2 \\ 0 & 1 & 3 & 1 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 2 & 1 \end{array}\right )
\stackrel{E_{13}(3)}{\stackrel{E_{23}(2)}{\stackrel{E_{43}(3)}{\longrightarrow}}}
\left (\begin{array}{rrrr} 1 & 0 & 0 & 1 \\ 0 & 1 & 0 & 2 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 0 & 0 \end{array}\right )$

</li>
</ol>
Y con esto, tenemos que
$U\cap W \equiv \left\{ \begin{array}{rrrrrrrrr} x & & & & & + & t & = & 0 \\ & & y & & & + & 2t & = & 0 \\ & & & & z & + & 3t & = & 0 \end{array}\right. \Longrightarrow
U\cap W \equiv \left\{ \begin{array}{rrr} x & = & 4t \\ y & = & 3t \\ z & = & 2t \end{array}\right.$

Vemos que, puesto que $U\cap W$ viene dado por tres ecuaciones, $\text{dim}(U\cap W) = 4-3=1$, algo que ya sabíamos.

Para obtener una base, le damos a $t$, la incógnita libre un valor (distinto de cero). Nos queda que $B_{U\cap W} = \{(4,3,2,1)\}$.
</li>
</ol>


::::
:::::

::::: {#exr-40 .medio-cuerpo_finito} 

Sea $U$ el subespacio de $({\mathbb Z}_5)^3$ generado por los vectores $(3,1,4)$ y $(4,3,2)$, y $W$ el subespacio de $({\mathbb Z}_5)^3$ dado por las ecuaciones $\left\{\begin{array}{l} x + 2y + 3z = 0 \\ x + 3y + 2z = 0 \end{array} \right.$.

Determina para qué valor del parámetro $\alpha$ el vector $(2,1,\alpha)$ pertenece al subespacio $U+W$.

:::: {.callout collapse="true" title="Solución"}

En primer lugar, calculamos una base de $U$.

$$\left (\begin{array}{rrr} 3 & 1 & 4 \\ 4 & 3 & 2 \end{array}\right ) \stackrel{E_1(2)}{\longrightarrow} \left (\begin{array}{rrr} 1 & 2 & 3 \\ 4 & 3 & 2 \end{array}\right ) \stackrel{E_{21}(1)}{\longrightarrow} \left (\begin{array}{rrr} 1 & 2 & 3 \\ 0 & 0 & 0 \end{array}\right )$$

Por lo que $B_U=\{(1,2,3)\}$.

A continuación calculamos una base de $W$.

$$\left (\begin{array}{rrr} 1 & 2 & 3 \\ 1 & 3 & 2 \end{array}\right ) \stackrel{E_{21}(4)}{\longrightarrow} \left (\begin{array}{rrr} 1 & 2 & 3 \\ 0 & 1 & 4 \end{array}\right ) \stackrel{E_{12}(3)}{\longrightarrow} \left (\begin{array}{rrr} 1 & 0 & 0 \\ 0 & 1 & 4 \end{array}\right )$$

Por lo que tenemos $W\equiv \left\{ \begin{array}{rrrrrrr} x & & & & & = & 0 \\ & & y & + & 4z & = & 0 \end{array}\right.$

Vemos entonces que $\text{dim}(W) = 3-2 = 1$ y $B_W = \{(0,1,1)\}$.

Por consiguiente, $U+W = L[(1,2,3),\ (0,1,1)]$ y puesto que estos dos vectores son linealmente independientes, tenemos la siguiente base de $U+W$: $B_{U+W} = \{(1,2,3),\ (0,1,1)\}$.

Así que el vector $(2,1,\alpha) \in U+W$ si, y solo si, los vectores $\{(1,2,3),\ (0,1,1),\ (2,1,\alpha)\}$ son linealmente dependientes, lo que se traduce en que el determinante de la matriz $\left (\begin{array}{rrr} 1 & 2 & 3 \\ 0 & 1 & 1 \\ 2 & 1 & \alpha \end{array}\right )$ es igual a cero.

$$
\left | \begin{array}{rrr} 1 & 2 & 3 \\ 0 & 1 & 1 \\ 2 & 1 & \alpha \end{array}\right | = 0 \Longleftrightarrow \alpha + 4 -6 -1 = 0 \Longleftrightarrow \alpha - 3 = 0 \Longleftrightarrow \alpha = 3.$$

También podemos calcular las ecuaciones cartesianas (en este caso la ecuación) de $U+W$ y luego estudiar para qué valores de $\alpha$ el vector $(2,1,\alpha)$ satisface esta ecuación.

Para esto, en primer lugar transformamos la base que tenemos de $U+W$:

$$\left (\begin{array}{rrr} 1 & 2 & 3 \\ 0 & 1 & 1 \end{array}\right ) \stackrel{E_{12}(3)}{\longrightarrow} \left (\begin{array}{rrr} 1 & 0 & 1 \\ 0 & 1 & 1 \end{array}\right ).$$

Con esta base $\{(1,0,1),\ (0,1,1)\}$ escribimos las ecuaciones paramétricas y de ellas deducimos las ecuaciones cartesianas:


$$U+W \equiv \left\{ \begin{array}{rrrrr} x & = & a & & \\ y & = & & & b \\ z & = & a & + & b \end{array}\right. \ \ \Longrightarrow \ \ U+W \equiv z = x+y.$$

Y ahora, para que el vector $(2,1,\alpha)$ pertenezca a $U+W$, debe satisfacer esta ecuación, lo que nos dice que $\alpha = 2+1 = 3$.

::::
:::::

::::: {#exr-41 .basico-cuerpo_finito} 

En el espacio vectorial ( $\left.\mathbb{Z}_{5}\right)^{4}$ consideramos los subespacios vectoriales

$$
\begin{aligned}
U & =\langle(0,1,1,1),(2,0,2,0)\rangle=L[(0,1,1,1),(2,0,2,0)] \\
W & \equiv\left\{\begin{array}{c}
x+y+z+t=0 \\
2 x+y+2 t=0
\end{array}\right.
\end{aligned}
$$

Calcula unas ecuaciones cartesianas de $U+W$ y comprueba si $(1,2,2,2) \in U+W$.

:::: {.callout collapse="true" title="Solución"}

Puesto que nos piden calcular la suma de los subespacios necesitamos una base de cada uno de ellos (con un sistema de generadores bastaría). Una base de $U$ la tenemos, pues nos la da el enunciado. Dicha base es $B_{U}=\{(0,1,1,1) ;(2,0,2,0)\}$.

Calculamos entonces una base de $W$. Como tenemos las ecuaciones cartesianas, resolvemos el sistema que nos define $W$ :

$$
\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
2 & 1 & 0 & 2
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
0 & 4 & 3 & 0
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 1 & 1 & 1 \\
0 & 1 & 2 & 0
\end{array}\right) \longrightarrow\left(\begin{array}{llll}
1 & 0 & 4 & 1 \\
0 & 1 & 2 & 0
\end{array}\right)
$$

Es decir,

$$
W \equiv\left\{\begin{array} { r l } 
{ x } & { + 4 z + t = 0 } \\
{ } & { y + 2 z }
\end{array} \text { es decir, } W \equiv \left\{\begin{array}{rl}
x & =z+4 t \\
y & =3 z
\end{array}\right.\right.
$$

Dándole a $z$ y a $t$ los valores 10 y 0,1 obtenemos una base de $W: B_{W}=\{(1,3,1,0) ;(4,0,0,1)\}$.\\
Si ahora unimos las dos bases lo que obtenemos es un sistema de generadores de $U+W$. A partir de ellos vamos a obtener una base:

$$
\left(\begin{array}{llll}
0 & 1 & 1 & 1 \\
2 & 0 & 2 & 0 \\
1 & 3 & 1 & 0 \\
4 & 0 & 0 & 1
\end{array}\right) \xrightarrow{E_{13}}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
2 & 0 & 2 & 0 \\
0 & 1 & 1 & 1 \\
4 & 0 & 0 & 1
\end{array}\right) \xrightarrow{E_{21}(3)}{ }^{E_{14}(1)}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
0 & 4 & 0 & 0 \\
0 & 1 & 1 & 1 \\
0 & 3 & 1 & 1
\end{array}\right) \xrightarrow{E_{2(4)}}\left(\begin{array}{llll}
1 & 3 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 1 & 1 & 1 \\
0 & 3 & 1 & 1
\end{array}\right) 
$$
$$\xrightarrow{\substack{E_{12}(2) \\
E_{32}(4) \\
E_{42}(2)}}\left(\begin{array}{llll}
1 & 0 & 1 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 1 \\
0 & 0 & 1 & 1
\end{array}\right) \xrightarrow{E_{13}(4)}\left(\begin{array}{llll}
1 & 0 & 0 & 4 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 1 \\
0 & 0 & 0 & 0
\end{array}\right)
$$

Y por tanto vemos que una base de $U+W$ es $B_{U+W}=\{(1,0,0,4) ;(0,1,0,0) ;(0,0,1,1)\}$.\\
Puesto que $\operatorname{dim}(U+W)=3$ y $U+W$ es subespacio de $\left(\mathbb{Z}_{5}\right)^{4}$, el subespacio $U+W$ viene dado por $4-3=1$ ecuación cartesiana. Para calcularla escribimos las ecuaciones paramétricas, y esto lo hacemos teniendo en cuenta que un vector $(x, y, z, t) \in U+W$ si, y sólo si, es combinación lineal de los vectores de la base. Por tanto, deben poder expresarse de la forma:

$$
(x, y, z, t)=a(1,0,0,4)+b(0,1,0,0)+c(0,0,1,1)
$$

o lo que es lo mismo:

$$
\begin{aligned}
x & =a \\
y & = b\\
z & =c \\
t & =4a+c
\end{aligned}
$$

Y aquí vemos que si $(x, y, z, t) \in U+W$ se tiene que $t=4 x+z$. Por tanto, $U+W \equiv x+4 z+t=0$. Y ya tenemos las ecuaciones cartesianas de $U+W$ (en este caso, la ecuación cartesiana).

Para comprobar si $(1,2,2,2) \in U+W$ basta comprobar si satisface la ecuación. Puesto que $1+4 \cdot 2+2=1 \neq 0$ dicho vector no pertenece a $U+W$.

::::
:::::



::::: {.test}
<iframe src="/assets/autoevaluacion/AutoevaluacionEV.html" style="border:none;" height="765" width="100%" title="Autoevaluación"></iframe>
:::::

::::: {.test-cuerpo_finito}
<iframe src="/assets/autoevaluacion/AutoevaluacionEV-CF.html" style="border:none;" height="765" width="100%" title="Autoevaluación CF"></iframe> 
:::::