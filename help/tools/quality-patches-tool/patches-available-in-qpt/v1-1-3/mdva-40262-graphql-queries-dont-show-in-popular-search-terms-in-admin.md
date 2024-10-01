---
title: "MDVA-40262: le query GraphQL non vengono visualizzate in termini di ricerca comuni in admin"
description: La patch di qualità di MDVA-40262 Adobe Commerce risolve il problema per cui le query di ricerca di GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3. L'ID della patch è MDVA-40262. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Admin Workspace, GraphQL, Search
role: Admin
source-git-commit: c1055ed10813aa6e585f93ec3091d216af06affd
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-40262: le query GraphQL non vengono visualizzate in termini di ricerca comuni in admin

La patch di qualità di MDVA-40262 Adobe Commerce risolve il problema per cui le query di ricerca di GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.3. L&#39;ID della patch è MDVA-40262. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le query GraphQL non vengono visualizzate nei termini di ricerca più comuni nell’amministratore.

<u>Prerequisiti</u>:

È necessario installare i dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > **Configurazione** > **Catalogo** > **SEO** > **Termini di ricerca popolari** e imposta per l&#39;attivazione.
1. Esegui la seguente query GraphQL:

<pre>
<code class="language-graphql">
{
  products(
    search: "jackets"
    filter: { price: { to: "50" } }
    pageSize: 20
   ) {
    total_count
    items {
      name
      sku
    }
    page_info {
      page_size
      current_page
    }
  }
}
</code>
</pre>

<u>Risultati previsti</u>:

Dopo aver eseguito la query di GraphQL per cercare un prodotto, è necessario aggiungerla ai termini di ricerca più comuni.

<u>Risultati effettivi</u>:

La query di ricerca non viene aggiunta ai termini di ricerca più comuni.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
