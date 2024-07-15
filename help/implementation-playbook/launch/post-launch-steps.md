---
title: Passaggi per l'avvio di Post
description: Utilizza la nostra checklist post-lancio per garantire un’implementazione fluida del sito Adobe Commerce.
exl-id: 0c3162d9-6475-4b34-9278-e5aea39bd0f9
feature: Deploy
source-git-commit: ce41158f900fad27e3e7b8157f5c64ac988bbabf
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Passaggi per l’avvio di Post

Una volta che il sito web è attivo, queste attività verrebbero eseguite il prima possibile per garantire che il sito sia stato avviato correttamente:

- Abilita lo strumento di monitoraggio dell’operatività (New Relic), attiva i controlli e monitora il sito per garantire che tutti i servizi e l’accesso siano in verde
- Abilita analisi della sicurezza Adobe Commerce periodicamente
- Assegna tag al cluster come live e crea un ticket di supporto per attivare il monitoraggio SLA elevato
- Il CSE (Customer Success Engineer) e il TAM (Technical Account Manager) eseguono le seguenti attività non appena il cutover è completato:
   - Assegnare al cluster i tag SLA elevati per il client Adobe Commerce e creare un ticket di supporto per attivarlo
   - Attiva i **controlli del regno interno** per i nomi di dominio (l&#39;accesso pubblico a PKingdom non è disponibile)
   - Verifica lo stato di monitoraggio e assicurati che tutti gli elementi siano in verde
   - Tieni informati gli interessati sulla durata della garanzia e sui parametri tramite e-mail il giorno di pubblicazione

![Diagramma che mostra la fase 4 del processo di avvio](../../assets/playbooks/launch-steps-4.svg)
