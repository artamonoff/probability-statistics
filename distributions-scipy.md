# Основные распределения в пакете `scipy`

Основные классы и методы по работе с основными распределениями в модуле [`scipy.stats`](https://docs.scipy.org/doc/scipy/reference/stats.html)

## Непрерывные распределения

### Основные методы

Общие методы для всех непрерывных распределений с плотностью $f$ и (кумулятивной) функцией распределения $F$.

|Метод|Описание|
|-|-|
|`.mean()`|Математическое ожидание $E[X]$|
|`.var()`|Дисперсия $Var[X]$|
|`.std()`|Стандартное отклонение $\sigma[X]$|
|`.pdf(x)`|Плотность распределения в точке $f(x)$|
|`.cdf(x)`|Значение функции распределения в точке $F(x)=P(X\leq x)=P(X<x)$|
|`.sf(x)=1-.cdf(x)`|Survival function $SF(x)=P(X\geq x)=P(X> x)=1-F(x)$|
|`.ppf(p)`|Квантиль уровня $p$: решение уравнения $F(x)=P(X\leq x)=p$|
|`.isf(p)=.ppf(1-p)`|Решение уравнения $P(X> x)=p$|
|`.median()`|Медиана распределения $Med[X]$|

__Замечание__: Вероятности $P(a\leq X\leq b)=P(a<X<b)=P(a<X\leq b)=P(a\leq X<b)=$`.cdf(b)-.cdf(a)`

### Основные непрерывные распределения

|Распределение|Обозначение|`scipy.stats`|Параметры|Импорт в Python|
|-|-|-|-|-|
|Гауссово/нормальное|$N(\mu,\sigma^2)$|`norm(loc=0,scale=1)`|loc = $\mu$, scale = $\sigma$|`from scipy.stats import norm`|
|Равномерное на отрезке|$U[a,b]$|`uniform(loc=0,scale=1)`|loc = $a$, scale = $b-a$|`from scipy.stats import uniform`|
|Экспоненциальное|$Exp(\lambda)$|`expon(loc=0,scale=1)`|loc = 0, scale = $1/\lambda$|`from scipy.stats import expon`|
|Хи-квадрат|$\chi^2_k$|`chi2(df)`|df = $k$|`from scipy.stats import chi2`|
|t-распределение (Стьюдента)|$t_k$|`t(df)`|df = $k$|`from scipy.stats import t`|
|F-распределение (Фишера)|$F_{k1, k2}$|`f(dfn, dfd)`|dfn = $k1$, dfd = $k2$|`from scipy.stats import f`|
|Логистическое|$\Lambda$|`logistic(loc=0,scale=1)`|loc = 0, scale = 1|`from scipy.stats import logistic`|
|Бета|$B(\alpha,\beta)$|`beta(a,b)`|a = $\alpha$, b = $\beta$|`from scipy.stats import beta`|
|Гамма|$\Gamma(k)$|`gamma(a)`|a = $k$|`from scipy.stats import gamma`|

__Замечание__: для распределений указаны значения параметров по умолчанию 

## Дискретные распределения

### Основные методы

Общие методы для всех дискретных распределений с распределением вероятностей $f(x)=P(X=x)$ и (кумулятивной) функцией распределения $F(x)=P(X\leq x)$.

|Метод|Описание|
|-|-|
|`.mean()`|Математическое ожидание $E[X]$|
|`.var()`|Дисперсия $Var[X]$|
|`.std()`|Стандартное отклонение $\sigma[X]$|
|`.pmf(x)`|Распределение вероятностей $f(x)=P(X=x)$|
|`.cdf(x)`|Значение функции распределения в точке $F(x)=P(X\leq x)$|
|`.sf(x)=1-.cdf(x)`|Survival function $SF(x)=P(X> x)=1-F(x)$|
|`.ppf(p)`|Квантиль уровня $p$: решение уравнения $F(x)=P(X\leq x)=p$|
|`.isf(p)=.ppf(1-p)`|Решение уравнения $P(X> x)=p$|
|`.median()`|Медиана распределения $Med[X]$|

__Замечание__: Вероятности

- $P(a< X\leq b)=$`.cdf(b)-.cdf(a)`
- $P(a\leq X\leq b)=P(a-c <X\leq b)=$`.cdf(b)-.cdf(a-c)` для достаточно малого $c$ (обычно $c=1$)
- $P(a< X< b)=P(a <X\leq b-c)=$`.cdf(b-c)-.cdf(a)` для достаточно малого $c$ (обычно $c=1$)

### Основные дискретные распределения

|Распределение|Обозначение|`scipy.stats`|Параметры|Импорт в Python|
|-|-|-|-|-|
|Биномиальное|$Bimon(n,p)$|`binom(n,p)`|n = $n$, p = $p$|`from scipy.stats import binom`|
|Гипергеометрическое|$Hypergeom(N, D, n)$|`hypergeom(M, n, N)`|M = $N$, n = $D$, N = $n$|`from scipy.stats import hypergeom`|
|Пуассона|$Poisson(\mu)$|`poisson(mu)`|mu = $\mu$|`from scipy.stats import poisson`|
|Отрицательное биномиальное|$NB(n,p)$|`nbinom(n,p)`|n = $n$, p = $p$|`from scipy.stats import nbinom`|
|Геометрическое|$Geom(p)$|`geom(p)`|p = $p$|`from scipy.stats import geom`|
