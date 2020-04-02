
### GOV 391L STATS II Midterm

- 1) All of the questions can be answerd in no more than 2-3 sencenses.
- 2) There isn't always one single correct answer to a question. 



---


##2. Explain what it means that OLS is efficient? When is it not?

<br>

\begin{equation}
\begin{aligned}
\hat \beta_{OLS} &= (X\prime X)^{-1}X\prime Y \\
&= (X\prime X)^{-1}X\prime (X\beta + \epsilon)\\
&= (X\prime X)^{-1}X\prime X\beta + (X\prime X)^{-1}X\prime \epsilon \\
&= \beta + (X\prime X)^{-1} X\prime \epsilon 
\end{aligned}
\end{equation}

<br>

\begin{equation}
\begin{aligned}
Var(\hat \beta_{OLS}) &= Var(\beta + (X\prime X)^{-1} X\prime \epsilon)\\
&= Var((X\prime X)^{-1} X\prime \epsilon) \\
&= (X\prime X)^{-1} X\prime Var(\epsilon) ((X\prime X)^{-1} X\prime)\prime \\
&=(X\prime X)^{-1} X\prime Var(\sigma^2 I) X(X\prime X)^{-1}\\
&= \sigma^2 (X\prime X)^{-1} (X\prime X) (X\prime X)^{-1}\\
&= \sigma^2 (X\prime X)^{-1}
\end{aligned}
\end{equation}

Therefore, OLS is efficient when $Var(\hat \beta_{OLS}) \leq Var(\beta^{*})$. For this to exist,
- the relationship between Y and X is liner so that $Y = X\beta + \epsilon$
- errors variation is constant so that $Var(\epsilon) = Var(\sigma^2 I)$
