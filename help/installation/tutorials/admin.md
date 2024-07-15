---
title: Creare, modificare o sbloccare un account amministratore
description: Per gestire l’account amministratore dell’applicazione Adobe Commerce Admin, segui la procedura riportata di seguito.
feature: Install, User Account
exl-id: d87871a1-717d-4662-b84d-98a018518286
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Creare, modificare o sbloccare un account amministratore

Prima di poter utilizzare questo comando, è necessario effettuare le seguenti operazioni:

- [Creare la configurazione della distribuzione](deployment.md)
- [Abilitare almeno i moduli Magento_Authorization e Magento_User](manage-modules.md)
- Creare lo schema del database

>[!NOTE]
>
>Il modo più semplice per creare il database è utilizzare il comando `magento setup:upgrade`.

## Creare o modificare un amministratore

Utilizzare questo comando per creare un amministratore o per modificare un amministratore esistente.

>[!NOTE]
>
>Se si modifica un amministratore, è possibile modificare solo `first name`, `last name` e `password`.

Utilizzo comando:

```bash
bin/magento admin:user:create [--<parameter_name>=<value>, ...]
```

Dove la tabella seguente definisce parametri e valori:

| Nome | Valore | Obbligatorio |
|--- |--- |--- |
| `--admin-firstname` | Nome dell&#39;utente amministratore. | Sì |
| `--admin-lastname` | Cognome dell&#39;utente amministratore. | Sì |
| `--admin-email` | Indirizzo di posta elettronica dell&#39;utente amministratore. | Sì |
| `--admin-user` | Nome utente amministratore. | Sì |
| `--admin-password` | Password utente amministratore. La password deve contenere almeno 7 caratteri e includere almeno un carattere alfabetico e almeno un carattere numerico. <br><br>È consigliabile impostare una password più lunga e complessa. Se la stringa della password contiene caratteri speciali che richiedono un&#39;interpretazione letterale, ad esempio barre rovesciate o spazi, racchiudere la password tra virgolette singole. | Sì |
| `--magento-init-params` | Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione dell&#39;applicazione<br/><br/>Ad esempio: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | No |

Esempio di utilizzo:

```bash
bin/magento admin:user:create --admin-firstname=John --admin-lastname=Doe --admin-email=j.doe@example.com --admin-user=j.doe --admin-password=A0b9%t3g
```

```terminal
Created Magento administrator user named j.doe
```

Se non si specifica alcun parametro obbligatorio, l&#39;applicazione chiede informazioni in CLI:

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

Il seguente esempio aggiorna `first name`, `last name` e `password` di `j.doe` utente amministratore:

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

Se l’account non è sbloccato o si è verificato un problema, viene visualizzato il seguente messaggio:

```terminal
The user account "admin" was not locked or could not be unlocked
```

Verificare che l&#39;utente sia un amministratore, che sia attivo e che l&#39;account sia bloccato. Per visualizzare l&#39;elenco degli utenti bloccati nell&#39;amministratore, accedere come amministratore e fare clic su **Sistema** > **Autorizzazioni** > **Utenti bloccati**.

Se l’account non esiste, viene visualizzato il seguente messaggio:

```terminal
Couldn't find the user account "bob"
```
