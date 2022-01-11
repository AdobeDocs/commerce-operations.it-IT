---
title: Percorsi di aggiornamento consigliati per il 2022
description: Rivedi le raccomandazioni per la pianificazione dell’aggiornamento di Adobe Commerce o Magento Open Source nel 2022.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Percorsi di aggiornamento consigliati per il 2022

Un’implementazione di e-commerce è un’evoluzione: non è mai realmente completa. La tua azienda deve rimanere un passo avanti rispetto alle tendenze, introducendo le funzionalità e le funzionalità più recenti che mantengono il coinvolgimento dei clienti. Nel tempo, queste funzionalità aggiuntive aumentano l&#39;impatto e la complessità complessiva dell&#39;implementazione.

Alcuni dei fattori generali che influiscono sul livello di impegno necessario per il progetto di aggiornamento includono, tra l’altro:

| Complessità tecnica | Pianificazione e strategia |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Ampiezza delle personalizzazioni | Chiarezza dei requisiti, decisioni vacillanti e ambiguità dell&#39;ambito |
| Numero di estensioni | Frequenza di aggiornamento |
| Numero di integrazioni con terzi (OMS, ERP) | Strategia di test |
| Codifica delle best practice |  |

Di seguito sono riportati i percorsi consigliati da Adobe Commerce per garantire la sicurezza e le prestazioni del sito durante tutto il 2022.

## Aggiornamento dalle versioni 2.3.0-2.3.6 (opzione 1)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option1.png)

È possibile passare da una riga 2.3.x alla versione 2.4.3. Tuttavia, più si va senza un aggiornamento, più lo sforzo è quello di andare direttamente alla versione 2.4.3, in quanto la base di codice ha cambiato di più.

Ad esempio, se utilizzi la versione 2.3.4 rilasciata a gennaio 2020, sei in una versione che ha quasi due anni, quindi la base di codice 2.4.3 rispetto alla versione 2.3.4 è di gran lunga superiore. Questo è il motivo per cui l’Adobe consiglia di eseguire spesso l’aggiornamento, in quanto il livello di impegno tende a essere ancora più elevato se si ritarda l’aggiornamento per un periodo prolungato.

Una volta attivato il 2.4.3, nel Q1 è possibile continuare ad essere sicuri prendendo 2.4.3-p2, il che è un poco sforzo in quanto si tratta di una versione di sicurezza leggera. Poi in Q3, è possibile prendere la patch completa 2.4.5 e un&#39;altra patch di sicurezza della luce per rimanere sicuro in Q4. Questo percorso richiede due aggiornamenti ad alto impegno entro la fine del 2022.

## Aggiornamento dalle versioni 2.3.0-2.3.6 (opzione 2)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option2.png)

In alternativa, puoi effettuare l’aggiornamento da 2.3.x direttamente a 2.4.4 a marzo 2022. A partire dalla versione 2.4.4, è quindi possibile prendere la patch relativa alla sicurezza della luce in Q3, quindi eseguire l’aggiornamento alla versione 2.4.5-p1 in Q4, che include tutti gli aggiornamenti presenti nella versione 2.4.5 e le patch di sicurezza aggiuntive.

Considerazioni chiave per decidere tra queste due opzioni:

| Opzione 1: Aggiornamento a 2.4.3-p1 o a -p2 | Opzione 2: Aggiornamento a 2.4.4 o 2.4.4-p1 |
|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Richiede 2 aggiornamenti significativi prima della fine del 2022 per rimanere sicuri, conformi allo standard PCI e ricevere il supporto qualità | Richiede 1 aggiornamento significativo e 1 aggiornamento a basso sforzo entro la fine del 2022 per rimanere sicuro, conforme allo standard PCI e ricevere il supporto qualità |
| Consente di accedere potenzialmente a una versione supportata compatibile con PCI prima | Potenzialmente si aprirà una finestra più lunga fino a raggiungere una versione supportata compatibile con PCI, poiché la linea 2.3 raggiunge EOL nell&#39;aprile 2022 |
| Considerazione sul tempo: può ritardare il passaggio a una nuova versione PHP fino a più tardi nell&#39;anno (agosto) | Considerazione sul tempo: può iniziare a passare a una nuova versione PHP all&#39;inizio dell&#39;anno (marzo) |

## Aggiornamento da 2.3.7 (opzione 1)

![](../../assets/upgrade-guide/2.3.7-option1.png)

Poiché sei nell’ultima versione 2.3.7, accedi solo alle versioni di sicurezza. Nel primo trimestre del ’22, Adobe rilascia l’ultima versione di 2.3, che è 2.3.7-p3, insieme a un rilascio di sicurezza (2.4.3-p2) e a una versione completa (2.4.4).

La prima opzione è prendere la versione 2.3.7-p3 e ricevere le ultime correzioni di sicurezza. Quindi, in agosto, potresti prendere la versione 2.4.5. Infine, in Q4 è possibile prendere la versione di sicurezza leggera in base alla versione completa 2.4.5. In questo scenario, si dovrebbe essere su una versione EOL per alcuni mesi fino a quando non si prende 2.4.5. Tuttavia, 2.3.x attualmente non offre supporto qualità e si avrebbe le vulnerabilità di sicurezza più recenti patch.

## Aggiornamento da 2.3.7 (opzione 2)

![](../../assets/upgrade-guide/2.3.7-option2.png)

La seconda opzione consiste nel prendere la versione 2.3.7-p3 per ottenere rapidamente le ultime correzioni di sicurezza, poiché le patch di sicurezza per la riga corrente sono poco impegno per l’implementazione, allora puoi avviare l’aggiornamento alla versione 2.4.4.

Ad agosto, potresti quindi prendere 2.4.4-p1, che sarebbe una versione di sicurezza leggera, poi nel secondo trimestre prendere 2.4.5-p1, che include tutti gli aggiornamenti inclusi nella versione 2.4.5 e le ultime versioni di sicurezza.

Puoi anche passare da 2.3.7-p3 a 2.4.4-p1, ma tieni presente che il 2.4.4-p1 è un &quot;pesante incremento&quot; in quanto stai essenzialmente ricevendo tutti gli aggiornamenti inclusi nella versione 2.4.4 e gli aggiornamenti di sicurezza nella versione 2.4.4-p1. Decidere se si desidera avviare questo ascensore più pesante alla linea 2.4.4 in marzo o agosto spetta a voi e al vostro team.

Considerazioni chiave per decidere tra queste due opzioni:

| Opzione 1: Aggiornamento a 2.3.7-p3 e 2.4.5 | Opzione 2: Aggiornamento a 2.3.7-p3 e 2.4.4 |
|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Ricevi prima gli ultimi aggiornamenti di sicurezza con una patch di sicurezza a basso sforzo | Ricevi prima gli ultimi aggiornamenti di sicurezza con una patch di sicurezza a basso sforzo |
| Richiede 1 aggiornamento significativo entro la fine del 2022 per rimanere sicuro, conforme allo standard PCI e ricevere il supporto qualità | Richiede 1 aggiornamento significativo e 1 aggiornamento a basso sforzo entro la fine del 2022 per rimanere sicuro, conforme allo standard PCI e ricevere il supporto qualità |
| Affronta una finestra più lunga fino a quando non arrivi a una versione supportata conforme allo standard PCI poiché la linea 2.3 raggiunge il sistema EOL ad aprile | Considerazione sul tempo: può iniziare a passare a una nuova versione PHP all&#39;inizio dell&#39;anno (marzo) |
| Considerazioni sul tempo: può ritardare l&#39;aggiornamento dello sforzo fino ad agosto | Considerazioni sul tempo: può avviare un aggiornamento dello sforzo più elevato a marzo, quindi effettuare un aggiornamento a medio termine a ottobre |

## Aggiornamento da 2.4.0 a 2.4.2

![](../../assets/upgrade-guide/2.4.0-2.4.2.png)

Poiché hai effettuato l’aggiornamento alla versione 2.4.0-2.4.2, ti consigliamo di effettuare l’aggiornamento alla versione 2.4.4 nel primo trimestre. Questo è uno sforzo relativamente alto a causa dei cambiamenti di rottura in 2.4.4 causati dal passaggio a PHP 8.1. Tuttavia, il resto degli aggiornamenti per l&#39;anno sono sforzi più bassi, quindi è solo necessario condurre un aggiornamento dello sforzo di livello superiore nel 2022.

## Aggiornamento da 2.4.3

![](../../assets/upgrade-guide/2.4.3.png)

Dal momento che siete su 2.4.3, prendere 2.4.3-p2 nel Q1 sarebbe la minima quantità di sforzo. Poi ad agosto, potresti prendere la versione 2.4.5. Infine, in Q4 è possibile prendere la versione di sicurezza leggera in base alla versione completa 2.4.5. In questo scenario, effettui un solo aggiornamento dello sforzo di livello superiore nel 2022.
