---
title: "MDVA-38799: prodotti scaricabili non salvati dopo la creazione di un aggiornamento di staging"
description: La patch MDVA-38799 risolve il problema che impedisce il salvataggio dei prodotti scaricabili dopo la creazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0. L'ID della patch è MDVA-38799. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
feature: Products, Staging
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: prodotti scaricabili non salvati dopo la creazione di un aggiornamento di staging

La patch MDVA-38799 risolve il problema che impedisce il salvataggio dei prodotti scaricabili dopo la creazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.0. L&#39;ID della patch è MDVA-38799. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti scaricabili non vengono salvati dopo la creazione di un aggiornamento di staging. Gli utenti ricevono il messaggio di errore: *L&#39;esempio scaricabile non è correlato al prodotto. Verifica il collegamento e riprova*.

<u>Passaggi da riprodurre</u>:

1. Passa a **Catalogo** > **Prodotti**.
1. Fai clic sul menu a discesa accanto a Aggiungi prodotto e seleziona Prodotto scaricabile.
   * Compila il nome, lo SKU, il prezzo e la quantità del prodotto.
1. Scorri fino alla pagina Informazioni scaricabili.
1. In Esempi fare clic su **Aggiungi collegamento**.
   * Compila il Titolo, Carica file (il tipo di file non conta).
1. Fai clic su **Salva**. Verrà visualizzato il seguente messaggio: *Il prodotto è stato salvato*.
1. Fai clic su **Pianifica nuovo aggiornamento** nella parte superiore della pagina.
   * Compila il Nome aggiornamento e una Data inizio e una Data fine legali.
1. Fai clic su **Salva** nell&#39;aggiornamento dell&#39;area di gestione temporanea.
1. Fai clic su **Salva** sul prodotto.

<u>Risultati previsti</u>:

Il prodotto viene salvato senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di errore: *L&#39;esempio scaricabile non è correlato al prodotto. Verifica il collegamento e riprova*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
