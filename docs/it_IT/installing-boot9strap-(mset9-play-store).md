# Installazione di boot9strap (MSET9 Play Store)

:::details Technical Details (optional)

[MSET9](https://github.com/zoogie/MSET9) è un exploit per l'applicazione "Impostazioni della console" sviluppata da [zoogie](https://github.com/zoogie). Sfrutta una falla per cui l'ID1 (la seconda cartella a 32 caratteri all'interno di Nintendo 3DS, all'interno di ID0) può essere _qualsiasi_ nome a condizione che sia lungo 32 caratteri. L'esecuzione di una sequenza specifica di azioni determina nella console l'esecuzione delle istruzioni codificate nel nome della cartella ID1, che può essere utilizzato per garantire pieno controllo del 3DS.

:::

## Compatibility Notes

::: warning

Questa pagina richiede un telefono/tablet Android o un Chromebook. Se hai un computer che esegue Windows, macOS o Linux, segui invece [Installazione di boot9strap (MSET9 CLI)](installing-boot9strap-\(mset9-cli\)). Se non hai accesso a nessuno di questi dispositivi, dovrai usare un [exploit alternativo](https://wiki.hacks.guide/wiki/3DS:Alternate_Exploits).

:::

::: warning

Su telefoni/tablet Android, la versione minima di Android richiesta è 6.0 (Marshmallow).

:::

## What You Need

- The following applications installed from the Google Play Store:
  - [MSET9 Installer](https://play.google.com/store/apps/details?id=moe.saru.homebrew.console3ds.mset9_installer_android)
  - [ZArchiver](https://play.google.com/store/apps/details?id=ru.zdevs.zarchiver)
  - If you wish, you can sideload these applications instead
- The latest release of [MSET9](https://github.com/zoogie/MSET9/releases/latest) (the Release `.zip` file)

## Instructions

### Section I - Prep Work

In questa sezione preparerai i dati della scheda SD necessari per attivare l'exploit MSET9.

1. Accendi la console **con la scheda SD inserita**

2. Avvia il Centro di creazione Mii

3. Attendi che la console raggiunga la schermata "Benvenuto nel Centro di creazione Mii", quindi esci dall'applicazione
   - You may see [this screen](/images/screenshots/mset9/mii-extdata.png), which indicates the necessary data has been created
   - If you just reach the normal Mii Maker screen, exit Mii Maker and continue to the next step

4. Spegni la tua console

5. Inserisci la tua scheda SD nel tuo telefono/tablet/computer

6. Copia tutto il contenuto dell'archivio Release `.zip` nella directory principale della tua scheda SD, sovrascrivendo tutti i file esistenti:

   - Open ZArchiver
   - If prompted, [allow ZArchiver to access files on your SD card](/images/screenshots/mset9/zarchiver-allow.png)
   - Navigate to where the downloaded MSET9 Release `.zip` is located ([likely in the Downloads folder](/images/screenshots/mset9/zarchiver-zip-location.png))
   - Select the Release `.zip`, then select "Extract..." ([image](/images/screenshots/mset9/zarchiver-extract-1.png))
   - Navigate to your SD card, then tap the blue 'down arrow' icon to extract the files to the root of your SD card ([image](/images/screenshots/mset9/zarchiver-extract-2.png))

   ::: info

   ![MSET9 root layout](/images/screenshots/mset9/mset9-root-layout-android.png)

   :::

7. Eseguire l'applicazione [MSET9 Installer](/images/screenshots/mset9/mset9-setup-android.png)

8. Tocca su `Select "Nintendo 3DS" Folder`, quindi vai alla cartella `Nintendo 3DS` sulla tua scheda SD ([immagine](/images/screenshots/mset9/select-mset9-folder-1.png))

9. Una volta all'interno della cartella `Nintendo 3DS`, tocca "Use this folder", quindi "Allow" se richiesto ([immagine](/images/screenshots/mset9/select-mset9-folder-2.png))

10. Se "Setup MSET9" è [evidenziato](/images/screenshots/mset9/setup-mset9-highlighted.png), procedi al passaggio successivo. **Non configurare MSET9.** Per ora chiudi l'Installer di MSET9
    - If "Check Again" is highlighted, there is a problem that you need to resolve before you can use MSET9. Fai riferimento alla [guida per risolvere i problemi](troubleshooting#installing-boot9strap-mset9)

11. Reinserisci la scheda SD nella tua console

12. Accendi la tua console

### Section II - MSET9

In questa sezione attiverai MSET9 per avviare SafeB9SInstaller (l'installer del custom firmware).

::: danger

Queste istruzioni vanno eseguite **ALLA LETTERA**, quindi ricontrolla TUTTO quello che farai per evitare errori!

:::

1. **[Passa sopra](/images/screenshots/mset9/hover-settings.png)** l'icona di "Impostazioni della console" con il D-Pad (senza selezionarlo)
2. Spegni, quindi riaccendi la tua console
3. Premi (A) per avviare le Impostazioni della console
4. Entra in `Gestione dati` -> `Nintendo 3DS` -> `Dati aggiuntivi` ([immagine](/images/screenshots/bb3/settings-extdata.png))
5. **Non premere alcun pulsante e non toccare lo schermo**
6. **Con la console ANCORA ACCESA e senza premere alcun pulsante o toccare lo schermo**, rimuovi la tua scheda SD dalla console
   - The menu will refresh and say that no SD card is inserted, which is expected
7. Inserisci la tua scheda SD nel tuo telefono/tablet/computer
8. Apri l'applicazione MSET9 Installer
9. Tocca "Setup MSET9"
10. Tocca la foto corrispondente al modello della tua console, quindi sul pulsante corrispondente alla versione attuale del software
    - If the injection was successful, all buttons should become grayed out except for "Remove MSET9"
11. Reinserisci la scheda SD nella console **senza premere alcun pulsante o toccare lo schermo**
12. Se l'exploit è andato a buon fine, si avvierà SafeB9SInstaller
    - If you get a red screen or the console gets stuck on a loading screen, follow the [troubleshooting guide](troubleshooting#installing-boot9strap-mset9)

### Section III - Installing boot9strap

In questa sezione installerai il custom firmware sulla tua console.

1. Quando richiesto, inserisci la combinazione di tasti richiesta sullo schermo superiore per installare boot9strap
   - If a step on the lower screen has red-colored text, and you are not prompted to input a key combo, [follow this troubleshooting guide](troubleshooting#issues-with-safeb9sinstaller)
2. Una volta completato tutto, premi (A) per riavviare la console

<!--@include: ./_include/configure-luma3ds.md -->

### Section IV - Removing MSET9

In questa sezione rimuoverai MSET9 per evitare problemi successivi. (Questo non rimuoverà il custom firmware che hai appena installato.)

::: danger

NON saltare questa sezione! Se lo salti, le applicazioni potrebbero inaspettatamente crashare e riscontrerai errori nella pagina successiva!

:::

1. Spegni la tua console
2. Inserisci la tua scheda SD nel tuo telefono/tablet/computer
3. Apri l'applicazione MSET9 Installer
4. Tocca "Remove MSET9"
5. Chiudi l'applicazione MSET9 Installer

<!--@include: ./_include/luma3ds-installed-note.md -->

___

::: danger

Hai seguito la Sezione IV (Disinstallare MSET9)? Quella sezione è OBBLIGATORIA!

:::

::: tip

Continue to [Finalizing Setup](finalizing-setup)

:::