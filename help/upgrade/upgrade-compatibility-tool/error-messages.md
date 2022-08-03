---
title: '"[!DNL Upgrade Compatibility Tool] Messaggi di errore"'
description: Ulteriori informazioni sui messaggi di errore riscontrati durante l’utilizzo del [!DNL Upgrade Compatibility Tool] sul progetto Adobe Commerce.
source-git-commit: a13b0ea5aa109ce2f5d33e0966b194d64bad5d0c
workflow-type: tm+mt
source-wordcount: '3781'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool] messaggi di errore

{{commerce-only}}

Questo riferimento al messaggio di errore fornisce informazioni sugli errori che possono verificarsi durante l&#39;esecuzione [!DNL Upgrade Compatibility Tool].

I messaggi di errore sono organizzati per livello (problemi critici, errori e avvisi) e per tipo (codice di base, codice personalizzato e schemi GraphQL). Ogni tipo contiene le seguenti informazioni:

- **Codice di errore**: Identificatore assegnato da Adobe Commerce per il messaggio di errore.
- **Descrizione errore**: Descrizione che riepiloga la causa dell’errore.
- **Errore nell&#39;azione suggerita**: Se applicabile, fornisce indicazioni per la risoluzione dei problemi e la risoluzione dell’errore.

## Problemi critici

### Codice core

Questi errori vengono segnalati quando alcuni dei file di base sono mancanti o non corrispondono all&#39;originale.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 2001 | File di base non trovato | Esegui il `composer install` dalla directory principale del progetto. |
| 2002 | Il file core è stato modificato | Esegui il `composer install` dalla directory principale del progetto. |
| 2003 | La dipendenza del compositore non è installata | La dipendenza del compositore mancante può potenzialmente causare problemi. Ripristina dipendenza tramite esecuzione `composer require package_name`. |
| 2005 | Cartella core non trovata | Esegui il `composer install` dalla directory principale del progetto. |

{style=&quot;table-layout:auto&quot;}

### Codice personalizzato

Gli errori critici vengono generati quando il codice personalizzato fa riferimento a entità che non sono presenti nella versione Adobe Commerce di destinazione. Questi errori sono segnalati anche quando gli standard critici di codifica sono stati infranti.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 1 110 | Istanza di una classe/interfaccia Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. Creazione di un&#39;istanza di classe/interfaccia Adobe Commerce inesistente. |
| 111 | Estensione dalla classe Adobe Commerce inesistente | La classe estesa non è più presente nel codebase. L’ereditarietà non è consigliata per estendere la funzionalità Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 112 | Importazione di una classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 113 | Caricamento della classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 114 | Utilizzo di una classe Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1214 | Utilizzo di una costante Adobe Commerce inesistente | Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1215 | Ignorare una costante Adobe Commerce inesistente | Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1216 | Assegnazione di una costante Adobe Commerce inesistente | Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1312 | Interfaccia Adobe Commerce non esistente importata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1314 | Interfaccia Adobe Commerce inesistente utilizzata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1317 | Interfaccia Adobe Commerce non esistente ereditata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1318 | Interfaccia Adobe Commerce inesistente implementata | È consigliabile rimuovere l’ereditarietà o sostituirla con l’interfaccia introdotta nell’ambito della personalizzazione. |
| 1410 | Chiama metodo Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1514 | Utilizzo di proprietà Adobe Commerce inesistenti | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1515 | Ignorare la proprietà Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1516 | Assegnazione della proprietà Adobe Commerce inesistente | Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. Aggiorna il livello di accesso alla proprietà a private se può essere utilizzato solo all&#39;interno di una singola classe. |
| 5002 | Il tag PHP di apertura deve essere il primo contenuto del file | Assicurati che non ci sia contenuto nel file prima del tag di apertura PHP. |
| 5003 | Funzione obsoleta | Utilizza una sostituzione suggerita nel messaggio di errore. Se il messaggio non suggerisce una sostituzione, è necessaria una stretta revisione per selezionare una funzione o un’implementazione alternativa. |
| 5005 | Errore di sintassi PHP | Il codice deve essere aggiornato per conformarsi agli standard di sintassi PHP. |
| 5072 | Possibile violazione del Magento 2. Rilevata una tipica costruzione di Magento 1.x | Aggiornare la costruzione agli standard del Magento 2. |
| 5076 | Impossibile utilizzare nello spazio dei nomi perché è riservato da PHP 7 | Sostituisci la parola riservata nello spazio dei nomi con una parola chiave non riservata. |
| 5077 | Impossibile utilizzare come nome di classe perché è riservato da PHP 7 | Sostituire il nome della classe riservata con un nome non riservato. |

{style=&quot;table-layout:auto&quot;}

### Schema GraphQL

I problemi critici dello schema GraphQL vengono sollevati se gli elementi dello schema non sono presenti nella versione di destinazione.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 3101 | Il tipo è stato rimosso | Elenca tutte le query che fanno riferimento a questo campo. Controlla se queste query vengono utilizzate dall&#39;implementazione di personalizzazione. Aggiorna il codice client per gestire l&#39;interfaccia di query modificata. |
| 3102 | Tipo rimosso dall&#39;unione | Se il tipo di unione viene utilizzato nella costruzione della richiesta GraphQL o nell&#39;implementazione dell&#39;elaborazione della risposta, potrebbe essere necessario aggiornarlo. |
| 3103 | Campo rimosso | Controlla se al campo viene fatto riferimento nel codebase di personalizzazione. Regola l’implementazione per gestire correttamente il nuovo tipo di campo. |
| 3105 | Interfaccia implementata rimossa | Controlla se il tipo che implementa l&#39;interfaccia rimossa viene utilizzato nella personalizzazione. Potrebbe essere necessario aggiornare l’implementazione se si basa sull’interfaccia rimossa. |
| 3106 | Valore rimosso dall&#39;enum | Se il valore enum rimosso viene utilizzato nella costruzione della richiesta GraphQL o nell&#39;implementazione dell&#39;elaborazione della risposta, potrebbe essere necessario aggiornarlo. |
| 3107 | Argomento rimosso | Controlla se il campo è utilizzato nella base di codice di personalizzazione. Rimuovere l&#39;argomento per questo campo. |
| 3109 | Rimozione della direttiva | Controlla se la direttiva è utilizzata nel codebase di personalizzazione. Adeguare l&#39;attuazione per rimuovere il riferimento alla direttiva. |
| 3110 | Argomento della direttiva rimosso | Controlla se la direttiva è utilizzata nel codebase di personalizzazione. Rimuovere l&#39;argomento della direttiva. |
| 311 | Rimozione ripetibile della direttiva | Controlla se la direttiva è utilizzata nel codebase di personalizzazione. Regola l’implementazione per gestire le modifiche all’interfaccia. |
| 3112 | Posizione della direttiva rimossa | Controlla se la direttiva è utilizzata nel codebase di personalizzazione. Regola l’implementazione per gestire le modifiche all’interfaccia. |
| 3201 | Tipo modificato | Elenca tutte le query che fanno riferimento a questo campo. Controlla se queste query vengono utilizzate dall&#39;implementazione di personalizzazione. Aggiorna il codice client per gestire l&#39;interfaccia di query modificata. |
| 3203 | Tipo di campo modificato | Controlla se al campo viene fatto riferimento nel codebase di personalizzazione. Regola l’implementazione per gestire correttamente il nuovo tipo di campo. |
| 3207 | Tipo di argomento modificato | Controlla se il campo è utilizzato nella base di codice di personalizzazione. Aggiorna il tipo di argomento per questo campo. |
| 3303 | Campo di input obbligatorio aggiunto | Il campo deve essere aggiunto alla richiesta se per la personalizzazione viene utilizzata la query che include questo campo. |
| 3307 | Argomento obbligatorio aggiunto | Controlla se il campo è utilizzato nella base di codice di personalizzazione. Il nuovo argomento obbligatorio deve essere specificato quando si utilizza il campo . |
| 3310 | Argomento obbligatorio della direttiva aggiunto | Controlla se la direttiva è utilizzata nel codebase di personalizzazione. Aggiungi l&#39;argomento direttiva. |

{style=&quot;table-layout:auto&quot;}

## Errori

### Codice personalizzato

Gli errori di codice personalizzato vengono generati quando il codice personalizzato utilizza punti di ingresso Adobe Commerce che non sono considerati/contrassegnati come `@api`. Il comportamento mantenuto di tali punti di ingresso non è garantito. La personalizzazione dovrebbe basarsi su `@api` punti di ingresso. La funzionalità basata su codice Adobe Commerce non API deve essere testata dopo l’aggiornamento. Questi errori sono segnalati anche quando i principali standard di codifica sono stati infranti.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 1104 | Utilizzo di una classe non API che eredita l’interfaccia API | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice per basarsi sull’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1121 | Estensione dalla classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. L’ereditarietà non è consigliata per estendere la funzionalità Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1122 | Importazione di una classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1123 | Caricamento della classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1124 | Utilizzo della classe API non Adobe Commerce | La classe estesa non è più presente nel codebase. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1224 | Utilizzo di una costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1225 | Ignorare la costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1226 | Assegnazione di una costante API non Adobe Commerce | Costanti non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1322 | Interfaccia API non Adobe Commerce importata | Interfacce non contrassegnate come `@api` possono essere modificate. È consigliabile rimuovere l’ereditarietà o sostituirla con l’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1324 | Interfaccia API utilizzata non di Adobe Commerce | Interfacce non contrassegnate come `@api` possono essere modificate. È consigliabile rimuovere l’ereditarietà o sostituirla con l’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1327 | Interfaccia API non Adobe Commerce ereditata | Costanti non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’introduzione e l’utilizzo di una costante privata del valore richiesto all’interno del codice personalizzato. |
| 1328 | Interfaccia API non Adobe Commerce implementata | Interfacce non contrassegnate come `@api` possono essere modificate. È consigliabile rimuovere l’ereditarietà o sostituirla con l’ereditarietà dall’interfaccia di Adobe Commerce contrassegnata come `@api` o un&#39;interfaccia introdotta nell&#39;ambito del codice di personalizzazione. |
| 1420 | Istanza di una classe/interfaccia API non Adobe Commerce | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice per basarsi sull’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. Inoltre, il modo consigliato per recuperare un&#39;istanza della classe è quello di utilizzare l&#39;ID. Considera l&#39;utilizzo di una fabbrica se è necessaria una nuova istanza della classe. |
| 1428 | Possibile dipendenza dai dettagli di implementazione. | Classi non contrassegnate come `@api` possono essere modificate. Prendi in considerazione l’aggiornamento del codice per basarsi sull’interfaccia contrassegnata come `@api` invece. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1429 | Metodi API per chiamate non Adobe Commerce | Metodi non contrassegnati come `@api` o non sono dichiarati all’interno della classe/interfaccia API possono essere modificati. Anche se l’interfaccia del metodo non viene aggiornata nella nuova versione, il suo comportamento o il suo output possono essere diversi. Considera l’utilizzo di un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1449 | Chiamata al metodo non di interfaccia (presente nell’implementazione) | I metodi non dichiarati nell’interfaccia possono essere modificati. Considera l’utilizzo di un metodo di interfaccia. In caso contrario, la funzionalità che si basa su questa implementazione deve essere testata dopo l’aggiornamento. |
| 1524 | Utilizzo di proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Al suo posto, considera l’utilizzo del metodo di interfaccia API . |
| 1525 | Sovrascrittura della proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Al suo posto, considera l’utilizzo del metodo di interfaccia API . |
| 1526 | Assegnazione di proprietà API non Adobe Commerce | Valori delle proprietà non contrassegnate come `@api` possono essere modificate. Al suo posto, considera l’utilizzo del metodo di interfaccia API . |
| 5004 | Funzione senza argomento obsoleta | Passa l’input da convalidare come primo argomento della funzione . |
| 5007 | L&#39;uso di talune funzioni è scoraggiato | Evita di utilizzare queste funzioni. |
| 5009 | Le direttive modello non possono richiamare metodi. È consentito solo l’accesso all’array scalare | Rimuovi chiamate di metodo dal modello. |
| 5010 | Modello `@vars` blocco di commento contiene JSON non valido | Correggi JSON non valido. |
| 5011 | Modello `@vars` blocco di commento contiene un&#39;etichetta non valida | Correggi etichetta non valida. |
| 5012 | Modello `@vars` nel blocco dei commenti manca una variabile utilizzata nel modello | Aggiungi la variabile mancante al blocco di commenti @vars. |
| 5013 | Evita di usare il tag di chiusura automatica con un elemento html non vuoto | Utilizza piuttosto il tag di chiusura . |
| 5014 | La `"active"` attributo obsoleto | L’elenco dei moduli attivi è definito nella configurazione della distribuzione. |
| 5015 | La `<param>` nodo obsoleto | Utilizzo `<argument name="..." xsi:type="...">` invece. |
| 5016 | La `<instance>` nodo obsoleto | Utilizzo `<argument name="..." xsi:type="object">` invece. |
| 5017 | La `<array>` nodo obsoleto | Utilizzo `<argument name="..." xsi:type="array">` invece. |
| 5018 | La `<item key="...">` nodo obsoleto | Utilizzo `<item name="..." xsi:type="...">` invece. |
| 5019 | La `<value>` nodo obsoleto | Fornisci invece il valore effettivo come letterale di testo. |
| 5020 | Nodo obsoleto: `<supported_blocks>` | Da sostituire con `<supported_containers>`. |
| 5021 | Nodo obsoleto: `<block_name>` | Da sostituire con `<container_name>`. |
| 5022 | Nome di fabbrica rilevato | Il tipo di widget non deve iniziare con /. |
| 5023 | Struttura ACL obsoleta rilevata in linea | Controlla lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Struttura del menu obsoleta rilevata in linea | Controlla app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | Struttura di configurazione del sistema obsoleta rilevata nel file | Controlla app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Non utilizzare `"text/javascript"` tipo di attributo | Utilizza solo membri pubblici. |
| 5028 | Accesso ai membri protetti e privati `Block` Classe obsoleta nei modelli phtml | Utilizza solo membri pubblici. |
| 5031 | Contiene un metodo obsoleto | Utilizzo `getConnection()` invece. |
| 5042 | Formato non corretto del riferimento di classe PHP | Verificare che venga fatto riferimento alla classe utilizzando solo lettere camelCased, numeri e nessuna barra iniziale. |
| 5043 | Formato non corretto del riferimento del modulo | Verificare che al modulo venga fatto riferimento utilizzando solo lettere, numeri, caratteri di sottolineatura e nessuna barra iniziale. |
| 5044 | Classe `Zend_Db_Select` è limitato | Sostituzione consigliata: `\Magento\Framework\DB\Select`. |
| 5045 | Classe `Zend_Db_Adapter_Pdo_Mysql` è limitato | Sostituzione consigliata: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Classe `Magento\Framework\Serialize\Serializer\Serialize` è limitato | Sostituzione consigliata: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Classe `ArrayObject` è limitato | Sostituzione consigliata: Classe personalizzata, estesa da `ArrayObject` con metodi di serializzazione/deserializzazione sovrascritti. |
| 5048 | Classe `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` è limitato | Sostituzione consigliata: Factory che crea classe personalizzata, estesa da `ArrayObject` con metodi di serializzazione/deserializzazione sovrascritti. |
| 5050 | Il blocco a cui si fa riferimento viene rimosso | Rimuovi il riferimento al blocco. |
| 5051 | `output="toHtml"` obsoleto | Utilizzo `output="1"`. |
| 5052 | Classe `\Magento\Framework\View\Element\Text\ListText` non deve più essere utilizzato nel layout | Rimuovi classe `\Magento\Framework\View\Element\Text\ListText` dal layout. |
| 5053 | Chiamata del metodo tramite istruzioni di layout `<action>` non consentito | Evita di utilizzare il metodo offensivo in `<action>`. |
| 5054 | `helper` attributo contiene `/` | Rimuovi `/` dall&#39;attributo helper. |
| 5055 | `helper` l&#39;attributo non contiene `::` | Aggiungi `::` all&#39;attributo helper. |
| 5056 | Gli script di installazione sono obsoleti | Utilizza l&#39;approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo\. |
| 5057 | Gli script InstallSchema sono obsoleti | Utilizza l&#39;approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo\. |
| 5058 | Gli script InstallData sono obsoleti | Utilizza l&#39;approccio delle patch dati in Setup/Patch/Data dir del modulo\. |
| 5059 | Gli script di installazione sono obsoleti | Crea una classe InstallData nella cartella Setup del modulo. |
| 5060 | Gli script di aggiornamento sono obsoleti | Utilizza l&#39;approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo\. |
| 5061 | Gli script UpgradeSchema sono obsoleti | Utilizza l&#39;approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo\. |
| 5062 | Gli script UpgradeData sono obsoleti | Utilizza l&#39;approccio delle patch dati in Setup/Patch/Data dir del modulo\. |
| 5063 | Gli script di aggiornamento sono obsoleti | Utilizza l&#39;approccio delle patch dati nella directory di configurazione/patch/dati del modulo. |
| 5064 | Gli script ricorrenti sono obsoleti | Crea classe ricorrente nella cartella Setup del modulo. |
| 5065 | &#39;data&#39; in una directory non valida | Crea una patch dati nella cartella Setup/Patch/Data del modulo per gli aggiornamenti dei dati o utilizza l’approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo per le modifiche dello schema. |
| 5066 | &#39;sql&#39; in una directory non valida | Crea una patch dati nella cartella Setup/Patch/Data del modulo per gli aggiornamenti dei dati o utilizza l’approccio dello schema dichiarativo nel file etc/db_schema.xml del modulo per le modifiche dello schema. |
| 5067 | I nodi identificati da XPath sono obsoleti | XML obsoleto indicato nell&#39;errore deve essere aggiornato. Segui i suggerimenti del messaggio di errore. |
| 5068 | Direttiva `{{htmlescape}}` obsoleto | Utilizzo `{{var}}` invece. |
| 5069 | Direttiva `{{escapehtml}}` obsoleto | Utilizzo `{{var}}` invece. |
| 5070 | Il terzo parametro non è più necessario per `getChildHtml()` | Rimuovi il terzo parametro dalla chiamata a `getChildHtml()`. |
| 5071 | Il quarto parametro non è più necessario per `getChildHtml()` | Rimuovi il quarto parametro dalla chiamata a `getChildHtml()`. |
| 5073 | I nomi di tabella legacy con barra devono essere fissati in modo da indirizzare i nomi di tabella | Utilizzare invece il nome della tabella diretta. |
| 5075 | I moduli di applicazione non devono utilizzare le classi dei moduli di prova | Rimuovi l&#39;uso delle classi dai moduli di test. |
| 5078 | La classe deve essere richiesta nel costruttore, altrimenti il compilatore non sarà in grado di trovare e generare queste classi | Aggiungi la classe al costruttore. |
| 5079 | L&#39;uso di variabili della classe var è scoraggiato | Evita di usare &#39;var&#39; per dichiarare la variabile di classe. |
| 5080 | Possibile istruzione SQL non elaborata rilevata | In alternativa, utilizza archivi o patch dati. |
| 5081 | L&#39;uso di aiutanti nei modelli è scoraggiato | Utilizzare invece ViewModel. |
| 5082 | L’utilizzo di $this nei modelli è obsoleto | Utilizza invece $block. |
| 5083 | Le costanti non sono consentite come primo argomento della funzione di traduzione | Utilizzare invece il valore letterale stringa. |
| 5085 | L&#39;uso di talune funzioni è scoraggiato | Utilizza invece la funzione alternativa consigliata sul messaggio. |
| 5087 | Problema di compatibilità tra versioni diverse di PHP | Segui i suggerimenti del messaggio e controlla il [guida alla migrazione](https://www.php.net/manual/en/migration81.php). |
| 5088 | Parametri opzionali trovati dopo quelli richiesti | Sposta i parametri richiesti dopo quelli facoltativi. |
| 5089 | Visibilità dei metodi `final private` trovato | Cambia visibilità metodo da `final private` solo `private`. |
| 5090 | Metodo magico `__set_state` non è definito come `static` | Metodo magico `__set_state` deve essere definito come `static`. |
| 5091 | Classe con `__toString()` metodo non ereditato da `Stringable` interfaccia | Aggiungi `Stringable` interfaccia a classe con `__toString()` metodo . |
| 5092 | `is_resource()` metodo utilizzato per le funzioni che ora restituiscono Object | Modifica `is_resource()` a `instanceof` Oggetto. |
| 6001 | `jQuery.andSelf()` rimosso | Utilizzo `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` e `$.unbind` sono obsoleti | Utilizzo `$.on` e `$.off` invece. |
| 6003 | Il metodo jQuery per la sottoscrizione a un evento è obsoleto e non deve essere utilizzato | Utilizzo `.on("event name", fn)` per effettuare la sottoscrizione a tale evento. |
| 6003 | Il metodo jQuery per attivare l’evento è obsoleto e non deve essere utilizzato | Utilizzo `.trigger("event name")` per attivare l&#39;evento. |
| 6004 | jQuery `$.delegate` e `$.undelegate` sono obsoleti | Utilizzo `$.on` e `$.off` invece. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) è stato rimosso | Usa (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`). |
| 6006 | `jQuery.size()` rimosso | Utilizzo `jQuery.length`. |
| 6007 | `jQuery.trim` è obsoleto | Utilizzo `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, tema &quot;inlite&quot;, tema &quot;mobile&quot;, tema &quot;moderno&quot;) è rimosso | Aggiorna il codice per renderlo compatibile con tinymce5. |
| 6009 | `jQuery.isFunction()` è obsoleto | Nella maggior parte dei casi, può essere sostituito da [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` è obsoleto | Sostituisci con un controllo di tipo appropriato [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` è obsoleto | Utilizzare invece il metodo nativo Array.isArray. |
| 6009 | `jQuery.parseJSON()` è obsoleto | Per analizzare le stringhe JSON, utilizza invece il metodo nativo JSON.parse . |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) è obsoleto | Utilizza invece jQuery.expr.pseudo. |

{style=&quot;table-layout:auto&quot;}

## Avvisi

### Codice core

Questi avvisi vengono segnalati quando ci sono incongruenze minori nella base di codice principale.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 2004 | Mancata corrispondenza della versione della dipendenza del compositore | Il problema indica che la versione della dipendenza del Compositore in etalon e nel progetto effettivo è diversa. Aggiornare la dipendenza tramite esecuzione `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### Codice personalizzato

Gli avvisi relativi al codice personalizzato vengono generati quando vengono rilevati riferimenti a codice obsoleto. Tali riferimenti devono essere sostituiti con i punti di estensione supportati. Presta attenzione al `@see` annotazione dell’elemento obsoleto per i consigli. Questi errori sono segnalati anche quando sono stati infranti gli standard di codifica minori.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 1 131 | Estensione da Adobe Commerce ``@deprecated`` Classe | La classe estesa verrà rimossa nelle prossime versioni. L’ereditarietà non è consigliata per estendere la funzionalità Adobe Commerce. Aggiorna il codice per utilizzare una classe contrassegnata come `@api`. |
| 1 132 | Importazione di Adobe Commerce `@deprecated` Classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1 133 | Caricamento di Adobe Commerce `@deprecated` Classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1 134 | Utilizzo di Adobe Commerce `@deprecated` Classe | La classe estesa verrà rimossa nelle prossime versioni. Valuta l’utilizzo della classe Adobe Commerce contrassegnata come `@api` invece. |
| 1234 | Utilizzo di Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Considera l&#39;utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1235 | Sovrascrittura di Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Considera l&#39;utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1236 | Assegnazione di Adobe Commerce `@deprecated` costante | La costante obsoleta verrà rimossa nelle prossime versioni. Considera l&#39;utilizzo di una costante contrassegnata come `@api` o una costante privata all’interno dell’implementazione. |
| 1332 | Adobe Commerce importato `@deprecated` interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. Valutare l&#39;utilizzo di un&#39;interfaccia o di una classe contrassegnata come `@api` invece. |
| 1334 | Usato Adobe Commerce `@deprecated` interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. Valutare l&#39;utilizzo di un&#39;interfaccia o di una classe contrassegnata come `@api` invece. |
| 1337 | Ereditato da Adobe Commerce `@deprecated` interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l’ereditarietà dell’interfaccia, utilizzando un’interfaccia contrassegnata come `@api` o un’interfaccia introdotta al suo interno. |
| 1338 | Implementazione di Adobe Commerce `@deprecated` interfaccia | L’interfaccia obsoleta verrà rimossa nelle prossime versioni. È consigliabile rimuovere l’ereditarietà dell’interfaccia, utilizzando un’interfaccia contrassegnata come `@api` o un’interfaccia introdotta al suo interno. |
| 1430 | Chiama metodo dataobject non dichiarato | I metodi magici non dichiarati possono essere modificati. Al suo posto, considera l’utilizzo di metodi di interfaccia. |
| 1439 | Chiama Adobe Commerce `@deprecated` metodo | Il metodo obsoleto verrà rimosso nelle prossime versioni. Al suo posto, considera l’utilizzo di metodi dichiarati nelle interfacce API. |
| 1440 | Mancata corrispondenza della firma del metodo | Viene rilevata una chiamata o un&#39;override del metodo core con parametri, argomenti o tipi restituiti che non corrispondono alla firma del metodo. |
| 1534 | Utilizzo di Adobe Commerce `@deprecated` property | Il metodo obsoleto verrà rimosso nelle prossime versioni. Al suo posto, considera l’utilizzo di metodi dichiarati nelle interfacce API. |
| 1535 | Sovrascrittura di Adobe Commerce `@deprecated` property | La proprietà obsoleta verrà rimossa nelle prossime versioni. Prendi in considerazione l’utilizzo di metodi dichiarati nelle interfacce API o di una proprietà privata all’interno dell’implementazione. |
| 1536 | Assegnazione di Adobe Commerce `@deprecated` property | Il metodo obsoleto verrà rimosso nelle prossime versioni. Al suo posto, considera l’utilizzo di metodi dichiarati nelle interfacce API. |
| 5006 | I proxy e gli intercettatori NON DEVONO mai essere richiesti esplicitamente nei costruttori | La classe originale deve essere dichiarata come un tipo del parametro del costruttore. La classe intercettore/proxy verrà passata dall&#39;implementazione dell&#39;iniezione di dipendenza del framework. |
| 5074 | Uso del metodo obsoleto `getResource()` Rilevati dati su (salvataggio/caricamento/eliminazione). | In alternativa, utilizza un archivio. |
| 5086 | Visibilità non dichiarata su una costante | Dichiara la visibilità su tutte le costanti. |

{style=&quot;table-layout:auto&quot;}

### Schema GraphQL

Gli avvisi relativi allo schema GraphQL vengono generati quando gli elementi aggiuntivi vengono aggiunti allo schema nella nuova versione. Si consiglia di rivedere l&#39;implementazione per vedere se deve essere utilizzata per le richieste.

| Codice di errore | Descrizione errore | Azione consigliata |
| --- | --- | --- |
| 3206 | Valore predefinito argomento modificato | Se la query viene utilizzata nella personalizzazione, potrebbe essere necessario specificare esplicitamente il valore dell&#39;argomento. |
| 3302 | Tipo aggiunto all’unione | Il tipo è stato aggiunto all&#39;unione. Controlla l&#39;implementazione che elabora il risultato della query che restituisce questo tipo di unione e assicurati che sia in grado di gestire il tipo aggiunto. |
| 3304 | Campo di ingresso opzionale aggiunto | È stato aggiunto un campo di input facoltativo. Controlla l’implementazione per assicurarti. |
| 3305 | È stata aggiunta l’interfaccia implementata | Il campo può accettare o fornire ulteriori informazioni che possono essere prese in considerazione nell’implementazione. |
| 3306 | Valore aggiunto all&#39;enum | Un valore è stato aggiunto a un enum. Se i client contengono un&#39;istruzione switch sul valore dell&#39;enum e non includono un caso predefinito, questa modifica potrebbe causare un comportamento imprevisto. |
| 3308 | Argomento facoltativo aggiunto | Se la query utilizza un nuovo argomento nella personalizzazione, potrebbe essere necessario aggiungerlo alla richiesta. |

{style=&quot;table-layout:auto&quot;}
