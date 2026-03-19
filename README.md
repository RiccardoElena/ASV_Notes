# Automated Software Verification - Appunti del Corso

Questo repository contiene appunti e materiali di studio relativi al corso di **Automated Software Verification** tenuto dai Prof. M. Benerecetti e F. Mogavero presso l'Università degli Studi Federico II di Napoli nell'Anno Accademico 2025/2026.

[![Download Latest Notes](https://img.shields.io/badge/Download-Latest_Notes-blue.svg)](https://github.com/RiccardoElena/ASV_Notes/releases/latest/download/Automated_Software_Verification.pdf)

## Contenuti del Corso

Il corso affronta gli aspetti teorici e pratici della verifica automatica del software, con particolare focus su tecniche formali e algoritmi per garantire la correttezza e l'affidabilità dei sistemi software. Gli argomenti trattati includono:

- Modellazione formale di sistemi computazionali
- Logica temporale e logiche per la specifica delle proprietà
- Teoria dei modelli e automi
- Tecniche di model checking
- Strumenti di verifica formale (NuSMV, SPIN)
- Relazione di soddisfacimento e verifica di proprietà

## Disclaimer

**Questi appunti sono destinati a supportare gli studenti nel loro percorso di apprendimento e a fornire una risorsa di riferimento per gli argomenti discussi durante il corso, ma non sostituiscono in alcun modo il materiale ufficiale e le lezioni dei docenti.**

Questo documento è prodotto da studenti, per studenti, e potrebbe contenere errori o imprecisioni. Feedback e correzioni sono ben accetti e incentivati, e possono essere inviati tramite pull request o issue in questa repository.

## Compilazione del Documento

Per compilare questo documento è necessario utilizzare il template LaTeX presente nella repository [https://github.com/RiccardoElena/UniNotes_Template].

Dopo il clone del repository, è necessario inizializzare i submodule per ottenere il template:

```bash
git submodule update --init --recursive
```

### Compilazione

Una volta configurato l'ambiente, compilare il documento principale:

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

Oppure utilizzare `latexmk` per la compilazione automatica:

```bash
latexmk -pdf main.tex
```
## Struttura della Repository

```bash
ASV_Notes/
├── main.tex           # File principale
├── csnotes.cls        # Classe LaTeX (symlink)
├── _files/            # Risorse grafiche
│   ├── _images/          # Immagini utilizzate nel documento
│   │   └── logo.pdf          # symlink
│   └── ...                # Altri file di risorse
├── _chapters/         # Capitoli del documento
│   ├── 0_intro.tex
│   ├── 1_introduction.tex
│   └── ...
└── _build/            # File di build (ignorati da git)
```

## Contribuire

Contributi, correzioni e miglioramenti sono benvenuti. Per contribuire:

1. Fare fork della repository
2. Creare un branch per le modifiche (`git checkout -b feature/miglioramento`)
3. Committare le modifiche (`git commit -am 'Descrizione modifiche'`)
4. Push del branch (`git push origin feature/miglioramento`)
5. Aprire una Pull Request

Per segnalare errori o problemi, aprire una issue dettagliando il problema riscontrato.

## Autori

- [Riccardo Elena](https://github.com/RiccardoElena)
- [Vincenzo Mennillo](https://github.com/ViMen23)

## Licenza

Questo materiale è fornito a scopo didattico ed è rilasciato sotto licenza MIT. Consultare il file [LICENSE](LICENSE) per i dettagli completi.

---

**Nota Bene**: Gli appunti sono in continuo aggiornamento durante lo svolgimento del corso.
