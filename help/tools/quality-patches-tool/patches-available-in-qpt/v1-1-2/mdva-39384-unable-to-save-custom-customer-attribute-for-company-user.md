---
title: 'MDVA-39384: impossibile salvare l''attributo cliente personalizzato per l''utente della società'
description: La patch MDVA-39384 risolve il problema che impedisce il salvataggio dell'attributo cliente personalizzato per un utente aziendale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-39384. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
exl-id: 0ccaa4c5-ca43-4b25-963b-b9a547ecc71f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: impossibile salvare l&#39;attributo cliente personalizzato per l&#39;utente della società

La patch MDVA-39384 risolve il problema che impedisce il salvataggio dell&#39;attributo cliente personalizzato per un utente aziendale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-39384. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’attributo cliente personalizzato per un utente della società non viene salvato.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > Impostazioni > **Configurazione** > **Caratteristiche B2B** e imposta **Abilita società** su Sì.
1. Creare un attributo cliente personalizzato:
   * Valori obbligatori: sì (facoltativo, abilitarlo in modo da visualizzare l’errore di convalida).
   * Mostra su Storefront: sì.
   * Forms da utilizzare in: tutto disponibile nell’elenco.
1. Crea una società e accedi come amministratore della società.
1. Passa alla struttura aziendale nel tuo account.
1. Fai clic sul collegamento **Aggiungi utente**.
1. Compila il modulo con l’attributo personalizzato.
1. Fai clic su **Salva**.

<u>Risultati previsti</u>:

I valori degli attributi personalizzati vengono salvati con il nuovo utente aziendale.

<u>Risultati effettivi</u>:

I valori degli attributi personalizzati NON vengono salvati con il nuovo utente aziendale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
