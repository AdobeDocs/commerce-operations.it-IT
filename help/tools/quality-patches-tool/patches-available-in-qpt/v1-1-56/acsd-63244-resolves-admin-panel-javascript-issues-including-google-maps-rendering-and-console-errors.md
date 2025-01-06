---
title: 'ACSD-63244: risoluzione dei problemi di JavaScript del pannello di amministrazione, inclusi  [!DNL Google Maps]  errori di rendering e console'
description: La patch ACSD-63244 risolve i diversi problemi di JavaScript nel pannello di amministrazione, inclusi i problemi relativi al rendering di  [!DNL Google Maps]  e al ricorrente errore di tipo "Uncovered TypeError"._each is not a function` errors (ciascuno non è una funzione) nella console del browser.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: 01d6d74bfb9a9491bc006f140a2eebf4bbee004b
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-63244: ACSD-63244: Risoluzione dei problemi del pannello di amministrazione di JavaScript, inclusi [!DNL Google Maps] errori di rendering e console

La patch ACSD-63244 risolve i diversi problemi di JavaScript nel pannello di amministrazione, inclusi i problemi relativi al rendering di [!DNL Google Maps] e gli errori ricorrenti di `Uncaught TypeError: this._each is not a function` nella console del browser. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-63244. Il problema era pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

* L&#39;errore `Uncaught TypeError: this._each is not a function` viene visualizzato nella console del browser, interrompendo le funzionalità dell&#39;interfaccia utente di amministrazione.
* Errore JavaScript impedisce a [!DNL Google Maps] di eseguire correttamente il rendering.

<u>Passaggi da riprodurre</u>:

1. Carica l’interfaccia utente di amministrazione di Adobe Commerce.
1. Apri la console del browser ed esegui il seguente script:

   ```
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Risultati previsti</u>:

Le funzioni di JavaScript disponibili nella libreria JS predefinita vengono eseguite correttamente senza errori.

<u>Risultati effettivi</u>:

Nella console del browser vengono visualizzati gli errori JavaScript:

```
Uncaught TypeError: this._each is not a function
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
