Här kommer vi att lösa tre problem:


## Ifall $t > 0$, $W_t$ en Wierner process, så gäller att $\lim_{u \rightarrow 0^{+}} \mathbb{E}[ |\frac{W(t+u) - W(t)}{u}| ] \rightarrow \infty$. 

Vad detta implicerar är att derivatan för en Wiernerprocess inte existerar.

Bevis:

Eftersom att väntevärdet är linjär, och $u > 0$, så kan vi skriva om problemet som:

 $$\lim_{u \rightarrow 0^{+}} \mathbb{E}[ |\frac{W(t+u) - W(t)}{u}| ] \rightarrow = \lim_{u \rightarrow 0^{+}} \frac{1}{u} \mathbb{E}[ |W(t+u) - W(t)| ] $$.

Vi ska utnyttja att vår Wierner process uppfyller: $W(t+u) - W(t) = Z \sim N(0, u)$. Notera att för en stokastisk variabel $X \sim N(0,1)$ så har vi att $\sqrt(a) X \sim N(0,a)$. Vi kan därmed skriva om vårt uttryck som:

$$\lim_{u \rightarrow 0^{+}} \frac{1}{u} \mathbb{E}[ |W(t+u) - W(t)| ] = \lim_{u \rightarrow 0^{+}} \frac{1}{u} \mathbb{E}[ |\sqrt(u)X| ] = \lim_{u \rightarrow 0^{+}} \frac{1}{\sqrt{u}} \mathbb{E}[ |X| ] = $$

$$\lim_{u \rightarrow 0^{+}} \frac{1}{\sqrt{u}} \int_{-\infty}^{\infty} |x|\frac{e^{x^2/2}}{\sqrt{2\pi}} = \lim_{u \rightarrow 0^{+}} \frac{1}{\sqrt{u}} \int_{0}^{\infty} x \frac{e^{x^2/2}}{\sqrt{2\pi}} \lim_{u \rightarrow 0^{+}} \frac{1}{\sqrt{u}} \cdot \frac{1}{2} \rightarrow \infty$$.



## Visa att $\lim_{N \rightarrow \infty} \mathbb{E}[\sup_{0 \leq t_0 \leq \dots \leq t_N = 1} \sum_{n=0}^{N-1} |W(t_{n+1}) - W(t_{n})|] \rightarrow \infty$. 

Vad detta implicerar är att Wiernerprocessen har en oändlig total variation. En snabb sammanfattning av "Total variation" är att givet en funktion så vill vi undersöka hur "slät" den är. Ifall vår totala variation är ändlig så säger det att den är rätt "slät", och vice versa. Ett fraktal är ett exempel på en funktion som har oändlig total variation.

 Bevis:

Notera att ett problem:

$\lim N_{\infty} sup_{x \in A_n} f(x)$ så räcker det att visa att ifall för något $x \in A_n$ att visa att $\lim_{n \rightarrow \infty} f(x) \rightarrow \infty$ ty $\lim_{n \rightarrow \infty} \sup_{x \in A_n} f(x) \geq \lim_{n \rightarrow \infty} f(x)$. Låt oss därför definiera partitionen
$T = (0 = t_0, t_1 = 1/n, t_2 = 2/n, \dots, n/n = 1)$. Då gäller:

$$\lim_{N \rightarrow \infty} \mathbb{E}[\sup_{0 \leq t_0 \leq \dots \leq t_N = 1} \sum_{n=0}^{N-1} |W(t_{n+1}) - W(t_{n})|] \geq \lim_{N \rightarrow \infty} \mathbb{E}[\sum_{n=0}^{N-1} |W(t_{n+1}) - W(t_{n})|]$$ för $t_i \in T$.

$$= \lim_{n \rightarrow \infty} \sum_{n=0}^{N-1} \mathbb{E}[| W(t_{n+1}) - W(t_n) |] = \lim_{n \rightarrow \infty} N \mathbb{E}[| W(t_{n+1}) - W(t_n) |]$$.

Notera att $W(t_{n+1}) - W(t_n) \sim N(0, 1/N)$, och att $1 / \sqrt{N} X \sim N(0, 1/N)$, där $X \sim N(0,1)$. Alltså kan vi skrva om detta som:

$$\lim_{n \rightarrow \infty} N \mathbb{E}[| W(t_{n+1}) - W(t_n) |] = \lim_{n \rightarrow \infty} N \mathbb{E}[|\frac{X}{N}|] = \lim_{n \rightarrow \infty} \sqrt{N} \mathbb{E}[|X|] = \lim_{n \rightarrow \infty} \sqrt{N} \frac{1}{2} \rightarrow \infty$$.

## Visa med Euler framåt att $\int_0^T s dW(s) = TW(t) - \int_0^T W(s)ds.$

Notera att Euler framåt för en funktion $f(t)$ från 0 till T kan skrivas som:

$$I := \int_0^T f(t)dt = \sum_{n=0}^{N-1}f(t_{n})(t_{n+1} - t_n)$$

Och för Euler bakåt:
   
$$I := \int_0^T f(t)dt = \sum_{n=0}^{N-1}f(t_{n+1})(t_{n+1} - t_n)$$

Med detta, låt oss nu hitta $\int_0^T s dW(s)$:

$$\int_0^T s dW(s) = \sum_{n=0}^{N-1} t_n(W(t_{n+1}) - W({t_n})) = \sum_{n=1}^{N-1} t_n(W(t_{n+1}) - W({t_n}))$$

ty $t_0 = 0$.

Vi delar upp integralen och får:

$$\sum_{n=1}^{N-1} t_nW(t_{n+1}) - \sum_{n=1}^{N-1} t_n(W({t_n}))$$

Vi byter indexet från $0$ istället för $1$:


$$\sum_{n=1}^{N-1} t_nW(t_{n+1}) - \sum_{n=0}^{N-2} t_{n+1}(W(t_{n+1}))$$

och utnyttjar återigen att $t_0 = 0$:


$$\sum_{n=0}^{N-1} t_nW(t_{n+1}) - \sum_{n=0}^{N-2} t_{n+1}(W(t_{n+1}))$$

Notera att vi går från $0$ till $N-2$ i den andra termen, och vill att den ska gå från $0$ till $N-1$. Vi gör det, men måste då addera det sista elementet (notera att den andra termen är negativ).

$$\sum_{n=0}^{N-1} t_nW(t_{n+1}) - \sum_{n=0}^{N-1} t_{n+1}(W(t_{n+1})) + T_N W(T_N) = \sum_{n=0}^{N-1} t_nW(t_{n+1}) - \sum_{n=0}^{N-1} t_{n+1}(W(t_{n+1}) - W(t_n)) + T_N W(T_N)$$

Och sen så använder vi att integralen också kan ges av $I = \int_0^T W(s)ds = \sum_{n=0}^{N-1} t_{n+1}(W(t_{n+1}) - W(t_n))$, och får:

$$T_N W(T_n) - \int_0^T W(s)ds$$
