# dida: materiali pubblici di Istituzioni di Matematica (a.a. 2026/27)

Repository **pubblico** del corso del prof. Francesco Della Pietra (CdL in Scienze per la Natura e per
l'Ambiente). Contiene solo materiale da pubblicare: il volume delle schede di esercizi e la mappa del corso.
Tutto il resto (appunti, regie, registro, programma, prove) sta nel repository privato `corso-scienze-natura-`,
dove c'è il `CLAUDE.md` completo con le convenzioni del corso: valgono anche qui.

## Regole

- **Il docente pubblica i link ai due PDF** (`esercizi.pdf` e `mappa-del-corso.pdf`, ramo `main`).
  Quindi i due PDF **si committano sempre**, rigenerati, a ogni modifica dei sorgenti, con gli stessi nomi e
  nella radice del repository: se cambiano nome o posizione, i link pubblicati smettono di funzionare.
- **Niente materiale riservato**: niente dati degli studenti, voti, scansioni, regie, note per il docente,
  testi o soluzioni delle prove prima che siano svolte. Il repository è pubblico, e lo sono anche i sorgenti
  (le soluzioni delle schede, dentro `\risp{...}`, si leggono nel `.tex`).
- Prima di toccare un file si esegue `git pull`: il docente modifica spesso i file a mano.
- Ogni lavoro va su `main` (è lì che puntano i link) e anche sul branch di lavoro della sessione.
  Messaggi di commit in italiano.
- Si compila fuori dal repository (`-output-directory`), poi si copia nel repository solo il PDF.
  Errori e overfull si contano sul log; il PDF si controlla visivamente.

## File

| File | Contenuto |
|---|---|
| `esercizi.tex` | Volume delle schede: include `schedaNN.tex` (una ogni 3 lezioni) e, in fondo, `scheda-recupero-N.tex`. `\soluzionitrue` stampa le soluzioni in fondo a ogni scheda. |
| `schedaNN.tex` | Una scheda: `\begin{esercizio}[\liv{k}]`, `\risp{...}`, `\stampasoluzioni` a fine scheda. |
| `scheda-recupero-N.tex` | Schede di recupero (R1, ...), sempre dopo le schede settimanali; ridefiniscono `\thechapter` e `\thesection`. |
| `mappa-del-corso.tex` | Mappa del corso, orizzontale; dalla pagina 3 con `flowfram`. Si aggiorna dopo ogni lezione: istruzioni in testa al file (`\fatte`, `bloccop` → `blocco`, `\prog` → `\fatta`). |
| `esercizi.pdf`, `mappa-del-corso.pdf` | I PDF pubblicati: rigenerati e committati a ogni modifica. |

## Compilazione

```bash
mkdir -p /tmp/build && pdflatex -interaction=nonstopmode -output-directory=/tmp/build esercizi.tex   # tre volte (indice)
```

Pacchetti necessari: vedi il `CLAUDE.md` di `corso-scienze-natura-` (fra gli altri `texlive-science` per
`yhmath`, `texlive-pictures`, `texlive-fonts-extra`, `cm-super`, e `flowfram` per la mappa).
