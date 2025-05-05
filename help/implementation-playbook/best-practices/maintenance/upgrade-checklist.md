---
title: Best practice per l’aggiornamento dell’elenco di controllo
description: Scopri come creare e utilizzare un elenco di controllo per l’aggiornamento per pianificare la tua strategia di aggiornamento di Adobe Commerce.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Best practice per l’aggiornamento dell’elenco di controllo

Utilizza questo elenco di controllo durante le conversazioni annuali e trimestrali con il team eCommerce. Molte aziende lavorano con budget e roadmap annuali. È fondamentale, durante queste discussioni annuali, parlare dello stato di salute, della direzione e della strategia di aggiornamento della piattaforma per l’anno, insieme a come si inserisce negli obiettivi generali e nei KPI dell’azienda. Durante le conversazioni trimestrali, assicurati che il piano annuale creato sia ancora in linea con la situazione corrente o pivot in caso contrario. L’obiettivo di questo elenco di controllo del piano di aggiornamento è aiutarti a pianificare e pianificare gli aggiornamenti di Adobe Commerce per garantire un processo di aggiornamento di successo durante l’anno. Questa checklist deve essere utilizzata dai seguenti tipi di pubblico per la pianificazione annuale e la revisione trimestrale:

- Director / Manager IT
- eCommerce Manager
- Partner/consulente della soluzione

>[!NOTE]
>
>Per una descrizione dettagliata dei passaggi tecnici per eseguire l&#39;aggiornamento, consulta [Prerequisiti per l&#39;aggiornamento completi](../../../upgrade/prepare/prerequisites.md) nella documentazione utente.

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

▢ Utilizza la [pianificazione del rilascio](../../../release/schedule.md) di Adobe Commerce per pianificare il tuo prossimo aggiornamento e prepararti in anticipo.

▢ Discuti quale versione pensi di adottare (completa o di sola sicurezza) in base alle esigenze previste.

▢ Accantonare un budget e la capacità del team per l&#39;aggiornamento.

## Integrazioni di terze parti

▢ Rivedi le integrazioni di terze parti Adobe Commerce correnti e le relative finestre di manutenzione per l’anno, e prendi in considerazione l’allineamento del lavoro di aggiornamento con la pianificazione della manutenzione.

## Pianificazione dell&#39;ambito e della distribuzione

▢ Attività di accesso anticipato

- Il partner partecipa a [Beta](../../../release/beta.md)
- Revisione delle note sulla versione di Beta.

▢ Accordo su budget, tempistica, ambito.

▢ Eseguire lo strumento di compatibilità per l&#39;aggiornamento [&#128279;](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Considerare l&#39;utilizzo dell&#39;aggiornamento per risolvere i problemi identificati dallo [strumento di analisi a livello di sito](../../../tools/site-wide-analysis-tool/intro.md).

▢ Documento dipendenze ed eventuali modifiche tecniche dello stack richieste, ad esempio le versioni PHP o Elastic Search.

▢ Raccogliere il team di progetto con le certificazioni Adobe Commerce.

▢ Creare un piano di comunicazione per le parti interessate.

▢ Finestra di manutenzione del piano se si prevedono tempi di inattività.

▢ Rivedi e approva la strategia di test; prova a utilizzare Adobe Commerce [test framework](https://developer.adobe.com/commerce/testing/) o una suite di automazione di terze parti.

▢ Verifica che tutte le estensioni e personalizzazioni siano compatibili.

▢ Rivedi e aggiorna il playbook successivo all’avvio; da utilizzare se vengono rilevati problemi durante o dopo l’aggiornamento.

## Distribuzione Post

▢ Monitora il sito per individuare eventuali problemi: prestazioni, elaborazione degli ordini, analisi e altro ancora.

▢ Eseguire un&#39;analisi della protezione di Adobe Commerce [&#128279;](https://account.magento.com/scanner/dashboard/) o un&#39;altra analisi di terze parti ed esaminare potenziali vulnerabilità di protezione.

▢ Esegui una retrospettiva con tutte le parti interessate e documenta cosa è andato bene e cosa non è andato e come migliorare.

▢ Modifica il piano per il prossimo aggiornamento tenendo conto delle lezioni apprese.
