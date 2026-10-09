---
title: 'ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione'
description: Applicare la patch ACSD-54472 per risolvere il problema di Adobe Commerce, in cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata e rifiutata possono ancora effettuare ordini.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '473'
ht-degree: 0%
---
# ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione

La patch ACSD-54472 risolve il problema per cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata o rifiutata possono ancora effettuare ordini. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54472. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata o rifiutata possono ancora effettuare ordini.

<u>Passaggi da riprodurre</u>:

1. Crea una società.
1. Aggiungi prodotti al carrello tramite [!DNL GraphQL].
1. Cambia lo stato dell&#39;azienda in *Bloccato*.
1. Invia una richiesta [!DNL GraphQL] per effettuare l&#39;ordine e creare un preventivo negoziabile.
1. Cambia lo stato dell&#39;azienda in *Rifiutato*.
1. Invia una richiesta [!DNL GraphQL] per ottenere il token di autorizzazione utente della società.
1. Imposta lo stato del cliente su *Inattivo*.
1. Invia una richiesta [!DNL GraphQL] per ottenere il token di autorizzazione utente della società.

<u>Risultati previsti</u>:

* L&#39;ordine e l&#39;offerta negoziabile non sono stati inseriti dall&#39;utente della società *Bloccata*.
* Token di autorizzazione non ottenuto per l&#39;utente della società *Rifiutato*.
* Token di autorizzazione non ottenuto per il cliente *Inattivo*.

<u>Risultati effettivi</u>:

* L&#39;ordine e l&#39;offerta negoziabile vengono inseriti dall&#39;utente della società *Bloccata*.
* Token di autorizzazione ottenuto per l&#39;utente della società *Rifiutato*.
* Token di autorizzazione ottenuto per il cliente *Inattivo*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
