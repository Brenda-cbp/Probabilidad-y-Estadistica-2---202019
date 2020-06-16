---
title: "Probabilidad y Estadística 1: Regresión Lineal"
author: "Nicolás Mejía & Tatiana Laverde"
output: 
  html_document:
    toc: true
    toc_depth: 5
    theme: united
    keep_md: true
---
<style>
body {
text-align: justify}
</style>

# 1. Introducción

Los modelos de regresión lineal buscar explicar el comportamiento de una variable aleatoria *$Y$* en funcion de un grupo de variables aleatorias *$X$*. Se asume que existe una relación lineal entre la variable dependiente ($Y$) y las variables independientes, la cual se puede expresar de la forma:

$$ Y = \beta X + \epsilon$$
Si se tiene una única variable $X$ se llama regresión simple y de lo contrario es una regresión múltiple.

Asi mediante una muestra se busca determinar la relacion entre las $X's$ y $Y$, mediante procedimientos de inferencia estadística: 

* Estimación de los parámetros ($\hat{\beta}, \hat{\sigma^2}$)
* Pruebas de hipótesis e Intervalos de confianza sobre los parámetros.

La estimación de los parámetros se hace mediante mínimos cuadrados ordinarios (MCO), el cual busca minimizar la suma de los errores cuadráticos de estimación, en otras palabras mejorar el ajuste.

$$ \rm{min }  \sum_{i=1}^n e_i^2 = \rm{min }  \sum_{i=1}^n (y_i-\hat{y_i})^2 = \rm{min }  \sum_{i=1}^n (y_i - \hat{\beta_0} - \hat{\beta_1}x_i)^2$$
Lo cual da como resultado para el caso de regresion lineal simple:
$$\hat{\beta_0} = \bar{Y} - \hat{\beta_1}\bar{X}  $$
$$\hat{\beta_1} = \frac{\sum_{i=1}^n(x_i - \bar{X})(y_i-\bar{Y})}{\sum_{i=1}^n (x_i-\bar{X})^2} $$
En el caso de la regresión lineal multiple las estimaciones de los parámetros que minimizan la suma de los errores cuadraticos son (en terminos matriciales):
$$\vec\beta = (X^TX)^{-1}X^TY$$


# 2. Inferencia Estadística

Un poco de notación antes de empezar:

* Usaremos $k$ para denotar el número de variables independientes ($X$) que tiene el modelo. Es decir el número de $\beta's$ de la regresión SIN contar $\beta_0$ 
* Usaremos $n$ para denotar el número total de datos de la muestra.
* Usaremos $SSE$ para denotar la suma de cuadrados del error.
* Usaremos $SSR$ para denotar la suma de cuadrados de la regresión.

Existen dos principales pruebas de interés al hacer una regresión lineal: la prueba de sigificancia global y la prueba de significancia individual.

## 2.1 Estimador de la varianza
Despues de estimar el modelo se puede obtener el mejor estimador de la varianza de los errores $\sigma^2$, el cual es:
$$\hat\sigma^2 = \frac{\sum_{i=1}^n (e_i - 0)^2}{n-k-1} = MSE$$

## 2.2. Prueba de significancia global

La prueba de significancia global prueba de forma simultanea si alguno de los betas (parámetros que acompañan a las $X$) es significativo. Es decir, si hay almenos una de las variables independientes que efectivamente explican a la variable $Y$. 
$$H_0: \beta_1 = \beta_2 = \cdots = \beta_k = 0\\ H_1: \textrm{Al menos un $\beta$ diferente de 0} $$
El estadístico de prueba esta dado por: 
$$EP = \frac{\frac{SSR}{glR}}{\frac{SSE}{glE}} = \frac{\frac{\sum_{i=1}^n (\hat{y_i} - \bar{Y})^2}{k}}{\frac{\sum_{i=1}^n (y_i-\hat{y_i})^2}{n-k-1}} \sim F_{k,n-k-1}  $$

Esta es una prueba de cola derecha por lo que la región de rechazo sera:
$$ RC = F_{1-\alpha,k,n-k-1}$$
El pvalor asociado es:
$$pvalue = P(F_{k,n-k-1} > EP)$$

##2.3. Prueba de significancia indivual

La prueba de significancia individual prueba una por una las variables independientes para concluir si existe o no relación entre dicha $X$ y la variable $Y$

$$H_0: \beta_i =  0\\ H_1: \beta_i \neq  0 $$
El estadístico de prueba esta dado por:

$$EP = \frac{\hat{\beta_i} - 0}{\sqrt{Var(\hat{\beta_i})}} \sim t_{n-k-1}$$
Al ser una prueba de dos colas la region de rechazo está dada por:
$$ RC_1: t_{1-\alpha/2,n-k-1} \\ RC_2: t_{\alpha/2,n-k-1} $$
El pvalor asociado es:
$$pvalue = 2*P(t_{n-k-1} > |EP|)$$

## 2.4. Salidas del modelo de regresión

De manera general con los resultados del modelo de regresión se pueden construir dos tablas (las cuales la mayoría de paquetes estadisticos entregan como salida despues de estimar el modelo). Estas tablas son:

* La tabla ANOVA que contiene toda la información para realizar la prueba de significancia global.
* La tabla de coeficientes que contiene toda la información para realizar las pruebas de significancia individual.

Las tablas tienen la siguiente forma:

### 2.4.1. Tabla ANOVA

SS                                              gl               MS      F        SIG
----------------------------------------------- ---------------- ------- -------- -----  
SSR = $\sum_{i=1}^n (\hat{y_i} - \bar{Y})^2$    glR = $k$        SSR/glR  MSR/MSE pvalor
SSE = $\sum_{i=1}^n (y_i-\hat{y_i})^2$          glE = $n-k-1$    SSE/glE
SST = $\sum_{i=1}^n (y_i - \bar{Y})^2$          glT = $n-1$

### 2.4.2. Tabla Coeficientes

Variable                  Coef ($\beta$)   E.S ($\beta$)                        t                                                          SIG 
------------------------ ---------------- ----------------------------------- ------------------------------------------------------------ -----  
Constante                 $\hat{\beta_0}$ $\sqrt{\hat{Var}(\hat{\beta_0})}$   $\frac{\hat{\beta_0}}{\sqrt{\hat{Var(\hat{\beta_0})}}}$      pvalor
$X_1$                     $\hat{\beta_1}$ $\sqrt{\hat{Var}(\hat{\beta_1})}$   $\frac{\hat{\beta_1}}{\sqrt{\hat{Var(\hat{\beta_1})}}}$      pvalor
$\vdots$                  $\vdots$        $\vdots$                            $\vdots$                                                     $\vdots$
$X_k$                     $\hat{\beta_k}$ $\sqrt{\hat{Var}(\hat{\beta_k})}$   $\frac{\hat{\beta_k}}{\sqrt{\hat{Var(\hat{\beta_k})}}}$      pvalor

# 3. Regresión Lineal en R

## 3.1. Regresión Simple

Antes de hacer la regresion creamos datos sintenticos. 


```r
X <- rnorm(n = 100, mean = 50, sd = 5)
Y <- 14 + 3*X + 5*rnorm(n=100)
plot(X,Y)
```

![](Regresión-Lineal_files/figure-html/unnamed-chunk-1-1.png)<!-- -->

### 3.1.1. Estimación
Para correr un modelo de regresión en R se utiliza el comando $lm$

```r
reg <- lm(Y ~ X)
summary(reg)
```

```
## 
## Call:
## lm(formula = Y ~ X)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -11.8850  -3.4288  -0.0582   3.8962  10.9681 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   20.359      5.093   3.997 0.000124 ***
## X              2.857      0.101  28.272  < 2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 5.238 on 98 degrees of freedom
## Multiple R-squared:  0.8908,	Adjusted R-squared:  0.8897 
## F-statistic: 799.3 on 1 and 98 DF,  p-value: < 2.2e-16
```

Como se puede observar la tabla nos entrega toda la información necesaria para oncluir acerca del modelo de regresión que acabamos de hacer. Tiene los valores estimados de los coeficientes, sus varianzas, su estadísticos de prueba y el estadístico de la prueba de significancia global. 


```r
plot(X,Y, col = 'black')
abline(reg,col = 'red')
```

![](Regresión-Lineal_files/figure-html/unnamed-chunk-3-1.png)<!-- -->



Con un poco de programación se pueden encontrar las sumas de cuadrados y los grados de libertad para realizar las pruebas a mano


```r
yhat <- reg$fitted.values #Las predicciones del modelo
```


```
## SSR: 21929.46 
## SSE: 2688.772 
## SST: 24618.23
```

```
## glR: 1 
## glE: 98 
## glT: 99
```

### 3.1.2. Prueba de significancia global

```r
EP <-  (SSR/glR)/(SSE/glE)
pvalue <- 1-pf(EP,glR,glE)
cat('Se rechaza la hipótesis nula ya que el pvalor de', pvalue, 'es menor a la significancia')
```

```
## Se rechaza la hipótesis nula ya que el pvalor de 0 es menor a la significancia
```

### 3.1.3. Prueba de significancia individual

```r
var_beta <- (SSE/glE)/sum((X-mean(X))^2) 
beta_hat<-reg$coefficients[2]
EP <-  (beta_hat-0)/sqrt(var_beta)
pvalue <- 2*(1-pt(abs(EP),glE))
cat('Se rechaza la hipótesis nula ya que el pvalor de', pvalue, 'es menor a la significancia')
```

```
## Se rechaza la hipótesis nula ya que el pvalor de 0 es menor a la significancia
```

## 3.2 Regresión Multiple


```r
X1 <- rnorm(n = 100, mean = 50, sd = 5)
X2 <- rnorm(n = 100, mean = 50, sd = 5)
X3 <- rnorm(n = 100, mean = 50, sd = 5)
Y <- 14 + 3*X - 5*X2 + 0.7*X3 + 10*rnorm(n=100)
```

Para estimar un modelo de regresión múltiple basta con especificar la ecuación de la recta en el comando $lm$

```r
reg <- lm(Y ~ X1+X2+X3)
summary(reg)
```

```
## 
## Call:
## lm(formula = Y ~ X1 + X2 + X3)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -41.148 -12.156  -0.839  11.413  43.742 
## 
## Coefficients:
##              Estimate Std. Error t value Pr(>|t|)    
## (Intercept) 225.14482   37.76752   5.961 4.14e-08 ***
## X1            0.03017    0.40487   0.075    0.941    
## X2           -5.63673    0.38408 -14.676  < 2e-16 ***
## X3            0.11510    0.43029   0.267    0.790    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 19.38 on 96 degrees of freedom
## Multiple R-squared:  0.6973,	Adjusted R-squared:  0.6878 
## F-statistic: 73.72 on 3 and 96 DF,  p-value: < 2.2e-16
```

