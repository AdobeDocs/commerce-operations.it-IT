---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Hotfix inclusi nelle patch di sicurezza di ottobre (eccetto 2.4.4)

Questa versione include un hotfix per risolvere un problema relativo al gateway di pagamento di Braintree.

Il sistema ora include i campi necessari per soddisfare i requisiti del mandato VISA 3DS quando si utilizza Braintree come gateway di pagamento. In questo modo tutte le operazioni sono conformi alle più recenti norme di sicurezza stabilite da VISA. In precedenza, questi campi supplementari non erano inclusi nelle informazioni di pagamento inviate, il che avrebbe potuto comportare il mancato rispetto dei nuovi requisiti in materia di visti.

<!--
BUNDLE-3360
-->