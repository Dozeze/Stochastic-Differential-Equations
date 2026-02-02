Stokastiska differential ekvationer kan användas i:

* Finans

* Ingenjörsskap

* Vetenskapliga modeller

* Maskininlärning

... och mycket mer. Nedan visas ett exempel på hur det kan användas:


## Noisy evoluation of stocks

Antag att värdet på en aktie ges av $S(t)$ - alltså beror den på tiden. Vi försöka modellera dens beteende genom att introducera en ordinär differential ekvation:


$$\frac{dS(t)}{dt} = a(t)S(t)$$

Denna differentialekvation har lösningen:

$$S(t) = e^{\int_0^t a(u)du}S(0)$$.

Men i aktiemarknaden så kan man modellera att aktierna köps och säljs halvt slumpmässigt, och det introducerar en viss störning. Man kallar störningen för "noise", och man kan modellera den genom att introducera det i modellen. Låt oss därför anta att $a(t)$ kan skrivas som:

$$a(t) = r(t) + \epsilon$$, där $\epsilon$ är en störning.

Detta ger oss då:

$$\frac{dS(t)}{dt} = (r(t) + \epsilon)S(t) = r(t)S(t) + \epsilon S(t)$$

Ett exempel på en modell som modellerar denna störning är differential ekvationen:

$$\Delta S(t) = r(t)S(t) \Delta t + \sigma S(t) \Delta W(t)$$

Ifall vi använder Eulers stegmetod (Euler forward) så kan vi diskritisera ekvationen som:

$$S_{n+1} - S_{n} = r_n S_n \Delta t + S_n \sigma_n \Delta W_n$$

Notera att vi till exempel kan använda att:

$$\mathbb{E}[ \Delta W_n ] = 0, \text{Var}[\Delta W_n] = t_{n+1} - t_{n} = \Delta t_n$$

## Brownian Motion/Wiener Process

Antag att vi har en sannolikhetsrum: $(\Omega, \mathcal{F}, \mathbb{P})$, så definierar vi Brownian motion som en funktion:

$$W : [0, \infty] \times \Omega \Rightarrow \mathbb{R}$$, där $\Omega$ betecknas som vårt "sannolikhetsrum",

som uppfyller att:

* $W_0 = 0$

* $W_t$ är kontinuerlig med sannolikhet 1, dvs att $\mathbb{P}(\{ W : t \rightarrow W_t(w) \text{ är kontinuerlig} \}) = 1$

* För varje partition för $0 = t \leq t_1 \leq t_2 \leq \dots \leq t_N$ så är varje inkrement $W_{t_{n+1}} - W_{t_{n}}$ oberoende

* För varje $t \geq 0$ och $u \geq 0$, så gäller att $W_{t+u} - W_{t} \sim N(0, u)$, dvs att $\mathbb{P}(W_{t+u} - W_{t} \in A) = \int_A \frac{1}{\sqrt{2 \pi u}} \exp (\frac{u^2}{2u})$

Med detta sagt, låt oss kolla värdet för en stokastisk integral. Notera att för en Riemann-integral så har vi att:


**Def: Riemannintegral**

En partition för $[a,b]$ definieras som:  $P = \{a = x_0, x_1, \dots, x_N = b \}$. Definiera den nedgre begränsningen för funktionsvärdet som: $m_i = \inf \{ f(x) | x \in [x_{i-1}, x_{i} \}$, och den övre begräsningen för funktionsvärdet som: $M_i = \sup \{ f(x) | x \in [x_{i-1}, x_{i} \}$. Låt $f(x)$ vara en begränsad funktion på intervallet $[a,b]$, och definiera:

$$L(f, P) = \sum_{i=0}^{n} m_i (x_{i-1} - x_i)$$ som "Lower sum", och:

$$U(f, P) = \sum_{i=0}^{n} M_i (x_{i-1} - x_i)$$ som "Upper sum".

Vi säger att $f$ är Riemann integrerbar om:

$$\sup_P L(f, P) = \inf_P U(f, P)$$.

Exempel:

Låt oss undersöka $f(x) = x^2$ i invervallet $[0,1]$. Tag $P = \{0, 1/n, 2/n \dots, n/n = 1\}$. Då får vi att:

$$m_i = \inf \{ f(x) | x \in [x_{i-1}, x_{i} \} = f(x_{i-1})$$

$$M_i = \sup \{ f(x) | x \in [x_{i-1}, x_{i} \} = f(x_i)$$

Då gäller:

$$L(f, P) = \sum_{i=0}^{n} f(x_{i-1}) (x_{i-1} - x_i) = \sum_{i=0}^{n} x_{i-1}^2 \frac{1}{n} = \sum_{i=0}^{n} (i-1)^2 \frac{1}{n^3} = $$
$$\frac{(n-1)(2n-1)}{6n^2}$$

$$U(f, P) = \sum_{i=0}^{n} f(x_{i}) (x_{i-1} - x_i) = \sum_{i=0}^{n} x_{i}^2 \frac{1}{n} = \sum_{i=0}^{n} (i)^2 \frac{1}{n^3} = $$
$$\frac{(n + 1)(2n + 1)}{6n^2}$$

Vi har att för $n \in \mathbb{Z}_{>0}$ så gäller det att $U > 1/3$, och $L < 1/3$. Men då får vi att $\sup_L = 1/3$ och $\inf_L = 1/3$, precis när $n \rightarrow \infty$. Eftersom att de är samma så drar vi slutsatsen att $f$ är Riemann integrerbar.

Syftet varför vi definierade Riemanintegralen var för att ifall vi antar att $W(t)$-funktionen är Riemann integrerbar, så ska:

$$\sum_{i=0}^n W(t_i) (W_{t_{i+1}} - W_{t_i}) = \sum_{i=0}^n W(t_{i+1}) (W_{t_{i+1}} - W_{t_i})$$.

Men det finns inte mycket att säga om denna integral, men eftersom att vi har antagit att den är Riemann-integrerbar, så borde ändå $\mathbb{E}[VL] = \mathbb{E}[HL]$, där VL = Vänsterled, HL = Högerled. Låt oss därför undersöka det:

$$\mathbb{E}[VL] = \mathbb{E}[\sum_{i=0}^n W(t_i) (W_{t_{i+1}} - W_{t_i}) ] = \sum_{i=0}^n \mathbb{E}[W(t_i) (W_{t_{i+1}} - W_{t_i}) ] = \sum_{i=0}^n \mathbb{E}[(W(t_i) - W(t_0)) (W_{t_{i+1}} - W_{t_i}) ] = $$

[Inkrementen är oberoende av varandra]

$$\sum_{i=0}^n (\mathbb{E}[(W(t_i) - W(t_0))] \mathbb{E}[(W_{t_{i+1}} - W_{t_i}) ]) = \sum_{i=0}^n (\mathbb{E}[(W(t_i) - W(t_0))] \cdot 0 = 0$$

Alltså är integralen lika med noll. Låt oss undersöka väntevärdet av HL:

$$\mathbb{E}[\sum_{i=0}^n W(t_{i+1}) (W_{t_{i+1}} - W_{t_i})] = \mathbb{E}[\sum_{i=0}^n W(t_{i+1}) (\Delta W_{t_i})] = \mathbb{E}[\sum_{i=0}^n (W(t_{i+1}) - W(t_i) + W(t_i)) (\Delta W_{t_i})] = $$
$$\mathbb{E}[\sum_{i=0}^n (\Delta W_{t_i}) + W(t_i)) (\Delta W_{t_i})] = \sum_{i=0}^n \mathbb{E}[(\Delta W_{t_i}) + W(t_i)) (\Delta W_{t_i})] = \sum_{i=0}^n \mathbb{E}[(\Delta W_{t_i})^2 + W(t_i)(\Delta W_{t_i}))] = $$
$$\sum_{i=0}^n (\mathbb{E}[\Delta W_{t_i})^2] + \mathbb{E}[W(t_i)(\Delta W_{t_i})]) = (0^2 + t^2) + 0 = t^2$$

Det är alltså ganska klart att $\mathbb{E}[VL] \neq \mathbb{E}[HL]$. Detta är ett problem för att ifall vi har definierat en integral som en Riemannsumma så får vi två olika svar. Vi vill därför definiera integralen med hjälp av någon diskretisering, och så håller vi oss fast vid den definitionen OM den existerar. Hur vi tar reda på ifall den existerar är att vi abstrakt definierar integralen på ett visst sätt, och så kollar vi ifall den konvergerar i ett visst rum. Ifall den gör det, så existerar den i det rummet, och då kan vi extrahera en massa egenskaper utifrån det där rummet och använda matematik för att komma fram till olika slutsatser som gynnar vårt arbete.

Vi börjar med att definiera en funktion som är Lischnitz kontinuerlig (som implicerar att funktionen är kontinuerlig och inte ändras mycket när vi ändrar lite i våra koordinater). Dvs:

$$|f(t + \Delta t, W + \Delta W) - f(t, w)| \leq C( \Delta t + | \Delta W | )$$

Eftersom att den beror på vår Wiener process och vårt tidsintervall, så kan vi säga att funktionen ger oss en stokastisk process. En stokastisk process är en process $P = (P_0, \dots, P_n)$ där varje element är stokastisk. Till exempel kan vi sätta $f(W_t, t) = W_t + t$. Det är mer eller mindre en funktion som är stokastisk, och processen är att den ändras med tiden, och vi kan indicera varje punkt som $P_n$. Med detta sagt så ska vi tillbaka till vad vi ville göra. Vi ville definiera en stokastisk integral. Så vad vi vill göra är att vi vill definiera en integral genom att säga att:

$$I = \sum_{i=0}^n f(W(t_n), t_{n})(W(t_{n+1}) - W(t_n))$$.

Det vill säga; vår integral definieras som Euler framåt approximationen av den riktiga integralen. Det går att definiera den som Euler bakåt, eller andra approximationer av integralen, men just nu så säger vi att integralen defnieras som Euler framåt approximationen av integralen. Ifall vi tar två partitioner av t:

$$(\bar{t})_{i=1}^{\bar{N}}, \bar{t}_0 = 0, \bar{t}\_{\bar{N}} = T$$

,och

$$(\bar{\bar{t}})_{i=1}^{\bar{\bar{N}}}, \bar{\bar{t}}_0 = 0, \bar{\bar{t}}\_{\bar{\bar{N}}} = T$$,

så kan vi använda dem för att definiera två diskretiseringar av samma integral med Euler framåt:

$$\bar{I} = \sum_{n=0}^{\bar{N}} f(W(\bar{t}_n, \bar{t}_n) (W(\bar{t}\_{n+1} - W(\bar{t}_n)))$$,

och

$$\bar{\bar{I}} = \sum_{n=0}^{\bar{\bar{N}}} f(W(\bar{\bar{t}}_n, \bar{\bar{t}}_n) (W(\bar{\bar{t}}\_{n+1} - W(\bar{\bar{t}}_n)))$$.

Ifall vi låter $\Delta t_{max}$ vara det största steget i båda partitionerna, dvs:

$$\Delta t_{max} = \max ( \max_{n} \bar{t}_{n+1} - \bar{t}_n, \max\_{\bar{n}} \bar{\bar{t}}\_{n+1} - \bar{\bar{t}}_n )$$

så går det att visa att väntevärdet mellan skillnaden av dessa integraler i kvadrat kommer alltid vara mindre eller lika med $\Delta t_{max}$. Dvs:

$$\mathbb{E}[(\bar{I} - \bar{\bar{I}})^2] \leq \Delta t_{max}$$.

Vad detta säger är att ifall $\Delta t_{max} \rightarrow 0$ så konvergerar dessa två approximerade integraler mot varandra. Med andra ord så är detta är en Cauchysekvens, och då vet vi att sekvensen konvergerar. Vi definierar nu:

"Ito integralen" som gränsen av denna Cauchy sekvens. 
