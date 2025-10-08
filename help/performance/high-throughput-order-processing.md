---
title: Best practice per le prestazioni del checkout
description: Scopri le best practice sulle prestazioni di pagamento in Adobe Commerce. Scopri le linee guida per l’implementazione e le strategie di ottimizzazione.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 0%

---


# Best practice per le prestazioni del checkout

Il processo di [estrazione](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) in Adobe Commerce è un aspetto critico dell&#39;esperienza di vetrina. Si basa sulle funzionalità integrate [cart](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) e [checkout](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page).

Le prestazioni sono fondamentali per mantenere una buona esperienza utente. Puoi ottimizzare le prestazioni di estrazione configurando le seguenti opzioni per l&#39;**elaborazione di ordini ad alta velocità**:

- [AsyncOrder](#asynchronous-order-placement)—Elabora gli ordini in modo asincrono utilizzando una coda.
- [Calcolo totale differito](#deferred-total-calculation)—Differisci i calcoli per i totali dell&#39;ordine fino all&#39;inizio dell&#39;estrazione.
- [Controllo scorte al caricamento del carrello](#disable-inventory-check)—Scegliere di ignorare la convalida dell&#39;inventario degli articoli del carrello.
- [Bilanciamento del carico](#load-balancing): abilita le connessioni secondarie per il database MySQL e l&#39;istanza Redis.

Le opzioni di configurazione AsyncOrder, Deferred Total Calculation e Inventory Check on Cart Load funzionano tutte in modo indipendente. Potete utilizzare tutte e tre le feature contemporaneamente oppure attivarle e disattivarle in qualsiasi combinazione.

>[!NOTE]
>
>Non utilizzare codice PHP personalizzato per personalizzare le funzionalità integrate del carrello e del pagamento. Oltre a potenziali problemi di prestazioni, l&#39;utilizzo di un codice PHP personalizzato può causare complessi problemi di aggiornamento e manutenzione. Questi problemi aumentano il costo totale di proprietà. Se la personalizzazione del carrello e del pagamento basata su PHP è inevitabile, utilizza solo le estensioni approvate da [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/). Tutte le estensioni del marketplace sono soggette a [revisione approfondita](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) per verificare che soddisfino gli standard di codifica e le best practice di Adobe Commerce.

## Posizionamento dell’ordine asincrono

Il modulo _Ordine asincrono_ consente il posizionamento dell&#39;ordine asincrono, che contrassegna l&#39;ordine come `received`, inserisce l&#39;ordine in una coda ed elabora gli ordini dalla coda in base al primo ordine in uscita. AsyncOrder è **disabilitato** per impostazione predefinita.

Ad esempio, un cliente aggiunge un prodotto al carrello e seleziona **[!UICONTROL Proceed to Checkout]**. Compila il modulo **[!UICONTROL Shipping Address]**, seleziona il **[!UICONTROL Shipping Method]** preferito, seleziona un metodo di pagamento e invia l&#39;ordine. Il carrello è stato cancellato, l&#39;ordine è contrassegnato come **[!UICONTROL Received]**, ma la quantità di prodotto non è ancora stata regolata e non viene inviata un&#39;e-mail di vendita al cliente. L&#39;ordine viene ricevuto, ma i dettagli dell&#39;ordine non sono ancora disponibili perché l&#39;ordine non è stato completamente elaborato. Rimane in coda finché il consumatore `placeOrderProcess` non inizia, verifica l&#39;ordine con la funzionalità [inventory check](#disable-inventory-check) (attivata per impostazione predefinita) e aggiorna l&#39;ordine come segue:

- **Prodotto disponibile**: lo stato dell&#39;ordine diventa _In sospeso_, la quantità del prodotto viene adeguata, al cliente viene inviata un&#39;e-mail con i dettagli dell&#39;ordine e i dettagli dell&#39;ordine riusciti diventano disponibili per la visualizzazione nell&#39;elenco **Ordini e restituzioni** con opzioni actionable, ad esempio il riordino.
- **Prodotto esaurito o fornitura insufficiente**. Lo stato dell&#39;ordine diventa _Rifiutato_, la quantità del prodotto non viene adeguata, viene inviata al cliente un&#39;e-mail con i dettagli dell&#39;ordine relativi al problema e i dettagli dell&#39;ordine rifiutato diventano disponibili nell&#39;elenco **Ordini e restituzioni** senza opzioni utilizzabili.

Utilizzare l&#39;interfaccia della riga di comando per abilitare queste funzionalità o modificare il file `app/etc/env.php` in base ai file README corrispondenti definiti nella [_Guida di riferimento al modulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Per abilitare AsyncOrder**:

È possibile abilitare AsyncOrder tramite l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 1
```

Il comando `set` scrive quanto segue nel file `app/etc/env.php`:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Vedi [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) nella _Guida di riferimento al modulo_.

**Per disabilitare AsyncOrder**:

>[!WARNING]
>
>Prima di disabilitare il modulo AsyncOrder, è necessario verificare che _tutti_ i processi dell&#39;ordine asincrono siano stati completati.

È possibile disattivare AsyncOrder utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --checkout-async 0
```

Il comando `set` scrive quanto segue nel file `app/etc/env.php`:

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
| Tipi di pagamento | Estrazione di OnePage<br>Estrazione standard<br>Offerta negoziabile B2B |
| Metodi di pagamento | Assegno o vaglia postale<br>Contanti alla consegna<br>Braintree<br>PayPal PayFlow Pro |
| Metodi di spedizione | Sono supportati tutti i metodi di spedizione. |

Le seguenti funzionalità sono **non** supportate da AsyncOrder, ma continuano a funzionare in modo sincrono:

- Metodi di pagamento non inclusi nell’elenco delle funzioni supportate
- Checkout multiindirizzo
- Creazione ordine amministratore

#### Supporto API web

Quando il modulo AsyncOrder è abilitato, i seguenti endpoint REST e le mutazioni GraphQL vengono eseguiti in modo asincrono:

**RESTO:**

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

Gli sviluppatori possono escludere esplicitamente alcuni metodi di pagamento dal posizionamento asincrono dell&#39;ordine aggiungendoli all&#39;array `Magento\AsyncOrder\Model\OrderManagement::paymentMethods`. Gli ordini che utilizzano metodi di pagamento esclusi vengono elaborati in modo sincrono.

### Ordine asincrono offerta negoziabile

Il modulo B2B _Negotiable Quote Async Order_ consente di salvare gli elementi dell&#39;ordine in modo asincrono per la funzionalità `NegotiableQuote`. AsyncOrder e NegotiableQuote devono essere abilitati.

## Calcolo del totale differito

Il modulo _Calcolo totale differito_ ottimizza il processo di pagamento posticipando il calcolo del totale fino a quando non viene richiesto per il carrello o durante i passaggi di pagamento finali. Quando questa opzione è attivata, solo il subtotale viene calcolato quando un cliente aggiunge prodotti al carrello.

Il calcolo del totale differito è **disabilitato** per impostazione predefinita. Utilizzare l&#39;interfaccia della riga di comando per abilitare queste funzionalità o modificare il file `app/etc/env.php` in base ai file README corrispondenti definiti nella [_Guida di riferimento al modulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Per abilitare DeferredTotalCalculation**:

È possibile abilitare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

Il comando `set` scrive quanto segue nel file `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Per disabilitare DeferredTotalCalculation**:

È possibile disattivare DeferredTotalCalculation utilizzando l&#39;interfaccia della riga di comando:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

Il comando `set` scrive quanto segue nel file `app/etc/env.php`:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Vedi [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) nella _Guida di riferimento del modulo_.

### Imposta Prodotto Fissa

Quando Calcolo totale differito è abilitato, l’imposta fissa sul prodotto (FPT, Fixed Product Tax) non viene inclusa nel prezzo del prodotto e nel subtotale del carrello del mini carrello dopo l’aggiunta del prodotto al carrello. Il calcolo dell’FPT viene differito quando si aggiunge un prodotto al mini carrello. L’FPT viene visualizzato correttamente nel carrello dopo aver proceduto al pagamento finale.

## Disabilita controllo scorte

L&#39;impostazione globale _Abilita inventario al caricamento del carrello_ determina se eseguire un controllo dell&#39;inventario durante il caricamento di un prodotto nel carrello. La disattivazione del processo di controllo dell’inventario migliora le prestazioni per tutti i passaggi di pagamento, in particolare quando si tratta di prodotti in blocco nel carrello.

Se è disabilitata, il controllo dell’inventario non viene eseguito quando si aggiunge un prodotto al carrello. Se questo controllo di inventario viene saltato, alcuni scenari esauriti potrebbero generare altri tipi di errori. Un controllo di inventario _always_ si verifica al passaggio di posizionamento dell&#39;ordine, anche se disabilitato.

**Abilita controllo inventario al caricamento del carrello** è abilitato (impostato su Sì) per impostazione predefinita. Per disabilitare il controllo dell&#39;inventario durante il caricamento del carrello, impostare **[!UICONTROL Enable Inventory Check On Cart Load]** su `No` nella sezione **Archivi** > **Configurazione** > **Catalogo** > **Inventario** > **Opzioni Stock**. Consulta [Configurare le opzioni globali](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) e [Inventario catalogo](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) nella _Guida utente_.

## Bilanciamento del carico

È possibile bilanciare il carico tra nodi diversi abilitando connessioni secondarie per il database MySQL e l&#39;istanza Redis.

Adobe Commerce può leggere più database o istanze Redis in modo asincrono. Se si utilizza Commerce nell&#39;infrastruttura cloud, è possibile configurare le connessioni secondarie modificando i valori [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) e [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) nel file `.magento.env.yaml`. Poiché solo un nodo deve gestire il traffico di lettura/scrittura, l&#39;impostazione delle variabili su `true` determina la creazione di una connessione secondaria per il traffico di sola lettura. Impostare i valori su `false` per rimuovere qualsiasi array di connessione di sola lettura esistente dal file `env.php`.

Esempio del file `.magento.env.yaml`:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
