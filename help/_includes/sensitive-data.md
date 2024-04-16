---
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '64'
ht-degree: 1%

---
# Dati sensibili

Adobe Commerce utilizza la tua chiave di crittografia per crittografare quanto segue:

* Informazioni carta di credito
* Nomi utente e password specificati nella configurazione amministratore (ad esempio, accessi ai gateway di pagamento)
* Valori CAPTCHA inviati tramite la rete

Adobe Commerce sì *non* crittografare:

* Password e nomi utente amministrativi e cliente (con hash)
* Indirizzo
* Numero di telefono
* Altri tipi di informazioni personali identificabili, ad eccezione dei numeri di carta di credito
