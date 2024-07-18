---
title: Avanzato [!DNL JavaScript] Bundling
description: Scopri come il bundling di JavaScript può ridurre le dimensioni e la frequenza delle richieste del server.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: f9f8aea1a77ef062d7076a61bbafd12433f15edf
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Bundling [!DNL JavaScript] avanzato

Il raggruppamento di [!DNL JavaScript] moduli per ottenere prestazioni migliori consiste nel ridurre due elementi:

1. Numero di richieste server.
1. Dimensione di tali richieste server.

In un’applicazione modulare, il numero di richieste server può raggiungere le centinaia. Ad esempio, la schermata seguente mostra solo l&#39;inizio dell&#39;elenco dei moduli [!DNL JavaScript] caricati nella home page di un&#39;installazione pulita.

![Nessun bundle](../assets/performance/images/noBundling.png)

## Unione e raggruppamento

Per ridurre il numero di richieste server, [!DNL Commerce] offre due modi predefiniti: unione e bundling. Queste impostazioni sono disattivate per impostazione predefinita. Puoi attivarli all&#39;interno dell&#39;interfaccia utente di amministrazione in **[!UICONTROL Stores]** > **Impostazioni** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** o dalla riga di comando.

![Bundling](../assets/performance/images/bundlingImage.png)

### Raggruppamento di base

Per abilitare il bundling incorporato dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Questo è un meccanismo nativo di [!DNL Commerce] che combina tutte le risorse presenti nel sistema e le distribuisce tra bundle delle stesse dimensioni (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] raggruppamento](../assets/performance/images/magentoBundling.png)

Meglio, ma il browser carica ancora TUTTI i bundle [!DNL JavaScript], non solo quelli necessari.

Il bundle [!DNL Commerce] riduce il numero di connessioni per pagina, ma per ogni richiesta di pagina carica tutti i bundle, anche quando la pagina richiesta può dipendere solo da file all&#39;interno di uno o due dei bundle. Le prestazioni migliorano dopo che il browser memorizza in cache i bundle. Tuttavia, poiché il browser carica questi bundle in modo sincrono, la prima visita dell&#39;utente a una vetrina [!DNL Commerce] potrebbe richiedere del tempo per il rendering e danneggiare l&#39;esperienza utente.

### Unione di base

Per abilitare l&#39;unione incorporata dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Questo comando unisce tutti i file [!DNL JavaScript] sincroni in un unico file. L&#39;abilitazione dell&#39;unione senza abilitare anche il bundling non è utile perché [!DNL Commerce] utilizza RequireJS. Se non si abilita il bundle, [!DNL Commerce] unisce solo RequireJS e la relativa configurazione. Quando si abilita sia l&#39;unione che il raggruppamento, [!DNL Commerce] crea un singolo file [!DNL JavaScript]:

![Unione reale](../assets/performance/images/magentoMergingDevWorld.png)

## Tempi di rendering reali

I precedenti tempi di caricamento in bundle e uniti sono molto simili in un ambiente di sviluppo. Ma nel mondo reale, molte cose possono rallentare il rendering: connessioni lente, soglie di connessione grandi, reti limitate. Inoltre, i dispositivi mobili non eseguono il rendering alla stessa velocità dei desktop.

Per testare e preparare la tua distribuzione in vetrina per il mondo reale, ti consigliamo di testare con il profilo di limitazione nativo di Chrome &quot;Slow 3G&quot;. Con Slow 3G, i nostri precedenti tempi di output in bundle ora riflettono le realtà di connessione di molti utenti:

![Bundling reale](../assets/performance/images/magentoBundlingRealWorld.png)

Con la connettività Slow 3G, sono necessari circa 44 secondi per caricare tutti i bundle per la home page di un&#39;installazione pulita di [!DNL Commerce].

Lo stesso vale quando si uniscono i bundle in un singolo file. Gli utenti possono ancora attendere circa 42 secondi per il caricamento iniziale della pagina, come illustrato di seguito:

![Unione reale](../assets/performance/images/magentoMergingRealWorld.png)

Con un approccio più avanzato al bundle [!DNL JavaScript], possiamo migliorare questi tempi di caricamento.

## Bundling avanzato

Ricorda che l&#39;obiettivo del bundling [!DNL JavaScript] è di ridurre il numero e le dimensioni delle risorse richieste per ogni pagina caricata nel browser. Per farlo, vogliamo creare i nostri bundle in modo che ogni pagina nel nostro store debba scaricare solo un bundle comune e un bundle specifico per ogni pagina a cui si accede.

Un modo per ottenere questo risultato è definire i bundle per tipo di pagina. È possibile categorizzare le pagine di [!DNL Commerce] in diversi tipi di pagina, tra cui Categoria, Prodotto, CMS, Cliente, Carrello e Pagamento. Ogni pagina categorizzata in uno di questi tipi di pagina ha un set diverso di dipendenze del modulo RequireJS. Quando si raggruppano i moduli RequireJS per tipo di pagina, si otterrà solo una manciata di bundle che coprono le dipendenze di qualsiasi pagina del negozio.

Ad esempio, potresti ottenere un bundle per le dipendenze comuni a tutte le pagine, un bundle per le pagine solo CMS, un bundle per le pagine solo catalogo, un altro bundle per le pagine solo ricerca e un bundle per le pagine Pagamento.

Puoi anche creare bundle in base allo scopo: per caratteristiche comuni, funzioni relative ai prodotti, funzioni di spedizione, funzioni di pagamento, imposte e convalide di moduli. Sta a te definire come definire i bundle e la struttura del tuo negozio. Potresti notare che alcune strategie di bundling funzionano meglio di altre.

Un&#39;installazione pulita di [!DNL Commerce] consente di ottenere prestazioni sufficienti suddividendo i bundle per tipo di pagina, ma alcune personalizzazioni potrebbero richiedere un&#39;analisi più approfondita e altre distribuzioni di risorse.

### Strumenti richiesti

I seguenti passaggi richiedono l’installazione di e di avere familiarità con i seguenti strumenti:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) (facoltativo)

### Codice di esempio

Le versioni complete del codice di esempio utilizzato in questo articolo sono disponibili qui:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Parte 1: Creare una configurazione di bundling

#### 1\. Aggiungere un file build.js

Creare un file `build.js` nella directory principale [!DNL Commerce]. Questo file contiene l’intera configurazione della build per i bundle.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

In seguito, cambieremo l&#39;impostazione `optimize:` da_ `none` a `uglify2` per minimizzare l&#39;output del bundle. Tuttavia, per il momento, durante lo sviluppo, puoi lasciarla impostata su `none` per garantire build più veloci.

#### 2\. Aggiungere dipendenze, shim, percorsi e mappe RequireJS

Aggiungi i seguenti nodi di configurazione della build RequireJS, `deps`, `shim`, `paths` e `map`, al file di build:

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

#### 3\. Aggregare i valori dell’istanza requirements-config.js

In questo passaggio sarà necessario aggregare tutti i più nodi di configurazione `deps`, `shim`, `paths` e `map` dal file `requirejs-config.js` dell&#39;archivio nei nodi corrispondenti nel file `build.js`. A tale scopo, è possibile aprire la scheda **[!UICONTROL Network]** nel pannello Strumenti per sviluppatori del browser e passare a qualsiasi pagina dell&#39;archivio, ad esempio la home page. Nella scheda Rete verrà visualizzata l&#39;istanza del file `requirejs-config.js` del tuo archivio nella parte superiore, evidenziata qui:

![Configurazione RequireJS](../assets/performance/images/RequireJSConfig.png)

In questo file sono disponibili più voci per ciascuno dei nodi di configurazione (`deps`, `shim`, `paths`, `map`). Devi aggregare questi valori su più nodi nel singolo nodo di configurazione del file build.js. Ad esempio, se l&#39;istanza `requirejs-config.js` dell&#39;archivio contiene voci per 15 nodi `map` separati, sarà necessario unire le voci per tutti i 15 nodi nel singolo nodo `map` nel file `build.js`. Lo stesso vale per i nodi `deps`, `shim` e `paths`. Senza uno script per automatizzare questo processo, potrebbe richiedere tempo.

È necessario modificare il percorso `mage/requirejs/text` in `requirejs/text` nel nodo di configurazione `paths` come segue:

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4. Aggiungi un nodo di moduli

Alla fine del file `build.js`, aggiungi l&#39;array module[] come segnaposto per i bundle che definirai per la vetrina in un secondo momento.

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

#### 5. Recuperare le dipendenze RequireJS

Puoi recuperare tutte le dipendenze del modulo [!DNL RequireJS] dai tipi di pagina del tuo store utilizzando:

1. [!DNL PhantomJS] dalla riga di comando (supponendo che sia installato [!DNL PhantomJS]).
1. RequireJS nella console del browser.

#### Per utilizzare [!DNL PhantomJS]:

Nella directory principale [!DNL Commerce], creare un nuovo file denominato `deps.js` e copiarlo nel codice seguente. Questo codice utilizza [!DNL [!DNL PhantomJS]] per aprire una pagina e attendere che il browser carichi tutte le risorse di pagina. Quindi restituisce tutte le dipendenze [!DNL RequireJS] per una determinata pagina.

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

Aprire un terminale all&#39;interno della directory principale [!DNL Commerce] ed eseguire lo script per ogni pagina dell&#39;archivio che rappresenta un tipo di pagina specifico:

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-presentation-pagetype-dependencies</i>
</pre>

Ad esempio, ecco quattro pagine dell’archivio esempi a tema Luma che rappresentano i quattro tipi di pagina che utilizzeremo per creare i nostri quattro bundle (homepage, categoria, prodotto, carrello):

```
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### Per utilizzare la console del browser:

Se non desideri utilizzare [!DNL PhantomJS], puoi eseguire il seguente comando dalla console del browser durante la visualizzazione di ogni tipo di pagina nella vetrina:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Questo comando (utilizzato nello script [!DNL PhantomJS]) crea lo stesso elenco di dipendenze [!DNL RequireJS] e le visualizza nella console del browser. Lo svantaggio di questo approccio è che dovrai creare un pacchetto personalizzato o file di testo di tipo pagina.

#### 6. Formattare e filtrare l’output

Dopo aver unito le dipendenze [!DNL RequireJS] in file di testo di tipo pagina, è possibile utilizzare il comando seguente in ogni file di dipendenza di tipo pagina per sostituire le virgole nei file con nuove righe:

```bash
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

È inoltre necessario rimuovere tutti i mixin per ciascun file perché i mixin duplicano le dipendenze. Utilizza il seguente comando su ciascun file di dipendenza:

```bash
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7. Identificare bundle univoci e comuni

L&#39;obiettivo è creare un bundle comune di [!DNL JavaScript] file necessari per tutte le pagine. In questo modo il browser deve caricare solo il bundle comune insieme a uno o più tipi di pagina specifici.

Aprire un terminale nella directory principale [!DNL Commerce] e utilizzare il comando seguente per verificare che siano presenti dipendenze che è possibile suddividere in bundle separati:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Questo comando unisce e ordina le dipendenze trovate nei file `bundle/*.txt`.  L’output mostra anche il numero di file che contengono ciascuna dipendenza:

```
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

Questo output mostra che `buildTools` è una dipendenza in uno solo dei file bundle/*.txt. La dipendenza `jquery/jquery.metadata` è in due (2) file e `es6-collections` è in tre (3) file.

L’output mostra solo tre tipi di pagina (home page, categoria e prodotto), che indicano:

- Tre dipendenze sono univoche per un solo tipo di pagina (mostrato dal numero 1).
- Altre tre dipendenze si verificano su due tipi di pagina (mostrati dal numero 2).
- Le ultime tre dipendenze sono comuni a tutti e tre i tipi di pagina (mostrati dal numero 3).

Questo ci dice che probabilmente possiamo migliorare le velocità di caricamento delle pagine del nostro negozio suddividendo le nostre dipendenze in un bundle diverso, una volta che sappiamo quali tipi di pagina hanno bisogno di quali dipendenze.

#### 8. Creare un file di distribuzione delle dipendenze

Per individuare i tipi di pagina necessari per le dipendenze, creare un nuovo file nella directory principale [!DNL Commerce] denominata `deps-map.sh` e copiarlo nel codice seguente:

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

Puoi anche trovare lo script in [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Aprire un terminale nella directory principale [!DNL Commerce] ed eseguire il file:

```bash
bash deps-map.sh
```

L’output di questo script, applicato ai tre tipi di pagina di esempio, dovrebbe essere simile al seguente (ma molto più lungo):

```
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

Queste informazioni sono sufficienti per creare una configurazione di bundle.

#### 9. Creare bundle nel file build.js

Apri il file di configurazione `build.js` e aggiungi i bundle al nodo `modules`. Ogni bundle deve definire le seguenti proprietà:

- `name`: nome del bundle. Ad esempio, un nome di `bundles/cart` genera un bundle `cart.js` in una sottodirectory `bundles`.

- `create`: un flag booleano per creare il bundle (valori: `true` o `false`).

- `include`: un array di risorse (stringhe) incluse come dipendenze per la pagina. RequireJS traccia tutte le dipendenze e le include nel bundle, a meno che non siano escluse.

- `exclude`: array di bundle o risorse da escludere dal bundle.

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

In questo esempio vengono riutilizzate `mage/bootstrap` e `requirejs/require` risorse, assegnando maggiore priorità ai componenti più importanti e ai componenti da caricare in modo sincrono. I bundle presenti sono:

- `requirejs/require`: l&#39;unico bundle caricato in modo sincrono
- `mage/bootstrap`: il bundle di bootstrap con i componenti dell&#39;interfaccia utente
- `bundles/default`: bundle predefinito richiesto per tutte le pagine
- `bundles/cart`: bundle richiesto per la pagina carrello
- `bundles/shipping`: bundle comune per il carrello e la pagina di pagamento (supponendo che il pagamento non venga mai aperto direttamente, la pagina di pagamento viene caricata ancora più velocemente se la pagina del carrello è stata aperta in precedenza e il bundle di spedizione è già stato caricato)
- `bundles/checkout`—tutto per il pagamento
- `bundles/catalog`—tutto per le pagine di prodotti e categorie

### Parte 2: generare i bundle

I passaggi seguenti descrivono il processo di base per la generazione di bundle [!DNL Commerce] più efficienti. Puoi automatizzare questo processo come preferisci, ma dovrai comunque utilizzare `nodejs` e `r.js` per generare effettivamente i bundle. E se i temi hanno personalizzazioni relative a [!DNL JavaScript] e non possono riutilizzare lo stesso file `build.js`, potrebbe essere necessario creare diverse `build.js` configurazioni per tema.

#### 1. Generare siti di archiviazione statici

Prima di generare i bundle, esegui il comando di distribuzione statica:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Questo comando genera distribuzioni statiche dell&#39;archivio per ogni tema e lingua impostati. Ad esempio, se utilizzi il tema Luma e un tema personalizzato con le lingue in inglese e francese, puoi generare quattro distribuzioni statiche:

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Per generare bundle per tutti i temi e le impostazioni internazionali dello store, ripeti i passaggi seguenti per ciascun tema e ciascuna impostazione locale dello store.

#### 2. Spostare il contenuto dell&#39;archivio statico in una directory temporanea

Innanzitutto, devi spostare il contenuto statico dalla directory di destinazione ad una directory temporanea perché RequireJS sostituisce tutto il contenuto all’interno della directory di destinazione.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Ad esempio:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Eseguire r.js optimizer

Eseguire quindi r.js optimizer sul file `build.js` dalla directory radice di [!DNL Commerce]. I percorsi di tutte le directory e dei file sono relativi alla directory di lavoro.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Questo comando genera i bundle in una sottodirectory `bundles` della directory di destinazione, che in questo caso restituisce `pub/static/frontend/Magento/luma/en_US/bundles`.

L’elenco dei contenuti della nuova directory del bundle potrebbe essere simile al seguente:

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4. Configurare RequireJS per l’utilizzo dei bundle

Per ottenere RequireJS per utilizzare i bundle, aggiungi un callback `onModuleBundleComplete` dopo il nodo `modules` nel file `build.js`:

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

#### 5. Rieseguire il comando di distribuzione

Esegui il comando seguente per distribuire:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Apri `requirejs-config.js` nella directory `pub/static/frontend/Magento/luma/en_US` per verificare che RequireJS abbia aggiunto il file con le chiamate di configurazione bundling:

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
>Durante la configurazione dei bundle, assicurati di inserire le chiamate `requirejs.config()` nell&#39;ordine in cui desideri che vengano eseguite, in quanto le chiamate vengono eseguite nell&#39;ordine in cui compaiono.

#### 6. Verificare i risultati

Una volta caricata la pagina, noterai che il browser sta caricando diverse dipendenze e bundle. Ad esempio, di seguito sono riportati i risultati per il profilo &quot;Slow 3G&quot;:

![Velocità doppia](../assets/performance/images/TwiceAsFast.png)

Il tempo di caricamento della pagina per una home page vuota è ora il doppio rispetto all&#39;utilizzo del bundling nativo [!DNL Commerce]. Ma possiamo fare ancora meglio.

#### 7. Ottimizzare i bundle

Anche se sono compressi, i file [!DNL JavaScript] sono ancora grandi. Minimizzarli con RequireJS, che utilizza un uglifier per minimizzare [!DNL JavaScript] e ottenere buoni risultati.

Per abilitare l&#39;ottimizzatore nel file `build.js`, aggiungere `uglify2` come valore per la proprietà di ottimizzazione nella parte superiore del file `build.js`:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

I risultati possono essere significativi:
![Tre volte più veloce](../assets/performance/images/ThreeTimesFaster.png)

I tempi di caricamento sono ora tre volte più veloci rispetto al bundling nativo di [!DNL Commerce].
