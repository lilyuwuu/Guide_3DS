# Informazioni importanti

::: danger

<!--@include: ./_include/3ds-online.md -->

:::

::: info

Se è la prima volta che modifichi un Nintendo 3DS (o non hai esperienza con la tecnologia), continua a leggere! Altrimenti, se hai già qualche esperienza e sai cosa tu stia facendo, prosegui con [Cominciamo!](get-started).

:::

Questa pagina contiene alcune terminologie informatiche di base e informazioni specifiche dei 3DS che dovresti conoscere prima di seguire questa guida.

Ogni sezione è collassata. Fai clic o tocca il nome della sezione per aprirla.

## Things you should know about the 3DS

:::: details 3DS/2DS compatibility

::: info

![](/images/screenshots/onboarding/compatible.png)

:::

Questa guida funziona su tutte le versioni retail della famiglia di console Nintendo 3DS (compresi 3DS, 3DS XL/LL, 2DS, New 3DS, New 3DS XL/LL, e New 2DS XL/LL), indipendentemente dalla regione o dal firmware.

::::

:::: details Computer compatibility

::: info

![](/images/screenshots/onboarding/os.jpg)

:::

Nella maggior parte dei casi, puoi seguire questa guida a patto che tu possa scaricare file tramite Internet e copiarli sulla tua scheda SD. A seconda del tuo computer/cellulare/dispositivo elettronico, potresti aver bisogno di acquistare un adattatore da scheda SD a USB, per far sì che il tuo computer possa leggere la scheda SD.

::::

:::: details SD card location, type, and capacity

::: info

![](/images/screenshots/onboarding/sdcard.jpg)

:::

La posizione dello slot della scheda SD e il tipo di scheda SD da usare dipendono dal modello del tuo 3DS. Ulteriori informazioni sono disponibili alla [pagina ufficiale di supporto Nintendo](https://www.nintendo.it/Servizio-al-consumatore/Nintendo-3DS-e-Nintendo-2DS/Uso/Schede-SD/Usare-le-schede-SD/Usare-le-schede-SD-826532.html).

Il 3DS può leggere schede SD di qualunque capienza (anche più grandi di 32GB), tuttavia la scheda dev'essere formattata con filesystem FAT32 (**non** exFAT né NTFS). Puoi usare una delle seguenti applicazioni per formattare la tua scheda SD, a seconda del tuo sistema operativo: [Windows](formatting-sd-\(windows\)), [macOS](formatting-sd-\(mac\)), [Linux](formatting-sd-\(linux\)). SD più grandi di **128GB** non sono consigliate a causa di problemi noti con i temi personalizzati e con la grafica GBA/DS.

::: warning

Per seguire questa guida, ti servirà una scheda SD di almeno **2GB**.

:::

::: info

È consigliabile verificare che la tua scheda SD sia priva di errori prima di seguire questa guida usando [H2testw (Windows)](h2testw-\(windows\)), [F3 (Linux)](f3-\(linux\)), o [F3XSwift (Mac)](f3xswift-\(mac\))

:::

::::

:::: warning
::: details Potential risks (Disclaimer)

Effettuando la modifica alla tua console, la sottoponi ad un remoto (ma possibile) rischio di brick (che la renderebbe inutilizzabile). _**Se sbagli a posizionare dei file NON brickerai la console**_, potresti invece brickarla saltando alcuni passaggi.

Riassumendo: Modificare la tua console è sicuro, ma _**è una tua responsabilità**_ se qualcosa dovesse andare storto.

:::
::::

## Things you need to do on your computer

::: warning

Seguendo questa guida non dovrebbero verificarsi perdite di dati, ma è sempre possibile che capiti una corruzione della scheda SD. Se hai dati importanti, dovresti fare un backup dei contenuti della tua scheda SD (soprattutto della cartella `Nintendo 3DS`).

:::

:::: details File placement terminology (e.g. "root of SD", "/luma/")

::: info

![](/images/screenshots/onboarding/sdroot.png)

:::

Quando si copiano i file nella scheda SD, è importante copiarli nella giusta posizione - altrimenti, la console non rileverà il file e l'exploit o il software che stai cercando di utilizzare non funzionerà. Un termine che vedrai frequentemente su questa guida è **directory principale della scheda SD**, il che significa che non si è all'interno di alcuna cartella sulla scheda SD. La cartella che appare immediatamente quando si apre la scheda SD sul computer è chiamata 'directory principale'.

Potresti anche vedere i nomi delle cartelle indicati in questa maniera: `/cartella/`. Gli slash sono usati per indicare le cartelle e non fanno parte del loro nome. Per esempio, `/cartella1/cartella2/` fa riferimento a `cartella2` all'interno di `cartella1`:

::: info

![](/images/screenshots/onboarding/folders.png)

:::

**Le parentesi angolari** (\< e \>) sono usate anche occasionalmente per fare riferimento a identificatori specifici del sistema. Ad esempio, se la guida dice `<ID0>`, si fa riferimento all'identificatore specifico di sistema all'interno della cartella `Nintendo 3DS`, piuttosto che ad una cartella chiamata letteralmente "ID0":

::: info

![](/images/screenshots/onboarding/anglebrackets.png)

:::

::::

:::: details Downloading files from GitHub

::: info

![](/images/screenshots/onboarding/github.png)

:::

In questa guida copierai i file scaricati dal tuo computer o cellulare nella scheda SD della tua console. Molti di questi file provengono da GitHub, un sito web utilizzato da sviluppatori per pubblicare le proprie applicazioni open-source. Quando scarichi file da GitHub, dovresti scaricare il file che _non è_ il codice sorgente.

::::

:::: details Opening/extracting files

::: info

![](/images/screenshots/onboarding/zipfiles.png)

:::

Alcuni dei file che ti verrà richiesto di scaricare saranno in formato `.zip`, utilizzato per comprimere più file in uno unico.

Quando ti verrà chiesto di "copiare il file (tizio) dall'archivio (caio).zip", significa che dovrai aprire (o meglio, "estrarre") il file ZIP. Dentro il file ZIP ci saranno i file che cerchi, che potrai copiare nella posizione richiesta sulla tua scheda SD.

Nella maggior parte dei sistemi operativi, per estrarre i file basta farci un doppio clic sopra. Se non ci riesci o non funziona, puoi installare invece un tool di terze parti affidabile come [7-Zip](https://7-zip.org/).

::::

:::: details (Windows only) File extensions

::: info

![](/images/screenshots/onboarding/fileext.png)

:::

Se hai un computer con Windows, le estensioni dopo il nome del file potrebbero essere nascoste per impostazione predefinita, rendendo più complicato trovare il file che stai cercando. Per abilitare le estensioni dopo il nome del file, segui [queste istruzioni](file-extensions-\(windows\)).

::::

## Getting help

Se riscontri dei problemi seguendo questa guida, ci sono tanti modi per ricevere aiuto!

- If you have any questions that haven't been answered on this page, their answers might be in the [Pre-Installation FAQ](faq#pre-installation-faq).
- If you experience an issue while following this guide, you can check the [Troubleshooting](troubleshooting) page for a solution.
- If the resources we've provided here aren't helping, you can get one-on-one support over at [Nintendo Homebrew on Discord](https://discord.gg/MWxPgEp).

::: tip

Prosegui con [Cominciamo!](get-started)

:::