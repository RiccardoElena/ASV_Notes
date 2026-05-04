08 Aprile

# Richiami
$L(\psi) = \{ w \in 2^{AP} \mid w \models \psi \}$
$L(K) = \{ label_{AP}(\pi) \mid \pi \in Path(K) \}$
> $\pi$ è un percorso del grafo, lo trasformiamo in una parola di cui ogni lettera corrisponde all' insieme delle cose che sono vere in quello stato.

$L(\psi)$ e $L(K)$ sono entrambi $\subseteq (2^{AP})^\omega$

# Problemi di Model Checking (MC)

>[!definition] Problema di Model Checking
>Ci domandiamo se è vero che $L(K) \subseteq L(\psi)$, cioè se tutto ciò che il modello $K$ soddisfa è tra le parole (esecuzioni) che soddisfano $\psi$

Concretamente andiamo a rispondere alla domanda opposta: $L(k) \cap L(\lnot \psi) \neq \emptyset$

> Negare il linguaggio (negare $L(\psi)$) è molto più complesso che negare "sulla logica" (cioè derivare $L(\lnot \psi)$), nonostante siano la stessa cosa.


## Richiamo Soddisfacibilità e Validità

**Soddisfacibilità** - mi chiedo se $L(\psi) \neq \emptyset$ (esiste almeno una parola che soddisfa la formula?)
**Validità** - $L(\psi) = (2^{AP})^\omega$ (se tutti i modelli soddisfano $\psi$)

## Model Checking
Sto lavorando su insiemi infiniti, mi serve una rappresentazione finita su cui posso lavorare
Come per le espressioni regolari che si traducono in automi a stati finiti (e viceversa), noi faremo una cosa simile con automi più espressivi.


### Esempio "come gli automi ci possono aiutare"
$AP = \{p_1, p_2, p_3\}$
$\psi = F p_1 \land F p_2 \land G \lnot p_3$

Vogliamo prendere un solo percorso e controllare se soddisfa $\psi$, lo diamo in pasto ad un automa.
Per semantica del $\land$, $L(\psi) = L(F p_1) \cap L(F p_2) \cap L(G \lnot p_3)$, quindi posso iniziare facendo tre automi indipendenti.

Siccome la cardinalità di $AP$ è $3$, allora ho $8$ possibili stati.

Usiamo $\sigma \in \Sigma$ per denotare uno stato (un "carattere") del percorso.
Usiamo $p_1 \not \in \sigma$ per denotare che non è vero $p_1$ nel carattere $\sigma$ corrente.
Per i primi due resto nel primo stato fin quando non si verifica $p_1$, poi passo in quello di accettazione e non mi muovo più.
>Sono condizioni di tipo $F$ (cioè "eventually"), cioè sto aspettando che qualcosa si avveri: una volta che la osservo non importa ciò che viene dopo.
![[IMG_20260408_170032.jpg|282]]

Per la terza proprietà, devo fare la stessa cosa ma invertendo accettazione e rifiuto, cioè resto in accettazione finché non trovo $p_3$.
![[IMG_20260408_170242.png|347]]


Per essere precisi dovremmo specificare uno stato pozzo di rifiuto (indicato nella foto con il riempimento a righe) oppure eliminare una run (cancellare la parte che nella foto è indicata con le parentesi quadre): ricordando che accettiamo "se esiste un percorso che ... " e quindi possiamo eliminare il percorso (come facevamo con gli NFA a EDIT).
![[IMG_20260408_171312.png|336]]

Infine, per mettere insieme le tre proprietà, faccio il prodotto cartesiano degli stati (gli stati accettanti sono quelli in cui sono tutti accettanti) e delle transizioni.
Il cartesiano ha tutti gli stati per esplicito, ma possiamo fare una versione più compatta.
La foto non presenta l'automa completo, ma si capisce l'idea.
![[IMG_20260408_171320.png|407]]

### Altro esempio (con next)

![[IMG_20260408_171629.png|584]]
Rimaniamo sullo stato $s_0$ fin quando non abbiamo $p_1$. Poi ci aspettiamo $p_2$ dopo aver visto $p_1$, quindi restiamo in $s_1$ fin quando non abbiamo $p_2$. Restiamo in $s_2$ perché ormai la proprietà è soddisfatta.

## Limite espressivo
Tutto ciò funziona solo se non ho $G$ e $F$ una dentro l'altra.
Con $GFp$ pretendiamo di verificare che $p$ sia vero infinite volte, questo richiede più espressività.


### Richiamo definizione automa
$A = < \Sigma, Q, \delta, q_0 \in Q, F \subseteq Q>$

$\Sigma$ - alfabeto finito di input
$Q$ - insieme finito di stati
$\delta$ - funzione di transizione
$q_0$ - stato iniziale
$F$ - stati finali

>[!tip] Tipi di nondeterminismo
 Gli automi non deterministici classici, detti **esistenziali**, accettano se esiste almeno una run buona.
 Gli automi **universali** pretendono che tutte le run siano accettanti.
 Gli automi **alternanti** permettono entrambe le modalità. Ne esistono vari tipi e sono in generale più complessi, con tempi di simulazione più alti.
 Tutti e tre hanno la stessa struttura, cambia solo la semantica.

Per gli automi deterministici, definiamo la funzione di transizione $\delta : Q \times \Sigma \to Q$
Per gli automi nondeterministici/universali/alternanti, invece, $\delta : Q \times \Sigma \to 2^Q$


### Richiamo proprietà di chiusura booleana
Usiamo $\uplus$ e per differenziare unione tra automi, il prof usa un simbolo simile per intersezione che non so rifare in Latex, quindi uso $\cap^+$.

- Unione: $L(A_1 \uplus A_2) = L(A_1) \cup L(A_2)$
- Intersezione: $L(A_1 \cap^+ A_2) = L(A_1) \cap L(A_2)$
- Complemento: $L(\overline{A}) = \overline{L(A)}$

#### Costruzione di $A_1 \uplus A_2$
Siano $A_1$ e $A_2$ due automi deterministici a stati finiti, assumiamo $Q_1 \cap Q_2 = \emptyset$ e $q_0 \not \in Q_1 \cup Q_2$.
Trascuriamo il caso limite della parola vuota come l'abbiamo trattato a EDIT perché siamo su parole infinite.
Costruiamo l'automa non-deterministico:
$A_1 \uplus A_2 = <\Sigma, Q_1 \cup Q_2 \cup \{q_0\}, \delta, q_0, F_1 \cup F_2>$
$\delta : \delta_1 \cup \delta_2 \cup \{(q_0, \sigma)\} \to \{\delta_1(q_0^1, \sigma), \delta_2(q_0^2, \sigma)\}$

$A_1 \cap^+ A_2 = <\Sigma, Q_1 \times Q_2, \delta, (q_0^1, q_0^2), F_1 \times F_2>$
con $\delta ((q_1,q_2), \sigma) = (\delta_1(q_1, \sigma), \delta_2(q_2, \sigma))$

Ad ogni automa non-deterministico a stati finiti corrisponde un automa deterministico a stati finiti ottenibile tramite subset construction.
La versione "direttamente deterministica" dell'unione sarebbe simile alla intersezione ma con stati finali che sono $F_1 \times Q_2 \cup Q_1 \times F_2$.


#### Costruzione del complemento di un automa deterministico
Per il complemento di un automa deterministico, invece:
$\overline{A} = <\Sigma, Q, \delta, q_0, Q \ F >$
Il motivo per cui costruiamo un automa deterministico è per poter trasformare facilmente un "esiste" in un "perogni", cosa che con i non-deterministici non si può fare se non passando da un automa esistenziale a uno universale.

#### Subset Construction

$D = <\Sigma, 2^Q, \hat{\delta}, \{q_0\}, \{Q' \subseteq Q | Q' \cap F \neq \emptyset \}>$

Sufficiente $2^Q$ per "piccionaia sui processi": è inutile simulare due volte due processi nello stesso stato perché sono indistinguibili.
$\hat{\delta}(Q', \sigma) = \bigcup \{\delta(q', \sigma) | q' \in Q'\} = \bigcup_{q' \in Q'} \delta(q', \sigma)$


## Automa di Buchi
$A$ non cambia
$A = <\Sigma, Q, \delta, q_0 \in Q, F \subseteq Q>$
Il $\delta$ è quello degli automi non-deterministici.
**Cambia la semantica**: si accetta se si passa infinitamente spesso per $F$.

>[!definition] Run
>Chiamiamo run una $r \in Q^\omega$ tale che $r_0 = q_0$, (oppure $r_0 \in Q_0$ se abbiamo un insieme di stati iniziali invece che uno solo), $r_{i+1} \in \delta(r_i, w_i)$.

$r = Run(A, w)$
$r \in Run(A, w)$ se non deterministico

Un run è accettante se passa infinitamente spesso per $F$.

$inf(r) = \{ q \in Q | q \text{ occorre un numero infinito di volte in }r\} = \{q \in Q | |\{i \in \mathcal{N} | r_i = q\}| = \infty\}$
$inf(r)$ non è mai vuoto

Dico che $r$ è accettante se $inf(r) \cap F \neq \emptyset$.
Banale condizione duale "co-Buchi": $inf(r) \cap F = \emptyset$

### Proprietà di chiusura per gli automi di Buchi (dualizzabili per co-Buchi)
Per l'unione è facile perché:
$L(A_1 \uplus A_2) = L(A_1) \cup L(A_2)$
Per l'intersezione è più complicato perché nulla vieta all'intersezione di fare "avanti e indietro" tra accettare $F_1$ e $F_2$ infinitamente spesso ma mai insieme.

![[IMG_20260408_182026.png|524]]

Il risultato della sincronizzazione di questi due automi è:

![[IMG_20260408_182427.png|325]]

L'idea è creare un automa copia del risultato della sincronizzazione di A_1 e A_2 che attende lo stato buono per A_1 e poi verificare A_2, alternando.

![[IMG_20260408_182522.png|540]]

