---
title: 'MDVA-43731: i sinonimi di ricerca non funzionano quando il valore viene aggiunto in "Termini minimi da abbinare"'
description: La patch MDVA-43731 risolve il problema che causa il funzionamento dei sinonimi di ricerca quando viene aggiunto un valore in "Minimum Terms to Match" (Termini minimi da abbinare). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-43731. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: i sinonimi di ricerca non funzionano quando il valore viene aggiunto in &quot;Termini minimi da abbinare&quot;

La patch MDVA-43731 risolve il problema che causa il funzionamento dei sinonimi di ricerca quando viene aggiunto un valore in &quot;Minimum Terms to Match&quot; (Termini minimi da abbinare). Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-43731. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I sinonimi di ricerca smettono di funzionare quando viene aggiunto un valore in &quot;Termini minimi da abbinare&quot;.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con dati di esempio.
1. Configura Elasticsearch7 come motore di ricerca.
1. Cercare la parola &quot;Giacca&quot;. Viene visualizzato un elenco di prodotti.
1. Aggiungi il parametro [4&lt;60%] in **Configurazione** > **Catalogo** > **Ricerca nel catalogo** > **Termini minimi da abbinare**.
1. Cancella la cache di configurazione ed esegui una reindicizzazione.
1. Cercare nuovamente la parola &quot;Giacca&quot; e notare che viene visualizzato un elenco di prodotti.
1. Vai a **Marketing** > **SEO &amp; Search** > **Cerca sinonimi**.
1. Crea i sinonimi di ricerca aggiungendo i seguenti sinonimi: jacket, bagtecs, express plus.
1. Reindicizzare.
1. Eseguire una ricerca di prodotti utilizzando uno dei sinonimi. Ad esempio, giacca.

<u>Risultati previsti</u>:

Nei risultati della ricerca viene visualizzato lo stesso elenco di prodotti di prima.

<u>Risultati effettivi</u>:

Nei risultati della ricerca non viene visualizzato alcun prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
