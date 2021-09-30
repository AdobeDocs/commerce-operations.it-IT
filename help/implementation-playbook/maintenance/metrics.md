---
title: Metriche di supporto
description: Monitora le attività di supporto e manutenzione per l’implementazione di Adobe Commerce utilizzando metriche comuni.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Support metrics

Il diagramma seguente mostra le metriche/KPI tipiche raccolte e riportate per le funzioni L1:

![Diagram showing SLA metrics](../../assets/playbooks/sla-metrics.svg)

Measurement and reporting of L2 services (enhancements and optional services) are similar to development projects. Le prestazioni e il progresso dei team L2 sono misurati da metriche quali velocità, qualità del codice, efficacia dei test e produttività.

| Misurazione delle prestazioni chiave | Unità di misura | Reported Metrics |
|------------------------------|---------------------|------------------------------------------------------------------------------------|
| Velocity | Numero | No. of story points the team were able to deliver for the sprint |
| Efficienza dell&#39;impegno di Sprint | Percentuale | Total no. of Story Points committed Vs Delivered for a Sprint |
| Sprint  Burn down | Number | Grafico (rapporto, traccia il completamento del lavoro durante tutto lo sprint) |
| Qualità del codice | Numbers, Percentage | Complexity, LoC, Violations, Code coverage for the sprint |
| Requirement volatility | Number | Numero di requisiti di modifica/totale # requisiti per lo sprint |
| Defect Density | Percentage | [No. di difetti validi trovati/Totale N. di casi di test eseguiti]*100 per lo sprint |
| Efficacia del test | Percentage | [Valid Defects raised/(Valid Defects raised+ Rejected defects)]*100 for the sprint |
| Produttività | Number (trend) | Punti di storia consegnati per velocità / capacità |