Stokastiska differential ekvationer kan användas i:

* Finans

* Ingenjörsskap

* Vetenskapliga modeller

* Maskininlärning

... och mycket mer. Nedan visas exempel på hur det kan användas:


**Noisy evoluation of stocks**

Antag att värdet på en aktie ges av $S(t)$ - alltså beror den på tiden. Vi försöka modellera dens beteende genom att introducera en ordinär differential ekvation:


$$\frac{dS(t)}{dt} = a(t)S(t)$$

Denna differentialekvation har lösningen:

$$S(t) = e^{\int_0^t a(u)du}S(0)$$.

Men i aktiemarknaden så kan man modellera att aktierna köps och säljs halvt slumpmässigt, och det introducerar en viss störning. Man kallar störningen för "noise", och man kan modellera den genom att introducera det i modellen. Låt oss därför anta att $a(t)$ kan skrivas som:

$$a(t) = r(t) + \epsilon$$, där $\epsilon$ är en störning.

Detta ger oss då:

$$\frac{dS(t)}{dt} = (r(t) + \epsilon)S(t) = r(t)S(t) + \epsilon S(t)$$

vilken kan diskretiseras som:

$$S_{n+1} - S_{n} = \delta t r_n s_n + \epsilon s_n \delta t$$
