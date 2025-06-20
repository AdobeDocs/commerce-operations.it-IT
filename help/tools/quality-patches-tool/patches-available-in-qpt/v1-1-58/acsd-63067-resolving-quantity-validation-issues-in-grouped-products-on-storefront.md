---
title: 'ACSD-63067: risoluzione dei problemi di convalida della quantità in prodotti raggruppati in vetrina'
description: Applica la patch ACSD-63067 per risolvere il problema di Adobe Commerce, in cui tutte le quantità di prodotti nei prodotti raggruppati vengono erroneamente evidenziate come non valide quando solo un prodotto presenta una quantità errata.
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: risoluzione dei problemi di convalida della quantità in prodotti raggruppati in vetrina

La patch ACSD-63067 risolve il problema che tutte le quantità di prodotti nei prodotti raggruppati vengono erroneamente evidenziate come non valide quando solo un prodotto ha una quantità errata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63067. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nei prodotti raggruppati, una quantità non valida in uno dei sottoprodotti fa sì che tutte le quantità vengano erroneamente evidenziate come non valide. Inoltre, viene visualizzato un messaggio di convalida per tutti i prodotti, anziché solo per quello con la quantità non valida.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo prodotto raggruppato con almeno due prodotti semplici come opzioni.
1. Apri il prodotto nella vetrina.
1. Immettere una quantità non valida (ad esempio: -1) per una delle opzioni e una quantità valida (ad esempio: 1) per le opzioni rimanenti.
1. Fare clic su **[!UICONTROL Add to Cart]**.

<u>Risultati previsti</u>:

Solo il prodotto con quantità non valida viene evidenziato come non valido.

<u>Risultati effettivi</u>:

Tutte le quantità di prodotti sono evidenziate come non valide e il messaggio *Specificare la quantità di prodotti. viene visualizzato per tutti i prodotti*.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
