# Automated Software Verification - Appunti del Corso

Questo repository contiene appunti e materiali di studio relativi al corso di **Automated Software Verification** tenuto dai Prof. M. Benerecetti e F. Mogavero presso l'Università degli Studi Federico II di Napoli nell'Anno Accademico 2025/2026.

[![Download Latest Notes](https://img.shields.io/badge/Download-Latest_Notes-blue.svg)](https://github.com/RiccardoElena/ASV_Notes/releases/latest/download/Automated_Software_Verification.pdf)
[![All Contributors](https://img.shields.io/github/all-contributors/RiccardoElena/LOGIC_Notes?color=ee8449&style=flat-square)](#contributors-)
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

## Contributors

<div style="width: 70%; margin-right: auto; margin-left: auto;">
<div align="center">
<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/RiccardoElena"><img src="https://avatars.githubusercontent.com/u/23059036?v=4?s=100" width="100px;" alt="Riccardo Elena"/><br /><sub><b>Riccardo Elena</b></sub></a><br /><a href="#content-RiccardoElena" title="Content">🖋</a> <a href="https://github.com/RiccardoElena/ASV_Notes/commits?author=RiccardoElena" title="Documentation">📖</a> <a href="#maintenance-RiccardoElena" title="Maintenance">🚧</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/ViMen23"><img src="https://avatars.githubusercontent.com/u/145158818?v=4?s=100" width="100px;" alt="ViMen23"/><br /><sub><b>ViMen23</b></sub></a><br /><a href="#content-ViMen23" title="Content">🖋</a> <a href="#maintenance-ViMen23" title="Maintenance">🚧</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
</div>
</div>

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification.
Contributions of any kind welcome!

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

### Convenzioni messaggi di commit

Per mantenere una cronologia chiara e leggibile dei commit e delle modifiche, si rimanda alla convenzione dei commit di tipo [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/), che prevede l'uso di prefissi standardizzati per indicare la natura delle modifiche. Tali convenzioni sono sviluppate nel contesto dello sviluppo software, ma possono essere adattate efficacemente anche per la gestione di documenti e materiali didattici come segue:

- `feat`: Aggiunta di nuovi contenuti o sezioni al documento.
- `fix`: Correzione di errori o imprecisioni nei contenuti esistenti.
- `docs`: Modifiche alla documentazione, come questo README, senza alterare i contenuti principali.
- `style`: Modifiche di formattazione, layout o stile del documento senza alterare il contenuto.
- `refactor`: Ristrutturazione del documento senza aggiungere o rimuovere contenuti, ad esempio riorganizzazione dei capitoli o miglioramento della chiarezza.
- `test`: Aggiunta o modifica di esempi, esercizi o casi di studio all'interno del documento.
- `chore`: Modifiche di manutenzione, come aggiornamenti di dipendenze o configurazioni di build, senza alterare i contenuti del documento.
- `ci`: Modifiche relative alla configurazione del Continuous Integration (CI) per la compilazione automatica del documento.

## Licenza

Questo materiale è fornito a scopo didattico ed è rilasciato sotto licenza MIT. Consultare il file [LICENSE](LICENSE) per i dettagli completi.

---

**Nota Bene**: Gli appunti sono in continuo aggiornamento durante lo svolgimento del corso.
