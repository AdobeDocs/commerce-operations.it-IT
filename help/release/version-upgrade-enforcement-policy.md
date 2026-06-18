---
title: Criterio di applicazione aggiornamento versione cloud
description: 'Scopri l’applicazione dell’aggiornamento della versione per Adobe Commerce su Cloud: perché Adobe applica aggiornamenti, date di applicazione, disattivazione e azioni richieste. Consulta la sezione sui criteri del ciclo di vita per le disposizioni transitorie e i percorsi di migrazione.'
nudge: false
source-git-commit: 797f067de451c8b1b4d735e82de66a3fd9b56563
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Criterio di applicazione dell’aggiornamento della versione per Adobe Commerce su Cloud

Quando il supporto regolare e il supporto esteso terminano per una versione di Adobe Commerce, Adobe si riserva il diritto di disattivare Adobe Commerce su ambienti Cloud che eseguono ancora tale versione non supportata. L’applicazione dell’aggiornamento della versione si applica solo agli ambienti Adobe Commerce on Cloud; i clienti on-premise gestiscono la propria infrastruttura.

Devi passare a una versione di Adobe Commerce supportata o eseguire la migrazione a [!DNL Adobe Commerce as a Cloud Service] prima della data di [fine del supporto esteso](lifecycle-policy.md#end-of-support-dates) pubblicata per la riga di rilascio.

Le sezioni seguenti spiegano perché Adobe applica gli aggiornamenti, come vengono calcolate le date di applicazione e cosa accade alla data di applicazione. Per le date di imposizione specifiche della versione, vedere la tabella [Date di fine supporto](lifecycle-policy.md#end-of-support-dates) nei criteri del ciclo di vita.

>[!NOTE]
>
>Questo argomento riguarda solo l’applicazione dell’aggiornamento cloud. Per le definizioni dei livelli di supporto, la tabella [fine delle date di supporto](lifecycle-policy.md#end-of-support-dates), [disposizioni transitorie per la sola protezione](lifecycle-policy.md#security-only-transitional-period), [dipendenze software di terze parti](lifecycle-policy.md#platform-dependencies), [fine del ciclo di vita PHP e conformità PCI](lifecycle-policy.md#php-end-of-life-and-pci-compliance) e [opzioni di aggiornamento e migrazione](lifecycle-policy.md#upgrade-and-migration-options), vedere [criteri del ciclo di vita](lifecycle-policy.md). Oltre a eseguire l’aggiornamento a una versione di Adobe Commerce supportata, Adobe richiede anche di mantenere le dipendenze software di terze parti dalle versioni supportate attivamente.

## Perché Adobe sta introducendo questo criterio

Adobe è responsabile della sicurezza e della conformità dell’infrastruttura della piattaforma ospitata su cui operano i clienti Adobe Commerce on Cloud. Ciò include l&#39;aggiornamento di tutte le dipendenze software sottostanti, l&#39;applicazione di patch di sicurezza e il rispetto degli standard di conformità, ad esempio PCI, su cui i clienti si affidano.

Quando il supporto di sicurezza per le dipendenze software sottostanti viene ufficialmente interrotto dai fornitori, Adobe non è più in grado di fornire il livello richiesto di copertura di sicurezza e supporto della piattaforma. Continuare a gestire i negozi su infrastrutture non supportate espone clienti, acquirenti e Adobe a rischi inaccettabili. Adobe sta pertanto introducendo un criterio formale di applicazione dell’aggiornamento della versione che definisce quando verranno disattivate le versioni di Adobe Commerce su ambienti Cloud in esecuzione su Commerce non supportate.

## Calcolo delle date di applicazione dell’aggiornamento

Per ogni riga di rilascio di Adobe Commerce, la data di applicazione dell’aggiornamento viene calcolata come segue:

**Data di applicazione dell&#39;aggiornamento** = Data di disponibilità generale + 3 anni di supporto regolare + fino a 1 anno di supporto esteso

Il supporto esteso viene annunciato verso la fine del supporto regolare per ogni linea di rilascio.

## Che cosa accade alla data di applicazione dell’aggiornamento della versione

Alla data pubblicata di applicazione dell’aggiornamento, Adobe interromperà la manutenzione di tutti gli ambienti Adobe Commerce su Cloud che ancora eseguono la versione interessata e si riserva il diritto di disattivarli. Riceverai notifiche prioritarie in corrispondenza delle fasi cardine principali che precedono la data di applicazione dell’aggiornamento della versione. Adobe fornirà una finestra di esportazione dei dati prima della disattivazione dell’ambiente, in modo da poter recuperare i dati.

La prima data di applicazione in base a questo criterio è il **1 giugno 2027**, per le righe della versione che raggiungono la fine del supporto esteso prima di tale data. Vedere la tabella [Date di fine supporto](lifecycle-policy.md#end-of-support-dates) per le date di imposizione specifiche per le versioni.
