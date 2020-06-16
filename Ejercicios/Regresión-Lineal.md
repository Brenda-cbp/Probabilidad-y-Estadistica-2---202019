Probabilidad y Estadística 1: Regresión Lineal
================
Nicolás Mejía & Tatiana Laverde


## 1. Introducción
===============

Los modelos de regresión lineal buscar explicar el comportamiento de una variable aleatoria **Y** en funcion de un grupo de variables aleatorias **X**. Se asume que existe una relación lineal entre la variable dependiente (*Y*) y las variables independientes, la cual se puede expresar de la forma:

*Y* = *β**X* + *ϵ*
 Si se tiene una única variable *X* se llama regresión simple y de lo contrario es una regresión múltiple.

Asi mediante una muestra se busca determinar la relacion entre las *X*′*s* y *Y*, mediante procedimientos de inferencia estadística:

-   Estimación de los parámetros ($\\hat{\\beta}, \\hat{\\sigma^2}$)
-   Pruebas de hipótesis e Intervalos de confianza sobre los parámetros.

La estimación de los parámetros se hace mediante mínimos cuadrados ordinarios (MCO), el cual busca minimizar la suma de los errores cuadráticos de estimación, en otras palabras mejorar el ajuste.

$$ \\rm{min }  \\sum\_{i=1}^n e\_i^2 = \\rm{min }  \\sum\_{i=1}^n (y\_i-\\hat{y\_i})^2 = \\rm{min }  \\sum\_{i=1}^n (y\_i - \\hat{\\beta\_0} - \\hat{\\beta\_1}x\_i)^2$$
 Lo cual da como resultado para el caso de regresion lineal simple:
$$\\hat{\\beta\_0} = \\bar{Y} - \\hat{\\beta\_1}\\bar{X}  $$
$$\\hat{\\beta\_1} = \\frac{\\sum\_{i=1}^n(x\_i - \\bar{X})(y\_i-\\bar{Y})}{\\sum\_{i=1}^n (x\_i-\\bar{X})^2} $$
 En el caso de la regresión lineal multiple las estimaciones de los parámetros que minimizan la suma de los errores cuadraticos son (en terminos matriciales):
$$\\vec\\beta = (X^TX)^{-1}X^TY$$

2. Inferencia Estadística
=========================

Un poco de notación antes de empezar:

-   Usaremos *k* para denotar el número de variables independientes (*X*) que tiene el modelo. Es decir el número de *β*′*s* de la regresión SIN contar *β*<sub>0</sub>
-   Usaremos *n* para denotar el número total de datos de la muestra.
-   Usaremos *S**S**E* para denotar la suma de cuadrados del error.
-   Usaremos *S**S**R* para denotar la suma de cuadrados de la regresión.

Existen dos principales pruebas de interés al hacer una regresión lineal: la prueba de sigificancia global y la prueba de significancia individual.

2.1 Estimador de la varianza
----------------------------

Despues de estimar el modelo se puede obtener el mejor estimador de la varianza de los errores *σ*<sup>2</sup>, el cual es:
$$\\hat\\sigma^2 = \\frac{\\sum\_{i=1}^n (e\_i - 0)^2}{n-k-1} = MSE$$

2.2. Prueba de significancia global
-----------------------------------

La prueba de significancia global prueba de forma simultanea si alguno de los betas (parámetros que acompañan a las *X*) es significativo. Es decir, si hay almenos una de las variables independientes que efectivamente explican a la variable *Y*.
$$H\_0: \\beta\_1 = \\beta\_2 = \\cdots = \\beta\_k = 0\\\\ H\_1: \\textrm{Al menos un $\\beta$ diferente de 0} $$
 El estadístico de prueba esta dado por:
$$EP = \\frac{\\frac{SSR}{glR}}{\\frac{SSE}{glE}} = \\frac{\\frac{\\sum\_{i=1}^n (\\hat{y\_i} - \\bar{Y})^2}{k}}{\\frac{\\sum\_{i=1}^n (y\_i-\\hat{y\_i})^2}{n-k-1}} \\sim F\_{k,n-k-1}  $$

Esta es una prueba de cola derecha por lo que la región de rechazo sera:
*R**C* = *F*<sub>1 − *α*, *k*, *n* − *k* − 1</sub>
 El pvalor asociado es:
*p**v**a**l**u**e* = *P*(*F*<sub>*k*, *n* − *k* − 1</sub> &gt; *E**P*)

2.3. Prueba de significancia indivual
-------------------------------------

La prueba de significancia individual prueba una por una las variables independientes para concluir si existe o no relación entre dicha *X* y la variable *Y*

$$H\_0: \\beta\_i =  0\\\\ H\_1: \\beta\_i \\neq  0 $$
 El estadístico de prueba esta dado por:

$$EP = \\frac{\\hat{\\beta\_i} - 0}{\\sqrt{Var(\\hat{\\beta\_i})}} \\sim t\_{n-k-1}$$
 Al ser una prueba de dos colas la region de rechazo está dada por:
$$ RC\_1: t\_{1-\\alpha/2,n-k-1} \\\\ RC\_2: t\_{\\alpha/2,n-k-1} $$
 El pvalor asociado es:
*p**v**a**l**u**e* = 2 \* *P*(*t*<sub>*n* − *k* − 1</sub> &gt; |*E**P*|)

2.4. Salidas del modelo de regresión
------------------------------------

De manera general con los resultados del modelo de regresión se pueden construir dos tablas (las cuales la mayoría de paquetes estadisticos entregan como salida despues de estimar el modelo). Estas tablas son:

-   La tabla ANOVA que contiene toda la información para realizar la prueba de significancia global.
-   La tabla de coeficientes que contiene toda la información para realizar las pruebas de significancia individual.

Las tablas tienen la siguiente forma:

### 2.4.1. Tabla ANOVA

| SS                                                | gl                  | MS      | F       | SIG    |
|:--------------------------------------------------|:--------------------|:--------|:--------|:-------|
| SSR = $\\sum\_{i=1}^n (\\hat{y\_i} - \\bar{Y})^2$ | glR = *k*           | SSR/glR | MSR/MSE | pvalor |
| SSE = $\\sum\_{i=1}^n (y\_i-\\hat{y\_i})^2$       | glE = *n* − *k* − 1 | SSE/glE |         |        |
| SST = $\\sum\_{i=1}^n (y\_i - \\bar{Y})^2$        | glT = *n* − 1       |         |         |        |

### 2.4.2. Tabla Coeficientes

| Variable          |     Coef (*β*)     |                E.S (*β*)               |                                 t                                | SIG    |
|:------------------|:------------------:|:--------------------------------------:|:----------------------------------------------------------------:|:-------|
| Constante         | $\\hat{\\beta\_0}$ | $\\sqrt{\\hat{Var}(\\hat{\\beta\_0})}$ | $\\frac{\\hat{\\beta\_0}}{\\sqrt{\\hat{Var(\\hat{\\beta\_0})}}}$ | pvalor |
| *X*<sub>1</sub>   | $\\hat{\\beta\_1}$ | $\\sqrt{\\hat{Var}(\\hat{\\beta\_1})}$ | $\\frac{\\hat{\\beta\_1}}{\\sqrt{\\hat{Var(\\hat{\\beta\_1})}}}$ | pvalor |
| ⋮                 |          ⋮         |                    ⋮                   |                                 ⋮                                | ⋮      |
| *X*<sub>*k*</sub> | $\\hat{\\beta\_k}$ | $\\sqrt{\\hat{Var}(\\hat{\\beta\_k})}$ | $\\frac{\\hat{\\beta\_k}}{\\sqrt{\\hat{Var(\\hat{\\beta\_k})}}}$ | pvalor |

3. Regresión Lineal en R
========================

3.1. Regresión Simple
---------------------

Antes de hacer la regresion creamos datos sintenticos.

``` r
X <- rnorm(n = 100, mean = 50, sd = 5)
Y <- 14 + 3*X + 5*rnorm(n=100)
plot(X,Y)
```

![](Regresión-Lineal_files/figure-markdown_github/unnamed-chunk-1-1.png)

### 3.1.1. Estimación

Para correr un modelo de regresión en R se utiliza el comando *l**m*

``` r
reg <- lm(Y ~ X)
summary(reg)
```

    ## 
    ## Call:
    ## lm(formula = Y ~ X)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -9.4716 -3.0800 -0.0611  2.6808 15.1958 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 20.98531    4.64985   4.513 1.78e-05 ***
    ## X            2.86216    0.09197  31.122  < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 4.649 on 98 degrees of freedom
    ## Multiple R-squared:  0.9081, Adjusted R-squared:  0.9072 
    ## F-statistic: 968.6 on 1 and 98 DF,  p-value: < 2.2e-16

Como se puede observar la tabla nos entrega toda la información necesaria para oncluir acerca del modelo de regresión que acabamos de hacer. Tiene los valores estimados de los coeficientes, sus varianzas, su estadísticos de prueba y el estadístico de la prueba de significancia global.

``` r
plot(X,Y, col = 'black')
abline(reg,col = 'red')
```

![](Regresión-Lineal_files/figure-markdown_github/unnamed-chunk-3-1.png)

Con un poco de programación se pueden encontrar las sumas de cuadrados y los grados de libertad para realizar las pruebas a mano

``` r
yhat <- reg$fitted.values #Las predicciones del modelo
```

    ## SSR: 20929.44 
    ## SSE: 2117.641 
    ## SST: 23047.08

    ## glR: 1 
    ## glE: 98 
    ## glT: 99

### 3.1.2. Prueba de significancia global

``` r
EP <-  (SSR/glR)/(SSE/glE)
pvalue <- 1-pf(EP,glR,glE)
cat('Se rechaza la hipótesis nula ya que el pvalor de', pvalue, 'es menor a la significancia')
```

    ## Se rechaza la hipótesis nula ya que el pvalor de 0 es menor a la significancia

### 3.1.3. Prueba de significancia individual

``` r
var_beta <- (SSE/glE)/sum((X-mean(X))^2) 
beta_hat<-reg$coefficients[2]
EP <-  (beta_hat-0)/sqrt(var_beta)
pvalue <- 2*(1-pt(abs(EP),glE))
cat('Se rechaza la hipótesis nula ya que el pvalor de', pvalue, 'es menor a la significancia')
```

    ## Se rechaza la hipótesis nula ya que el pvalor de 0 es menor a la significancia

3.2 Regresión Multiple
----------------------

``` r
X1 <- rnorm(n = 100, mean = 50, sd = 5)
X2 <- rnorm(n = 100, mean = 50, sd = 5)
X3 <- rnorm(n = 100, mean = 50, sd = 5)
Y <- 14 + 3*X - 5*X2 + 0.7*X3 + 10*rnorm(n=100)
```

Para estimar un modelo de regresión múltiple basta con especificar la ecuación de la recta en el comando *l**m*

``` r
reg <- lm(Y ~ X1+X2+X3)
summary(reg)
```

    ## 
    ## Call:
    ## lm(formula = Y ~ X1 + X2 + X3)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -47.770 -10.746   1.274  12.676  38.427 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 217.4610    30.0932   7.226 1.19e-10 ***
    ## X1           -0.5832     0.3396  -1.717   0.0892 .  
    ## X2           -5.1018     0.3293 -15.492  < 2e-16 ***
    ## X3            0.3484     0.3338   1.044   0.2993    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 18.02 on 96 degrees of freedom
    ## Multiple R-squared:  0.7151, Adjusted R-squared:  0.7062 
    ## F-statistic: 80.31 on 3 and 96 DF,  p-value: < 2.2e-16
