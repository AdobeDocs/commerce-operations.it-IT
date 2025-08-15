---
title: 'MDVA-43232: l’ordinamento dei prodotti nel merchandiser visivo in base al prezzo speciale in alto (o in basso) causa un errore'
description: La patch di MDVA-43232 risolve il problema relativo all'ordinamento dei prodotti in visual merchandiser in base al prezzo speciale in alto (o in basso), causando un errore durante il salvataggio della categoria. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-43232. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# MDVA-43232: l’ordinamento dei prodotti nel merchandiser visivo in base al prezzo speciale in alto (o in basso) causa un errore

La patch di MDVA-43232 risolve il problema relativo all&#39;ordinamento dei prodotti in visual merchandiser in base al prezzo speciale in alto (o in basso), causando un errore durante il salvataggio della categoria. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-43232. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’ordinamento dei prodotti nel merchandiser visivo in base al prezzo speciale in alto (o in basso) causa un errore durante il salvataggio della categoria.

<u>Passaggi da riprodurre</u>:

1. Assicurati che siano presenti due siti web.
1. Passa a **Archivi** > **Configurazione** > **Catalogo** > **Prezzo** e imposta Limite prezzo catalogo = Sito Web.
1. Di nuovo, passa a **Archivi** > **Configurazione** > **Catalogo** > **Visual Merchandiser** > **Attributi visibili per le regole delle categorie** > e aggiungi un prezzo speciale.
1. Crea un prodotto semplice e assegna i prodotti a entrambi i siti web.
1. Aggiungere un prezzo speciale all&#39;ambito predefinito del prodotto.
1. Passa all&#39;ambito dell&#39;altro negozio e sovrascrivi sia il prezzo che il prezzo speciale di quel prodotto.
1. Reindicizzare `catalog_product_price`.
1. Vai a **Catalogo** > **Categorie** e crea una nuova categoria.
1. Aggiungi una regola di categoria per filtrare i prodotti con un prezzo speciale.
1. Salva la categoria.
1. Nella sezione Prodotti in categoria impostare Ordinamento = Prezzo speciale su Superiore (o Inferiore).
1. Salva di nuovo la categoria.

<u>Risultati previsti</u>:

La categoria viene salvata senza errori.

<u>Risultati effettivi</u>:

Viene generata un&#39;eccezione:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
