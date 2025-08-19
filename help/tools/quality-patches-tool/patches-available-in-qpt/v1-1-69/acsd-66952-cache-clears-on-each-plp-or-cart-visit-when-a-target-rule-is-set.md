---
title: 'ACSD-66952: la cache si cancella a ogni visita del PLP o del carrello quando viene impostata una regola di destinazione'
description: Applica la patch ACSD-66952 per risolvere il problema di Adobe Commerce in cui la cache veniva cancellata su ogni visita del PLP o del carrello, causando un sovraccarico di prestazioni non necessario, quando veniva impostata una regola target.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
source-git-commit: 1aec8de86696ffc9ecb13100e6ffa1f912b281fb
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# ACSD-66952: la cache si cancella a ogni visita del PLP o del carrello quando viene impostata una regola di destinazione

La patch ACSD-66952 risolve il problema della cancellazione della cache in ogni visita al PLP o al carrello, causando un sovraccarico delle prestazioni quando viene impostata una regola target. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66952. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Problema che causa la cancellazione della cache in ogni visita del PLP o del carrello e un sovraccarico delle prestazioni quando viene impostata una regola di destinazione.

<u>Passaggi da riprodurre</u>:

1. Genera un piccolo set di dati di esempio.
1. Crea i valori delle regole di destinazione come segue:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Prodotti correlati*
      * **[!UICONTROL Status]** = *Attivo*
      * **[!UICONTROL Apply to]** = *Prodotti correlati*
   1. **[!UICONTROL Products to Match]**
      * Lascia il valore predefinito.
   1. **[!UICONTROL Products to Display]**
      * Se **ALL** di queste condizioni sono *true*, impostare **[!UICONTROL Product Category]** = *Valore costante 111111*
1. Avvia il monitoraggio dei registri per le richieste di invalidamento della cache.
1. Visita la pagina del prodotto.
1. Aggiungi un prodotto al carrello e passa alla pagina del carrello.

<u>Risultati previsti</u>:

L’applicazione non deve invalidare la cache durante la navigazione nel sito.

<u>Risultati effettivi</u>:

I tag della cache vengono invalidati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
