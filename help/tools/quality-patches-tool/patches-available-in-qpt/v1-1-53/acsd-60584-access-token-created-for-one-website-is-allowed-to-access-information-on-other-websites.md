---
title: "ACSD-60584: il token di accesso creato per un sito Web può accedere alle informazioni su altri siti Web"
description: Applica la patch ACSD-60584 per risolvere il problema che consente al token di accesso creato per l’utente su un sito web di accedere alle informazioni dei clienti su altri siti web o di modificarle.
feature: Customers, GraphQL
role: Admin, Developer
source-git-commit: eba4a8fd7bbf52fbc4295feab0d5bb79e7383b66
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-60584: il token di accesso creato per un sito Web può accedere alle informazioni su altri siti Web

La patch ACSD-60584 risolve il problema per cui il token di accesso creato per l’utente su un sito web può accedere o modificare le informazioni del cliente su altri siti web. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) 1.1.53. L’ID della patch è ACSD-60584. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il token API creato per l’utente su un sito web consente di accedere alle informazioni sul cliente, creare un carrello e aggiungere prodotti al carrello su altre visualizzazioni del sito web.

<u>Passaggi da riprodurre</u>:

1. Assicurarsi che **[!DNL Share Customer Accounts configuration]** sia impostato su **[!UICONTROL Per Website]**.
1. Crea un altro *sito Web*, *archivio* e *storeview*.
1. Crea due clienti con la stessa e-mail sul *sito Web* principale e sul *sito Web* del passaggio precedente.
1. Genera un token cliente tramite [!DNL GraphQL] sul sito Web principale.
1. Utilizzando il token generato, inviare una query del cliente **[!DNL GraphQL]** con il secondo sito Web nell&#39;intestazione per recuperare le informazioni sul cliente.
1. Osserva il risultato restituito.

<u>Risultati previsti</u>:

Sono state restituite informazioni sul cliente dal *sito Web* principale perché il token del *sito Web* principale è utilizzato nella query [!DNL GraphQL].

<u>Risultati effettivi</u>:

Vengono restituite le informazioni sul cliente provenienti dal secondo sito Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
