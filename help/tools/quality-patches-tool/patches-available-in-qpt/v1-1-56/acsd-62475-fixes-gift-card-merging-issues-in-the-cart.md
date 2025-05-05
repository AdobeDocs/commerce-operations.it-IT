---
title: 'ACSD-62475: risolve i problemi di unione delle gift card nel carrello'
description: Applica la patch ACSD-62475 per risolvere il problema di Adobe Commerce, in cui i prodotti gift card con dettagli diversi vengono uniti in modo errato in un’unica riga nel carrello.
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 7c35c245d6a464f7758053bd8aa1854c8fe8a5f2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: risolve i problemi di unione delle gift card nel carrello

La patch ACSD-62475 risolve il problema in cui i prodotti gift card con dettagli diversi vengono erroneamente uniti in un&#39;unica riga nel carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62475. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti gift card aggiunti al carrello con dettagli univoci del mittente o del destinatario non vengono uniti correttamente in un’unica riga, con conseguenti incongruenze nei dati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto [!UICONTROL Gift Card] con le impostazioni seguenti:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. Nella vetrina, crea un nuovo utente e accedi.

1. Aggiungi il prodotto Gift Card al carrello con i seguenti dettagli:
   * **[!UICONTROL Sender Name]**: Mittente 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: Destinatario 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Disconnetti

1. Aggiungi lo stesso prodotto Gift Card al carrello con i seguenti dettagli:
   * **[!UICONTROL Sender Name]**: Mittente 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: destinatario 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Accedi di nuovo e controlla il carrello.

<u>Risultati previsti</u>:

Entrambe le gift card devono essere visualizzate come due voci separate con i rispettivi dettagli.

<u>Risultati effettivi</u>:

Le gift card vengono unite in un&#39;unica riga con una quantità di 2, conservando i dettagli della prima gift card.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
