---
source-git-commit: 00b8e1bb5ee259763ddb2c52065cee2af98641e0
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Novità di ottobre 2024 di Adobe Commerce 2.4.7-beta

## In evidenza

Questa versione di Adobe Commerce include diverse correzioni di sicurezza critiche e miglioramenti alla piattaforma.

### Sicurezza

I seguenti miglioramenti di sicurezza in questa versione migliorano la conformità alle best practice di sicurezza più recenti:

>[!NOTE]
>
>Per informazioni aggiornate sulle correzioni dei bug di sicurezza, vedere [Adobe Security Bulletin APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Impostazioni</strong></td>
            <td>Questa versione include i seguenti miglioramenti alle impostazioni di sicurezza:
              <ul>
                <li><strong>Rotazione chiave di crittografia</strong>: è ora disponibile un nuovo comando CLI per la modifica della chiave di crittografia. Per ulteriori informazioni, vedere l'articolo della Knowledge Base relativo alla risoluzione dei problemi relativi alla rotazione delle chiavi di crittografia: CVE-2024-34102</a>.<a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102"><!-- AC-12589 --></li>
                <li><strong>Impostazioni password monouso (OTP)</strong>: questo aggiornamento è necessario per risolvere un errore introdotto da una <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">modifica non compatibile con le versioni precedenti</a> nella versione 2.4.7. La descrizione del campo <strong>[!UICONTROL OTP Window]</strong> fornisce ora una spiegazione accurata dell'impostazione e il valore predefinito è stato modificato da <code>1</code> a <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Piattaforma

I seguenti aggiornamenti di piattaforma per questa versione assicurano che Adobe Commerce rimanga una piattaforma solida e affidabile, pronta per soddisfare le esigenze dei moderni ambienti commerce:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Database</strong></td>
            <td>In linea con i <a href="/help/release/lifecycle-policy.md">criteri del ciclo di vita del supporto</a>, Adobe Commerce è ora compatibile con le seguenti versioni LTS (Long-term Support) delle seguenti tecnologie di database:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(supportato fino al 2029)_</em>: la versione precedente (MariaDB 10.6) ha raggiunto la fine del ciclo di vita nel 2026, rendendo questo aggiornamento essenziale per mantenere l'integrità e le prestazioni del sistema. MariaDB 10.6 è ancora supportato, ma l’Adobe consiglia di effettuare l’aggiornamento a MariaDB 11.4 quando si esegue l’aggiornamento ad Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(supportato fino al 2032)_</em>: la versione precedente (MySQL 8.0) ha raggiunto la fine del ciclo di vita nel 2026, rendendo questo aggiornamento essenziale per mantenere l'integrità e le prestazioni del sistema. MySQL 8.0 è ancora supportato, ma l’Adobe consiglia di eseguire l’aggiornamento a MySQL 8.4 quando si esegue l’aggiornamento ad Adobe Commerce 2.4.8</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Questa versione include i seguenti miglioramenti PHP:
            <ul>
              <li><strong>PHP 8.1</strong>: questa versione rimuove la compatibilità di PHP 8.1 per Adobe Commerce 2.4.8. Prima di eseguire l’aggiornamento ad Adobe Commerce 2.4.8, è necessario eseguire l’aggiornamento a PHP 8.3.</li>
              <li><strong>PHP 8.2</strong>: una delle modifiche più importanti di PHP 8.2 consiste nel rendere obsoleti i parametri della funzione interna che non ammettono i valori Null. Questa versione risolve le funzioni obsolete di PHP 8.1 nei componenti della piattaforma di base e garantisce la compatibilità con PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong>: questa versione risolve diversi problemi critici, migliora la compatibilità e assicura che il framework di test di Adobe Commerce sia allineato agli standard di settore più recenti. L'Adobe consiglia a tutti i fornitori di Commerci Marketplace e ai clienti con personalizzazioni di verificare che i test di unità e integrazione vengano eseguiti su PHPUnit 10 anziché su 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Componenti</strong></td>
            <td>I seguenti <a href="/help/release/packages/adobe-commerce.md">componenti e dipendenze</a> di terze parti sono stati aggiornati alle ultime versioni stabili per migliorare la stabilità e le prestazioni della piattaforma:
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monologo/monologo 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Ricerca</strong></td>
            <td>Adobe Commerce è ora ottimizzato per OpenSearch 2.x e non è più compatibile con Elasticsearch. Tutti i moduli e le classi Elasticsearch 7 e 8 sono ora obsoleti nel codebase. Adobe consiglia vivamente di passare a OpenSearch per implementazioni di infrastrutture sia on-premise che cloud, al fine di garantire supporto e compatibilità continui. Consulta <a href="/help/upgrade/prepare/opensearch-migration.md">Migrazione a OpenSearch</a>.
              <ul>
                <li>Le opzioni Elasticsearch 7 e Elasticsearch 8 ora sono etichettate come "(Obsoleto)" nella configurazione Admin.</li>
                <li>Quando un utente seleziona Elasticsearch come motore di ricerca nella configurazione Admin, Commerce visualizza una notifica con il seguente messaggio: <em>"Questa opzione del motore di ricerca non è più supportata da Adobe. È consigliabile utilizzare OpenSearch come motore di ricerca."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Prestazioni

Questa versione include i seguenti miglioramenti delle prestazioni:

<table style="table-layout:auto">
    <tbody>
        <tr>
            <td><strong>Indicizzatori</strong></td>
            <td>La modalità <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">indicizzatore</a> predefinita per tutti gli indicizzatori è ora [!UICONTROL **Update by Schedule**] quando si installa una nuova versione di Adobe Commerce o si esegue l'aggiornamento da una versione precedente. La nuova impostazione predefinita garantisce che gli indicizzatori siano nella configurazione consigliata, migliorando le prestazioni del sistema e riducendo potenziali problemi.</td>
        </tr>
    </tbody>
</table>

### Qualità

Questa versione include i seguenti miglioramenti della qualità:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Inventario</strong></td>
           <td>Il sistema ora funziona senza la dipendenza precedentemente nascosta da Catalog introdotta da InventoryIndexer, garantendo che la creazione del prodotto, il cambio della modalità di visualizzazione, la modifica dello stato del magazzino e altre funzionalità correlate funzionino come previsto. In precedenza, questa dipendenza nascosta causava incongruenze in quanto diverse entità venivano sincronizzate e l’indicizzatore utilizzava entità diverse.</td>
        </tr>
        <tr>
            <td><strong>Ordini</strong></td>
            <td>Per evitare confusione, l'etichetta del pulsante [!UICONTROL **Submit Comment**] è stata modificata in [!UICONTROL **Update**] nella pagina <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">dettagli ordine</a>.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Questa versione include i seguenti miglioramenti di GraphQL:

<table style="table-layout:auto">
    <tbody>
        <tr>
           <td><strong>Miglioramenti generali</strong></td>
           <td>Questa versione include i seguenti miglioramenti generali all’API di GraphQL:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: sono stati aggiunti i campi <code>grouped_product_image</code> e <code>configurable_product_image</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>.</li>
              <li><!--LYNX-387--><strong>CartItemPrice</strong>: sono stati aggiunti i seguenti nuovi campi al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> per supportare la visualizzazione precisa dei prezzi e i calcoli degli sconti:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>CartPrice</strong>: il campo <code>grand_total_excluding_tax</code> è stato aggiunto al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>, fornendo una chiara determinazione dei prezzi comprensiva di IVA.</li>
              <li><!--LYNX-542--><strong>mutazione updateCartItems</strong>: la mutazione <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> è stata aggiornata per restituire le risposte di successo con dettagli sull'errore anziché eccezioni. È stata migliorata la mappatura degli errori per migliorare la chiarezza delle notifiche degli utenti.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config query</strong>: introdotto un campo <code>theme</code> nella query <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>. Questo campo consente di specificare il nome del tema da utilizzare per il rendering del reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: è stato introdotto un campo <code>quantity</code> in <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> per fornire i dettagli del livello di stock. Vengono visualizzate le scorte disponibili o nulle in base alle impostazioni dell’amministratore.</li>
               <li><!--LYNX-460--><strong>Prodotti bundle</strong>: è stata corretta la visualizzazione dei prezzi per i prodotti bundle, garantendo informazioni precise su prezzo e valuta.</li>
               <li><!--LYNX-547--><strong>Quantità</strong>: messaggi perfezionati per notifiche quantità insufficienti e non disponibili.</li>
               <li><!--LYNX-541--><strong>Tipo InsufficienteStockError</strong>: aggiunto un nuovo tipo <code>InsufficientStockError</code> per gestire i casi in cui i livelli di azioni sono insufficienti. Lo schema è stato modificato per supportare nuovi tipi di errore, migliorando le funzionalità di segnalazione degli errori.</li>
               <li><!--LYNX-476--><strong>Importo inventario</strong>: messaggi di errore migliorati per includere gli importi di magazzino disponibili. Fornisce agli utenti informazioni più chiare sui livelli delle scorte durante gli aggiornamenti degli ordini.</li>
               <li><!--LYNX-377--><strong>Quantità richiesta</strong>: aggiunta di <code>not_available_message</code> a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gestione clienti</strong></td>
           <td>Questa versione include i seguenti miglioramenti alla gestione dei clienti:
             <ul>
               <li><!--LYNX-391--><strong>mutazione generateCustomerToken</strong>: la gestione degli errori nella mutazione <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> è stata perfezionata per fornire messaggi specifici per le e-mail non confermate. Supporta una migliore guida utente e la risoluzione degli errori.</li>
               <li><!--LYNX-390--><strong>mutazione resendConfirmationEmail</strong>: aggiunta nuova mutazione <code>resendConfirmationEmail</code> per l'invio di conferme e-mail.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Gestione ordini</strong></td>
           <td>Questa versione include i seguenti miglioramenti alla gestione degli ordini degli utenti:
             <ul>
              <li><!--LYNX-470--><strong>Data del primo ordine</strong>: aggiunto un nuovo campo <code>date_of_first_order</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>.</li>
              <li><!--LYNX-468--><strong>IndirizzoOrdine</strong>: esteso il tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> per includere attributi personalizzati, migliorando la visibilità dei dettagli dell'ordine. Supporta la visualizzazione di informazioni aggiuntive nelle pagine di conferma degli ordini.</li>
              <li><!--LYNX-458--><strong>query guestOrder e guestOrderByToken</strong>: le query <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> e <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> sono state aggiornate per includere attributi di indirizzo personalizzati, garantendo informazioni complete sull'indirizzo per i nuovi account.</li>
              <li><!--LYNX-450--><strong>Tipo CustomerOrder</strong>: il campo <code>is_virtual</code> è stato aggiunto al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>, per supportare l'identificazione del prodotto virtuale. Migliora l'elaborazione degli ordini distinguendo i prodotti virtuali da quelli fisici.</li>
              <li><!--LYNX-449--><strong>orderItemPrice</strong>: aggiunto un tipo <code>OrderItemPrices</code> simile a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> con diversi nuovi campi per il prezzo.</li>
              <li><!--LYNX-448--><strong>Unisci ordini guest</strong>: è stata migliorata la funzionalità API per unire gli ordini dei guest con gli account cliente in base alla corrispondenza delle e-mail. Gestione semplificata degli ordini per i clienti fidelizzati.</li>
              <li>Campo <!-- LYNX-523: --><strong>available_actions</strong>: esteso il tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> per includere un campo <code>available_actions</code> per una migliore gestione degli ordini. Il campo "available_actions" è associato a un’enumerazione che elenca le possibili azioni che possono essere eseguite sull’ordine.</li>
              <li><!-- LYNX-524 --><strong>Tipo CustomerOrder</strong>: aggiunto il campo <code>customer_info</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>. Questo campo richiede e <code>OrderCustomerInfo</code>, che definisce i dettagli sul nome del cliente.</li>
              <li><!--LYNX-519--><strong>Codici di errore per l'annullamento dell'ordine</strong>: aggiunti codici di errore dettagliati al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>. È stata migliorata la gestione degli errori e il feedback degli utenti per i processi di annullamento degli ordini.</li>
              <li><!--LYNX-515--><strong>Gli utenti guest sono stati abilitati a creare restituzioni per gli ordini</strong>: è stata modificata la mutazione <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> per supportare le restituzioni degli ordini dei guest.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong>: aggiunta nuova mutazione <code>confirmCancelOrder</code> per facilitare l'annullamento dell'ordine per gli utenti guest.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
