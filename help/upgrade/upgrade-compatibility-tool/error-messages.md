---
title: '''[!DNL Upgrade Compatibility Tool] Messaggi di errore"'
description: Ulteriori informazioni sui messaggi di errore che si verificano quando si utilizza [!DNL Upgrade Compatibility Tool] sul progetto Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4113'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] messaggi di errore

{{commerce-only}}

Questo riferimento al messaggio di errore fornisce informazioni sugli errori che possono verificarsi durante l&#39;esecuzione di [!DNL Upgrade Compatibility Tool].

I messaggi di errore sono suddivisi per livello (problemi critici, errori e avvisi) e per tipo (codice core, codice personalizzato e schemi di GraphQL). Ogni tipo contiene le seguenti informazioni:

- **Codice di errore**: identificatore assegnato da Adobe Commerce al messaggio di errore.
- **Descrizione errore**: descrizione che riepiloga la causa dell’errore.
- **Azione suggerita per errore**: se applicabile, fornisce indicazioni per la risoluzione dei problemi e la risoluzione dell’errore.

## Problemi critici

### Codice core

Questi errori vengono segnalati quando alcuni dei file core sono mancanti o non corrispondono all’originale.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 2001 | File core non trovato | Esegui il `composer install` dalla directory principale del progetto. |
| 2002 | File core modificato | Esegui il `composer install` dalla directory principale del progetto. |
| 2003 | La dipendenza del compositore non è installata | La mancanza di dipendenza del compositore può potenzialmente causare problemi. Ripristina dipendenza eseguendo `composer require package_name`. |
| 2005 | Cartella core non trovata | Esegui il `composer install` dalla directory principale del progetto. |

{style="table-layout:auto"}

### Codice personalizzato

Gli errori critici vengono generati quando il codice personalizzato fa riferimento a entità che non sono presenti nella versione Adobe Commerce di destinazione. Questi errori sono segnalati anche quando gli standard di codifica critici sono stati violati.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1110 | Creazione di un&#39;istanza di una classe/interfaccia Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. Creazione di un&#39;istanza di una classe/interfaccia Adobe Commerce inesistente. |
| 1111 | Estensione da una classe Adobe Commerce non esistente | La classe estesa non è più presente nel codebase. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1112 | Importazione di una classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1113 | Caricamento della classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1114 | Utilizzo di una classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1214 | Utilizzo di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1215 | Sovrascrittura di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1216 | Assegnazione di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1312 | Interfaccia Adobe Commerce importata inesistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1314 | Interfaccia Adobe Commerce inesistente utilizzata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1317 | Interfaccia Adobe Commerce ereditata non esistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1318 | Implementata interfaccia Adobe Commerce inesistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1410 | Chiama metodo Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1514 | Utilizzo di una proprietà Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1515 | Sovrascrittura di una proprietà Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1516 | Assegnazione di una proprietà Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. Aggiorna il livello di accesso alle proprietà su privato se può essere utilizzato solo all&#39;interno di una singola classe. |
| 5002 | Il tag PHP di apertura deve essere il primo contenuto del file | Assicurati che nel file non sia presente alcun contenuto prima del tag di apertura PHP. |
| 5003 | La funzione è diventata obsoleta | Utilizza un sostituto suggerito nel messaggio di errore. Se il messaggio non suggerisce una sostituzione, è necessario un esame approfondito per selezionare una funzione o un’implementazione alternativa. |
| 5005 | Errore di sintassi PHP | Il codice deve essere aggiornato per rispettare gli standard di sintassi PHP. |
| 5072 | Possibile violazione di progettazione del Magento 2. È stata rilevata una tipica costruzione Magento 1.x | Aggiornare la costruzione agli standard del Magento 2. |
| 5076 | Impossibile utilizzare nello spazio dei nomi perché è riservato a partire da PHP 7 | Sostituisci la parola riservata nello spazio dei nomi con una parola chiave non riservata. |
| 5077 | Impossibile utilizzare come nome di classe perché è riservato a partire da PHP 7 | Sostituire il nome della classe riservata con un nome non riservato. |

{style="table-layout:auto"}

### Schema DB

I problemi critici dello schema di database vengono segnalati se i vincoli personalizzati fanno riferimento a tabelle o colonne core rimosse.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 7009 | Il vincolo personalizzato fa riferimento a una tabella di base rimossa nella versione di destinazione | Rimuovere il vincolo o aggiornare gli attributi referenceTable e referenceColumn |
| 7010 | Il vincolo personalizzato fa riferimento a una colonna core rimossa nella versione di destinazione | Rimuovere il vincolo o aggiornare l&#39;attributo referenceColumn |

{style="table-layout:auto"}

### Schema GraphQL

Se gli elementi dello schema non sono presenti nella versione di destinazione, vengono generati problemi critici relativi allo schema di GraphQL.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 3101 | Tipo rimosso | Elenca tutte le query che fanno riferimento a questo campo. Verifica se queste query sono utilizzate dall’implementazione di personalizzazione. Aggiorna il codice client per gestire l’interfaccia query modificata. |
| 3102 | Tipo rimosso dall’unione | Se il tipo di unione viene utilizzato nell’implementazione della costruzione di richieste GraphQL o dell’elaborazione di risposte, potrebbe essere necessario aggiornarlo. |
| 3103 | Campo rimosso | Verifica se nel codebase di personalizzazione viene fatto riferimento al campo. Regola l’implementazione per gestire correttamente il nuovo tipo di campo. |
| 3105 | Interfaccia implementata rimossa | Verifica se il tipo che implementa l’interfaccia rimossa è utilizzato nella personalizzazione. Potrebbe essere necessario aggiornare l’implementazione se si basa sull’interfaccia rimossa. |
| 3106 | Valore rimosso da enum | Se il valore enum rimosso viene utilizzato nell’implementazione della costruzione di richieste GraphQL o dell’elaborazione di risposte, potrebbe essere necessario aggiornarlo. |
| 3107 | Argomento rimosso | Verifica se il campo viene utilizzato nel codebase di personalizzazione. Rimuovi l&#39;argomento per questo campo. |
| 3109 | Direttiva rimossa | Verifica se la direttiva è utilizzata nel codebase di personalizzazione. Adeguare l&#39;attuazione per eliminare il riferimento alla direttiva. |
| 3110 | Argomento direttiva rimosso | Verifica se la direttiva è utilizzata nel codebase di personalizzazione. Rimuovere l&#39;argomento della direttiva. |
| 3111 | Direttiva ripetibile rimossa | Verifica se la direttiva è utilizzata nel codebase di personalizzazione. Regola l’implementazione per gestire le modifiche all’interfaccia. |
| 3112 | Posizione direttiva rimossa | Verifica se la direttiva è utilizzata nel codebase di personalizzazione. Regola l’implementazione per gestire le modifiche all’interfaccia. |
| 3201 | Tipo modificato | Elenca tutte le query che fanno riferimento a questo campo. Verifica se queste query sono utilizzate dall’implementazione di personalizzazione. Aggiorna il codice client per gestire l’interfaccia query modificata. |
| 3203 | Tipo di campo modificato | Verifica se nel codebase di personalizzazione viene fatto riferimento al campo. Regola l’implementazione per gestire correttamente il nuovo tipo di campo. |
| 3207 | Tipo di argomento modificato | Verifica se il campo viene utilizzato nel codebase di personalizzazione. Aggiorna il tipo di argomento per questo campo. |
| 3303 | È stato aggiunto un campo di input richiesto | Il campo deve essere aggiunto alla richiesta se per la personalizzazione viene utilizzata la query che include questo campo. |
| 3307 | Argomento richiesto aggiunto | Verifica se il campo viene utilizzato nel codebase di personalizzazione. Quando si utilizza il campo, è necessario specificare il nuovo argomento obbligatorio. |
| 3310 | Argomento direttiva obbligatorio aggiunto | Verifica se la direttiva è utilizzata nel codebase di personalizzazione. Aggiungere l&#39;argomento direttiva. |

{style="table-layout:auto"}

## Errori

### Codice personalizzato

Gli errori del codice personalizzato vengono generati quando il codice personalizzato utilizza i punti di ingresso di Adobe Commerce che non sono considerati/contrassegnati come `@api`. Il mantenimento del comportamento di tali punti di ingresso non è garantito. La personalizzazione deve basarsi su `@api` punti di ingresso. La funzionalità basata su codice Adobe Commerce non API deve essere testata dopo l’aggiornamento. Questi errori sono segnalati anche quando i principali standard di codifica non sono stati rispettati.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1104 | Utilizzo di una classe non API che eredita l’interfaccia API | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice in base all’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1121 | Estensione da una classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1122 | Importazione classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1123 | Caricamento classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1124 | Utilizzo di una classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1224 | Utilizzo di una costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1225 | Sovrascrittura di una costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1226 | Assegnazione di una costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1322 | Interfaccia API non Adobe Commerce importata | Interfacce non contrassegnate come `@api` possono essere modificate. Prova a rimuovere questa ereditarietà o a sostituirla con un’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un’interfaccia introdotta nell’ambito del codice di personalizzazione. |
| 1324 | Interfaccia API non Adobe Commerce utilizzata | Interfacce non contrassegnate come `@api` possono essere modificate. Prova a rimuovere questa ereditarietà o a sostituirla con un’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un’interfaccia introdotta nell’ambito del codice di personalizzazione. |
| 1327 | Interfaccia API non Adobe Commerce ereditata | Costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1328 | Implementata interfaccia API non Adobe Commerce | Interfacce non contrassegnate come `@api` possono essere modificate. Prova a rimuovere questa ereditarietà o a sostituirla con un’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un’interfaccia introdotta nell’ambito del codice di personalizzazione. |
| 1420 | Creazione di un’istanza della classe/interfaccia API non Adobe Commerce | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice in base all’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. Inoltre, il modo consigliato per recuperare un’istanza della classe è l’utilizzo di. Prendere in considerazione l&#39;utilizzo di una factory se è necessaria una nuova istanza della classe. |
| 1428 | Possibile dipendenza dai dettagli di implementazione. | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice in base all’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1429 | Chiamare metodi API non Adobe Commerce | Metodi non contrassegnati come `@api` o non sono dichiarati all’interno della classe/interfaccia API possono essere modificati. Anche se l’interfaccia del metodo non viene aggiornata nella nuova versione, il suo comportamento o output può essere diverso. Valuta la possibilità di affidarti a un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1449 | Chiamata a un metodo non di interfaccia (presente nell’implementazione) | I metodi non dichiarati nell’interfaccia possono essere modificati. Valuta la possibilità di affidarti a un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1524 | Utilizzo della proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 1525 | Sovrascrittura della proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 1526 | Assegnazione di proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 5004 | La funzione senza argomento è stata deprecata | Passa l’input da convalidare come primo argomento della funzione. |
| 5007 | Si sconsiglia l&#39;uso di alcune funzioni | Evita di usare queste funzioni. |
| 5009 | Le direttive modello non possono richiamare metodi. È consentito solo l’accesso ad array scalari | Rimuovere le chiamate al metodo dal modello. |
| 5010 | Modello `@vars` il blocco di commenti contiene JSON non valido | Correzione di JSON non valido. |
| 5011 | Modello `@vars` il blocco di commenti contiene un’etichetta non valida | Correggi l’etichetta non valida. |
| 5012 | Modello `@vars` nel blocco di commento manca una variabile utilizzata nel modello | Aggiungi variabile mancante @vars blocco di commenti. |
| 5013 | Evita di utilizzare tag di chiusura automatica con elemento html non void | Utilizza invece il tag di chiusura. |
| 5014 | Il `"active"` l&#39;attributo è obsoleto | L’elenco dei moduli attivi è definito nella configurazione di distribuzione. |
| 5015 | Il `<param>` nodo obsoleto | Utilizzare `<argument name="..." xsi:type="...">` invece. |
| 5016 | Il `<instance>` nodo obsoleto | Utilizzare `<argument name="..." xsi:type="object">` invece. |
| 5017 | Il `<array>` nodo obsoleto | Utilizzare `<argument name="..." xsi:type="array">` invece. |
| 5018 | Il `<item key="...">` nodo obsoleto | Utilizzare `<item name="..." xsi:type="...">` invece. |
| 5019 | Il `<value>` nodo obsoleto | Fornisci invece il valore effettivo come valore letterale di testo. |
| 5020 | Nodo obsoleto: `<supported_blocks>` | Da sostituire con `<supported_containers>`. |
| 5021 | Nodo obsoleto: `<block_name>` | Da sostituire con `<container_name>`. |
| 5022 | Rilevato nome factory | Il tipo di widget non deve iniziare con /. |
| 5023 | Struttura ACL obsoleta rilevata nella riga | Controlla lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Rilevata struttura di menu obsoleta nella riga | Controlla app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Rilevata struttura di configurazione del sistema obsoleta nel file | Controlla app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Non usi `"text/javascript"` attributo type | Utilizzare solo membri pubblici. |
| 5028 | Accesso a membri protetti e privati di `Block` classe obsoleta nei modelli phtml | Utilizzare solo membri pubblici. |
| 5031 | Contiene un metodo obsoleto | Utilizzare `getConnection()` al suo posto. |
| 5042 | Formato non corretto del riferimento della classe PHP | Controlla che ci siano riferimenti alla classe utilizzando solo lettere CamelCased, numeri e nessuna barra iniziale. |
| 5043 | Formato non corretto del riferimento al modulo | Verifica che al modulo venga fatto riferimento utilizzando solo lettere, numeri, trattini bassi e nessuna barra iniziale. |
| 5044 | Classe `Zend_Db_Select` è limitato | Sostituzione consigliata: `\Magento\Framework\DB\Select`. |
| 5045 | Classe `Zend_Db_Adapter_Pdo_Mysql` è limitato | Sostituzione consigliata: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Classe `Magento\Framework\Serialize\Serializer\Serialize` è limitato | Sostituzione consigliata: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Classe `ArrayObject` è limitato | Sostituzione consigliata: classe personalizzata, estesa da `ArrayObject` con metodi serialize/unserialize sovrascritti. |
| 5048 | Classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` è limitato | Sostituzione consigliata: factory che crea una classe personalizzata, estesa da `ArrayObject` con metodi serialize/unserialize sovrascritti. |
| 5050 | Il blocco a cui si fa riferimento viene rimosso | Rimuovi il riferimento al blocco. |
| 5051 | `output="toHtml"` è obsoleto | Utilizzare `output="1"`. |
| 5052 | La classe `\Magento\Framework\View\Element\Text\ListText` non deve più essere utilizzato nel layout | Rimuovi classe `\Magento\Framework\View\Element\Text\ListText` dal layout. |
| 5053 | Chiamata del metodo tramite istruzione di layout `<action>` non è consentito | Evita l’utilizzo di un metodo che genera pregiudizio in `<action>`. |
| 5054 | `helper` l&#39;attributo contiene `/` | Rimuovi `/` dall’attributo helper. |
| 5055 | `helper` l’attributo non contiene `::` | Aggiungi `::` all&#39;attributo helper. |
| 5056 | Gli script di installazione sono obsoleti | Utilizza l’approccio basato su schema dichiarativo nel file etc/db_schema.xml di module\. |
| 5057 | Gli script InstallSchema sono obsoleti | Utilizza l’approccio basato su schema dichiarativo nel file etc/db_schema.xml di module\. |
| 5058 | Gli script InstallData sono obsoleti | Utilizza l’approccio patch dati nella directory Setup/Patch/Data di Module\. |
| 5059 | Gli script di installazione sono obsoleti | Creare una classe InstallData nella cartella Setup del modulo. |
| 5060 | Gli script di aggiornamento sono obsoleti | Utilizza l’approccio basato su schema dichiarativo nel file etc/db_schema.xml di module\. |
| 5061 | Gli script UpgradeSchema sono obsoleti | Utilizza l’approccio basato su schema dichiarativo nel file etc/db_schema.xml di module\. |
| 5062 | Gli script UpgradeData sono obsoleti | Utilizza l’approccio patch dati nella directory Setup/Patch/Data di Module\. |
| 5063 | Gli script di aggiornamento sono obsoleti | Utilizza l’approccio patch dati nella directory Setup/Patch/Data del modulo. |
| 5064 | Gli script ricorrenti sono obsoleti | Crea la classe Ricorrente nella cartella Setup del modulo. |
| 5065 | &#39;data&#39; si trova in una directory non valida | Crea una patch di dati nella cartella Setup/Patch/Data del modulo per gli aggiornamenti dei dati o utilizza l’approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo per le modifiche dello schema. |
| 5066 | &#39;sql&#39; si trova in una directory non valida | Crea una patch di dati nella cartella Setup/Patch/Data del modulo per gli aggiornamenti dei dati o utilizza l’approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo per le modifiche dello schema. |
| 5067 | I nodi identificati da XPath sono obsoleti | Il codice XML obsoleto indicato nell’errore deve essere aggiornato. Segui i suggerimenti dal messaggio di errore. |
| 5068 | Direttiva `{{htmlescape}}` è obsoleto | Utilizzare `{{var}}` invece. |
| 5069 | Direttiva `{{escapehtml}}` è obsoleto | Utilizzare `{{var}}` invece. |
| 5070 | Il terzo parametro non è più necessario per `getChildHtml()` | Rimuovi terzo parametro dalla chiamata a `getChildHtml()`. |
| 5071 | Il quarto parametro non è più necessario per `getChildHtml()` | Rimuovi quarto parametro dalla chiamata a `getChildHtml()`. |
| 5073 | I nomi di tabella legacy con barra devono essere impostati su nomi di tabella diretti | Utilizza invece il nome diretto della tabella. |
| 5075 | I moduli applicativi non devono utilizzare le classi dei moduli di test | Rimuovi l’utilizzo delle classi dai moduli di test. |
| 5078 | La classe deve essere richiesta nel costruttore, altrimenti il compilatore non sarà in grado di trovare e generare tali classi | Aggiungi classe al costruttore. |
| 5079 | L’uso delle variabili di classe var è sconsigliato | Evita di utilizzare &#39;var&#39; per dichiarare la variabile di classe. |
| 5080 | Rilevata possibile istruzione SQL non elaborata | Utilizza invece archivi o patch di dati. |
| 5081 | L’utilizzo di helper nei modelli è sconsigliato | Utilizzate invece ViewModel. |
| 5082 | L&#39;utilizzo di $this nei modelli è obsoleto | Utilizza invece $block. |
| 5083 | Le costanti non sono consentite come primo argomento della funzione di traduzione | Utilizza invece il valore letterale stringa. |
| 5085 | Si sconsiglia l&#39;uso di alcune funzioni | Utilizza invece la funzione alternativa consigliata sul messaggio. |
| 5087 | Problema di compatibilità cross-version PHP | Segui i suggerimenti del messaggio e controlla [guida alla migrazione](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parametri opzionali trovati dopo quelli richiesti | Sposta i parametri richiesti dopo quelli facoltativi. |
| 5089 | Visibilità metodo `final private` trovato | Cambia visibilità metodo da `final private` solo a `private`. |
| 5090 | Metodo magico `__set_state` non è definito come `static` | Metodo magico `__set_state` deve essere definito come `static`. |
| 5091 | Classe con `__toString()` metodo che non eredita da `Stringable` Interfaccia | Aggiungi `Stringable` interfaccia con classe con `__toString()` metodo. |
| 5092 | `is_resource()` metodo utilizzato per le funzioni che ora restituiscono Object | Cambia `is_resource()` a `instanceof` Oggetto. |
| 6001 | `jQuery.andSelf()` rimosso | Utilizzare `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` e `$.unbind` sono obsoleti | Utilizzare `$.on` e `$.off` invece. |
| 6003 | Il metodo jQuery per sottoscrivere l’evento è obsoleto e non deve essere utilizzato | Utilizzare `.on("event name", fn)` invece di sottoscrivere a tale evento. |
| 6003 | Il metodo jQuery per attivare l’evento è obsoleto e non deve essere utilizzato | Utilizzare `.trigger("event name")` per attivare l&#39;evento. |
| 6004 | jQuery `$.delegate` e `$.undelegate` sono obsoleti | Utilizzare `$.on` e `$.off` invece. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) è stato rimosso | Usa (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` rimosso | Utilizzare `jQuery.length`. |
| 6007 | `jQuery.trim` è obsoleto | Utilizzare `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &#39;inlite&#39;, tema &#39;mobile&#39;, tema &#39;moderno&#39;) è stato rimosso | Aggiorna il codice per renderlo compatibile con tinymce5. |
| 6009 | `jQuery.isFunction()` è obsoleto | Nella maggior parte dei casi può essere sostituito da [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` è obsoleto | Sostituisci con un controllo del tipo appropriato, ad esempio [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` è obsoleto | Utilizzare invece il metodo Array.isArray nativo. |
| 6009 | `jQuery.parseJSON()` è obsoleto | Per analizzare le stringhe JSON, utilizza invece il metodo JSON.parse nativo. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) è obsoleto | Utilizza invece jQuery.expr.pseudos. |

{style="table-layout:auto"}

### Schema DB

Gli errori dello schema di database vengono generati se le tabelle, le colonne, gli indici o i vincoli del database, aggiunti o rimossi nella versione Adobe Commerce di destinazione, possono causare conflitti con lo schema di database personalizzato.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 7001 | La versione core di destinazione introduce una tabella con lo stesso nome di una tabella dichiarata da un modulo personalizzato | Utilizza la nuova tabella core (se applicabile) o rinomina la tabella personalizzata |
| 7002 | La tabella core estesa da un modulo personalizzato è stata rimossa nella versione di destinazione | Tutti i riferimenti di tabella core rimossi devono essere rimossi dalla base di codice |
| 7003 | La versione core di destinazione introduce una colonna con lo stesso nome di una colonna dichiarata da un modulo personalizzato | Utilizza la nuova colonna core (se applicabile) o rinomina la colonna personalizzata |
| 7004 | La colonna core estesa da un modulo personalizzato è stata rimossa nella versione di destinazione | Tutti i riferimenti alle colonne core rimossi devono essere rimossi dalla base di codice |
| 7005 | La versione core di destinazione introduce un indice con lo stesso referenceId di un indice dichiarato da un modulo personalizzato | Rimuovi (se duplicato nell’indice core introdotto) o rinomina l’indice personalizzato |
| 7006 | L’indice core esteso da un modulo personalizzato è stato rimosso nella versione di destinazione | Tutti i riferimenti all’indice core rimossi devono essere rimossi dalla base di codice |
| 7007 | La versione core di destinazione introduce un vincolo con lo stesso nome di un vincolo dichiarato da un modulo personalizzato | Rimuovi (se duplicato rispetto al vincolo di base introdotto) o rinomina il vincolo personalizzato |
| 7008 | Il vincolo core esteso da un modulo personalizzato è stato rimosso nella versione di destinazione | Utilizzate il nuovo vincolo di base (se appropriato) o rinominate il vincolo personalizzato |

{style="table-layout:auto"}

## Avvisi

### Codice core

Questi avvisi vengono segnalati in caso di lievi incongruenze nella base di codice principale.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 2004 | Mancata corrispondenza versione dipendenza compositore | Problema indica che la versione della dipendenza del compositore in etalon e nel progetto effettivo è diversa. Aggiornare la dipendenza eseguendo `composer update <package_name>`. |

{style="table-layout:auto"}

### Codice personalizzato

Gli avvisi di codice personalizzato vengono generati quando vengono rilevati riferimenti a codice obsoleto. Tali riferimenti devono essere sostituiti con i punti di estensione supportati. Presta attenzione alla `@see` annotazione di un elemento obsoleto per i consigli. Questi errori sono segnalati anche quando non sono stati rispettati standard di codifica minori.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1131 | Estensione da Adobe Commerce ``@deprecated`` classe | La classe estesa verrà rimossa nelle prossime versioni. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1132 | Importazione di Adobe Commerce `@deprecated` classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1133 | Caricamento di Adobe Commerce `@deprecated` classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1134 | Utilizzo di Adobe Commerce `@deprecated` classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1234 | Utilizzo di Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Valuta l’utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1235 | Ignorare Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Valuta l’utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1236 | Assegnazione di Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Valuta l’utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1332 | Adobe Commerce importato `@deprecated` Interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. Valuta l’utilizzo di un’interfaccia o di una classe contrassegnata come `@api` invece. |
| 1334 | Adobe Commerce utilizzato `@deprecated` Interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. Valuta l’utilizzo di un’interfaccia o di una classe contrassegnata come `@api` invece. |
| 1337 | Ereditato da Adobe Commerce `@deprecated` Interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l’ereditarietà dell’interfaccia utilizzando un’interfaccia contrassegnata come `@api` o un’interfaccia introdotta all’interno dell’implementazione. |
| 1338 | Implementato Adobe Commerce `@deprecated` Interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l’ereditarietà dell’interfaccia utilizzando un’interfaccia contrassegnata come `@api` o un’interfaccia introdotta all’interno dell’implementazione. |
| 1430 | Richiama metodo dataobject non dichiarato | I metodi magici non dichiarati possono essere modificati. Valuta invece l’utilizzo di metodi di interfaccia. |
| 1439 | Chiama Adobe Commerce `@deprecated` metodo | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 1440 | Firma del metodo non corrispondente | È stata rilevata una chiamata o un override del metodo di base con parametri, argomenti o tipo restituito che non corrispondono alla firma del metodo. |
| 1534 | Utilizzo di Adobe Commerce `@deprecated` proprietà | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 1535 | Ignorare Adobe Commerce `@deprecated` proprietà | La proprietà obsoleta verrà rimossa nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API o di utilizzare invece una proprietà privata all’interno dell’implementazione. |
| 1536 | Assegnazione di Adobe Commerce `@deprecated` proprietà | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 5006 | I proxy e gli intercettori NON DEVONO mai essere esplicitamente richiesti nei costruttori | La classe originale deve essere dichiarata come tipo del parametro del costruttore. La classe Interceptor/Proxy verrà passata dall&#39;implementazione dell&#39;iniezione di dipendenza del framework. |
| 5074 | Utilizzo di un metodo obsoleto `getResource()` ai dati rilevati (salvataggio/caricamento/eliminazione). | Utilizza invece un archivio. |
| 5086 | Visibilità non dichiarata su una costante | Dichiara la visibilità su tutte le costanti. |

{style="table-layout:auto"}

### Schema GraphQL

Gli avvisi relativi allo schema di GraphQL vengono generati quando gli elementi aggiuntivi vengono aggiunti allo schema nella nuova versione. Si consiglia di rivedere l’implementazione per verificare se deve essere utilizzata per le richieste.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 3206 | Valore predefinito dell&#39;argomento modificato | Se la query viene utilizzata nella personalizzazione, il valore dell’argomento potrebbe dover essere specificato in modo esplicito. |
| 3302 | Tipo aggiunto all&#39;unione | Il tipo è stato aggiunto all&#39;unione. Controlla l’implementazione durante l’elaborazione del risultato della query che restituisce questo tipo di unione e assicurati che sia in grado di gestire il tipo aggiunto. |
| 3304 | Campo di input opzionale aggiunto | È stato aggiunto un campo di input facoltativo. Controlla l’implementazione per assicurarti che. |
| 3305 | Interfaccia implementata aggiunta | Il campo può accettare/fornire ulteriori informazioni che possono essere prese in considerazione nell’implementazione. |
| 3306 | Valore aggiunto a enum | Un valore è stato aggiunto a un&#39;enumerazione. Se i client contengono un&#39;istruzione switch sul valore dell&#39;enumerazione e non includono un caso predefinito, questa modifica potrebbe causare un comportamento imprevisto. |
| 3308 | Argomento facoltativo aggiunto | Se la query utilizza un nuovo argomento nella personalizzazione, potrebbe essere necessario aggiungerlo alla richiesta. |

{style="table-layout:auto"}
