---
title: 'MDVA-40619: le modifiche della gerarchia interrompono la modifica in linea della pagina CMS e generano l''errore 500'
description: La patch MDVA-40619 risolve il problema relativo alle modifiche apportate alla gerarchia delle pagine di CMS che causano l'interruzione della modifica in linea della pagina di CMS e la generazione di "errore 500". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. L'ID della patch è MDVA-40619. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: CMS
role: Admin
exl-id: 148cb0a5-5a6c-4cfa-bf95-4bafc57beec6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# MDVA-40619: le modifiche della gerarchia interrompono la modifica in linea della pagina CMS e generano l&#39;errore 500

La patch MDVA-40619 risolve il problema relativo alle modifiche apportate alla gerarchia delle pagine di CMS che causano l&#39;interruzione della modifica in linea della pagina di CMS e la generazione di &quot;errore 500&quot;. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. L&#39;ID della patch è MDVA-40619. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche della gerarchia di pagine CMS interrompono la modifica in linea della pagina CMS e generano &quot;errore 500&quot;.

<u>Passaggi da riprodurre</u>:

1. Vai a Pannello di amministrazione > **Contenuto** > **Gerarchia**.
1. Seleziona &quot;Visualizzazione store predefinita&quot;.
1. Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
1. Seleziona la pagina manualmente e fai clic su **Salva**.
1. Quindi Vai a **Contenuto** > **Pagine**.
1. Prova a modificare qualsiasi pagina di CMS dalla griglia.
1. Fai clic su **Salva**.

<u>Risultati previsti</u>:

La pagina è stata salvata.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

*Un problema tecnico con il server ha creato un errore. Riprova a continuare quello che stavi facendo. Se il problema persiste, riprovare più tardi.*

`Error: Call to a member function getData() on null in /magento2ee/app/code/Magento/VersionsCms/Controller/Adminhtml/Cms/Page/InlineEdit/Plugin.php:62`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
