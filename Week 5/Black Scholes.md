Anta att $S_t$ är priset på en aktie vid tid $t$. Låt oss också anta att vi kan köpa ett "europeiskt kontrakt", som ger oss rätt till att köpa en aktie i framtiden.

Exempel:

En aktie kostar 100kr. Låt oss anta att ett kontrakt kostar 5 kr. Kontraktet säger att vid tid $T$ så får du köpa aktien för 105kr. Vid tid $T$ så har aktien gått upp till 150kr. Då kan du köpa den för 105kr. Du har nu vunnit 130-105-5 = 20kr. Ifall aktien kraschar 
och går ner till 50kr så behöver du inte köpa den, och då har du endast förlorat 5kr.

Låt oss nu kalla priset på vårt kontrakt för ett "strike price", och att den är värderad $K$. Notera att tiden $T$ är den tiden vårt kontrakt löper ut, och tiden vi måste göra ett val att antingen köpa eller inte köpa aktien. Låt oss skriva priset på vårt kontrakt som 
$V(S,t)$ - alltså beror den på dels hur mycket aktien kostar, och vilken tid vi befinner oss i.  Låt $r$ vara den riskfria räntan av en aktie. Det låter korkat att en aktie är riskfri, men vi vill inkludera det här i vår modell. Låt $\sigma$ vara volatilitet, dvs
hur mycket aktien rör sig osäkert. Ett exempel på detta skulle vara att ifall aktien rör sig mycket upp och ner så är volatiliteten hög, och ifall den är väldigt stadig så är volatilitet låg. Låt $\mu$ vara hur mycket aktien i snitt rör sig per tidsenhet.

Låt oss nu modellera en aktie:

$$dS_t = \mu S_t dt + \sigma S_t dW_t$$

Intuition:

Ifall aktien inte rörde sig slumpmässigt, utan hade en klar bana så hade vi modellerat den som:

$$dS_t = \mu S_t dt$$

Som har lösningen

$$S_t = S_0e^{\mu t}$$

Dvs, att aktien ökar med $\mu$ vid varje tidsenhet, som ger oss det svaret. Ifall vi lägger till randomness i vår mådell så får vi precis


$$dS_t = \mu S_t dt + \sigma S_t dW_t$$

Låt oss gå tillbaka till vårt europeiska kontrakt. Låt oss skriva hur mycket vi hade tjänat av att antingen köpa aktien eller inte vid tid $T$. Det blir lika med $\max(S_T - K, 0)$. Notera att vi inte har tagit med vad kontraktet kostade här, utan detta är endast
vad vi hade tjänat efter vårt kontrakt. Tillbaka till priset av vårt kontrakt; $V(S(t), t)$. Hur vet vi egentligen hur mycket den borde vara värd? Vi vet att vid tid $T$ så har kontraktet löpt ut, så antingen är den värdelös, och borde kosta 0 kr, eller kosta
$S_T - K$ kr. Ifall den kostade mer än $S_T - K$ kr vid tid $T$, så förlorar vi pengar på att köpa kontraktet (eftersom att vi är tvungna att antingen köpa aktien direkt eller inte köpa den direkt). Alltså borde den vara värderad $\max(S_T - K, 0)$ kronor vid
tid $T$. Alltså; $V(S_T, T) = \max (S_T - K, 0)$.

Låt oss nu introducera ett portfölj: $\Pi$. Vi vill investera pengar, och vi vill på något sätt beräkna hur mycket pengar vi kommer tjäna i vårt portfölj. Låt oss anta att den löper NOLL risk, och vi vet exakt hur mycket pengar vi kommer att tjäna. Då
kan vi den som en ODE:

$$d \Pi = r \Pi dt$$

Och låt oss anta att vi köper europeiska kontrakt i vårt portfölj. Hur mycket den kommer att vara värd blir då:

$$\Pi = V(S_t, t) - S_t \frac{\partial}{\partial S }V(S_t, t)$$

Det vill säga att - 
