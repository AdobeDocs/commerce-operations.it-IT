---
title: 'MDVA-37592: l''ordinamento in base al prezzo non funziona per i prodotti con prezzo zero'
description: La patch di MDVA-37592 Adobe Commerce risolve il problema relativo al funzionamento non corretto dell'ordinamento in base al prezzo per i prodotti con prezzo zero assegnato a un catalogo condiviso. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. L'ID della patch è MDVA-37592. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Categories, Orders, Products
role: Admin
exl-id: 4d4a158c-2020-42a4-9b8b-14c9b48b4107
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%
---
# MDVA-37592: l&#39;ordinamento in base al prezzo non funziona per i prodotti con prezzo zero

La patch di MDVA-37592 Adobe Commerce risolve il problema relativo al funzionamento non corretto dell&#39;ordinamento in base al prezzo per i prodotti con prezzo zero assegnato a un catalogo condiviso. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.0. L&#39;ID della patch è MDVA-37592. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sulla nostra architettura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i tipi di distribuzione) 2.3.6-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;ordinamento in base al prezzo non funziona correttamente per i prodotti con il prezzo zero assegnato a un catalogo condiviso.

<u>Prerequisiti</u>:

B2B è installato.

<u>Passaggi da riprodurre</u>:

1. Abilita catalogo condiviso.
1. Crea quattro prodotti con i seguenti prezzi e assegnali a una categoria: $ 50, $ 60, $ 70 e $ 80.
1. Crea un catalogo condiviso con i prodotti di cui sopra.
1. Imposta il prezzo personalizzato su zero per il prodotto con un prezzo di $ 70.
1. Ora crea un utente aziendale e assegnalo al catalogo condiviso appena creato.
1. Accedi con l&#39;account aziendale e individua la categoria a cui sono assegnati i prodotti.
1. Prova a ordinare per prezzo.

<u>Risultati previsti</u>:

Il prodotto con prezzo zero è ordinato correttamente.

<u>Risultati effettivi</u>:

Il prodotto con prezzo zero NON è ordinato correttamente. Viene invece ordinata in base al prezzo originale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
