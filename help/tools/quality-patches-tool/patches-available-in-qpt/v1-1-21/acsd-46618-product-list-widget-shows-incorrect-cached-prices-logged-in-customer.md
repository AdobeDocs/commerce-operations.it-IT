---
title: 'ACSD-46618: il widget dell’elenco prodotti mostra prezzi non corretti nella cache per il cliente connesso'
description: Applica una patch per risolvere il problema di Adobe Commerce, in cui il widget dell’elenco dei prodotti mostra prezzi memorizzati nella cache non corretti per un cliente connesso.
feature: Cache, Orders, Products
role: Admin
exl-id: fa350f84-2fe5-474b-b4fd-d6c1e8bb0f95
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-46618: il widget elenco prodotti mostra prezzi memorizzati nella cache non corretti per un cliente connesso

La patch ACSD-46618 risolve il problema relativo alla visualizzazione di prezzi non corretti nella cache da parte del widget elenco prodotti per un cliente connesso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21. L’ID della patch è ACSD-46618. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch ACSD-46618 risolve il problema relativo alla visualizzazione di prezzi non corretti nella cache da parte del widget elenco prodotti per un cliente connesso.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, selezionare **[!UICONTROL Stores]**, quindi **[!UICONTROL Configuration]**, espandere **[!UICONTROL Sales]** e selezionare **[!UICONTROL Tax]**. Aggiornare le impostazioni relative alle imposte per visualizzare i prezzi, incluse e escluse le imposte.
1. Imposta **[!UICONTROL Enable Cross Border Trade]** = _Sì_.
1. Creare una regola fiscale applicabile solo agli Stati Uniti.
1. Aggiungi un widget alla home page che include più di un prodotto.
1. Crea due clienti con un indirizzo USA e un indirizzo non USA.
1. Accedi utilizzando il cliente americano dalla vetrina. Assicurati che la pagina sia memorizzata in cache.
1. Osserva il prezzo visualizzato nel widget della pagina principale.
1. Esci e accedi utilizzando il cliente non statunitense.

<u>Risultati previsti</u>:

Il prezzo visualizzato nel widget della home page corrisponde all&#39;indirizzo del cliente.

<u>Risultati effettivi</u>:

Il widget della pagina Home mostra i prezzi utilizzando l’imposta per i clienti non statunitensi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
