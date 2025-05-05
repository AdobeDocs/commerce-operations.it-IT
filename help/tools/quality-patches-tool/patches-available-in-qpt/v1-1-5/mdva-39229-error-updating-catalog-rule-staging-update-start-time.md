---
title: "MDVA-39229: errore dopo l'aggiornamento dell'ora di inizio dell'aggiornamento della gestione temporanea della regola del catalogo"
description: La patch di MDVA-39229 risolve il problema relativo all'errore restituito dagli utenti dopo l'aggiornamento dell'ora di inizio dell'aggiornamento della gestione temporanea delle regole del catalogo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. L'ID della patch è MDVA-39229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Catalog Management, Staging
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-39229: errore dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento della gestione temporanea della regola del catalogo

La patch di MDVA-39229 risolve il problema relativo all&#39;errore restituito dagli utenti dopo l&#39;aggiornamento dell&#39;ora di inizio dell&#39;aggiornamento della gestione temporanea delle regole del catalogo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.5. L&#39;ID della patch è MDVA-39229. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore dopo l’aggiornamento dell’ora di inizio dell’aggiornamento della gestione temporanea della regola del catalogo.

<u>Passaggi da riprodurre</u>:

1. Crea una regola di prezzo catalogo.
1. Crea ed esegui qualsiasi aggiornamento di staging.
1. Esegui la query e verifica che il flag Staging sia stato creato.


   `select * from flag;`


1. Crea un nuovo aggiornamento di staging da avviare dopo cinque minuti.
1. Apri **Contenuto** > **Gestione temporanea** > **Dashboard** > **Nuovo aggiornamento** e ritarda di un minuto l&#39;ora di inizio.
1. Aspettate sei minuti.
1. Esegui cron.

<u>Risultati previsti</u>:

L&#39;ora di inizio dell&#39;aggiornamento viene modificata e l&#39;aggiornamento viene applicato. Il vecchio aggiornamento è stato eliminato dalla tabella `staging_update`.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente errore:

*report.ERROR: il processo Cron staging_synchronize_entities_period contiene un errore: impossibile eliminare l&#39;aggiornamento attivo.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).
