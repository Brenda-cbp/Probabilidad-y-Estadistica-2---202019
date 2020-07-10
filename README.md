# Probabilidad y Estadística 2 (IIND2107) - 202019
### Universidad de los Andes

Este curso presenta conceptos básicos para la aplicación de modelos estadísticos que buscan explicar una variable de interés a partir de un grupo de variables independientes. Dos formas generales de modelos serán estudiadas: modelos de comparación de medias cuando las variables explicativas son categóricas y modelos de regresión lineal cuando son continuas. Los primeros modelos se usan en el contexto de Diseño y Análisis de Experimentos estadísticos y se fundamentan en las pruebas de Análisis de Varianza. Los modelos de regresión lineal explican la variable de interés mediante una ecuación lineal en las demás variables y cuyos coeficientes son los parámetros de interés. 

Los objetivos primarios de curso son: 
* Desarrollar la capacidad de formular modelos estadísticos apropiados para describir fenómenos aleatorios
* Desarrollar habilidades para diseñar y analizar experimentos estadísticos 
* Comprender los conceptos fundamentales de los modelos vistos en el curso, incluyendo sus supuestos y limitaciones
* Aprender a utilizar herramientas computacionales que permitan la correcta aplicación de los métodos vistos 
* Desarrollar habilidades para el análisis, comprensión y comunicación de resultados 

**Profesor:** Nicolás Mejía Martínez - n.mejia10@uniandes.edu.co

**Asistente Graduada:** Diana Cassiani - ds.cassiani10@uniandes.edu.co 

## Recursos
* Para las clases utilizaremos Zoom, siempre en la misma sala.
* Para las comunicaciones nos pueden escribir por correo o preferiblemente utilizar el espacio de trabajo de Slack.
* Los videos de las clases quedarán guardados en una carpeta compartida de OneDrive a la cual pueden acceder usando su cuenta uniandes.
* Las presentaciones, ejercicios, tutoriales de R los pueden encontrar actualizados en este repositorio o publicados en la página del curso de SicuaPlus corto tiempo después.
* El software recomendado para el desarrollo de tareas/proyectos/quices es R. Les dejo unos tutoriales para descargarlo en [Windows](https://medium.com/@GalarnykMichael/install-r-and-rstudio-on-windows-5f503f708027) y en [Mac](https://medium.com/@GalarnykMichael/install-r-and-rstudio-on-mac-e911606ce4f4)
* A la hora de programar [StackOverflow](https://stackoverflow.com/) es su mejor amigo. StackOverflow es un sitio de preguntas y respuestas acerca de funciones, comandos o simplemente formas de abordar problemas utilizando los lenguajes de programación más populares, entre ellos R.
## Casos
Al finalizar cada una de las partes del curso veremos un caso de aplicación donde solucionaremos un problema del mundo real con las herramientas que vimos en la sección de curso.
* Caso 1: TBA
* Caso 2: TBA

## Contenido


<table>
<thead>
  <tr>
    <th>Tema</th>
    <th>Sesión</th>
    <th>Presentaciones</th>
    <th>Ejercicios </th>
    <th>Notebooks </th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="9">Diseño de Experimentos</td>
    <td>1. Estadística Inferencial </td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%201%20-%20Inferencia%20Estadística.pdf">Presentación 1</a></td>
    <td><a href = "https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%201.pdf">Clase 1</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Tutoriales%20R/R%20-%20Cheatsheet.pdf">Cheatsheet</a><br><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Tutoría-R.html">Tutorial R</a></td>
  </tr>
  <tr>
    <td>2. Introducción al diseño de experimentos</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%202%20-%20Introducción%20al%20Diseño%20de%20Experimentos.pdf">Presentación 2</a></td>
    <td><a href = "https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%202.pdf">Clase 2 </a></td>
    <td><a href = "https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Pruebas%20T.html">Pruebas T</a></td>
  </tr>
  <tr>
    <td>3. ANOVA de 1 Factor</td>
    <td><a href = "https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%203%20-%20ANOVA%20de%201%20Factor.pdf">Presentación 3</a> <br> <a href = "https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%204%20-%20ANOVA%20de%201%20Factor%20Otros%20Detalles.pdf">Presentación 4</a><br></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%203.pdf">Clase 3</a></td>
    <td><a href ="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/ANOVA%201%20Factor.html">ANOVA 1 Factor</a></td>
  </tr>
  <tr>
    <td>4. ANOVA de 2 Factores</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%204%20-%20ANOVA%20de%202%20Factores%20(Bloques).pdf">Presentación 5</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%204.pdf">Clase 4</a></td>
    <td><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/ANOVA%202%20Factores.html">ANOVA 2 Factores</a></td>
  </tr>
  <tr>
    <td>5. ANOVA de 2 Factores con Interacción</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%205%20-%20ANOVA%20de%202%20Factores%20con%20Interacción.pdf">Presentación 6</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%205.pdf">Clase 5</a></td>
    <td><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/ANOVA%203%20Factores.html">Interacción</a></td>
  </tr>
  <tr>
    <td>6. Diseños Multifactoriales</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%206%20-%20Diseños%20Multifactoriales.pdf">Presentación 7</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%206.pdf">Clase 6</a></td>
    <td><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Diseños%20Multifactoriales.html">ANOVA 3 Factores</a></td>
  </tr>
  <tr>
    <td>7. Pruebas de Contraste</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%207%20-%20Pruebas%20de%20Contraste.pdf">Presentación 8</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%207.pdf">Clase 7</a></td>
    <td></td>
  </tr>
  <tr>
    <td>8. Múltiples Contrastes</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%208%20-%20Mu%CC%81ltiples%20Contrastes.pdf">Presentación 9</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%208.pdf">Clase 8</a></td>
    <td><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Tukey.html">Tukey</a></td>
  </tr>
  <tr>
    <td>9. Validación Supuestos ANOVA</td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%209%20-%20Heteroscedasticidad.pdf">Presentación 10</a><br>
    <a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Presentaciones/Clase%209%20-%20Validacio%CC%81n%20ANOVA.pdf">Presentación 11</a></td>
    <td><a href="https://github.com/nmejia10/Probabilidad-y-Estadistica-2---202019/blob/master/Ejercicios/Ejercicios%20Clase%209.pdf">Clase 9</a></td>
    <td><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Heteroscedasticidad.html">Heteroscedasticidad</a><br><a href="https://nmejia10.github.io/Probabilidad-y-Estadistica-2---202019/Tutoriales%20R/Validacion.html">Validación</a></td>
  </tr>

</tbody>
</table>

## Bibliografía
* Walpole, R.; Myers, S.; Ye, K. (2012) [Probabilidad y Estadística para ingeniería y ciencias](https://vereniciafunez94hotmail.files.wordpress.com/2014/08/8va-probabilidad-y-estadistica-para-ingenier-walpole_8.pdf). Octava edición. Prentice Hall. 
* Montgomery, D. (2013) [Design and analysis of experiments](http://faculty.business.utsa.edu/manderso/STA4723/readings/Douglas-C.-Montgomery-Design-and-Analysis-of-Experiments-Wiley-2012.pdf). Eighth edition. John Wiley and Sons. 
* Neter, J.; Kutner, M.; Nachtsheim, C.; Wasserman, W. (1996) [Applied Linear Statistical Models](http://users.stat.ufl.edu/~rohitpatra/4210/KNNL.pdf). Fourth edition. Irwin. 
* Gujarati, D.; Porter, D. (2010) [Econometría](https://www.academia.edu/33064534/Gujarati_-_Econometría_-_5ta_Edición.pdf). Quinta edición. McGraw Hill 

## Articulos de Interés
* [How Data Scientists Turned Against Statistics](https://www.forbes.com/sites/kalevleetaru/2019/03/07/how-data-scientists-turned-against-statistics/)
* [Role of Statistics in Data Science](https://blog.floydhub.com/statistics-for-data-science/)
* [ANOVA 1 factor en R](http://rstudio-pubs-static.s3.amazonaws.com/252809_ce002d0706444317b41f0cff7c2c494d.html)
* [Regresion Lineal en R](https://rpubs.com/bitettir/simpleregression)
* [Fighting the Coronavirus with Statistics](https://www.analyticsvidhya.com/blog/2020/06/introduction-anova-statistics-data-science-covid-python/)
* [Practical K means Clustering in R](https://uc-r.github.io/kmeans_clustering)
 
 ********
**Este es un curso increíblemente útil, que cubre temas muy interesantes y para nada complicados :bar_chart: , los cuales nos dan abren la puerta a un conjunto de aplicaciones, modelos y habilidades gigantesca. Aprovechenlo lo mas que puedan.** 

**Esperamos disfruten el curso, tanto como nosotros disfrutamos darlo.** :sunglasses:         
