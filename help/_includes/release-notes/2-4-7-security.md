---
source-git-commit: 10a6329502bc63ec06bac0652301770bd8e2935a
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---
# 2.4.7 miglioramenti della sicurezza

Ad oggi non si sono verificati attacchi confermati relativi a questi problemi. Tuttavia, alcune vulnerabilità possono potenzialmente essere sfruttate per accedere alle informazioni dei clienti o assumere il controllo delle sessioni dell’amministratore. La maggior parte di questi problemi richiede che un utente malintenzionato ottenga prima l’accesso all’amministratore. Di conseguenza, ti ricordiamo di adottare tutte le misure necessarie per proteggere l’Amministratore, tra cui, ma non solo:

* INSERIRE NELL&#39;ELENCO CONSENTITI IP
* [Autenticazione a due fattori](https://developer.adobe.com/commerce/testing/functional-testing-framework/two-factor-authentication/)
* Utilizzo di una VPN
* Utilizzo di una posizione univoca anziché `/admin`
* Buona igiene della password

Miglioramenti di sicurezza per questa versione migliorano la conformità alle più recenti best practice di sicurezza.

* **Modifiche al comportamento delle chiavi della cache non generate**:

   * Le chiavi della cache non generate per i blocchi ora includono prefissi che differiscono dai prefissi per le chiavi generate automaticamente. Le chiavi della cache non generate sono chiavi impostate tramite la sintassi della direttiva del modello o `setCacheKey` o `setData` metodi.)
   * Le chiavi della cache non generate per i blocchi ora devono contenere solo lettere, cifre, trattini (-) e caratteri di sottolineatura (_).  <!-- AC-9831 -->

* **Limitazioni al numero di codici coupon generati automaticamente**. Commerce ora limita il numero di codici coupon generati automaticamente. Il valore massimo predefinito è 250.000. I commercianti possono utilizzare il nuovo **[!UICONTROL Code Quantity Limit]** opzione di configurazione (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) per evitare di sovraccaricare il sistema con molti coupon. <!-- AC-8753 -->

* **Ottimizzazione del processo predefinito di generazione URL amministratore**. La generazione dell’URL amministratore predefinito è ottimizzata per una maggiore casualità, il che rende gli URL generati meno prevedibili. <!-- AC-9028 -->

* **È stato aggiunto il supporto per l’integrità della sottorisorsa (SRI)** rispettare i requisiti PCI 4.0 per la verifica dell&#39;integrità dello script sulle pagine di pagamento. Il supporto per l’integrità della sottorisorsa (SRI) fornisce hash di integrità per tutte le risorse JavaScript residenti nel file system locale. La funzione SRI predefinita viene implementata solo nelle pagine di pagamento per le aree amministratore e vetrina. Tuttavia, i commercianti possono estendere la configurazione predefinita ad altre pagine. Consulta [Integrità della sottorisorsa](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) nel _Guida per gli sviluppatori di Commerce PHP_.<!--AC-1153-->

* **Modifiche a Content Security Policy (CSP)**: aggiornamenti della configurazione e miglioramenti apportati ai criteri di sicurezza dei contenuti (CSP, Content Security Policy) di Adobe Commerce per garantire la conformità ai requisiti PCI 4.0. Per ulteriori informazioni, consulta [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) nel _Guida per gli sviluppatori di Commerce PHP_. <!--AC-11513-->

   * La configurazione CSP predefinita per le pagine di pagamento per le aree di amministrazione e vetrina di Commerce è ora `restrict` modalità. Per tutte le altre pagine, la configurazione predefinita è `report-only` modalità.  Nelle versioni precedenti alla 2.4.7, CSP era configurato in `report-only` per tutte le pagine.

   * È stato aggiunto un provider nonce per consentire l’esecuzione di script in linea in un CSP. Il provider di nonce facilita la generazione di stringhe di nonce univoche per ogni richiesta. Le stringhe vengono quindi collegate all’intestazione CSP.

   * Sono state aggiunte opzioni per configurare URI personalizzati in modo da segnalare le violazioni CSP per le pagine Crea ordine in Amministrazione e Pagamento nella vetrina. Puoi aggiungere la configurazione dall’amministratore o aggiungendo l’URI al file `config.xml` file.

     >[!NOTE]
     >
     >Aggiornamento della configurazione CSP a `restrict` La modalità potrebbe bloccare gli script in linea esistenti sulle pagine di pagamento in Admin e storefront, causando il seguente errore del browser quando viene caricata una pagina: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Correggi questi errori aggiornando la configurazione della whitelist per consentire gli script richiesti. Consulta [Risoluzione dei problemi](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) nel _Guida per gli sviluppatori di Commerce PHP_.

* Una nuova impostazione di configurazione della cache a pagina intera può aiutare a mitigare i rischi associati al `{BASE-URL}/page_cache/block/esi` endpoint. Questo endpoint supporta frammenti di contenuto senza restrizioni e caricati dinamicamente dagli handle di layout e dalle strutture di blocco di Commerce. Il nuovo **[!UICONTROL Handles params size]** L&#39;impostazione di configurazione imposta il valore dell&#39;endpoint `handles` , che determina il numero massimo consentito di handle per API. Il valore predefinito di questa proprietà è 100. Gli esercenti possono modificare questo valore da Admin (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles params size]**). Consulta [Configurare l&#39;applicazione Commerce per l&#39;utilizzo di Vernice](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/configure-varnish-commerce.html). <!-- AC-9113 -->

* **Limitazione della tariffa nativa per le informazioni di pagamento trasmesse tramite API REST e GraphQL**. Gli esercenti ora possono [configurare la limitazione della frequenza](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales#rate-limiting) per le informazioni di pagamento trasmesse utilizzando REST e GraphQL. Questo livello di protezione aggiuntivo supporta la prevenzione degli attacchi di carte di credito e potenzialmente riduce il volume di attacchi di carte di credito che testano molti numeri di carta di credito contemporaneamente. Si tratta di una modifica del comportamento predefinito di un endpoint REST esistente. Consulta [Limitazione di velocità](https://developer.adobe.com/commerce/webapi/get-started/rate-limiting/).

* Il comportamento predefinito del [isEmailAvailable](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) query GraphQL e ([V1/customers/isEmailAvailable](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)a) L&#39;endpoint REST è stato modificato. Per impostazione predefinita, le API ora restituiscono sempre `true`. I commercianti possono abilitare il comportamento originale impostando *[Abilita accesso per estrazione guest](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/checkout)* opzione in Admin to `yes`, ma in questo modo è possibile esporre le informazioni del cliente a utenti non autenticati.
