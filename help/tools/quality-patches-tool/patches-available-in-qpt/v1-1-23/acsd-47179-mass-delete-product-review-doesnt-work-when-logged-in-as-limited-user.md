---
title: 'ACSD-47179: l’eliminazione di massa delle recensioni dei prodotti non funziona se si accede come ruolo utente limitato'
description: Applica la patch ACSD-47179 per risolvere il problema di Adobe Commerce, in cui l’eliminazione di massa delle revisioni dei prodotti non funziona quando si accede come ruolo utente limitato.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: l’eliminazione di massa delle recensioni dei prodotti non funziona se si accede come ruolo utente limitato

La patch ACSD-47179 risolve il problema dell’eliminazione di massa delle revisioni dei prodotti quando si accede come ruolo utente limitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23. L’ID della patch è ACSD-47179. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’eliminazione di massa delle revisioni dei prodotti non funziona se si accede come ruolo utente limitato.

<u>Passaggi da riprodurre</u>:

1. Crea un sito Web secondario.
1. Crea un ruolo utente limitato al sito Web secondario con autorizzazioni complete per le sezioni seguenti:
   * Catalogo
   * Cliente
   * Marketing
1. Crea un prodotto e assegnalo al sito web secondario.
1. Aggiungi due recensioni al prodotto dal front-end.
1. Accedere all&#39;amministratore [!DNL Commerce] utilizzando l&#39;utente amministratore con restrizioni appena creato.
1. Prova a eliminare in massa le recensioni in sospeso.

<u>Risultati previsti</u>:

Un amministratore con autorizzazioni sufficienti è in grado di eliminare in massa le revisioni in sospeso.

<u>Risultati effettivi</u>:

Si è verificato il seguente errore: _Si è verificato un errore. Eccezione generata in support_report.log_

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
