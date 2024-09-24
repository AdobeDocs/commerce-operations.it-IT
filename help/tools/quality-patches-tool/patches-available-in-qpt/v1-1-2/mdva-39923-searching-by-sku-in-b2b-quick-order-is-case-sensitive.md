---
title: "MDVA-39923: la funzionalità di ricerca per SKU nella gestione degli ordini rapidi B2B distingue tra maiuscole e minuscole"
description: La patch MDVA-39923 risolve il problema relativo all'errore che si verifica quando i clienti cercano l'ordine in base allo SKU nella funzionalità di ordinamento rapido B2B utilizzando un caso diverso da quello con cui viene salvato il nome. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-39923. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923: la funzionalità di ricerca per SKU nella gestione degli ordini rapidi B2B distingue tra maiuscole e minuscole

La patch MDVA-39923 risolve il problema relativo all&#39;errore che si verifica quando i clienti cercano l&#39;ordine in base allo SKU nella funzionalità di ordinamento rapido B2B utilizzando un caso diverso da quello con cui viene salvato il nome. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-39923. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La ricerca per SKU nella funzionalità di ordinamento rapido B2B distingue tra maiuscole e minuscole e mostra un errore quando si utilizza una maiuscola diversa da quella con cui viene salvato lo SKU.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore e vai a **Archivi** > **Configurazione** > **B2B**.
1. Abilita **Catalogo condiviso** e **Ordine rapido**.
1. Crea un prodotto con SKU maiuscola, ad esempio TEST20-1234
1. Assegna il prodotto creato al **catalogo condiviso**.
1. Accedi come cliente e fai clic su **Ordine rapido**.
1. Immetti lo SKU in minuscolo, ad esempio test20-1234.

<u>Risultati previsti</u>:

Il prodotto deve essere disponibile indipendentemente dal caso utilizzato.

<u>Risultati effettivi</u>:

Ricevuto il seguente messaggio di errore: *1 prodotto/i richiede/richiedono attenzione*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
