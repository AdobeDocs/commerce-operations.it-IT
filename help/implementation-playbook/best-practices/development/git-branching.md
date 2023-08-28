---
title: Best practice per la ramificazione Git
description: Scopri diverse strategie di ramificazione per la gestione del codice sorgente.
feature: Best Practices
role: Developer
source-git-commit: 9b1c3f7ca56cb6baf262bbd4abc732a30a7eb0ed
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Best practice per la ramificazione Git

Il codice sorgente viene sottoposto a più fasi di stabilità durante il processo di sviluppo:

- Sviluppo attivo
- Integrazione del codice iniziale
- Integrazione del codice per la garanzia di qualità (QA)
- Integrazione del codice per il test di accettazione da parte dell’utente finale (UAT)
- Integrazione del codice finale per le versioni di produzione

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce locale

## Gestione delle filiali

Ogni fase di sviluppo deve avere un ramo corrispondente in Git per tenere traccia delle modifiche al codice e facilitare il processo di distribuzione:

- **Ramo attività**: sviluppatori eseguono il commit delle singole modifiche al codice durante l&#39;implementazione di attività specifiche, come funzionalità e correzioni di bug.
- **Ramo di sviluppo**: più sviluppatori uniscono le modifiche dei singoli rami di attività in un unico ramo di sviluppo per test di integrazione automatizzati. Questo ramo viene distribuito in un ambiente di sviluppo.
- **Ramo di controllo qualità**- Quando gli sviluppatori uniscono le modifiche al termine dello sviluppo e il codice ha superato tutti i test di integrazione automatizzata e la revisione del codice. Questo ramo viene distribuito nell’ambiente di controllo qualità per il test di controllo qualità manuale.
- **Ramo stabile/UAT**- Dove il codice viene unito dopo aver superato il test di controllo qualità manuale. Questo ramo viene distribuito in un ambiente UAT per test di accettazione da parte dell’utente.
- **Ramo produzione/rilascio**- Dove il codice viene unito dopo aver passato l&#39;UAT. Questo ramo viene distribuito in produzione per una versione.

>[!TIP]
>
>I progetti Adobe Commerce su infrastrutture cloud contengono rami specifici che corrispondono a ambienti diversi. Consulta la [Flusso di lavoro di un progetto professionale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) e [Flusso di lavoro progetto iniziale](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) nel _Guida a Cloud_.

## Strategie per i rami

È possibile utilizzare diverse strategie di ramificazione. Scegli una strategia che funzioni al meglio per il tuo team di sviluppo e per la complessità del tuo progetto.

Per ulteriori informazioni, consulta le seguenti risorse esterne:

- [Branching dei flussi di lavoro](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Flussi di lavoro distribuiti](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Modelli per la gestione dei rami del codice sorgente](https://martinfowler.com/articles/branching-patterns.html)
- [Un modello di ramificazione Git riuscito](https://nvie.com/posts/a-successful-git-branching-model/)
- [Flusso GitHub](https://docs.github.com/en/get-started/quickstart/github-flow)
- [Flusso GitLab](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
