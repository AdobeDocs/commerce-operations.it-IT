---
title: 'MDVA-43983: i prodotti impostati come "Not Visible Individually" (Non visibile singolarmente) vengono visualizzati nei risultati della ricerca'
description: La patch di MDVA-43983 risolve il problema relativo alla visualizzazione dei prodotti impostati come "Non visibili singolarmente" nei risultati della ricerca avanzata del catalogo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L'ID della patch è MDVA-43983. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%
---
# MDVA-43983: i prodotti impostati come &quot;Not Visible Individually&quot; (Non visibile singolarmente) vengono visualizzati nei risultati della ricerca

La patch di MDVA-43983 risolve il problema relativo alla visualizzazione dei prodotti impostati come &quot;Non visibili singolarmente&quot; nei risultati della ricerca avanzata del catalogo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.14. L&#39;ID della patch è MDVA-43983. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti impostati come &quot;Non visibile singolarmente&quot; vengono comunque visualizzati nei risultati della ricerca avanzata del catalogo.

<u>Passaggi da riprodurre</u>:

1. Crea un attributo con **Tipo di input catalogo per il proprietario dello store** come **A discesa** o **Campione visivo** (ad esempio, Colore).
1. Impostare **Utilizzo nella ricerca** come **Sì** e **Visibile nella ricerca avanzata** come **Sì**.
1. Aggiungi alcune opzioni di attributo.
1. Crea prodotti con **Visibilità** come **Non visibile singolarmente**.
1. Assegna opzioni attributo colore.
1. Vai alla pagina **Ricerca avanzata nel catalogo** nella vetrina.
1. Selezionare solo l&#39;opzione Attributo colore dal campo Attributo colore e lasciare vuoti i campi rimanenti o invariati.
1. Inviare un modulo di ricerca avanzata.
1. Osserva i risultati della ricerca.

<u>Risultati previsti</u>:

I prodotti impostati come &quot;Non visibile singolarmente&quot; non vengono visualizzati nei risultati della ricerca avanzata del catalogo.

<u>Risultati effettivi</u>:

I prodotti impostati come &quot;Non visibile singolarmente&quot; vengono visualizzati nei risultati della ricerca avanzata del catalogo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
