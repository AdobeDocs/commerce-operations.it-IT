---
title: 'ACSD-63870: il cliente non si è disconnesso correttamente durante la modifica dello stato della società'
description: Applica la patch ACSD-63870 per risolvere il problema Adobe Commerce, in cui il cliente dell’azienda non viene disconnesso correttamente se cambia lo stato dell’azienda durante una sessione attiva del cliente.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870: il cliente non si è disconnesso correttamente durante la modifica dello stato della società

La patch ACSD-63870 risolve il problema relativo alla disconnessione non corretta di un cliente aziendale quando lo stato dell&#39;azienda cambia durante una sessione attiva del cliente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-63870. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore di disconnessione del cliente quando lo stato della società viene modificato durante una sessione attiva del cliente.

<u>Passaggi da riprodurre</u>:

1. Abilita la funzionalità B2B.
1. Crea un prodotto semplice.
1. Crea una nuova società e contrassegnala come *Attiva*.
1. Accedi come utente aziendale e aggiungi un prodotto al carrello.
1. Procedi con l&#39;estrazione fino al passaggio [!UICONTROL Shipping Address]. Non inserire l&#39;indirizzo.
1. Vai all&#39;amministratore e cambia lo stato dell&#39;azienda in *In attesa di approvazione*.
1. Torna al front-end e compila l’indirizzo di spedizione.

<u>Risultati previsti</u>:

Il cliente è stato disconnesso.

<u>Risultati effettivi</u>:

* Gli utenti ricevono l&#39;errore *Si è verificato un errore*.
* `var/log/exception.log` contiene:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
