---
title: 'ACSD-65540: errore SQL dovuto alla mancanza della funzione REGEXP_LIKE negli aggiornamenti company_structure'
description: Applicare la patch ACSD-65540 per risolvere il problema Adobe Commerce in cui si verifica un errore SQL a causa della mancanza della funzione REGEXP_LIKE negli aggiornamenti company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%
---
# ACSD-65540: errore SQL a causa della mancanza della funzione `REGEXP_LIKE` in `company_structure` aggiornamenti

La patch ACSD-65540 risolve il problema relativo all&#39;errore SQL dovuto alla mancanza della funzione `REGEXP_LIKE` negli aggiornamenti di `company_structure`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. L’ID della patch è ACSD-65540.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce B2B (tutti i metodi di implementazione) 1.5.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce B2B (tutti i metodi di implementazione) 1.5.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si è verificato un errore di sintassi SQL a causa della mancanza della funzione `REGEXP_LIKE` negli aggiornamenti `company_structure`.

<u>Passaggi da riprodurre</u>:

1. Aggiornare [!DNL B2B] alla versione 1.5.2.
1. Esegui il comando seguente:

```shell
bin/magento setup:upgrade
```

<u>Risultati previsti</u>:

Aggiornamento completato.

<u>Risultati effettivi</u>:

```text
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
