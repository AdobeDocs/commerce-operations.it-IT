---
title: 'ACSD-66149: il gestore IPN restituisce *500* per i tipi non supportati'
description: Applica la patch ACSD-66149 per risolvere il problema Adobe Commerce, in cui il gestore IPN non ignora i tipi IPN non supportati o sconosciuti, causando la mancata registrazione del problema, l’interruzione del processo e la restituzione di un errore 500.
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149: il gestore IPN restituisce *500* per i tipi non supportati

La patch ACSD-66149 risolve il problema che causa la restituzione di un errore 500 da parte del gestore IPN (Instant Payment Notification) per i tipi di IPN non supportati o sconosciuti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66149. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il problema è che il gestore IPN restituisce un errore *500* per tipi IPN non supportati o sconosciuti. Si verifica quando Paypal invia l&#39;IPN con alcuni campi mancanti.

<u>Passaggi da riprodurre</u>:

1. Crea un modulo personalizzato che emula tutti i tipi di tipi di IPN sconosciuti da PayPal.
1. Crea almeno un prodotto.
1. Configura PayPal Express con le tue credenziali.
1. Effettua un ordine con Paypal Express.
1. Esegui l&#39;emulatore PayPal.

<u>Risultati previsti</u>:

Il gestore IPN dell&#39;applicazione ignora i tipi IPN errati e non genera *500* errori:

```Order 000000001: Status processing — HTTP 500```

<u>Risultati effettivi</u>:

L&#39;applicazione genera molti errori *500* durante l&#39;elaborazione di IPN non corretti e sporadicamente non elabora alcuni ordini se i campi previsti sono assenti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
