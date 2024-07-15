---
title: '[!DNL Upgrade Compatibility Tool] messaggi di errore'
description: Ulteriori informazioni sui messaggi di errore che si verificano quando si utilizza  [!DNL Upgrade Compatibility Tool]  nel progetto Adobe Commerce.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] messaggi di errore

{{commerce-only}}

Questo riferimento al messaggio di errore fornisce informazioni sugli errori che possono verificarsi durante l&#39;esecuzione di [!DNL Upgrade Compatibility Tool].

I messaggi di errore sono suddivisi per livello (problemi critici, errori e avvisi) e per tipo (codice core, codice personalizzato e schemi di GraphQL). Ogni tipo contiene le seguenti informazioni:

- **Codice errore**: identificatore assegnato da Adobe Commerce al messaggio di errore.
- **Descrizione errore**: descrizione che riepiloga la causa dell&#39;errore.
- **Azione suggerita per l&#39;errore**: se applicabile, fornisce indicazioni per la risoluzione dei problemi e la risoluzione dell&#39;errore.

## Problemi critici

### Codice core

Questi errori vengono segnalati quando alcuni dei file core sono mancanti o non corrispondono all’originale.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 2001 | File core non trovato | Eseguire il comando `composer install` dalla directory principale del progetto. |
| 2002 | File core modificato | Eseguire il comando `composer install` dalla directory principale del progetto. |
| 2003 | La dipendenza del compositore non è installata | La mancanza di dipendenza del compositore può potenzialmente causare problemi. Ripristinare la dipendenza eseguendo `composer require package_name`. |
| 2005 | Cartella core non trovata | Eseguire il comando `composer install` dalla directory principale del progetto. |

{style="table-layout:auto"}

### Codice personalizzato

Gli errori critici vengono generati quando il codice personalizzato fa riferimento a entità che non sono presenti nella versione Adobe Commerce di destinazione. Questi errori vengono segnalati anche quando gli standard di codifica critici non sono stati rispettati.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1110 | Creazione di un&#39;istanza di una classe/interfaccia Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. Creazione di un&#39;istanza di una classe/interfaccia Adobe Commerce inesistente. |
| 1111 | Estensione da una classe Adobe Commerce non esistente | La classe estesa non è più presente nel codebase. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1112 | Importazione di una classe Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1113 | Caricamento della classe Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1114 | Utilizzo di una classe Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1214 | Utilizzo di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1215 | Sovrascrittura di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1216 | Assegnazione di una costante Adobe Commerce inesistente | In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1312 | Interfaccia Adobe Commerce importata inesistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1314 | Interfaccia Adobe Commerce inesistente utilizzata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1317 | Interfaccia Adobe Commerce ereditata non esistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1318 | Implementata interfaccia Adobe Commerce inesistente | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1410 | Chiama metodo Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1514 | Utilizzo di una proprietà Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1515 | Sovrascrittura di una proprietà Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1516 | Assegnazione di una proprietà Adobe Commerce inesistente | Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. Aggiorna il livello di accesso alle proprietà su privato se può essere utilizzato solo all&#39;interno di una singola classe. |
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

Gli errori del codice personalizzato vengono generati quando il codice personalizzato utilizza i punti di ingresso di Adobe Commerce che non sono considerati/contrassegnati come `@api`. Il mantenimento del comportamento di tali punti di ingresso non è garantito. La personalizzazione deve invece basarsi su `@api` punti di ingresso. La funzionalità basata su codice Adobe Commerce non API deve essere testata dopo l’aggiornamento. Questi errori sono segnalati anche quando i principali standard di codifica non sono stati rispettati.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1104 | Utilizzo di una classe non API che eredita l’interfaccia API | Le classi non contrassegnate come `@api` possono essere modificate. Prendere in considerazione l&#39;aggiornamento del codice in modo che si basi sull&#39;interfaccia contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1121 | Estensione da una classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1122 | Importazione classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1123 | Caricamento classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1124 | Utilizzo di una classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1224 | Utilizzo di una costante API non Adobe Commerce | Le costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1225 | Sovrascrittura di una costante API non Adobe Commerce | Le costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1226 | Assegnazione di una costante API non Adobe Commerce | Le costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1322 | Interfaccia API non Adobe Commerce importata | Le interfacce non contrassegnate come `@api` possono essere modificate. Provare a rimuovere l&#39;ereditarietà o a sostituirla con un&#39;ereditarietà dall&#39;interfaccia Adobe Commerce contrassegnata come `@api` o con un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1324 | Interfaccia API non Adobe Commerce utilizzata | Le interfacce non contrassegnate come `@api` possono essere modificate. Provare a rimuovere l&#39;ereditarietà o a sostituirla con un&#39;ereditarietà dall&#39;interfaccia Adobe Commerce contrassegnata come `@api` o con un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1327 | Interfaccia API non Adobe Commerce ereditata | Le costanti non contrassegnate come `@api` possono essere modificate. In alternativa, puoi introdurre e utilizzare una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1328 | Implementata interfaccia API non Adobe Commerce | Le interfacce non contrassegnate come `@api` possono essere modificate. Provare a rimuovere l&#39;ereditarietà o a sostituirla con un&#39;ereditarietà dall&#39;interfaccia Adobe Commerce contrassegnata come `@api` o con un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1420 | Creazione di un’istanza della classe/interfaccia API non Adobe Commerce | Le classi non contrassegnate come `@api` possono essere modificate. Prendere in considerazione l&#39;aggiornamento del codice in modo che si basi sull&#39;interfaccia contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. Inoltre, il modo consigliato per recuperare un’istanza della classe è l’utilizzo di. Prendere in considerazione l&#39;utilizzo di una factory se è necessaria una nuova istanza della classe. |
| 1428 | Possibile dipendenza dai dettagli di implementazione. | Le classi non contrassegnate come `@api` possono essere modificate. Prendere in considerazione l&#39;aggiornamento del codice in modo che si basi sull&#39;interfaccia contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1429 | Chiamare metodi API non Adobe Commerce | I metodi non contrassegnati come `@api` o non dichiarati nella classe/interfaccia API possono essere modificati. Anche se l’interfaccia del metodo non viene aggiornata nella nuova versione, il suo comportamento o output può essere diverso. Valuta la possibilità di affidarti a un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1449 | Chiamata a un metodo non di interfaccia (presente nell’implementazione) | I metodi non dichiarati nell’interfaccia possono essere modificati. Valuta la possibilità di affidarti a un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1524 | Utilizzo della proprietà API non Adobe Commerce | I valori delle proprietà non contrassegnate come `@api` possono essere modificati. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 1525 | Sovrascrittura della proprietà API non Adobe Commerce | I valori delle proprietà non contrassegnate come `@api` possono essere modificati. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 1526 | Assegnazione di proprietà API non Adobe Commerce | I valori delle proprietà non contrassegnate come `@api` possono essere modificati. Valuta invece di affidarti al metodo dell’interfaccia API. |
| 5004 | La funzione senza argomento è stata deprecata | Passa l’input da convalidare come primo argomento della funzione. |
| 5007 | Si sconsiglia l&#39;uso di alcune funzioni | Evita di usare queste funzioni. |
| 5009 | Le direttive modello non possono richiamare metodi. È consentito solo l’accesso ad array scalari | Rimuovere le chiamate al metodo dal modello. |
| 5010 | Il blocco di commenti del modello `@vars` contiene JSON non valido | Correzione di JSON non valido. |
| 5011 | Il blocco di commenti del modello `@vars` contiene un&#39;etichetta non valida | Correggi l’etichetta non valida. |
| 5012 | Nel blocco di commenti del modello `@vars` manca una variabile utilizzata nel modello | Aggiungi variabile mancante @vars blocco di commenti. |
| 5013 | Evita di utilizzare tag di chiusura automatica con elemento html non void | Utilizza invece il tag di chiusura. |
| 5014 | L&#39;attributo `"active"` è obsoleto | L’elenco dei moduli attivi è definito nella configurazione di distribuzione. |
| 5015 | Il nodo `<param>` è obsoleto | Utilizza invece `<argument name="..." xsi:type="...">`. |
| 5016 | Il nodo `<instance>` è obsoleto | Utilizza invece `<argument name="..." xsi:type="object">`. |
| 5017 | Il nodo `<array>` è obsoleto | Utilizza invece `<argument name="..." xsi:type="array">`. |
| 5018 | Il nodo `<item key="...">` è obsoleto | Utilizza invece `<item name="..." xsi:type="...">`. |
| 5019 | Il nodo `<value>` è obsoleto | Fornisci invece il valore effettivo come valore letterale di testo. |
| 5020 | Nodo obsoleto: `<supported_blocks>` | Da sostituire con `<supported_containers>`. |
| 5021 | Nodo obsoleto: `<block_name>` | Da sostituire con `<container_name>`. |
| 5022 | Rilevato nome factory | Il tipo di widget non deve iniziare con /. |
| 5023 | Struttura ACL obsoleta rilevata nella riga | Controlla lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Rilevata struttura di menu obsoleta nella riga | Controlla app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Rilevata struttura di configurazione del sistema obsoleta nel file | Controlla app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Non utilizzare attributo di tipo `"text/javascript"` | Utilizzare solo membri pubblici. |
| 5028 | L&#39;accesso ai membri protetti e privati della classe `Block` è obsoleto nei modelli phtml | Utilizzare solo membri pubblici. |
| 5031 | Contiene un metodo obsoleto | Utilizza invece il metodo `getConnection()`. |
| 5042 | Formato non corretto del riferimento della classe PHP | Controlla che ci siano riferimenti alla classe utilizzando solo lettere CamelCased, numeri e nessuna barra iniziale. |
| 5043 | Formato non corretto del riferimento al modulo | Verifica che al modulo venga fatto riferimento utilizzando solo lettere, numeri, trattini bassi e nessuna barra iniziale. |
| 5044 | La classe `Zend_Db_Select` è limitata | Sostituzione suggerita: `\Magento\Framework\DB\Select`. |
| 5045 | La classe `Zend_Db_Adapter_Pdo_Mysql` è limitata | Sostituzione suggerita: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | La classe `Magento\Framework\Serialize\Serializer\Serialize` è limitata | Sostituzione suggerita: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | La classe `ArrayObject` è limitata | Sostituzione consigliata: classe personalizzata, estesa da `ArrayObject` con metodi serialize/unserialize sovrascritti. |
| 5048 | La classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` è limitata | Sostituzione consigliata: factory che crea una classe personalizzata, estesa da `ArrayObject` con metodi serialize/unserialize sovrascritti. |
| 5050 | Il blocco a cui si fa riferimento viene rimosso | Rimuovi il riferimento al blocco. |
| 5051 | `output="toHtml"` è obsoleto | Usa `output="1"`. |
| 5052 | La classe `\Magento\Framework\View\Element\Text\ListText` non deve più essere utilizzata nel layout | Rimuovi la classe `\Magento\Framework\View\Element\Text\ListText` dal layout. |
| 5053 | Chiamata del metodo tramite l&#39;istruzione di layout `<action>` non consentita | Evitare l&#39;utilizzo di un metodo che causa un errore in `<action>`. |
| 5054 | L&#39;attributo `helper` contiene `/` | Rimuovi `/` dall&#39;attributo helper. |
| 5055 | L&#39;attributo `helper` non contiene `::` | Aggiungi `::` all&#39;attributo helper. |
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
| 5068 | Direttiva `{{htmlescape}}` obsoleta | Utilizza invece `{{var}}`. |
| 5069 | Direttiva `{{escapehtml}}` obsoleta | Utilizza invece `{{var}}`. |
| 5070 | Il terzo parametro non è più necessario per `getChildHtml()` | Rimuovi il terzo parametro dalla chiamata a `getChildHtml()`. |
| 5071 | Il quarto parametro non è più necessario per `getChildHtml()` | Rimuovere il quarto parametro dalla chiamata a `getChildHtml()`. |
| 5073 | I nomi di tabella legacy con barra devono essere impostati su nomi di tabella diretti | Utilizza invece il nome diretto della tabella. |
| 5075 | I moduli applicativi non devono utilizzare le classi dei moduli di test | Rimuovi l’utilizzo delle classi dai moduli di test. |
| 5078 | La classe deve essere richiesta nel costruttore, altrimenti il compilatore non sarà in grado di trovare e generare tali classi | Aggiungi classe al costruttore. |
| 5079 | L’uso delle variabili di classe var è sconsigliato | Evita di utilizzare &#39;var&#39; per dichiarare la variabile di classe. |
| 5080 | Rilevata possibile istruzione SQL non elaborata | Utilizza invece archivi o patch di dati. |
| 5081 | L’utilizzo di helper nei modelli è sconsigliato | Utilizzate invece ViewModel. |
| 5082 | L&#39;utilizzo di $this nei modelli è obsoleto | Utilizza invece $block. |
| 5083 | Le costanti non sono consentite come primo argomento della funzione di traduzione | Utilizza invece il valore letterale stringa. |
| 5085 | Si sconsiglia l&#39;uso di alcune funzioni | Utilizza invece la funzione alternativa consigliata sul messaggio. |
| 5087 | Problema di compatibilità cross-version PHP | Segui i suggerimenti del messaggio e controlla la [guida alla migrazione](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parametri opzionali trovati dopo quelli richiesti | Sposta i parametri richiesti dopo quelli facoltativi. |
| 5089 | Visibilità metodo `final private` trovata | Cambia la visibilità del metodo da `final private` a solo `private`. |
| 5090 | Metodo Magic `__set_state` non definito come `static` | Il metodo Magic `__set_state` deve essere definito come `static`. |
| 5091 | La classe con il metodo `__toString()` non eredita dall&#39;interfaccia `Stringable` | Aggiungere l&#39;interfaccia `Stringable` alla classe con il metodo `__toString()`. |
| 5092 | Metodo `is_resource()` utilizzato per le funzioni che ora restituiscono l&#39;oggetto | Cambia `is_resource()` in `instanceof` oggetto. |
| 6001 | `jQuery.andSelf()` rimosso | Usa `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` e `$.unbind` sono obsoleti | Utilizza invece `$.on` e `$.off`. |
| 6003 | Il metodo jQuery per sottoscrivere l’evento è obsoleto e non deve essere utilizzato | Utilizzare il metodo `.on("event name", fn)` per sottoscrivere l&#39;evento. |
| 6003 | Il metodo jQuery per attivare l’evento è obsoleto e non deve essere utilizzato | Utilizzare il metodo `.trigger("event name")` per attivare l&#39;evento. |
| 6004 | jQuery `$.delegate` e `$.undelegate` sono obsoleti | Utilizza invece `$.on` e `$.off`. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) è stato rimosso | Utilizza invece (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` rimosso | Usa `jQuery.length`. |
| 6007 | `jQuery.trim` è obsoleto | Usa `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &#39;inlite&#39;, tema &#39;mobile&#39;, tema &#39;modern&#39;) è stato rimosso | Aggiorna il codice per renderlo compatibile con tinymce5. |
| 6009 | `jQuery.isFunction()` è obsoleto | Nella maggior parte dei casi può essere sostituito da [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` è obsoleto | Sostituire con un controllo del tipo appropriato, ad esempio [typeof x === &quot;function&quot;]. |
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

Gli avvisi di codice personalizzato vengono generati quando vengono rilevati riferimenti a codice obsoleto. Tali riferimenti devono essere sostituiti con i punti di estensione supportati. Presta attenzione all&#39;annotazione `@see` dell&#39;elemento obsoleto per i consigli. Questi errori sono segnalati anche quando non sono stati rispettati standard di codifica minori.

| Codice di errore | Descrizione errore | Azione suggerita |
| --- | --- | --- |
| 1131 | Estensione dalla classe Adobe Commerce ``@deprecated`` | La classe estesa verrà rimossa nelle prossime versioni. L’ereditarietà non è un metodo consigliato per estendere la funzionalità di Adobe Commerce. Aggiornare il codice per utilizzare una classe contrassegnata come `@api`. |
| 1132 | Importazione classe Adobe Commerce `@deprecated` | La classe estesa verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo della classe Adobe Commerce contrassegnata come `@api`. |
| 1133 | Caricamento classe `@deprecated` di Adobe Commerce | La classe estesa verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo della classe Adobe Commerce contrassegnata come `@api`. |
| 1134 | Utilizzo della classe Adobe Commerce `@deprecated` | La classe estesa verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo della classe Adobe Commerce contrassegnata come `@api`. |
| 1234 | Utilizzo della costante `@deprecated` di Adobe Commerce | La costante obsoleta verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo di una costante contrassegnata come `@api` o di una costante privata nell&#39;implementazione. |
| 1235 | Override della costante `@deprecated` di Adobe Commerce | La costante obsoleta verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo di una costante contrassegnata come `@api` o di una costante privata nell&#39;implementazione. |
| 1236 | Assegnazione della costante `@deprecated` di Adobe Commerce | La costante obsoleta verrà rimossa nelle prossime versioni. Prendere in considerazione l&#39;utilizzo di una costante contrassegnata come `@api` o di una costante privata nell&#39;implementazione. |
| 1332 | Interfaccia `@deprecated` di Adobe Commerce importata | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile utilizzare un&#39;interfaccia o una classe contrassegnata come `@api`. |
| 1334 | Ha utilizzato l&#39;interfaccia di Adobe Commerce `@deprecated` | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile utilizzare un&#39;interfaccia o una classe contrassegnata come `@api`. |
| 1337 | Ereditato dall&#39;interfaccia di Adobe Commerce `@deprecated` | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l&#39;ereditarietà dell&#39;interfaccia utilizzando un&#39;interfaccia contrassegnata come `@api` o un&#39;interfaccia introdotta all&#39;interno dell&#39;implementazione. |
| 1338 | Implementazione dell&#39;interfaccia `@deprecated` di Adobe Commerce | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l&#39;ereditarietà dell&#39;interfaccia utilizzando un&#39;interfaccia contrassegnata come `@api` o un&#39;interfaccia introdotta all&#39;interno dell&#39;implementazione. |
| 1430 | Richiama metodo dataobject non dichiarato | I metodi magici non dichiarati possono essere modificati. Valuta invece l’utilizzo di metodi di interfaccia. |
| 1439 | Chiama metodo `@deprecated` di Adobe Commerce | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 1440 | Firma del metodo non corrispondente | È stata rilevata una chiamata o un override del metodo di base con parametri, argomenti o tipo restituito che non corrispondono alla firma del metodo. |
| 1534 | Utilizzo della proprietà `@deprecated` di Adobe Commerce | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 1535 | Ignorare la proprietà `@deprecated` di Adobe Commerce | La proprietà obsoleta verrà rimossa nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API o di utilizzare invece una proprietà privata all’interno dell’implementazione. |
| 1536 | Assegnazione della proprietà `@deprecated` di Adobe Commerce | Il metodo obsoleto verrà rimosso nelle prossime versioni. Valuta la possibilità di fare affidamento sui metodi dichiarati nelle interfacce API. |
| 5006 | I proxy e gli intercettori NON DEVONO mai essere esplicitamente richiesti nei costruttori | La classe originale deve essere dichiarata come tipo del parametro del costruttore. La classe Interceptor/Proxy verrà passata dall&#39;implementazione dell&#39;iniezione di dipendenza del framework. |
| 5074 | Rilevato utilizzo del metodo obsoleto `getResource()` per (salvare/caricare/eliminare) i dati. | Utilizza invece un archivio. |
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
