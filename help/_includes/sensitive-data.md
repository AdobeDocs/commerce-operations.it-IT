---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '72'
ht-degree: 0%

---
# Dati sensibili

Adobe Commerce e Magenti Open Source utilizzano la chiave di crittografia per crittografare quanto segue:

* Informazioni sulla carta di credito
* Nomi utente e password specificati nella configurazione Amministratore (ad esempio, accessi ai gateway di pagamento)
* Valori CAPTCHA inviati sulla rete

Adobe Commerce e Magenti Open Source *not* encrypt:

* Password e nomi utente amministrativi e clienti (queste password sono crittografate)
* Indirizzo
* Numero di telefono
* Altri tipi di informazioni personali identificabili ad eccezione dei numeri di carta di credito
