---
title: 'ACSD-63242: importazione lenta quando si aggiungono più di 10.000 prodotti catalogo'
description: Applica la patch ACSD-63242 per risolvere il problema Adobe Commerce delle importazioni lente quando vengono aggiunti prodotti di catalogo con più di 10.000 voci.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 5fe00c9341414a0a2ba6b535d992d6c64e1c3b3a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242: importazione lenta quando si aggiungono più di 10.000 prodotti catalogo

La patch ACSD-63242 risolve il problema delle importazioni lente quando vengono aggiunti prodotti di catalogo con più di 10.000 voci. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-63242. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8 e 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione dei prodotti è lenta quando si aggiungono prodotti del catalogo con più di 10.000 voci.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]**.
1. Importa file con più di 10.000 voci.

<u>Risultati previsti</u>:

L’importazione dei prodotti del catalogo viene eseguita nel tempo previsto.

<u>Risultati effettivi</u>:

L&#39;importazione dei prodotti è lenta. `var/log/exception.log` contiene:

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
