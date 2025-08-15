---
title: Best practice per modificare il codice PHP di base e di terze parti
description: Scopri come e quando modificare il codice PHP di base di Adobe Commerce e di terze parti.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Best practice per modificare o ignorare il codice PHP di base e di terze parti

Questo documento descrive le best practice da seguire quando si rende necessario modificare la funzionalità, il risultato o l’input di un codice che non è stato creato o che non è stato controllato direttamente. In altre parole, codice core e codice di terze parti. Questo documento si concentra principalmente sul codice PHP back-end.

## Metodi di modifica del codice

Quando modifichi il codice, è importante considerare l’ambito delle modifiche. La &quot;portata&quot; delle modifiche si riferisce alla portata degli effetti delle modifiche al codice. Come best practice, basa la decisione su come completare l’implementazione finale in base all’opzione che ha il minore impatto ambientale e il minore utilizzo di risorse. Più ampie sono le sostituzioni del codice, più un team di sviluppo si discosta dalla funzionalità di base di Adobe Commerce, aumentando la probabilità di bug e un maggiore sforzo per mantenere la base di codice in futuro.

### Patch

Una patch è un file che contiene istruzioni per modificare direttamente il codice all’interno di un file che non è sotto il controllo diretto del team di sviluppo. Si tratta di un’opzione che in genere deve essere considerata come ultima risorsa quando non esistono altre opzioni. I cerotti sono destinati ad essere una soluzione temporanea. Se è necessario creare un cerotto, come best practice generale, rimuoverlo a favore di una soluzione più permanente entro le 2-4 settimane successive. 

Le chiazze si rompono facilmente. Se i file di destinazione della patch vengono aggiornati, spesso la patch non funziona più. Questo perché un file patch contiene numeri di riga e numeri di colonna che indicano in modo specifico ciò che deve essere modificato dalla patch. Se qualcosa non corrisponde a quello che la patch si aspettava, cessa di essere applicata e interrompe il codice.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Cosa può essere modificato con una patch

Qualsiasi cosa. Letteralmente, qualsiasi carattere all’interno di un file di destinazione può essere modificato. Le patch non sono limitate a un particolare tipo di file o linguaggio di codice. In genere, si utilizza una patch per eseguire il targeting dei file nella directory `vendor`. 

#### Quando usare un cerotto

Se ti rendi conto che non esiste altra opzione. Ad esempio, se il fornitore non ha ancora pubblicato una correzione per il codice, puoi utilizzare una patch per risolvere temporaneamente il problema in attesa di una soluzione permanente.

#### Svantaggi

Le chiazze si rompono facilmente. Quando il codice di destinazione cambia, la patch non funziona più. Sono pensati per essere una soluzione solo a breve termine.

### Preferenza

Una preferenza è un concetto progettato nella piattaforma Adobe Commerce. Si tratta essenzialmente di una &quot;sostituzione di classe PHP&quot;.

La piattaforma Adobe Commerce utilizza un &quot;object manager&quot; per creare istanze delle classi PHP perché non crea istanze delle classi PHP con la nuova parola chiave, come avviene nelle applicazioni PHP tradizionali. Al contrario, il gestore degli oggetti fa riferimento al nome della classe PHP da creare in base a una configurazione compilata per determinare se un modulo ha dichiarato una preferenza per la classe originale. Se viene trovata una preferenza per la classe PHP, il gestore oggetti crea un&#39;istanza della classe specificata.

Va notato che (solitamente) la nuova classe PHP che sostituisce la classe PHP originale si estende/eredita dalla classe PHP originale. Ciò avviene per un paio di motivi:

- Garantire che l’iniezione di dipendenze/suggerimenti sul tipo sia rispettata. In caso contrario, si verificherà un errore irreversibile e l’applicazione si interromperà.
- Per consentire una scrittura minima del codice. Se la classe PHP originale contiene dieci metodi, ma è sufficiente sostituire un solo metodo, è in genere possibile modificare un solo metodo e lasciare intatti gli altri nove metodi. Questo è importante per assicurarsi di non bloccare gli aggiornamenti alle funzionalità di base quando la piattaforma viene aggiornata alle nuove versioni.

#### Dichiarare una preferenza

Dichiarare una preferenza è un processo abbastanza semplice. È necessario aggiungere una singola riga di codice a un file `di.xml` all&#39;interno di un modulo. Questa operazione può essere eseguita a livello globale o all&#39;interno di qualsiasi &quot;area&quot; Adobe Commerce, ad esempio `frontend`, `adminhtml`, `graphql`, `webapi_rest` e `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Cosa è possibile modificare con una preferenza

Solo le classi PHP possono essere sostituite con una preferenza. All&#39;interno della classe PHP, è possibile modificare i metodi e le proprietà pubblici e protetti. Per i metodi pubblici e protetti, è possibile sostituire completamente il metodo oppure modificare gli argomenti che entrano nel metodo padre originale o il risultato che ne deriva.

I metodi privati non possono tecnicamente essere sostituiti. Tuttavia, puoi creare un sostituto personalizzato per il metodo privato originale. Puoi anche dargli un nome arbitrario, puoi anche usare il nome originale. Non ha importanza perché esiste un metodo privato solo all&#39;interno del file effettivo che lo contiene. Per ignorare un metodo privato, devi sovrascrivere o modificare il metodo pubblico o protetto che chiama il metodo privato originale e devi sostituirlo con la tua funzionalità.

#### Quando utilizzare una preferenza

Ancora una volta, devi utilizzare le preferenze quando non esiste alcuna altra opzione e quando non puoi raggiungere il tuo obiettivo con l’iniezione di dipendenza, un plug-in o un osservatore. A volte potrebbe essere necessaria una preferenza se è necessario modificare o sostituire metodi o proprietà private o protette. Va notato che le preferenze dovrebbero essere utilizzate con moderazione. Sono un metodo abbastanza &quot;greedy&quot; di cambiare l&#39;applicazione e si prende effettivamente la proprietà della classe PHP. Questo può portare a conflitti con moduli di terze parti, bloccare gli aggiornamenti alla classe core e causare bug difficili da diagnosticare. La piattaforma Adobe Commerce è stata progettata per includere altre strade mediante le quali è possibile apportare modifiche al codice sottostante con un ingombro ridotto.

#### Svantaggi

Le preferenze sono un modo ingordo per modificare il codice e devono essere utilizzate solo quando non esistono altre opzioni. Le preferenze possono spesso causare conflitti all’interno della base di codice e, peggio ancora, possono bloccare gli aggiornamenti principali che si verificano con gli aggiornamenti di Platform. 

### Osservatore

Un osservatore è il concetto di listener di eventi, presente in molte applicazioni, piattaforme, librerie e linguaggi di codifica. Il concetto non è univoco per la piattaforma Adobe Commerce. Gli osservatori sono stati inseriti nella piattaforma fin dai tempi di Magento 1 e sono considerati una scelta primaria di come modificare il codice di base e il codice di terze parti. 

La base di codice core e qualsiasi modulo di terze parti possono inviare un evento in un luogo scelto nel codice. L&#39;osservatore, dichiarato in un file `events.xml` e in ascolto dell&#39;evento inviato per nome, può lavorare a livello globale o essere vincolato a qualsiasi &quot;area&quot; di Adobe Commerce, ad esempio `frontend`, `adminhtml`, `graphql`, `webapi_rest` e `crontab`.

#### Come dichiarare un osservatore

Gli osservatori possono essere configurati in un file `events.xml` globale o specifico per l&#39;area.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Cosa può essere modificato con un osservatore

Gli osservatori si applicano solo al codice PHP all’interno della piattaforma Adobe Commerce. Puoi modificare solo i dati e gli oggetti specifici trasmessi con l’invio di eventi.

#### Quando utilizzare un osservatore

Quando disponibile Se gli osservatori fossero più ampiamente disponibili e flessibili, allora gli osservatori sarebbero al secondo posto in questa lista. Gli osservatori hanno un carico di elaborazione inferiore rispetto ai plug-in, sono meno disponibili e meno flessibili.

#### Svantaggi

Anche se gli osservatori sono un modo eccellente per intercettare e modificare il codice, l’invio degli eventi deve essere aggiunto al codice di base o di terze parti per essere disponibile affinché il codice possa essere in ascolto. Questo rende il concetto di utilizzo degli osservatori un po&#39; limitato. L&#39;utente è limitato agli eventi che uno sviluppatore può includere nel codice.

Inoltre, un altro fattore limitante per gli osservatori è che l’evento inviato fornisce accesso solo ai dati e agli oggetti specifici che lo sviluppatore ha deciso di trasmettere insieme all’evento.

### Plug-in

Un plug-in è un concetto flessibile introdotto nella piattaforma Adobe Commerce. Consente di intercettare, sostituire e modificare qualsiasi metodo PHP pubblico. I plug-in consentono di modificare gli argomenti che entrano in un metodo prima dell&#39;esecuzione del metodo di destinazione, di modificare il risultato dopo l&#39;esecuzione del metodo di destinazione o di sostituire completamente il metodo di destinazione. Puoi modificare molti metodi di una classe PHP di destinazione all&#39;interno di un singolo file di plug-in. È inoltre possibile utilizzare l&#39;argomento `$subject` per eseguire qualsiasi metodo pubblico esistente nella classe PHP di destinazione.

#### Come dichiarare un plug-in

I plug-in possono essere configurati in un file `di.xml` globale o specifico per l&#39;area.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Cosa è possibile modificare con un plug-in

Questa funzionalità è disponibile solo per le classi PHP target. Puoi modificare l’input o l’output di un metodo pubblico e utilizzare un plug-in per attivare altre funzionalità. Se più plug-in sono destinati alla stessa classe PHP, è possibile impostare un criterio di ordinamento per l’esecuzione dei plug-in in modo che possa essere eseguito prima o dopo altri plug-in.

#### Quando utilizzare un plug-in

Quando la sostituzione della dipendenza non è disponibile. I plug-in vengono comunemente utilizzati nella base di codice principale, nel codice di terze parti, e possono essere comunemente utilizzati nel codice personalizzato. Di solito, quando devi modificare funzionalità non possedute o controllate dal codice personalizzato, un plug-in è il modo migliore.

#### Svantaggi

Impossibile modificare le proprietà o i metodi protetti. Il sovraccarico di elaborazione è superiore a quello di un osservatore. Non è un vero argomento per non utilizzare i plugin, la differenza è banale. Tuttavia, questo è qualcosa di buono da tenere a mente.

### Sostituzione dipendenze

Iniezione di dipendenza è un concetto di codifica standard orientato agli oggetti in cui le dipendenze richieste vengono passate in una classe con il costruttore. Tuttavia, la piattaforma Adobe Commerce compie un ulteriore passo avanti offrendo diverse possibilità di sostituzione delle dipendenze con XML. Sostanzialmente, la sostituzione della dipendenza. La sostituzione della dipendenza non è adatta a ogni situazione, ma consente una scrittura del codice minima, un sovraccarico ridotto e consente di eseguire il targeting di parti esatte di codice solo in modo limitato. È possibile modificare metodi privati e protetti con la sostituzione della dipendenza.

#### Come utilizzare la sostituzione della dipendenza

La sostituzione della dipendenza può essere eseguita su base globale o in base a un&#39;area specifica.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Dopo aver seguito questi passaggi, avrai modificato correttamente il comportamento di un metodo privato.

#### Cosa è possibile modificare con la sostituzione della dipendenza

I metodi pubblici, protetti e privati possono essere modificati con la sostituzione della dipendenza. Come con un plug-in, è possibile modificare gli argomenti in ingresso, sostituire completamente la funzione o modificare l&#39;output della funzione.

#### Quando utilizzare la sostituzione delle dipendenze

Si tratta di una buona prima opzione quando in realtà raggiungerebbe l’obiettivo desiderato, supponendo che non sia necessario fare nulla di troppo complesso per implementarlo.

#### Svantaggi

Non molti. Non è utilizzabile in ogni situazione. Lo svantaggio principale consiste nel fatto che è necessario estendere la classe originale contenente la funzionalità che si desidera modificare. Questo va contro il principio della &quot;composizione sull&#39;ereditarietà&quot;.
