---
title: 'ACSD-48313: colonna [!UICONTROL configurable_variations] non analizzata se il valore dell''attributo contiene la virgola'
description: Applica la patch ACSD-48313 per risolvere il problema Adobe Commerce, in cui la colonna [!UICONTROL configurable_variations] non viene analizzata se il valore dell’attributo contiene una virgola.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-48313: colonna **[!UICONTROL configurable_variations]** non analizzata se il valore dell&#39;attributo contiene la virgola

La patch ACSD-48313 risolve il problema in cui la colonna **[!UICONTROL configurable_variations]** non viene analizzata se il valore dell&#39;attributo contiene una virgola. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-48313. La versione in cui verrà risolto il problema non è ancora disponibile.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo l&#39;esportazione di prodotti configurabili, non è possibile importare nuovamente il file risultante a causa di un problema di formattazione con l&#39;attributo **[!UICONTROL configurable_variations]**. Ciò si verifica quando sono presenti opzioni di attributo che includono una virgola.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** e crea un nuovo attributo _Size_:
1. Tipo di input del catalogo per il proprietario del negozio: **[!UICONTROL Dropdown]**.
1. Crea opzioni che includono una virgola, ad esempio:
   * 10,2 cm
   * 15,5 cm
1. **[!UICONTROL Advanced Attribute Properties]** - Ambito: _Globale_.
1. Crea un nuovo prodotto configurabile utilizzando la funzionalità Crea configurazioni.
1. Selezionare l&#39;attributo _Dimensione_ e le due opzioni che includono la virgola.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** e crea una nuova esportazione di prodotti (esegui il cron per attivare la generazione del file CSV).
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e prova a reimportare lo stesso file CSV creato in precedenza.

<u>Risultati previsti</u>:

L’utente deve essere in grado di importare il file.

<u>Risultati effettivi</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
