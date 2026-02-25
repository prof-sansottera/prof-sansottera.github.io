# Tipi di dati

Come abbiamo già visto in precedenza, in Python hai a disposizione
dati di tipo numerico (ad esempio `int` per i numeri interi, `float`
per numeri con la virgola) per rappresentare numeri e stringhe (`str`)
per rappresentare caratteri, parole ed intere frasi.

:::{warning}
12 e "12" sono due dati completamente diversi! Il primo è un numero,
con cui puoi fare operazioni numeriche, il secondo è un stringa
composta da due caratteri ("1" e "2").
:::

## List, Tuple, Set

Come puoi facilmente immaginare, usare un nome diverso per ogni
variabile non è sempre la scelta migliore. A volte potrebbe essere
utile raggruppare diversi dati. In Python ci sono diversi modi per
raggruppare una *collezione* di dati: le liste (`list`), le tuple
(`tuple`) e gli insiemi (`set`).

### List

Una lista è una successione ordinata di elementi, ordinati in base ad
un _indice_ che indica la posizione dell'elemento all'interno della
lista.

Abbiamo detto che una variabile è come una scatola con un'etichetta,
il valore della variabile è il contenuto della scatola, il nome della
variabile è l'etichetta sulla scatola.  In maniera del tutto simile,
puoi pensare alla lista come ad una cassettiera con dei cassetti
numerati con un numero in ordine progressivo (a partire da $0$): il nome della
cassettiera è il nome della lista, il numero sul cassetto indica quale
cassetto vuoi aprire, il contenuto del cassetto è il valore
dell'elemento della lista.

In Python, puoi creare una lista in diversi modi: elencando gli
elementi della lista, separati da una virgola e racchiusi tra
parentesi quadre; utilizzando l'operatore `*` per ripetere più volte
lo stesso elemento; utilizzando la funzione `list()` (su questo ci
torneremo più avanti!).

```{code} python
>>> x=[42, 3.14, "pirata"]
>>> type(x)
<class 'list'>
>>> print(x)
[42, 3.14, 'pirata']
>>> x*2
[42, 3.14, 'pirata', 42, 3.14, 'pirata']
>>> y=[0]
>>> z=y*10
>>> z
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```

Gli elementi di una lista, come abbiamo già detto, sono
ordinati. Possiamo dunque accedere agli elementi di una lista,
sfruttando la loro posizione. In Python il primo elemento ha indice
`0` e possiamo usare anche indici negativi, con la convenzione che
`-1` indica l'utimo elemento, `-2` il penutilmo, etc. Per accere a più
elementi consecutivi, è utile l'operatore di _slicing_ `:`, vediamo come.


```{code} python
>>> x=[42, 3.14, "pirata"]
>>> x[0]
42
>>> x[1]
3.14
>>> x[2]
'pirata'
>>> x[3]
Traceback (most recent call last):
  File "<python-input-5>", line 1, in <module>
    x[3]
    ~^^^
IndexError: list index out of range
>>> x[-1]
'pirata'
>>> x[-2]
3.14
>>> x[-3]
42
>>> x[-4]
Traceback (most recent call last):
  File "<python-input-9>", line 1, in <module>
    x[-4]
    ~^^^^
>>> y=[1,2,3,4,5,6,7,8,9,10]
>>> y
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> y[:]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> y[1:]
[2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> y[2:]
[3, 4, 5, 6, 7, 8, 9, 10]
>>> y[:5]
[1, 2, 3, 4, 5]
>>> y[:4]
[1, 2, 3, 4]
>>> y[2:6]
[3, 4, 5, 6]
```

Come potrai facilmente intuire, sarebbe utile poter aggiungere e
rimuovere elementi ad una lista e naturalmente in Python esistono dei
metodi predefiniti per farlo: `insert()` inserisce un nuovo elemento
in una posizione specifica, `append()` aggiunde un elemento alla fine
della lista, `extend()` aggiunge più elementi, presi da un'altra
lista, alla fine della lista, `index` restituisce la posizione della
prima occorrenza di un elemento all'interno della lista, `remove()`
rimuove la prima occorrenza di un elemento dalla lista, `pop()`
rimuove un elemento in una posizione specifica o l'ultimo elemento se
non diversamente indicato, `del` rimuove un elmento in una posizione
specifica, `clear()` rimuove tutti gli elementi di una lista.

```{code} python
>>> y=["pirata", 3.14, 100, "pirata", 100, 3.14]
>>> y
['pirata', 3.14, 100, 'pirata', 100, 3.14]
>>> y.insert(0, "nuovo elemento")
>>> y
['nuovo elemento', 'pirata', 3.14, 100, 'pirata', 100, 3.14]
>>> y.append(123)
>>> y
['nuovo elemento', 'pirata', 3.14, 100, 'pirata', 100, 3.14, 123]
>>> y.extend(["penultimo", "ultimo"])
>>> y
['nuovo elemento', 'pirata', 3.14, 100, 'pirata', 100, 3.14, 123, 'penultimo', 'ultimo']
>>> y.index('pirata')
1
>>> y.index('pippo')
Traceback (most recent call last):
  File "<python-input-27>", line 1, in <module>
    y.index('pippo')
    ~~~~~~~^^^^^^^^^
ValueError: list.index(x): x not in list
>>> y.remove('pirata')
>>> y
['nuovo elemento', 3.14, 100, 'pirata', 100, 3.14, 123, 'penultimo', 'ultimo']
>>> y.remove(1)
Traceback (most recent call last):
  File "<python-input-28>", line 1, in <module>
    y.remove(1)
    ~~~~~~~~^^^
ValueError: list.remove(x): x not in list
>>> y.pop()
'ultimo'
>>> y.pop()
'penultimo'
>>> y.pop(0)
'nuovo elemento'
>>> y.clear()
>>> y
[]
```

Modificando la lista, come avrai certamente notato, possiamo cambiare
il numero di elementi contenuti nella lista. Per sapere il numero di
elmenti contenuti nella lista, ovvero la lunghezza della lsta, puoi
usare il comando `len()`
```{code} python
>>> len([1,2,3])
3
```

### Tuple

Una tupla è una successione ordinata di elementi, ordinati in base ad
un _indice_ che indica la posizione dell'elemento all'interno della
tupla. A differenza della lista però, una tupla è _immutabile_, ovvero
una volta definita non può essere modificata.

Se ti stai chiedendo perchè mai dovrei creare una lista che non è più
possibile modificare, pensa ad esempio a questioni di sicurezza, la
lista delle transazioni bancarie di un account sarebbe meglio non
fosse modificabile erroneamente, una tupla ti garantisce di poter
leggere una lista senza il rischio di modificarne il contenuto.

In Python, puoi creare una tupla in diversi modi: elencando gli
elementi della lista, separati da una virgola e racchiusi tra
parentesi tonde; utilizzando l'operatore `*` per ripetere più volte
lo stesso elemento; utilizzando la funzione `tuple()` (su questo ci
torneremo più avanti!).

```{code} python
>>> (1,"ciao",2)
(1, 'ciao', 2)
>>> type((1,"ciao",2))
<class 'tuple'>
```

Gli elementi di una tupla, come quelli di una lista, sono
ordinati. Possiamo dunque accedere agli elementi di una lista,
sfruttando la loro posizione. In Python il primo elemento ha indice
`0` e possiamo usare anche indici negativi, con la convenzione che
`-1` indica l'utimo elemento, `-2` il penutilmo, etc. Per accere a più
elementi consecutivi, è utile l'operatore di _slicing_ `:`.

Ovviamente, essendo una lista immutabile, non potrai aggiungere o
rimuovere elementi da una tupla, ma solo sapere quanto è lunga con
`len()`.

### Set

Un `set` è un insieme, ovvero una collezione di elementi.  A
differenza delle liste e delle tuple, gli elementi _non_ sono ordinati
e, come negli insiemi matematici, ogni elmento può comparire una sola
volta in un insieme.

In Python, puoi creare un set in diversi modi: elencando gli
elementi del set, separati da una virgola e racchiusi tra
parentesi graffe; utilizzando la funzione `set()` (su questo ci
torneremo più avanti!).

```{code} python
>>> {1,2,3}
{1, 2, 3}
>>> type({1,2,3})
<class 'set'>
>>> {1,2,3,3,3,3}
{1, 2, 3}
>>> {3,2,1,4,3,2,1}
{1, 2, 3, 4}
```

Come potrai facilmente intuire, sarebbe utile poter aggiungere e
rimuovere elementi ad un insieme e naturalmente in Python esistono dei
metodi predefiniti per farlo: `add()` inserisce un nuovo elemento,
`remove()/discard()` rimuove un elemento (se proviamo ad eliminare un
elemento che non fa parte dell'insieme, `discard()` da errore!),
`clear()` rimuove tutti gli elementi dall'insieme.

```{code} python
>>> a={1,2,3,4}
>>> a
{1, 2, 3, 4}
>>> a.add(5)
>>> a
{1, 2, 3, 4, 5}
>>> a.add(4)
>>> a
{1, 2, 3, 4, 5}
>>> a.remove(2)
>>> a
{1, 3, 4, 5}
>>> a.remove(7)
Traceback (most recent call last):
  File "<python-input-19>", line 1, in <module>
    a.remove(7)
    ~~~~~~~~^^^
KeyError: 7
>>> a.discard(3)
>>> a
{1, 4, 5}
>>> a.discard(7)
>>> a
{1, 4, 5}
>>> a.clear()
>>> a
set()
```

## Dict

Un dizionario è una collezione di elementi, costituiti da una coppia
_chiave-valore_ (`key:value`) ordinata (da Python 3.7 in poi, prima
non era ordinata!), modificabile e che non ammette chiavi duplicate.

In Python, puoi creare un dizionario in diversi modi: elencando gli
elementi del dizionario, separando chiave-valore con i due punti
(`:`), separati da una virgola e racchiusi tra parentesi graffe;
utilizzando la funzione `dict()` (su questo ci torneremo più
avanti!).

Per sapere le _chiavi_ di un dizionario possiamo usare il metodo
`keys()`, per ottenere i _valori_ del dizionario invece possiamo usare
il metodo `values()`.

```{code} python
>>> libro = {"autore": "Orwell", "titolo": "1984", "anno": 1949}
>>> libro
{'autore': 'Orwell', 'titolo': '1984', 'anno': 1949}
>>> libro["autore"]
'Orwell'
>>> libro["titolo"]
'1984'
>>> libro["anno"]
1949
>>> libro.keys()
dict_keys(['autore', 'titolo', 'anno'])
>>> libro.values()
dict_values(['Orwell', '1984', 1949])
```
