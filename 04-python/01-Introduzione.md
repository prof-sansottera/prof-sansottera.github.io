# Python Base

[Python](https://it.wikipedia.org/wiki/Python) è un linguaggio di
programmazione ad alto livello sviluppato nel 1991 da Guido van Rossum.

Python è stato progettato in modo da risultare facilmente leggibile e
scrivibile. Visivamente si presenta in modo lineare e pulito, con
pochi costrutti sintattici rispetto ad altri linguaggi di
programmazione come il
[C](https://it.wikipedia.org/wiki/C_(linguaggio_di_programmazione)).

Un aspetto peculiare di Python è il metodo che usa per delimitare i
blocchi di programma, che lo rende unico fra i linguaggi più diffusi.
Python, invece di usare parentesi o parole chiave come la stragrande
maggioranza dei linguaggi di programmazione, usa l'indentazione stessa
per indicare i blocchi nidificati, in congiunzione col carattere "due
punti" (:).

Python obbliga a scrivere sorgenti indentati correttamente, aumentando
così la leggibilità del codice.

## Installazione

DA SCRIVERE

Useremo Python 3.

## L'interprete Python

Python può essere usato direttamente da terminale, invocando
l'interprete da riga di comando (le modalità dipendono dal sistema
operativo che stai utilizzando e dal tipo di installazione di Python
che hai a disposizione).

```{warning}
In laboratorio, al momento, il modo più comodo è quello di aprire
l'IDE Thonny e usare la shell integrata.

Cerchiamo di installare qualcosa di meglio appena possibile.


```

L'interprete Python si presenta (più o meno) così
```
Python 3.13.5 (main, Jun 25 2025, 18:55:22) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

Nelle prime due righe Python _si presenta_, dandoti alcune
informazioni utili, ad esempio ti dice che sto usando Python sul mio
pc che ha GNU/Linux come sistema operativo.  I simboli `>>>` indicano
che Python è pronto e aspetta istruzioni!



## Dati Numerici

Anzitutto, puoi usare Python come una calcolatrice
```
>>> 3+4
7
>>> 3-4
-1
>>> 3*4
12
>>> 3/4
0.75
 
```
Nessuna sorpresa fino a qui, Python sa fare le quattro operazioni.

Se ti ricordi, quando hai imparato a fare le divisioni, prima di usare i numeri con la virgola, calcolavi il _quoziente_ e il _resto_. Python sa fare anche questo, ma devi proprio dirgli che vuoi fare le divisioni in quel modo

```
>>> 3//4
0
>>> 3%4
3

```
Gli operatori `//` e `%` servono proprio a calcolare la _divisione
intera_ e il _resto_.


Un'altra operazione che Python sa fare è l'elevamento a potenza
```
>>> 2**3
8
>>> 3**3
27
>>> 4**3
64
```

Se vuoi calcolare espressioni più complicate non hai che da scriverle,
usando se necessario anche le parentesi (*solo parentesi tonde
naturalmente!*)

Ad esempio per calcolare le espressioni
\begin{align*}
\left( 2-\frac{1}{5}\right) -
\frac{\left(4-\frac{2}{9}\right)}{\left(3-\frac{1}{7}\right)}+\left(2\cdot3\right)^{2}\\
\frac{\left( 2-\frac{1}{5}\right) -
\left(4-\frac{2}{9}\right)}{\left(3-\frac{1}{7}\right)}+\left(2\cdot3\right)^{2}
\end{align*}
mi basta scrivere
```
>>> (2-1/5)-(4-2/9)/(3-1/7)+(2*3)**2
36.477777777777774
>>> ((2-1/5)-(4-2/9))/(3-1/7)+(2*3)**2
35.30777777777778

```

Le operazioni vengono calcolate secondo un ordine di precedenza:
- Parentesi `()`: Vengono valutate per prime, partendo da quelle più interne.
- Potenza `**`: Ha la priorità subito dopo le parentesi.
- Moltiplicazione `*`, divisione `/`, divisione intera `//`, modulo `%`: Hanno la stessa priorità, vengono eseguite da sinistra a destra.
- Addizione `+`, sottrazione `-`: Hanno la stessa priorità, vengono eseguite per ultime, da sinistra a destra. 

Senza entrare in troppi dettagli tecnici, sappi che in Python ci sono
due tipi fondamentali di numeri: gli *interi* (`int`) e i *numeri con
la virgola* (`float`).
```
>>> type(3)
<class 'int'>
>>> type(4)
<class 'int'>
>>> type(3/4)
<class 'float'>
```

Il comando `type` ti permette di scoprire, in informatichese, il tipo
di dato che stai utilizzando.

Riassumendo, in Python puoi usare numeri interi, numeri con la
virgola, e fare le operazioni di base che hai imparato a fare alle
scuole medie.  Naturalmente potrai fare molto di più, ma ti chiedo
ancora un po' di pazienza.

## Stringhe

Non si vive di soli numeri, se ci pensi la maggior parte del tempo con
cui interagisci con il tuo smartphone lo passi digitando del testo.

Python, come sostanzialmente ogni altro linguaggio di programmazione,
naturalmente è in grado di gestire i testi (caratteri, parole e
frasi). In Python questo tipo di dati è detto _stringa_ (`str`) e per
dire a Python che voglio trattare una sequenza di caratteri
(carattere, parola o frase) come una stringa devo racchiuderla tra
virgolette singole o doppie (`'` o `"`).

```
>>> 'ape'
'ape'
>>> "ape"
'ape'
>>> 'l'ape'
  File "<python-input-8>", line 1
    'l'ape'
          ^
SyntaxError: unterminated string literal (detected at line 1)
>>> "l'ape"
"l'ape"
>>> 'l\'ape'
"l'ape"
>>> '"l\'ape"'
'"l\'ape"'
>>> type('ape')
<class 'str'>
```

Come si vede dall'esempio qui sopra, se in una stringa devo inserire
delle virgolette, l'interprete Python deve essere in grado di
distinguere quelle che delimitano la stringa e quelle all'interno
della stessa stringa.  Nel caso non sia possibile, posso _proteggere_
le virgolette all'interno della stringa con una slash `\'` o `\"`.

Approfondiremo le stringhe più avanti, lasciami solo anticipare che le
operazioni `+` e `*`, quando coinvolgono delle stringhe, assumono un
significato completamente diverso da quello che hanno con i numeri
visti in precedenza.

```
>>> 'ciao' + 5
Traceback (most recent call last):
  File "<python-input-17>", line 1, in <module>
    'ciao' + 5
    ~~~~~~~^~~
TypeError: can only concatenate str (not "int") to str
>>> 'ciao' + "come va?"
'ciaocome va?'
>>> 'ciao ' + "come va?"
'ciao come va?'
>>> 5*'ciao'
'ciaociaociaociaociao'
>>> 5*'ciao '
'ciao ciao ciao ciao ciao '
>>> 'ciao '*5
'ciao ciao ciao ciao ciao '
```

Nello specifico, l'operatore `+` permette di _concatenare_ due
stringhe, mentre il `*` _replica_ la stringa più volte.
