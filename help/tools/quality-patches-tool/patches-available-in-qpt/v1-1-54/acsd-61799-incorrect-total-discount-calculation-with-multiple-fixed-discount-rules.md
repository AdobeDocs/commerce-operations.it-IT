---
title: 'ACSD-61799: calcolo dello sconto totale errato con più regole del carrello sconti fissi applicate all''offerta'
description: Applicare la patch ACSD-61799 per risolvere il problema di Adobe Commerce in cui lo sconto totale non viene calcolato correttamente quando al preventivo vengono applicate più regole del carrello con sconti fissi.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: calcolo dello sconto totale errato con più regole del carrello sconti fissi applicate all&#39;offerta

La patch ACSD-61799 risolve/risolve il problema relativo al calcolo errato dello sconto totale quando vengono applicate al preventivo più regole del carrello con sconti fissi. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-61799. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo sconto totale non viene calcolato correttamente quando a un carrello vengono applicate più regole del carrello con *[!UICONTROL Fixed amount discount for the whole cart]*.

<u>Passaggi da riprodurre</u>:

1. Crea quattro prodotti al prezzo di 1000 dollari.
1. Crea tre regole di prezzo del carrello senza condizioni che offrono uno sconto di 100 $ per l’intero carrello.
1. Crea un’altra regola di prezzo del carrello che offre uno sconto di 100 $ per l’intero carrello, con una condizione che impedisce l’applicazione della regola.
1. Disattiva la regola.
1. Aggiungi tre prodotti al carrello e osserva lo sconto nel carrello.
1. Aggiungi prodotti aggiuntivi al carrello e osserva lo sconto nel carrello.
1. Abilita la regola prezzi carrello disabilitata.
1. Aggiorna la pagina del carrello e osserva lo sconto nel carrello.

<u>Risultati previsti</u>:

1. L’aggiunta di prodotti aggiuntivi al carrello non modifica l’importo dello sconto.
1. Se si abilita la regola del prezzo del carrello con una condizione che non è applicabile, l’importo dello sconto non viene modificato.

<u>Risultati effettivi</u>:

1. L’aggiunta di prodotti aggiuntivi al carrello modifica l’importo dello sconto.
1. Se si abilita la regola del prezzo del carrello con una condizione che non viene applicata, viene modificato l’importo dello sconto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
