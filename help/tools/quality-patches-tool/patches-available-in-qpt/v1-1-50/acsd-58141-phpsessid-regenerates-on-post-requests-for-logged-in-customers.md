---
title: 'ACSD-58141: PHPSESSID viene rigenerato nelle richieste POST per i clienti connessi con la cache L2 Redis abilitata'
description: Applica la patch ACSD-58141 per risolvere il problema Adobe Commerce in cui "PHPSESSID" si rigenera sulle richieste POST nell’area Storefront per un cliente connesso con la cache L2 Redis abilitata e il cliente viene aggiornato dall’Amministratore.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# ACSD-58141: PHPSESSID viene rigenerato in [!DNL POST] richieste per i clienti connessi se la cache L2 Redis è abilitata

La patch ACSD-58141 risolve il problema relativo alla rigenerazione di `PHPSESSID` in [!DNL POST] richieste per un cliente connesso se la cache L2 Redis è abilitata e il cliente viene aggiornato dall&#39;amministratore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. L’ID della patch è ACSD-58141. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con Adobe Commerce e Magento Open Source:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`PHPSESSID` viene rigenerato su [!DNL POST] richieste per un cliente connesso con la cache L2 Redis abilitata.

<u>Prerequisiti</u>

L’ambiente deve essere configurato con Redis con almeno 3 nodi.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea un cliente e accedi a Storefront.
1. Verificare il valore di `PHPSESSID`.
1. Invia alcune [!DNL POST] richieste (ad esempio, aggiungendo un prodotto al carrello) e osserva che `PHPSESSID` rimane invariato).
1. Accedi al pannello **[!UICONTROL Admin]** e cambia il secondo nome del cliente.
1. Quando il secondo nome viene salvato, modificarlo e salvarlo di nuovo alcune volte.
1. Nella vetrina, invia una richiesta [!DNL POST]. `PHPSESSID` avrebbe dovuto essere aggiornato.
1. Nella vetrina, invia un&#39;altra richiesta [!DNL POST] e controlla `PHPSESSID`.
1. Ripetere più volte il passaggio precedente.

<u>Risultati previsti</u>

`PHPSESSID` viene rigenerato una sola volta dopo la modifica dei dati del cliente.

<u>Risultati effettivi</u>:

`PHPSESSID` viene rigenerato ogni volta che vengono inviate le [!DNL POST] richieste.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
