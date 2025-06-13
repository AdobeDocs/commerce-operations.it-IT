---
title: 'MDVA-39713: l''utente può modificare l''ora di inizio dell''aggiornamento pianificato attivo'
description: La patch MDVA-39713 risolve il problema che consente all'utente di modificare l'ora di inizio di un aggiornamento pianificato attivo. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-39713. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: CMS
role: Admin
exl-id: 450a968f-a5ed-478f-a857-579fea1eb3b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# MDVA-39713: l&#39;utente può modificare l&#39;ora di inizio dell&#39;aggiornamento pianificato attivo

La patch MDVA-39713 risolve il problema che consente all&#39;utente di modificare l&#39;ora di inizio di un aggiornamento pianificato attivo. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-39713. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.3.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente può modificare l’ora di inizio di un aggiornamento pianificato attivo.

<u>Passaggi da riprodurre</u>:

1. Creare nuove pagine CMS.
1. Seleziona **Pianifica nuovo aggiornamento** e imposta la **Data inizio** su +1 minuto corrente.
1. Attivare Aggiornamento pianificato eseguendo il comando `bin/magento cron:run --group=staging` nell&#39;ambiente locale. Attendi alcuni minuti e controlla se la pianificazione è attiva.
1. Quando la pianificazione è attiva, aggiorna la pagina.
1. Fare clic su **Visualizza/Modifica** nella sezione Modifiche pianificate.
1. Modifica l’ora aggiungendo +2 minuti e salva la modifica.
1. Salva la pagina CMS.
1. Eseguire nuovamente il comando seguente: `bin/magento cron:run --group=staging`.
1. Fai clic su **Visualizza/Modifica** dell&#39;aggiornamento pianificato.

<u>Risultati previsti</u>:

L’utente non è in grado di modificare l’ora di inizio di un aggiornamento pianificato attivo.

<u>Risultati effettivi</u>:

L&#39;utente riceve un errore simile a *Elemento (Magento\Cms\Model\Page) con lo stesso ID &quot;11&quot; già esistente.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
