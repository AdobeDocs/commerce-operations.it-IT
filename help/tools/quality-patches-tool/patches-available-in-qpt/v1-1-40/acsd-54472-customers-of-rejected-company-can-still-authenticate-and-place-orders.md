---
title: 'ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione'
description: Applicare la patch ACSD-54472 per risolvere il problema di Adobe Commerce, in cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata e rifiutata possono ancora effettuare ordini.
feature: B2B
role: Admin, Developer
exl-id: c0bd960f-609b-4253-9fc8-dc47fbbddc93
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-54472: i clienti di un’azienda rifiutata possono ancora eseguire l’autenticazione

La patch ACSD-54472 risolve il problema per cui i clienti di una società rifiutata possono ancora autenticarsi e i clienti di una società bloccata o rifiutata possono ancora effettuare ordini. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. L’ID della patch è ACSD-54472. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
