---
title: 'ACSD-65540: errore SQL dovuto alla mancanza della funzione REGEXP_LIKE negli aggiornamenti company_structure'
description: Applicare la patch ACSD-65540 per risolvere il problema Adobe Commerce in cui si verifica un errore SQL a causa della mancanza della funzione REGEXP_LIKE negli aggiornamenti company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
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
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si è verificato un errore di sintassi SQL a causa della mancanza della funzione `REGEXP_LIKE` negli aggiornamenti `company_structure`.

<u>Passaggi da riprodurre</u>:

1. Aggiornare [!DNL B2B] alla versione 1.5.2.
1. Esegui il comando seguente:

```
bin/magento setup:upgrade
```

<u>Risultati previsti</u>:

Aggiornamento completato.

<u>Risultati effettivi</u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
