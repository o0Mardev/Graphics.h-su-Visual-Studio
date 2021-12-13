# Graphics.h su Visual Studio
Questa è una guida con l'intento di aiutare coloro che vorrebbero per qualuncue motivo installare e configurare Visual Studio per la libreria graphics.h


### Indice
Si divide in 3 sezioni:
-[Installazione del compilatore](#prima-sezione)
-[Installazione di Visul Studio](#seconda-sezione)
-[Test funzionamento](#terza-sezione)


## Prima sezione
1. andare su https://sourceforge.net/projects/mingw/
   scaricare e installare il programma.
   N.B. Cambiare la cartella di installazione provoca errori nell'installazione si consiglia di lasaciarla invariata


2. Una volta avviato il programma MinGW Installation Manager selezionare nella schermata di sinistra:

```
   -mingw32-base
   -mingw32-gcc-g++
```
   cliccare su mark for installation per selezionare
 
   nella barra delle opzioni del programma fare click su Installation e cliccare su Apply Changes.
   aspettare che finisca di installare il compilatore e quando fatto premere su Close e chiudere il programma.


3. Copiare il file graphics.h nella cartella include del compilatore C:\MinGW\include 
   Copiare il file libbgi.h nella cartella lib del compilatore C:\MinGW\lib

   Per raggiungere la cartella Esplora file -> questo PC -> Disco locale -> MinGW


4. Cercare nella barra di ricerca di Windows "Modifica le variabili di ambiente relative al sistema"
   dalla schermata cliccare il pulsante "Variabili di ambiente" successivamente nella parte di sopra
   "Variabili dell'utente per ..." doppio click su "Path" andare su "Nuovo" e scrivere "C:\MinGW\bin" (no virgolette).
   Per finire questa sezione IMPORTANTE Fare click su "Ok" poi di nuovo "Ok" e per finire "Ok" (Altrimenti non salva le impostazioni).


5. Per testare che tutto funzioni correttamente
   aprire il prompt dei comandi (Dalla barra di ricerca di windows Prompt dei comandi)
   e digitare "g++ --version" (senza virgolette)
   dovrebbe uscire:
```
g++ (MinGW.org GCC Build-2) 9.2.0
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

## Seconda Sezione

Seconda sezione Installazione di visual studio code e configurazione.

1. Scaricare e installare visual studio code da: https://code.visualstudio.com/


2. Una volta installato e aperto ci darà il benvenuto possiamo scegliere il tema tra quelli proposti a lato
   in basso a destra dovrebbe comparire (dipende dalla connesione) una notifica che ci chiede di installare il pacchetto lingua italiano
   premiamo su Install, visual studio si riavvierà e la lingua sarà impostata


3. Nella barra laterale a sinistra ci sono 5 pulsanti premiamo il 5° quello con la forma di un puzzle e scriviamo Code runnner
   Installiamo l'estensione la prima (quella con l'icona .run)


4. Dal pannello dove abbiamo cercato l'estensione clicchiamo sul piccolo ingranaggio a lato (non quello in basso) da lì clicco ancora Impostazione estensione
   troviamo l'impostazione "Code-runner: Executor Map"
   Da lì cliccare su modifica in settings.json
  in settings.json tra le due parentesi graffe incollare (no trattini):
```
"code-runner.executorMap": {
        "cpp": "g++ $fullFileName -o $fileNameWithoutExt.exe -lbgi -lgdi32 -lcomdlg32 -luuid -loleaut32 -lole32 && start $fileNameWithoutExt.exe",
        "c": "gcc $fullFileName -o $fileNameWithoutExt.exe && start $fileNameWithoutExt.exe"
    }
```
  Premere ctrl + s per salvare.




## Terza sezione

1. Proviamo un run con questo esempio:

2. Per creare un nuovo file prima di tutto creiamo una cartella dove salvare gli esercizi
   se ne hai già una andare su File nella barra in alto, apri Cartella, selezionare la cartella e premere apri.

3. Dalla barra laterale a sinistra con le 5 opzioni premiamo la prima (Esplora risorse)
   Per creare il file conviene premere sulla prima icona con il + piccolino accanto a ESPLORA RISORSE: nomecartella...

4. Da lì scrivere il nome del file (ATTENZIONE NON DEVE CONTENERE SPAZI) e dopo il nome scrivere .cpp
   esempio:
   Test.cpp
   Una volta scritto dare invio dalla schermata incollare il seguente esempio:

```cpp
#include <stdio.h>
#include <stdlib.h>
#include <graphics.h>
int main(int argc, char *argv[])
{
    initwindow(300, 400, "IL MIO PRIMO GRAFICO", 100, 80);
    putpixel(150, 250, COLOR(255,0,0));
    circle(80, 100, 30);
    line(30, 60, 100, 160);
    getch();
    closegraph();
    exit(0);
}
```
Premi infine il tasto Run Code in alto a destra appena sotto al tasto per ripristinare la finestra (oppure premi ctrl + alt + n).
