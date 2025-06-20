---
title: 'ACSD-51666: errore "La sessione è scaduta, effettua di nuovo l’accesso." dopo l’accesso'
description: Applica la patch ACSD-51666 per risolvere il problema Adobe Commerce in cui l’errore *La sessione è scaduta. Accedi di nuovo.* si verifica dopo il tentativo di accesso.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# ACSD-51666: errore *La sessione è scaduta. Effettuare di nuovo l&#39;accesso.* dopo l&#39;accesso

La patch ACSD-51666 risolve il problema relativo alla scadenza della sessione, *Accedere di nuovo.* si verifica dopo il tentativo di accesso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36. L’ID della patch è ACSD-51666. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Errore *La sessione è scaduta. Effettuare di nuovo l&#39;accesso.* quando si tenta di accedere con la nuova password da un dispositivo dopo aver reimpostato la password su un altro dispositivo. Ciò accade solo se nella pagina aggiunta da un modulo personalizzato è presente una richiesta Ajax aggiuntiva.

<u>Passaggi da riprodurre</u>:

1. Installa un modulo personalizzato che aggiunge una richiesta Ajax su ogni pagina della vetrina.
1. Crea un nuovo account.
1. Esci e torna alla pagina di accesso.
1. Apri il collegamento *Password dimenticata* in un altro browser e invia l&#39;e-mail *Reimposta password*.
1. Apri l’e-mail di reimpostazione della password nel primo browser e imposta la nuova password.
1. Prova ad accedere con il secondo browser.

<u>Risultati previsti</u>:

Al primo tentativo potrai effettuare l&#39;accesso.

<u>Risultati effettivi</u>:

* *La sessione è scaduta. Accedere di nuovo.Errore*.
* Non hai effettuato l’accesso e non sei reindirizzato alla home page.
* Il secondo tentativo di accesso è riuscito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
