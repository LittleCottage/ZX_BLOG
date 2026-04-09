---
title: "On Definitions and the Interpretation of Partial Correlation"
date: 2026-04-02
categories: ["Statistics"]
tags: ["FAQ", "Regression Analysis", "Factor Analysis"]
---

$\newcommand{\real}{\mathbb{R}}$
$\newcommand{\bX}{\boldsymbol{X}}$
$\newcommand{\Cov}{\operatorname{Cov}}$
$\newcommand{\diag}{\operatorname{diag}}$
$\newcommand{\sp}{\operatorname{\overline{sp}}}$
$\newcommand{\tr}{\operatorname{tr}}$

## Zhanxiong's Definition
First let me present the (seemingly) most general mathematical definition of the *partial correlation of a random vector 
$\bX_1 \in \real^p$ given another random vector $\bX_2 \in \real^q$*. This definition I presented here incorporated three 
sources: Brockwell and Davis ([<a href='#brockwell2006time'>1</a>]), Mulaik ([<a href='mulaik2009foundations'>2</a>]), and
Muirhead ([<a href='muirhead1982aspects'>3</a>]). Later I will explain how my definition connects to definitions proposed 
by these authors. 

> **Definition (Partial Correlation).** Let $\bX_1 \in \real^p$ and $\bX_2 \in \real^q$ be two non-degenerate zero-mean random vectors 
> with covariance matrix $\begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\\\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}$, where 
> $\Sigma_{11}$ and $\Sigma_{22}$ are order $p$ and order $q$ matrices respectively.
> Denote by $\Sigma_{11 \cdot 2} \in \real^{p \times p}$ the variance-covariance matrix of $\bX_1 - P_{\sp(\bX_2)}(\bX_1)$, where
>  $P_{\sp(\bX_2)}(\bX_1)$ is the *best linear predictor of $\bX_1$ in terms of $\bX_2 := (X_{21}, \ldots, X_{2q})$* 
> (see [<a href='#brockwell2006time'>1</a>], Definition 2.7.4). The *partial correlation (matrix)* of $\bX_1$ given (or adjusted for, or 
> after partialling out) $\bX_2$ is defined as
> $$
> \begin{equation*}
> \rho_{11 \cdot 2} = \diag(\Sigma_{11\cdot 2})^{-1/2}\Sigma_{11\cdot 2}\diag(\Sigma_{11\cdot 2})^{-1/2}.
> \end{equation*}
> $$

## A Closed-form Expression of $\rho_{11\cdot 2}$ (in $L^2$ space)
In Definition 2.7.4 of [<a href='#brockwell2006time'>1</a>], $\bX_1$ is a scalar-valued random variable, i.e., $p = 1$, under which case 
$P_{\sp(\bX_2)}(X_1)$ is naturally defined as the projection ([<a href='#brockwell2006time'>1</a>], Theorem 2.3.1) of $X_1$ onto the closed
 subspace $\sp(\bX_2)$ in $L^2(\Omega, \mathscr{F}, P)$. When $\bX_1$ is a random vector from $\Omega$ to $\real^p$, the classical inner product space
 $L^2(\Omega, \mathscr{F}, P)$ needs to be generalized to $L^2(\Omega, \mathscr{F}, P; \real^p)$, which consists of all $X$ such that 
 $E[\\|X\\|^2] = \int_\Omega \\|X\\|^2 dP < \infty$. Analogously, the inner product in $L^2(\Omega, \mathscr{F}, P; \real^p)$ can be defined 
 as $\langle \xi, \eta\rangle = E[\xi^\top\eta]$. Since a linear predictor of $\bX_1$ in terms of $\bX_2$ by definition is $B\bX_2$ for 
 some non-random matrix $B \in \real^{p \times q}$ (or a linear transformation $B \in L(\real^q, \real^p)$), the best linear predictor of $\bX_1$
 in terms of $\bX_2$, say $\hat{\bX}_1 = B_0\bX_2$, must minimize the squared-norm $\\|\bX_1 - B\bX_2\\|^2$ in $L^2(\Omega, \mathscr{F}, P; \real^p)$ 
 over $B \in \real^{p \times q}$. Furthermore, since

$$ 
\begin{align*} 
 \\|\bX_1 - B\bX_2\\|^2 &= E[(\bX_1 - B\bX_2)^\top(\bX_1 - B\bX_2)] = E[\tr\left((\bX_1 - B\bX_2)(\bX_1 - B\bX_2)^\top\right)] \\\\
 &= \tr\left(\Sigma_{11} - B\Sigma_{21} - \Sigma_{12}B^\top + B\Sigma_{22}B^\top\right)
 = \tr\left(\Sigma_{11} - 2B\Sigma_{21} + B\Sigma_{22}B^\top\right) \\\\
 &= \tr\left(\Sigma_{11} - 2A\Sigma_{22}^{-1/2}\Sigma_{21} + AA^\top\right) \tag{Set $A = B\Sigma_{22}^{1/2}$} \\\\
 &= \tr\left((A - \Sigma_{12}\Sigma_{22}^{-1/2})(A - \Sigma_{12}\Sigma_{22}^{-1/2})^\top + \Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} \right) \\\\
 &\geq \tr\left(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21} \right)
\end{align*}  
$$
with the equality holds if and only if $A = \Sigma_{12}\Sigma_{22}^{-1/2}$, or equivalently $B = \Sigma_{12}\Sigma_{22}^{-1}$, we conclude that 
$B_0 = \Sigma_{12}\Sigma_{22}^{-1}$. Consequently, it follows that 
$$ \rho_{11\cdot 2} =  \diag(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})^{-1/2}(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})\diag(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})^{-1/2}. \tag{1}
$$
 
## Special Cases and Discussion
Perhaps the most important special case of the general formula (1) is the "partial correlation coefficient between two variables $\xi$ and $\eta$ given another $k$ variables 
$Z_1, \ldots, Z_k$", which is of primary interest in (linear) regression models where $\xi \leftarrow Y$, $\eta \leftarrow X_0$ for one explanatory variable, and 
$(Z_1, \ldots, Z_k)$ is assigned to be remaining explanatory variables entering the model. Denote the variance-covariance matrix of $(\xi, \eta, Z_1, \ldots, Z_k)$ by
$$
\Sigma = \begin{bmatrix}
\sigma_{\xi\xi}  & \sigma_{\xi\eta}  & \sigma_{\xi 1}  & \cdots & \sigma_{\xi k}  \\\\
\sigma_{\eta\xi} & \sigma_{\eta\eta} & \sigma_{\eta 1} & \cdots & \sigma_{\eta k} \\\\
\sigma_{\xi 1}   & \sigma_{\eta 1}     & \sigma_{11}     & \cdots & \sigma_{1k}     \\\\
\vdots           & \vdots            & \vdots          & \ddots & \vdots          \\\\
\sigma_{\xi k}   & \sigma_{\eta k}     & \sigma_{1k}     & \cdots & \sigma_{kk}     
\end{bmatrix} =: 
\begin{bmatrix}
\Sigma_{11} & \Sigma_{12} \\\\
\Sigma_{21} & \Sigma_{22}
\end{bmatrix},
$$
where $\Sigma_{11}$ is the northwestern order $2$ block matrix in $\Sigma$. The partial correlation between $\xi$ and $\eta$ given $(Z_1, \ldots, Z_k)$ is then intuitively defined
as the $(1, 2)$ (or $(2, 1)$) entry of the matrix in (1), namely, with $e_1 = (1, 0)^\top$ and $e_2 = (0, 1)^\top$: 
$$
\begin{align*}
\rho_{\xi\eta \cdot Z_1\cdots Z_k} &:= 
\frac{e_1^\top(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})e_2}
{\sqrt{e_1^\top(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})e_1 \cdot e_2^\top(\Sigma_{11} - \Sigma_{12}\Sigma_{22}^{-1}\Sigma_{21})e_2}} \\\\
&= \frac{M_{12}/\det(\Sigma_{22})}{\sqrt{M_{22}/\det(\Sigma_{22}) \cdot M_{11}/\det(\Sigma_{22})}} = \frac{M_{12}}{\sqrt{M_{11}M_{22}}}, \tag{2}
\end{align*}
$$
where $M_{ij}$ denotes the $(i, j)$ minor of $\Sigma$. (2) agrees with Equation (4.46) in [<a href='mulaik2009foundations'>2</a>]. 
The penultimate step in the derivation above follows from the Schur's identity $\det(A) = \det(A_{22})\det(A_{11} - A_{12}A_{22}^{-1}A_{21})$ for a block matrix 
$\begin{bmatrix} A_{11} & A_{12} \\\\ A_{21} & A_{22}\end{bmatrix}$ in which $A_{22}$ is invertible. 
## How to Interpret the Qualifier "Partial"?

## References
<a id="brockwell2006time"></a>
[1] Brockwell, Peter J., Davis, Richard A. (2006). Time Series: Theory and Methods (2nd ed.). Springer Science+Business Media, LLC.

<a id="mulaik2009foundations"></a>
[2] Mulaik, Stanley A. (2009). Foundations of Factor Analysis. CRC Press.

<a id="muirhead1982aspects"></a>
[3] Muirhead, Robb J. (1982). Aspects of Multivariate Statistical Theory. John Wiley \& Sons, Inc.