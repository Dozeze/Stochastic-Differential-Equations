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

##
**Stokastiska differential ekvationer**

Eulers metod:

Är ett sätt att estimera en ODE. Låt till exempel $y(t)$ vara en funktion. För att hitta $y(t)$ så kan vi diskritisera den. Då får vi tidsintervall: $t_0 \leq t_1 \leq \dots \leq t_N$. Med Eulers metod så kan vi lösa varje punkt $y(t_n)$:

$$y(t_{n+1}) = y(t_n) + \delta t y'(t_n)$$

Ifall vi skriver den approximerade funktionen som $\bar{y}(t)$ så får vi att felet: $|y(t) - \bar{y}(t)| = \mathcal{O}(\Delta t^2)$.

Hur som helst så kan vi definiera en funktion som rör sig i tiden. Låt oss kalla den funktionen för $X(t)$. Notera att den beror på tiden $t$. Men vi vill modellera den så att den dels beror på en funktion som rör sig i tiden, och en annan funktion som rör sig lite slumpmässigt.

Låt oss därför skriva:

$$dX(t) = a(t, X(t))dt + b(t, X(t))dW(t)$$

Vad den säger är att ifall vi rör $X(t)$ en liten bit, så kommer den att bero på en funktion $a(t, X(t))$ som rör sig i tiden, och en annan funktion $b(t, X(t))$ som rör sig lite slumpmässigt - precis som vi ville! Men hur ska vi approximera den? Vad vi kan göra är att vi kan använda oss av Eulers metod för att lösa $X(t_n)$ för något tidsintervall $t_0 \leq \dots \leq t_N$. Enligt Eulers metod så får vi då diskretiseringen:

$$X_{n+1} - X_n = a(t_n, X_n)(t_{n+1} - t_n) + b(t_n, X_n)(W(t_{n+1}) - W(t_n)) = a(t_n, X_n)\Delta t_n + b(t_n, X_n) \Delta W(t_n)$$

Men en fråga uppstår, och det är - konvergerar denna funktion för Euler framåt? Normalt så gör den det, men vi har en funktion vars förändring beror på tiden och en stokastisk process. Den stokastiska processen har potentiellt oändligt många lösningar eftersom att den kan röra sig annorlunda i varje tidssteg. Så vad vi vill göra är att vi vill kolla ifall $\mathbb{E}[|X(t) - \hat{X}(t)|^2] \rightarrow 0$ när $\Delta t \rightarrow 0$; dvs att den konvergerar i L2. Detta kallas för "Strong convergence". Ett annat sätt att göra det är genom att skapa en Cauchy sekvens .... ( Fortsätt förklara detta ).

Vi kommer göra detta vecka 3. Notera att ifall vi sätter restriktioner på funktionerna $a$, $b$ och en massa andra saker:

1) $\leq C \Delta t_{\text{max}}$

etc..

Så får vi konvergens:

$$\mathbb{E}[()^2] \leq C \Delta t_{\text{max}}$$

Låt oss visa att vi också kan visa konvergens på ett annat sätt (se vecka 3).
