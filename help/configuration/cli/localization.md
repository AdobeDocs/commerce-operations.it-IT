---
title: Dizionari di traduzione e pacchetti di lingue
description: Scopri come generare dizionari di traduzione e generare pacchetti di lingue.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---


# Localizzazione

{{file-system-owner}}

Le traduzioni commerciali consentono di personalizzare e localizzare il negozio per più aree geografiche e mercati generando:

- **Dizionari di traduzione**, che sono un modo conveniente per personalizzare o tradurre _alcuni_ parole e frasi, ad esempio quelle per un modulo o un tema personalizzato.
- **Pacchetti per lingua** che ti permettono di tradurre _qualsiasi_ parole e frasi nell’applicazione Commerce.

Vedi [Panoramica sulle traduzioni].

## Generare un dizionario di traduzione

Puoi generare una [dizionario di traduzione] per personalizzare le stringhe esistenti, tradurre parole e frasi in un modulo personalizzato, localizzare un tema o creare pacchetti di lingue.

Per iniziare a tradurre, utilizza un comando per generare un file CSV del dizionario con un elenco raccolto di tutte le frasi e le parole esistenti.

Per generare il dizionario e iniziare la traduzione:

1. Estrarre parole e frasi traducibili dai componenti abilitati utilizzando il comando di raccolta di traduzione. Il contenuto viene estratto in un file CSV.
1. Traduci le parole e le frasi esistenti. Se necessario, puoi aggiungere altri termini personalizzati.

   Sono disponibili opzioni per l&#39;utilizzo del dizionario tradotto:

1. Puoi creare un pacchetto con i dizionari di traduzione in un pacchetto linguistico e fornire il pacchetto all’amministratore di Commerce Store.

1. Nell’amministratore, l’amministratore dello store [configura le traduzioni].

Opzioni di comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

Nella tabella seguente sono illustrati parametri e valori:

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `<path to directory to translate>` | Percorso di una directory con codice traducibile; in altre parole, file PHP, PHTML o XML con frasi da tradurre.<br><br>Lo strumento inizia a cercare il percorso inserito e cerca tutti i file e le sottodirectory che contiene.<br><br>Non utilizzare questo parametro se utilizzi `-m --magento`. | Sì (dizionari), no (pacchetti). |
| `-m --magento` | Obbligatorio per creare un pacchetto di lingue da questo dizionario di traduzione. Se utilizzato, cerca nelle directory che contengono bin/magento. Questa opzione aggiunge temi o moduli a ogni riga del dizionario.<br><br>Segue un esempio:<br><br>&quot;Nessun elemento trovato&quot;,&quot;Nessun elemento trovato&quot;, modulo,elenco_Magento | No |
| `-o --output="<path>"` | Specifica il percorso assoluto del file system e il nome file del file CSV del dizionario di traduzione da creare. Il valore inserito fa distinzione tra maiuscole e minuscole. Il nome del file CSV deve corrispondere esattamente al nome delle impostazioni internazionali, comprese le maiuscole in minuscole e viceversa.<br><br>Se si omette questo parametro, l&#39;output viene indirizzato a stdout. | No |

>[!INFO]
>
>Per creare un Language Pack da un dizionario di traduzione, è necessario _deve_ utilizza `-m|--magento` opzione .

### Linee guida sulla traduzione

Per tradurre parole e frasi, attenersi alle seguenti linee guida:

- Modifica solo il contenuto della seconda colonna. Traduci le frasi dall&#39;inglese (`US`) nella lingua desiderata.
- Quando crei dizionari per le impostazioni internazionali, utilizza le stringhe Commerce predefinite.
- Durante la traduzione, prestare attenzione ai segnaposto: `%1`, `%2`

Commerce utilizza i segnaposto per inserire valori di contesto; sono _not_ utilizzato per le traduzioni. Ad esempio:

```text
Product '%1' has been added to shopping cart.
```

Popola con un valore:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

La frase risultante deve contenere almeno un segnaposto. Ad esempio, supponiamo che siano presenti segnaposto da `%1` a `%3` nella frase originale. La traduzione può avere tanti di questi segnaposto in qualsiasi ordine, ma ci deve essere almeno una occorrenza di `%1`, `%2`e `%3`. La traduzione non può contenere valori segnaposto non presenti nel valore originale (ad esempio, `%4`, `%5`e così via).

Esempio di traduzione di una frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Creare un pacchetto linguistico

Al contrario di un dizionario di traduzione, è possibile tradurre qualsiasi o tutte le parole e frasi nell&#39;applicazione Commerce utilizzando un pacchetto di lingue. Puoi tradurre un particolare componente, come un modulo o un tema, utilizzando un dizionario di traduzione. [Ulteriori informazioni sui pacchetti linguistici].

Questa sezione illustra come creare un pacchetto linguistico, che scrive file CSV in moduli e temi. Per creare un pacchetto linguistico, è necessario eseguire le attività descritte nelle sezioni seguenti:

1. [Raccogliere e tradurre parole e frasi](#generate-a-translation-dictionary). (2) `--magento` è obbligatorio.)
1. [Esegui il comando pacchetto linguistico](#run-the-language-package-command).
1. [Creare directory e file](#create-directories-and-files).
1. (Facoltativo) [Configurare più pacchetti per una lingua](#configure-multiple-packages-for-a-language).

### Esegui il comando pacchetto linguistico

Utilizzo comando:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

Nella tabella seguente sono illustrati i parametri e i valori del comando Language Package:

| Parametro | Valore | Obbligatorio |
|--- |--- |--- |
| `<source>` | Percorso assoluto del file system e nome file di un file CSV contenente il dizionario di traduzione combinato e le meta-informazioni necessarie per la suddivisione in un pacchetto linguistico.<br><br>Utilizzo [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) per creare il file CSV, crea il pacchetto linguistico come descritto in [Creare directory e file](#m2devgde-xlate-files). | Sì |
| `<locale>` | [ISO 639-1] (lingua) e [ISO 3166] (Paese) identificatore della lingua utilizzata come nome file per tutti i file CSV risultanti. Esempi: `de_DE`, `pt_PT`, `pt_BR`. | Sì |
| `-m --mode` | Se esiste un file di destinazione, specifica se sostituire il pacchetto lingua esistente o unirlo al nuovo Language Pack. L’unione ignora tutte le frasi esistenti e ne aggiunge di nuove.<br><br>Valori: merge o replace (predefinito). | No |
| `-d --allow-duplicates` | Includi questa opzione per consentire i duplicati nel Language Pack. In caso contrario, il comando non riesce con un errore se incontra la stessa frase in più voci con traduzioni diverse. | No |

### Creare directory e file

I pacchetti di lingua si trovano in una directory sotto `app/i18n/<VendorName>` nel file system Commerce con i seguenti contenuti:

- File di licenza richiesti
- `composer.json`
- `registration.php` che [registri] il pacchetto linguistico
- [`language.xml`](#language-package-languagexml) file meta-informazioni

>[!INFO]
>
>Devi abbassare l’intero percorso. Ad esempio, vedi [`de_de`].

Per creare questi file:

1. Crea una directory in `app/i18n`.

   Ad esempio, i pacchetti di Commerce Language si trovano in `app/i18n/magento`

1. Aggiungi i file di licenza richiesti.
1. Aggiungi [`composer.json`] specifica le dipendenze per il pacchetto linguistico.
1. Registra il pacchetto linguistico con [`registration.php`]
1. Aggiungi `language.xml` file meta-informazioni come descritto nella sezione successiva.

#### Language.xml del pacchetto linguistico

Quando si dichiara un pacchetto linguistico nel `language.xml` file di configurazione, è necessario specificare la sequenza dell&#39;ereditarietà della lingua per questo pacchetto.

L’ereditarietà della lingua consente di creare una traduzione denominata _bambino_ in base a una traduzione esistente denominata _parent_. Le traduzioni figlio sostituiscono l&#39;elemento padre. Tuttavia, se la traduzione figlio non viene caricata o visualizzata o se manca una frase o una parola, Commerce utilizza le impostazioni internazionali principali. [Esempi di ereditarietà di pacchetti linguistici](#example-of-language-inheritance).

Per dichiarare un pacchetto, specificare le seguenti informazioni:

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

- `code`—Impostazioni internazionali del pacchetto lingua (obbligatorio)
- `vendor`- Nome fornitore del modulo (obbligatorio)
- `package`—Nome del pacchetto linguistico (obbligatorio)
- `sort_order`—Priorità del caricamento di un pacchetto quando sono disponibili diversi pacchetti linguistici per un archivio
- `use`- Impostazioni internazionali del pacchetto lingua padre da cui ereditare i dizionari

Se necessario, puoi specificare diversi pacchetti principali. I pacchetti padre vengono applicati in base al primo utilizzo elencato.

#### Esempio di ereditarietà della lingua

Supponiamo che un pacchetto di linguaggio erediti da altri due pacchetti e che tali pacchetti abbiano anche pacchetti padre e &quot;nonno&quot;.

Se un pacchetto linguistico eredita da due pacchetti, il relativo `language.xml` potrebbe avere un aspetto simile al seguente:

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

Nell&#39;esempio precedente:

- `language_package_one` eredita da `en_au_package` e `en_au_package` eredita da `en_ie_package`
- `language_package_two` eredita da `en_ca_package` e `en_ca_package` eredita da `en_us_package`

Se l’applicazione Commerce non è in grado di trovare parole o frasi nel `en_GB` pacchetto, cerca in altri pacchetti nella seguente sequenza:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Se si specificano tutte le ereditarietà tra i pacchetti di lingua, è possibile creare catene di ereditarietà circolari. Utilizzo [Magento\Test\Integrity\App\Language\CircularDependencyTest] test per individuare e correggere tali catene.

### Configurare più pacchetti per una lingua

Per rendere più flessibile il tuo negozio, puoi caricare diversi pacchetti di lingue per la stessa lingua nel tuo negozio. Pertanto, è possibile utilizzare pacchetti personalizzati diversi per diverse parti del negozio perché il sistema compila un unico pacchetto da tutti i pacchetti disponibili per una lingua.

Per abilitare un pacchetto aggiuntivo per una lingua esistente, assegna un nome al nuovo pacchetto qualsiasi, ad eccezione di un nome di codice della lingua esistente (per evitare confusione). Specifica le configurazioni di un pacchetto nel pacchetto linguistico `language.xml` file meta-informazioni come descritto nella sezione successiva.

## Esempi di utilizzo dei comandi di traduzione

Le sezioni seguenti forniscono esempi end-to-end sull&#39;utilizzo dei comandi descritti in questo argomento per creare dizionari di traduzione e pacchetti di traduzione:

### Esempio: Creare un dizionario di traduzione per un modulo o un tema

Per aggiungere una traduzione tedesca a un modulo o a un tema che si desidera distribuire ad altri esercenti:

1. Raccogliere frasi dal modulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >Il nome del file CSV deve _corrispondenza esatta_ le impostazioni internazionali, comprese le lettere maiuscole in minuscole e viceversa.

1. Tradurre parole e frasi utilizzando [presenti linee guida](#translation-guidelines).
1. Se necessario, copia `xx_YY.csv` a `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` o nella directory dei temi del modulo (a seconda che il dizionario di traduzione sia per un modulo o un tema).

### Esempio: Creare un pacchetto linguistico

Simile all’esempio precedente, genera un file CSV, ma invece di specificare un modulo o una directory di tema, specifica l’intera directory principale dell’applicazione Commerce. Il CSV risultante contiene tutte le frasi che il comando potrebbe trovare nel codice.

1. Raccogliere frasi dal modulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >Il nome del file CSV deve _corrispondenza esatta_ le impostazioni internazionali, comprese le lettere maiuscole in minuscole e viceversa.

1. Tradurre parole e frasi utilizzando [presenti linee guida](#translation-guidelines).
1. Crea il pacchetto linguistico.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Crea una directory per il pacchetto linguistico.

   Ad esempio: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. In tale directory, aggiungi tutti i seguenti elementi:

   - Una licenza, se richiesta
   - `composer.json` (campione successivo)
   - `registration.php` (campione successivo)
   - `language.xml` (campione successivo)

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
[Ulteriori informazioni sui pacchetti linguistici]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registri]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`compositore.json`]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[`registration.php`]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
