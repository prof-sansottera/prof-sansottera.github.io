# Variabili

Consideriamo un quadrato di lato 1, come ben sai l'area del quadrato
vale 1.  Se invece il lato vale 2, l'area vale 4. In generale, dato un
quadrato di lato $l$, l'area vale $A=l^2$.  L'area $A$ è quindi un
_monomio_ nella variabile $l$, che può assumere un qualsiasi valore
reale _positivo_.

In informatica, puoi pensare ad una _variable_ come ad una
"scatola". Il _nome della variable_ è un pò come un'etichetta che
identifica la scatola, il _valore della variabile_ invece rappresenta
il contenuto della scatola.

![variabili](./variabili.png)

```{code} python
>>> x=10
>>> y=3
>>> x+y
13
>>> z=x+y
>>> z
13 
>>> x*y
30
>>> x="ciao"
>>> x+y
Traceback (most recent call last):
  File "<python-input-32>", line 1, in <module>
    x+y
    ~^~
TypeError: can only concatenate str (not "int") to str
>>> x*y
'ciaociaociao'
```

Una variabile viene creata (_inizializzata_) la prima volta che le
viene assegnato un valore, con l'operatore `=`.

:::{warning} Attenzione
Non confondere l'operatore di _assegnazione_ `=` con l'uguaglianza matematica.

Ad esempio, `x=x+1` ha perfettamente senso se pensata come assegnazione (assegna ad `x` il valore corrente di `x`, aumentato di 1), ma è un'espressione impossibile dal punto di vista matematico.
:::

Per quanto riguarde i nomi delle variabili, hai abbastanza libertà
nella scelta, con poche limitazioni:
- non puoi usare spazi;
- puoi usare solamente lettere, numeri e il carattere di underscore `_`;
- non puoi iniziare con un numero;
- non puoi usare _nomi riservati_ da Python quali `if`, `for`, `return` e altri che imparearai strada facendo.

Ricorda che maiuscole e minuscole sono a tutti gli effetti lettere
diverse, quindi `base` e `Base` sono due nomi di due variabili
distinte.

:::{warning} Da grandi poteri, derivano grandi responsabilità

Avere libertà di scelta nel nome delle variabili, non significa che
scelgliere nomi a caso per le variabili sia una buona idea!

Ecco alcune semplici regole che è bene tenere a mente:
- usare nomi di variabili che _descrivono_ cosa rappresentano rende il codice autoesplicativo (`A=b*h` vs. `area=base*altezza`)
- usa sempre nomi in minuscolo, e separa le parole con un underscore `_` (`Arett` vs. `area_rettangolo`)
:::
