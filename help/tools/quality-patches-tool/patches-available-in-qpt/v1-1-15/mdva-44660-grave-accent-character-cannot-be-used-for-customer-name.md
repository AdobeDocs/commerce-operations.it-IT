---
title: 'MDVA-44660: impossibile utilizzare il carattere accento grave per il nome del cliente'
description: La patch MDVA-44660 risolve il problema che impediva l'utilizzo del carattere di accento grave per il nome di un cliente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L'ID della patch è MDVA-44660. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: 603161bf-fac3-4571-b872-d98de1bdf6b4
source-git-commit: 42e95722c59d29864bc631b5fadbe0bc520c8997
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# MDVA-44660: impossibile utilizzare il carattere di accento grave (&grave;) per il nome del cliente

La patch MDVA-44660 risolve il problema che impediva l&#39;utilizzo del carattere di accento grave (\`) per il nome di un cliente. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.15. L&#39;ID della patch è MDVA-44660. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il carattere grave (\`) non può essere utilizzato per il nome e il cognome di un cliente.

<u>Passaggi da riprodurre</u>:

Crea un nuovo cliente dall’account Amministratore o registrati sullo Storefront utilizzando il carattere con accento grave nel nome o nel cognome, ad esempio &quot;L’Epicerie&quot;.

<u>Risultati previsti</u>:

È possibile creare un nuovo cliente il cui nome contenga il carattere di accento grave.

<u>Risultati effettivi</u>:

*Il nome non è valido.* O *Il cognome non è valido* viene visualizzato l&#39;errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
