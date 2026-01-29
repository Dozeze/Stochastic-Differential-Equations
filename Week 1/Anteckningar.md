Stokastiska differential ekvationer kan användas i:

* Finans

* Ingenjörsskap

* Vetenskapliga modeller

* Maskininlärning

... och mycket mer. Nedan visas ett exempel på hur det kan användas:


**Noisy evoluation of stocks**

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

**The Coarse-graining and Discretization Analysis**



