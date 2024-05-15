---
title: Best practice per le prestazioni del checkout
description: Scopri come ottimizzare le prestazioni delle esperienze di pagamento sul tuo sito Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Best practice per le prestazioni del checkout

Il [pagamento](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) processo in Adobe Commerce è un aspetto critico dell’esperienza di vetrina. Si basa sul [carrello](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) e [pagamento](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) funzionalità.

Le prestazioni sono fondamentali per mantenere una buona esperienza utente. Rivedi [riepilogo benchmark prestazioni](../implementation-playbook/infrastructure/performance/benchmarks.md) per ulteriori informazioni sulle aspettative relative alle prestazioni. È possibile ottimizzare le prestazioni di pagamento configurando le seguenti opzioni per **elaborazione degli ordini con throughput elevato**:

- [AsyncOrder](#asynchronous-order-placement)- Elabora in modo asincrono gli ordini utilizzando una coda.
- [Calcolo del totale differito](#deferred-total-calculation)- Differisce i calcoli per i totali dell&#39;ordine fino all&#39;inizio del pagamento.
- [Controllo magazzino al caricamento del carrello](#disable-inventory-check)- Consente di ignorare la convalida dell&#39;inventario degli articoli del carrello.
- [Bilanciamento del carico](#load-balancing)- Attiva connessioni secondarie per il database MySQL e l&#39;istanza Redis.

Le opzioni di configurazione AsyncOrder, Deferred Total Calculation e Inventory Check on Cart Load funzionano tutte in modo indipendente. Potete utilizzare tutte e tre le feature contemporaneamente oppure attivarle e disattivarle in qualsiasi combinazione.

>[!NOTE]
>
>Non utilizzare codice PHP personalizzato per personalizzare le funzionalità integrate del carrello e del pagamento. Oltre a potenziali problemi di prestazioni, l&#39;utilizzo di un codice PHP personalizzato può causare complessi problemi di aggiornamento e manutenzione. Questi problemi aumentano il costo totale di proprietà. Se la personalizzazione del carrello e del pagamento basato su PHP è inevitabile, utilizza [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)Solo estensioni approvate da. Tutte le estensioni del marketplace sono soggette a [recensione completa](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) per verificare che soddisfino gli standard di codifica e le best practice di Adobe Commerce.

## Posizionamento dell’ordine asincrono

Il _Ordine asincrono_ Il modulo consente il posizionamento asincrono dell’ordine, che contrassegna l’ordine come `received`, inserisce l&#39;ordine in una coda ed elabora gli ordini dalla coda in base al primo ordine in uscita. AsyncOrder è **disabilitato** per impostazione predefinita.

Ad esempio, un cliente aggiunge un prodotto al carrello e seleziona **[!UICONTROL Proceed to Checkout]**. Compilano il **[!UICONTROL Shipping Address]** modulo, seleziona il modulo preferito **[!UICONTROL Shipping Method]**, selezionare un metodo di pagamento e inoltrare l&#39;ordine. Il carrello viene cancellato, l’ordine è contrassegnato come **[!UICONTROL Received]**, ma la quantità di prodotto non è ancora stata regolata e non viene inviata al cliente un’e-mail di vendita. L&#39;ordine viene ricevuto, ma i dettagli dell&#39;ordine non sono ancora disponibili perché l&#39;ordine non è stato completamente elaborato. Rimane in coda fino al `placeOrderProcess` il consumatore inizia, verifica l’ordine con [controllo di inventario](#disable-inventory-check) (attivata per impostazione predefinita) e aggiorna l’ordine come segue:

- **Prodotto disponibile**- lo stato dell&#39;ordine viene modificato in _In sospeso_, la quantità del prodotto viene adeguata, viene inviata al cliente un’e-mail con i dettagli dell’ordine e i dettagli dell’ordine riusciti diventano disponibili per la visualizzazione nel **Ordini e restituzioni** con opzioni actionable, ad esempio riordina.
- **Prodotto esaurito o di scarsa fornitura**- lo stato dell&#39;ordine viene modificato in _Rifiutato_, la quantità del prodotto non viene regolata, viene inviata al cliente un’e-mail con i dettagli dell’ordine relativi all’emissione e i dettagli dell’ordine rifiutato diventano disponibili nel **Ordini e restituzioni** senza opzioni utilizzabili.

Utilizza l’interfaccia della riga di comando per abilitare queste funzioni o modifica `app/etc/env.php` in base ai file README corrispondenti definiti nella [_Guida di riferimento del modulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Per abilitare AsyncOrder**:

È possibile abilitare AsyncOrder tramite l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

Il `set` Il comando scrive quanto segue in `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulta [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) nel _Guida di riferimento del modulo_.

**Per disattivare AsyncOrder**:

>[!WARNING]
>
>Prima di disabilitare il modulo AsyncOrder, è necessario verificare che _tutto_ i processi di ordinamento asincrono sono stati completati.

È possibile disattivare AsyncOrder utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

Il `set` Il comando scrive quanto segue in `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilità con AsyncOrder

AsyncOrder supporta un set limitato di funzioni di Adobe Commerce.

| Categoria | Funzionalità supportata |
|------------------|--------------------------------------------------------------------------|
| Tipi di pagamento | Estrazione di OnePage<br>Pagamento standard<br>Offerta B2B negoziabile |
| Metodi di pagamento | Assegno/vaglia postale<br>Consegna in contanti<br>Braintree<br>PayPal PayFlow Pro |
| Metodi di spedizione | Sono supportati tutti i metodi di spedizione. |

Le seguenti funzioni sono **non** supportato da AsyncOrder, ma continua a funzionare in modo sincrono:

- Metodi di pagamento non inclusi nell’elenco delle funzioni supportate
- Checkout multiindirizzo
- Creazione ordine amministratore

#### Supporto API web

Quando il modulo AsyncOrder è abilitato, i seguenti endpoint REST e le mutazioni GraphQL vengono eseguiti in modo asincrono:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL non supporta il posizionamento asincrono degli ordini di preventivo negoziabili.

#### Esclusione dei metodi di pagamento

Gli sviluppatori possono escludere esplicitamente alcuni metodi di pagamento dal posizionamento asincrono dell’ordine aggiungendoli al `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` array. Gli ordini che utilizzano metodi di pagamento esclusi vengono elaborati in modo sincrono.

### Ordine asincrono offerta negoziabile

Il _Ordine asincrono offerta negoziabile_ Il modulo B2B consente di salvare gli articoli dell’ordine in modo asincrono per `NegotiableQuote` funzionalità. AsyncOrder e NegotiableQuote devono essere abilitati.

## Calcolo del totale differito

Il _Calcolo del totale differito_ Il modulo ottimizza il processo di pagamento posticipando il calcolo del totale fino a quando non viene richiesto per il carrello o durante i passaggi di pagamento finali. Quando questa opzione è attivata, solo il subtotale viene calcolato quando un cliente aggiunge prodotti al carrello.

Il calcolo del totale differito è **disabilitato** per impostazione predefinita. Utilizza l’interfaccia della riga di comando per abilitare queste funzioni o modifica `app/etc/env.php` in base ai file README corrispondenti definiti nella [_Guida di riferimento del modulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Per abilitare DeferredTotalCalculation**:

È possibile abilitare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Il `set` Il comando scrive quanto segue in `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Per disattivare DeferredTotalCalculation**:

È possibile disattivare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Il `set` Il comando scrive quanto segue in `app/etc/env.php` file:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulta [CalcoloTotaleDifferito](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) nel _Guida di riferimento del modulo_.

### Imposta Prodotto Fissa

Quando Calcolo totale differito è abilitato, l’imposta fissa sul prodotto (FPT, Fixed Product Tax) non viene inclusa nel prezzo del prodotto e nel subtotale del carrello del mini carrello dopo l’aggiunta del prodotto al carrello. Il calcolo dell’FPT viene differito quando si aggiunge un prodotto al mini carrello. L’FPT viene visualizzato correttamente nel carrello dopo aver proceduto al pagamento finale.

## Disabilita controllo scorte

Il _Abilita magazzino al caricamento del carrello_ impostazione globale determina se eseguire un controllo di inventario durante il caricamento di un prodotto nel carrello. La disattivazione del processo di controllo dell’inventario migliora le prestazioni per tutti i passaggi di pagamento, in particolare quando si tratta di prodotti in blocco nel carrello.

Se è disabilitata, il controllo dell’inventario non viene eseguito quando si aggiunge un prodotto al carrello. Se questo controllo di inventario viene saltato, alcuni scenari esauriti potrebbero generare altri tipi di errori. Un controllo di inventario _sempre_ si verifica al passaggio di posizionamento dell’ordine, anche se disabilitato.

**Abilita controllo magazzino al caricamento del carrello** è attivato (impostato su Sì) per impostazione predefinita. Per disattivare il controllo dell&#39;inventario durante il caricamento del carrello, impostare **[!UICONTROL Enable Inventory Check On Cart Load]** a `No` nell’interfaccia di amministrazione **Negozi** > **Configurazione** > **Catalogo** > **Inventario** > **Opzioni Stock** sezione. Consulta [Configurare le opzioni globali](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) e [Inventario catalogo](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) nel _Guida utente_.

## Bilanciamento del carico

È possibile bilanciare il carico tra nodi diversi abilitando connessioni secondarie per il database MySQL e l&#39;istanza Redis.

Adobe Commerce può leggere più database o istanze Redis in modo asincrono. Se utilizzi Commerce su infrastruttura cloud, puoi configurare le connessioni secondarie modificando il [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) e [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) valori in `.magento.env.yaml` file. Solo un nodo deve gestire il traffico di lettura-scrittura, quindi impostare le variabili su `true` determina la creazione di una connessione secondaria per il traffico di sola lettura. Imposta i valori su `false` per rimuovere qualsiasi array di connessione di sola lettura esistente dal `env.php` file.

Esempio di `.magento.env.yaml` file:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
