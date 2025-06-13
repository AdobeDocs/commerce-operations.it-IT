---
title: 'MDVA-43178: impossibile recuperare in GraphQL il token cliente per l''archivio personalizzato'
description: La patch MDVA-43178 risolve il problema che impediva il recupero in GraphQL del token cliente per un archivio personalizzato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L'ID della patch è MDVA-43178. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: GraphQL
role: Admin
exl-id: 8dd9c9e7-573c-4c7a-8fd0-3b3886649af3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-43178: impossibile recuperare in GraphQL il token cliente per l&#39;archivio personalizzato

La patch MDVA-43178 risolve il problema che impediva il recupero in GraphQL del token cliente per un archivio personalizzato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L&#39;ID della patch è MDVA-43178. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Impossibile recuperare in GraphQL il token cliente per un archivio personalizzato.

<u>Passaggi da riprodurre</u>:

1. Crea due visualizzazioni store per lo store predefinito.
1. Crea un nuovo sito Web, un Negozio e una Visualizzazione Store. Denomina &#39;test3&#39; la visualizzazione archivio.
1. Crea un cliente per il nuovo sito web.
1. Genera token di amministrazione API:

   `http://domain/rest/all/V1/integration/admin/token`

   <pre>
    <code class="language-graphql">
    &lbrace;
      "username": "login",
      "password": "password"
    &rbrace;
    </code>
    </pre>

1. Invia a GraphQL per recuperare il token cliente come amministratore, utilizza il token amministratore per l’autorizzazione, con &quot;store&quot; = &quot;test3&quot; nell’intestazione:

   <pre>
    <customer_email>
      </pre>

<u>Risultati previsti</u>:

Token cliente generato.

<u>Risultati effettivi</u>:

Token cliente non generato. I commercianti ricevono *L&#39;e-mail fornita dal cliente non esiste* nella risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
