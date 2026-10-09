---
title: 'ACSD-51666: errore "La sessione è scaduta, effettua di nuovo l’accesso." dopo l’accesso'
description: Applica la patch ACSD-51666 per risolvere il problema di Adobe Commerce se l’errore *La sessione è scaduta, effettua di nuovo l’accesso.* si verifica dopo aver tentato di accedere.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%
---
# ACSD-51666: Errore *La sessione è scaduta. Effettuare di nuovo l&#39;accesso.* dopo l’accesso

La patch ACSD-51666 risolve il problema relativo alla scadenza della sessione. *Accedere di nuovo.* si verifica dopo il tentativo di accesso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36. L’ID della patch è ACSD-51666. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene visualizzato l&#39;errore *La sessione è scaduta. Accedere di nuovo.* quando si tenta di accedere con la nuova password da un dispositivo dopo aver reimpostato la password su un altro dispositivo. Ciò accade solo se nella pagina aggiunta da un modulo personalizzato è presente una richiesta Ajax aggiuntiva.

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

* *La sessione è scaduta. Effettuare di nuovo l&#39;accesso.* errore.
* Non hai effettuato l’accesso e non sei reindirizzato alla home page.
* Il secondo tentativo di accesso è riuscito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
