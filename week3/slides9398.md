
Properties for $\E[X]$

1. $\E[A - B] = \E[A]-\E[B]$
2. $\E[X] = \Pr(B) \cdot\E[X\mid B] + \Pr(\mathrm{not \ } B) \E[X \mid \mathrm{not \ } B]$


Proof of Property (2):
* First, we know $\Pr(A) = \Pr(B)\Pr(A \mid B) + \Pr(\mathrm{not \ }B) \Pr(A \mid \mathrm{not \ } B)$, because:
$$
\begin{aligned}
\Pr(A)  & = \Pr(A \cap B) + \Pr(A \cap \mathrm{not \ }B)  \\
 & = \Pr(B) \cdot \frac{\Pr(A \cap B)}{\Pr(B)} + \Pr(\mathrm{not \ } B) \frac{\Pr(A \cap \mathrm{not \ }B)}{\Pr(\mathrm{not \ } B)} \\
 & = \Pr(B) \cdot PR(A \mid B) + \Pr(\mathrm{ not \ }B) \Pr(A \mid \mathrm{ not} B)
\end{aligned}
$$
* Applying this to the definition of $\E[X]$:
$$
\begin{aligned}
\E[X]  & = \sum x \Pr(X=x) \\
 & = \sum x \{ \Pr(B)\Pr(X=x \mid B) + \Pr(\mathrm{not \ } B)\Pr(X=x \mid \mathrm{not \ }B)\} \\
 & = \sum x \Pr(B) \Pr(X = x  \mid B) + \sum x \Pr(\mathrm{not \ }B) \Pr(X = x \mid \mathrm{not \ }B) \\
 & = \Pr(B) \left\{ \sum x \Pr(X = x \mid B) \right\} + \Pr(\mathrm{ not \ }B)  \left\{  \sum x \Pr(X = x \mid \mathrm{not \ } B) \right\} \\
 & = \Pr(B) \E[X\mid B] + \Pr(\mathrm{not \ }B ) \E[X \mid \mathrm{not \ } B]
\end{aligned}
$$
* Q.E.D.


Now, we can expand the expression for ATE using Properties 1 and 2:

$$
\begin{aligned}
\mathrm{ATE}  & = \E[Y_{i}(1)-Y_{i}(0)]  \\
 & = \E[Y_{i}(1)]-\E[Y_{i}(0)] \\
 & = \Pr(D_{i} = 1) \E[Y_{i}(1)\mid D_{i} =  1]  + \Pr(D_{i} = 0) \E[Y_{i}(1) \mid D_{i}=0] \\
 & \ \ \ - \left\{ \Pr(D_{i} = 1) \E[Y_{i}(0)\mid D_{i} =  1]  + \Pr(D_{i} = 0) \E[Y_{i}(0) \mid D_{i}=0]  \right\}
\end{aligned}
$$

For our convenience, let's define $\Pr(D_{i}=1) = p$, such that $\Pr(D_{i}=0) = (1-p)$, we arrive at the expression on slide 94:

$$
\begin{aligned}
\mathrm{ATE} =  &  p\textcolor{red}{ \E[Y_{i}(1)\mid D_{i}=1]  }+ (1-p) \E[Y_{i}(1)\mid D_{i}=0]  \\
 & - p\E[Y(0) \mid D_{i} = 1] - (1-p) \textcolor{red}{ \E[Y_{i}(0) \mid D_{i}=0] }
\end{aligned}
$$

***

Recall that out of the four terms in the previous equation, only the first and fourth terms (in red) are observable (and are indeed the constituent terms of SDO). So our goal here is to try to express the SDO as a combination of ATE and the other two unobservable terms in order to quantify the unobserved biases.

For simplicity, I will reexpress the conditional probabilties as 
$$
\begin{cases}
\E[Y_{i}(1) \mid D_{i}= 1]  & = e_{11} \\
\E[Y_{i}(1) \mid D_{i}=0]  & = e_{00} \\
\E[Y_{i}(0) \mid D_{i} = 1]  & = e_{01} \\
\E[Y_{i}(0) \mid D_{i} = 0]  & = e_{00} 
\end{cases}
$$
Such that 
$$
\begin{cases}
\mathrm{SDO} = e_{11} - e_{00} \\
\mathrm{ATE} = pe_{11} + (1-p)e_{10} - p e_{01} - (1-p) e_{00} \\
\mathrm{ATT} = e_{11}-e_{01} \\
\mathrm{ATU} = e_{10}-e_{00}
\end{cases}
$$

Now, we can try rearranging the terms, with a bit of brute force:
$$
\begin{aligned}
\mathrm{ATE} &  = pe_{11} + (1-p)e_{10} - p e_{01} - (1-p) e_{00} \\
   0& = \mathrm{}\mathrm{ATE} -pe_{11}-(1-p)e_{01}+ p e_{10} + e_{00}-pe_{00} \\
 e_{11}-e_{00} & = \mathrm{ATE} + (1-p)e_{11}  - (1-p)e_{10} + p{e_{01}} -p e_{00}  \\
\end{aligned}
$$
Here, our next goal is to simplify the RHS, by factorizing most terms with $(1-p)$ and expressing them as ATT or ATU
$$
\begin{aligned}
e_{11}-e_{00} & = \mathrm{ATE} + (1-p)e_{11}  - (1-p)e_{10} + p{e_{01}} -p e_{00}  \\
 & = \mathrm{ATE} + (1-p)e_{11}  - (1-p)e_{10} + (p-1){e_{01}} - (p-1) e_{00} + e_{01} - e_{00} \\
 & = \mathrm{ATE} + (1-p)e_{11}  - (1-p)e_{10} - (1-p){e_{01}} + (1-p) e_{00} + e_{01} - e_{00} \\ 
 & = \mathrm{ATE} + \underbrace{ (1-p)e_{11}  - (1-p)e_{01} }_{ (1-p)  \mathrm{ATT} } - \underbrace{ (1-p){e_{10}} + (1-p) e_{00} }_{ (1-p) \mathrm{ATU} } + e_{01} - e_{00} \\ 
 & = \mathrm{ATE } + \left\{ e_{01}-e_{00} \right\}  +(1-p)\mathrm{ATT} - (1-p)\mathrm{ATU} \\
 & = \mathrm{ATE } + \left\{ e_{01}-e_{00} \right\}  +(1-p) (\mathrm{ATT}-\mathrm{ATU})
\end{aligned}
$$
Q.E.D.

***

Thus, we now know that,
$$
\mathrm{SDO} = \mathrm{ATE} + {e_{01}-e_{00}} + (1-p)(\mathrm{ATT} - \mathrm{ATU})
$$

So for the SDO to be an unbiased estimator of the ATE (i.e. $\mathrm{SDO=ATE}$), we will need that:

$$
\begin{cases}
e_{01}-e_{00} =0 \\
\mathrm{ATT}-\mathrm{ATU}=0
\end{cases}
$$

This will only happen when
1. The average of baseline potential outcomes of folks ($Y_{i}(0)$) in the treated group is the same as those in the control group. We call this no "selection bias."
	- This will be violated when, say, I run a study on whether revision increases grades, but I put all the rich kids in the treatment group, and all the poor kids in the control groups. Since we know that the rich kids will most probably have higher baseline grades than the poor kids even if they don't study, there will be a difference in the average $Y_{i}(0)$ s across the two groups - hence there is a selection bias.
2. The average (individual) treatment effect of the folks in the treatment group, is same as that of those in the control group. We call this no "heterogeneous treatment effect bias."
	* Using the same example, rich kids with higher baseline grades will receive less marginal benefit from studying than poor kids (i.e. it is much harder to go from 80 to 90 than 60 to 70). This means the average treatment effect of the two groups will not the same (or $\mathrm{ATT} \neq \mathrm{ATU}$) - hence a heterogenous treatment effect bias.
	* As you might imagine, both biases will be resolved automatically if people are randomly assigned into the treatment and control groups. So the above biases are most relevant for poorly-designed experiments or observational studies, where we have no control over the treatment assignment (e.g. a historical of educational policies in England vs India).

