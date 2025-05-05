---
title: 'ACSD-64684: errore di convalida durante il salvataggio di una gift card con un valore superiore a 999 a causa della virgola in mille (1.000)'
description: Applica la patch ACSD-64684 per risolvere il problema Adobe Commerce, se si verifica un errore di convalida durante il salvataggio di una gift card con valore superiore a 999 a causa della virgola in "mille" (1.000).
feature: Catalog Management
role: Admin, Developer
source-git-commit: 58d385c0e3479f5f9d826dc6e892c8ec2ebfdbb5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-64684: errore di convalida durante il salvataggio di una gift card con un valore superiore a 999 a causa della virgola in mille (1.000)

La patch ACSD-64684 risolve il problema relativo a un errore di convalida durante il salvataggio di una gift card con un valore superiore a 999 a causa della virgola in &quot;mille&quot; (1.000). Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64684. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore di convalida durante la modifica e il salvataggio di una gift card con un valore maggiore di 999 a causa della virgola (separatore delle migliaia) nel numero, ad esempio &#39;mille&#39; (1.000).

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto gift card.
   1. Immetti 1.000 come [!UICONTROL Amount].
   1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

* La nuova gift card con un importo di 1.000 viene salvata.

<u>Risultati effettivi</u>:

* Se l&#39;importo della gift card è maggiore di 999, si verifica un errore di convalida.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
