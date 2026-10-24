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
- `fionda/assets/sfondi/trastevere-case.webp`: fila di case di Trastevere approvata (generata con FLUX su cielo magenta, poi resa trasparente). È tagliata tra due grondaie, così si ripete senza giunture. Nel gioco è lo strato vicino dello sfondo (oggetto `CASE`: `h` = altezza, `haze` = velo chiaro che la allontana e fa risaltare fortino e personaggi).
- Lezione imparata: un'immagine "scena completa" in prospettiva non serve come sfondo. Servono strati separati, visti di fronte, senza personaggi né oggetti, ripetibili in orizzontale.
- `daje/index.html`: il primo esperimento, infinite runner 3D (three.js in `daje/lib/`). Da tenere come possibile minigioco bonus.
- Il ramo `daje-de-fionda` contiene entrambi. Non è ancora su `main`: il sito pubblico non è cambiato.

## Prossimi step (uno alla volta)
1. ~~Ritagliare i personaggi dal foglio (sfondo trasparente) e usarli come sprite al posto dei disegni via codice.~~ Fatto.
2. Sfondo di Trastevere: ~~case (strato vicino)~~ fatto. Manca il fondale lontano (cielo, cupola di San Pietro, campanile di Santa Maria in Trastevere, pini), oggi ancora disegnato via codice e quasi coperto dalle case.
3. Grafica dei materiali (legno, vetro, travertino, metallo, cassonetto), selciato, buca e fionda; poi sfondi per gli altri rioni.
4. Poteri degli altri personaggi (maranza che si divide in 3, tassista col clacson, turista col selfie stick), suoni e voci in romanesco.
5. Altri mondi: Fontana di Trevi, Pantheon, Piazza Venezia, Colosseo con il Re Gabbiano.
6. Pubblicazione su ozencore: unire il ramo a `main`.

## Prova in locale
Serve un server HTTP: `python3 -m http.server` dalla radice del repo, poi apri `http://localhost:8000/fionda/`.
