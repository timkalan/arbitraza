# Arbitraža
*ALi lahko s pomočjo cikličnih menjav valut zaslužimo denar?*

*Ali je bolje menjati direktno EUR-GBP ali morda EUR-USD-GBP?*

S pomočjo [FLoyd-Warshallovega algoritma](https://en.wikipedia.org/wiki/Floyd%E2%80%93Warshall_algorithm)
bomo preverili, če se s trenutnimi stanji na trgu valut da menjati tako, da pridemo do arbitraže 
(npr. $1$ EUR menjamo tako, da dobimo nazaj $1,1$ EUR).

Algoritem išče vse možne poti v uteženem grafu. Če slučajno najde negativni cikel, se na diagonali matrike 
dolžin poti (tam so poti od vozlišča do samega sebe) nahaja negativno število. To za nas pomeni arbitražo. 

Natančneje: menjava iz valute v valuto predstavlja množenje med tečaji (npr. menjava $1$ EUR -> YEN -> HUF -> USD
je približno $1 * 131,9 * ...$). Če želimo torej to prevesti v iskanje negativnih ciklov moramo storiti sledeče. Vse 
skupaj logaritmirati, kar prevede množenje v seštevanje. Problem pa je še to, da sedaj iščemo najdaljšo pot v grafu, 
saj želimo največji zaslužek. Tu se rešimo tako, da vse pomonožimo z $-1$, kar iskanje našega maksimuma prevede v 
iskanje minimuma.