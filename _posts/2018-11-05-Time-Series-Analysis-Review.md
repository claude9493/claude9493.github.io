---
layout: post
title: Time Series Analysis Midterm Review
excerpt_separator:  <!--more-->
---

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/KaTeX/0.5.1/katex.min.css">

I'm reviewing the TSA for tomorrw's midterm. And I wrote some notes of markdown format in the application wiz-notes. And I'd like to see whether the math formulas can be displayed as desired on my blog.

## Chapter 1
略

## Chapter 2
### Some functions
- Mean function: $\mu_t = E(Y_t)$
- Autocovariance function: $\gamma_{t,s} = Cov(Y_t, Y_S)$
- Autocorrelation function (ACF): $\rho_{t,s} = Corr(Y_t, Y_s) = \frac{\gamma_{t,s}}{\sqrt{\gamma_{t,t}\gamma_{s,s}}}$
<!--more-->
### Stationarity
- Strictly stationarity
    - if the joint distribution of $Y_{t_1}, Y_{t_2},...,Y_{t_n}$  is the same as the joint distribution of $Y_{t_1-k}, Y_{t_2-k},...,Y_{t_n-k}$ for all choices of time $t_1, t_2, ..., t_n$ and all choices of time lags $k$
    - White noise ${e_t}$ [A sequence of i.i.d random variables] is strictly stationary
    - $\gamma_{t,s} = \gamma_{0,|t-s|} = \gamma_{k}, k = |t-s|$
    - Properties: $\gamma_0 = Var(Y_t)\qquad\rho_0 = 1\qquad\gamma_k = \gamma_{-k}\qquad |\gamma_k|\leq\gamma_0, |\rho_k|\leq1$
- Weak stationaity
    - $E(Y_t) = c$, $c$ is a constant, $\gamma_{t,t-k} = \gamma_{0,k}$ for all time $t$ and lag $k$
    - A strictly stationary process with finite variance must be a weak stationary process

## Chapter 3
### Trends
- Stochastic trend
    - Every simulation show completely different "trend"
- Deterministic trend
    - Mean function is relatively simple (not constant) functions of time
### Mean of series with deterministic trend (Estimation)
- Constant mean
    - $Y_t = \mu + X_t$ with $E(X_t) = 0$
    - $\bar{Y} = \frac{1}{n}\sum_{t=1}^{n}Y_t$
    - $Var(\bar{Y}) = \frac{\gamma_0}{n}[1+2\sum_{k=1}^{n-1}(1-\frac{k}{n})\rho_k]$
- Linear trend
    - $\mu_t = \beta_0 + \beta_1t$
    - $\hat{\beta_1} = \frac{\sum_{t=0}^{n}(Y_t-\bar{Y})(t-\bar{t})}{\sum_{t=1}^{n}(t-\bar{t})^2}$
    - $\hat{\beta_0} = \bar{Y} - \hat{\beta_1}\bar{t}$
- Seasonal means model
    - Think: 在拟合的时候截距项如何存在, 未知参数个数和方程个数要一致.
### Reliability and Efficiency of Regression Model
Variance of the estimates
$Var(\bar{Y}) = \frac{\gamma_0}{n}[1+2\sum_{k=1}^{n-1}(1-\frac{k}{n})\rho_k]$
### Interpreting Regression Output
$R^2 = \frac{SSR}{SST} = 1-\frac{SSE}{SST}$
$R_{adj}^2 = 1-\frac{n-1}{n-k-1}(1-R^2)$ $p = k+1$
### Residual Analysis
- Residual sequence diagram, Histogram of standardized residuals, QQ-plot, sample autocorrelation function,
- `rstudent(model)`  返回拟合模型的*(外)学生化*残差

## Chapter 4
### General Linear Process
A weighted linear combination of present and past **white noise terms**.
$Y_t = e_t + \psi_1e_{t-1} + \psi_2e_{t-2} + ...$, $e_t\sim i.i.d(0,\sigma_e^2)$
Condition which make the process meaningful mathematically: $\sum_{i=1}^{\infty}\psi_i^2 < \infty$
$E(Y_t) = 0$, $\gamma_k = Cov(Y_t, Y_{t-k}) = \sigma_e^2\sum_{i=0}^{\infty}\psi_i\psi_{i+k}, k>0$ where $\psi_0 = 1$
非零均值的话在右边加$\mu$就行
### Moving Average
MA(q): $Y_t = e_t - \theta_1e_{t-1} - \theta_2e_{t-2} - ...- \theta_qe_{t-q}$
ACF of MA(q) is `tailed-off` beyond lag q..
MA(1), MA(2): Autocovariance 和 Autocorrelation 的推导


### Autoregressive
AR(p): $Y_t = \phi_1Y_{t-1} + \phi_2Y_{t-2} + ... + \phi_pY_{t-p} + e_t$
AR(1), AR(2): Autocovariance 和 Autocorrelation 的推导
- 在算$Cov(Y_t, Y_{t-1})$ 的时候别忘了$Y_{t-1}$ 和 $Y_{t-2}$之间的关系
- When calculating $\gamma_k$ of AR(p), it's useful to assume $\mu = 0$ and multiple $Y_{t-k}$ in both sides of the equation which defines the model.
- Stationary Conditions
    - AR(1): $Y_t = \phi Y_{t-1} + e_{t-1}$ $|\phi| < 1$
    - AR(p): the roots of AR characteristic equation $\phi(x) = 0$ each exceed 1 in absolute value.
    - AR(2): $\phi_1+\phi_2 < 1, \phi_2-\phi_1 < 1, |\phi_2| < 1$
##### Backshift operator
$BX_t = X_{t-1}$
$\phi(B)Y_t = \phi_0+e_t$, AR polynomial. For AR(2), $\phi(B) = 1-\phi_1B-\phi_2B^2$
$\phi(x) = 0$ AR characteristic equation: replace $B$ by $x$ in AR polynomial.
##### How to rewrite AR(p) model as MA($\infty$) model?
AR(p): $\Phi(B)Y_t = \phi_0 + e_t$
Consider whether the reverse operator $\Phi^{-1}(B)$ exists.
If exists, $Y_t = \Phi^{-1}(B)\phi_0 + \Phi^{-1}(B)e_t$
##### Yule-Walker equations
什么东东?
### ARMA(p,q)
$Y_t = \phi_1Y_{t-1}+\phi_2Y_{t-2}+...+\phi_pY_{t-p}+e_t-\theta_1e_{t-1}-\theta_2e_{t-2}-...-\theta_qe_{t-q}, \phi_p\neq0, \theta_q\neq0$
$\phi(B)Y_t = \theta(B)e_t$, $\phi(B) = 1 - \phi_1B - \phi_2B^2 - ... - \phi_pB^p$, $\theta(B) = 1 - \theta_1B - \theta_2B^2 - ... - \theta_qB^q$.
ARMA(p,q), p, q 的确定, 记得看在用滞后算子表示的情况下两边能不能约分. Whether there is a *common factor* between AR polynomial $\phi(B)$ and MA polynomial $\theta(B)$.
ARMA(1,1) 的各种推导, $Y_t = \phi_0+\phi_1Y_{t-1}+e_t-\theta_1e_{t-1}$
**Stationary condition**: Roots of $\phi(z) = 0$ are outside the unit circle.
Stationarity is only related with the coefficients in the AR part.
##### ARMA(p,q) to MA($\infty$), General linear process expression for ARMA model
Under stationary condition, $\phi^{-1}(B)$ exists.
$Y_t = \phi^{-1}(B)\phi_0 + \phi^{-1}(B)\theta(B)e_t$
##### ARMA(p,q) to AR($\infty$), Invertibility
Reversible condition: all roots of $\theta(x) = 0$ are outside the unit circle.
Under reversible condition, $\theta^{-1}(B)$ exists.
$\theta^{-1}(B)\phi(B)Y_t = \theta^{-1}(B)\phi_0+e_t$
##### Useful Taylor Equation
$\frac{1}{1-x} = 1 + x + x^2 + x^3 + ...$
