---
title: Esempio utilizzando i comandi CLI
description: Vedi un esempio di come impostare valori condivisi, specifici del sistema e sensibili nel tuo sistema di sviluppo utilizzando la riga di comando.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1019'
ht-degree: 0%

---


# Esempio utilizzando i comandi CLI

Questo esempio mostra come impostare valori condivisi, specifici del sistema e sensibili nel sistema di sviluppo, quindi distribuire tali valori nel sistema di produzione.
Questo viene fatto utilizzando una combinazione di configurazioni condivise, il `config.php` file e comando Commerce CLI.

In questo esempio vengono utilizzate le seguenti impostazioni di configurazione:

- **Numero iva** e **Nome archivio** per le impostazioni di configurazione condivise.

   Questi sono disponibili in **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.

- **Invia e-mail a** per il valore di configurazione sensibile.

   Questo è disponibile in **Negozi** > Impostazioni > **Configurazione** > Generale > **Contatti**.

- **Dominio e-mail predefinito** per il valore di configurazione specifico del sistema.

   Questo è disponibile in **Negozi** > Impostazioni > **Configurazione** > Clienti > **Configurazione del cliente** > **Crea nuove opzioni account**.

È possibile utilizzare la stessa procedura mostrata in questo esempio per configurare le impostazioni nei riferimenti seguenti:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento ad altri percorsi di configurazione](../reference/config-reference-general.md)
- [Riferimento per i percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Prima di iniziare

Prima di iniziare, impostare le autorizzazioni e la proprietà del file system come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/prerequisites.md).

## Ipotesi

Questo argomento fornisce un esempio di modifica della configurazione del sistema di produzione. Se lo desideri, puoi scegliere diverse opzioni di configurazione.

Ai fini di questo esempio, si assume quanto segue:

- Utilizzare il controllo sorgente Git
- Il sistema di sviluppo è disponibile in un archivio remoto Git denominato `mconfig`
- Il tuo ramo di lavoro Git si chiama `m2.2_deploy`

## Passaggio 1: Impostare la configurazione nel sistema di sviluppo

Per impostare le impostazioni internazionali e le unità di peso predefinite nel sistema di sviluppo:

1. Accedi all&#39;amministratore.
1. Fai clic su **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Se sono disponibili più siti web, utilizza le **Visualizzazione store** nell’angolo in alto a sinistra per passare a un sito Web diverso, come illustrato nella figura riportata di seguito.

   ![Cambia siti web](../../assets/configuration/split-deploy-switch-website.png)

1. Nel riquadro a destra, espandi **Informazioni sul negozio**.
1. Se necessario, cancella il **Usa predefinito** accanto a **Numero IVA** e **Nome archivio** campi.
1. Immetti un numero nel campo (ad esempio, `12345`).
1. In **Nome archivio** campo , inserisci un valore (come `My Store`).
1. Fai clic su **Salva configurazione**.
1. Nella navigazione a sinistra, in Generale, fai clic su **Contatti**.
1. Nel riquadro a destra, espandi **Opzioni e-mail**.
1. Se necessario, cancella il **Usa predefinito** accanto a **Invia e-mail a** campo .
1. Immettere un indirizzo di posta elettronica nel campo .
1. Fai clic su **Salva configurazione**.
1. Utilizza la **Visualizzazione store** elenco per selezionare **Configurazione predefinita** come illustrato nella figura riportata di seguito.

   ![Passa alla configurazione predefinita](../../assets/configuration/split-deploy-default-config.png)

1. Nel riquadro a sinistra, fai clic su Clienti > **Configurazione del cliente**.
1. Nel riquadro a destra, espandi **Crea nuove opzioni account**.
1. Se necessario, cancella il **Usa valore di sistema** accanto a **Dominio e-mail predefinito** campo .
1. Immetti un nome di dominio nel campo .
1. Fai clic su **Salva configurazione**.
1. Se richiesto, svuota la cache.

## Passaggio 2: Aggiorna la configurazione

Dopo aver modificato la configurazione nell&#39;amministratore, scrivi la configurazione condivisa in un file come segue:

{{$include /help/_includes/config-save-config.md}}

Anche se `app/etc/env.php` (la configurazione specifica del sistema) è stata aggiornata e non archiviarla nel controllo del codice sorgente.
In seguito, in questa procedura verrà creata la stessa configurazione sul sistema di produzione.

## Passaggio 3: Aggiorna il sistema di compilazione e genera file

Dopo aver eseguito il commit delle modifiche nella configurazione condivisa nel controllo del codice sorgente, è possibile estrarre tali modifiche nel sistema di compilazione, compilare il codice e generare file statici.

{{$include /help/_includes/config-update-build-system.md}}

## Passaggio 4: Aggiornare il sistema di produzione

L&#39;ultimo passaggio del processo consiste nell&#39;aggiornare il sistema di produzione. È necessario eseguire questa operazione in due parti:

- Aggiornare le impostazioni sensibili e specifiche del sistema
- Aggiornare le impostazioni condivise

### Aggiornare le impostazioni sensibili e specifiche del sistema

Per impostare le impostazioni sensibili e specifiche del sistema utilizzando le variabili di ambiente, è necessario conoscere quanto segue:

- Ambito di applicazione di ciascuna impostazione

   Se hai seguito le istruzioni del passaggio 1, l&#39;ambito per **Invia e-mail a** è un sito web e ha la possibilità di **Dominio e-mail predefinito** è globale (ovvero l&#39;ambito Configurazione predefinita).

   È necessario il codice del sito web per impostare il **Invia e-mail a** valore di configurazione.

   Per ulteriori informazioni su come trovare questo valore, consulta: [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables).

- Percorsi di configurazione per le impostazioni utilizzate in questo esempio:

   | Nome impostazione | Percorso di configurazione |
   | -------------------- | -------------------------------------- |
   | Invia e-mail a | `contact/email/recipient_email` |
   | Dominio e-mail predefinito | `customer/create_account/email_domain` |

   Per tutti i percorsi di configurazione sensibili e specifici del sistema, vedi: [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md).

### Impostare le variabili utilizzando i comandi CLI

Utilizza i seguenti comandi CLI per impostare le impostazioni di configurazione specifiche e sensibili del sistema:

- `magento config:set` per le impostazioni specifiche del sistema
- `magento config:sensitive:set` per le impostazioni sensibili

Impostazione dell&#39;impostazione specifica del sistema **Dominio e-mail predefinito**, che si trova nell&#39;ambito predefinito, utilizza il comando seguente:

```bash
bin/magento config:set customer/create_account/email_domain <email domain>
```

Non è necessario utilizzare l&#39;ambito nel comando perché è l&#39;ambito predefinito.

Per impostare valori per **Invia e-mail a**, tuttavia, devi conoscere il tipo di ambito (`website`) e il codice dell&#39;ambito, che è probabilmente diverso in ogni sito.

Esempio:

```unix
bin/magento config:sensitive:set contact/email/recipient_email --scope=website --scope-code=<website code> <email address>
```

### Aggiornare le impostazioni condivise

Questa sezione illustra come richiamare tutte le modifiche apportate ai sistemi di sviluppo e di generazione in un ambiente di produzione, che aggiorna le impostazioni di configurazione condivise (Nome archivio e Numero IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifica le impostazioni di configurazione nell’amministratore

Per verificare le impostazioni di configurazione:

1. Accedi all&#39;amministratore del sistema di produzione.
1. Fai clic su **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Utilizza la **Visualizzazione store** nell’angolo in alto a sinistra per passare a un sito Web diverso.

   Le opzioni di configurazione condivise impostate nel sistema di sviluppo vengono visualizzate in modo simile alle seguenti.

   ![Controllare le impostazioni nel sistema di produzione](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >La **Nome archivio** Il campo è modificabile nell&#39;ambito del sito web, ma se si passa all&#39;ambito Configurazione predefinita, non è modificabile. Questo è il risultato della modalità di impostazione delle opzioni nel sistema di sviluppo. Il valore di **Numero IVA** non è modificabile nell&#39;ambito del sito web.

1. Se non lo hai già fatto, passa all&#39;ambito Configurazione predefinita.
1. Nella navigazione a sinistra, in Generale, fai clic su **Contatti**.

   La **Invia e-mail a** campo non modificabile, come illustrato nella figura riportata di seguito. Si tratta di un’impostazione sensibile.

   ![Controllare le impostazioni nel sistema di produzione](../../assets/configuration/split-deploy-verify-contacts.png)

1. Nel riquadro a sinistra, fai clic su Clienti > **Configurazione del cliente**.
1. Nel riquadro a destra, espandi **Crea nuove opzioni account**.

   Il valore del **Dominio e-mail predefinito** viene visualizzato come segue. Si tratta di un’impostazione specifica del sistema.

   ![Controllare le impostazioni nel sistema di produzione](../../assets/configuration/split-default-domain.png)
