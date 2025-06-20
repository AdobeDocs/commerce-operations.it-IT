---
title: 'ACSD-51471: l’utente amministratore non può salvare l’aggiornamento pianificato per il prodotto in bundle'
description: Applica la patch ACSD-51471 per risolvere il problema di Adobe Commerce, a causa del quale un utente amministratore non può salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.
exl-id: d8134111-63f0-4476-a407-677bda52fa90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-51471: l’utente amministratore non può salvare l’aggiornamento pianificato per il prodotto in bundle

La patch ACSD-51471 risolve il problema per cui un utente amministratore non può salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. L’ID della patch è ACSD-51471. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti amministratori non possono salvare un aggiornamento pianificato per un prodotto in bundle che utilizza un prodotto semplice con un aggiornamento pianificato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Aggiungi un aggiornamento pianificato per il prodotto semplice con solo la *data iniziale* e nessuna *data finale*.
1. Dopo aver applicato l’aggiornamento, modifica lo SKU del prodotto.
1. Crea un prodotto in bundle e aggiungi il prodotto semplice creato nel passaggio 1 come prodotto secondario.
1. Crea un aggiornamento pianificato per il prodotto nel pacchetto per abilitare il prodotto nel pacchetto. Fornisci sia *Data inizio* che *Data fine* per l&#39;aggiornamento pianificato.
1. Salva l’aggiornamento pianificato.

<u>Risultati previsti</u>:

L&#39;aggiornamento pianificato è stato salvato.

<u>Risultati effettivi</u>:

Durante il salvataggio dell&#39;aggiornamento pianificato si verifica l&#39;errore seguente: *Il prodotto richiesto non esiste. Verificare il prodotto e riprovare.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
