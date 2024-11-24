<!-- LTeX: language=es --->

# Instrucciones básicas

Los ejercicios tienen la siguiente estructura básica.

```
::::: {#exr-identificador}

Enunciado del ejercicio

:::: {.callout collapse="true" title="Solución"}

Solución del ejercicio

::::
:::::
```

El `identificador` puede ser cualquier cadena de caracteres. Inicialmente he usado números para los que se introdujeron en la primera fase, salvo en el fichero `resueltos-examenes.md` que he usado la numeración `oN` con `N` un número.

## Clasificación de ejercicios

Hay dos tipos de clasificación: 

- dependiendo de si el ejercicio contiene o no cuerpos finitos,

- dependiendo de la dificultad.

Si un ejercicio involucra operaciones en cuerpos finitos tendrá una cabecera de la forma 

```
::::: {#exr-identificador .cuerpo_finito}
```

La dificultad puede ser básico, medio o avanzado. Así un ejercicio con dificultad básica que no trate de cuerpos finitos se etiquetará como sigue.

```
::::: {#exr-identificador .basico}
```

Mientras que si conlleva operaciones en cuerpos finitos, se etiqueta así:

```
::::: {#exr-identificador .cuerpo_finito-basico}
```


## Celdas `sagemath`

Para introducir una celda en `sagemath` usamos la siguiente sintaxis.

```
::: {.sage}
<script type="text/x-sage">
código en sagemath
</script>
:::
```

