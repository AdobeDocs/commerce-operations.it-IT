---
title: 'ACSD-57570: correzione relativa all’accesso limitato degli utenti amministratori ai cataloghi condivisi'
description: Applica la patch ACSD-57570 per risolvere il problema di Adobe Commerce, a causa del quale un utente amministratore con restrizioni e accesso a un particolare archivio non può visualizzare in modo coerente tutti i cataloghi condivisi assegnati ai prodotti o salvare le informazioni sui clienti, causando incongruenze nel sistema.
feature: B2B, Companies, Roles/Permissions
role: Admin, Developer
exl-id: 3eeaf1f1-0338-459f-99ec-53764f3f12db
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---

# ACSD-57570: correzione relativa all’accesso limitato degli utenti amministratori ai cataloghi condivisi

La patch ACSD-57570 risolve il problema che impediva a un utente amministratore con restrizioni di accedere a un particolare archivio di visualizzare in modo coerente tutti i cataloghi condivisi assegnati ai prodotti o di salvare informazioni sui clienti, causando incongruenze nel sistema. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-57570. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4-p9

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore con accesso limitato a un particolare archivio non può sempre visualizzare tutti i cataloghi condivisi o salvare i clienti, con conseguenti incongruenze. Con più store, l’amministratore con restrizioni non può visualizzare nuove aziende o cataloghi condivisi personalizzati.

<u>Passaggi da riprodurre</u>:

1. Impostare i negozi nel seguente ordine:
   * Creare un nuovo sito Web denominato W2.
   * Crea una nuova visualizzazione Store per il sito Web predefinito.
   * Crea un nuovo store denominato W2S2 per il sito Web W2.
   * Creare una nuova visualizzazione dello store denominata W2S2SV1 per lo store W2S2.
   * Creare un&#39;altra nuova visualizzazione dello store denominata W2S2SV2 per lo store W2S2.
   * Crea una società per W2.
1. Assegna prodotti:
   * Assegnare alcuni prodotti solo a W1.
   * Assegnare alcuni prodotti solo a W2.
   * Assegnare alcuni prodotti a W1 e W2.
1. Crea un catalogo condiviso personalizzato e assegna a esso tutti i prodotti.
1. Creare un ruolo amministratore personalizzato con accesso solo a **W2S2**, non a **W2**.
1. Assegna l’utente amministratore con restrizioni al nuovo ruolo amministratore personalizzato.
1. Accedi come utente amministratore con restrizioni.
1. Verifica accesso:
   * Controlla quali aziende riesci a vedere.
   * Controlla quali cataloghi condivisi puoi visualizzare.
   * Apri l’elenco dei prodotti e verifica se puoi visualizzare tutti i cataloghi condivisi a cui sono assegnati i prodotti.

<u>Risultati previsti</u>:

Il comportamento deve essere coerente.

<u>Risultati effettivi</u>:

Se crei una sola visualizzazione aggiuntiva per sito web, store e store, l’utente amministratore con restrizioni può visualizzare la società, il catalogo condiviso ed entrambi i cataloghi condivisi nell’elenco dei prodotti. Con la configurazione di cui sopra, l’amministratore con restrizioni non può visualizzare la nuova società o il catalogo condiviso personalizzato e nell’elenco dei prodotti viene visualizzato solo il catalogo condiviso predefinito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
