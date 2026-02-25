# Controlli condizionali

Sino ad ora abbiamo fatto eseguire alcune semplici istruzioni al
nostro programma.  Vediamo ora come far prendere semplici
**decisioni** al programma.

Supponiamo di conoscere l'età di una persona (memorizzata in una
variabile `anni`) e di voler stampare a schermo se è **maggiorenne** o
**minorenne**.

Per farlo dobbiamo:

1. confrontare due dati (in questo caso numeri)
2. usare il risultato del confronto per prendere una decisione


## Operatori di confronto

Gli **operatori di confronto** servono per confrontare due valori.
Il risultato di un confronto è sempre un valore booleano:
- `True` (vero)
- `False` (falso)

### Elenco degli operatori

| Operatore | Significato       | Esempio      | Risultato                       |
| --------- | ----------------- | ------------ | ------------------------------- |
| `==`      | uguale a          | `anni == 18` | True se `anni` vale 18          |
| `!=`      | diverso da        | `anni != 18` | True se `anni` non vale 18      |
| `>`       | maggiore di       | `anni > 18`  | True se `anni` è maggiore di 18 |
| `<`       | minore di         | `anni < 18`  | True se `anni` è minore di 18   |
| `>=`      | maggiore o uguale | `anni >= 18` | True se `anni` è almeno 18      |
| `<=`      | minore o uguale   | `anni <= 18` | True se `anni` è al massimo 18  |

```{warning} Attenzione
* `=` serve per **assegnare** un valore a una variabile
* `==` serve per **confrontare** due valori
```


### Esempi di confronto

```python
>>> anni = 20
>>> anni >= 18
True
>>> anni < 18
False
>>> anni == 20
True
>>> anni != 15
True
```

Ogni espressione produce un valore booleano (`True` o `False`).

## Istruzione `if`

Per far prendere una decisione al programma utilizziamo l'istruzione `if`.

### Sintassi e funzionamento

```python
if condizione:
    istruzioni
```

```{warning}
- Se la `condizione` è **vera**, le istruzioni vengono eseguite.
- Se è **falsa**, le istruzioni vengono ignorate.
- Le istruzioni ***devono*** essere indentate con lo stesso numero di spazi (tipicamente quattro spazi).
```

## Istruzione `if`-`else`

Per gestire due possibili casi (vero/falso) utilizziamo la coppia di istruzioni `if`-`else`.

### Esempio: maggiorenne o minorenne

```python
anni = 16

if anni >= 18:
    print("Sei maggiorenne")
else:
    print("Sei minorenne")
```

### Sintassi e funzionamento

```python
if condizione:
    istruzioni
else:
    istruzioni
```

1. Il programma valuta la condizione `anni >= 18`
2. Se è vera, esegue il blocco `if`
3. Altrimenti esegue il blocco `else`

## Istruzione `if`-`elif`-`else`

Per gestire più casi possibili (opzione 1, opzione 2, ...) utilizziamo le istruzioni `if`-`elif`-`else`.

### Esempio: maggiore di 18, 18 o minorenne di 18

```python
anni = 16

if anni > 18:
    print("Hai più di 18 anni")
elif anni == 18:
    print("Hai 18 anni")
else:
    print("Hai meno di 18 anni")
```

### Funzionamento

1. Il programma valuta la condizione `anni > 18`; se è vera, esegue il blocco `if`
2. Altrimenti, valuta se la condizione `anni == 18`; se è vera, esegue il blocco `elif`
3. Altrimenti, se tutte le precedenti condizioni non sono vere, esegue il blocco `else`
