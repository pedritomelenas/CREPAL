# CREPAL
## Archivos H5P de Autoevaluación de Álgebra Lineal

Los archivos formato [H5P](https://h5p.org/) han sido creados a través del sitio web [LUMI](https://app.lumi.education/) para agregar cuestionarios de ejercicios interactivos para el alumnado. Para futuras revisiones y/o modificaciones de dichos cuestionarios, importar los archivos .h5p en LUMI y editarlos según sea necesario, exportándolos después tanto en formato .h5p como .html

Los cuestionarios han sido elaborados por [Juan Francisco Ocaña Rivas](https://github.com/jfocana) a partir de ejercicios redactados y resueltos por Evangelina Sántos Aláez.

Estos archivos forman parte del Proyecto de Innovación Docente PID-24-117 "Creación de Repositorio de Ejercicios para Álgebra Lineal (CREPAL)" aprobado en la convocatoria 2024-25 (Plan AcademiaUGR) de la Universidad de Granada.

## Notas para futuros editores 

Tener en cuenta que los archivos .h5p utilizan "\(...\)" y "\[...\]" para el formato de matemáticas de LaTeX, y no reconoce bien "\$...\$" y "$$...$$". 
Por tanto, si se desea incluir expresiones matemáticas en los textos de las preguntas, respuestas, etc., utilizar siempre "\(...\)" y "\[...\]".
Si los archivos LaTeX de origen utilizan "$...$" y "$$...$$" (así es como Eva suele escribir), habrá que sustituirlos por "\(...\)" y "\[...\]" antes de importar los ejercicios a LUMI, para lo cual recomiendo seguir las instrucciones del siguiente enlace:

[Instrucciones para reemplazar símbolos de LaTeX de forma rudimentaria](https://tex.stackexchange.com/questions/118021/how-to-replace-all-by/707974#707974)

Estas instrucciones son aptas tanto para el editor de LaTeX Overleaf como para trabajar desde VS Code, y son válidas para cualquier otro editor de texto que permita buscar y reemplazar utilizando "regular expressions" (regex). Aunque no está mencionado, para evitar errores se ha de reemplazar primeramente los símbolos de doble dólar "$$...$$" y después los de un solo dólar "$...$". 

Existen algunos scripts que podrían automatizar este proceso, pero no he comprobado su buen funcionamiento y la solución anterior me parece lo suficientemente eficiente, por lo que no los incluyo aquí.