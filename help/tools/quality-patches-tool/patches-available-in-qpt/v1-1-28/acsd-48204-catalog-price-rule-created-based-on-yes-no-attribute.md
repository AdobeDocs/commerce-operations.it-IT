---
title: 'ACSD-48204: la regola del prezzo di catalogo creata in base all’attributo *Sì/No* non considera l’ambito selezionato'
description: Applica la patch ACSD-48204 per risolvere il problema Adobe Commerce per cui la regola del prezzo di catalogo creata in base all’attributo *Sì/No* non considera l’ambito selezionato.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
exl-id: 69f2b35c-856e-4f96-ae2f-fb0c64d5eb94
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 2%
---
# ACSD-48204: la regola del prezzo del catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato

La patch ACSD-48204 risolve il problema per cui la regola del prezzo di catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-48204. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola del prezzo di catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web (predefinito e W2).
1. Creare un attributo di prodotto di tipo *Sì/No*.
   * Imposta [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crea un prodotto configurabile in base a qualsiasi attributo con due varianti (V1 e V2).
   * Aggiungi l&#39;attributo *Sì/No* al set di attributi delle varianti configurabili
   * Per una delle varianti (V1), imposta il valore su *[!UICONTROL Yes]* nel sito Web non predefinito (W2)
1. Creare una regola di catalogo:
   * Applicato a entrambi i siti Web
   * Condizione: *Il valore dell&#39;attributo* è *[!UICONTROL Yes]*
   * Sconto = 50%
1. Apri il prodotto configurabile sul sito Web non predefinito (W2).
1. Verifica che alla variante V1 sia applicato lo sconto del 50%.
1. Apri la variante V1 in Adobe Commerce Admin.
   * Passa al sito Web predefinito
   * Non apportare modifiche e salvare il prodotto
1. Aggiorna la pagina della vetrina del prodotto configurabile.

<u>Risultati previsti</u>:

Alla variante V1 viene ancora applicato lo sconto del 50% in quanto non sono state apportate modifiche.

<u>Risultati effettivi</u>:

Lo sconto scompare.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
