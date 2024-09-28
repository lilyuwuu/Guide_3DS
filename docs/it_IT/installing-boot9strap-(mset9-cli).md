# Installazione di boot9strap (MSET9 CLI)

:::details Technical Details (optional)

[MSET9](https://github.com/zoogie/MSET9) è un exploit per l'applicazione "Impostazioni della console" sviluppata da [zoogie](https://github.com/zoogie). Sfrutta una falla per cui l'ID1 (la seconda cartella a 32 caratteri all'interno di Nintendo 3DS, all'interno di ID0) può essere _qualsiasi_ nome a condizione che sia lungo 32 caratteri. L'esecuzione di una sequenza specifica di azioni determina nella console l'esecuzione delle istruzioni codificate nel nome della cartella ID1, che può essere utilizzato per garantire pieno controllo del 3DS.

:::

## Compatibility Notes

::: warning

Questa pagina richiede un computer che esegue Windows, Linux o macOS. Se hai un telefono/tablet Android o un Chromebook, segui invece [Installazione di boot9strap (MSET9 Play Store)](installing-boot9strap-\(mset9-play-store\)). Se non hai accesso a nessuno di questi dispositivi, dovrai usare un [exploit alternativo](https://wiki.hacks.guide/wiki/3DS:Alternate_Exploits).

:::

## What You Need

- The latest release of [MSET9](https://github.com/hacks-guide/MSET9/releases/latest)
- Any 3.x version of [Python](https://www.python.org/downloads/) **installed on your computer**
  - If you are on Linux or macOS, you may already have Python 3. Controlla aprendo una finestra del terminale e inserendo `python3 -V`. Se il comando restituisce un numero di versione, funzionerà per questa guida.

## Instructions

::: info

In questa pagina eseguirai lo script di MSET9, che viene utilizzato per attivare MSET9. Durante l'esecuzione dello script i dati utente scompariranno temporaneamente, ma torneranno al completamento di questa pagina. Se ricevi un errore durante l'esecuzione dello script, puoi probabilmente trovarne la soluzione alla pagina [Risoluzione dei problemi](troubleshooting#installing-boot9strap-mset9).

:::

### Section I - Prep Work

In questa sezione preparerai l'exploit MSET9 creando **temporaneamente** un nuovo profilo per il menu HOME senza dati utente, configurandolo con i dati minimi necessari per l'esecuzione di MSET9. I tuoi dati dati utente attuali scompariranno, ma torneranno al termine di questa pagina.

1. Inserisci la scheda SD nel tuo computer

2. Copia tutto il contenuto dell'archivio `.zip` di MSET9 nella directory principale della tua scheda SD, sovrascrivendo tutti i file esistenti

   ::: info

   ![MSET9 root layout](/images/screenshots/mset9/mset9-root-layout.png)

   :::

3. Esegui lo script di MSET9:

<!--@include: ./_include/mset9-chorus.md -->

```
::: info

![Image: MSET9 setup](/images/screenshots/mset9/mset9-select.png)

:::
```

1. Digita il numero corrispondente al modello di console e alla versione, quindi premi Invio

   - The window should change to this:

   ::: info

   ![Image: MSET9 setup](/images/screenshots/mset9/mset9-setup-notcreated.png)

   :::

   - Ensure that the correct console model and version is displayed
2. Digita `1`, quindi premi Invio per iniziare il processo di creazione dell'ID1 di MSET9
3. Dopo aver letto il disclaimer, digita di nuovo `1` e premi Invio per accettarlo
   - If you get an error, check the [troubleshooting](troubleshooting#installing-boot9strap-mset9), then try again
4. Se vedi il messaggio "Created hacked ID1.", premi Invio per chiudere lo script di MSET9
   - Your 3DS will appear to have no data / no user-installed apps on HOME Menu. **È normale.** I tuoi dati saranno ripristinati in un secondo momento
5. Reinserisci la scheda SD nella tua console
6. Accendi la tua console
7. Avvia il Centro di creazione Mii
8. Attendi che la console raggiunga la schermata [Benvenuto al Centro di creazione Mii](/images/screenshots/mset9/mii-welcome.png), quindi esci per tornare al menu HOME
   - You may see [this screen](/images/screenshots/mset9/mii-extdata.png), which indicates the necessary data has been created
   - If you just reach the [normal](/images/screenshots/mset9/mii-existing.png) Mii Maker screen, then the data already exists. Esci dal Centro di creazione Mii e torna al menu HOME
9. Avvia le Impostazioni della console e vai su `Gestione dati` -> `Nintendo 3DS` -> `Software` -> Reset ([immagine](/images/screenshots/database-reset.jpg))
   - This will not wipe any of your data
10. Spegni la console premendo il pulsante di accensione, quindi tocca "Spegni" sullo schermo inferiore
11. Inserisci la scheda SD nel tuo computer
12. Esegui lo script di MSET9:

<!--@include: ./_include/mset9-chorus.md -->

1. Digita il numero corrispondente al modello di console e alla versione, quindi premi Invio

   - The window should change to this and display `Ready`:

   ::: info

   ![Image: MSET9 setup](/images/screenshots/mset9/mset9-ready.png)

   :::

   - If the window says [Not ready - check MSET9 status for more details](/images/screenshots/mset9/mset9-not-ready.png):
     - Type `2`, then press Enter to check the MSET9 status and follow the directions indicated
     - Once you have resolved the issue, return to Section I Step 14
     - For more information, check the [troubleshooting](troubleshooting#installing-boot9strap-mset9) page
2. Digita `0`, quindi premi Invio per chiudere lo script
3. Reinserisci la scheda SD nella tua console

### Section II - MSET9

In questa sezione attiverai MSET9 per avviare SafeB9SInstaller (l'installer del custom firmware).

::: danger

Queste istruzioni vanno eseguite **ALLA LETTERA**, quindi ricontrolla TUTTO quello che farai per evitare errori!

:::

1. Accendi la tua console, assicurandoti che le Impostazioni della console siano selezionate
   - If System Settings is not selected, **[hover over](/images/screenshots/mset9/hover-settings.png)** the System Settings icon using the D-Pad, power your console off, then back on
2. Premi (A) per avviare le Impostazioni della console
3. Entra in `Gestione dati` -> `Nintendo 3DS` -> `Dati aggiuntivi` ([immagine](/images/screenshots/bb3/settings-extdata.png))
4. **Non premere alcun pulsante e non toccare lo schermo**
5. **Con la console ANCORA ACCESA e senza premere alcun pulsante o toccare lo schermo**, rimuovi la tua scheda SD dalla console
   - The menu will refresh and say that no SD card is inserted
6. Inserisci la scheda SD nel tuo computer
7. Esegui lo script di MSET9:

<!--@include: ./_include/mset9-chorus.md -->

1. Digita il numero corrispondente al modello di console e alla versione, quindi premi Invio
2. Nella finestra di MSET9, premi `3`, quindi premi Invio per iniettare MSET9
   - You should see "MSET9 successfully injected!"
3. Premi Invio per chiudere lo script di MSET9
4. Reinserisci la scheda SD nella console **senza premere alcun pulsante o toccare lo schermo**
5. Se l'exploit è andato a buon fine, si avvierà SafeB9SInstaller
   - If you get a red screen or the console gets stuck on a loading screen, follow the [troubleshooting guide](troubleshooting#installing-boot9strap-mset9)

### Section III - Installing boot9strap

In questa sezione installerai il custom firmware sulla tua console.

1. Quando richiesto, inserisci la combinazione di tasti richiesta sullo schermo superiore per installare boot9strap
   - If a step on the lower screen has red-colored text, and you are not prompted to input a key combo, [follow this troubleshooting guide](troubleshooting#issues-with-safeb9sinstaller)
2. Una volta completato tutto, premi (A) per riavviare la console

<!--@include: ./_include/configure-luma3ds.md -->

### Section IV - Removing MSET9

In questa sezione rimuoverai MSET9 per evitare ulteriori problemi e per ripristinare i tuoi dati utente (giochi, temi, ecc.). (Questo non rimuoverà il custom firmware che hai appena installato.)

::: danger

NON saltare questa sezione! Se lo salti, le applicazioni potrebbero inaspettatamente crashare e riscontrerai errori nella pagina successiva!

:::

1. Spegni la tua console
2. Inserisci la scheda SD nel tuo computer
3. Esegui lo script di MSET9:

<!--@include: ./_include/mset9-chorus.md -->

1. Digita il numero corrispondente al modello di console e alla versione, quindi premi Invio
   - The current state should display [Injected](/images/screenshots/mset9/mset9-injected.png)
   - If you have already removed the trigger file (or never injected in the first place), the current state will show [Ready](/images/screenshots/mset9/mset9-ready.png), skip to Step 6
2. Digita `4`, quindi premi Invio per rimuovere il file
   - You should see "Removed trigger file."
3. Digita `5`, quindi premi Invio per rimuovere MSET9
   - You should see "Successfully removed MSET9!"
4. Premi Invio per chiudere lo script di MSET9

<!--@include: ./_include/luma3ds-installed-note.md -->

___

::: danger

Hai seguito la Sezione IV (Disinstallare MSET9)? Quella sezione è OBBLIGATORIA!

:::

::: tip

Continue to [Finalizing Setup](finalizing-setup)

:::