---
title: 'ACSD-64627: impossibile salvare gli attributi cliente personalizzati in [!UICONTROL Company Structure]'
description: Applicare la patch ACSD-64627 per risolvere il problema di Adobe Commerce che impedisce il salvataggio degli attributi personalizzati dei clienti durante l'aggiunta o la modifica di utenti in [!UICONTROL Company Structure].
feature: B2B
role: Admin, Developer
exl-id: 8e7dd72e-c21e-46cf-8e2b-9dccedfd8b04
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '396'
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
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
