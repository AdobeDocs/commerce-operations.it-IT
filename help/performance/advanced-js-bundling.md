---
title: Avanzate [!DNL JavaScript] Bundle
description: Scopri come il bundling JavaScript può ridurre le dimensioni e la frequenza delle richieste server.
source-git-commit: 09c4d0e09354230c8779b930f085d8c7c131b85b
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---


# Avanzate [!DNL JavaScript] raggruppamento

Bundle [!DNL JavaScript] i moduli per migliorare le prestazioni riguardano la riduzione di due elementi:

1. Numero di richieste server.
1. Dimensione di tali richieste server.

In un&#39;applicazione modulare, il numero di richieste server può raggiungere le centinaia. Ad esempio, la seguente schermata mostra solo l’inizio dell’elenco di [!DNL JavaScript] moduli caricati nella home page di un&#39;installazione pulita.

![Nessun bundle](../assets/performance/images/noBundling.png)

## Unione e bundle

Fuori dalla scatola, [!DNL Commerce] fornisce due modi per ridurre il numero di richieste server: unione e bundling. Queste impostazioni sono disattivate per impostazione predefinita. Puoi attivarli nell’interfaccia utente di amministrazione in **[!UICONTROL Stores]** > **Impostazioni** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** o dalla riga di comando.

![Bundle](../assets/performance/images/bundlingImage.png)

### Bundle di base

Per abilitare il bundling integrato dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Questo è un nativo [!DNL Commerce] meccanismo che combina tutte le risorse presenti nel sistema e le distribuisce tra bundle di dimensioni uguali (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] raggruppamento](../assets/performance/images/magentoBundling.png)

Meglio, ma il browser carica ancora TUTTI i [!DNL JavaScript] i bundle, non solo quelli necessari.

[!DNL Commerce] il bundling riduce il numero di connessioni per pagina, ma per ogni richiesta di pagina carica tutti i bundle, anche quando la pagina richiesta può dipendere solo da file all&#39;interno di uno o due dei bundle. Le prestazioni migliorano dopo che il browser memorizza in cache i bundle. Ma, poiché il browser carica questi bundle in modo sincrono, la prima visita dell&#39;utente a un [!DNL Commerce] storefront potrebbe richiedere un po&#39; di tempo per eseguire il rendering e danneggiare l&#39;esperienza utente.

### Unione di base

Per abilitare l&#39;unione integrata dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Questo comando unisce tutti i sincroni [!DNL JavaScript] file in un unico file. L’abilitazione dell’unione senza l’abilitazione del bundling non è utile perché [!DNL Commerce] utilizza RequireJS. Se non attivi il bundling, [!DNL Commerce] unisce solo RequireJS e la relativa configurazione. Quando abiliti sia il bundling che l&#39;unione, [!DNL Commerce] crea un singolo [!DNL JavaScript] file:

![Unione nel mondo reale](../assets/performance/images/magentoMergingDevWorld.png)

## Tempi di rendering del mondo reale

I tempi di caricamento precedenti raggruppati e uniti si presentano benissimo in un ambiente di sviluppo. Ma nel mondo reale, molte cose possono rallentare il rendering: connessioni lente, soglie di connessione elevate, reti limitate. Inoltre, i dispositivi mobili non eseguono il rendering rapido quanto i desktop.

Per testare e preparare la distribuzione di vetrina per il mondo reale, ti consigliamo di testare con il profilo di limitazione nativo di Chrome di &quot;Slow 3G&quot;. Con Slow 3G, i nostri precedenti tempi di uscita in bundle ora riflettono le realtà di connessione di molti utenti:

![Bundle reale](../assets/performance/images/magentoBundlingRealWorld.png)

Con una connettività 3G lenta, ci vogliono circa 44 secondi per caricare tutti i bundle per la homepage di una pulizia [!DNL Commerce] installazione.

Lo stesso vale per l’unione dei bundle in un singolo file. Gli utenti potevano comunque attendere circa 42 secondi per il caricamento iniziale della pagina, come illustrato di seguito:

![Unione nel mondo reale](../assets/performance/images/magentoMergingRealWorld.png)

Con un approccio più avanzato a [!DNL JavaScript] Possiamo migliorare questi tempi di caricamento.

## Bundle avanzato

Ricordate, l&#39;obiettivo di [!DNL JavaScript] Il bundling consiste nel ridurre il numero e la dimensione delle risorse richieste per ogni pagina caricata nel browser. Per farlo, vogliamo creare i nostri bundle in modo che ogni pagina nel nostro negozio dovrà scaricare solo un bundle comune e un bundle specifico per la pagina per ogni pagina a cui si accede.

Un modo per farlo è definire i bundle in base ai tipi di pagina. Puoi categorizzare [!DNL Commerce]Pagine in diversi tipi di pagine, tra cui Categoria, Prodotto, CMS, Cliente, Carrello e Pagamento. Ogni pagina suddivisa in uno di questi tipi di pagina dispone di un diverso set di dipendenze del modulo RequireJS. Quando esegui il bundle dei moduli RequireJS per tipo di pagina, finirai con una manciata di bundle che coprono le dipendenze di qualsiasi pagina nel tuo negozio.

Ad esempio, potresti ritrovarti con un bundle per le dipendenze comuni a tutte le pagine, un bundle per le pagine solo CMS, un bundle per le pagine solo catalogo, un altro bundle per le pagine solo ricerca e un bundle per le pagine di checkout.

Puoi anche creare bundle in base allo scopo: per funzioni comuni, funzionalità relative ai prodotti, funzionalità di spedizione, funzioni di pagamento, imposte e convalide dei moduli. La definizione dei bundle dipende da te e dalla struttura del tuo negozio. È possibile che alcune strategie di bundling funzionino meglio di altre.

Una pulizia [!DNL Commerce] l’installazione consente di raggiungere prestazioni abbastanza buone suddividendo i bundle per tipi di pagina, ma alcune personalizzazioni possono richiedere un’analisi più approfondita e altre distribuzioni di risorse.

### Strumenti richiesti

I passaggi seguenti richiedono l’installazione e la familiarità con i seguenti strumenti:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](http://phantomjs.org/) (facoltativo)

### Codice di esempio

Le versioni complete del codice di esempio utilizzato in questo articolo sono disponibili qui:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Parte 1: Creare una configurazione di bundle

#### 1\. Aggiungere un file build.js

Crea un `build.js` nel [!DNL Commerce] directory principale. Questo file conterrà l&#39;intera configurazione di build per i bundle.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Successivamente, cambieremo il `optimize:` impostazione da_ `none` a `uglify2` per minimizzare l&#39;output del bundle. Ma per ora, durante lo sviluppo, si può lasciare impostato su `none` per garantire build più veloci.

#### 2\. Aggiungi dipendenze RequireJS, shims, percorsi e mappa

Aggiungi i seguenti nodi di configurazione della build RequireJS, `deps`, `shim`, `paths`e `map`, al file di build:

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\. Aggrega i valori dell&#39;istanza Requirejs-config.js

In questo passaggio, dovrai aggregare tutti i multipli `deps`, `shim`, `paths`e `map` nodi di configurazione dell&#39;archivio `requirejs-config.js` nei nodi corrispondenti nel tuo `build.js` file. A questo scopo, puoi aprire il **[!UICONTROL Network]** nel pannello Strumenti per sviluppatori del browser e passa a qualsiasi pagina del negozio, ad esempio alla home page. Nella scheda Rete verrà visualizzata l&#39;istanza del tuo negozio di `requirejs-config.js` file vicino alla parte superiore, evidenziato qui:

![Richiedi configurazione JS](../assets/performance/images/RequireJSConfig.png)

All&#39;interno di questo file, troverai più voci per ciascuno dei nodi di configurazione (`deps`, `shim`, `paths`, `map`). Devi aggregare questi valori di nodo multipli nel nodo di configurazione singolo del file build.js. Ad esempio, se il tuo negozio è `requirejs-config.js` istanza ha voci per 15 separate `map` nodi, sarà necessario unire le voci per tutti i 15 nodi nel singolo `map` nel nodo `build.js` file. Lo stesso vale per il `deps`, `shim`e `paths` nodi. Senza uno script per automatizzare questo processo, potrebbe essere necessario del tempo.

Sarà necessario modificare il percorso `mage/requirejs/text` a `requirejs/text` in `paths` nodo di configurazione come segue:

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. Aggiungi un nodo di moduli

Alla fine del `build.js` file, aggiungi i moduli[] array come segnaposto per i bundle che verranno definiti per la vetrina in un secondo momento.

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\. Recuperare le dipendenze RequireJS

È possibile recuperare tutte le [!DNL RequireJS] dipendenze del modulo dai tipi di pagina dell&#39;archivio utilizzando:

1. [!DNL PhantomJS] dalla riga di comando (supponendo che [!DNL PhantomJS] installati).
1. Richiedi il comando JS nella console del browser.

#### Per utilizzare [!DNL PhantomJS]:

In [!DNL Commerce] directory principale, creare un nuovo file denominato `deps.js` e copia nel codice seguente. Questo codice utilizza [!DNL [!DNL PhantomJS]] per aprire una pagina e attendere che il browser carichi tutte le risorse di pagina. e quindi emette tutte le [!DNL RequireJS] dipendenze per una determinata pagina.

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

Apri un terminale all&#39;interno di [!DNL Commerce] directory principale ed esegui lo script su ogni pagina nello store che rappresenta un tipo di pagina specifico:

<pre>
phantomjs deps.js <i>da url a pagina specifica</i> &gt; <i>text-file-rappresentanti-pagetype-dependencies</i>
</pre>

Ad esempio, ecco quattro pagine dall’archivio di campioni a tema Luma che rappresentano i quattro tipi di pagina che utilizzeremo per creare i nostri quattro bundle (home page, categoria, prodotto, carrello):

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### Per utilizzare la console del browser:

Se non desideri utilizzare [!DNL PhantomJS], puoi eseguire il seguente comando dalla console del browser quando visualizzi ogni tipo di pagina nella vetrina:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Questo comando (utilizzato all&#39;interno del [!DNL PhantomJS] crea lo stesso elenco di [!DNL RequireJS] le dipendenze e le visualizza nella console del browser. Lo svantaggio di questo approccio è che dovrai creare file di testo di tipo bundle/page.

#### 6\. Formattare e filtrare l&#39;output

Dopo l&#39;unione [!DNL RequireJS] dipendenze in file di testo di tipo pagina, è possibile utilizzare il seguente comando su ogni file di dipendenza di tipo pagina per sostituire le virgole nei file con righe nuove:

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

È inoltre necessario rimuovere tutti i mixin per ogni file perché i mixin duplicano le dipendenze. Utilizzare il seguente comando su ogni file di dipendenza:

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7 Identificare bundle univoci e comuni

L&#39;obiettivo è quello di creare un bundle comune di [!DNL JavaScript] file necessari per tutte le pagine. In questo modo il browser deve caricare solo il bundle comune insieme a uno o più tipi di pagina specifici.

Apri un terminale in [!DNL Commerce] directory principale e utilizza il seguente comando per verificare di disporre di dipendenze da dividere in bundle separati:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Questo comando unisce e ordina le dipendenze rilevate nella `bundle/*.txt` file.  L&#39;output mostra anche il numero di file che contengono ogni dipendenza:

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

Questo risultato mostra che `buildTools` è una dipendenza in solo uno dei file bundle/*.txt. La `jquery/jquery.metadata` la dipendenza si trova in due (2) file e `es6-collections` è in tre (3) file.

Il nostro output mostra solo tre tipi di pagina (homepage, categoria e prodotto), che ci dicono:

- Tre dipendenze sono univoche per un solo tipo di pagina (mostrato dal numero 1).
- Si verificano altre tre dipendenze su due tipi di pagina (mostrato dal numero 2).
- Le ultime tre dipendenze sono comuni a tutti e tre i nostri tipi di pagina (mostrato dal numero 3).

Questo ci dice che probabilmente possiamo migliorare la velocità di caricamento delle pagine del nostro negozio suddividendo le nostre dipendenze in un bundle diverso, una volta che sappiamo quali tipi di pagina hanno bisogno di quali dipendenze.

#### 8\. Creare un file di distribuzione delle dipendenze

Per individuare i tipi di pagina necessari per le dipendenze, crea un nuovo file nel [!DNL Commerce] directory principale denominata `deps-map.sh` e copia nel codice seguente:

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

È inoltre possibile trovare lo script in [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Apri un terminale in [!DNL Commerce] directory principale ed esegui il file:

```bash
bash deps-map.sh
```

L&#39;output di questo script, applicato ai nostri tre tipi di pagina di esempio, dovrebbe essere simile al seguente (ma molto più a lungo):

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

Informazioni sufficienti per creare una configurazione dei bundle.

#### 9\. Crea bundle nel file build.js

Apri `build.js` file di configurazione e aggiungi i tuoi bundle al `modules` nodo. Ogni bundle deve definire le seguenti proprietà:

- `name`— il nome del bundle. Ad esempio, un nome di `bundles/cart` genera un `cart.js` in un pacchetto `bundles` sottodirectory.

- `create`— un flag booleano per creare il bundle (valori: `true` o `false`).

- `include`— un array di risorse (stringhe) incluse come dipendenze per la pagina. RequireJS traccia tutte le dipendenze e le include nel bundle, a meno che non sia escluso.

- `exclude`— un array di bundle o risorse da escludere dal bundle.

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

Questo esempio utilizza `mage/bootstrap` e `requirejs/require` risorse, dando priorità ai componenti e componenti più importanti che devono essere caricati in modo sincrono. I bundle presenti sono:

- `requirejs/require`- l&#39;unico bundle caricato in modo sincrono
- `mage/bootstrap`- il bundle bootstrap con i componenti dell&#39;interfaccia utente
- `bundles/default`—bundle predefinito richiesto per tutte le pagine
- `bundles/cart`—un bundle richiesto per la pagina del carrello
- `bundles/shipping`—bundle comune per il carrello e la pagina di pagamento (supponendo che il pagamento non venga mai aperto direttamente la pagina di pagamento si carica ancora più velocemente se la pagina del carrello è stata aperta in precedenza e il bundle di spedizione era già caricato)
- `bundles/checkout`—tutto per il pagamento
- `bundles/catalog`- tutto per le pagine di prodotti e categorie

### Parte 2: Generare bundle

I passaggi descritti di seguito descrivono il processo di base per la generazione di [!DNL Commerce] fasci. Puoi automatizzare questo processo nel modo desiderato, ma dovrai comunque utilizzare `nodejs` e `r.js` per generare effettivamente i vostri bundle. E se i tuoi temi hanno [!DNL JavaScript]- personalizzazioni correlate e non possono riutilizzare lo stesso `build.js` file, potrebbe essere necessario creare diversi `build.js` configurazioni per tema.

#### 1. Generare siti store statici

Prima di generare i bundle, esegui il comando di distribuzione statica:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Questo comando genera distribuzioni di archivi statici per ogni tema e impostazioni internazionali configurate. Ad esempio, se utilizzi il tema Luma e un tema personalizzato con impostazioni internazionali in inglese e francese, genererai quattro distribuzioni statiche:

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Per generare bundle per tutti i temi e le impostazioni internazionali dello store, ripeti passaggi seguenti per ogni tema e impostazione internazionale dello store.

#### 2. Spostare il contenuto dell&#39;archivio statico in una directory temporanea

Innanzitutto, devi spostare il contenuto statico dalla directory di destinazione ad una directory temporanea perché RequireJS sostituisce tutto il contenuto all’interno della directory di destinazione.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Ad esempio:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Esegui l&#39;ottimizzatore r.js

Quindi esegui l&#39;ottimizzatore r.js sul `build.js` file da [!DNL Commerce]La directory principale. I percorsi di tutte le directory e i file sono relativi alla directory di lavoro.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Questo comando genera i bundle in un `bundles` sottodirectory della directory di destinazione, che in questo caso si traduce in `pub/static/frontend/Magento/luma/en_US/bundles`.

L&#39;elenco dei contenuti della nuova directory del bundle potrebbe essere simile al seguente:

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4. Configurare RequireJS per utilizzare i bundle

Per ottenere che RequireJS utilizzi i tuoi bundle, aggiungi un `onModuleBundleComplete` callback dopo `modules` nel nodo `build.js` file:

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5. Esegui nuovamente il comando di distribuzione

Esegui il seguente comando per distribuire:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Apri `requirejs-config.js` in `pub/static/frontend/Magento/luma/en_US` directory per verificare che RequireJS abbia aggiunto il file con le chiamate di configurazione del bundling:

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>Durante la configurazione dei bundle, assicurati di inserire il `requirejs.config()` le chiamate nell&#39;ordine desiderato, in quanto vengono eseguite nell&#39;ordine in cui compaiono.

#### 6. Test dei risultati

Dopo il caricamento della pagina, osserva il browser che carica diverse dipendenze e bundle. Ad esempio, di seguito sono riportati i risultati del profilo &quot;Slow 3G&quot;:

![Due volte più veloce](../assets/performance/images/TwiceAsFast.png)

Il tempo di caricamento della pagina per una home page vuota è ora due volte più veloce rispetto all’utilizzo della pagina nativa [!DNL Commerce] in bundle. Ma possiamo fare ancora meglio.

#### 7. Ottimizzare i bundle

Anche se gzip, il [!DNL JavaScript] i file sono ancora grandi. Miniizzali con RequireJS, che utilizza uglifier per la minimizzazione [!DNL JavaScript] a buon risultato.

Per abilitare l&#39;ottimizzatore nel tuo `build.js` file, aggiungi `uglify2` come valore della proprietà optimize nella parte superiore della `build.js` file:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

I risultati possono essere significativi:
![Tre volte più veloce](../assets/performance/images/ThreeTimesFaster.png)

I tempi di caricamento sono tre volte più veloci rispetto a quelli dei file nativi [!DNL Commerce] in bundle.
