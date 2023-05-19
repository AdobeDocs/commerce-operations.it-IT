---
title: Esempio di utilizzo di una configurazione condivisa
description: Vedi un esempio di come modificare le impostazioni in un sistema di sviluppo con un file di configurazione condiviso.
exl-id: c980ec01-ca2d-43db-b68d-8e9435e07e6a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# Esempio di utilizzo di una configurazione condivisa

Questo esempio mostra come modificare le seguenti impostazioni nel sistema di sviluppo, aggiornare il file di configurazione condiviso, `config.php`, nel sistema di build e implementare le stesse impostazioni nel sistema di produzione:

- Fuso orario
- Unità di peso

Queste impostazioni sono disponibili nella sezione Amministrazione di **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.

È possibile utilizzare la stessa procedura per configurare qualsiasi impostazione non sensibile e non specifica del sistema nei seguenti riferimenti:

- [Altri percorsi di configurazione di riferimento](../reference/config-reference-general.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Prima di iniziare

Prima di iniziare, imposta le autorizzazioni e la proprietà del file system come descritto in [Prerequisiti per i sistemi di sviluppo, generazione e produzione](../deployment/prerequisites.md).

## Presupposti

Questo argomento fornisce un esempio di modifica della configurazione del sistema di produzione. Se lo desideri, puoi scegliere diverse opzioni di configurazione.

Ai fini del presente esempio, si assume quanto segue:

- Usa il controllo del codice sorgente Git
- Il sistema di sviluppo è disponibile in un archivio remoto Git denominato `mconfig`
- Il ramo di lavoro Git è denominato `m2.2_deploy`

## Passaggio 1: impostare la configurazione nel sistema di sviluppo

Per impostare il fuso orario e le unità di peso nel sistema di sviluppo:

1. Accedi all’amministratore.
1. Clic **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Nel riquadro di destra, espandere **Opzioni internazionali**.

   Nella figura seguente viene illustrato un esempio.

   ![Impostare le opzioni internazionali nel sistema di sviluppo](../../assets/configuration/split-deploy-set-locale.png)

1. Dalla sezione **Fuso orario** , fare clic su **GMT+00:00 (UTC)**.
1. Cancella **Usa valore di sistema** accanto alla casella di controllo **Unità di peso** campo.
1. Dalla sezione **Unità di peso** , fare clic su **kg**.
1. Clic **Salva configurazione**.
1. Se richiesto, svuotare la cache.

## Passaggio 2: aggiornare la configurazione condivisa

Genera il file di configurazione condiviso, `app/etc/config.php`, nel sistema di sviluppo e trasferirlo utilizzando il controllo del codice sorgente nel sistema di build, come descritto in questa sezione.

{{$include /help/_includes/config-save-config.md}}

## Passaggio 3: aggiornare il sistema di generazione e generare i file

Dopo aver confermato le modifiche apportate alla configurazione condivisa nel controllo del codice sorgente, è possibile richiamarle nel sistema di generazione, compilare il codice e generare file statici. L’ultimo passaggio consiste nel richiamare tali modifiche nel sistema di produzione. Di conseguenza, la configurazione del sistema di produzione corrisponderà a quella del sistema di sviluppo.

{{$include /help/_includes/config-update-build-system.md}}

## Passaggio 4: aggiornare il sistema di produzione

L’ultimo passaggio del processo consiste nell’aggiornare il sistema di produzione dal controllo del codice sorgente. In questo modo vengono richiamate tutte le modifiche apportate ai sistemi di sviluppo e creazione, il che significa che il sistema di produzione è completamente aggiornato.

{{$include /help/_includes/config-update-prod-system.md}}

### Verificare le modifiche in Admin

**Per verificare che queste impostazioni non siano modificabili in Amministrazione**:

1. Accedi all’amministratore.
1. Clic **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Nel riquadro di destra, espandere **Opzioni internazionali**.

   Le opzioni appena impostate vengono visualizzate come segue:

   ![Opzioni di configurazione non modificabili in Amministrazione](../../assets/configuration/split-deploy-not-editable.png)

>[!INFO]
>
>Per modificare un’impostazione bloccata in Admin, utilizza [`magento config:set --lock` comando](../cli/set-configuration-values.md).
