---
title: Dizionari di traduzione e pacchetti linguistici
description: Scopri come generare dizionari di traduzione e pacchetti linguistici.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---

# Localizzazione

{{file-system-owner}}

Le traduzioni Commerce ti consentono di personalizzare e localizzare il tuo negozio per più aree geografiche e mercati generando:

- **Dizionari di traduzione**, che sono un modo pratico per personalizzare o tradurre _alcuni_ parole e frasi, ad esempio quelle per un modulo o un tema personalizzato.
- **Pacchetti per lingua** che ti consentono di tradurre _uno o tutti_ parole e frasi nell’applicazione Commerce.

Consulta [Panoramica sulle traduzioni].

## Generare un dizionario di traduzione

Puoi generare un [dizionario di traduzione] per personalizzare le stringhe esistenti, traduci parole e frasi in un modulo personalizzato, localizza un tema o crea pacchetti di lingue.

Per iniziare la traduzione, utilizza un comando per generare un file CSV del dizionario con un elenco di tutte le frasi e parole esistenti.

Per generare il dizionario e avviare la traduzione:

1. Estrai termini e frasi traducibili dai componenti abilitati utilizzando il comando raccolta di traduzioni. Il contenuto viene estratto in un file CSV.
1. Traduci parole e frasi esistenti. Se necessario, puoi aggiungere altri termini personalizzati.

   Sono disponibili opzioni per l’utilizzo del dizionario tradotto:

1. Puoi creare un pacchetto dei dizionari di traduzione in un pacchetto per lingua e fornirlo all’amministratore di Commerce Store.

1. Nell’amministratore, l’amministratore dello store [configura le traduzioni].

Opzioni comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

Nella tabella seguente vengono illustrati i parametri e i valori:

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `<path to directory to translate>` | Percorso di una directory che contiene codice traducibile, ovvero file PHP, PHTML o XML con frasi da tradurre.<br><br>Lo strumento inizia la ricerca nel percorso immesso e cerca tutti i file e le sottodirectory in esso contenuti.<br><br>Non utilizzare questo parametro se si utilizza `-m --magento`. | Sì (dizionari), no (pacchetti). |
| `-m --magento` | Necessario per creare un pacchetto lingua da questo dizionario di traduzione. Se utilizzato, esegue la ricerca nelle directory che contengono bin/magento. Questa opzione aggiunge temi o moduli a ogni riga del dizionario.<br><br>Di seguito è riportato un esempio:<br><br>&quot;Nessun elemento trovato&quot;,&quot;Nessun elemento trovato&quot;,modulo,Magento_Wishlist | No |
| `-o --output="<path>"` | Specifica il percorso assoluto del file system e il nome del file CSV del dizionario di traduzione da creare. Il valore immesso fa distinzione tra maiuscole e minuscole. Il nome del file CSV deve corrispondere esattamente al nome delle impostazioni internazionali, comprese le lettere maiuscole e minuscole.<br><br>Se si omette questo parametro, l&#39;output viene indirizzato a stdout. | No |

>[!INFO]
>
>Per creare un Language Pack da un dizionario di traduzione, _deve_ utilizzare il `-m|--magento` opzione.

### Linee guida per la traduzione

Utilizza le seguenti linee guida per tradurre parole e frasi:

- Modificare solo il contenuto della seconda colonna. Traduci le frasi da Inglese (`US`) alla lingua desiderata.
- Quando crei dizionari per le lingue, utilizza le stringhe Commerce predefinite.
- Durante la traduzione, presta attenzione ai segnaposto: `%1`, `%2`

Commerce utilizza i segnaposto per inserire valori contestuali; sono _non_ utilizzato per le traduzioni. Ad esempio:

```text
Product '%1' has been added to shopping cart.
```

Popola con un valore:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

La frase risultante deve contenere almeno uno di ciascun segnaposto. Si supponga, ad esempio, che siano presenti segnaposto da `%1` a `%3` nella frase originale. La traduzione può avere un numero illimitato di segnaposto in qualsiasi ordine, ma deve esserci almeno un&#39;occorrenza di `%1`, `%2`, e `%3`. La traduzione non può contenere valori segnaposto non presenti nel valore originale (ad esempio, `%4`, `%5`e così via).

Un esempio di traduzione di una frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Creare un pacchetto lingua

Al contrario di un dizionario di traduzione, puoi tradurre qualsiasi parola o tutte le parole e le frasi nell’applicazione Commerce utilizzando un pacchetto lingua. È possibile tradurre un particolare componente, come un modulo o un tema, utilizzando un dizionario di traduzione. [Ulteriori informazioni sui pacchetti per lingua].

Questa sezione illustra come creare un pacchetto per la lingua, che scrive i file CSV in moduli e temi. Per creare un pacchetto lingua, è necessario eseguire le attività descritte nelle sezioni seguenti:

1. [Raccogliere e tradurre parole e frasi](#generate-a-translation-dictionary). (Il `--magento` è obbligatorio.)
1. [Esegui il comando del pacchetto lingua](#run-the-language-package-command).
1. [Creare directory e file](#create-directories-and-files).
1. (Facoltativo.) [Configurare più pacchetti per una lingua](#configure-multiple-packages-for-a-language).

### Esegui il comando del pacchetto lingua

Utilizzo comando:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

Nella tabella seguente vengono illustrati i parametri e i valori per il comando Language Package:

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `<source>` | Percorso assoluto del file system e nome file di un file CSV che contiene il dizionario di traduzione combinato e le metainformazioni necessarie per la suddivisione in un pacchetto lingua.<br><br>Utilizzare [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) per creare il file CSV, quindi crea il pacchetto lingua come descritto in [Creare directory e file](#m2devgde-xlate-files). | Sì |
| `<locale>` | [ISO 639-1] (lingua) e [ISO 3166] (paese) identificatore della lingua utilizzata come nome file per tutti i file CSV risultanti. Esempi: `de_DE`, `pt_PT`, `pt_BR`. | Sì |
| `-m --mode` | Se esiste un file di destinazione, specifica se sostituire il pacchetto lingua esistente o unire con il nuovo Language Pack. L’unione sostituisce tutte le frasi esistenti e ne aggiunge di nuove.<br><br>Valori: unisci o sostituisci (impostazione predefinita). | No |
| `-d --allow-duplicates` | Includi questa opzione per consentire i duplicati nel Language Pack. In caso contrario, il comando non riesce se rileva la stessa frase in più voci con traduzioni diverse. | No |

### Creare directory e file

I pacchetti di lingua si trovano in una directory in `app/i18n/<VendorName>` nel file system di Commerce con i seguenti contenuti:

- File di licenza richiesti
- `composer.json`
- `registration.php` che [registri] il pacchetto lingua
- [`language.xml`](#language-package-languagexml) file di metadati

>[!INFO]
>
>L&#39;intero percorso deve essere scritto in minuscolo. Ad esempio, consulta [`de_de`].

Per creare questi file:

1. Creare una directory in `app/i18n`.

   Ad esempio, i pacchetti per lingua Commerce si trovano in `app/i18n/magento`

1. Aggiungi i file di licenza richiesti.
1. Aggiungi [`composer.json`] che specifica le dipendenze per il pacchetto lingua.
1. Registrare il pacchetto lingua con [`registration.php`]
1. Aggiungi `language.xml` file di metadati, come descritto nella sezione successiva.

#### Language.xml del pacchetto lingua

Quando si dichiara un pacchetto lingua in `language.xml` file di configurazione, è necessario specificare la sequenza dell&#39;ereditarietà della lingua per questo pacchetto.

L’ereditarietà della lingua consente di creare una traduzione denominata _secondario_ in base a una traduzione esistente denominata _principale_. Le traduzioni secondarie hanno la precedenza su quelle principali. Tuttavia, se la traduzione secondaria non viene caricata o visualizzata o manca una frase o una parola, Commerce utilizza le impostazioni locali principali. [Esempi di ereditarietà dei pacchetti di linguaggio](#example-of-language-inheritance).

Per dichiarare un pacchetto, specificare le informazioni seguenti:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Dove:

- `code`- Impostazioni locali del pacchetto lingua (obbligatorio)
- `vendor`- Nome del fornitore del modulo (obbligatorio)
- `package`- Nome pacchetto lingua (obbligatorio)
- `sort_order`- Priorità di caricamento di un pacchetto quando sono disponibili diversi pacchetti di lingue per uno store
- `use`- Impostazioni locali del pacchetto lingua padre da cui ereditare i dizionari

Se necessario, puoi specificare diversi pacchetti principali. I pacchetti padre vengono applicati in base al primo elenco utilizzato.

#### Esempio di ereditarietà del linguaggio

Supponiamo che un pacchetto di linguaggio erediti da altri due pacchetti e che questi pacchetti abbiano anche pacchetti padre e &quot;nonno&quot;.

Se un pacchetto di linguaggio eredita da due pacchetti, `language.xml` potrebbe essere simile al seguente:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

Nell’esempio precedente:

- `language_package_one` eredita da `en_au_package` e `en_au_package` eredita da `en_ie_package`
- `language_package_two` eredita da `en_ca_package` e `en_ca_package` eredita da `en_us_package`

Se l’applicazione Commerce non è in grado di trovare una parola o una frase nel `en_GB` pacchetto, cerca in altri pacchetti nella seguente sequenza:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

La specifica di tutte le ereditarietà tra i pacchetti di linguaggio potrebbe causare la creazione di catene di ereditarietà circolari. Utilizzare [Magento\Test\Integrity\App\Language\CircularDependencyTest] per individuare e correggere tali catene.

### Configurare più pacchetti per una lingua

Per rendere il tuo negozio più flessibile, puoi caricare diversi pacchetti linguistici per la stessa lingua nel tuo negozio. Pertanto, puoi utilizzare pacchetti personalizzati diversi per parti diverse del tuo archivio, perché il sistema compila un singolo pacchetto da tutti i pacchetti disponibili per una lingua.

Per abilitare un pacchetto aggiuntivo per una lingua esistente, assegna al nuovo pacchetto un nome qualsiasi ad eccezione del nome di un codice della lingua esistente (per evitare confusione). Specificare le configurazioni di un pacchetto nel file del pacchetto lingua `language.xml` file di metadati, come descritto nella sezione successiva.

## Esempi di utilizzo dei comandi di traduzione

Nelle sezioni seguenti vengono forniti esempi end-to-end dell&#39;utilizzo dei comandi descritti in questo argomento per creare dizionari di traduzione e pacchetti di traduzione:

### Esempio: creare un dizionario di traduzione per un modulo o un tema

Per aggiungere una traduzione in tedesco a un modulo o a un tema che desideri distribuire ad altri commercianti:

1. Raccogli frasi dal modulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Il nome del file CSV deve _corrisponde esattamente_ le impostazioni locali, comprese le lettere maiuscole e minuscole dei caratteri.

1. Traduci parole e frasi utilizzando [le presenti linee guida](#translation-guidelines).
1. Se necessario, copia `xx_YY.csv` a `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` o nella directory dei temi del modulo (a seconda che il dizionario di traduzione sia per un modulo o per un tema).

### Esempio: creare un pacchetto lingua

Come nell’esempio precedente, genera un file CSV, ma invece di specificare un modulo o una directory tematica, specifica l’intera directory principale dell’applicazione Commerce. Il file CSV risultante contiene tutte le frasi che il comando potrebbe trovare nel codice.

1. Raccogli frasi dal modulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Il nome del file CSV deve _corrisponde esattamente_ le impostazioni locali, comprese le lettere maiuscole e minuscole dei caratteri.

1. Traduci parole e frasi utilizzando [le presenti linee guida](#translation-guidelines).
1. Crea il pacchetto lingua.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Crea una directory per il pacchetto lingua.

   Ad esempio: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. In tale directory, aggiungi quanto segue:

   - Una licenza, se necessario
   - `composer.json` (esempio seguente)
   - `registration.php` (esempio seguente)
   - `language.xml` (esempio seguente)

   **Esempio`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Esempio`registration.php`**:

   ```php
   <?php
   /**
    * Copyright &copy; Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Esempio`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright &copy; Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Panoramica sulle traduzioni]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[dizionario di traduzione]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configura le traduzioni]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Ulteriori informazioni sui pacchetti per lingua]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registri]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[&quot;de_de&quot;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[&quot;compositore.json&quot;]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[&quot;registration.php&quot;]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
