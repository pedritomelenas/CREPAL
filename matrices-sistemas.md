---
title: Matrices y sistemas de ecuaciones
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
<input type="checkbox" id="casilla_cf" value="cuerpo_finitoon" checked onclick="mostrar();"> Mostrar ejercicios sobre cuerpos finitos. &nbsp;
<input type="checkbox" id="casilla_basico" value="basicoon" checked onclick="mostrar();"> Básicos. &nbsp;
<input type="checkbox" id="casilla_medio" value="medioon" checked onclick="mostrar();"> Dificultad media. &nbsp; 
<input type="checkbox" id="casilla_avanzado" value="avanzadon" checked onclick="mostrar();"> Avanzados. 


::::: {#exr-1 .basico}
Resuelve el siguiente sistema de ecuaciones lineales considerado en $\mathbb{Q}$[, $\mathbb{Z}_3$ y $\mathbb{Z}_5$]{.cuerpo_finito}.

$$\left\{\begin{aligned} x_{2}-2x_{3}&= -4,\\ x_{1}+x_{2}-x_{3}&=0,\\ 2x_{1}-x_{2}+x_{3}&=3. \end{aligned}\right.$$

::::{.callout collapse="true" title="Solución"}

Usaremos el método de Gauss-Jordan, que consiste en encontrar la forma escalonada reducida del sistema de ecuaciones. Trabajaremos directamente en la matriz de coeficientes ampliada. 

:::{.cuerpo_finito}
**Coeficientes en $\mathbb{Q}$**
:::

En primer lugar buscamos el pivote en la primera posición de la fila uno, en este caso intercambiando las posiciones de las ecuaciones una y dos:

$$\left(\begin{array}{ccc|c}
0 & 1 & -2 & -4\\
1 & 1 & -1 & 0\\
2 & -1 & 1 & 3
\end{array}\right)\sim_{f_1\rightarrow f_2} 
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & -1 & 0\\
0 & 1 & -2 & -4\\
2 & -1 & 1 & 3
\end{array}\right).$$

Ahora utilizamos el pivote para hacer ceros debajo de él, por medio de una operación elemental del tipo: a la fila $j$ se le resta la fila uno multiplicada por el coeficiente $a_{j1}$. En este caso solo hay que realizarlo para la fila tres:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 1 & -1 & 0\\
0 & 1 & -2 & -4\\
2 & -1 & 1 & 3
\end{array}\right)
\sim_{f_3-2f_1\rightarrow f_3}  
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & -1 & 0\\
0 & 1 & -2 & -4\\
0 & -3 & 3 & 3
\end{array}\right).$$

Ahora procedemos de un modo similar con el pivote de la segunda ecuación, que ya está en la posición deseada, con él hacemos cero todos los elementos que están en su columna, tanto debajo como encima:

$$  
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & -1 & 0\\
0 & \boxed{1} & -2 & -4\\
0 & -3 & 3 & 3
\end{array}\right)\sim_{f_1-f_2\rightarrow f_1}  
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & -2 & -4\\
0 & -3 & 3 & 3
\end{array}\right)\sim_{f_3+3f_2\rightarrow f_3}  
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & -2 & -4\\
0 & 0 & -3 & -9
\end{array}\right).$$

Por último, normalizamos la tercera fila dividiéndola por menos tres:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & -2 & -4\\
0 & 0 & -3 & -9
\end{array}\right)
\sim_{-\frac{1}{3}f_3\rightarrow f_3}\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & -2 & -4\\
0 & 0 & \boxed{1} & 3
\end{array}\right).$$

Por último usamos este pivote para hacer ceros el resto de entradas de su columna:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & -2 & -4\\
0 & 0 & \boxed{1} & 3
\end{array}\right)
\sim_{f_1-f_3\rightarrow f_1}\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 0 & 1\\
0 & \boxed{1} & -2 & -4\\
0 & 0 & \boxed{1} & -3
\end{array}\right)\sim_{f_2+2f_3\rightarrow f_2}\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 0 & 1\\
0 & \boxed{1} & 0 & 2\\
0 & 0 & \boxed{1} & 3
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[0,1,-2],[1,1,-1],[2,-1,1]]) #matriz de coeficientes
b=vector(QQ,[-4,0,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::


El sistema asociado a esta matriz tiene exactamente las mismas soluciones que el de partida (son sistemas equivalentes), y ha quedado de la siguiente manera:

$$
\left\{\begin{aligned}
x_{1}&= 1,\\
x_{2}&=2,\\
x_{3}&=3.
\end{aligned}\right.
$$

Luego es un sistema compatible determinado, y su única solución es $$(1,2,3).$$

:::{.cuerpo_finito}
**Coeficientes en $\mathbb{Z}_3$**

En primer lugar vamos a substituir los coeficientes por representantes en $\{0,1,2\}$:

$$\left(\begin{array}{ccc|c}
0 & 1 & 1 & 2\\
1 & 1 & 2 & 0\\
2 & 2 & 1 & 0
\end{array}\right).$$

Y ahora calculamos la forma escalonada reducida por filas de esa matriz. Buscamos un pivote para la primera columna, que puede ser perfectamente el primer elemento de la segunda fila.

$$\left(\begin{array}{ccc|c}
0 & 1 & 1 & 2\\
1 & 1 & 2 & 0\\
2 & 2 & 1 & 0
\end{array}\right)\sim_{f_1\rightarrow f_2}\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 2 & 0\\
0 & 1 & 1 & 2\\
2 & 2 & 1 & 0
\end{array}\right).$$

Para eliminar la otra entrada no nula de la primera columna, que está en la tercera fila, multiplicamos la primera por $-2$ y se lo sumamos a la última fila. Como $-2$ módulo $3$ es $1$, esto equivale a sumarle a la tercera la primera fila.

$$\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 2 & 0\\
0 & 1 & 1 & 2\\
2 & 2 & 1 & 0
\end{array}\right)\sim_{f_3+f_1\rightarrow f_3}\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 2 & 0\\
0 & 1 & 1 & 2\\
0 & 0 & 0 & 0
\end{array}\right).$$

Ahora señalamos (ya está hecho) el pivote de la segunda fila y lo usamos para hacer cero el resto de posiciones de su columna:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 2 & 0\\
0 & \boxed{1} & 1 & 2\\
0 & 0 & 0 & 0
\end{array}\right)\sim_{f_1+2f_2\rightarrow f_1}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 1\\
0 & \boxed{1} & 1 & 2\\
0 & 0 & 0 & 0
\end{array}\right).
$$

Obtenemos así la forma escalonada reducida de nuestra matriz de coeficientes ampliada. 


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(3),[[0,1,-2],[1,1,-1],[2,-1,1]]) #matriz de coeficientes
b=vector(GF(3),[-4,0,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

Puesto que la tercera fila ha quedado $0=0$, la correspondiente ecuación  se puede eliminar, quedando el siguiente sistema que es equivalente al de partida:

$$
\left\{\begin{aligned}
x_{1}+x_3&= 1,\\
x_{2}+x_3&=2.\\
\end{aligned}\right.
$$

Donde podemos despejar $x_1$ y $x_2$ (que son las incógnitas que corresponden con los pivotes) y usar $x_3$ como parámetro (la incógnita restante), quedando las soluciones parametrizadas de la siguiente forma:

$$
\left.\begin{aligned}
x_{1}&= 1+2\lambda\\
x_{2}&=2+2\lambda\\
x_3&=\lambda 
\end{aligned}\right\}, \lambda \in \mathbb{Z}_3.
$$

Luego este sistema tiene el siguiente conjunto de soluciones:

$$\{ (1,2,0), (0,1,1),(2,0,2)\}.$$

Por tanto, en el caso de tomar coeficientes en $\mathbb{Z}_3$, obtenemos un sistema compatible indeterminado.

**Coeficientes en $\mathbb{Z}_5$**

En primer lugar vamos a sustituir los coeficientes por sus respectivos  representantes en $\{0,1,2,3,4\}$:

$$\left(\begin{array}{ccc|c}
0 & 1 & 3 & 1\\
1 & 1 & 4 & 0\\
2 & 4 & 1 & 3
\end{array}\right).$$

Procedemos com en los casos anteriores, buscando un pivote con el que reducir la primera columna.

$$\left(\begin{array}{ccc|c}
0 & 1 & 3 & 1\\
1 & 1 & 4 & 0\\
2 & 4 & 1 & 3
\end{array}\right)
\sim_{f_1\rightarrow f_2}\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 4 & 0\\
0 & 1 & 3 & 1\\
2 & 4 & 1 & 3
\end{array}\right) \sim_{f_3+3f_1\rightarrow f_3}\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 4 & 0\\
0 & \boxed{1} & 3 & 1\\
0 & 2 & 3 & 3
\end{array}\right).$$

Procedemos con la segunda fila (y columna):

$$\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 4 & 0\\
0 & \boxed{1} & 3 & 1\\
0 & 2 & 3 & 3
\end{array}\right)
\sim_{f_1+4f_2\rightarrow f_1}\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & 3 & 1\\
0 & 2 & 3 & 3
\end{array}\right)\sim_{f_3+3f_2\rightarrow f_3}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & 2 & 1
\end{array}\right).
$$

Teniendo en cuenta que $2^{-1}=3$ en $\mathbb{Z}_5$:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & 2 & 1
\end{array}\right)\sim_{3f_3\rightarrow f_3}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & \boxed{1} & 3
\end{array}\right).
$$

Por último usamos este pivote para hacer todos los ceros que sea posible:

$$\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 4\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & \boxed{1} & 3
\end{array}\right)\sim_{f_1+4f_3\rightarrow f_1}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 0 & 1\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & \boxed{1} & 3
\end{array}\right)\sim_{f_2+2f_3\rightarrow f_2}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 0 & 1\\
0 & \boxed{1} & 0 & 2\\
0 & 0 & \boxed{1} & 3
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[0,1,-2],[1,1,-1],[2,-1,1]]) #matriz de coeficientes
b=vector(GF(5),[-4,0,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

Nos ha quedado el sistema (equivalente al original):

$$
\left\{\begin{aligned}
x_{1}&= 1,\\
x_{2}&=2,\\
x_{3}&=3.
\end{aligned}\right.
$$

Luego este sistema tiene una única solución:

$$(1,2,3),$$

y de esta forma es compatible determinado.
:::
::::
:::::

::::: {#exr-2 .basico}

Resuelve el siguiente sistema de ecuaciones lineales considerado en $\mathbb{Q}$[, $\mathbb{Z}_3$, $\mathbb{Z}_5$ y $\mathbb{Z}_2$]{.cuerpo_finito}.

$$\left\{\begin{aligned} x-y+z+t+v&=0,\\ x+y+z+t-v&=0,\\ -x-y+z+t-v&=0. \end{aligned}\right.$$

:::: {.callout collapse="true" title="Solución"}


Este sistema es homogéneo, es decir, la columna de términos independientes es entera de ceros. Puesto que las operaciones elementales en esa columna siempre la mantienen igual, solo escribiremos la matriz de coeficientes. 
Además, un sistema homogéneo siempre es Compatible puesto que admite la solución $(0,0,0,0,0)$.

:::{.cuerpo_finito}
**Coeficientes en $\mathbb{Q}$**
:::

$$
\left(\begin{array}{rrrrr}
\boxed{1} & -1 & 1 & 1 & 1\\
1 & 1 & 1 & 1 & -1\\
-1 & -1 & 1 & 1 & -1
\end{array}\right)\sim_{\tiny \begin{array}{l} f_2-f_1\rightarrow f_2\\
f_3+f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{rrrrr}
\boxed{1} & -1 & 1 & 1 & 1\\
0 & 2 & 0 & 0 & -2\\
0 & -2 & 2 & 2 & 0
\end{array}\right).
$$

Podemos tomar como pivote el segundo elemento de la segunda fila o utilizarla antes para hacer cero en la posición $(3,2)$. Estaríamos apartándonos del método de Gauss-Jordan, pero al ser la forma de escalonada reducida por filas de la matriz única, no importa cuál es el camino para obtenerla.

$$
\left(\begin{array}{rrrrr}
\boxed{1} & -1 & 1 & 1 & 1\\
0 & 2 & 0 & 0 & -2\\
0 & -2 & 2 & 2 & 0
\end{array}\right)
\sim_{f_3+f_2\rightarrow f_3}  
\left(\begin{array}{rrrrr}
\boxed{1} & -1 & 1 & 1 & 1\\
0 & 2 & 0 & 0 & -2\\
0 & 0 & 2 & 2 & -2
\end{array}\right).
$$

Ahora sí tomamos como pivote el segundo elemento de la segunda fila y con él hacemos cero todos los elementos que están en su columna; después continuamos con el pivote de la tercera fila:

$$
\left(\begin{array}{rrrrr}
\boxed{1} & -1 & 1 & 1 & 1\\
0 & 2 & 0 & 0 & -2\\
0 & 0 & 2 & 2 & -2
\end{array}\right)
\sim_{\tiny \begin{array}{l} \frac{1}{2}f_2\rightarrow f_2\\
f_1+f_2\rightarrow f_1 \end{array}}\left(\begin{array}{rrrrr}
\boxed{1} & 0 & 1 & 1 & 0\\
0 & \boxed{1} & 0 & 0 & -1\\
0 & 0 & 2 & 2 & -2
\end{array}\right)\sim_{\tiny \begin{array}{l} \frac{1}{2}f_3\rightarrow f_3 \\f_1-f_3\rightarrow f_1 \end{array}} 
\left(\begin{array}{rrrrr}
\boxed{1} & 0 & 0 & 0 & 1\\
0 & \boxed{1} & 0 & 0 & -1\\
0 & 0 & \boxed{1} & 1 & -1
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,-1,1,1,1],[1,1,1,1,-1],[-1,-1,1,1,-1]])
show(A,"~",A.rref())
</script>
:::

Como ya tenemos una matriz escalonada reducida por filas, el sistema no puede simplificarse más. Solo queda escribir las soluciones: para ello observamos que las incógnitas $x,y$ y $z$ están listas para ser despejadas, son las que corresponden a los pivotes. Las que no corresponden a pivotes se utilizan como parámetros (o variables libres). La solución del sistema queda:  

$$
\left.\begin{aligned}
x&=-\lambda_2\\
y&=\lambda_2\\
z&=-\lambda_1+\lambda_2\\
t&=\lambda_1 \\
v&=\lambda_2 
\end{aligned}\right\},   \lambda_1, \lambda_2 \in \mathbb{Q}.
$$

Luego es un sistema compatible Indeterminado.

:::{.cuerpo_finito}
**Coeficientes en $\mathbb{Z}_3$**

Este ejemplo es un caso muy especial, puesto que todos los coeficientes del sistema son unos y menos unos (también podrían haber sido ceros y razonaríamos igual), y estos elementos se pueden usar en cualquier cuerpo en el que $1\not = -1$. 

Si repasamos las operaciones utilizadas, son también válidas en $\mathbb{Z}_3$ y en $\mathbb{Z}_5$ (aunque multiplicar por $\frac{1}{2}$ correspondería a multiplicar por $2$ en $\mathbb{Z}_3$ o por $3$ en $\mathbb{Z}_5$).

Comprobemos el razonamiento con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(3),[[1,-1,1,1,1],[1,1,1,1,-1],[-1,-1,1,1,-1]])
show(A,"~",A.rref())
</script>
:::


Las soluciones en $\mathbb{Z}_3$ serían

$$
\left.\begin{aligned}
x&=2\lambda_2\\
y&=\lambda_2\\
z&=2\lambda_1+\lambda_2\\
t&=\lambda_1 \\
v&=\lambda_2 
\end{aligned}\right\},  \lambda_1, \lambda_2 \in \mathbb{Z}_3,
$$

y por tanto es compatible indeterminado y tiene un total de $9$ soluciones.

**Coeficientes en $\mathbb{Z}_5$**

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[1,-1,1,1,1],[1,1,1,1,-1],[-1,-1,1,1,-1]])
show(A,"~",A.rref())
</script>
:::

Como hemos comentado, la matriz escalonada reducida es la misma, luego las soluciones son:

$$
\left.\begin{aligned}
x&=4\lambda_2\\
y&=\lambda_2\\
z&=4\lambda_1+\lambda_2\\
t&=\lambda_1 \\
v&=\lambda_2 
\end{aligned}\right\},  \ \lambda_1, \lambda_2 \in \mathbb{Z}_5,
$$

y por tanto es compatible indeterminado y tiene un total de $25$ soluciones.

**Coeficientes en $\mathbb{Z}_2$**

$$
\left(\begin{array}{ccccc}
\boxed{1} & 1 & 1 & 1 & 1\\
1 & 1 & 1 & 1 & 1\\
1 & 1 & 1 & 1 & 1
\end{array}\right)\sim_{\tiny \begin{array}{l} f_2-f_1\rightarrow f_2\\
f_3-f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{ccccc}
\boxed{1} & 1 & 1 & 1 & 1\\
0 & 0 & 0 & 0 & 0\\
0 & 0 & 0 & 0 & 0
\end{array}\right),
$$

luego la única incógnita despejada sería $x$, y las soluciones dependerían de $4$ parámetros:

$$
\left.\begin{aligned}
x&=\lambda_1+\lambda_2+\lambda_3+\lambda_4\\
y&=\lambda_1\\
z&=\lambda_2\\
t&=\lambda_3 \\
v&=\lambda_4 
\end{aligned}\right\},  \lambda_i \in \mathbb{Z}_2,\ i\in\{1,2,3,4\},
$$

luego es compatible indeterminado y tiene un total de $2^4=16$ soluciones.
:::
::::
:::::


::::: {#exr-3 .basico}

Resuelve el siguiente sistema de ecuaciones lineales considerado en $\mathbb{Q}$[, $\mathbb{Z}_3$, $\mathbb{Z}_5$ y $\mathbb{Z}_7$]{.cuerpo_finito}.

$$\left\{\begin{aligned} x_{1}+x_{2}+x_{3}&= 2,\\ x_{1}+2x_{2}+x_{3}&=1,\\ x_{2}&=3. \end{aligned}\right.$$

:::: {.callout collapse="true" title="Solución"}


Trabajaremos directamente con la matriz de coeficientes ampliada, buscando en cada caso la forma escalonada reducida por filas.

:::{.cuerpo_finito}
**En $\mathbb{Z}_7$:**

$$
\begin{aligned}\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
1 & 2 & 1 & 1\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{f_2-f_1\rightarrow f_2}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
0 & \boxed{1} & 0 & 6\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-f_2\rightarrow f_2\\
f_3-f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 & 6\\
0 & 0 & 0 &  4
\end{array}\right)\\
\sim_{2f_3\rightarrow f_3} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 &  6\\
0 & 0 & 0 & 1\\
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2-6f_3\rightarrow f_2 \end{array}}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 0\\
0 & \boxed{1} & 0 &  0\\
0 & 0 & 0 & \boxed{1}\\
\end{array}\right).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(7),[[1,1,1],[1,2,1],[0,1,0]]) #matriz de coeficientes
b=vector(GF(7),[2,1,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

En el último paso no hemos escrito las operaciones elementales puesto que se da una circunstancia muy especial: el único elemento no nulo es el pivote. Eso hace que operar con esta fila sea muy sencillo, solo borra los elementos de su columna sin cambiar nada más.

Como hay un pivote en la columna de términos independientes (es decir, aparece la ecuación $0=1$) entonces el sistema es incompatible.

**En $\mathbb{Z}_5$:**

$$\begin{aligned}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
1 & 2 & 1 & 1\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{f_2-f_1\rightarrow f_2}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
0 & \boxed{1} & 0 & 4\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-f_2\rightarrow f_2\\
f_3-f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 & 4\\
0 & 0 & 0 &  4
\end{array}\right)\\
\sim_{4f_3\rightarrow f_3} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 &  4\\
0 & 0 & 0 & 1\\
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2-4f_3\rightarrow f_2 \end{array}}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 0\\
0 & \boxed{1} & 0 &  0\\
0 & 0 & 0 & \boxed{1}\\
\end{array}\right).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[1,1,1],[1,2,1],[0,1,0]]) #matriz de coeficientes
b=vector(GF(5),[2,1,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

Como hay un pivote en la columna de términos independientes (es decir, aparece la ecuación $0=1$), el sistema es incompatible.

**En $\mathbb{Z}_3$:**

$$\begin{aligned}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
1 & 2 & 1 & 1\\
0 & 1 & 0 &  0
\end{array}\right)\sim_{f_2-f_1\rightarrow f_2}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
0 & \boxed{1} & 0 & 4\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-f_2\rightarrow f_2\\
f_3-f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 & 4\\
0 & 0 & 0 &  4
\end{array}\right)\\
\sim_{4f_3\rightarrow f_3} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 &  4\\
0 & 0 & 0 & 1\\
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2-4f_3\rightarrow f_2 \end{array}}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 0\\
0 & \boxed{1} & 0 &  0\\
0 & 0 & 0 & \boxed{1}\\
\end{array}\right).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(3),[[1,1,1],[1,2,1],[0,1,0]]) #matriz de coeficientes
b=vector(GF(3),[2,1,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

Como hay un pivote en la columna de términos independientes (es decir, aparece la ecuación $0=1$), el sistema es incompatible.

**En $\mathbb{Q}$:**
:::


$$\begin{aligned}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
1 & 2 & 1 & 1\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{f_2-f_1\rightarrow f_2}
\left(\begin{array}{ccc|c}
\boxed{1} & 1 & 1 & 2\\
0 & \boxed{1} & 0 & -1\\
0 & 1 & 0 &  3
\end{array}\right)\sim_{\tiny \begin{array}{l} f_1-f_2\rightarrow f_2\\
f_3-f_1\rightarrow f_3 \end{array}} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 & -1\\
0 & 0 & 0 &  4
\end{array}\right)\\
\sim_{\frac{1}{4}f_3\rightarrow f_3} 
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 3\\
0 & \boxed{1} & 0 &  -1\\
0 & 0 & 0 & 1\\
\end{array}\right)
\sim_{\tiny \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2+f_3\rightarrow f_2 \end{array}}
\left(\begin{array}{ccc|c}
\boxed{1} & 0 & 1 & 0\\
0 & \boxed{1} & 0 &  0\\
0 & 0 & 0 & \boxed{1}\\
\end{array}\right).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,1,1],[1,2,1],[0,1,0]]) #matriz de coeficientes
b=vector(QQ,[2,1,3]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::

Como hay un pivote en la columna de términos independientes (es decir, aparece la ecuación $0=1$), el sistema es incompatible.
::::
:::::

::::: {#exr-4 .cuerpo_finito-basico}

En el cuerpo $\mathbb{Z}_5$ se considera la matriz
$$C = \begin{pmatrix} 1&1&1&1 \\ 0&2&1&2 \\ 0&4&1&1 \\ \end{pmatrix}.$$

<ol type="a">
  <li>Calcula la forma de Hermite por filas de $C$.</li>
  <li>Calcula la forma de Hermite por columnas de $C$.</li>
  <li>Elige una submatriz cuadrada de $C$ de orden tres que sea regular y calcula su inversa.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Forma de Hermite por filas.
Realizamos operaciones elemntales por filas hasta obtener una matriz escalonada reducida por filas:

$$
\begin{aligned}
\left( 
\begin{array}{rrrr}
\boxed{1} & 1 & 1 & 1\\
0 & 2 & 1 & 2\\
0 & 4 & 1 & 1\\
\end{array}
\right) & \sim_{\begin{array}{l} 3f_2\rightarrow f_2\end{array}}
\left(
\begin{array}{rrrr}
\boxed{1} & 1 & 1 & 1\\
0 & 1 & 3 & 1\\
0 & 4 & 1 & 1\\
\end{array}
\right)\sim_{ \begin{array}{l} f_3-4f_2\rightarrow f_3\end{array}}
\left( 
\begin{array}{rrrr}
\boxed{1} & 0 & 3 & 0\\
0 & \boxed{1} & 3 & 1\\
0 & 0 & 4 & 2\\
\end{array}
\right) \\
& \sim_{ \begin{array}{l} 4f_3\rightarrow f_3\end{array}}
\left( 
\begin{array}{rrrr}
\boxed{1} & 0 & 3 & 0\\
0 & \boxed{1} & 3 & 1\\
0 & 0 &\boxed{1} & 3\\
\end{array}
\right)\sim_{ \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2-3f_3\rightarrow f_2 \end{array}}
\left(
\begin{array}{rrrr}
\boxed{1} & 0 & 0 & 1\\
0 &\boxed{1} & 0 & 2\\
0 & 0 & \boxed{1} & 3\\
\end{array}
\right).
\end{aligned}
$$

Por tanto la forma de Hermite por filas es 

$$
\left( 
\begin{array}{rrrr}
1 & 0 & 0 & 1\\
0 & 1 & 0 & 2\\
0 & 0 & 1 & 3\\
\end{array}
\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[1,1,1,1],[0,2,1,2],[0,4,1,1]])
show(A,"~",A.rref())
</script>
:::

</li>

<li>Forma de Hermite por columnas.
Como el número de pivotes en la forma de Hermite por columnas coincide con el que hay en la de filas, entonces la única posibilidad es que sea 
$$
\left( 
\begin{array}{rrrr}
\boxed{1} & 0 & 0 & 0\\
0 & \boxed{1} & 0 & 0\\
0 & 0 & \boxed{1} & 0\\
\end{array}
\right).
$$

Comprobemos el resultado obtenido con <code>sage</code> (para eso transponemos la matriz, calculamos su forma escalonada reducida por filas, y volvemos a transponer).

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[1,1,1,1],[0,2,1,2],[0,4,1,1]])
show(A,"~",(A.T).rref().T)
</script>
:::

</li>


<li>Una submatriz cuadrada de orden tres regular y su inversa.
Hay cuatro elecciones posibles. Solo damos un ejemplo de cómo calcularlo.
Elegimos por ejemplo las tres primeras columnas (como el determinante vale $2-4=-2=3$ en  $\mathbb{Z}_5$, es regular) y unimos una matriz identidad a la derecha. Para calcular la inversa realizamos operaciones elementales por filas en las filas de $(A\mid I)$:

$$
\begin{aligned}
(A \mid I)& =\left( 
\begin{array}{rrr|rrr}
\boxed{1} & 1 & 1 & 1 & 0 & 0\\
0 & 2 & 1 & 0 & 1 & 0\\
0 & 4 & 1 & 0 & 0 & 1\\
\end{array}
\right)\sim_{ \begin{array}{l} 3f_2\rightarrow f_2\end{array}}
\left( 
\begin{array}{rrr|rrr}
\boxed{1} & 1 & 1 & 1 & 0 & 0\\
0 & \boxed{1} & 3 & 0 & 3 & 0\\
0 & 4 & 1 & 0 & 0 & 1\\
\end{array}
\right) \sim_{ \begin{array}{l} f_3-4f_2\rightarrow f_3\end{array}} 
\left(
\begin{array}{rrr|rrr}
\boxed{1} & 0 & 3 & 1 & 2 & 0\\
0 & \boxed{1} & 3 & 0 & 3 & 0\\
0 & 0 & 4 & 0 & 3 & 1\\
\end{array}
\right)  \\
& \sim_{ \begin{array}{l} 4f_3\rightarrow f_3\end{array}}
\left(
\begin{array}{rrr|rrr}
\boxed{1} & 0 & 3 & 1 & 2 & 0\\
0 & \boxed{1} & 3 & 0 & 3 & 0\\
0 & 0 & \boxed{1} & 0 & 2 & 4\\
\end{array}
\right) \sim_{ \begin{array}{l} f_1-3f_3\rightarrow f_1\\
f_2-3f_3\rightarrow f_2 \end{array}}
\left( 
\begin{array}{rrr|rrr}
\boxed{1} & 0 & 0 & 1 & 1 & 3\\
0 & \boxed{1} & 0 & 0 & 2 & 3\\
0 & 0 & \boxed{1} & 0 & 2 & 4\\
\end{array}
\right)=(I\mid A^{-1}).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[1,1,1],[0,2,1],[0,4,1]])
I=matrix(GF(5),[[1,0,0],[0,1,0],[0,0,1]]) #matriz identidad
AI=A.augment(I,subdivide=True) #matriz aumentada
show(AI,"~",AI.rref())
</script>
:::

Finalmente comprobamos que es inversa:

$$
\left( 
\begin{array}{rrr}
1 & 1 & 1 \\
0 & 2 & 1 \\
0 & 4 & 1 \\
\end{array}
\right)\left( 
\begin{array}{rrr}
1 & 1 & 3 \\
0 & 2 & 3 \\
0 & 2 & 4 \\
\end{array}
\right)=\left( 
\begin{array}{rrr}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 \\
\end{array}
\right).
$$
</li>

</ol>
::::
:::::

::::: {#exr-5 .cuerpo_finito-medio}

Encuentra, si es posible, $P \in \mathcal{M}_{4}(\mathbb{Z}_3)$, regular, tal que $PA=B$, donde
$$
A = \begin{pmatrix} 1&1&0&2&1 \\ 2&1&1&2&0 \\ 0&2&1&0&2 \\ 0&1&2&1&0 \end{pmatrix}, \qquad B = \begin{pmatrix} 1&1&0&1&2 \\ 1&2&2&1&0 \\ 1&0&1&2&0 \\ 2&2&0&0&0 \end{pmatrix}.
$$

:::: {.callout collapse="true" title="Solución"}

Sabemos que $A\sim_f B$ si y sólo si existe  $P$ regular tal que $PA=B$. Por tanto, primero comprobaremos que $A$ y $B$ tienen la misma forma escalonada reducida por filas, calculando además las matrices de paso. Si coinciden, entonces usando las matrices de paso que hemos calculado, podremos encontrar $P$.

<ol type="a">
<li> En primer lugar calculamos las formas de Hermite por filas para comprobar que ambas, la de $A$ y la de $B$ son iguales. Al mismo tiempo calcularemos matrices de paso correspondientes a cada una de ellas.

$$
\begin{aligned}
(A \mid I) & = \left(\begin{array}{ccccc|cccc}
\boxed{1} & 1 & 0 & 2 & 1 & 1 & 0 & 0 & 0  \\
2 & 1 & 1 & 2 & 0 & 0 & 1 & 0 & 0  \\ 
0 & 2 & 1 & 0 & 2 & 0 & 0 & 1 & 0 \\ 
0 & 1 & 2 & 1 & 0 & 0 & 0 & 0 & 1 \\
\end{array}\right)\sim_f  \left(\begin{array}{ccccc|cccc}
\boxed{1} & 1 & 0 & 2 & 1 & 1 & 0 & 0 & 0  \\
0 & 2 & 1 & 1 & 1 & 1 & 1 & 0 & 0  \\ 
0 & 2 & 1 & 0 & 2 & 0 & 0 & 1 & 0 \\ 
0 & 1 & 2 & 1 & 0 & 0 & 0 & 0 & 1 \\
\end{array}\right) \\
& \sim_f  \left(\begin{array}{ccccc|cccc}
\boxed{1} & 1 & 0 & 2 & 1 & 1 & 0 & 0 & 0  \\
0 & \boxed{1} & 2 & 2 & 2 & 2 & 2 & 0 & 0  \\ 
0 & 2 & 1 & 0 & 2 & 0 & 0 & 1 & 0 \\ 
0 & 1 & 2 & 1 & 0 & 0 & 0 & 0 & 1 \\
\end{array}\right)
\sim_f  \left(\begin{array}{ccccc|cccc}
\boxed{1} & 0 & 1 & 0 & 2 & 2 & 1 & 0 & 0  \\
0 & \boxed{1} & 2 & 2 & 2 & 2 & 2 & 0 & 0  \\ 
0 & 0 & 0 & 2 & 1 & 2 & 2 & 1 & 0 \\ 
0 & 0 & 0 & 2 & 1 & 1 & 1 & 0 & 1 \\
\end{array}\right) \\ 
& \sim_f  \left(\begin{array}{ccccc|cccc}
\boxed{1} & 0 & 1 & 0 & 2 & 2 & 1 & 0 & 0  \\
0 & \boxed{1} & 2 & 2 & 2 & 2 & 2 & 0 & 0  \\ 
0 & 0 & 0 & \boxed{1} & 2 & 1 & 1 & 2 & 0 \\ 
0 & 0 & 0 & 0 & 0 & 2 & 2 & 2 & 1 \\
\end{array}\right)
\sim_f  \left(\begin{array}{ccccc|cccc}
\boxed{1} & 0 & 1 & 0 & 2 & 2 & 1 & 0 & 0  \\
0 & \boxed{1} & 2 & 0 & 1 & 0 & 0 & 2 & 0  \\ 
0 & 0 & 0 & \boxed{1} & 2 & 1 & 1 & 2 & 0 \\ 
0 & 0 & 0 & 0 & 0 & 2 & 2 & 2 & 1 \\
\end{array}\right)=(H_A|P_A).
\end{aligned}
$$

$$
\begin{aligned}
(B \mid I) & = \left(\begin{array}{ccccc|cccc}
\boxed{1} & 1 & 0 & 1 & 2 & 1 & 0 & 0 & 0  \\
1 & 2 & 2 & 1 & 0 & 0 & 1 & 0 & 0  \\ 
1 & 0 & 1 & 2 & 0 & 0 & 0 & 1 & 0 \\ 
2 & 2 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\
\end{array}\right)\sim_f \left(\begin{array}{ccccc|cccc}
\boxed{1} & 1 & 0 & 1 & 2 & 1 & 0 & 0 & 0  \\
0 & 1 & 2 & 0 & 1 & 2 & 1 & 0 & 0  \\ 
0 & 2 & 1 & 1 & 1 & 2 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1 & 2 & 1 & 0 & 0 & 1 \\
\end{array}\right) \\
& \sim_f \left(\begin{array}{ccccc|cccc}
\boxed{1} & 0 & 1 & 1 & 1 & 2 & 2 & 0 & 0  \\
0 & \boxed{1} & 2 & 0 & 1 & 2 & 1 & 0 & 0  \\ 
0 & 0 & 0 & \boxed{1} & 2 & 1 & 1 & 1 & 0 \\ 
0 & 0 & 0 & 1 & 2 & 1 & 0 & 0 & 1 \\
\end{array}\right) \sim_f \left(\begin{array}{ccccc|cccc}
\boxed{1} & 0 & 1 & 0 & 2 & 1 & 1 & 2 & 0  \\
0 & \boxed{1} & 2 & 0 & 1 & 2 & 1 & 0 & 0  \\ 
0 & 0 & 0 & \boxed{1} & 2 & 1 & 1 & 1 & 0 \\ 
0 & 0 & 0 & 0 & 0 & 0 & 2 & 2 & 1 \\
\end{array}\right)=(H_B \mid P_B).
\end{aligned}
$$
</li>

<li> Hemos comprobado que $H_A=H_B$ y por tanto $A\sim_f B$ y existe una matriz $P$ tal que $PA=B$.</li>
<li> Para calcular $P$ podemos ayudarnos de las matrices de paso $P_A$ y $P_B$ calculadas:
$$
P_A A=H_A=H_B=P_B B,
$$

y por tanto

$$
P_A A=P_B B.
$$

Como $P_B$ es regular, 

$$
(P_B)^{-1}P_A A=B.
$$

Luego una matriz que verifica la condición pedida sería el producto $(P_B)^{-1}P_A$.

Para calcularla necesitamos en primer lugar calcular la inversa de $P_B$, también usando operaciones elementales por filas.

$$
\begin{aligned}
(P_B \mid I) & = \left(\begin{array}{cccc|cccc}
 1 & 1 & 2 & 0  & 1 & 0 & 0 & 0\\
 2 & 1 & 0 & 0  & 0 & 1 & 0 & 0\\ 
 1 & 1 & 1 & 0  & 0 & 0 & 1 & 0\\ 
 0 & 2 & 2 & 1  & 0 & 0 & 0 & 1\\
\end{array}\right)\sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 2 & 1 & 0 & 0  & 0 & 1 & 0 & 0\\ 
 1 & 1 & 1 & 0  & 0 & 0 & 1 & 0\\ 
 0 & 2 & 2 & 1  & 0 & 0 & 0 & 1\\
\end{array}\right) \\
& \sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 0 & 2 & 2 & 0  & 1 & 1 & 0 & 0\\
 0 & 0 & 2 & 0  & 2 & 0 & 1 & 0\\ 
 0 & 2 & 2 & 1  & 0 & 0 & 0 & 1\\
\end{array}\right)\sim_f
\left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 0 & 2 & 2 & 0  & 1 & 1 & 0 & 0\\
 0 & 0 & 2 & 0  & 2 & 0 & 1 & 0\\ 
 0 & 2 & 2 & 1  & 0 & 0 & 0 & 1\\
\end{array}\right) \\
& \sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 0 & \boxed{1} & 1 & 0  & 2 & 2 & 0 & 0\\
 0 & 0 & 2 & 0  & 2 & 0 & 1 & 0\\ 
 0 & 2 & 2 & 1  & 0 & 0 & 0 & 1\\
\end{array}\right)
\sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 0 & \boxed{1} & 1 & 0  & 2 & 2 & 0 & 0\\
 0 & 0 & 2 & 0  & 2 & 0 & 1 & 0\\ 
 0 & 0 & 0 & 1  & 2 & 2 & 0 & 1\\
\end{array}\right) \\
& \sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 2 & 0  & 1 & 0 & 0 & 0\\ 
 0 & \boxed{1} & 1 & 0  & 2 & 2 & 0 & 0\\
 0 & 0 & \boxed{1} & 0  & 1 & 0 & 2 & 0\\ 
 0 & 0 & 0 & \boxed{1}  & 2 & 2 & 0 & 1\\
\end{array}\right)
\sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 1 & 0 & 0  & 2 & 0 & 2 & 0\\ 
 0 & \boxed{1} & 0 & 0  & 1 & 2 & 1 & 0\\
 0 & 0 & \boxed{1} & 0  & 1 & 0 & 2 & 0\\ 
 0 & 0 & 0 & \boxed{1}  & 2 & 2 & 0 & 1\\
\end{array}\right) \\
& \sim_f \left(\begin{array}{cccc|cccc}
 \boxed{1} & 0 & 0 & 0  & 1 & 1 & 1 & 0\\ 
 0 & \boxed{1} & 0 & 0  & 1 & 2 & 1 & 0\\
 0 & 0 & \boxed{1} & 0  & 1 & 0 & 2 & 0\\ 
 0 & 0 & 0 & \boxed{1}  & 2 & 2 & 0 & 1\\
\end{array}\right).
\end{aligned}
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
PB=matrix(GF(3),[[1,1,2,0],[2,1,0,0],[1,1,1,0],[0,2,2,1]]) 
I=matrix(GF(3),[[1,0,0,0],[0,1,0,0],[0,0,1,0],[0,0,0,1]]) #matriz identidad
PBI=PB.augment(I,subdivide=True) #matriz aumentada
show(PBI,"~",PBI.rref())
</script>
:::

Luego una posible $P$ es

$$
P=(P_B)^{-1}P_A=\left(\begin{array}{cccc}
 1 & 1 & 1 & 0\\ 
 1 & 2 & 1 & 0\\
 1 & 0 & 2 & 0\\ 
 2 & 2 & 0 & 1\\
\end{array}\right) \left(\begin{array}{cccc}
 2 & 1 & 0 & 0  \\
 0 & 0 & 2 & 0  \\ 
 1 & 1 & 2 & 0 \\ 
 2 & 2 & 2 & 1 \\
\end{array}\right)= \left(\begin{array}{cccc}
 0 & 2 & 1 & 0  \\
 0 & 2 & 0 & 0  \\ 
 1 & 0 & 1 & 0 \\ 
 0 & 1 & 0 & 1 \\
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
PBI=matrix(GF(3),[[1,1,1,0],[1,2,1,0],[1,0,2,0],[2,2,0,1]]) 
PA=matrix(GF(3),[[2,1,0,0],[0,0,2,0],[1,1,2,0],[2,2,2,1]])
P=PBI*PA
A=matrix(GF(3),[[1,1,0,2,1],[2,1,1,2,0],[0,2,1,0,2],[0,1,2,1,0]]) 
B=matrix(GF(3),[[1,1,0,1,2],[1,2,2,1,0],[1,0,1,2,0],[2,2,0,0,0]]) 
P*A==B
</script>
:::

</li>
</ol>
::::
:::::

::::: {#exr-6 .cuerpo_finito-avanzado}

Sea $$A=\left (\begin{array}{cccc} 2 & 1 & 3 & 0 \\ 1 & 2 & 1 & 1 \\ 3 & 4 & 2 & 1 \end{array}\right ) \in \mathcal{M}_{3\times 4}({\mathbb{Z}}_5)$$

<ol type="a">
  <li>Encuentra una matriz $B$ tal que $A\cdot B = Id$.</li>
  <li>Encuentra todas las matrices $B$ que cumplan la propiedad anterior.</li>
  <li>¿Existe una matriz $C$ tal que $C\cdot A = Id$?</li>
</ol>

::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Encontrar $B$ tal que $A\cdot B = Id$.

¿Qué orden debe tener $B$? Como la identidad es una matriz cuadrada, y $A$ tiene tres filas, deducimos que $I$ es la identidad $3\times 3$. De aquí también deducimos que $B$ tiene que tener cuatro filas y tres columnas.


Si calculamos la forma de Hermite por columnas de $A$ y la matriz de paso, a la que llamaremos $Q$, entonces $A Q=H$. La matriz $H$ no es la matriz identidad, por supuesto, porque tiene orden $3\times 4$, pero puede parecerse bastante. Calculémosla:

$$
\left[ \begin{array}{c}
A\\
\hline
I_4
\end{array}\right]=\left (\begin{array}{cccc}
2 & \boxed{1} & 3 & 0 \\ 1 & 2 & 1 & 1 \\ 3 & 4 & 2 & 1\\
\hline
1 & 0 & 0 &0\\
0 & 1 & 0 &0\\
0 & 0 & 1 &0\\
0 & 0 & 0 &1\\
 \end{array}\right)\sim_c 
\left (\begin{array}{cccc}
\boxed{1} & 0 & 0 & 0 \\ 2 & 2 & 1 & 0 \\ 
4 & 0 & 1 & 0\\
\hline
0 & 1 & 0 &0\\
1 & 3 & 0 & 2\\
0 & 0 & 0 &1\\
0 & 0 & 1 &0\\
\end{array}\right) \sim_c 
\left (\begin{array}{cccc}
\boxed{1} & 0 & 0 & 0 \\ 
2 & \boxed{1} & 1 & 0 \\ 
4 & 0 & 1 & 0\\
\hline
0 & 3 & 0 &0\\
1 & 4 & 0 & 2\\
0 & 0 & 0 &1\\
0 & 0 & 1 &0\\
\end{array}\right)
$$ 

$$
\sim_c 
\left (\begin{array}{cccc}
\boxed{1} & 0 & 0 & 0 \\ 
0 & \boxed{1} & 0 & 0 \\ 
4 & 0 & \boxed{1} & 0\\
\hline
4 & 3 & 2 &0\\
3 & 4 & 1 & 2\\
0 & 0 & 0 &1\\
0 & 0 & 1 &0\\
\end{array}\right) \sim_c
\left (\begin{array}{cccc}
\boxed{1} & 0 & 0 & 0 \\ 
0 & \boxed{1} & 0 & 0 \\ 
0 & 0 & \boxed{1} & 0\\
\hline
1 & 3 & 2 &0\\
4 & 4 & 1 & 2\\
0 & 0 & 0 &1\\
1 & 0 & 1 &0\\
\end{array}\right)=\left[ \begin{array}{c}
H\\
\hline
Q
\end{array}\right].
$$ 

Así que 

$$\left(\begin{array}{cccc}
2 & 1 & 3 & 0 \\ 1 & 2 & 1 & 1 \\ 3 & 4 & 2 & 1\\
\end{array}\right)
\left (\begin{array}{ccc|c}
1 & 3 & 2 &0\\
4 & 4 & 1 & 2\\
0 & 0 & 0 &1\\
1 & 0 & 1 &0\\
\end{array}\right)=\left (\begin{array}{ccc|c}
\boxed{1} & 0 & 0 & 0 \\ 
0 & \boxed{1} & 0 & 0 \\ 
0 & 0 & \boxed{1} & 0\\
\end{array}\right). 
$$


Observando el producto anterior nos damos cuenta de que si tomamos solo las 3 primeras columnas de $Q$ tenemos una matriz que verifica la condición.
Así que una posible matriz $B$ es 

$$
B=\left (\begin{array}{ccc}
1 & 3 & 2 \\
4 & 4 & 1 \\
0 & 0 & 0 \\
1 & 0 & 1 \\
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(GF(5),[[2,1,3,0],[1,2,1,1],[3,4,2,1]]) 
B=matrix(GF(5),[[1,3,2],[4,4,1],[0,0,0],[1,0,1]]) 
I=matrix(GF(5),[[1,0,0],[0,1,0],[0,0,1]])
A*B==I
</script>
:::

</li>

<li>Todas las matrices $B$ que cumplen la propiedad anterior.
En realidad el planteamiento es sencillo, sería resolver:

$$
\left(\begin{array}{cccc}
2 & 1 & 3 & 0 \\ 1 & 2 & 1 & 1 \\ 3 & 4 & 2 & 1\\
\end{array}\right)
\left (\begin{array}{ccc}
x_1 & y_1 & z_1 \\
x_2 & y_2 & z_2\\
x_3 & y_3 & z_3\\
x_4 & y_4 & z_4\\
\end{array}\right)=\left (\begin{array}{ccc}
1 & 0 & 0 \\ 
0 & 1 & 0  \\ 
0 & 0 & 1 \\
\end{array}\right),
$$

que puede parecer complicado, son $12$ incógnitas, pero realmente no se mezclan (por eso las  he designado con letras distintas).
El primer sistema será el que corresponde a las $x$:

$$
\left(\begin{array}{cccc}
2 & 1 & 3 & 0 \\ 1 & 2 & 1 & 1 \\ 3 & 4 & 2 & 1\\
\end{array}\right)
\left (\begin{array}{c}
x_1 \\
x_2 \\
x_3 \\
x_4\\
\end{array}\right)=\left (\begin{array}{c}
1 \\ 
0   \\ 
0  \\
\end{array}\right) 
$$

con matriz ampliada

$$
\left(\begin{array}{cccc|c}
2 & 1 & 3 & 0 & 1\\ 1 & 2 & 1 & 1 & 0 \\ 3 & 4 & 2 & 1 & 0\\
\end{array}\right)$$

y las correspondientes a los sistemas para las $y$ y las $z$:

$$\left(\begin{array}{cccc|c}
2 & 1 & 3 & 0 & 0\\ 1 & 2 & 1 & 1 & 1 \\ 3 & 4 & 2 & 1 & 0\\
\end{array}\right), \quad \left(\begin{array}{cccc|c}
2 & 1 & 3 & 0 & 0\\ 1 & 2 & 1 & 1 & 0 \\ 3 & 4 & 2 & 1 & 1\\
\end{array}\right).
$$

Como se resuelven haciendo operaciones elementales por filas sobre la matriz de coeficientes, los tres pueden resolverse simultáneamente utilizando la matriz:

$$
\left(\begin{array}{cccc|ccc}
2 & 1 & 3 & 0 & 1 & 0 & 0\\ 1 & 2 & 1 & 1 & 0 & 1 & 0 \\ 3 & 4 & 2 & 1 & 0 & 0 & 1\\
\end{array}\right)
$$

que incluye las tres columnas de términos independientes.

Utilizamos el método de Gauss-Jordan:

$$
\begin{aligned}
\left(\begin{array}{cccc|ccc}
2 & 1 & 3 & 0 & 1 & 0 & 0\\ \boxed{1} & 2 & 1 & 1 & 0 & 1 & 0 \\ 3 & 4 & 2 & 1 & 0 & 0 & 1\\
\end{array}\right) & \sim_f 
\left(\begin{array}{cccc|ccc}
\boxed{1} & 2 & 1 & 1 & 0 & 1 & 0 \\ 
0 & 2 & 1 & 3 & 1 & 3 & 0\\ 
0 & 0 & 0 & 1 & 1 & 0 & 1\\
\end{array}\right)  \sim_f 
\left(\begin{array}{cccc|ccc}
\boxed{1} & 2 & 1 & 1 & 0 & 1 & 0 \\ 
0 & \boxed{1} & 3 & 4 & 3 & 4 & 0\\ 
0 & 0 & 0 & 1 & 1 & 0 & 1\\
\end{array}\right)\\
& \sim_f
\left(\begin{array}{cccc|ccc}
\boxed{1} & 0 & 0 & 3 & 4 & 3 & 0 \\ 
0 & \boxed{1} & 3 & 4 & 3 & 4 & 0\\ 
0 & 0 & 0 & \boxed{1} & 1 & 0 & 1\\
\end{array}\right)\sim_f \left(\begin{array}{cccc|ccc}
\boxed{1} & 0 & 0 & 0 & 1 & 3 & 2 \\ 
0 & \boxed{1} & 3 & 0 & 4 & 4 & 1\\ 
0 & 0 & 0 & \boxed{1} & 1 & 0 & 1\\
\end{array}\right).
\end{aligned}
$$

Eligiendo en cada caso la columna de términos independientes que corresponde tendremos la solución de los tres sistemas.
Por tanto la solución de cada uno de los sistemas es

$$
\begin{array}{lll}
x_1=1, & y_1= 3, & z_1=2,\\ 
x_2=4+2\lambda_1, & y_2=4+2\lambda_2, & z_2=1+2\lambda_3,\\
x_3=\lambda_1, & y_3=\lambda_2, &z_3=\lambda_3,\\
x_4=1, & y_4=0, & z_4=1,\\
\end{array} \quad \lambda_1,\lambda_2,\lambda_3\in \mathbb{Z}_5.
$$

Es decir, todas las matrices son de la forma:

$$
\left(\begin{array}{ccc}
1 &  3 & 2\\ 
4+2\lambda_1 & 4+2\lambda_2 & 1+2\lambda_3\\
\lambda_1 & \lambda_2 &\lambda_3\\
1 & 0 & 1\\
\end{array}\right), \quad \lambda_1,\lambda_2,\lambda_3\in \mathbb{Z}_5.
$$
</li>

<li>Encontrar $C$ tal que $C\cdot A = Id$.
Si pensamos primero en el orden de $C$, como $A$ tiene tres filas y cuatro columnas, necesariamente $C$ debe tener tres columnas. Por otro lado, como la matriz identidad es cuadrada, en este caso será una matriz $4\times4$, por lo que $C$ debe tener cuatro filas.


El argumento más fácil de utilizar es posterior al momento en que nos encontramos en el desarrollo del tema. Se usa:

$$
\operatorname{rg}(A\cdot B)\leq \min\{\operatorname{rg}(A),\operatorname{rg}(B)\}
$$

en este caso, por los órdenes de $A$ y $C$ su rango máximo posible es $3$, luego $\operatorname{rg}(C\cdot A)\leq 3$ mientras que $\operatorname{rg}(I_4)=4.$


También es posible plantearlo de una forma similar al apartado 2, al resolver los sistemas encontraremos que son incompatibles.</li>
</ol>
::::
:::::


::::: {#exr-7 .basico}

Dado el sistema de ecuaciones con coeficientes en $\mathbb{Q}$
$$\left\{\begin{aligned} x - ay + (a+1)z & = 4, \\ ax + 2y + z & = -1. \end{aligned}\right.$$
Discútelo según los valores del parámetro $a$, y resuélvelo para $a=-1$.

:::: {.callout collapse="true" title="Solución"}


En este tipo de ejercicio utilizaremos el Teorema de Rouché-Frobenius  junto a los distintos métodos para calcular el rango de una matriz.

En primer lugar escribimos la matriz ampliada del sistema

$$
(A|b)=\left( \begin{array}{rcc|r}
1 & -a & a+1 & 4\\
a & 2 & 1 & -1
\end{array}\right).
$$

Puesto que el orden de matriz de coeficientes es $2\times3$ y el de la ampliada $2\times4$, en el caso de que $\operatorname{rg}(A)=2$, entonces $\operatorname{rg}(A|b)=2$ (puesto que no puede haber más de dos pivotes, uno por fila) y usando Teorema de Rouché-Frobenius el sistema será compatible indeterminado. 
Puesto que el rango no cambia si realizamos cualquier operaciones elementales por columnas, para calcular $\operatorname{rg}(A)$ realizamos algunas, por ejemplo:

$$
{\small A=\left( \begin{array}{rcc}
1 & -a & a+1 \\
a & 2 & 1  
\end{array}\right) \sim_c \left( \begin{array}{rcc}
1 & -a & 1 \\
a & 2 & 3 
\end{array}\right) \sim_c \left( \begin{array}{rcc}
1 & -a & 0 \\
a & 2 & 3-a 
\end{array}\right) }.
$$ 

Para el rango de esta matriz es muy fácil utilizar el cálculo de determinantes: si
$\begin{vmatrix}
1 & 0 \\
a & 3-a
\end{vmatrix}= 3-a \not = 0$ 
el rango de $A$ es dos.
(También se podría haber hecho en la matriz $A$ directamente, pero este determinante es muy sencillo de calcular y de determinar cuándo es distinto de $0$.)


Entonces tenemos que en todos los casos en los que $a\not = 3$ tendremos  $\operatorname{rg}(A)=\operatorname{rg}(A|b)=2$ es menor que el  número de incógnitas y el sistema es compatible indeterminado.

Solo nos queda estudiar el caso $a=3$, para el que podemos proceder como en los ejercicios del comienzo del tema: 

$$
(A|b)=\left( \begin{array}{rrr|r}
\boxed{1} & -3 & 4 & 4\\
3 & 2 & 1 & -1
\end{array}\right)\sim_f  \left( \begin{array}{rrr|r}
\boxed{1} & 0 & 1 & 5/11\\
0 & 1 & -1 & -13/11
\end{array}\right).
$$

O bien, podemos volver a aplicar el Teorema de Rouché-Frobenius, en este caso observamos que tomando las dos primeras columnas de $A$ se tiene

$\begin{vmatrix}
1 & 3 \\
-3 & 2
\end{vmatrix}=2+9=11$ luego $\operatorname{rg}(A)=2$ y el mismo razonamiento nos lleva a que también en este caso es compatible indeterminado. 


Por tanto, siempre es compatible indeterminado dependiendo de un parámetro.


Para el caso $a=-1$:

$$
(A|b)=\left( \begin{array}{rrr|r}
\boxed{1} & 1 & 0 & 4\\
-1 & 2 & 1 & -1
\end{array}\right)\sim_f \left( \begin{array}{rrr|r}
\boxed{1} & 1 & 0 & 4\\
0 & 3 & 1 & 3
\end{array}\right)\sim_f \left( \begin{array}{rrr|r}
\boxed{1} & 1 & 0 & 4\\
0 & \boxed{1} & 1/3 & 1
\end{array}\right)\sim_f \left( \begin{array}{rrr|r}
\boxed{1} & 0 & -1/3 & 3\\
0 & \boxed{1} & 1/3 & 1
\end{array}\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,1,0],[-1,2,1]]) #matriz de coeficientes
b=vector(QQ,[4,-1]) #término independiente
Ab=A.augment(b,subdivide=True) #matriz aumentada
show(Ab,"~",Ab.rref())
</script>
:::
::::
:::::

::::: {#exr-8 .cuerpo_finito-medio}

Calcula el rango de la siguiente matriz, con coeficientes en $\mathbb{Z}_3$, según los valores de los parámetros $a$ y $b$.
$$\begin{pmatrix} 1 & a & 0 & 1 \\ 2 & 1 & 1 & b \\ 0 & a & b & a+b \end{pmatrix}$$

:::: {.callout collapse="true" title="Solución"}


El rango máximo posible de esta matriz es 3. Elegimos una submatriz cuadrada de orden 3 y calculamos su determinante. Escogemos una que a priori sepamos que su determinante no sea nulo y que sea fácil de calcular.
Por ejemplo

$$
\begin{vmatrix}
1 & a & 0  \\ 2 & 1 & 1  \\ 0 & a & b 
\end{vmatrix}=_{
(C_2-aC_1 \rightarrow C_2)}= \begin{vmatrix}
1 & 0 & 0  \\ 2 & 1-2a & 1  \\ 0 & a & b 
\end{vmatrix}=(1-2a)b-a=(1+a)b+2a=2a+b+ab.
$$

Al estar trabajando en $\mathbb{Z}_3$, $a$ y $b$ pueden tomar solo 3 valores posibles.

Podemos examinar todos los casos en una tabla de doble entrada, donde en cada casillero escribiremos el valor del determinante. Por ejemplo,
si $a=0$, entonces $|A|= b$; si $a=1$, $|A|= 2b+2$; si $a=2$, $|A|= 1$.


<table class="default">
  <tr>
    <td>$_b \setminus  ^a$</td>
    <td>0</td>
    <td>1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>2</td>
    <td>1</td>
  </tr>
  <tr>
    <td>1</td>
    <td>1</td>
    <td>1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>2</td>
    <td>2</td>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

De la observación de la tabla anterior deducimos que $\operatorname{rg}(A)=3$ para 7 de los 9 casos, siempre que el determinante es distinto de $0$.
Ahora, estudiamos los dos casos particulares que nos faltan.


Para $a=0=b$:


$$
\begin{pmatrix}
1 & 0 & 0 & 1 \\ 2 & 1 & 1 & 0 \\ 0 & 0 & 0 & 0
\end{pmatrix}
$$

que tiene rango 2 puesto que hay una fila entera de ceros y en las otras dos se pueden hacer pivotes.


Para $a=1$, $b=2$:


$$
\begin{pmatrix}
1 & 1 & 0 & 1 \\ 2 & 1 & 1 & 2 \\ 0 & 1 & 2 & 0
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 1 & 0 & 1 \\ 0 & 2 & 1 & 0 \\ 0 & 1 & 2 & 0
\end{pmatrix}
$$

que también tiene rango 2 (recordemos que estamos en $\mathbb{Z}_3$).
::::
:::::


::::: {#exr-9 .basico}

Sea $$A=\left( \begin{array}{cccc} 3-\lambda & 1 & 1 & 0\\ 5 &-\lambda & 0 & 0\\ 0 & -\lambda & -\lambda & 1\\ 0 & -1 & -1 & 2-\lambda \end{array}\right).$$
<ol type="a">
<li>Calcula el determinante de la matriz $A$ considerando sus coeficientes en $\mathbb{Q}$.</li>
<li class="cuerpo_finito">Calcula el rango de la matriz $A$ según los valores de $\lambda$ considerando sus coeficientes en $\mathbb{Z}_3$.</li>
<li>Discute el sistema de ecuaciones con matriz ampliada $A$ considerando sus coeficientes en $\mathbb{Q}$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinante.
Para calcular el determinante más fácilmente, a la segunda columna le restamos la tercera, luego desarrollamos por la segunda columna:

$$
|A|=\left| \begin{array}{cccc}
3-\lambda & 1 & 1 & 0\\
5 &-\lambda & 0 & 0\\
0 & -\lambda & -\lambda & 1\\
0 & -1 & -1 & 2-\lambda 
\end{array}\right|=\left| \begin{array}{cccc}
3-\lambda & 0 & 1 & 0\\
5 &-\lambda & 0 & 0\\
0 & 0 & -\lambda & 1\\
0 & 0 & -1 & 2-\lambda 
\end{array}\right|=(-\lambda)\left| \begin{array}{ccc}
3-\lambda &  1 & 0\\
0 &  -\lambda & 1\\
0 &  -1 & 2-\lambda 
\end{array}\right|.
$$

Desarrollando ahora por la primera columna
$$
|A|=(-\lambda)(3-\lambda)[(-\lambda)(2-\lambda)+1]=(-\lambda)(3-\lambda)(\lambda -1)^2
$$ 

y este resultado es válido en cualquier cuerpo.</li>

<li class="cuerpo_finito">Rango.
Puesto que el cálculo del determinante es válido en $\mathbb{Z}_3$, cuando $\lambda=2$ la matriz tiene rango 4 (observamos que $2$ no es raíz del polinomio que tenemos descompuesto en factores lineales, y por tanto el determinante es distinto de $0$); en cambio, para los casos $\lambda\in \{0,1\}$ (que son raíces del polinomio obtenido) es menor o igual que 3. Para estos casos calculamos el rango mediante operaciones elementales.


Para $\lambda=0$:


$$
A=\left( \begin{array}{cccc}
0 & 1 & 1 & 0\\
2 &0 & 0 & 0\\
0 & 0 & 0 & 1\\
0 & 2 & 2 & 2 
\end{array}\right)\sim_{f}\left( \begin{array}{cccc}
0 & 1 & 1 & 0\\
1 &0 & 0 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 2 
\end{array}\right)\sim_{f}\left( \begin{array}{cccc}
1 & 0 & 0 & 0\\
0 &1 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0 
\end{array}\right)
$$ 
luego el rango es 3. 


Para $\lambda=1$:

$$
A=\left( \begin{array}{cccc}
2 & 1 & 1 & 0\\
2 &2 & 0 & 0\\
0 & 2 & 2 & 1\\
0 & 2 & 2 & 1 
\end{array}\right)\sim_{f}\left( \begin{array}{cccc}
2 & 1 & 1 & 0\\
0 &1 & 2 & 0\\
0 & 2 & 2 & 1\\
0 & 0 & 0 & 0 
\end{array}\right)
$$
que tiene rango 3.</li>

<li>Sistema de ecuaciones.

Como la matriz ampliada tiene rango 4 para $\lambda\not\in \{0,1,3\}$, y la de coeficientes solo tiene tres columnas y por tanto el rango máximo es 3, en estos casos el sistema es incompatible. Nos queda estudiar los casos particulares $\lambda\in\{0,1,3\}$:


Para $\lambda=0$:
$$
\left( \begin{array}{ccc|c}
3 & 1 & 1 & 0\\
5 & 0 & 0 & 0\\
0 & 0 & 0 & 1\\
0 & -1 & -1 & 2 
\end{array}\right).
$$

Como aparece la ecuación $0=1$ entonces también es incompatible.


Para $\lambda=1$:
$$
\left( \begin{array}{ccc|c}
2 & 1 & 1 & 0\\
5 & -1 & 0 & 0\\
0 & -1 & -1 & 1\\
0 & -1 & -1 & 1 
\end{array}\right)\sim_{f}\left( \begin{array}{ccc|c}
2 & 0 & 0 & 1\\
5 & -1 & 0 & 0\\
0 & -1 & -1 & 1\\
0 & 0 & 0 & 0 
\end{array}\right)
$$

en este caso la matriz de coeficientes tiene rango 3, y por tanto el sistema es compatible determinado.


Para $\lambda=3$:

$$
\left( \begin{array}{ccc|c}
0 & 1 & 1 & 0\\
5 & -3 & 0 & 0\\
0 & -3 & -3 & 1\\
0 & -1 & -1 & -1 
\end{array}\right)\sim_{f}\left( \begin{array}{ccc|c}
0 & 1 & 1 & 0\\
5 & -3 & 0 & 0\\
0 & -3 & -3 & 1\\
0 & 0 & 0 & -1 
\end{array}\right).
$$

y de nuevo aparece la ecuación $0=1$ con lo que en este caso es incompatible.</li>
</ol>
::::
:::::


::::: {#exr-10 .medio}

Sea 

$$
A=\left(\begin{array}{rccc} 1 & 1 & 1 & 0\\ a & a-1 & a & 1\\ 1 & 1 & 1 & a-1\\ 1 & a & 0 & 0  \end{array}\right)\in \mathcal{M}_4(\mathbb{R}).
$$
y el sistema de ecuaciones
$$
\left\{\begin{aligned} 
x+y+z&=0,\\
ax+(a-1)y+az&=1,\\
x+y+z&=a-1,\\ 
x+ay&=0. 
\end{aligned}\right.
$$

<ol type="a">
<li>Calcula el determinante de la matriz $A$.</li>
<li>Calcula el rango de $A$ según los valores de $a$.</li>
<li>Calcula la forma de Hermite por filas de $A$ según los valores de $a$.</li>
<li>Discute el sistema de ecuaciones según los valores de $a$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinante:

$$
|A|=\left|\begin{array}{rccc}
1 & 1 & 1 & 0\\
a & a-1 & a & 1\\
1 & 1 & 1 & a-1\\
1 & a & 0 & 0 
\end{array}\right|= \left|\begin{array}{rccc}
0 & 0 & 1 & 0\\
0 & -1 & a & 1\\
0 & 0 & 1 & a-1\\
1 & a & 0 & 0 
\end{array}\right|
$$

donde a la primera y a la segunda columnas le hemos restado la tercera. Ahora, desarrollando el determinante por la primera columna (y el de orden 3 que aparece de nuevo por su primera columna):

$$
|A|= (-1) \left|\begin{array}{ccc}
0 & 1 & 0\\
-1 & a & 1\\
0 & 1 & a-1\\
\end{array}\right|= (-1)^3 \left|\begin{array}{cc}
1 & 0\\
1 & a-1\\
\end{array}\right|=1-a.
$$
</li>

<li>Rango.
Como $|A|=a-1$, si $a\not = 1$ el rango de $A$ es 4. Solo queda calcular el rango si $a=1$. Como después se pide calcular la forma de Hermite por filas, lo realizamos ahora:

$$
\begin{aligned}
A= & \left(\begin{array}{rccc}
1 & 1 & 1 & 0\\
1 & 0 & 1 & 1\\
1 & 1 & 1 & 0\\
\mathbf{1} & 1 & 0 & 0 
\end{array}\right)\sim_f \left(\begin{array}{rccc}
0 & 0 & 1 & 0\\
0 & -1 & 1 & 1\\
0 & 0 & 1 & 0\\
\mathbf{1} & 1 & 0 & 0 
\end{array}\right)\sim_f \left(\begin{array}{rccc}
\mathbf{1} & 1 & 0 & 0 \\
0 & 0 & \mathbf{1} & 0\\
0 & -1 & 1 & 1\\
0 & 0 & 1 & 0\\
\end{array}\right)\\
& \sim_f  \left(\begin{array}{rccc}
\mathbf{1} & 1 & 0 & 0 \\
0 & 0 & \mathbf{1} & 0\\
0 & -1 & 0 & 1\\
0 & 0 & 0 & 0\\
\end{array}\right)\sim_f \left(\begin{array}{rccc}
\mathbf{1} & 0 & 0 & 1 \\
0 & \mathbf{1} & 0 & -1\\
0 & 0 & \mathbf{1} & 0\\
0 & 0 & 0 & 0\\
\end{array}\right).
\end{aligned}
$$

Así, si $a=1$ el rango es $3$.

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,1,1,0],[1,0,1,1],[1,1,1,0],[1,1,0,0]]) #matriz de coeficientes
show(A,"~",A.rref())
</script>
:::

</li>

<li>Forma de Hermite por filas.
Cuando $a\not = 1$ como el rango es $4$, la forma de Hermite por filas es $I_4$, para $a=1$ es la calculada en el apartado anterior.</li>

<li>Discusión del sistema.
Como la matriz ampliada del sistema es $A$, entonces cuando $a\not = 1$ la matriz ampliada tiene rango 4 mientras que la de coeficientes como máximo podría tener rango 3, así que el sistema es incompatible; en el caso $a=1$, usando la forma de Hermite por filas de $A$ que hemos calculado observamos que el sistema es compatible determinado.</li>
</ol>
::::
:::::


::::: {#exr-11 .avanzado}

Dadas las matrices 

$$
A=\begin{pmatrix}
1 & 0 & 1 & a\\
1 & 1 & 0 & 1\\
1 & 1 & a-2 & 1
\end{pmatrix}, \hspace{1em}
B=\begin{pmatrix}
1 & a-1& 1 & 1\\
1 & 0 & 1 & 1\\
1 & a & 1 & 1\\
\end{pmatrix}.
$$

<ol type="a">
<li>Calcula los valores de $a$ para los que $A$ y $B$ son equivalentes.</li>
<li>Calcula para qué valores de $a$ son equivalentes por filas.</li>
<li>Para $a=1$ calcula la forma de Hermite por columnas de $B$, que llamaremos $H$, y $P$ regular tal que $H=BP$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular los valores de $a$ para los que $A$ y $B$ son equivalentes.

Dos matrices son equivalentes $\Leftrightarrow$ tienen el mismo rango.

Calculamos el rango de ambas matrices. Como son de orden $3\times 4$ su rango máximo es tres. 

Para $A$ calculamos un menor de orden tres

$$
\left|\begin{array}{ccc}
1 & 0 & 1 \\
1 & 1 & 0 \\
1 & 1 & a-2 \\
\end{array}\right|= \left|\begin{array}{ccc}
1 & 0 & 1 \\
0 & 1 & 0 \\
0 & 1 & a-2 \\
\end{array}\right|=a-2.
$$

Si $a\not = 2$ este menor es distinto de cero y por tanto $\operatorname{rg}(A)=2$. Veamos qué ocurre para $a=2$, para lo que sustituimos y calculamos la forma de Hermite por filas:

$$
A=\begin{pmatrix}
1 & 0 & 1 & 2\\
1 & 1 & 0 & 1\\
1 & 1 & 0 & 1
\end{pmatrix} \sim_f 
\begin{pmatrix}
1 & 1 & 0 & 1\\
0 & -1 & 1 & 1\\
0 & 0 & 0 & 0
\end{pmatrix} \sim_f 
\begin{pmatrix}
1 & 0 & 1 & 2\\
0 & 1 & -1 & -1\\
0 & 0 & 0 & 0
\end{pmatrix},
$$

así que para $a=2$ tiene rango 2.

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,0,1,2],[1,1,0,1],[1,1,0,1]]) #matriz de coeficientes
show(A,"~",A.rref())
</script>
:::

Para $B$ observamos que tiene tres columnas idénticas, por lo que el rango máximo puede ser dos. También podemos calcular su forma de Hermite por filas 

$$
B=\begin{pmatrix}
1 & a-1& 1 & 1\\
1 & 0 & 1 & 1\\
1 & a & 1 & 1\\
\end{pmatrix}\sim_f 
\begin{pmatrix}
1 & 0 & 1 & 1\\
0 & a-1 & 0 & 0\\
0 & a & 0 & 0\\
\end{pmatrix}\sim_f 
\begin{pmatrix}
1 & 0 & 1 & 1\\
0 & 1 & 0 & 0\\
0 & 0 & 0 & 0\\
\end{pmatrix},
$$

con lo que $\operatorname{rg}(B)=2$ para todo valor de $a$.Así que $A$ y $B$ son equivalentes para $a=2$.</li>

<li>Calcular para qué valores de $a$ son equivalentes por filas.

Para que sean equivalentes por filas deben tener la misma forma de Hermite por filas, y en particular el mismo rango, así que en cualquier caso solo hay que investigar el caso $a=2$. Como en el apartado anterior hemos calculado la forma de Hermite por filas en este caso, concluimos que nunca son equivalentes por filas. </li>

<li>Calcular $H$, y $P$ regular tal que $H=BP$.

Sustituimos $a=1$ en $B$ y realizamos operaciones elementales por columnas apuntándolas en una matriz regular:

$$
B=\begin{pmatrix}
1 & 0 & 1 & 1\\
1 & 0 & 1 & 1\\
1 & 1 & 1 & 1\\
\hline
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{pmatrix}\sim_c
\begin{pmatrix}
1 & 0 & 0 & 0\\
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
\hline
1 & 0 & -1 & -1\\
-1 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{pmatrix},
$$

luego 

$$H= \begin{pmatrix}
1 & 0 & 0 & 0\\
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
\end{pmatrix} \hspace{2cm}
P=\begin{pmatrix}
1 & 0 & -1 & -1\\
-1 & 1 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1
\end{pmatrix}.
$$
</li>
</ol>
::::
:::::


::::: {#exr-12 .medio}

Dada la matriz

$$
A=\begin{pmatrix}
1 & a-1 & a & 1\\
-1 & a-1 & a & 1\\
0 &2a-2 & 2a & 1\\
1 & 0 & 2a & 3 
\end{pmatrix}
$$

<ol type="a">
<li>Calcula el determinante.</li>
<li>Calcula la forma de Hermite por filas según los valores de $a$.</li>
<li>Discute el sistema cuya matriz ampliada es $A$ en función de los valores de $a$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular el determinante.

$$
\begin{aligned}
|A|= &\left|\begin{array}{cccc}
1 & a-1 & a & 1\\
-1 & a-1 & a & 1\\
0 &2a-2 & 2a & 1\\
1 & 0 & 2a & 3 
\end{array}\right|=\left|\begin{array}{cccc}
1 & a-1 & a & 1\\
0 & 2a-2 & 2a & 2\\
0 &2a-2 & 2a & 1\\
0 & 1-a & a & 2 
\end{array}\right|= \left|\begin{array}{ccc}
2a-2 & 2a & 2\\
2a-2 & 2a & 1\\
1-a & a & 2 
\end{array}\right|\\
= & \left|\begin{array}{ccc}
0 & 0 & 1\\
2a-2 & 2a & 1\\
1-a & a & 2 
\end{array}\right|= \left|\begin{array}{cc}
2a-2 & 2a \\
1-a & a  
\end{array}\right|=4a^2-4a=4a(a-1).
\end{aligned}
$$
</li>

<li>Calcular la forma de Hermite por filas según los valores de $a$.

Por el Teorema de las matrices regulares, si $|A|\not = 0$ la forma de Hermite por filas de $A$ es $I_4$, por tanto si $a\not = 0,1$ entonces $H=I_4$.
Estudiamos los casos particulares $a=0$ y $a=1$.

Si $a=0$ 

$$
A=\begin{pmatrix}
1 & -1 & 0 & 1\\
-1 & -1 & 0 & 1\\
0 & -2 & 0 & 1\\
1 & 0 & 0 & 3 
\end{pmatrix}\sim_f \begin{pmatrix}
1 & -1 & 0 & 1\\
0 & -2 & 0 & 2\\
0 & -2 & 0 & 1\\
0 & 1 & 0 & 2 
\end{pmatrix} \sim_f \begin{pmatrix}
1 & 0 & 0 & -1\\
0 & 1 & 0 & 2\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 5 
\end{pmatrix} \sim_f \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0 
\end{pmatrix}=H. 
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,-1,0,1],[-1,-1,0,1],[0,-2,0,1],[1,0,0,3]])
show(A,"~",A.rref())
</script>
:::

Si $a=1$

$$
A=\begin{pmatrix}
1 & 0 & 1 & 1\\
-1 & 0 & 1 & 1\\
0 & 0 & 2 & 1\\
1 & 0 & 2 & 3 
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 0 & 1 & 1\\
0 & 0 & 2 & 2\\
0 & 0 & 2 & 1\\
0 & 0 & 1 & 2 
\end{pmatrix} \sim_f \begin{pmatrix}
1 & 0 & 0 & -1\\
0 & 0 & 1 & 2\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & -1 
\end{pmatrix} \sim_f \begin{pmatrix}
1 & 0 & 0 & 0\\
0 & 0 & 1 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0 
\end{pmatrix} =H.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[1,0,1,1],[-1,0,1,1],[0,0,2,1],[1,0,2,3]])
show(A,"~",A.rref())
</script>
:::
</li>

<li>Discutir el sistema cuya matriz ampliada es $A$ en función de los valores de $a$.

Como tenemos la forma de Hermite por filas en todos los casos, entonces el sistema es equivalente al que tiene matriz ampliada $H$.

Si $a\not = 0,1$ entonces 

$$
H= \left(\begin{array}{ccc|c}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{array}\right)
$$

y como aparece la ecuación $0=1$ es incompatible.

Si $a=0$

$$
H=\left( \begin{array}{ccc|c}
1 & 0 & 0 & 0\\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{array}\right)
$$ 

y también es incompatible.

Por último para $a=1$

$$
H= \left( \begin{array}{ccc|c}
1 & 0 & 0 & 0\\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{array}\right)
$$

también es incompatible.</li>
</ol>
::::
:::::


::::: {#exr-13 .medio}
Para las matrices:

$$
A=\begin{pmatrix}
2 & 1 & 2 \\
1 & 2 & 2 \\
2 & 1 & 2 \\
1 & 2 & 2  
\end{pmatrix},\;\;
B=\begin{pmatrix}
2 & 1 & 2 \\
1 & 2 & 2 \\
2 & 1 & 2 \\
2 & 2 & 2  
\end{pmatrix},\;\;
C=\begin{pmatrix}
1 & 0 & 0  \\
0 & 1 &  0  \\
0 & 0 & 0  \\
0 & 0 & 0  \\
\end{pmatrix}.
$$

Determinar matrices regulares $P$ y $Q$ de forma que:
$Q\cdot A \cdot P= C$.

Razonar que 
no pueden existir matrices regulares $P$ y $Q$ de forma que:
$Q\cdot B \cdot P=C$

:::: {.callout collapse="true" title="Solución"}

El rango de $A$ es dos, las filas priemra y tercera son idénticas y también lo son la segunda y la cuarta, además el menor principal de orden dos es distinto de cero. Como $C$ es de rango dos y del mismo orden, entonces $A$ y $C$ son equivalentes y por tanto existen matrices regulares $Q$ y $P$ verificando $Q\, A \, P=C$. Sin embargo $B$ tiene rango tres (el menor principal de orden tres es distinto de cero) y por tanto no es equivalente con $C$.


Para calcular $Q$ y $P$ realizamos operaciones elementales por filas y columnas sobre $A$ hasta obtener $C$. Una forma posible es transformar $A$ hasta su forma de Hermite por filas y después, a la matriz obtenida se le realizan operaciones elementales por columnas. También podrían realizarse unas y otras operaciones elementales en cualquier orden.

$$
\begin{aligned}
\left(\begin{array}{ccc|cccc}
2 & 1 & 2 & 1 & 0 & 0 & 0\\
1 & 2 & 2 & 0 & 1 & 0 & 0\\
2 & 1 & 2 & 0 & 0 & 1 & 0\\
1 & 2 & 2 & 0 & 0 & 0 & 1
\end{array}\right)& \sim_f 
\left(\begin{array}{ccc|cccc}
2 & 1 & 2 & 1 & 0 & 0 & 0\\
1 & 2 & 2 & 0 & 1 & 0 & 0\\
0 & 0 & 0 & -1 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & -1 & 0 & 1
\end{array}\right)\sim_f 
\left(\begin{array}{ccc|cccc}
1 & 1/2 & 1 & 1/2 & 0 & 0 & 0\\
0 & 3/2 & 1 & -1/2 & 1 & 0 & 0\\
0 & 0 & 0 & -1 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & -1 & 0 & 1
\end{array}\right)\\
& \sim_f \left(\begin{array}{ccc|cccc}
1 & 1/2 & 1 & 1/2 & 0 & 0 & 0\\
0 & 1/2 & 1/3 & -1/6 & 1/3 & 0 & 0\\
0 & 0 & 0 & -1 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & -1 & 0 & 1
\end{array}\right)\sim_f 
\left(\begin{array}{ccc|cccc}
1 & 0 & 2/3 & 2/3 & -1/3 & 0 & 0\\
0 & 1/2 & 1/3 & -1/6 & 1/3 & 0 & 0\\
0 & 0 & 0 & -1 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & -1 & 0 & 1
\end{array}\right)\\
&\sim_f \left(\begin{array}{ccc|cccc}
1 & 0 & 2/3 & 2/3 & -1/3 & 0 & 0\\
0 & 1 & 2/3 & -1/3 & 2/3 & 0 & 0\\
0 & 0 & 0 & -1 & 0 & 1 & 0\\
0 & 0 & 0 & 0 & -1 & 0 & 1
\end{array}\right)
\end{aligned}
$$

Ahora por columnas

$$
\left(\begin{array}{ccc}
1 & 0 & 2/3 \\
0 & 1 & 2/3 \\
0 & 0 & 0  \\
0 & 0 & 0  \\
\hline
1 & 0 & 0 \\
0 & 1 & 0\\
0 & 0 & 1
\end{array}\right)\sim_c
\left(\begin{array}{ccc}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 0  \\
0 & 0 & 0  \\
\hline
1 & 0 & -2/3 \\
0 & 1 & -2/3\\
0 & 0 & 1
\end{array}\right).
$$

Luego, una solución (hay muchas) es 

$$
Q=
\left(\begin{array}{cccc}
 2/3 & -1/3 & 0 & 0\\
 -1/3 & 2/3 & 0 & 0\\
 -1 & 0 & 1 & 0\\
 0 & -1 & 0 & 1
\end{array}\right),  \hspace{2cm}  
P=\left(\begin{array}{ccc}
1 & 0 & -2/3 \\
0 & 1 & -2/3\\
0 & 0 & 1
\end{array}\right).
$$
::::
:::::


::::: {#exr-14 .medio}

Dada la matriz

$$
A= \left(\begin{array}{rrrr}
a & 1 & 0 & 1\\
1 & a & 0 & 1\\
1 & 0 & a & 1\\
1 & 0 & 1 & a
\end{array}\right).
$$

<ol type="a">
<li>Calcula el determinante de $A$.</li>
<li>Determina los valores de $a$ para los que la forma de Hermite por filas de $A$ es $I_4$.</li>
<li>Estudia el rango de $A$ para todos los valores reales de $a$.</li>
<li>Para $a=-2$ calcula la forma de Hermite por filas de $A$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Calcular el determinante de $A$.

$$\begin{aligned}
|A| & = \left|\begin{array}{rrrr}
a & 1 & 0 & 1\\
1 & a & 0 & 1\\
1 & 0 & a & 1\\
1 & 0 & 1 & a
\end{array}\right|=\begin{array}{l}\text{restamos a cada fila}\\ \text{la anterior,} \\ \text{empezando desde arriba} \end{array}  = \left|\begin{array}{rrrr}
a-1 & 1-a & 0 & 0\\
0 & a & -a & 1\\
0 & 0 & a-1 & 1-a\\
1 & 0 & 1 & a
\end{array}\right|\\
& =\begin{array}{l}\text{desarrollando}\\ \text{por la primera fila} \end{array}  = 
(a-1)\left|  \begin{array}{ccc}
 a & -a & 0 \\
0 & a-1 & 1-a \\
 0 & 1 & a \\
 \end{array} 
 \right| + (-1)^{1+2}(1-a) \left|  \begin{array}{ccc}
0 & -a & 0 \\
0 & a-1 & 1-a \\
 1 & 1 & a \\
 \end{array}
 \right|\\
& =(a-1)a[a(a-1)+(a-1)]+(1-a)[a(1-a)]=(a-1)^2a(a+1)+(a-1)^2a\\
& =(a-1)^2a[a+1+1]=(a-1)^2a(a+2).
\end{aligned}
$$
</li> 

<li>Determinar los valores de $a$ para los que la forma de Hermite por filas de $A$ es $I_4$.

Por el Teorema de las matrices regulares, la forma de Hermite por filas es $I_4$ sí y sólo sí $|A|\neq 0$, luego ocurre para todo $a\in\mathbb{R}\setminus\{-2,0,1\}$, esto es , si $a\neq -2, 0, 1$.
</li>

<li>Estudiar el rango de $A$.

Si  $a\neq -2, 0, 1$, entonces el $\operatorname{rg}(A)=4$.


Si $a=1$:

$$
\left|
    \begin{array}{cccc}
      1 & 1 & 0 & 1 \\
      1 & 1 & 0 & 1 \\
      1 & 0 & 1 & 1 \\
      1 & 0 & 1 & 1 \\
    \end{array}
  \right| \sim_f\left| \begin{array}{cccc}
      1 & 1 & 0 & 1 \\
      0 & -1 & 1 & 0  \\
      0 & 0 & 0 & 0 \\
      0 & 0 & 0 & 0 \\
    \end{array}
  \right| \Rightarrow \operatorname{rg}(A)=2. 
$$
  
Si $a=0$:

$$
\left|
    \begin{array}{cccc}
      0 & 1 & 0 & 1 \\
      1 & 0 & 0 & 1 \\
      1 & 0 & 0 & 1 \\
      1 & 0 & 1 & 0 \\
    \end{array}
  \right| \sim_c\left| \begin{array}{cccc}
      1 & 0 & 0 & 0 \\
      0 & 1 & 0 & 0  \\
      0 & 1 & 0 & 0 \\
      0 & 0 & 1 & 0 \\
    \end{array}
  \right| \Rightarrow \operatorname{rg}(A)=3. 
$$
  
  
Si $a=-2$:

$$
\left|
    \begin{array}{cccc}
      -2 & 1 & 0 & 1 \\
      1 & -2 & 0 & 1 \\
      1 & 0 & -2 & 1 \\
      1 & 0 & 1 & -2 \\
    \end{array}
  \right| \sim_f\left| \begin{array}{cccc}
      1 & 0 & 1 & -2 \\
      0 & 1 & 2 & -3  \\
      0 & -2 & -1 & 3 \\
      0 & 0 & -3 & 3 \\
    \end{array}
  \right| \sim_f \left| \begin{array}{cccc}
      1 & 0 & 1 & -2 \\
      0 & 1 & 2 & -3  \\
      0 & 0& 3 & -3 \\
      0 & 0 & -3 & 3 \\
    \end{array}
  \right| \sim_f \left| \begin{array}{cccc}
      1 & 0 & 0 & -1 \\
      0 & 1 & 0 & -1  \\
      0 & 0& 1 & -1 \\
      0 & 0 & 0& 0 \\
    \end{array}
  \right|    .
$$
  
Luego $\operatorname{rg}(A)=3$.
</li>

<li>Para $a=-2$ calcula la forma de Hermite por filas de $A$.

Se ha calculado en el apartado anterior, 

$$
H=\left( \begin{array}{cccc}
      1 & 0 & 0 & -1 \\
      0 & 1 & 0 & -1  \\
      0 & 0& 1 & -1 \\
      0 & 0 & 0& 0 \\
    \end{array}
\right).
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix(QQ,[[-2,1,0,1],[1,-2,0,1],[1,0,-2,1],[1,0,1,-2]])
show(A,"~",A.rref())
</script>
:::
</li>
</ol>
::::
:::::


::::: {#exr-15 .avanzado}

Se consideran las matrices:

$$
A=\begin{pmatrix}
-1 & -a & a-1 \\
2a-1 & a & a-1 \\
1-2a & 0 & 1
\end{pmatrix},\;\;\;\;
B=\begin{pmatrix}
2 & 3 & 4\\
-2 &-3 &-4 \\
3 & 4 & 5
\end{pmatrix}.
$$

<ol type="a">
<li>Determinar para qué valores del parámetro $a$ es la matriz $A$ invertible.</li>
<li>Determinar para qué valores del parámetro $a$ existe una matriz $P$ regular de forma que $B=A\cdot P$.</li>
<li>Determinar para qué valores del parámetro $a$ existe una matriz $P$ de forma que $B=A\cdot P$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}

<ol type="a">
<li>Determinar para qué valores del parámetro $a$ es la matriz $A$ invertible.

La matriz $A$ es invertible si, y solo si, su determinante es distinto de cero. Calculamos el determinante realizando primero algunas operaciones elementales:

$$
|A|=\left|\begin{array}{ccc}
-1 & -a & a-1 \\
2a-1 & a & a-1 \\
1-2a & 0 & 1
\end{array}\right|= \left|\begin{array}{ccc}
-1 & -a & a-1 \\
0 & a & a \\
1-2a & 0 & 1
\end{array}\right|=\left|\begin{array}{ccc}
-1 & 0 & 2a-1 \\
0 & a & a \\
1-2a & 0 & 1
\end{array}\right|,
$$

y desarrollando por la segunda columna,

$$
\left|\begin{array}{ccc}
-1 & 0 & 2a-1 \\
0 & a & a \\
1-2a & 0 & 1
\end{array}\right|=a(-1+(2a-1)^2)=a(4a^2-4a)=4a^2(a-1).
$$

Así, que $A$ tiene inversa cuando $a\not = 0,1$.
</li>

<li>Determinar para qué valores del parámetro $a$ existe una matriz $P$ regular de forma que $B=A\cdot P$.

Para que exista esa matriz regular $P$ (que representa la composición de operaciones elementales y en este caso por columnas porque está a la derecha de A) deben ser $A$ y $B$ equivalentes por columnas, es decir, deben tener la misma forma de Hermite por columnas.

Entonces calculamos la de $B$:

$$
B=\begin{pmatrix}
2 & 3 & 4\\
-2 &-3 &-4 \\
3 & 4 & 5
\end{pmatrix}\sim_c \begin{pmatrix}
2 & 3 & 0\\
-2 &-3 &0 \\
3 & 4 & -1
\end{pmatrix} \sim_c \begin{pmatrix}
2 & 3 & 0\\
-2 &-3 &0 \\
0 & 0 & 1
\end{pmatrix} \sim_c \begin{pmatrix}
1 & 0 & 0\\
-1 &0 &0 \\
0 & 1 & 0
\end{pmatrix}.
$$

Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
B=matrix([[2,3,4],[-2,-3,-4],[3,4,5]])
show(B,"~",(B.T).rref().T)
</script>
:::

Puesto que $\operatorname{rg}(B)=2$ solo es posible que sean equivalentes por columnas cuando $a=0$ o $a=1$, porque en otro caso $A$ tiene rango tres.

Calculamos la forma de Hermite de $A$ en ambos casos:

$$
A=\begin{pmatrix}
-1 & 0 & -1 \\
-1 & 0 & -1 \\
1 & 0 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
-1 & 0 & 0 \\
-1 & 0 & 0 \\
1 & 0 & 0
\end{pmatrix}.
$$ 

En el caso $a=0$ no existe $P$ regular.

$$
A=\begin{pmatrix}
-1 & -1 & 0 \\
1 & 1 & 0 \\
-1 & 0 & 1
\end{pmatrix}\sim_c \begin{pmatrix}
1 & 0 & 0\\
-1 &0 &0 \\
0 & 1 & 0
\end{pmatrix}. 
$$
</li>

<li>Determinar para qué valores del parámetro $a$ existe una matriz $P$ de forma que $B=A\cdot P$.

Como hemos razonado en el caso anterior, $P$ existe para $a=1$ y es regular. Cuando $a\not=0,1$ como $A$ es regular, podemos despejar $P$ en la fórmula $B=AP$:

$$
P=A^{-1}B,
$$

que existe, aunque no es regular porque $B$ no lo es. Así que existe una tal $P$ para todo $a$ salvo $a=0$.
</li>
</ol>
::::
:::::


::::: {#exr-16 .basico}

Discutir en función de los parámetros $a$ y $b$ el sistema de ecuaciones lineales:

$$
\left\{
\begin{array}{rcl}
x+y+z &=& 1, \\
x+y+az &=& 2, \\
x+y+bz &=& 3. \\
\end{array}
\right.
$$

y resolverlo en aquellos casos en que sea compatible.

:::: {.callout collapse="true" title="Solución"}

La matriz de coeficientes del sistema 

$$
\begin{pmatrix}
1 & 1 & 1\\
1 & 1 & a\\
1 & 1 & b
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 1 & 1\\
0 & 0 & a-1\\
0 & 0 & b-1
\end{pmatrix},
$$

tiene rango 1 si $a=b=1$ y rango 2 en otro caso.
La matriz ampliada del sistema 

$$
\begin{pmatrix}
1 & 1 & 1 & 1\\
1 & 1 & a & 2\\
1 & 1 & b & 3
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 1 & 1 & 1 \\
0 & 0 & a-1 & 1\\
0 & 0 & b-1 & 2
\end{pmatrix},
$$

tiene rango 2 si $b-1=2(a-1)$ ( o lo que es lo mismo $b=2a-1$, que incluye el caso $a=b=1$) y rango 3 en cualquier otro caso.

Así, el sistema es compatible si, y solo si, $b= 2a-1$ y $a\not = 1$ y en esos casos, como $\operatorname{rg}(A)=\operatorname{rg}(A|B)=2$, que es menor que el número de incógnitas, el sistema es compatible Indeterminado dependiendo de un parámetro. En el resto de los casos es (cuando $a=b=1$ o bien cuando $b\not = 2a-1$) es incompatible.

Cuando $b=2a-1$ y $a\not = 1$, resolviendo desde la matriz anterior 

$$
\begin{pmatrix}
1 & 1 & 1 & 1 \\
0 & 0 & a-1 & 1\\
0 & 0 & 2(a-1) & 2
\end{pmatrix}\sim_f \begin{pmatrix}
1 & 1 & 1 & 1 \\
0 & 0 & a-1 & 1\\
0 & 0 & 0 & 0
\end{pmatrix},
$$

y el conjunto de soluciones es

$$
\left\{ \left(1-\lambda-\frac{1}{a-1}  , \lambda, \frac{1}{a-1}\right); \lambda \in \mathbb{R} \right\}.
$$
::::
:::::


::::: {#exr-17 .medio}

Dadas las matrices 
$$
A=\left(\begin{array}{rrr}
   1 & a & -1\\
   a & 1 & 1\\
   1 & -1 & a\\
  0 & 0 & a
  \end{array}
\right),\,\,\,\,
B=\left(\begin{array}{rrr}
   1 & -1 & 1\\
   1 & 1 & 0\\
   0 & -b & b\\
  b & b & 0
  \end{array}
\right)
$$

<ol type="a">
<li>Encuentra los valores de $a$ y $b$ para los que las matrices $A$ y $B$ sean equivalentes.</li>
<li>Encuentra los valores de $a$ y $b$ para los que las matrices $A$ y $B$ sean equivalentes por filas.</li>
<li>Para la pareja de valores $a=0$, $b=1$, calcula una matriz $Q$ tal que $QA=B$.</li>
</ol>

:::: {.callout collapse="true" title="Solución"}


<ol type="a">
<li>Encontrar los valores de $a$ y $b$ para los que las matrices $A$ y $B$ sean equivalentes.

Dos matrices del mismo orden son equivalentes cuando tienen el mismo rango.  Calculamos el rango en función de los parámetros:
en ambos casos elegiremos una submatriz cuadrada de orden 3 y calculamos el determinante.

Para $A$ elegimos

$$
\left|\begin{array}{rrr}
      a & 1 & 1\\
   1 & -1 & a\\
  0 & 0 & a
  \end{array}
\right|= a\left|\begin{array}{rr}
    a & 1 \\
   1 & -1 \\
    \end{array}
\right|= a(-a-1).$$
Así que si $a\not =0, a\not = -1$, $\operatorname{rg}(A)=3$.

Para $a=0$
$$A=\left(\begin{array}{rrr}
   1 & 0 & -1\\
   0 & 1 & 1\\
   1 & -1 & 0\\
  0 & 0 & 0
  \end{array}
\right) \sim_{f} \left(\begin{array}{rrr}
   1 & 0 & -1\\
   0 & 1 & 1\\
   0 & -1 & 1\\
  0 & 0 & 0
  \end{array}
\right) \sim_{f} \left(\begin{array}{rrr}
   1 & 0 & -1\\
   0 & 1 & 1\\
   0 & 0 & 2\\
  0 & 0 & 0
  \end{array}
\right) \sim_{f} \left(\begin{array}{rrr}
   1 & 0 & 0\\
   0 & 1 & 0\\
   0 & 0 & 1\\
  0 & 0 & 0
  \end{array}
\right),
$$

tiene también rango tres y la anterior es su forma de Hermite por filas.


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
A=matrix([[1,0,-1],[0,1,1],[1,-1,0],[0,0,0]])
show(A,"~",A.rref())
</script>
:::

Para $a=-1$

$$
A=\left(\begin{array}{rrr}
   1 & -1 & -1\\
   -1 & 1 & 1\\
   1 & -1 & -1\\
  0 & 0 & -1
  \end{array}
\right)\sim_{f} \left(\begin{array}{rrr}
   1 & -1 & -1\\
   0 & 0 & 0\\
   0 & 0 & 0\\
  0 & 0 & -1
  \end{array}
\right)\sim_{f} \left(\begin{array}{rrr}
   1 & -1 & 0\\
  0 & 0 & 1\\
   0 & 0 & 0\\
   0 & 0 & 0\\

  \end{array}
\right).
$$  

tiene rango dos y la anterior es su forma de Hermite por filas.


Para $B$:

$$
\left|\begin{array}{rrr}
   1 & -1 & 1\\
   1 & 1 & 0\\
   0 & -b & b\\
    \end{array}
\right|=\left|\begin{array}{rrr}
   1 & -1 & 1\\
   0 & 2 & -1\\
   0 & -b & b\\
    \end{array}
\right|=\left|\begin{array}{rr}
    1 & 0\\
    -b & b\\
    \end{array}
\right|=b.
$$

Así, cuando $b\not = 0$, $\operatorname{rg}(B)=3$.
Para $b=0$

$$
B=\left(\begin{array}{rrr}
   1 & -1 & 1\\
   1 & 1 & 0\\
   0 & 0 & 0\\
  0 & 0 & 0
  \end{array}
\right)\sim_{f} \left(\begin{array}{rrr}
   1 & -1 & 1\\
   0 & 2 & -1\\
   0 & 0 & 0\\
  0 & 0 & 0
  \end{array}
\right)\sim_{f} \left(\begin{array}{rrr}
   1 & 0 & 1/2\\
   0 & 1 & -1/2\\
   0 & 0 & 0\\
  0 & 0 & 0
  \end{array}
\right),
$$

que tiene rango dos y tenemos su forma de Hermite por filas.


Comprobemos el resultado obtenido con <code>sage</code>.

::: {.sage}
<script type="text/x-sage">
B=matrix([[1,-1,1],[1,1,0],[0,0,0],[0,0,0]])
show(B,"~",B.rref())
</script>
:::

Por tanto, concluimos que si $a=-1$ y $b=0$, o bien, $a\neq-1$ y $b\neq0$, son equivalentes mientras que si $a=-1$ y $b\neq0$, o bien, $a\neq-1$ y $b=0$, no son equivalentes.
</li>

<li>Encontrar los valores de $a$ y $b$ para los que las matrices $A$ y $B$ sean equivalentes por filas.

En el caso de que una matriz $4\times 3$ tenga rango tres, su forma de Hermite por filas es necesariamente 

$$
H= \left(\begin{array}{rrr}
   1 & 0 & 0\\
   0 & 1 & 0\\
   0 & 0 & 1\\
  0 & 0 & 0
  \end{array}
\right),
$$

puesto que cada uno de los tres pivotes tienen que estar en columnas distintas. Así que tenemos calculada la forma de Hermite en todos los casos y podemos concluir que no serán equivalentes por filas excepto si $a\neq-1$ y $b\neq0$.
</li>

<li>Para la pareja de valores $a=0$, $b=1$, calcular una matriz $Q$ tal que $QA=B$.

En ese caso las matrices son equivalentes por filas, para encontrar una matriz $Q$, calculamos $Q_1$ y $Q_2$ tales que:

$$ 
Q_{1}A=H,  \hspace{2cm} Q_{2}B=H.
$$

Igualando y despejando $B$ sería $Q=Q_{2}^{-1}Q_{1}$. 
</li>
</ol>
::::
:::::