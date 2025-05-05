---
title: 'ACSD-62793: attributi Datetime nelle esportazioni per cui manca il componente time. Inoltre, se **[!UICONTROL Fields Enclosure]** abilitato, i valori degli attributi racchiusi tra virgolette doppie'
description: Applica la patch ACSD-62793 per risolvere il problema di Adobe Commerce per cui negli attributi datetime nei dati esportati manca il componente time. Inoltre, se **[!UICONTROL Fields Enclosure]** è abilitato, i valori degli attributi nella colonna *additional_attributes* saranno racchiusi tra virgolette doppie.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
source-git-commit: 1645006f142c902ac729a99502f59b6d42266691
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# ACSD-62793: attributi Datetime nelle esportazioni per cui manca il componente time. Inoltre, se **[!UICONTROL Fields Enclosure]** è abilitato, i valori degli attributi racchiusi tra virgolette doppie

La patch ACSD-62793 risolve il problema per cui gli attributi datetime nei dati esportati non contengono il componente time. Inoltre, se **[!UICONTROL Fields Enclosure]** è abilitato, i valori degli attributi nella colonna *additional_attributes* verranno racchiusi tra virgolette doppie. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-62793. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli attributi Datetime nei dati esportati non includono il componente time. Inoltre, se **[!UICONTROL Fields Enclosure]** è abilitato, i valori degli attributi nella colonna *additional_attributes* verranno racchiusi tra virgolette doppie.

<u>Passaggi da riprodurre</u>:

1. Creare un attributo di prodotto con **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Assegnare l&#39;attributo al set di attributi **[!UICONTROL Default]**.
1. Crea un prodotto semplice con un valore di data e ora per il nuovo attributo.
1. Esporta il prodotto in un file CSV da **[!UICONTROL System]** > *Trasferimento dati* > **[!UICONTROL Export]**.
1. Controlla il valore dell&#39;attributo nella colonna *additional_attributes*. Ha solo la parte della data, ma non l’ora.
1. Aggiorna il valore dell’attributo in modo che utilizzi l’ora, ad esempio &quot;08/10/22, 3:20 PM&quot;.
1. Importa il file CSV.
1. Controlla la tabella *catalog_product_entity_datetime*.

<u>Risultati previsti</u>:

La data e l’ora vengono esportate e importate correttamente.

<u>Risultati effettivi</u>:

Solo la parte della data viene esportata e importata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
