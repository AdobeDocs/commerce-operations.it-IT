---
source-git-commit: 233ff6d5de2f4da3d477e70d066dd5cd46c771ee
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---
# Note sulla versione di Magento Open Source (v2.4.9-alpha3)

## Elementi di rilievo in v2.4.9-alpha3

Le seguenti caratteristiche si applicano alla versione Magento Open Source 2.4.9-alpha3.

### Braintree

#### Vaulting di Google Pay tramite l&#39;area del conto

In Magento 2.4.9-alpha3, i clienti possono ora effettuare il vaulting delle proprie Google Pay card tramite l’area del conto quando Google Pay Vault è abilitato in Braintree. Le carte vendute appaiono in metodi di pagamento memorizzati, possono essere utilizzate per acquisti futuri al momento del pagamento e possono essere eliminate dal cliente. Questo estende il supporto del vaulting oltre le schede e da PayPal a Google Pay.

_BUNDLE-3459_

#### Collega ordine Magento a ordine Braintree Portal

In Magento 2.4.9-alpha3, un collegamento al portale Braintree viene ora aggiunto ai dettagli dell’ordine in Magento Admin. Facendo clic sul collegamento, la transazione correlata viene aperta nel portale Braintree (in una nuova scheda), utilizzando l&#39;ID commerciante e l&#39;ID transazione dell&#39;ordine Magento. Questo consente di effettuare riferimenti incrociati diretti senza effettuare l’accesso a entrambi i sistemi separatamente.

_BUNDLE-3461_

#### RTAU (Real Time Account Updater)

La funzione Real Time Account Updater (RTAU) in Magento 2.4.9-alpha3 per Braintree garantisce che i dettagli di Visa, Mastercard e Discover archiviati vengano aggiornati automaticamente quando le schede scadono o vengono sostituite. In questo modo si riducono al minimo i pagamenti non riusciti, si mantiene aggiornato Magento Vault e si ignorano i tipi non supportati (prepagati, Apple Pay, Google Pay) senza errori.

_BUNDLE-3462_

#### Supporto di tipo carta ELO per i pagamenti con carta Braintree

In Magento 2.4.9-alpha3, il supporto per il tipo di carta ELO è stato aggiunto a Braintree Payments. Gli amministratori possono ora abilitare ELO nella configurazione della carta di credito e i clienti possono effettuare con successo gli ordini utilizzando le carte ELO al momento del pagamento, garantendo transazioni senza soluzione di continuità tramite Braintree.

_BUNDLE-3464_

### Framework

#### Migrazione da RabbitMQ ad Apache ActiveMQ

_AC-14558_

#### Aggiorna la dipendenza chart.js alla versione più recente

La dipendenza chart.js viene aggiornata alla versione più recente 4.5.0

_AC-15133 - [Contributo codice GitHub](https://github.com/magento/magento2/commit/657f983e)_

#### Migrazione da Laminas MVC

Adobe Commerce ha introdotto un&#39;implementazione MVC nativa, sostituendo la precedente versione di Laminas MVC, per garantire compatibilità e stabilità a lungo termine oltre PHP 8.5. Questa modifica migliora le prestazioni, riduce le dipendenze esterne e fornisce una base più pronta per il futuro per Commerce

_AC-15160_
