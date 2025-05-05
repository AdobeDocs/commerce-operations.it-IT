---
title: '"ACSD-61366: il comando "bin/magento setup:static-content:deploy —jobs 4" riscontra più errori di processo con un errore"'
description: Applica la patch ACSD-61366 per risolvere il problema di Adobe Commerce in cui il comando "bin/magento setup:static-content:deploy —jobs 4" riscontra più errori di processo con l’errore *Port must be configured within the host parameter*, nonostante sia stata specificata la porta per la connessione DB.
feature: SCD
role: Admin, Developer
source-git-commit: b671dc30cd511d63dbbbaa6edd47ee36c1351620
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61366: il comando `bin/magento setup:static-content:deploy --jobs 4` rileva più errori di processo con un errore

La patch ACSD-61366 risolve il problema in cui il comando `bin/magento setup:static-content:deploy --jobs 4` rileva più errori di processo con *La porta deve essere configurata nell&#39;errore del parametro host*, nonostante la specifica della porta per la connessione DB. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52. L’ID della patch è ACSD-61366. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il comando `bin/magento setup:static-content:deploy --jobs 4` rileva più errori di processo con *La porta deve essere configurata all&#39;interno dell&#39;errore del parametro host*, nonostante sia stata specificata la porta per la connessione DB.

<u>Passaggi da riprodurre</u>:

1. Specificare una porta nella connessione al database in `app/etc/env.php`.
1. Esegui il comando `bin/magento setup:static-content:deploy --jobs 4`.

<u>Risultati previsti</u>:

La distribuzione del contenuto statico viene completata correttamente.

<u>Risultati effettivi</u>:

Il comando ha esito negativo con l&#39;errore *Porta deve essere configurato all&#39;interno del parametro host*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].