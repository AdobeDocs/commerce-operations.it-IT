---
title: Esempio di utilizzo delle variabili di ambiente
description: Vedi un esempio di come impostare valori condivisi, specifici del sistema e sensibili nel tuo sistema di sviluppo utilizzando le variabili di ambiente.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---


# Esempio di utilizzo delle variabili di ambiente

Questo esempio mostra come impostare valori condivisi, specifici del sistema e sensibili nel sistema di sviluppo, quindi impostare tutti i valori nel sistema di produzione utilizzando una combinazione della configurazione condivisa, `config.php`e variabili di ambiente PHP.

Queste impostazioni di configurazione possono essere condivise tra i sistemi di sviluppo e produzione:

Numero IVA e nome del negozio da **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**

Queste impostazioni di configurazione sono specifiche del sistema o sensibili, come indicato:

- Invia e-mail a (sensibile) da **Negozi** > Impostazioni > **Configurazione** > Generale > **Contatti**
- Dominio e-mail predefinito (specifico del sistema) da **Negozi** > Impostazioni > **Configurazione** > Clienti > **Configurazione del cliente** > **Crea nuove opzioni account**

È possibile utilizzare la stessa procedura per configurare le impostazioni nei riferimenti seguenti:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento a percorsi di configurazione generali](../reference/config-reference-general.md)
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
1. Se necessario, cancella il **Usa predefinito** accanto a **Numero IVA** campo .
1. Immetti un numero nel campo (ad esempio, `12345`).
1. In **Nome archivio** campo , inserisci un valore (come `My Store`).
1. Fai clic su **Salva configurazione**.
1. Utilizza la **Visualizzazione store** elenco per selezionare **Configurazione predefinita** come illustrato nella figura riportata di seguito.

   ![Passa alla configurazione predefinita](../../assets/configuration/split-deploy-default-config.png)

1. Nella navigazione a sinistra, in Generale, fai clic su **Contatti**.
1. Elimina **Usa predefinito** accanto a **Invia e-mail a** campo .
1. Immettere un indirizzo di posta elettronica nel campo .
1. Fai clic su **Salva configurazione**.
1. Nel riquadro a sinistra, fai clic su Clienti > **Configurazione del cliente**.
1. Nel riquadro a destra, espandi **Crea nuove opzioni account**.
1. Elimina **Usa valore di sistema** accanto a **Dominio e-mail predefinito** campo .
1. Immetti un nome di dominio nel campo .
1. Fai clic su **Salva configurazione**.
1. Se richiesto, svuota la cache.

## Passaggio 2: Aggiorna la configurazione

Dopo aver modificato la configurazione nell&#39;amministratore, scrivi la configurazione condivisa in un file come descritto in questa sezione.

{{$include /help/_includes/config-save-config.md}}

Tieni presente che anche se `app/etc/env.php` (la configurazione specifica del sistema) è stata aggiornata e non archiviarla nel controllo del codice sorgente. In seguito, in questa procedura verrà creata la stessa configurazione sul sistema di produzione.

## Passaggio 3: Aggiorna il sistema di compilazione e genera file

Dopo aver eseguito il commit delle modifiche nella configurazione condivisa nel controllo del codice sorgente, è possibile estrarre tali modifiche nel sistema di compilazione, compilare il codice e generare file statici. L&#39;ultimo passo è quello di estrarre queste modifiche al sistema di produzione.

{{$include /help/_includes/config-update-build-system.md}}

## Passaggio 4: Aggiornare il sistema di produzione

L&#39;ultimo passaggio del processo consiste nell&#39;aggiornare il sistema di produzione. È necessario eseguire questa operazione in due parti:

- Aggiornare le impostazioni sensibili e specifiche del sistema
- Aggiornare le impostazioni condivise

### Aggiornare le impostazioni sensibili e specifiche del sistema

Per impostare le impostazioni sensibili e specifiche del sistema utilizzando le variabili di ambiente, è necessario conoscere quanto segue:

- Ambito di applicazione di ciascuna impostazione

   Se hai seguito le istruzioni del passaggio 1, l’ambito per Invia e-mail a è globale (ovvero, l’ambito Configurazione predefinita) e l’ambito per Dominio e-mail predefinito è il sito web.

   Devi conoscere il codice del sito web per impostare il valore di configurazione Default Email Domain. Vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables) per ulteriori informazioni su come trovarlo.

- Percorso di configurazione per ogni impostazione

   Di seguito sono riportati i percorsi di configurazione utilizzati in questo esempio:

   | Nome impostazione | Percorso di configurazione |
   |--------------|--------------|
   | Invia e-mail a | `contact/email/recipient_email` |
   | Dominio e-mail predefinito | `customer/create_account/email_domain` |

   Puoi trovare tutti i percorsi di configurazione sensibili e specifici del sistema in [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md).

#### Convertire i percorsi di configurazione in nomi di variabili

Come discusso in [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables), il formato delle variabili è:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

Il valore di `<SCOPE>` è `CONFIG__DEFAULT__` per ambito globale o `CONFIG__WEBSITES__<WEBSITE CODE>` per ambito del sito web.

Per trovare il valore di `<SYSTEM__VARIABLE__NAME>`, sostituisci ogni `/` nel percorso di configurazione con due caratteri di sottolineatura.

Di seguito sono riportati i nomi delle variabili:

| Nome | Percorso di configurazione | Nome della variabile |
|--------------|--------------|--------------|
| Invia e-mail a | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Dominio e-mail predefinito | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>La tabella precedente ha un codice di esempio per il sito web, `BASE`, per l’impostazione di configurazione Default Email Domain (Dominio e-mail predefinito). Sostituisci `BASE` con il codice del sito web appropriato per il tuo negozio.

#### Impostare le variabili utilizzando le variabili di ambiente

Puoi impostare i valori delle variabili nella `index.php` utilizzando il formato seguente:

```php
$_ENV['VARIABLE'] = 'value';
```

**Per impostare i valori delle variabili**:

1. Accedi al tuo sistema di produzione come proprietario del file system o passa a tale proprietario.
1. Apri `<Commerce root dir>/pub/index.php` in un editor di testo.
1. Accesso remoto `index.php`, imposta i valori per le variabili in modo simile al seguente:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Salva le modifiche in `pub/index.php` e esci dall’editor di testo.
1. Procedi alla sezione successiva.

### Aggiornare le impostazioni condivise

Questa sezione illustra come richiamare tutte le modifiche apportate ai sistemi di sviluppo e di generazione, che aggiornano le impostazioni di configurazione condivise (Nome archivio e Numero IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verifica le impostazioni di configurazione nell’amministratore

Questa sezione illustra come verificare le impostazioni di configurazione nell&#39;amministratore del sistema di produzione.

**Verificare le impostazioni di configurazione**:

1. Accedi all&#39;amministratore del sistema di produzione.
1. Fai clic su **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Utilizza la **Visualizzazione store** nell’angolo in alto a sinistra per passare a un sito Web diverso.

   Le opzioni di configurazione condivise impostate nel sistema di sviluppo vengono visualizzate in modo simile a quanto segue.

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
