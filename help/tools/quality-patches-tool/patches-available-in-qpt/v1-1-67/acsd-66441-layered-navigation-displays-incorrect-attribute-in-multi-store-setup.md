---
title: 'ACSD-66441: la navigazione a livelli visualizza opzioni di attributo errate in una configurazione con più store'
description: Applicare la patch ACSD-66441 per risolvere il problema di Adobe Commerce, in cui la navigazione a livelli mostra gli attributi di altri archivi in modo errato in una configurazione multi-store.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66441: la navigazione a livelli visualizza opzioni di attributo errate in una configurazione con più store

La patch ACSD-66441 risolve il problema relativo alla visualizzazione errata degli attributi di altri archivi in una configurazione multi-store. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66441. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La navigazione a livelli nella vetrina include i valori degli attributi di altri negozi, anche quando tali prodotti non sono disponibili nella vista dello store corrente.

<u>Passaggi da riprodurre</u>:

1. Crea una visualizzazione secondaria per sito Web, store e store.
1. Crea un prodotto configurabile utilizzando un attributo personalizzato (ad esempio, dimensione).
1. Assegna il prodotto configurabile al sito web principale e a una categoria.
1. Reindicizza tutti i dati.
1. Passa alla categoria assegnata nella vetrina. Tutte le opzioni di dimensione vengono visualizzate correttamente in Navigazione a livelli.
1. Annullare l&#39;assegnazione di due prodotti semplici dal sito Web principale e assegnarli al sito Web secondario oppure rimuoverli dal sito Web principale.
1. Reindicizza tutti i dati.
1. Rivedi la pagina della categoria vetrina e controlla la sezione Navigazione a livelli.

<u>Risultati previsti</u>:

Nella barra di navigazione a livelli vengono visualizzate solo le opzioni attributo dei prodotti assegnati all&#39;archivio o al sito Web corrente.

<u>Risultati effettivi</u>:

In Navigazione a livelli vengono visualizzate le opzioni (dimensioni) degli attributi dei prodotti assegnati ad altri store o siti Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
