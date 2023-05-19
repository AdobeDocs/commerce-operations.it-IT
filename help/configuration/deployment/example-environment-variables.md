---
title: Esempio di utilizzo di variabili di ambiente
description: Vedi un esempio di come impostare valori condivisi, specifici del sistema e sensibili nel sistema di sviluppo utilizzando variabili di ambiente.
exl-id: 98438674-e7f8-4143-9a76-3cc8bf0a73dc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1085'
ht-degree: 0%

---

# Esempio di utilizzo di variabili di ambiente

Questo esempio mostra come impostare valori condivisi, specifici del sistema e sensibili nel sistema di sviluppo, quindi impostare tutti i valori nel sistema di produzione utilizzando una combinazione della configurazione condivisa, `config.php`e PHP.

Queste impostazioni di configurazione possono essere condivise tra i sistemi di sviluppo e produzione:

Partita IVA e nome negozio da **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**

Queste impostazioni di configurazione sono specifiche del sistema o sensibili, come indicato:

- Invia e-mail a (sensibile) da **Negozi** > Impostazioni > **Configurazione** > Generale > **Contatti**
- Dominio e-mail predefinito (specifico per il sistema) da **Negozi** > Impostazioni > **Configurazione** > Clienti > **Configurazione cliente** > **Crea nuove opzioni account**

È possibile utilizzare la stessa procedura per configurare le impostazioni nei seguenti riferimenti:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento generale ai percorsi di configurazione](../reference/config-reference-general.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

## Prima di iniziare

Prima di iniziare, imposta le autorizzazioni e la proprietà del file system come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/prerequisites.md).

## Presupposti

Questo argomento fornisce un esempio di modifica della configurazione del sistema di produzione. Se lo desideri, puoi scegliere diverse opzioni di configurazione.

Ai fini del presente esempio, si assume quanto segue:

- Usa il controllo del codice sorgente Git
- Il sistema di sviluppo è disponibile in un archivio remoto Git denominato `mconfig`
- Il ramo di lavoro Git è denominato `m2.2_deploy`

## Passaggio 1: impostare la configurazione nel sistema di sviluppo

Per impostare le impostazioni internazionali e le unità di misura predefinite nel sistema di sviluppo:

1. Accedi all’amministratore.
1. Clic **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Se sono disponibili più siti Web, utilizzare **Visualizzazione store** nell’angolo in alto a sinistra per passare a un sito web diverso, come illustrato nella figura seguente.

   ![Cambia siti Web](../../assets/configuration/split-deploy-switch-website.png)

1. Nel riquadro di destra, espandere **Informazioni sul negozio**.
1. Se necessario, cancellare il **Usa predefinito** accanto alla casella di controllo **Partita IVA** campo.
1. Immettere un numero nel campo, ad esempio `12345`).
1. In **Nome store** , immetti un valore (come `My Store`).
1. Clic **Salva configurazione**.
1. Utilizza il **Visualizzazione store** elenco per selezionare **Configurazione predefinita** come illustrato nella figura seguente.

   ![Passa alla configurazione predefinita](../../assets/configuration/split-deploy-default-config.png)

1. Nel menu di navigazione a sinistra, nella sezione Generale, fai clic su **Contatti**.
1. Cancella **Usa predefinito** accanto alla casella di controllo **Invia e-mail a** campo.
1. Immetti un indirizzo e-mail nel campo.
1. Clic **Salva configurazione**.
1. Nel riquadro a sinistra, fai clic su Clienti > **Configurazione cliente**.
1. Nel riquadro di destra, espandere **Crea nuove opzioni account**.
1. Cancella **Usa valore di sistema** accanto alla casella di controllo **Dominio e-mail predefinito** campo.
1. Immetti un nome di dominio nel campo.
1. Clic **Salva configurazione**.
1. Se richiesto, svuotare la cache.

## Passaggio 2: aggiornare la configurazione

Dopo aver modificato la configurazione nell’amministratore, scrivi la configurazione condivisa in un file come descritto in questa sezione.

{{$include /help/_includes/config-save-config.md}}

Tieni presente che anche se `app/etc/env.php` (la configurazione specifica del sistema) è stata aggiornata, non archiviarla nel controllo del codice sorgente. Le stesse impostazioni di configurazione verranno create nel sistema di produzione più avanti in questa procedura.

## Passaggio 3: aggiornare il sistema di generazione e generare i file

Dopo aver confermato le modifiche apportate alla configurazione condivisa nel controllo del codice sorgente, è possibile richiamarle nel sistema di generazione, compilare il codice e generare file statici. L’ultimo passaggio consiste nel richiamare tali modifiche nel sistema di produzione.

{{$include /help/_includes/config-update-build-system.md}}

## Passaggio 4: aggiornare il sistema di produzione

L’ultimo passaggio del processo consiste nell’aggiornare il sistema di produzione. È necessario eseguire questa operazione in due parti:

- Aggiornare le impostazioni sensibili e specifiche del sistema
- Aggiornare le impostazioni condivise

### Aggiornare le impostazioni sensibili e specifiche del sistema

Per impostare le impostazioni sensibili e specifiche del sistema utilizzando le variabili di ambiente, è necessario conoscere quanto segue:

- Ambito per ogni impostazione

   Se hai seguito le istruzioni riportate nel passaggio 1, l’ambito per l’invio di e-mail a è globale (ovvero, l’ambito della configurazione predefinita) e l’ambito per il dominio e-mail predefinito è sito web.

   Devi conoscere il codice del sito web per impostare il valore di configurazione del dominio e-mail predefinito. Consulta [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables) per ulteriori informazioni su come trovarlo.

- Percorso di configurazione per ogni impostazione

   I percorsi di configurazione utilizzati in questo esempio seguono:

   | Nome impostazione | Percorso di configurazione |
   |--------------|--------------|
   | Invia e-mail a | `contact/email/recipient_email` |
   | Dominio e-mail predefinito | `customer/create_account/email_domain` |

   Puoi trovare tutti i percorsi di configurazione sensibili e specifici del sistema in [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md).

#### Convertire i percorsi di configurazione in nomi di variabili

Come discusso in [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables), il formato delle variabili è:

```text
<SCOPE>__<SYSTEM__VARIABLE__NAME>
```

Il valore di `<SCOPE>` è `CONFIG__DEFAULT__` per ambito globale o `CONFIG__WEBSITES__<WEBSITE CODE>` per l’ambito del sito web.

Per trovare il valore di `<SYSTEM__VARIABLE__NAME>`, sostituisci ogni `/` nel percorso di configurazione con due caratteri di sottolineatura.

I nomi delle variabili sono i seguenti:

| Nome | Percorso configurazione | Nome variabile |
|--------------|--------------|--------------|
| Invia e-mail a | `contact/email/recipient_email` | `CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL` |
| Dominio e-mail predefinito | `customer/create_account/email_domain` | `CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN` |

>[!INFO]
>
>Nella tabella precedente è presente un esempio di codice per un sito Web, `BASE`, per l’impostazione di configurazione del dominio e-mail predefinito. Sostituisci `BASE` con il codice del sito web appropriato per il tuo negozio.

#### Impostare le variabili utilizzando le variabili di ambiente

È possibile impostare i valori delle variabili in `index.php` utilizzando il seguente formato:

```php
$_ENV['VARIABLE'] = 'value';
```

**Per impostare i valori delle variabili**:

1. Accedi al sistema di produzione come proprietario del file system o passa a tale proprietario.
1. Apri `<Commerce root dir>/pub/index.php` in un editor di testo.
1. Ovunque in `index.php`, imposta valori per le variabili simili ai seguenti:

   ```php
   $_ENV['CONFIG__DEFAULT__CONTACT__EMAIL__RECIPIENT_EMAIL'] = 'myname@example.com';
   $_ENV['CONFIG__WEBSITES__BASE__CUSTOMER__CREATE_ACCOUNT__EMAIL_DOMAIN'] = 'magento.com';
   ```

1. Salva le modifiche apportate a `pub/index.php` ed esci dall’editor di testo.
1. Procedi alla sezione successiva.

### Aggiornare le impostazioni condivise

Questa sezione illustra come richiamare tutte le modifiche apportate ai sistemi di sviluppo e di creazione, che aggiornano le impostazioni di configurazione condivise (Nome store e Partita IVA).

{{$include /help/_includes/config-update-prod-system.md}}

### Verificare le impostazioni di configurazione in Admin

Questa sezione descrive come verificare le impostazioni di configurazione nell’amministratore del sistema di produzione.

**Verificare le impostazioni di configurazione**:

1. Accedi all’amministratore del sistema di produzione.
1. Clic **Negozi** > Impostazioni > **Configurazione** > Generale > **Generale**.
1. Utilizza il **Visualizzazione store** nell’angolo in alto a sinistra per passare a un altro sito web.

   Le opzioni di configurazione condivise impostate nel sistema di sviluppo vengono visualizzate in modo simile alle seguenti.

   ![Verifica le impostazioni nel sistema di produzione](../../assets/configuration/split-deploy-verify-storeinfo.png)

   >[!INFO]
   >
   >Il **Nome store** è modificabile nell’ambito del sito web, ma se passi all’ambito Configurazione predefinita non è modificabile. Questo è il risultato di come si impostano le opzioni nel sistema di sviluppo. Il valore di **Partita IVA** non è modificabile nell’ambito del sito web.

1. Se non lo hai già fatto, passa all’ambito Configurazione predefinita.
1. Nel menu di navigazione a sinistra, nella sezione Generale, fai clic su **Contatti**.

   Il **Invia e-mail a** non è modificabile, come illustrato nella figura seguente. Si tratta di un’impostazione sensibile.

   ![Verifica le impostazioni nel sistema di produzione](../../assets/configuration/split-deploy-verify-contacts.png)

1. Nel riquadro a sinistra, fai clic su Clienti > **Configurazione cliente**.
1. Nel riquadro di destra, espandere **Crea nuove opzioni account**.

   Il valore della proprietà **Dominio e-mail predefinito** viene visualizzato come segue. Si tratta di un’impostazione specifica del sistema.

   ![Verifica le impostazioni nel sistema di produzione](../../assets/configuration/split-default-domain.png)
