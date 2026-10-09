---
title: 'ACSD-46703: il trascinamento della personalizzazione del prodotto non funziona'
description: Questo articolo fornisce una soluzione per il problema in cui il trascinamento e il rilascio delle opzioni personalizzabili del prodotto non funzionano come previsto.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-46703: il trascinamento della personalizzazione del prodotto non funziona

La patch ACSD-46703 risolve il problema relativo al mancato funzionamento delle opzioni personalizzabili del prodotto (trascinamento della selezione). Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-46703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono trascinare e rilasciare le opzioni personalizzabili da una pagina all’altra.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Aggiungi opzioni personalizzabili al prodotto semplice e assicurati di aggiungere più di 20 opzioni con conseguente impaginazione.
1. Prova a spostare un’opzione personalizzabile (tramite trascinamento) all’interno della stessa pagina.
1. Ora prova a spostare un’opzione personalizzabile dalla pagina 2 alla pagina 1.

<u>Risultati previsti</u>:

* Puoi trascinare le opzioni personalizzabili da una pagina all’altra.
* Puoi ordinare i valori utilizzando la funzionalità di trascinamento della selezione, anche per più pagine.

<u>Risultati effettivi</u>:

Non puoi spostare alcun valore in un’altra pagina utilizzando la funzionalità di trascinamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Strumenti patch di qualità > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida dello strumento Patch di qualità.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
