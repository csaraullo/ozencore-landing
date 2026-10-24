# Daje de Fionda: dove siamo

Gioco alla Angry Birds ambientato a Roma, in 2D. I romani tirati con la fionda contro i gabbiani che hanno rubato la spesa alla nonna.

## Stato
- `fionda/index.html`: prototipo giocabile (grafica semplice disegnata via codice, canvas 2D + fisica Planck.js in `fionda/lib/`).
  - Fionda con traiettoria, materiali legno, vetro, travertino, metallo, cassonetto che esplode.
  - Ciclista (tocco in volo: scatto), nonna (tocco in volo: bustata).
  - Gabbiani normali e grassi da eliminare, corvo ladro col supplì d'oro (scappa in volo, se non lo prendi niente terzo supplì), pappagalli verdi velocissimi, buche che inghiottono tutto.
  - 3 livelli a Trastevere, valutazione da 1 a 3 supplì, record in localStorage.
- `fionda/assets/personaggi.webp`: foglio personaggi approvato (ciclista, nonna, gabbiano, corvo, pappagallo). Stile di riferimento per tutta la grafica.
- `fionda/assets/sprites/*.webp`: i 5 personaggi ritagliati dal foglio (sfondo trasparente, ombre a terra tolte, 320 px, tutti girati a destra). Nel gioco li usa la tabella `SPRITES`: `cx`, `cy`, `r` dicono dove sta il corpo tondo nell'immagine, così combacia col cerchio della fisica. Il gabbiano grasso è lo stesso sprite più grande; i nemici colpiti a metà mostrano due cerotti in testa.
- `fionda/assets/sfondi/`: sfondo di Trastevere a due strati, generati con FLUX su cielo magenta e resi trasparenti; ognuno è tagliato dove i bordi combaciano, così si ripete senza giunture.
  - `trastevere-case.webp`: fila di case, strato vicino (tagliata tra due grondaie).
  - `trastevere-fondale.webp`: cupola di San Pietro, campanile di Santa Maria in Trastevere, pini e cipressi, strato lontano. Scelta la versione più chiara e sfumata tra due prove.
  - Nel gioco: lista `STRIPS`, per ogni strato `strip(file, altezza, profondità, velo)`. La profondità è quanto scorre con la telecamera, il velo è una foschia chiara opzionale. Oggi è a 0 su entrambi: Cristian vuole le case a colori pieni (col velo sembrava tutto sbiadito); il fondale è già chiaro di suo. La leggibilità del fortino va ottenuta con la grafica dei materiali, non schiarendo lo sfondo. Il cielo azzurro e il sole restano disegnati via codice.
- `fionda/assets/oggetti/`: materiali e oggetti ritagliati da due fogli FLUX su magenta.
  - Materiali: per legno, vetro, travertino, metallo una trave lunga (`*-trave`) e un blocco quadrato (`*-blocco`). I pezzi lunghi (almeno 2,5 volte più lunghi che larghi) usano la trave, girata in verticale per i pali; gli altri il blocco. La funzione `slice` tiene i bordi in proporzione e prende il centro dell'immagine (o lo allunga se non basta), così chiodi e bordi non si deformano. Il vetro è disegnato un po' trasparente; le crepe restano via codice.
  - `strada`: selciato con terra sotto, ripetibile. `buca`: pezzo di buca con i lati sfumati nel selciato, disegnato davanti ai corpi (chi ci cade sparisce nella terra) con una parete scura dietro. `cono`, `cassonetto` (con l'adesivo della fiamma via codice), `fionda` (gli elastici e la sacca restano via codice; la sacca sta dietro al personaggio).
  - Le misure dentro le immagini (dove sta il buco, dove si legano gli elastici) sono nelle costanti `STRADA`, `BUCA`, `FIONDA`.
- Lezione imparata: un'immagine "scena completa" in prospettiva non serve come sfondo. Servono strati separati, visti di fronte, senza personaggi né oggetti, ripetibili in orizzontale.
- `daje/index.html`: il primo esperimento, infinite runner 3D (three.js in `daje/lib/`). Da tenere come possibile minigioco bonus.
- Il ramo `daje-de-fionda` contiene entrambi. Non è ancora su `main`: il sito pubblico non è cambiato.

## Prossimi step (uno alla volta)
1. ~~Ritagliare i personaggi dal foglio (sfondo trasparente) e usarli come sprite al posto dei disegni via codice.~~ Fatto.
2. ~~Sfondo di Trastevere: case e fondale lontano.~~ Fatto.
3. ~~Grafica dei materiali (legno, vetro, travertino, metallo, cassonetto), selciato, buca e fionda.~~ Fatto. Gli sfondi per gli altri rioni arriveranno con i nuovi mondi (step 5).
4. Poteri degli altri personaggi (maranza che si divide in 3, tassista col clacson, turista col selfie stick), suoni e voci in romanesco.
5. Altri mondi: Fontana di Trevi, Pantheon, Piazza Venezia, Colosseo con il Re Gabbiano.
6. Pubblicazione su ozencore: unire il ramo a `main`.

## Prova in locale
Serve un server HTTP: `python3 -m http.server` dalla radice del repo, poi apri `http://localhost:8000/fionda/`.
