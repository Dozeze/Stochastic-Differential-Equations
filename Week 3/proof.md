Konvergensteori för SDE

För att visa att det existerar en lösning för en stokastisk differentialekvation, när vi approximerar den med Euler framåt, så måste vi visa att lösningen konvergerar mot ett tal. Ifall vi approximerar vår lösning till differentialekvationen med Euler framåt, så har vi på något sätt skapat en sekvens. Vi vill visa att sekvensen konvergerar. Notera att vårt rum, $L^2( \Omega )$ är komplett, vilket innebär att ifall en funktion $f$ i detta rum konvergerar om och endast om den är Cauchy. Alltså räcker det med att visa att den är en Cauchysekvens. Låt oss därför börja med definitionen av en Cauchy sekvens:

##

**Def: Cauchy sekvens**
Låt $A_1, A_2, \dots$ vara en sekvens i ett rum, $(A, d)$, så säger vi att sekvensen är Cauchy ifall för varje $\epsilon > 0$ så existerar $n,m \in \mathbb{N}$ s.a. $d(A_n, A_m) < \epsilon$

Notera att i vårt rum, så är $(A,d)$ lika med $Y : [0,1] \times \Omega \rightarrow \mathbb{R}^d$, där $A$ är någon stokastisk process $ $d(A,B) = \sqrt{\mathbb{E}[|A - B|^2]}$, och detta rum är komplett.

##

Notera att diskretiseringen av vår lösningen till en differentialekvation, $X$, kan skrivas på flera sätt. Vi väljer $(t_0, \dots, t_{N-1})$. Alltså, för att visa att den är Cauchy så måste vi ta skillnaden mellan två olika diskretiseringar för att visa att hela familjen är Cauchy. När vi har visat att alla diskretiseringar av $X$ är cauchy, så vet vi enligt teori att de konvergerar. Men innan vi börjar med detta, så måste vi definiera vad en lösning, $X$, verkligen är. Anta att vi vill lösa den stokastiska differentialekvationen:

$$dX(t) = a(t, X(t))dt + b(t, X(t))dW(t)$$

där $W(t)$ är en Wiernerprocess. Låt oss nu skapa en diskretisering med Euler framåt:

$$\bar{X}_{n+1} = \bar{X}\_{n} + a(\bar{t}_n, \bar{X}\_{n}) \Delta \bar{t}_n + a(\bar{t}_n, \bar{X}\_{n}) \Delta \bar{W}_n$$

Ifall vi definierar funktionen $\bar{a}(s, .) = \sum_{n=0}^{N-1} a(\bar{t}_n, \bar{X}_n) 1\_{[t_n, t\_{n+1})}(s)$ så får vi att ifall $s \in [t_n, t\_{n+1})$ så blir den precis $a(\bar{t}_n, \bar{X}_n)$. Därmed så får vi att för punkter som är mellan våra tidsintervaller nu också är definierade för funktionen. Vi gör samma för $\bar{b}(s, .) = \sum\_{n=0}^{N-1} b(\bar{t}_n, \bar{X}_n) 1\_{[W_n, W\_{n+1})}(s)$. Vi definierar ett till tidsintervall, $(\bar{\bar{t}})\_{n=0}^{N-1}$, och definierar $\bar{\bar{a}}$, och $\bar{\bar{b}}$ likadant. Låt oss nu ställa några krav på våra funktioner. Vi vill att de ska vara "snälla":

* $|a(t, x) - a(t, y)| \leq C |x - y|$ för något $C$ (Dvs att den rör sig inte rör mycket när vi rör oss i den stokastiska axeln)

* $|a(t, x) - a(s, x)| \leq C (1 + |x|) \sqrt{|s - t|}$ för något $C$ (Dvs att den inte rör sig för mycket när vi rör oss i tiden)

* samma för $b$.

* $\mathbb{E}[|\bar{X}(0)|^2 + \bar{\bar{X}}(0)^2|] \leq C$ för något C

* $\mathbb{E}[|\bar{X}(0) - \bar{\bar{X}}(0)|^2] \leq C \Delta t_{\text{max}}$ för något C

Ifall vi sätter dessa krav på våra funktioner så går det att visa att:

$\mathbb{E}[\bar{X}\_t^2 + \bar{\bar{X}}_t^2] \leq C e^{CT^2}$ och $\mathbb{E}[|\bar{X}\_t^2 - \bar{\bar{X}}_t|] \leq C \Delta t_{\text{max}} e^{CT^2}$.

M
