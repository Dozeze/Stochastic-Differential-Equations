# Week 3

Handlar om ...

## Ito SDE Convergence

Ito's SDE konvergens. För att visa detta så behöver vi veta Grönwalls lemma och ett uttryck för en energybegränsning (Energy Bound)

To prove this, we have to know Grönwall's Lemnma, and a expression for an Energy Bound. Then we'll go through a proof overviiew

## Ito's Formula (Chain Rule)

* Kommer att använda energigränsen (Energy Bound)

=> Med Ito's formel så kan vi få en bättre begränsning på "energi begränsningen"

## Stratonovic Integral

## Optimal Estimate of a Brownian motion $W_t |  W_{t_1}, \dots, W_{t_n}$


## SDE Konvergens Teori

Låt $W : [0,T] \times \Omega \rightarrow \mathbb{R}$ vara Brownian Motion, och $a,b : t$ vara funktioner. 

Tag $(\bar{t})_{n=1}^N$ och $(\bar{\bar{t}}) _{n=0}^N$ vara partitioner av $[0,T]$.

Låt $\Delta \bar{W}_n = W_{\bar{t}_{n+1}} - W_{\bar{t}_{n}}$,
och $\Delta \bar{t}_n = \bar{t}_{n+1} - \bar{t}_{n}$. Definiera $\bar{X}_{n+1} = \bar{X}_{n} + a(\bar{t}_n, \bar{x}_n) \Delta \bar{t}_n + \bar{X}_{n} + b(\bar{t}_n, \bar{x}_n) \Delta \bar{t}_n$. Vi skriver:

$$a(s, \dot) = \sum_{n=1}^{N-1} a() 1_{[t_n, t_{n+1}}(s)$$. Samma för $\bar{\bar{a}}$, etc...

Definiera funktionen $\hat{X} : [0,T] \times \Omega \rightarrow \mathbb{R}$, så får vi att:

$\hat{X}_t = \hat{X}_0 + \int_0^t \bar{a}(s, \dot) ds + \int_0^t \hat{b}(s, \dot) d W_s$

**Teori**
Låt $W,a,b,\bar{X}, \bar{\bar{X}}$ vara som definierat. Antag att:

$$\vert a(t,x) - a(t, y) \leq C \vert x -y \vert$$
$$\vert a(t,x) - a(t, y) \leq C (1 + \vert x \vert)$$

Då får vi att 

$$\mathbb{E}[|\bar{X}_0 | - | \bar{\bar{X}}_0 |] \leq C$$


$$\mathbb{E}[|\bar{X}_0 - \bar{\bar{X}}_0 |] \leq C \Delta t_{max}$$

Då får vi att


$$\mathbb{E}[\bar{X}^2_t - \bar{\bar{X}}^2_t] \leq c \Delta t_{max} e^{cT^2}$$


$$\mathbb{E}[\bar{X}^2_t + \bar{\bar{X}}^2_t] \leq c \Delta e^{cT^2}$$


##Grönlands lemma

Antag $f : [0,T] \rightarrow \mathbb{R}$ uppfyller att $f(t) \leq A + B \int_0^t f(s)ds$, för $t \leq T$. Då får vi att:

$$f(t) \leq A e^{Bt}$$, $t \leq T$.

Bevis:

Låt $I(t) = \int_0^t f(t)dt$. Då får vi att $I'(t) \leq A + B I(t)$. Men:

$$I'(t) - B I(t) \leq A \Rightleftarrow (I'(t) - B I(t))e^{-Bt} \leq Ae^{-Bt}$$

Tar vi derivatan så får vi:

$$\frac{d}{dt} (I(t)e^{-Bt}) }keq Ae^{-Bt} \Rightarrow I(t)e^{-Bt} \leq \int_0^t Ae^{-Bs}ds = \frac{A}{B}(1 - e^{-Bt}$$

vilket är ekvivalent med:

$$I(t) \leq \frac{A}{B} (e^{Bt} - 1)$$

$$f(t) \leq I'(t) \leq A + BI(t) = ... = Ae^{Bt}$$ !?

## Användbar när $f(t) = \mathbb{E}[X^2_t]$

## Energy Bound

Antag att $X, a, b$ är funktioner $[0,T] \times \Omega \rightarrow \mathbb{R}$ som uppfyller:

$$x_t = x_0 + \int_0^t a(s, \dot)ds + \int_0^t b(s, \dot) d W_s$$, och antag att:

$$\mathbb{E}[x^2_0] \leq C, \mathbb{E}[a(t, \dot) + b(t, \dot)] \leq ...$$

Då får vi att:

$$\mathbb{E}[x^2_t[ \leq 3(c + (1 + T)^2 TA e^{3(T+1)TB})$$

Bevis:

$$\mathbb{E}[x^2_t] = \mathbb{E}[(x_0 + \int_0^t a(s, \dot)ds + \int_0^t b(s, \dot) d W_s)^2]$$.

Vi använder Jensens olikhet

$$\leq 3 \mathbb{E}[x^2_0] + 3 \mathbb{E}[(\int_0^t a(s, \dot)ds)^2] + 3\mathbb{E}[(\int_0^t b(s, \dot) d W_s)^2]$$

... Får anteckna sen


