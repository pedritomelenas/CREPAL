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

*Diagonalización por semejanza. Valores y vectores propios (autovalores, autovectores). Ecuación característica de una matriz/endomorfismo. Cálculo de los valores propios. Cálculo de los subespacios propios. Matriz diagonal y matriz de paso.*


<!--Se muestran ejercicios sobre cuerpos finitos y sobre los racionales y reales. Puedes cambiar esta opción marcando o desmarcando la siguiente casilla.<br>-->

<!-- por ahora todos medios, cambiar luego
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_basico" value="basicoon" checked onclick="mostrar();"> Básicos </button> 
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_medio" value="medioon" checked onclick="mostrar();"> Dificultad media </button>
<button class="btn btn-outline-secondary btn-sm mb-2"><input type="checkbox" id="casilla_avanzado" value="avanzadon" checked onclick="mostrar();"> Avanzados. </button>
-->

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

::::: {#exr-1 .cuerpo_finito-medio}

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

::::: {#exr-2 .medio}

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

::::: {#exr-3 .cuerpo_finito}

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


::::: {#exr-4 .cuerpo_finito-medio}

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

::::: {#exr-5 .avanzado}

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

::::: {#exr-6 .avanzado}
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

:::::{#exr-7 .medio}

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

:::::{#exr-8 .basico}

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

:::::{#exr-9 .basico}

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

:::::{#exr-10 .medio}

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

:::::{#exr-11 .medio}

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

:::::{#exr-12 .medio}

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

:::::{#exr-13 .medio}

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

:::::{#exr-14 .medio}

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

:::::{#exr-15 .basico}

Para la matriz simétrica
$$
\begin{pmatrix}
2 & 1 \\ 1 & 2
\end{pmatrix}
$$

determinar su forma diagonal y una matriz de paso $P$ tal que $D=P^{-1}AP$.

:::: {.callout collapse="true" title="Solución"}

Calculamos su polinomio característico, que nos permitirá obtener los valores propios

$$
\begin{vmatrix}
2-\lambda & 1 \\ 1 & 2-\lambda
\end{vmatrix}= (2-\lambda)^2-1= \lambda^2-4\lambda+3= (\lambda-3)(\lambda-1)
$$

Calculamos cada uno de los subespacios propios:

$\boxed{V_{\lambda=3}}$

$$
\begin{pmatrix}
2-3 & 1 \\ 1 & 2-3
\end{pmatrix}=
\begin{pmatrix}
-1 & 1 \\ 1 & -1
\end{pmatrix}
\sim_f \begin{pmatrix}
1 & -1 \\ 0 & 0
\end{pmatrix}
$$

así que la ecuación cartesiana es $x-y=0$ y una base, por ejemplo, el vector $\{(1,1)\}$.

$\boxed{V_{\lambda=1}}$

$$
\begin{pmatrix}
2-1 & 1 \\ 1 & 2-1
\end{pmatrix}=
\begin{pmatrix}
1 & 1 \\ 1 & 1
\end{pmatrix}
\sim_f \begin{pmatrix}
1 & 1 \\ 0 & 0
\end{pmatrix}
$$

así que la ecuación cartesiana es $x+y=0$ y una base, por ejemplo, el vector $\{(1,-1)\}$.
Por tanto 

$$
D=\begin{pmatrix}
3 & 0 \\ 0 & 1
\end{pmatrix}  \hspace{2cm} P=\begin{pmatrix}
1 & 1 \\ -1 & 1
\end{pmatrix}
$$

::::
:::::

:::::{#exr-16 .basico}

Determinar para qué valores de $a$ y $b$ es diagonalizable por semejanza la matriz
$$
\begin{pmatrix}
a & 1 \\ 0 & b
\end{pmatrix}
$$

:::: {.callout collapse="true" title="Solución"}

Calculamos el polinomio característico que nos permite obtener los valores propios:

$$
\begin{vmatrix}
a-\lambda & 1 \\ 0 & b-\lambda
\end{vmatrix}= (a-\lambda)(b-\lambda)
$$

Cuando $a$ y $b$ son <b>distintos</b>, entonces cada uno de ellos tiene multiplicidad algeraica 1 y, por tanto, también multiplicidad geométrica 1. Eso nos asegura que la matriz es diagonalizable por semejanza.
En el caso $a=b$, entonces tenemos un único valor propio con multiplicidad algebraica 2, calculamos su multiplicidad geométrica, que es la dimensión del subespacio propio. Calculamos las ecuaciones cartesianas de $V_{\lambda=a}$ 

$$
A-aI=
\begin{pmatrix}
a-a & 1 \\ 0 & a-a
\end{pmatrix}=
\begin{pmatrix}
0 & 1 \\ 0 & 0
\end{pmatrix}
$$

luego obtenemos la ecuación $y=0$, por tanto $dim \, V_{\lambda=a}=dim\, \mathbb{R}^2 - \mbox{ nº mínimo de ecuaciones} =1$ con lo que no coincide con la algebraica y por tanto la matriz <b>no</b> es diagonalizable por semejanza.

::::
:::::

:::::{#exr-17 .basico-cuerpo_finito}

Sea 
$$
A = 
\begin{pmatrix}
3 & 5 \\
9 & 0
\end{pmatrix} \in M_2(\mathbb{Z}_{47}).
$$

<ol type="a">
<li> Estudia si $A$ es diagonalizable, y en caso afirmativo, encuentra $P \in M_2(\mathbb{Z}_{47})$, regular, tal que $P^{-1}AP$ sea una matriz diagonal.
</li>
<li> Calcula $A^{48}$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> <b>Polinomio característico</b>:
$$
p_A(\lambda) = \lambda^2 - \text{tr}(A)\lambda + \det(A) 
= \lambda^2 - 3\lambda - 45 
= \lambda^2 + 44\lambda + 2 \quad (\text{en } \mathbb{Z}_{47}).
$$

Comprobamos que $p_A(1)=0$, por lo que $\lambda=1$ es raíz. Dividiendo, obtenemos:
$$
p_A(\lambda) = (\lambda-1)(\lambda-2).
$$
Por tanto, los valores propios son $\lambda_1=1$, $\lambda_2=2$, ambos con multiplicidad algebraica $1$.

La tabla queda:
$$
\begin{array}{c|c|c}
\text{Valor propio} & \alpha & d \\ \hline
\lambda_1=1 & 1 & 1 \\
\lambda_2=2 & 1 & 1
\end{array}
$$
Como $d_1+d_2=2$, $A$ es diagonalizable.

<b>Vectores propios</b>:

Para $\lambda=1$:
$$
A-I =
\begin{pmatrix}
2 & 5 \\
9 & 46
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 26 \\
0 & 0
\end{pmatrix}.
$$
Ecuación: $x+26y=0$. Una base es:
$$
B_{V_1} = \{(21,1)\}.
$$

Para $\lambda=2$:
$$
A-2I =
\begin{pmatrix}
1 & 5 \\
9 & 45
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 5 \\
0 & 0
\end{pmatrix}.
$$
Ecuación: $x+5y=0$. Una base es:
$$
B_{V_2} = \{(42,1)\}.
$$

Por tanto, tomando:
$$
P =
\begin{pmatrix}
21 & 42 \\
1 & 1
\end{pmatrix}, \quad
P^{-1}AP =
\begin{pmatrix}
1 & 0 \\
0 & 2
\end{pmatrix} = D.
$$

</li>
<li> <b>Potencia de la matriz.</b>

Dado que $A=PDP^{-1}$, tenemos:
$$
A^{48} = P D^{48} P^{-1}, \quad D^{48} = 
\begin{pmatrix}
1^{48} & 0 \\
0 & 2^{48}
\end{pmatrix}.
$$

En $\mathbb{Z}_{47}$, por el pequeño teorema de Fermat:
$$
2^{46} \equiv 1 \ (\text{mod } 47).
$$

Así:
$$
2^{48} = 2^{46}\cdot 2^2 \equiv 1\cdot 4 = 4.
$$

Por tanto:
$$
D^{48} =
\begin{pmatrix}
1 & 0 \\
0 & 4
\end{pmatrix}.
$$

Finalmente:
$$
A^{48} = P D^{48} P^{-1}.
$$

También, como $A^{46}=I$, se cumple:
$$
A^{48} = A^{46}A^2 = A^2.
$$

Calculamos:
$$
A^2 =
\begin{pmatrix}
3 & 5 \\
9 & 0
\end{pmatrix}
\begin{pmatrix}
3 & 5 \\
9 & 0
\end{pmatrix}
=
\begin{pmatrix}
7 & 15 \\
27 & 45
\end{pmatrix}.
$$

$$
\boxed{A^{48} =
\begin{pmatrix}
7 & 15 \\
27 & 45
\end{pmatrix}}
$$

</li>
</ol>

::::
:::::

:::::{#exr-18 .basico-cuerpo_finito}

Dada la matriz
$$
A =
\begin{pmatrix}
2 & 1 & 1 \\
2 & 0 & 2 \\
1 & 1 & 2
\end{pmatrix} \in M_3(\mathbb{Z}_5),
$$

estudia si $A$ es o no diagonalizable y, en caso afirmativo, encuentra una matriz regular $P$ tal que $P^{-1}AP$ sea una matriz diagonal $D$. Di cuál es la matriz $D$.

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Polinomio característico.
Sabemos:
$$
\text{tr}(A) = 2+0+2=4=1 \ (\text{en } \mathbb{Z}_5),
$$

$$
\det(A)=2\cdot 0\cdot 2 + 1\cdot 2\cdot 1 + 1\cdot 2\cdot 1 - 1\cdot 0\cdot 1 - 1\cdot 2\cdot 2 - 2\cdot 2\cdot 1 = 2.
$$

De aquí:
$$
p_A(\lambda) = -\lambda^3 + \text{tr}(A)\lambda^2 - \text{tr}(\text{Adj}(A))\lambda + \det(A) = 2\lambda^3 + \lambda^2 + \lambda + 2.
$$

También puede calcularse como el determinante de $|A-\lambda I|$.

</li>
<li> Valores propios.

Resolviendo en $\mathbb{Z}_5$, obtenemos:
$$
\lambda_1 = 1 \ (\alpha_1=2), \quad \lambda_2 = 2 \ (\alpha_2=1).
$$

</li>
<li> Multiplicidades geométricas.

Para $\lambda=1$:
$$
A-I =
\begin{pmatrix}
1 & 1 & 1 \\
2 & 2 & 2 \\
1 & 1 & 1
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 1 & 1 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{pmatrix}.
$$
Así, $rg(A-I)=1$, por tanto $\dim V_1 = 2$.

Para $\lambda=2$:
$$
A-2I =
\begin{pmatrix}
0 & 1 & 1 \\
2 & 1 & 2 \\
1 & 1 & 0
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 0 & 2 \\
0 & 1 & 1 \\
0 & 0 & 0
\end{pmatrix}.
$$
Así, $rg(A-2I)=2$, luego $\dim V_2=1$.

En resumen:
$$
\lambda=1, \ \alpha_1=2, \ d_1=2; 
\quad 
\lambda=2, \ \alpha_2=1, \ d_2=1.
$$
Dado que $d_1+d_2=3$, la matriz es diagonalizable.

</li>
<li> Subespacios propios.

Para $\lambda=1$:
$$
V_1 \equiv \{x+y+z=0\}, \quad \mbox{Base }V_1 = \{(1,0,2), (0,1,2)\}.
$$

Para $\lambda=2$:
$$
V_2 \equiv \{x+2z=0, \ y+z=0\}, \quad \mbox{Base }V_2 = \{(1,2,1)\}.
$$

</li>
<li> Matrices $P$ y $D$.

Tomamos como columnas de $P$ las bases de $V_1$ y $V_2$:
$$
P =
\begin{pmatrix}
1 & 0 & 1 \\
0 & 1 & 2 \\
2 & 2 & 1
\end{pmatrix}, \quad
D =
\begin{pmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 2
\end{pmatrix}.
$$

Así, $P^{-1}AP = D$.

</li>
</ol>

::::
:::::

:::::{#exr-19 .basico-cuerpo_finito}

Dada la matriz
$$
A =
\begin{pmatrix}
0 & 2 & 2 & 2 \\
1 & 2 & 1 & 1 \\
0 & 0 & 2 & 0 \\
1 & 1 & 0 & 2
\end{pmatrix} \in M_4(\mathbb{Z}_3),
$$

estudia si $A$ es o no diagonalizable, y en caso afirmativo, encuentra una matriz regular $P$ tal que $P^{-1}AP$ sea una matriz diagonal $D$ e indica cuál es la matriz $D$.


:::: {.callout collapse="true" title="Solución"}

Dividimos la resolución en pasos:

<ol type="i">
<li> Cálculo del polinomio característico
$$
p_A(\lambda) = \det(A-\lambda I) 
= 
\begin{vmatrix}
-\lambda & 2 & 2 & 2 \\
1 & 2-\lambda & 1 & 1 \\
0 & 0 & 2-\lambda & 0 \\
1 & 1 & 0 & 2-\lambda
\end{vmatrix}
$$

$$
= (2-\lambda)\cdot
\begin{vmatrix}
-\lambda & 2 & 2 \\
1 & 2-\lambda & 1 \\
1 & 1 & 2-\lambda
\end{vmatrix}.
$$

Tras desarrollar y simplificar en $\mathbb{Z}_3$, se obtiene:
$$
p_A(\lambda) = (2-\lambda)(2\lambda^3 + \lambda^2 + \lambda + 2).
$$

De aquí se deduce que los valores propios son $\lambda=1$ y $\lambda=2$, ambos con multiplicidad algebraica $2$.

</li>
<li> Multiplicidades geométricas

Para $\lambda=1$:
Se resuelve $(A-I)x=0$:
$$
A-I =
\begin{pmatrix}
2 & 2 & 2 & 2 \\
1 & 1 & 1 & 1 \\
0 & 0 & 1 & 0 \\
1 & 1 & 0 & 1
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 1 & 0 & 1 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}.
$$

Así,
$$
V_1 \equiv \{x+y+t=0, \ z=0\}, \quad \dim V_1 = 2.
$$

Para $\lambda=2$:
Se resuelve $(A-2I)x=0$:
$$
A-2I =
\begin{pmatrix}
1 & 2 & 2 & 2 \\
1 & 0 & 1 & 1 \\
0 & 0 & 0 & 0 \\
1 & 1 & 0 & 0
\end{pmatrix}
\longrightarrow
\begin{pmatrix}
1 & 0 & 1 & 1 \\
0 & 1 & 2 & 2 \\
0 & 0 & 0 & 0 \\
0 & 2 & 1 & 1
\end{pmatrix}.
$$

Así,
$$
V_2 \equiv \{x+z+t=0,\ y+2z+2t=0\}, \quad \dim V_2 = 2.
$$

Por tanto, $A$ es diagonalizable.

</li>
<li> Bases de cada subespacio propios

De $V_1$:
$$
\{(2,1,0,0), (2,0,0,1)\}.
$$

De $V_2$:
$$
\{(2,1,1,0), (2,1,0,1)\}.
$$

</li>
<li> Matriz de paso y diagonalización

Tomando como $P$ la matriz con estas columnas:
$$
P =
\begin{pmatrix}
2 & 2 & 2 & 2 \\
1 & 0 & 1 & 1 \\
0 & 0 & 1 & 0 \\
0 & 1 & 0 & 1
\end{pmatrix},
$$
tenemos que $P$ es regular y
$$
P^{-1}AP =
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 2 & 0 \\
0 & 0 & 0 & 2
\end{pmatrix}
= D.
$$

</li>
</ol>

::::
:::::

:::::{#exr-20 .basico-cuerpo_finito}

Dada la matriz

$$
A=\left(\begin{array}{lll}
5 & 1 & 1 \\
6 & 4 & 2 \\
5 & 4 & 6
\end{array}\right) \in \mathcal{M}_{3}\left(\mathbb{Z}_{7}\right)
$$

calcula, si es posible, matrices $P, D \in \mathcal{M}_{3}\left(\mathbb{Z}_{7}\right)$ tales que $D$ es diagonal y $A=P D P^{-1}$.

:::: {.callout collapse="true" title="Solución"}

Notemos que nos piden es encontrar una matriz regular $P$ tal que $P^{-1} \cdot A \cdot P$ sea una matriz diagonal.\\
De existir esta matriz $P$, sus columnas serían vectores propios de $A$. Por tanto hemos de ver si la matriz $A$ tiene una base de vectores propios, o lo que es lo mismo si $A$ es diagonalizable.

Comenzamos entonces calculando el polinomio característico de $A$, que es igual al determinante de la matriz $A-\lambda I d$.

$$
\begin{aligned}
\left|\begin{array}{ccc}
5-\lambda & 1 & 1 \\
6 & 4-\lambda & 2 \\
5 & 4 & 6-\lambda
\end{array}\right| & =(5-\lambda)(4-\lambda)(6-\lambda)+6 \cdot 4 \cdot 1+1 \cdot 2 \cdot 5-(1 \cdot 5(4-\lambda)+1 \cdot 6(6-\lambda)+2 \cdot 4(5-\lambda)) \\
& =\left(20-5 \lambda-4 \lambda+\lambda^{2}\right)(6-\lambda)+24+10-(20-5 \lambda+36-6 \lambda+40-8 \lambda) \\
& =\left(\lambda^{2}-9 \lambda+20\right)(6-\lambda)+34-(96-19 \lambda) \\
& =\left(6 \lambda^{2}-\lambda^{3}-54 \lambda+9 \lambda^{2}+120-20 \lambda\right)+34-96+19 \lambda \\
& =-\lambda^{3}+15 \lambda^{2}-55 \lambda+58 \\
& =6 \lambda^{3}+\lambda^{2}+\lambda+2
\end{aligned}
$$

Continuamos calculando los valores propios, es decir, las raíces de este polinomio (usando la división por Ruffini y probando con valores sencillos). Calculamos también sus multiplicidades algebraicas.

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			0
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			0
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			3
		</td>
	</tr>
</table>

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			5
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			5
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			5
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			0
		</td>
	</tr>
</table>

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			5
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			0
		</td>
	</tr>
</table>

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			5
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			2
		</td>
	</tr>
</table>

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			3
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			1
		</td>
	</tr>
</table>

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			4
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-bottom: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
			3
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			6
		</td>
		<td style="padding-right: 3pt; padding-left: 3pt;">
			0
		</td>
	</tr>
</table>

Y vemos que tiene dos valores propios: $\lambda_{1}=2$ con multiplicidad algebraica $m_{2}=2$ y $\lambda_{2}=4$ con multiplicidad algebraica $m_{4}=1$.

Vamos con la multiplicidad geométrica. Puesto que si $\lambda$ es un valor propio su multiplicdad geométrica $d_{\lambda}$ verifica que $1 \leq d_{\lambda} \leq m_{\lambda}$ sabemos que la multiplicidad geométrica del valor propio 4 vale 1 mientras que la del valor propio 2 puede valer 1 ó 2 .

Lo siguiente es calcular los subespacios propios y de esta forma tendremos $d_{2}$ y $d_{4}$.\\
Primero calculamos $V_{2}$. Este subespacio viene dado por unas ecuaciones cuya matriz de coeficientes es $A-2 I d$. Es decir,

$$
V_{2} \equiv\left\{\begin{array}{l}
3 x+y+z=0 \\
6 x+2 y+2 z=0 \\
5 x+4 y+4 z=0
\end{array}\right.
$$

Calculamos la forma normal de Hermite de su matriz de coeficientes:

$$
\left(\begin{array}{lll}
3 & 1 & 1 \\
6 & 2 & 2 \\
5 & 4 & 4
\end{array}\right) \xrightarrow{E_{1}(15)}\left(\begin{array}{lll}
1 & 5 & 5 \\
6 & 2 & 2 \\
5 & 4 & 4
\end{array}\right) \xrightarrow{E_{21}(1)}\left(\begin{array}{lll}
1 & 5 & 5 \\
0 & 0 & 0 \\
0 & 0 & 0
\end{array}\right)
$$

Luego $V_{2} \equiv x+5 y+5 z=0$ de donde $d_{2}=\operatorname{dim}\left(V_{2}\right)=2$.\\
Una base de $V_{2}$ es $B_{V_{2}}=\{(2,1,0) ;(2,0,1)\}$.\\
Para calcular $V_{4}$ repetimos lo mismo. Calculamos la forma normal de Hermite de $A-4 / d$.

$$
\left(\begin{array}{lll}
1 & 1 & 1 \\
6 & 0 & 2 \\
5 & 4 & 2
\end{array}\right) \xrightarrow{E_{21}(1)}\left(\begin{array}{lll}
1 & 1 & 1 \\
0 & 1 & 3 \\
0 & 6 & 4
\end{array}\right) \xrightarrow{E_{31}(2)}\left(\begin{array}{lll}
1 & 0 & 5 \\
0 & 1 & 3 \\
0 & 0 & 0
\end{array}\right)
$$

Luego $V_{4}$ viene dado por las ecuaciones $\left\{\begin{aligned} x \quad & \begin{array}{rl}x & =0 \\ & y\end{array}=3 z=0\end{aligned}\right.$. La dimensión es entonces 1 y una base es $B_{V_{4}}\{(2,4,1)\}$.

Con lo que hemos hecho hasta ahora podemos saber que la matriz $A$ es diagonalizable, y una base de vectores propios es $B=\{(2,1,0) ;(2,0,1) ;(2,4,1)\}$. Los dos primeros son vectores propios de valor propio 2 y el tercero es un vector propio de valor propio 4.

Si tomamos como $P$ a la matriz cuyas columnas son estos tres vectores, es decir, $P=\left(\begin{array}{lll}2 & 2 & 2 \\ 1 & 0 & 4 \\ 0 & 1 & 1\end{array}\right)$ entonces $P^{-1} \cdot A \cdot P=\left(\begin{array}{lll}2 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 4\end{array}\right)$ que es una matriz diagonal.

Tenemos entonces las matrices $D$ y $P$ que nos pedía el enundiado.


::::
:::::

:::::{#exr-21 .medio-cuerpo_finito}

Sea $f:\left(\mathbb{Z}_{7}\right)^{3} \rightarrow\left(\mathbb{Z}_{7}\right)^{3}$ la única aplicación lineal tal que

$$
\begin{aligned}
\operatorname{ker}(f) & =N(f) \equiv\left\{\begin{array}{r}
x+4 y+6 z=0 \\
3 x+3 y=0
\end{array}\right. \\
V_{2} & =\langle(1,0,1),(1,1,0)\rangle=L[(1,0,1),(1,1,0)]
\end{aligned}
$$

donde $V_{2}$ denota el subespacio propio de valor propio 2.
Calcula $M_{B_{c}}(f)=A\left(f ; B_{c}, B_{c}\right)$ donde $B_{c}$ es la base canónica de $\left(\mathbb{Z}_{7}\right)^{3}$.


:::: {.callout collapse="true" title="Solución"}

Recordemos que el subespacio propio de valor propio 2 está formado por todos los vectores $u \in\left(\mathbb{Z}_{7}\right)^{3}$ tales que $f(u)=2 \cdot u$.

Calculamos ahora una base del núcleo de $f$. Como tenemos las ecuaciones de dicho subespacio, resolvemos el sistema:

$$
\left(\begin{array}{lll}
1 & 4 & 6 \\
3 & 3 & 0
\end{array}\right) \xrightarrow{E_{21}(4)}\left(\begin{array}{lll}
1 & 4 & 6 \\
0 & 5 & 3
\end{array}\right) \xrightarrow{E_{2}(3)}\left(\begin{array}{lll}
1 & 4 & 6 \\
0 & 1 & 2
\end{array}\right) \xrightarrow{E_{12}(3)}\left(\begin{array}{lll}
1 & 0 & 5 \\
0 & 1 & 2
\end{array}\right)
$$

Luego $N(f) \equiv\left\{\begin{aligned} x & +5 z=0 \\ & y+2 z=0,\end{aligned}\right.$ es decir, $N(f) \equiv \begin{cases}x & =2 z \\ y & =5 z\end{cases}$\\
Teniendo esto en cuenta, los distintos datos que nos dan sobre la aplicación $f$ nos dicen:

<ul>
  <li> $(2,5,1) \in N(f)$, es decir, $f(2,5,1)=(0,0,0)$.</li>
  <li> $(1,0,1)$ es un vector de valor propio 2 , es decir, $f(1,0,1)=(2,0,2)$.</li>
  <li> $(1,1,0)$ es un vector de valor propio 2 , es decir, $f(1,1,0)=(2,2,0)$.</li>
</ul>

Y puesto que $B=\{(2,5,1) ;(1,0,1) ;(1,1,0)\}$ forma una base de $\left(\mathbb{Z}_{7}\right)^{3}$ tenemos todo lo necesario para determinar la aplicación lineal $f$.

Notemos que las columnas de la matriz $A=\left(\begin{array}{lll}0 & 2 & 2 \\ 0 & 0 & 2 \\ 0 & 2 & 0\end{array}\right)$ son las coordenadas de los vectores $f(2,5,1)$, $f(1,0,1)$ y $f(1,1,0)$ en la base canónica. Por tanto, tenemos que $A=M_{B, B_{c}}(f)$.

Para calcular la matriz de $f$ en la base canónica tenemos en cuenta que $M_{B_{c}}(f)=M_{B, B_{c}}(f) \cdot M_{B_{c} \rightarrow B}$ y que

$$
\begin{aligned}
M_{B_{c} \rightarrow B}=\left(M_{B \rightarrow B_{c}}\right)^{-1} & =\left(\begin{array}{lll}
2 & 1 & 1 \\
5 & 0 & 1 \\
1 & 1 & 0
\end{array}\right)^{-1}=\left(\begin{array}{lll}
5 & 2 & 2 \\
2 & 5 & 6 \\
3 & 5 & 4
\end{array}\right) . \\
M_{B_{c}}(f) & =M_{B, B_{c}}(f) \cdot M_{B_{c} \rightarrow B}=\left(\begin{array}{lll}
0 & 2 & 2 \\
0 & 0 & 2 \\
0 & 2 & 0
\end{array}\right) \cdot\left(\begin{array}{lll}
5 & 2 & 2 \\
2 & 5 & 6 \\
3 & 5 & 4
\end{array}\right)=\left(\begin{array}{lll}
3 & 6 & 6 \\
6 & 3 & 1 \\
4 & 3 & 5
\end{array}\right)
\end{aligned}
$$

De aquí podemos calcular una expresión explícita para $f: f(x, y, z)=(3 x+6 y+6 z, 6 x+3 y+z, 4 x+3 y+5 z)$. Es fácil comprobar, con esta expresión, que $f(2,5,1)=(0,0,0), f(1,0,1)=(2,0,2)$ y $f(1,1,0)=(2,2,0)$.

Otra forma de resolver este ejercicio sería la siguiente:\\
Conocemos cuanto vale $f(2,5,1), f(1,0,1)$ y $f(1,1,0)$. Necesitamos calcular $f(1,0,0), f(0,1,0)$ y $f(0,0,1)$. Para esto, escribimos estos tres vectores como combinación lineal de los vectores de la base $B$.

<ul>
  <li> $(1,0,0)=a(2,5,1)+b(1,0,1)+c(1,1,0)$. Esto nos da lugar al sistema </li>
</ul>

$$
\left\{\begin{array}{rl}
2 a+b+c & =1 \\
5 a +c &=0\\
a+b & =0
\end{array}
\right.
$$

que resolvemos a continuación:

$$
\left(\begin{array}{llll}
2 & 1 & 1 & 1 \\
5 & 0 & 1 & 0 \\
1 & 1 & 0 & 0
\end{array}\right) \xrightarrow{E_{13}}\left(\begin{array}{llll}
1 & 1 & 0 & 0 \\
5 & 0 & 1 & 0 \\
2 & 1 & 1 & 1
\end{array}\right) \xrightarrow{E_{21}(2)}\left(\begin{array}{llll}
1 & 1 & 0 & 0 \\
0 & 2 & 1 & 0 \\
0 & 6 & 1 & 1
\end{array}\right) \xrightarrow{E_{31}(5)}\left(\begin{array}{llll}
1 & 1 & 0 & 0 \\
0 & 1 & 4 & 0 \\
0 & 6 & 1 & 1
\end{array}\right) \xrightarrow{E_{12}(6)}
$$
$$\left(\begin{array}{llll}
1 & 0 & 3 & 0 \\
0 & 1 & 4 & 0 \\
0 & 0 & 5 & 1
\end{array}\right) \xrightarrow{E_{32}(5)}\left(\begin{array}{llll}
1 & 0 & 3 & 0 \\
0 & 1 & 4 & 0 \\
0 & 0 & 1 & 3
\end{array}\right) \xrightarrow{E_{13}(4)}\left(\begin{array}{lll}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{array}\right)
$$

Y que nos da la solución $a=5, b=2, c=3$. Notemos que estos valores coinciden con los de la primera columna de la matriz $M_{B_{c} \rightarrow B}$. A partir de aquí calculamos $f(1,0,0)$.

$$
f(1,0,0)=f(5(2,5,1)+2(1,0,1)+3(1,1,0))=5 f(2,5,1)+2 f(1,0,1)+3(1,1,0)=5(0,0,0)+2(2,0,2)+3(2,2,0)=(3,6,4)
$$

Y esto nos da la primera columna de la matriz $M_{B_{c}}(f)$.

<ul>
<li> $(0,1,0)=a^{\prime}(2,5,1)+b^{\prime}(1,0,1)+c^{\prime}(1,1,0)$. 
El sistema que resulta tiene como solución $a^{\prime}=2$, $b^{\prime}=5, c^{\prime}=5$.
$f(0,1,0)=f(2(2,5,1)+5(1,0,1)+5(1,1,0))=2 f(2,5,1)+5 f(1,0,1)+5(1,1,0)=2(0,0,0)+5(2,0,2)+5(2,2,0)=(6,3,3)$
$Y$ ya tenemos la segunda columna de $M_{B_{c}}(f)$. 
</li>
<li> $(0,0,1)=a^{\prime \prime}(2,5,1)+b^{\prime \prime}(1,0,1)+c^{\prime \prime}(1,1,0)$. 
El sistema que resulta tiene como solución $a^{\prime \prime}=2$, $b^{\prime \prime}=6, c^{\prime \prime}=4$
$f(0,0,1)=f(2(2,5,1)+6(1,0,1)+4(1,1,0))=2 f(2,5,1)+6 f(1,0,1)+4(1,1,0)=2(0,0,0)+6(2,0,2)+4(2,2,0)=(6,1,5)$ 
</li>
</ul>


::::
:::::

:::::{#exr-22 .basico}

Sea $A=\left (\begin{array}{ccc} 2 & -1 & 1 \\ 0 & 0 & 2 \\ 0 & -1 & 3 \end{array}\right )\in M_{3\times 3}({\mathbb R})$.

<ol type="a">
<li> Estudia si $A$ es o no diagonalizable (por semejanza). En caso afirmativo, encuentra una matriz regular $P$ y una matriz diagonal $D$ tal que $P^{-1}\cdot A \cdot P = D$.</li>
<li> Utiliza lo obtenido en el apartado anterior para calcular $A^{10}$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Comenzamos calculando el polinomio característico:

$\begin{array}{rcl}
p_A(\lambda) & = & \left | \begin{array}{ccc} 2-\lambda & -1 & 1 \\ 0 & -\lambda & 2 \\ 0 & -1 & 3-\lambda \end{array}\right | \\ \\
& = & (2-\lambda) \cdot \left | \begin{array}{cc} -\lambda & 2 \\ -1 & 3-\lambda \end{array}\right | \\ \\
& = & (2-\lambda) \cdot (-\lambda (3-\lambda) - (-2)) \\ \\
& = & (2-\lambda)(-3\lambda + \lambda^2 + 2 ) \\ \\
& = & (2-\lambda)(\lambda^2 - 3\lambda + 2). \end{array}$

También se puede calcular sabiendo que $p_A(\lambda) = -\lambda^3 + \text{tr}(A) \lambda ^2 - \text{tr}(\text{Adj}(A)) \lambda + \text{det}(A)$.

<ul>
  <li> $\text{tr}(A) = 2 + 0 + 3 = 5$</li>
  <li> $\text{tr}(\text{Adj}(A)) = \left | \begin{array}{rr} 0 & 2 \\ -1 & 3 \end{array}\right | + \left | \begin{array}{rr} 2 & 1 \\ 0 & 3 \end{array}\right | + \left | \begin{array}{rr} 2 & -1 \\ 0 & 0 \end{array}\right | = 2 + 6 + 0 = 8$.</li>
  <li> $\text{det}(A) = 0 + 0 + 0 - (0 + 0 - 4) = 4$.</li>
</ul>

Con esto tenemos que $p_A(\lambda) = -\lambda^3 + 5\lambda^2 - 8 \lambda + 4$.

Calculamos ahora las raíces, con sus multiplicidades.

Si partimos de la primera expresión, $p_A(\lambda) = (2-\lambda)(\lambda^2-3\lambda + 2)$, ya tenemos que $\lambda=2$ es raíz, y nos falta calcular las raíces de $\lambda^2 - 3\lambda + 2$. Las calculamos usando la fórmula de la ecuación de segundo grado: $\lambda = \frac{3 \pm \sqrt{3^2 - 4\cdot 1 \cdot 2}}{2} = \frac{3 \pm \sqrt{1}}{2} = \frac{3\pm 1}{2}$, que nos da como raíces $\lambda=2$ y $\lambda=1$.

Así que $p_A(\lambda)$ tiene dos raíces, que son $\lambda = 2$ (doble) y $\lambda = 1$ (simple).

También las podíamos haber obtenido a partir de la expresión $p_A(\lambda) = -\lambda^3 + 5\lambda^2 - 8 \lambda + 4$.

$\hspace{2cm} \begin{array}{r|rrrr}
& -1 & 5 & 8 & 4 \\ 1 & & -1 & 4 & -4 \\ \hline
& -1 & 4 & -4 & 0 \\ 2 & & -2 & 4 & \\ \hline
& -1 & 2 & 0 & \\ 2 & & -2 & & \\ \hline 
& -1 & 0 & & \end{array}$

Y tenemos el mismo resultado. Las raíces son $\lambda = 1$ (simple) y $\lambda=2$ (doble).

Calculamos ahora las multiplicidades geométricas. Tenemos el siguiente cuadro:

<table align="center" style="border-collapse: collapse; border: none; border-spacing: 0px;">
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: right; padding-right: 3pt; padding-left: 3pt;">
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			Multiplicidad algebraica
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			Multiplicidad geométrica
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: right; padding-right: 3pt; padding-left: 3pt;">
			$$\lambda = 1$$
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			$$\alpha_1 = 1$$
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			$$d_1 = 1$$
		</td>
	</tr>
	<tr>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: right; padding-right: 3pt; padding-left: 3pt;">
			$$\lambda = 2$$
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			$$\alpha_2 = 2$$
		</td>
		<td style="border-right: 1px solid black; border-bottom: 1px solid black; text-align: center; padding-right: 3pt; padding-left: 3pt;">
			$$d_2 = 1$$ o $$d_2 = 2$$
		</td>
	</tr>
</table>

Nos falta calcular $d_2$, y sabemos que $d_2 = 3 - \text{rg}(A - 2Id)$. Tenemos que $A - 2Id = \left ( \begin{array}{rrr} 0 & -1 & 1 \\ 0 & -2 & 2 \\ 0 & -1 & 1 \end{array}\right )$, y su rango es igual a $1$. Por consiguiente, $d_2=2$.

Y puesto que la suma de las multiplicidades geométricas es $3$, que es igual al número de filas (o columas) de la matriz $A$, la matriz es diagonalizable.

Una vez comprobado que $A$ es diagonalizable, tenemos que calcular la matriz $P$. Las columnas de esta matriz forman una base de vectores propios de $A$, por lo que lo vamos a calcular una base de cada uno de los subespacios propios.

Comenzamos con el subespacio de valor propio $1$, que viene dado como la solución de un sistema de ecuaciones homogéneo cuya matriz de coeficientes es $A - 1\cdot Id$.

$\left (\begin{array}{rrr} 1 & -1 & 1 \\ 0 & -1 & 2 \\ 0 & -1 & 2 \end{array}\right ) \stackrel{E_{2}(-1)}{\longrightarrow}
\left (\begin{array}{rrr} 1 & -1 & 1 \\ 0 & 1 & -2 \\ 0 & -1 & 2 \end{array}\right ) \stackrel{E_{12}(1)}{\stackrel{E_{32}(1)}{\longrightarrow}}
\left (\begin{array}{rrr} 1 & 0 & -1 \\ 0 & 1 & -2 \\ 0 & 0 & 0 \end{array}\right )$

Tenemos que $V_1 \equiv \left \{ \begin{array}{rrrrrrr} x & & & - & z & = & 0\ \\ & & y & - & 2z & = & 0. \end{array}\right.$ Una base de este subespacio es $B_{V_1} = \{(1,2,1)\}$.

Seguimos con $V_2$. A partir de la matriz $A - 2Id$ vemos que este subespacio viene dado por una ecuación, que es $-y+z=0$. Una base de este subespacio es $B_{V_2} = \{(1,0,0),\ (0,1,1)\}$.

Y ya tenemos las dos matrices que nos pide: la matriz $P$ cuyas columnas son los vectores propios que hemos obtenido, y la matriz $D$ que es una matriz diagonal y que en la diagonal tiene los valores propios (en el mismo orden en que colocamos los vectores en la matriz $P$). Es decir:

$$
P = \left (\begin{array}{rrr} 1 & 1 & 0 \\ 2 & 0 & 1 \\ 1 & 0 & 1 \end{array} \right );\qquad D = \left (\begin{array}{rrr} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 2 \end{array} \right ).
$$


</li>
<li> Tenemos que $P^{-1}A P = D$, luego $A = PDP^{-1}$. Entonces $A^{10} = PD^{10}P^{-1}$. Necesitamos calcular $P^{-1}$ y $D^{10}$. 

$$
\left (\begin{array}{rrrrrr} 1 & 1 & 0 & 1 & 0 & 0 \\ 2 & 0 & 1 & 0 & 1 & 0 \\ 1 & 0 & 1 & 0 & 0 & 1 \end{array} \right ) \stackrel{E_{21}(-2)}{\stackrel{E_{31}(-1)}{\longrightarrow}}
\left (\begin{array}{rrrrrr} 1 & 1 & 0 & 1 & 0 & 0 \\ 0 & -2 & 1 & -2 & 1 & 0 \\ 0 & -1 & 1 & -1 & 0 & 1 \end{array} \right ) \stackrel{E_{23}}{\longrightarrow}
\left (\begin{array}{rrrrrr} 1 & 1 & 0 & 1 & 0 & 0 \\ 0 & -1 & 1 & -1 & 0 & 1  \\ 0 & -2 & 1 & -2 & 1 & 0 \end{array} \right )
\stackrel{E_{12}(1)}{\stackrel{E_{32}(-2)}{\longrightarrow}}
$$

$$
\left (\begin{array}{rrrrrr} 1 & 0 & 1 & 0 & 0 & 1 \\ 0 & -1 & 1 & -1 & 0 & 1  \\ 0 & 0 & -1 & 0 & 1 & -2 \end{array} \right )
\stackrel{E_{13}(1)}{\stackrel{E_{23}(1)}{\longrightarrow}}
\left (\begin{array}{rrrrrr} 1 & 0 & 0 & 0 & 1 & -1 \\ 0 & -1 & 0 & -1 & 1 & -1  \\ 0 & 0 & -1 & 0 & 1 & -2 \end{array} \right )
\stackrel{E_{2}(-1)}{\stackrel{E_{3}(-1)}{\longrightarrow}}
\left (\begin{array}{rrrrrr} 1 & 0 & 0 & 0 & 1 & -1 \\ 0 & 1 & 0 & 1 & -1 & 1  \\ 0 & 0 & 1 & 0 & -1 & 2 \end{array} \right )
$$

Ya tenemos $P^{-1}$. En cuanto a $D^{10}$ se tiene que

$$D^{10} = \left (\begin{array}{rrr} 1 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 2 \end{array} \right )^{10} = \left (\begin{array}{ccc} 1^{10} & 0 & 0 \\ 0 & 2^{10} & 0 \\ 0 & 0 & 2^{10} \end{array} \right ) = \left (\begin{array}{ccc} 1 & 0 & 0 \\ 0 & 1024 & 0 \\ 0 & 0 & 1024 \end{array} \right )
$$

Finalmente:

$$
A^{10} = \left (\begin{array}{ccc} 1 & 1 & 0 \\ 2 & 0 & 1 \\ 1 & 0 & 1 \end{array}\right )
\left (\begin{array}{ccc} 1 & 0 & 0 \\ 0 & 1024 & 0 \\ 0 & 0 & 1024 \end{array}\right )
\left  (\begin{array}{ccc} 0 & 1 & -1 \\ 1 & -1 & 1 \\ 0 & -1 & 2 \end{array}\right )=
\left (\begin{array}{ccc} 1 & 1 & 0 \\ 2 & 0 & 1 \\ 1 & 0 & 1 \end{array}\right ) \left  (\begin{array}{ccc} 0 & 1 & -1 \\ 1024 & -1024 & 1024 \\ 0 & -1024 & 2048 \end{array}\right)
$$

$$
A^{10} = \left  (\begin{array}{ccc} 1024 & -1023 & 1023 \\ 0 & -1022 & 2046 \\ 0 & -1023 & 2047 \end{array}\right)
$$
</li>
</ol>

::::
:::::

:::::{#exr-23 .medio-cuerpo_finito}

Sea $V_2$ el subespacio de $({\mathbb Z}_7)^3$ generado por $(1,1,0)$ y $V_3$ el subespacio de $({\mathbb Z}_7)^3$ de ecuación $y+z=0$.

Sea $A\in M_3({\mathbb Z}_7)$ la matriz cuyos valores propios son $2$ y $3$ y cuyos subespacios propios son $V_2$ y $V_3$ respectivamente.

Calcula las matrices $A$ y $A^{96}$.


:::: {.callout collapse="true" title="Solución"}

Para resolver este ejercicio necesitamos una base de cada uno de los subespacios propios. Como base de $V_2$ tenemos $B_{V_2}=\{(1,1,0)\}$. En cuanto a $V_3$, puesto que viene dado por una ecuación, su dimensión es igual a $3-1=2$. Una base estará formada por dos vectores linealmente independientes que satisfagan la ecuación. Tomamos la siguiente base: $B_{V_3} = \{(1,0,0),\ (0,1,6)\}$.

Por otra parte, la matriz $A$ tiene dos valores propios $\lambda=2$ y $\lambda = 3$. Sus mulitplicidades geométricas son $d_2 = \text{dim}(V_2) = 1$ y $d_3 = \text{dim}(V_3) = 2$. Al ser la suma de las multiplicidades geométricas igual al número de filas (o columnas) de la matriz $A$, la matriz $A$ es diagonalizable.

Esto significa que existe una matriz $P\in M_3({\mathbb Z}_7)$, regular, para la que $P^{-1}\cdot A\cdot P$ es una matriz diagonal (y en la diagonal están los valores propios de $A$, tantas veces como nos indica su multiplicidad).

La matriz $P$ tienen como columnas una base de vectores propios de $A$, por lo que $P = \left (\begin{array}{rrr} 1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 0 & 6 \end{array}\right )$,  mientras que la matriz $D$ es igual a $\left (\begin{array}{rrr} 2 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 3 \end{array}\right )$.

Y tenemos ahora: $P^{-1}\cdot A\cdot P = D \Longrightarrow P\cdot P^{-1}\cdot A \cdot P \cdot P^{-1}= P\cdot D\cdot P^{-1} \Longrightarrow A = P\cdot D \cdot P^{-1}$.

Calculamos $P^{-1}$.

$$
\begin{array}{l}
\quad \left ( \begin{array}{rrrrrr} 1 & 1 & 0 & 1 & 0 & 0 \\ 1 & 0 & 1 & 0 & 1 & 0 \\ 0 & 0 & 6 & 0 & 0 & 1 \end{array}\right ) \stackrel{E_{12}}{\longrightarrow}\left ( \begin{array}{rrrrrr} 1 & 0 & 1 & 0 & 1 & 0 \\ 1 & 1 & 0 & 1 & 0 & 0 \\ 0 & 0 & 6 & 0 & 0 & 1 \end{array}\right ) \\
\stackrel{E_{21}(6)}{\stackrel{E_{3}(6)}{\longrightarrow}} \left ( \begin{array}{rrrrrr} 1 & 0 & 1 & 0 & 1 & 0 \\ 0 & 1 & 6 & 1 & 6 & 0 \\ 0 & 0 & 1 & 0 & 0 & 6 \end{array}\right ) \stackrel{E_{13}(6)}{\stackrel{E_{23}(1)}{\longrightarrow}}  \left ( \begin{array}{rrrrrr} 1 & 0 & 0 & 0 & 1 & 1 \\ 0 & 1 & 0 & 1 & 6 & 6 \\ 0 & 0 & 1 & 0 & 0 & 6 \end{array}\right )
\end{array}
$$

Y multiplicamos:

$P\cdot D =  \left (\begin{array}{rrr} 1 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 0 & 6 \end{array}\right )\cdot \left (\begin{array}{rrr} 2 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 3 \end{array}\right ) = \left (\begin{array}{rrr} 2 & 3 & 0 \\ 2 & 0 & 3 \\ 0 & 0 & 4 \end{array}\right )$

$A = P\cdot D \cdot P^{-1} = \left (\begin{array}{rrr} 2 & 3 & 0 \\ 2 & 0 & 3 \\ 0 & 0 & 4 \end{array}\right )\cdot \left (\begin{array}{rrr} 0 & 1 & 1 \\ 1 & 6 & 6 \\ 0 & 0 & 6 \end{array}\right ) = \left (\begin{array}{rrr} 3 & 6 & 6 \\ 0 & 2 & 6 \\ 0 & 0 & 3 \end{array}\right )$

Por último, calculamos $A^{96}$. Antes, calculamos la matriz $D^{96}$. Al ser una matriz diagonal, para calcularla hay que elevar cada uno de sus coeficientes al exponente $96$.

Por otra parte, $2^6 = 1$ y $3^6=1$, ya que $\varphi(7) = 6$, así que  $2^{96} = (2^6)^{16} = 1^{16} = 1$, e igual para $3^{96}$.

$D^{96} = \left (\begin{array}{rrr} 2^{96} & 0 & 0 \\ 0 & 3^{96} & 0 \\ 0 & 0 & 3^{96} \end{array}\right ) = \left (\begin{array}{rrr} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{array}\right ) = Id$.

Tenemos entonces:

$A^{96} = (P\cdot D\cdot P^{-1})^{96} = P \cdot D^{96} \cdot P^{-1} = P\cdot Id \cdot P^{-1} = Id$.


::::
:::::

:::::{#exr-24 .medio}

Encuentra todos los valores $a\in {\mathbb R}$ para los que la matriz $A=\begin{pmatrix} 2 & 0 & 0 \\3 & 4 & a \\ a & 0 & 4 \end{pmatrix}\in\mathcal{M}_{3\times 3}({\mathbb R})$ es diagonalizable. Para aquellos valores de $a$ en que la matriz $A$ sea diagonalizable, calcula una matriz regular $P$ y una matriz diagonal $D$ tales que $P^{-1}\cdot A\cdot P = D.$


:::: {.callout collapse="true" title="Solución"}

En primer lugar calculamos los valores propios con sus multiplicidades algebraicas. Para eso, calculamos el polinomio característico:

$$p_A(\lambda) = \left | \begin{array}{ccc} 2-\lambda & 0 & 0 \\3 & 4-\lambda & a \\ a & 0 & 4-\lambda\end{array}\right | = (2-\lambda) \cdot \left | \begin{array}{cc} 4-\lambda & a \\ 0 & 4-\lambda \end{array}\right | = (2-\lambda)\cdot (4-\lambda)^2.$$

Vemos que $A$ tiene dos valorer propios: $\lambda_1=2$, cuya multiplicidad algebraica es $1$ y $\lambda_2=4$ cuya multiplicidad algebraica es $2$. Tenemos entonces:

$$
\begin{array}{|c|c|c|}
  \text{Valor propio} & \text{Multiplicidad algebraica} & \text{Multiplicidad geométrica} \\ \hline
  \lambda_1 = 2 & \alpha_2=1 & d_2 = 1 \\ \hline \lambda_2 = 4 & \alpha_4 = 2 & d_4 = 1 \text{ ó } 2 \\ \hline \end{array}$$

La matriz $A$ es entonces diagonalizable si $d_4=2$. Puesto que $d_4 = 3 - \text{rg}(A-4\cdot Id)$, estudiamos esta matriz.

$$
A - 4\cdot Id = \left (\begin{array}{rrr}  -2 & 0 & 0 \\3 & 0 & a \\ a & 0 & 0 \end{array}\right ).$$

Si $a=0$ la matriz $A-4\cdot Id$ tiene solo una columna distinta de cero, luego $\text{rg}(A-4\cdot Id)=1$, mientras que si $a\neq 0$ encontramos una submatriz $2\times 2$ (la formada por las filas primera y segunda, y columnas primera y tercera) cuyo determinante es $-2a \neq 0$, por lo que $\text{rg}(A-4\cdot Id) = 2$. En resumen, tenemos:

<ul>
  <li> Si $a=0$, $d_4 = 3-\text{rg}(A-4\cdot Id) = 3-1=2$, por lo que $A$ es diaogonalizable. </li>
  <li> Si $a\neq 0$, $d_4=3-\text{rg}(A-4\cdot Id) = 3-2=1$, por lo que $A$ no es diagonalizable.</li>
</ul>

En conclusión, $A$ es diagonalizable si, y solo si, $a=0$. Vamos en este caso a calcular los vectores propios.

<ul>
  <li> Para el valor propio $2$, y puesto que $A-2\cdot Id = \left (\begin{array}{rrr}  0 & 0 & 0 \\3 & 2 & 0 \\ 0 & 0 & 2 \end{array}\right )$, el subespacio $V_2$ tiene ecuaciones:

  $$
  V_2 \equiv \left\{ \begin{array}{rrrrrr} 3x & + & 2y & & = & 0 \\ & &  & 2z & = & 0 \end{array}\right.
  $$

  Y una base de $V_2$ es $B_{V_2} = \{(2,-3,0)\}$.
  
  </li>
  <li> Para el valor propio $4$, y puesto que $A-4\cdot Id = \left (\begin{array}{rrr}  -2 & 0 & 0 \\3 & 0 & 0 \\ 0 & 0 & 0 \end{array}\right )$, el subespacio $V_4$ tiene ecuación $V_4 \equiv x = 0$. Una base es $B_{V_4} = \{(0,1,0),\ (0,0,1)\}$.</li>
</ul>

Con estas bases formamos la matriz $P=\left (\begin{array}{rrr} 2 & 0 & 0 \\ -3 & 1 & 0 \\ 0 & 0 & 1 \end{array} \right )$ (sus columnas son los vectores propios que hemos encontrado). Se tiene que:

$$
P^{-1}\cdot A \cdot P = \left (\begin{array}{ccc} 2& 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 4 \end{array}\right ).
$$

Y esta última es la matriz $D$ que  nos piden.


::::
:::::

:::::{#exr-25 .basico}

Sea $f:{\mathbb R}^3\rightarrow {\mathbb R}^3$ la aplicación lineal dada por
$$
f(x,y,z) = (-2x+z,-x-y+z,-2x+z).
$$

Y sea $A=M_{B_c}(f)$.

<ol type="a">
<li> Halla la matriz $A$.</li>
<li> Calcula los valores propios de $A$.</li>
<li> Calcula una base de vectores propios de $A$. Llama a esta base $B$.</li>
<li> Calcula $M_{B}(f)$.</li>
<li> Calcula las ecuaciones cartesianas de $\text{Im}(f)$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li> Tenemos que $f(1,0,0) = (-2,-1,-2)$, $f(0,1,0) = (0,-1,0)$ y $f(0,0,1) = (1,1,1)$. Por tanto:

$$
A = M_B(f) = \left (\begin{array}{rrr} -2 & 0 & 1 \\ -1 & -1 & 1 \\ -2 & 0 & 1 \end{array}\right ).
$$

</li>
<li> Calculamos el polinomio característico de $A$:

$$
\begin{array}{lll}
p_A(\lambda) & = & \left | \begin{array}{ccc} -2-\lambda & 0 & 1 \\ -1 & -1-\lambda & 1 \\ -2 & 0 & 1-\lambda  \end{array}\right | \\ & & \\
& = & (-1-\lambda)\left | \begin{array}{cc} -2-\lambda & 1 \\ -2 & 1-\lambda  \end{array}\right | \\ & & \\
& = & (-1-\lambda) ((-2-\lambda)(1-\lambda) - (-2)) \\ & & \\
& = & (-1-\lambda)(-2+2\lambda-\lambda+\lambda^2+2) \\ & & \\
& = & (-1-\lambda)(\lambda^2+\lambda) \\ & & \\
& = & (-1-\lambda)\lambda (\lambda+1) \\ & & \\
& = & -\lambda(\lambda+1)^2\end{array} 
$$

La matriz $A$ tiene dos valores propios: $\lambda=0$, con multiplicidad algebraica $1$ y $\lambda=-1$ con multiplicidad algebraica $2$.
</li>
<li> Calculamos una base de cada uno de los subespacios propios, y las unimos:
  <ul>
  <li> Subespacio $V_0$. Este subespacio viene definido por un sistema de ecuaciones cuya matriz de coeficientes es $A-0Id = A$. Resolvemos el sistema:
$$
\begin{array}{c}
\left (\begin{array}{rrr} -2 & 0 & 1 \\ -1 & -1 & 1 \\ -2 & 0 & 1 \end{array}\right )
  \stackrel{\stackrel{E_{12}(-3)}{}}{\longrightarrow}
\left (\begin{array}{rrr} 1 & 3 & -2 \\ -1 & -1 & 1 \\ -2 & 0 & 1 \end{array}\right )
  \stackrel{\stackrel{E_{21}(1)}{\stackrel{E_{31}(2)}{}}}{\longrightarrow}
\left (\begin{array}{rrr} 1 & 3 & -2 \\ 0 & 2 & -1 \\ 0 & 6 & -3 \end{array}\right ) \\ \\
\stackrel{\stackrel{E_{12}\left (\frac{1}{2}\right )}{}}{\longrightarrow}
\left (\begin{array}{rrr} 1 & 3 & -2 \\ & & \\ 0 & 1 & \frac{-1}{2} \\ & & \\ 0 & 6 & -3 \end{array}\right )
  \stackrel{\stackrel{E_{12}(-3)}{\stackrel{E_{32}(-6)}{}}}{\longrightarrow}
\left (\begin{array}{rrr} 1 & 0 & \frac{-1}{2} \\ & & \\ 0 & 1 & \frac{-1}{2} \\ & & \\ 0 & 0 & 0 \end{array}\right ) \end{array}
$$

Luego $V_0\equiv \left\{ \begin{array}{rrrrrrr} x & & & - & \frac{1}{2} z & = & 0 \\ &&&&&& \\ & & y & - & \frac{1}{2}z & = & 0 \end{array}\right.$, es decir, $V_0\equiv \left\{ \begin{array}{rrr} x & = & \frac{z}{2}  \\ & & \\ y & = & \frac{z}{2} \end{array}\right.$

Una base de $V_0$ la obtenemos dándole a $z$ el valor $2$, y nos queda $B_{V_0}=\{(1,1,2)\}$. 

  </li>
  <li> Subespacio $V_{-1}$. Repetimos lo el apartado anterior pero con la matriz $A-(-Id) = A+Id$.
$$
\left (\begin{array}{rrr} -1 &0 & 1 \\ 0 & 0 & 0 \\ -2 & 0 & 2 \end{array}\right )
  \stackrel{\stackrel{E_{1}(-1)}{}}{\longrightarrow}
\left (\begin{array}{rrr} 1 &0 & -1 \\ 0 & 0 & 0 \\ -2 & 0 & 2 \end{array}\right )
  \stackrel{\stackrel{E_{31}(2)}{}}{\longrightarrow}
\left (\begin{array}{rrr} 1 &0 & -1 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{array}\right )
$$

$V_{-1}\equiv x-z=0$, luego $\text{dim}(V_{-1}) = 2$ y una base es $B_{V_{1}}=\{(1,0,1),\ (0,1,0)\}$.

  </li>
  </ul>
La base $B$ se obtiene uniendo ambas bases: $B=\{(1,1,2),\ (1,0,1),\ (0,1,0)\}$.

</li>
<li> Calculamos la imagen de los tres vectores de $B$:
<ul>
  <li> $f(1,1,2) = (0,0,0)$.</li>

  <li> $f(1,0,1) = (-2+1,-1+1,-2+1) = (-1,0,-1) = 0\cdot (1,1,2) -1\cdot (1,0,1) + 0\cdot (0,1,0)$.</li>

  <li> $f(0,1,0) = (0,-1,0) = 0\cdot (1,1,2) + 0\cdot (1,0,1) -1\cdot (0,1,0)$.</li>
</ul>

Luego $M_B(f) = \left (\begin{array}{rrr} 0 & 0 & 0 \\ 0 & -1 & 0 \\ 0 & 0 & -1 \end{array}\right )$.

</li>
<li> Sabemos que $\text{dim}(Im(f)) = 2$ (pues $\text{rg}(A)=2$). Además, los vectores de $V_{-1}$ pertenecen a $\text{Im}(f)$. Por tanto, tenemos que  $\text{Im}(f)=V_{-1}$. Las ecuaciones están calculadas más arriba: $\text{Im}(f) \equiv x-z=0$.

</li>
</ol>

::::
:::::



<!-- ::::: {.test}
<iframe src="/assets/autoevaluacion/AutoevaluacionDS.html" style="border:none;" height="1000" width="100%" title="Autoevaluación"></iframe>
::::: -->

::::: {.test-cuerpo_finito}
<iframe src="/assets/autoevaluacion/AutoevaluacionDS-CF.html" style="border:none;" height="765" width="100%" title="Autoevaluación CF"></iframe> 
:::::