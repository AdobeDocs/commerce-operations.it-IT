---
title: 'ACSD-65195: La mutazione GraphQL &grave;createCompany&grave; restituisce un errore per un paese senza un’area geografica richiesta'
description: Applica la patch ACSD-65195 per risolvere il problema di Adobe Commerce, in cui la mutazione GraphQL "createCompany" genera un errore per i paesi che non richiedono un’area geografica.
feature: B2B, Companies, GraphQL
role: Admin, Developer
source-git-commit: 8eb1d7f9d787ddb3b1cc619744920ab8a9914ae8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-65195: la mutazione di GraphQL `createCompany` restituisce un errore per un paese senza area geografica richiesta

La patch ACSD-65195 risolve il problema per cui la mutazione [!UICONTROL GraphQL] `createCompany` genera un errore per i paesi che non richiedono una regione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. L’ID della patch è ACSD-65195. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La mutazione [!UICONTROL GraphQL] `createCompany` restituisce un errore quando viene specificata un&#39;area geografica per un paese che non ne richiede uno.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL B2B Companies]**.
1. Invia la mutazione `createCompany` [!UICONTROL GraphQL] con un campo di area specificato per un paese che non ne richiede una. Ad esempio: [!UICONTROL country_id]: *AE* e [!UICONTROL region]: *Dubai*.
1. Controlla la risposta di GraphQL.

<u>Risultati previsti</u>:

La società deve essere creata correttamente senza restituire un errore quando viene specificata un&#39;area geografica per un paese che non ne richiede una.

<u>Risultati effettivi</u>:

La società non viene creata e viene restituito il seguente errore:
`Error: Invalid value of "Dubai" provided for the region field.`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
