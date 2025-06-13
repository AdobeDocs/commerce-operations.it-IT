---
title: 'ACSD-49773: l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota'
description: Applica la patch ACSD-49773 per risolvere il problema di Adobe Commerce in cui l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota.
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
exl-id: 82f1299f-52b6-4f87-b01c-072d1661c022
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-49773: l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota

La patch ACSD-49773 risolve il problema se l’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archivio remoto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-49773. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto non riesce quando AWS S3 viene utilizzato come archiviazione remota.

<u>Passaggi da riprodurre</u>:

1. Installa un profilo dati di grandi dimensioni.
1. Crea un account AWS e configura un bucket S3 e un utente IAM.
1. Aggiorna `app/etc/env.php` con le configurazioni.
1. Esegui `bin/magento setup:upgrade`.
1. Vai al back-end ed esegui un’esportazione completa del prodotto.
1. Monitorare lo stato dei messaggi della coda dalla tabella `[queue_message_status]`.
1. Controllare i registri di sistema.

<u>Risultati previsti</u>:

L’esportazione del prodotto termina senza errori.

<u>Risultati effettivi</u>:

Nei registri di sistema viene registrato un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool]
* [Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
