**Definition: Anpassad funktion**

Vi säger att en process $f : [0, T ] × \Omega \rightarrow \mathbb{R}$ är anpassad (adapted) om $f (t, \cdot)$ bara beror på event som är genererade av $W(s)$, där $s \leq t$. Vad vi menar är att vår funktion endast beror på det som hände innan, och inte det som kommer att hända i framtiden. 
Ifall vi till exempel tar en aktie som ett exempel, och vi skriver $f = \max_{t_0, \dots, t_N} W(t_n)$. Ifall vi låter $W(t)$ vara aktiepriset, så beskriver $f$ aktiepriset när den var som störst. Notera att den endast beror på förgående värden för $W(t)$ och inget annat, och är därmed anpassad.
Ett annat exempel är ifall vi vill hitta medelvärdet för aktien - $\mathbb{E}[W(s)] = \int_0^T W(s)ds$. Denna funktion kallas för "the moving average", och beror endast på förgående händelser och inget annat - också en anpassad funktion.



Notera att $\omega \in \Omega$. Alltså ifall $\Omega$ är utfall i ett sannolikhetsrum så betyder det att $\omega$ är ett utfall. För funktionen $f(\cdot, \omega)$ så betyder det att utfallet $\omega$ hade tagits. Ett exempel med aktier återigen:

Låt $f$ återigen vara våra aktier. Låt $\Omega = \{w_A, w_B\}$, där i $w_A$ är aktiemarknaden när det går bra, och $w_B$ när det går dåligt. Eftersom att vi förväntar oss att våra aktier kommer bli värda mer i $w_A$ än $w_B$ så kanske vi tror att:

$f(t, w_A) > f(t, w_B)$. Men eftersom att $f$ endast beror på det som hände innan, så spelar det ingen roll. Men däremot så kan $\mathbb{E}[f(t, w_A)] > \mathbb{E}[f(t, w_B)]$ när $t > T$, men vi kan inte riktigt se in i framtiden. Tror vi kommer undersöka detta i senare föreläsningar.


##
**Lemma: Hur mycket funktionen får "röra på sig"**:
Om vi antar att $f$ är en anpassad funktion, så existerar det en konstant $C$ sådana att:

$$\sqrt{\mathbb{E}[|f(t + \Delta t, \omega) - f(t, \omega)|^2]} \leq C \Delta t$$

Låt oss definiera Ito-integralen lite fort:
**Def: Ito integral** Låt $W_t$ vara en Wierner process, $f : [0, T] \times \Omega \rightarrow \mathbb{R}$ en anpassad stokastisk process som uppfyller Lipschitz kontinuitet, och låt $\lim_{n \rightarrow \infty} (t_i)_{i=0}^N$, där $0 = t_0 \leq \dots \leq t_N = T$ för alla $N$, och
$\lim\_{n \rightarrow \infty} max\_{n \in \mathbb{N}} | t\_{n+1} - t_n | = 0$, så konvergerar integralen i L2:

$$\int_0^T f(t, \cdot) dw(t) = \lim_{n \rightarrow \infty} \sum_{n=0}^{N-1}f(t_n, \cdot)(w(t_{n+1}) - w(t_n))$$

##
**Egenskaper från Ito-integralen**

Om $f,g$ är ito integrerbara, är anpassade, är Lipschitz kontinuerliga, $a,b \in \mathbb{R}$ så gäller:

1) Linjäritet: $\int_0^T (a f(t) + b g(t))dW(t) = a \int_0^T f(t)dW(t) + b \int_0^T g(t)dW(t)$

2) Väntevärde noll: $\mathbb{E}[\int_0^T f(t)dW(t)] = 0$

3) Isometri: $\mathbb{E}[\int_0^T f(t)dW(t) \int_0^T g(t)dW(t)] = \int_0^T \mathbb{E}[f(t)g(t)]dt$
