---
title: "ACSD-46815: la distribuzione di contenuti statici non riesce con una strategia compatta"
description: Applica la patch ACSD-46815 per risolvere il problema Adobe Commerce in cui la distribuzione di contenuto statico non riesce quando si utilizza una strategia compatta.
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-46815: l’implementazione di contenuti statici non riesce quando si utilizza una strategia compatta

La patch ACSD-46815 risolve il problema relativo all&#39;errore di distribuzione del contenuto statico quando si utilizza la strategia compatta. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20. L’ID della patch è ACSD-46815. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’implementazione di contenuti statici non riesce se si utilizza una strategia compatta.

<u>Passaggi da riprodurre</u>:

1. Distribuisci il contenuto statico con una strategia compatta eseguendo il seguente comando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Risultati previsti</u>:

La distribuzione del contenuto statico è stata completata senza errori.

<u>Risultati effettivi</u>:

L’implementazione di contenuti statici non riesce con una strategia compatta. Durante il processo di distribuzione si verifica l&#39;errore seguente: *Il contenuto di /app/pub/static/adminhtml/Magento/base/default/.Impossibile leggere il file /node_modules/@spectrum-css/vars/dist/spectrum-global.css.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
