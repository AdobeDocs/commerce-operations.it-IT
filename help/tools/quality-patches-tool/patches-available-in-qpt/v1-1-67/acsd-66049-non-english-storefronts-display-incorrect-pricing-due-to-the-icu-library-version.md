---
title: 'ACSD-66049: i vetrine non inglesi mostrano prezzi errati a causa della versione della libreria ICU'
description: Applica la patch ACSD-66049 per risolvere il problema Adobe Commerce, in cui gli store front non inglesi mostrano prezzi errati a causa della mancata corrispondenza della versione della libreria ICU negli ambienti PHP precedenti (versioni da 63.1 a 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 39e0b972dfa41f74f3c19e61d8fc1188d5c93f7c
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-66049: i vetrine non inglesi mostrano prezzi errati a causa della versione della libreria ICU

La patch ACSD-66049 risolve il problema della visualizzazione di prezzi non corretti da parte di storefront non inglesi a causa della mancata corrispondenza delle versioni della libreria ICU nei vecchi ambienti PHP (versioni da 63.1 a 74.1). Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66049. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I vetrine non inglesi mostrano prezzi errati quando si utilizzano versioni precedenti della libreria PHP ICU (da 63.1 a 74.1).

<u>Passaggi da riprodurre</u>:

1. Verifica versione ICU:
   * Connettersi al server tramite SSH ed eseguire il comando: `php -a`
   * Al prompt, immettere: `echo INTL_ICU_VERSION;`
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[UICONTOL Ebraico (Israele)]*.
1. Crea un prodotto con prezzo = 100.
1. Visualizza la pagina del prodotto nella vetrina.

<u>Risultati previsti</u>:

Il prezzo visualizzato non è 0.

<u>Risultati effettivi</u>:

Dopo essere comparso brevemente come 100, il prezzo viene immediatamente aggiornato a 0.
(Questo problema riguarda le versioni da 63.1 a 74.1 della libreria ICU PHP).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
