---
title: 'ACSD-62952: la data del registro degli omaggi non viene visualizzata correttamente sul vetrina'
description: Applica la patch ACSD-62952 per risolvere il problema di Adobe Commerce, in cui la data del registro dei regali viene visualizzata in modo impreciso sulla vetrina.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952: la data del registro degli omaggi non viene visualizzata correttamente sul vetrina

La patch ACSD-62952 risolve il problema relativo alla visualizzazione non corretta della data del registro dei regali nella vetrina. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62952. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La data evento visualizzata nella vetrina di un registro degli omaggi condivisi non viene visualizzata correttamente se è anteriore di un giorno alla data effettiva.

<u>Passaggi da riprodurre</u>:

1. Accedi al front-end come cliente.
1. Nel dashboard [!UICONTROL My Account], fare clic su **[!UICONTROL Gift Registry]**.
1. Se non esiste alcun registro, crearne uno e specificare una data.
1. Aggiungi qualsiasi elemento al carrello.
1. Dalla pagina del carrello, fai clic su **[!UICONTROL Add all items to Gift Registry]**.
1. Condividi il registro dei regali.

<u>Risultati previsti</u>:

Nel registro dei regali viene visualizzata la data dell&#39;evento corretta.

<u>Risultati effettivi</u>:

Il Registro regali aperto dall’e-mail di invito mostra la data dell’evento come un giorno prima.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
