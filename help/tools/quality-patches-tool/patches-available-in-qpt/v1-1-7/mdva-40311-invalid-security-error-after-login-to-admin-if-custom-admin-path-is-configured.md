---
title: 'MDVA-40311: errore "Sicurezza o chiave del modulo non valida" dopo l''accesso ad Admin se è configurato un percorso di amministrazione personalizzato'
description: 'La patch di MDVA-40311 risolve il problema che causa all''utente amministratore un messaggio di errore: *Protezione o chiave del modulo non valida. Aggiorna la pagina* dopo aver effettuato l’accesso all’amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. L''ID della patch è MDVA-40311. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.'
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311: errore &quot;Sicurezza o chiave del modulo non valida&quot; dopo l&#39;accesso ad Admin se è configurato un percorso di amministrazione personalizzato

La patch di MDVA-40311 risolve il problema relativo al messaggio di errore ricevuto dall&#39;utente amministratore: *Protezione o chiave del modulo non valida. Aggiornare la pagina* dopo aver effettuato l&#39;accesso all&#39;amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. L&#39;ID della patch è MDVA-40311. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente amministratore riceve un messaggio di errore: *Sicurezza o chiave modulo non valida. Aggiornare la pagina* dopo aver effettuato l&#39;accesso all&#39;amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata.

<u>Passaggi da riprodurre</u>:

* Accedi come utente amministratore utilizzando un nome utente e una password validi.

<u>Risultati previsti</u>:

L’utente è in grado di accedere senza alcun messaggio di errore.

<u>Risultati effettivi</u>:

*Chiave modulo o protezione non valida. Aggiorna il messaggio di errore della pagina*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
