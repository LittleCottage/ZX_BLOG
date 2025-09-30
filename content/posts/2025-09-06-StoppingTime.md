---
title: "Characterization of the sigma-field associated with a stopping time"
date: 2025-09-06
categories: ["Probability"]
math: true
tags: ["Self Study", "Martingales"]
---

In Section 35 of *Probability and Measure*, after defining the $\sigma$-field $\mathscr{F}_\tau$ associated with a stopping time $\tau$, Billingsley wrote:

> If $\tau(\omega) < \infty$ for all $\omega$ and $\mathscr{F}_n = \sigma(X_1, \ldots, X_n)$, then $I_A(\omega) = I_A(\omega')$ for all $A$ in $\mathscr{F}$ if and only if $X_i(\omega_1) = X_i(\omega_2)$ for $i \leq \tau(\omega_1) = \tau(\omega_2)$: The information in $\mathscr{F}$ consists of values $\tau(\omega), X_1(\omega), \ldots, X\_{\tau(\omega)}(\omega)$.

How to verify this statement? Below is the proof.

Suppose $I_A(\omega) = I_A(\omega')$ for all $A \in \mathscr{F}_\tau$. If $\tau(\omega) \neq \tau(\omega')$, say $\tau(\omega) = i < j = \tau(\omega')$, 
then for the set $A = [\tau = j] \in \mathscr{F}\_\tau$, we have $\omega \not\in A$ but $\omega' \in A$, contradiction.  Hence $\tau(\omega) = \tau(\omega') =: N$.  Next, we show that $X_i(\omega) = X_i(\omega')$ for $i \leq N$.  Consider the 
set $A := [X_i = X_i(\omega), i \leq N] \cap [\tau = N]$.  It is a member of $\mathscr{F}\_\tau$, because $A \cap [\tau \leq i] = \varnothing \in \mathscr{F}_i$ for $i < N$ and $A \cap [\tau \leq i] = A \cap [\tau = N] \in \mathscr{F}_i$ for $i \geq N$. Since $\omega \in A$ trivially, 
it follows by the assumption that $\omega' \in A$, which means that $X_i(\omega') = X_i(\omega)$ for $i \leq N$. 

Conversely, suppose $X_i(\omega) = X_i(\omega')$ for all $i \leq \tau(\omega) = \tau(\omega') =: N$ and let $A \in \mathscr{F}\_\tau$. If $\omega \in A$, then $\omega \in A \cap [\tau \leq N] \in \mathscr{F}_N$, meaning that 
$\omega \in A \cap [\tau \leq N] := [(X_1, \ldots, X_N) \in H]$ for some $H \in \mathscr{R}^N$, i.e.,
$(X_1(\omega), \ldots, X_N(\omega)) \in H$. By condition, we have $(X_1(\omega'), \ldots, X_N(\omega')) \in H$, whence $\omega' \in A \cap [\tau \leq N]$, which implies that $\omega' \in A$. 
Reversing the role of $\omega'$ and $\omega$ gives $\omega' \in A$ implies that $\omega \in A$. This shows that $\omega$ 
and $\omega'$ are $\mathscr{F}\_\tau$-equivalent. 