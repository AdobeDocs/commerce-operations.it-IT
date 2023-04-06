---
title: Creare, modificare o sbloccare un account amministratore
description: Segui questi passaggi per gestire l’account amministratore dell’applicazione Adobe Commerce o Amministratore di Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Creare, modificare o sbloccare un account amministratore

Prima di poter utilizzare questo comando, è necessario effettuare le seguenti operazioni:

- [Creare la configurazione della distribuzione](deployment.md)
- [Abilitare almeno i moduli Magento_Authorization e Magento_User](manage-modules.md)
- Creare lo schema del database

>[!NOTE]
>
>Il modo più semplice per creare il database è quello di utilizzare il comando `magento setup:upgrade`.

## Creare o modificare un amministratore

Utilizzare questo comando per creare un amministratore o per modificare un amministratore esistente.

>[!NOTE]
>
>Se modifichi un amministratore, solo la variabile `first name`, `last name`e `password` può essere modificato.

Utilizzo comando:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Se la tabella seguente definisce parametri e valori:

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--admin-firstname` | Nome utente amministratore. | Sì |
| `--admin-lastname` | Cognome utente amministratore. | Sì |
| `--admin-email` | Indirizzo e-mail dell&#39;utente amministratore. | Sì |
| `--admin-user` | Nome utente amministratore. | Sì |
| `--admin-password` | Password utente amministratore. La password deve contenere almeno 7 caratteri e deve contenere almeno un carattere alfabetico e almeno un carattere numerico. <br><br>È consigliabile impostare una password più lunga e complessa. Se la stringa di password contiene caratteri speciali che richiedono un’interpretazione letterale (come barre rovesciate o spazi), racchiudi la password tra virgolette singole. | Sì |
| `--magento-init-params` | Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione dell&#39;applicazione<br/><br/>Ad esempio: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

Esempio di utilizzo:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

Se non si specifica nessuno dei parametri richiesti, l’applicazione ne chiede informazioni in CLI:

```bash
bin/magento admin:user:create
```

```terminal
Admin user: John
Admin password:
Admin email: j.doe.young@example.com
Admin first name: John
Admin last name: Doe Young
```

```terminal
Created Magento administrator user named John
```

L’esempio seguente viene aggiornato `first name`, `last name`e `password` di `j.doe` utente amministratore:

```bash
bin/magento admin:user:create --admin-firstname="John X" --admin-lastname="Doe X" --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A1234567
```

```terminal
Created Magento administrator user named j.doe
```

## Sbloccare un account amministratore

Utilizzare questo comando per sbloccare l&#39;account di un amministratore bloccato, in genere a causa di più tentativi di accesso non corretti.

```bash
bin/magento admin:user:unlock {username}
```

Specificare il nome utente dell&#39;amministratore. Esempio:

```bash
bin/magento admin:user:unlock admin
```

```terminal
The user account "admin" has been unlocked
```

Se l&#39;account non è sbloccato o se si è verificato un problema, viene visualizzato il seguente messaggio:

```terminal
The user account "admin" was not locked or could not be unlocked
```

Verifica che l’utente sia un amministratore, che l’utente sia attivo e che l’account sia bloccato. Per visualizzare l’elenco degli utenti bloccati nell’amministratore, accedi come amministratore e fai clic su **Sistema** > **Autorizzazioni** > **Utenti bloccati**.

Se l&#39;account non esiste, viene visualizzato il seguente messaggio:

```terminal
Couldn't find the user account "bob"
```
