---
title: Best practice per l’aggiornamento dell’elenco di controllo
description: Scopri come creare e utilizzare un elenco di controllo per l’aggiornamento per pianificare la tua strategia di aggiornamento di Adobe Commerce e di Magento Open Source.
role: Leader
feature: Best Practices
feature-set: Commerce
source-git-commit: 5e02f300bb0b5601c653fdea1dd5b85f4e18ed9c
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---


# Best practice per l’aggiornamento dell’elenco di controllo

Utilizza questo elenco di controllo durante le conversazioni annuali e trimestrali con il team eCommerce. Molte aziende lavorano con budget e roadmap annuali. È fondamentale, durante queste discussioni annuali, parlare dello stato di salute, della direzione e della strategia di aggiornamento della piattaforma per l’anno, insieme a come si inserisce negli obiettivi generali e nei KPI dell’azienda. Durante le conversazioni trimestrali, assicurati che il piano annuale creato sia ancora in linea con la situazione corrente o pivot in caso contrario. L’obiettivo di questo elenco di controllo del piano di aggiornamento è aiutarti a pianificare e pianificare gli aggiornamenti di Adobe Commerce per garantire un processo di aggiornamento di successo durante l’anno. Questa checklist deve essere utilizzata dai seguenti tipi di pubblico per la pianificazione annuale e la revisione trimestrale:

- Director / Manager IT
- eCommerce Manager
- Partner/consulente della soluzione

>[!NOTE]
>
>Per una descrizione dettagliata dei passaggi tecnici per il corretto aggiornamento, fare riferimento a [Completare i prerequisiti per l’aggiornamento](../../../upgrade/prepare/prerequisites.md) nella documentazione per gli utenti.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Obiettivi

▢ Rivedi i KPI correnti e apporta le modifiche necessarie.

## Estensioni e personalizzazioni

▢ Esamina tutte le estensioni e le personalizzazioni correnti e assicurati che siano ancora necessarie in base ai requisiti aziendali.

▢ Valuta la possibilità di sostituire tutte le estensioni che non hanno una buona tradizione di aggiornamento con le versioni di Adobe Commerce.

## Team

▢ Assicurati di disporre del team giusto con le certificazioni e le competenze Adobe Commerce appropriate.

## Budget e tempistica

▢ Utilizzare Adobe Commerce [pianificazione delle versioni](../../../release/schedule.md) per pianificare il prossimo aggiornamento e prepararsi in anticipo.

▢ Discuti quale versione pensi di adottare (completa o di sola sicurezza) in base alle esigenze previste.

▢ Accantonare un budget e la capacità del team per l&#39;aggiornamento.

## Integrazioni di terze parti

▢ Rivedi le integrazioni di terze parti Adobe Commerce correnti e le relative finestre di manutenzione per l’anno, e prendi in considerazione l’allineamento del lavoro di aggiornamento con la pianificazione della manutenzione.

## Pianificazione dell&#39;ambito e della distribuzione

▢ Attività di accesso anticipato

- Partecipazione del partner [Beta](../../../release/beta.md)
- Revisione delle note sulla versione beta.

▢ Accordo su budget, tempistica, ambito.

▢ Esegui il [Upgrade Compatibility Tool](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Valuta l&#39;utilizzo dell&#39;aggiornamento per risolvere i problemi identificati da [Strumento di analisi a livello di sito](../../../tools/site-wide-analysis-tool/intro.md).

▢ Documento dipendenze ed eventuali modifiche tecniche dello stack richieste, ad esempio le versioni PHP o Elastic Search.

▢ Raccogliere il team di progetto con le certificazioni Adobe Commerce.

▢ Creare un piano di comunicazione per le parti interessate.

▢ Finestra di manutenzione del piano se si prevedono tempi di inattività.

▢ Rivedere e approvare la strategia di test; considerare l’utilizzo di Adobe Commerce [framework di test](https://developer.adobe.com/commerce/testing/) o una suite di automazione di terze parti.

▢ Verifica che tutte le estensioni e personalizzazioni siano compatibili.

▢ Rivedi e aggiorna il playbook successivo all’avvio; da utilizzare se vengono rilevati problemi durante o dopo l’aggiornamento.

## Post-implementazione

▢ Monitora il sito per individuare eventuali problemi: prestazioni, elaborazione degli ordini, analisi e altro ancora.

▢ Eseguire un’Adobe Commerce [analisi della sicurezza](https://account.magento.com/scanner/dashboard/) o altre analisi di terze parti e analisi di potenziali vulnerabilità di sicurezza.

▢ Esegui una retrospettiva con tutte le parti interessate e documenta cosa è andato bene e cosa non è andato e come migliorare.

▢ Modifica il piano per il prossimo aggiornamento tenendo conto delle lezioni apprese.
