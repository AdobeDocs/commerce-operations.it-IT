---
title: 'ACSD-67039: i record cliente non sono stati salvati a causa della convalida dell''attributo di sistema rp_token'
description: Applica la patch ACSD-67039 per risolvere il problema di Adobe Commerce in cui i segni diacritici di codifica causano interruzioni di convalida su rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: i record cliente non sono stati salvati a causa della convalida dell&#39;attributo di sistema `rp_token`

La patch ACSD-67039 risolve il problema che impediva il salvataggio dei record dei clienti a causa della convalida dell&#39;attributo di sistema `rp_token` e che limitava la convalida dei segni diacritici all&#39;e-mail risultante. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-67039. Tieni presente che questo problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p9

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La codifica dei segni diacritici causa errori di convalida su `rp_token`, che è escluso dalla convalida. I segni diacritici sono consentiti solo per gli indirizzi e-mail, come previsto.

<u>Passaggi da riprodurre</u>:

1. Installa la versione 2.4.4 di Adobe Commerce.
1. Crea un cliente.
1. Aggiornare Adobe Commerce alla versione 2.4.6 dalla versione precedente 2.4.4 in cui il cliente era già stato creato.
1. Imposta la chiave di crittografia su `env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. Impostare i valori seguenti nel database per qualsiasi cliente nella tabella `customer_entity`:
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. Nel pannello di amministrazione, passa a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Modifica il cliente per il quale hai appena aggiornato i valori precedenti.
1. Fare clic su **[!UICONTROL Save Customer]** o **[!UICONTROL Save and Continue Edit]**.

<u>Risultati previsti</u>:

I valori del cliente vengono salvati correttamente.

<u>Risultati effettivi</u>:

Il record cliente non viene salvato e l&#39;utente amministratore visualizza il messaggio di errore *Si è verificato un errore durante il salvataggio del cliente.*
`system.log` contiene il seguente errore:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
