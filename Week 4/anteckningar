Föreläsning 4

Innehåller:

* Bevis för Itos formel

* Geometrisk BM: $d S_t = \mu S_t dt + \sigma S_t dW_t$

* Weak/Strong konvergens

* Feynman K. formel / Kolmogorov bakåt ekvationer

* Exempel, analogier till deterministiska fall

* Black Scholes, pris av europeiska "option"

##

**Itos formel**

Låt $X_t$ lösa differnetialekvationen $dX_t = a_t dt + b_t dW_t$, där $t \leq T$, $X_0 = x$, och $a,b$ är funktioner som uppfyller villkoren för konvergens för SDE, och $\mathbb{E}[a^4_t + b^4_t] < \infty$.

Då gäller för en två ggr deriverbar funktion, $g \in C^2([0,T]^2 \times \mathbb{R}, \mathbb{R})$, $y_t = g(t, x_t)$ uppfyller:


$$dy_t (d_t \g_t + a_t d_x g_t + \frac{1}{2} b_t^2d_x^2g_t)dt + b_t d_xg_td_W_t$$

$$y_0 = g(0, X_0)$$

där vi antar att $d_xg, d_tg,d_x^2g, d_xd_t g, d_t^2g, g=x^2$ ??

Bevis:

... (Finns i anteckningar)

##

**Geometrisk BM: $d S_t = \mu S_t dt + \sigma S_t dW_t$**

Exempel: $\mu S_t dt + \sigma S_t dW_t, \mu > 0, \sigma > 0$

Låt $\log(S_t) = \mu t + \ln(S_0)$

Idé: $g(x) = \log(x)$, och $y_t = g(S_t)$ via Ito. $dY_t = (0 + \mu S_t \frac{1}{S_t} + \frac{1}{2} (\sigma S_t)^2 (- \frac{1}{S_t^2})dt + \sigma_S_t \frac{1}{S_t}dW_t = (\mu - \frac{\sigma}{2})$

vilket har lösningen

$$Y_t = Y_0 + (\mu - \frac{1}{2}\sigma^2)t + \sigma W_t$$

vilket ger:

$$S_t = \€xp(Y_t) = e^{Y_0} e^{}$$
