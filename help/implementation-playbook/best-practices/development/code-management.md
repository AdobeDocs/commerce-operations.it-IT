---
title: Best practice per la gestione del codice
description: Scopri le best practice per la gestione del codice nella fase di sviluppo dei progetti Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 0bff4c7a-1082-4b3e-b19c-bc8ad529b131
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 0%

---

# Best practice per la gestione del codice per Adobe Commerce

Questo argomento è progettato per aiutarti a decidere se utilizzare Git o Composer per distribuire il codice personalizzato, tenendo in considerazione la gestione delle versioni, la complessità del codice e la gestione delle dipendenze.

>[!NOTE]
>
>Queste best practice sono più adatte per le migrazioni e le implementazioni, meno per lo sviluppo di singoli moduli.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Definizioni

{{$include /help/_includes/gra-definitions.md}}

## Quando utilizzare Git o Composer

<table>
<thead>
  <tr>
    <th></th>
    <th>Codice gestito principalmente tramite Git</th>
    <th>Codice gestito principalmente tramite Composer</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Quando utilizzare per una configurazione a istanza singola</td>
    <td>
      <ul>
        <li><strong>Approccio standard per la gestione del codice per una configurazione a istanza singola</strong></li>
        <li>Quando la base di codice non farà parte di un GRA multi-brand in futuro</li>
        <li>Quando tutti i brand vengono eseguiti su una singola istanza come siti web</li>
      </ul>
    </td>
    <td>
      <ul>
        <li>Quando la base di codice può o diventerà parte di una configurazione con più istanze in futuro</li>
      </ul>
    </td>
  </tr>
  <tr>
    <td>Quando utilizzare per una configurazione con più istanze</td>
    <td>
      <ul>
        <li>Quando quasi tutti i moduli sono interconnessi (scelta non consigliata)</li>
        <li>Quando il codice viene gestito da un team che non ha familiarità con Composer</li>
      </ul>
    </td>
    <td>
      <ul>
        <li><strong>Approccio standard per la gestione del codice per una configurazione con più istanze</strong></li>
        <li>Quando Adobe gestisce la base di codice o il team di manutenzione ha familiarità con Composer</li>
      </ul>
    </td>
  </tr>
</tbody>
</table>

## Matrice di funzioni

| Funzionalità | Git | Compositore |
|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Archivio del codice principale | Tutto il codice risiede in un singolo archivio Git o in alcuni archivi Git | Tutto il codice risiede nei pacchetti di un repository Composer<br>Ogni singolo pacchetto Composer è rappresentato da un repository Git |
| Posizione codice | Lo sviluppo avviene nella directory `app/` | Lo sviluppo avviene nella directory `vendor/` |
| Gestione degli aggiornamenti di base | Adobe Commerce Core viene installato e aggiornato tramite Composer, il risultato è confermato in Git | Adobe Commerce Core viene installato e aggiornato tramite Composer; il risultato viene confermato in Git |
| Gestione dei moduli di terze parti | I moduli di terze parti vengono installati in `vendor/` se sono installati tramite il marketplace o packagist.org. Altrimenti sono installati in `app/` | Tutti i moduli di terze parti sono installati nella directory `vendor/` |
| Versioni | Rilascio caratterizzato da `git merge` e `git pull` o `git checkout` comandi | Rilascio caratterizzato da `composer update` e `git pull` o `git checkout` comandi |
| Numero di archivi Git | Pochi | Molti |
| Complessità dello sviluppo | Semplice | Complesso |
| Complessità della richiesta pull | Semplice | Complesso |
| Complessità della revisione del codice | Semplice | Semplice |
| Complessità dell’aggiornamento dell’ambiente di sviluppo/QA/UAT | Semplice | Complesso |
| Supporto GRA | ![Icona Sì](../../../assets/yes.svg) | ![Icona Sì](../../../assets/yes.svg) |
| I moduli possono installare automaticamente librerie esterne | ![Nessuna icona](../../../assets/no.svg) | ![Icona Sì](../../../assets/yes.svg) |
| Flessibilità nella composizione del GRA | ![Nessuna icona](../../../assets/no.svg) | ![Icona Sì](../../../assets/yes.svg) |
| Gestione delle dipendenze dei moduli | ![Icona Sì](../../../assets/yes.svg) Solo tramite `module.xml`, funzionalità limitata | ![Icona Sì](../../../assets/yes.svg) Gestione completa delle dipendenze tramite `composer.json` |
| Controllo delle versioni dei moduli | ![Icona Sì](../../../assets/yes.svg) È possibile definire una versione, ma non installare una versione specifica | ![Icona Sì](../../../assets/yes.svg) Supporto versione completa |
| Servizi a pagamento necessari | Archivio Git | Archivio Git, Packagist privato (± €600 all&#39;anno) |
| È possibile integrare Bitbucket con Jira | ![Icona Sì](../../../assets/yes.svg) | ![Icona Sì](../../../assets/yes.svg) |
| Modifiche al codice immediatamente disponibili per l’installazione | ![Icona Sì](../../../assets/yes.svg) | ![Icona Sì](../../../assets/yes.svg) |

## Soluzioni da evitare

1. **Compositore combinato e `app/code` per i moduli**

   Comporta tutti gli svantaggi di entrambi gli stili di gestione del codice combinati nel progetto. Aggiunge inutili complessità, instabilità e mancanza di flessibilità.

   Ad esempio:
   - Spiega al team di sviluppo i flussi di lavoro Git e Compositore (anziché uno solo).
   - Installare moduli incompatibili in `app/code` poiché non è disponibile alcuna risorsa per impedire che ciò accada.
   - Lo spostamento di un modulo da `app/code` a Compositore (o viceversa) è complicato, soprattutto con lo sviluppo in corso.

1. **Gestione pacchetti Satis**

   Private Packagist costa ± €600 all&#39;anno. Questo costo è per l&#39;intero GRA combinato, non per marchio. Non cercare di evitare questi costi utilizzando la soluzione gratuita Satis. Satis non aggiorna automaticamente i pacchetti ogni volta che invii commit a Git. Anche Satis non ha un&#39;autorizzazione incorporata. Per eseguire Satis, è necessario gestire un server Web. Alla fine si finisce per spendere una moltitudine della tassa di abbonamento a Private Packagist mantenendo Satis.

1. **Inizia con Git, quindi passa a Compositore**

   Scegli un approccio di gestione del codice all’inizio del progetto. Il passaggio da Git a Compositore o viceversa, con lo sviluppo in corso, è complicato e potrebbe portare alla perdita di codice e/o di cronologia delle revisioni.

<!-- Last updated from includes: 2023-08-23 15:56:59 -->
