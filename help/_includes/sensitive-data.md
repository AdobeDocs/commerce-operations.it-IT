---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Dati sensibili

Adobe Commerce e Magenti Open Source utilizzano la chiave di crittografia per crittografare quanto segue:

* Informazioni carta di credito
* Nomi utente e password specificati nella configurazione amministratore (ad esempio, accessi ai gateway di pagamento)
* Valori CAPTCHA inviati tramite la rete

Adobe Commerce e Magenti Open Source fanno *non* crittografare:

* Password e nomi utente amministrativi e cliente (con hash)
* Indirizzo
* Numero di telefono
* Altri tipi di informazioni personali identificabili, ad eccezione dei numeri di carta di credito
