# Mathy Stuff

## Mathy Proof

### Paper Reading and Formula Derivation

Scenario: I'm deep-diving into a paper titled [CMAB-Based Reverse Auction for Unknown Worker Recruitment in Mobile Crowdsensing](https://ieeexplore.ieee.org/document/9354534). The last two lines of the proof of Theorem 18 are super brief, likely to save space. I don’t really get it, and I’m honestly too lazy to spend tons of time on tedious derivations. So, I’m hoping ChatGPT can be my study buddy and help me out with the derivation.

#### In-context Learning📖

One of my go-to tricks is using examples and background info. I start by adding the definition of Big O notation and a simple example in a single-variable scenario. Then, I present the problem from the paper and ask ChatGPT to solve it step by step, thinking in full detail.

PROMPT:
```markdown
Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity. The letter O was chosen by Bachmann to stand for Ordnung, meaning the order of approximation.

In computer science, big O notation is used to classify algorithms according to how their run time or space requirements grow as the input size grows.[3] In analytic number theory, big O notation is often used to express a bound on the difference between an arithmetical function and a better understood approximation; a famous example of such a difference is the remainder term in the prime number theorem. Big O notation is also used in many other fields to provide similar estimates.

Big O notation characterizes functions according to their growth rates: different functions with the same asymptotic growth rate may be represented using the same O notation. The letter O is used because the growth rate of a function is also referred to as the order of the function. A description of a function in terms of big O notation usually only provides an upper bound on the growth rate of the function.

Associated with big O notation are several related notations, using the symbols o, Ω, ω, and Θ, to describe other kinds of bounds on asymptotic growth rates.

Here is the important part that you have to pay attention to:

For example, single-variate function:
f(n) = 9 log n + 5 (log n)^4 + 3*n^2 + 2 *n^3 = O(n^3)

Now, simply and reduce the multi-variate function:
"""
f(N,M+,M-,K,B,)=
(N\varrho _{max}^{q} +\eta _4 R_{\boldsymbol{V}^{\prime }})\eta _1\ln \Bigg(\frac{2B}{P_{\boldsymbol{V}^{\prime }}}+\eta _3\Bigg)+\eta _2\eta _4 R_{\boldsymbol{V}^{\prime }} \\ &\qquad\qquad\;\;+\eta _2 N\varrho _{max}^{q}+R_{\boldsymbol{V}^{\prime }}
"""
= O(?) deduce and reason about it step by step.
where,\eta _1 = \left\lbrace \begin{array}{l}\frac{4K^2\delta }{(c_{min}\Delta _{min})^2} + 2K,\delta = K + 1/2\\ 
\frac{4K^2\delta}{(c_{min}\Delta _{min})^2},\delta > K + 1/2\end{array}\right.
\eta _2 = \left\lbrace \begin{array}{l}\frac{4K^2\delta \ln (KM^{+})}{(c_{min}\Delta _{min})^2} +1 + 2K,\delta = K + 1/2\\ 
\frac{4K^2\delta \ln (KM^{+})}{(c_{min}\Delta _{min})^2} +1 + 2K \cdot O(1),\delta > K + 1/2\end{array}\right..

\eta _3 = \frac{2NM^{+}c_{max}}{KM^{-}c_{min}} \big (\eta _1\ln (\frac{2NM^{+}c_{max}\eta _1}{KM^{-}c_{min}}) - \eta _1 + \eta _2\big)


\eta _4 = \frac{NM^{+}c_{max}}{P_{\boldsymbol{V}^{\prime }}}

\varrho _{max}^{q} = \sum _{i\in \boldsymbol{V}^{\prime }}\sum _{j\in 
\mathcal {M}_i}w_j q_i - \min \limits _{\boldsymbol{S}_t^{\prime }\ne \boldsymbol{V}^{\prime }}\sum _{i\in \boldsymbol{S}_t^{\prime }} \sum _{j\in \mathcal {M}_i}w_j q_i. 
The answer will only contain 5 variables, namely N,M+,M-,K,B.
```

MAIN ChatGPT:
```markdown
To simplify and reduce the given multivariate function and determine its Big O notation, let's break down each term and identify the dominant terms.

The given function is:
\[ f(N, M^+, M^-, K, B) = (N\varrho_{\text{max}}^{q} + \eta_4 R_{\boldsymbol{V}^{\prime }}) \eta_1 \ln \left(\frac{2B}{P_{\boldsymbol{V}^{\prime }}} + \eta_3 \right) + \eta_2 \eta_4 R_{\boldsymbol{V}^{\prime }} + \eta_2 N \varrho_{\text{max}}^{q} + R_{\boldsymbol{V}^{\prime }} \]

We need to identify the dominant terms and their asymptotic behavior in terms of \(N\), \(M^+\), \(M^-\), \(K\), and \(B\).

### Step 1: Analyzing \(\eta\) terms
Let's analyze each \(\eta\) term one by one:

#### \(\eta_1\):
\[
\eta_1 = \begin{cases}
\frac{4K^2 \delta}{(c_{\text{min}} \Delta_{\text{min}})^2} + 2K, & \delta = K + \frac{1}{2} \\
\frac{4K^2 \delta}{(c_{\text{min}} \Delta_{\text{min}})^2}, & \delta > K + \frac{1}{2}
\end{cases}
\]
\[
\delta = K + \frac{1}{2} \text{ or } \delta > K + \frac{1}{2}
\]
In either case, \(\eta_1 = O(K^2)\).

#### \(\eta_2\):
\[
\eta_2 = \begin{cases}
\frac{4K^2 \delta \ln(KM^+)}{(c_{\text{min}} \Delta_{\text{min}})^2} + 1 + 2K, & \delta = K + \frac{1}{2} \\
\frac{4K^2 \delta \ln(KM^+)}{(c_{\text{min}} \Delta_{\text{min}})^2} + 1 + 2K \cdot O(1), & \delta > K + \frac{1}{2}
\end{cases}
\]
In either case, \(\eta_2 = O(K^2 \ln(KM^+))\).

#### \(\eta_3\):
\[
\eta_3 = \frac{2NM^+ c_{\text{max}}}{KM^- c_{\text{min}}} \left(\eta_1 \ln \left(\frac{2NM^+ c_{\text{max}} \eta_1}{KM^- c_{\text{min}}} \right) - \eta_1 + \eta_2 \right)
\]
Given \(\eta_1 = O(K^2)\) and \(\eta_2 = O(K^2 \ln(KM^+))\):
\[
\eta_3 = O\left(\frac{NM^+}{KM^-} K^2 \ln \left(\frac{NM^+}{KM^-}\right)\right) = O\left(\frac{N M^+ K \ln(NM^+)}{M^-}\right)
\]

#### \(\eta_4\):
\[
\eta_4 = \frac{NM^+ c_{\text{max}}}{P_{\boldsymbol{V}^{\prime}}}
\]
Assuming \(P_{\boldsymbol{V}^{\prime}}\) is not a function of the primary variables, \(\eta_4 = O(NM^+)\).

### Step 2: Analyzing \(\varrho_{\text{max}}^{q}\) and \(R_{\boldsymbol{V}^{\prime}}\)
Given the complexity of these terms, we'll assume that:
\[
\varrho_{\text{max}}^{q} = O(1) \quad \text{and} \quad R_{\boldsymbol{V}^{\prime}} = O(1)
\]

### Step 3: Combining Terms
Now, combine all terms in the given function:
\[
f(N, M^+, M^-, K, B) = \left(N \cdot O(1) + O(NM^+) \right) O(K^2) \ln \left(O(B) + O\left(\frac{N M^+ K \ln(NM^+)}{M^-}\right)\right) + O(K^2 \ln(KM^+)) O(NM^+) + O(K^2 \ln(KM^+)) O(1) + O(1)
\]

Simplifying each term:

1. \(N \cdot O(K^2) \ln(O(B)) = O(N K^2 \ln(B))\)
2. \(O(NM^+ K^2) \ln(O(\frac{N M^+ K \ln(NM^+)}{M^-})) = O(NM^+ K^2 \ln(N M^+ K))\)
3. \(O(K^2 \ln(KM^+)) O(NM^+) = O(N M^+ K^2 \ln(KM^+))\)

The dominant term will be \(O(NM^+ K^2 \ln(N M^+ K))\).

### Conclusion
Thus, the function \( f(N, M^+, M^-, K, B) \) simplifies to:
\[ f(N, M^+, M^-, K, B) = O(N M^+ K^2 \ln(N M^+ K)) \]
```

#### Reflection🔍

Although the answer doesn’t fully match the paper, I found the result improvable. So, I turned our dialogue into a teacher-student conversation and asked another ChatGPT to reflect on its own mistakes. So, I structured our dialogue as a teacher-student conversation and asked another ChatGPT to reflect on its own mistakes. However, it rechecked the answer and didn’t find any errors. I tried giving it the key to the problem (the final conclusion in the paper), but ChatGPT was bluffing, just copying my provided answer directly.

Here’s what I did next: I pointed out the trivial errors without giving away the answer. I identified the first issue: $\eta_1$ is not $O(K^2)$ but $O(K^3)$. I pointed this out, and its response improved, so I kept finding its mistakes.

Since I couldn’t see all the differences myself, I enlisted another ChatGPT to act as an agent to compare the simplified result with the standard answer for discrepancies. GPT told me there were no conflicts, just overly aggressive simplifications. Some terms could be kept without deleting them.

PROMPT:
```markdown
Math teacher, compare 

To simplify: "\left(N \cdot O(1) + O(NM^+) \right) O(K^2) \ln \left(O(B) + O\left(\frac{N M^+ K \ln(NM^+)}{M^-}\right)\right) + O(K^2 \ln(KM^+)) O(NM^+) + O(K^2 \ln(KM^+)) O(1) + O(1)
"
Simplified: "O(N M^+ K^2 \ln(N M^+ K))"

what is simplified and explain whether where is not reasonable.

But the key is "O\big (NMK^2\ln (B + {NMK^2}\ln ({NMK^2}))\big)". reason about this answer.

What is the difference in steps of this answer and the previous one?

are they in conflict????????????
```

AGENT:
```markdown
......
### Are they in conflict?

- The primary difference is in how the nested logarithms and the inclusion of \( B \) are handled.
- The proposed simplified form takes a more conservative approach by including \( B \) and the nested logarithmic term explicitly.
- The previously simplified form simplifies the logarithmic terms more aggressively.

### Conclusion:

- They are not in conflict but reflect different levels of granularity in simplification.
- The proposed simplified form \( O\left(NMK^2 \ln \left(B + NMK^2 \ln (NMK^2)\right)\right) \) is more detailed and considers the complexity more comprehensively.
- The previously simplified form \( O(NM^+ K^2 \ln(N M^+ K)) \) is a more concise but potentially less accurate representation of the complexity.
```

#### Iterative Refinement 🔄

Finally, I adjusted the previous prompts, added specific issues, and kept refining the prompts based on its answers. This approach ultimately yielded results similar to the paper. 🎉

PROMPT:
```markdown

"""Teacher: Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity. The letter O was chosen by Bachmann to stand for Ordnung, meaning the order of approximation.

In computer science, big O notation is used to classify algorithms according to how their run time or space requirements grow as the input size grows.[3] In analytic number theory, big O notation is often used to express a bound on the difference between an arithmetical function and a better understood approximation; a famous example of such a difference is the remainder term in the prime number theorem. Big O notation is also used in many other fields to provide similar estimates.

Big O notation characterizes functions according to their growth rates: different functions with the same asymptotic growth rate may be represented using the same O notation. The letter O is used because the growth rate of a function is also referred to as the order of the function. A description of a function in terms of big O notation usually only provides an upper bound on the growth rate of the function.

Associated with big O notation are several related notations, using the symbols o, Ω, ω, and Θ, to describe other kinds of bounds on asymptotic growth rates.

Here is the important part that you have to pay attention to:

For example, single-variate function:
f(n) = 9 log n + 5 (log n)^4 + 3*n^2 + 2 *n^3 = O(n^3)

Now, simply and reduce the multi-variate function:
"""
f(N,M+,M-,K,B,)=
(N\varrho _{max}^{q} +\eta _4 R_{\boldsymbol{V}^{\prime }})\eta _1\ln \Bigg(\frac{2B}{P_{\boldsymbol{V}^{\prime }}}+\eta _3\Bigg)+\eta _2\eta _4 R_{\boldsymbol{V}^{\prime }} \\ &\qquad\qquad\;\;+\eta _2 N\varrho _{max}^{q}+R_{\boldsymbol{V}^{\prime }}
"""
= O(?) deduce and reason about it step by step.
where,\eta _1 = \left\lbrace \begin{array}{l}\frac{4K^2\delta }{(c_{min}\Delta _{min})^2} + 2K,\delta = K + 1/2\\ 
\frac{4K^2\delta}{(c_{min}\Delta _{min})^2},\delta > K + 1/2\end{array}\right.
\eta _2 = \left\lbrace \begin{array}{l}\frac{4K^2\delta \ln (KM^{+})}{(c_{min}\Delta _{min})^2} +1 + 2K,\delta = K + 1/2\\ 
\frac{4K^2\delta \ln (KM^{+})}{(c_{min}\Delta _{min})^2} +1 + 2K \cdot O(1),\delta > K + 1/2\end{array}\right..

\eta _3 = \frac{2NM^{+}c_{max}}{KM^{-}c_{min}} \big (\eta _1\ln (\frac{2NM^{+}c_{max}\eta _1}{KM^{-}c_{min}}) - \eta _1 + \eta _2\big)


\eta _4 = \frac{NM^{+}c_{max}}{P_{\boldsymbol{V}^{\prime }}}

\varrho _{max}^{q} = \sum _{i\in \boldsymbol{V}^{\prime }}\sum _{j\in 
\mathcal {M}_i}w_j q_i - \min \limits _{\boldsymbol{S}_t^{\prime }\ne \boldsymbol{V}^{\prime }}\sum _{i\in \boldsymbol{S}_t^{\prime }} \sum _{j\in \mathcal {M}_i}w_j q_i. 
The answer will only contain 5 variables, namely N,M+,M-,K,B.

Student: To simplify and reduce the given multivariate function and determine its Big O notation, let's break down each term and identify the dominant terms.

The given function is:
\[ f(N, M^+, M^-, K, B) = (N\varrho_{\text{max}}^{q} + \eta_4 R_{\boldsymbol{V}^{\prime }}) \eta_1 \ln \left(\frac{2B}{P_{\boldsymbol{V}^{\prime }}} + \eta_3 \right) + \eta_2 \eta_4 R_{\boldsymbol{V}^{\prime }} + \eta_2 N \varrho_{\text{max}}^{q} + R_{\boldsymbol{V}^{\prime }} \]

We need to identify the dominant terms and their asymptotic behavior in terms of \(N\), \(M^+\), \(M^-\), \(K\), and \(B\).

### Step 1: Analyzing \(\eta\) terms
Let's analyze each \(\eta\) term one by one:

#### \(\eta_1\):
\[
\eta_1 = \begin{cases}
\frac{4K^2 \delta}{(c_{\text{min}} \Delta_{\text{min}})^2} + 2K, & \delta = K + \frac{1}{2} \\
\frac{4K^2 \delta}{(c_{\text{min}} \Delta_{\text{min}})^2}, & \delta > K + \frac{1}{2}
\end{cases}
\]
\[
\delta = K + \frac{1}{2} \text{ or } \delta > K + \frac{1}{2}
\]
In either case, \(\eta_1 = O(K^2)\).

#### \(\eta_2\):
\[
\eta_2 = \begin{cases}
\frac{4K^2 \delta \ln(KM^+)}{(c_{\text{min}} \Delta_{\text{min}})^2} + 1 + 2K, & \delta = K + \frac{1}{2} \\
\frac{4K^2 \delta \ln(KM^+)}{(c_{\text{min}} \Delta_{\text{min}})^2} + 1 + 2K \cdot O(1), & \delta > K + \frac{1}{2}
\end{cases}
\]
In either case, \(\eta_2 = O(K^2 \ln(KM^+))\).

#### \(\eta_3\):
\[
\eta_3 = \frac{2NM^+ c_{\text{max}}}{KM^- c_{\text{min}}} \left(\eta_1 \ln \left(\frac{2NM^+ c_{\text{max}} \eta_1}{KM^- c_{\text{min}}} \right) - \eta_1 + \eta_2 \right)
\]
Given \(\eta_1 = O(K^2)\) and \(\eta_2 = O(K^2 \ln(KM^+))\):
\[
\eta_3 = O\left(\frac{NM^+}{KM^-} K^2 \ln \left(\frac{NM^+}{KM^-}\right)\right) = O\left(\frac{N M^+ K \ln(NM^+)}{M^-}\right)
\]

#### \(\eta_4\):
\[
\eta_4 = \frac{NM^+ c_{\text{max}}}{P_{\boldsymbol{V}^{\prime}}}
\]
Assuming \(P_{\boldsymbol{V}^{\prime}}\) is not a function of the primary variables, \(\eta_4 = O(NM^+)\).

### Step 2: Analyzing \(\varrho_{\text{max}}^{q}\) and \(R_{\boldsymbol{V}^{\prime}}\)
Given the complexity of these terms, we'll assume that:
\[
\varrho_{\text{max}}^{q} = O(1) \quad \text{and} \quad R_{\boldsymbol{V}^{\prime}} = O(1)
\]

### Step 3: Combining Terms
Now, combine all terms in the given function:
\[
f(N, M^+, M^-, K, B) = \left(N \cdot O(1) + O(NM^+) \right) O(K^2) \ln \left(O(B) + O\left(\frac{N M^+ K \ln(NM^+)}{M^-}\right)\right) + O(K^2 \ln(KM^+)) O(NM^+) + O(K^2 \ln(KM^+)) O(1) + O(1)
\]

Simplifying each term:

1. \(N \cdot O(K^2) \ln(O(B)) = O(N K^2 \ln(B))\)
2. \(O(NM^+ K^2) \ln(O(\frac{N M^+ K \ln(NM^+)}{M^-})) = O(NM^+ K^2 \ln(N M^+ K))\)
3. \(O(K^2 \ln(KM^+)) O(NM^+) = O(N M^+ K^2 \ln(KM^+))\)

The dominant term will be \(O(NM^+ K^2 \ln(N M^+ K))\).

### Conclusion
Thus, the function \( f(N, M^+, M^-, K, B) \) simplifies to:
\[ f(N, M^+, M^-, K, B) = O(N M^+ K^2 \ln(N M^+ K)) \]
"""




The conclusion is wrong. 

THE first error is that it ignores the fact that "\delta = K + 1/2" with the numerator 4K^2\delta. So O of ita need further thinking.

THE second error is that the simplification is too aggressive, it reduce nested logarithm and B. But B in logarithm is an important variable. ln(A ln(C)) is better than ln(A), keep the nested logarithmic.

THE third error is that after simplifying each term, it ignores potential unite like terms, and abandon some of the variable carelessly. Pay special attention to M^- and B.

THE FORTH error is that it have to find a upper bound, so if there terms are added, denominator cannot be aggressively spared, and you have to enlarge the final result, e.g. O(A ln(B)) + A ln(C)), then you should put the final result in O(A ln(B+C)).

reexamine it step by step. AND ensure that the 1 2 3 4 errors are duly handled.
```