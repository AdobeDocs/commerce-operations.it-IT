---
title: 'ACSD-64627: impossibile salvare gli attributi cliente personalizzati in [!UICONTROL Company Structure]'
description: Applicare la patch ACSD-64627 per risolvere il problema di Adobe Commerce che impedisce il salvataggio degli attributi personalizzati dei clienti durante l'aggiunta o la modifica di utenti in [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-64627: impossibile salvare gli attributi cliente personalizzati in [!UICONTROL Company Structure]

La patch ACSD-64627 risolve il problema che impediva il salvataggio degli attributi personalizzati del cliente quando si aggiungono o si modificano utenti nella pagina **[!UICONTROL Company Structure]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. L’ID della patch è ACSD-64627. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3, 2.4.7-p4, 2.4.8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p8, 2.4.7-p3, 2.4.7-p4, 2.4.8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli attributi cliente personalizzati non vengono salvati quando si aggiungono o si modificano utenti nella pagina **[!UICONTROL Company Structure]**.

<u>Passaggi da riprodurre</u>:

1. Installa un’istanza di Adobe Commerce con le funzioni B2B abilitate.
1. Crea un nuovo attributo cliente denominato *custom_upload* con **[!UICONTROL Input Type]** impostato su *[!UICONTROL File (attachment)]*.
1. Crea un altro attributo cliente denominato *image_attachment* con **[!UICONTROL Input Type]** impostato su *[!UICONTROL Image File]*.
1. Impostare **[!UICONTROL Show on Storefront]** su *Sì* per rendere entrambi gli attributi visibili nella vetrina. Seleziona tutti i moduli:
   * Registrazione cliente
   * Modifica account cliente
   * Pagamento amministratore
1. Crea e attiva una nuova società.
1. Accedi alla vetrina come amministratore della società.
1. Passa a **[!UICONTROL Customer Account]** > **[!UICONTROL Company Structure]** o **[!UICONTROL Customer Account]** > **[!UICONTROL Company Users]**.
1. Fare clic su **[!UICONTROL Add New User]**.
1. Fare clic su **[!UICONTROL Upload]** per l&#39;attributo *custom_upload*.
1. Fare clic su **[!UICONTROL Select file]** per l&#39;attributo *image_attachment*.

<u>Risultati previsti</u>:

Esplora file si apre per entrambi gli attributi. Al momento del salvataggio, i valori vengono memorizzati e i file caricati correttamente.

<u>Risultati effettivi</u>:

I pulsanti non rispondono. Non viene aperto l&#39;elenco delle cartelle dei file né vengono salvati dati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
