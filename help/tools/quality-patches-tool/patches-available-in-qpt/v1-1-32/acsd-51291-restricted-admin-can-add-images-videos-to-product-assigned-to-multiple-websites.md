---
title: "ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web"
description: Applica la patch ACSD-51291 per risolvere il problema di Adobe Commerce, in cui un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.
feature: Admin Workspace, Products, Page Content
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# ACSD-51291: l’amministratore con restrizioni può aggiungere immagini/video a prodotti assegnati a più siti web

La patch ACSD-51291 risolve il problema per cui un amministratore con restrizioni con accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32. L’ID della patch è ACSD-51291. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un amministratore con restrizioni di accesso a un sito web può aggiungere immagini/video a un prodotto assegnato a più siti web.

<u>Passaggi da riprodurre</u>

1. Accedi come amministratore.
1. Crea un secondo sito Web, store e visualizzazione store.
1. Crea un secondo ruolo di amministratore con risorse solo per il secondo sito Web, store e visualizzazione store.
1. Crea un secondo amministratore e assegnalo al nuovo ruolo di amministratore con restrizioni.
1. Crea un nuovo prodotto e assegnalo ai siti Web predefiniti e nuovi.
1. Esci dal profilo di amministrazione principale.
1. Accedi come nuovo amministratore con restrizioni.
1. Modifica il prodotto creato, che è stato assegnato a entrambi i siti web.
1. Apri la scheda **[!UICONTROL Images and Videos]**.

<u>Risultati previsti</u>:

* Viene visualizzato il seguente messaggio:

  *L&#39;amministratore con restrizioni può eseguire azioni con immagini o video solo quando dispone dei diritti per tutti i siti Web a cui è assegnato il prodotto.*

* Il pulsante **[!UICONTROL Add Video]** non è attivo.

<u>Risultati effettivi</u>:

L’amministratore con restrizioni può aggiungere immagini e video anche quando il prodotto viene assegnato a un sito web a cui non ha accesso.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
