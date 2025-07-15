---
source-git-commit: 4dd926ca7014c9e007a8c2c847e076064eb8d170
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 1%

---
# Contribuire

Grazie per aver scelto di contribuire.

Di seguito è riportato un set di linee guida da seguire quando si contribuisce a questo progetto.

## Codice di condotta

Il progetto aderisce al [Codice di condotta](code-of-conduct.md) di Adobe. Partecipando,
è previsto che tu mantenga questo codice. Segnala eventuali condotte scorrette a
[Grp-opensourceoffice@adobe.com](mailto:Grp-opensourceoffice@adobe.com).

## Documentazione della Guida per i collaboratori

Consulta la [Guida per i collaboratori](https://experienceleague.adobe.com/en/docs/contributor/contributor-guide/introduction).

## Hai una domanda?

Inizia segnalando un problema. I committer esistenti di questo progetto lavorano per raggiungere
consenso sulla direzione del progetto e sulle soluzioni dei problemi all’interno dei thread dei problemi
(se del caso).

## Contratto di licenza da collaboratore

Tutti i contributi di terze parti a questo progetto devono essere accompagnati da un collaboratore firmato
contratto di licenza. In questo modo si concede ad Adobe il permesso di ridistribuire i contributi
come parte del progetto. [Firma il Contratto di licenza da collaboratore](https://opensource.adobe.com/cla.html). Tu
è sufficiente inviare un CLA di Adobe una sola volta, quindi se ne hai già inviato uno in precedenza,
sei bravo ad andare!

## Revisioni del codice

Tutte le richieste devono essere presentate sotto forma di richieste pull e devono essere riviste
dai committenti del progetto. Leggi la documentazione sulle richieste pull di [GitHub](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)
per ulteriori informazioni sull’invio di richieste pull.

<!--
Lastly, please follow the [pull request template](PULL_REQUEST_TEMPLATE.md) when
submitting a pull request!
-->

## Da collaboratore a committente

Apprezziamo i contributi della nostra community! Se desideri andare oltre il collaboratore
e diventare un committer con accesso in scrittura completo e una voce in capitolo nel progetto, devi
essere invitati al progetto. I committer esistenti utilizzano una nomina interna
processo che deve raggiungere il consenso pigro (il silenzio è approvazione) prima degli inviti
sono emessi. Se ritieni di essere qualificato e vuoi essere coinvolto più a fondo,
Puoi rivolgerti ai committer esistenti per parlarne con loro.

## Problemi di sicurezza

I problemi di sicurezza non devono essere segnalati in questo Issue tracker. [segnala un problema ai nostri esperti di sicurezza](https://helpx.adobe.com/security/alertus.html).

## Novità

Se le modifiche introducono nuovi argomenti, aggiornamenti significativi o correzioni che devono essere evidenziati, puoi aggiungere una breve descrizione alla [sezione Novità](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home#whats-new) direttamente dal corpo della richiesta di pull.

Per aggiungere un&#39;evidenziazione Novità:

1. Includi il tag `whatsnew` con la descrizione appropriata nel corpo della richiesta di pull alla fine. La descrizione deve fornire contesto sulla modifica e un collegamento all&#39;argomento o agli argomenti di destinazione. Utilizza il seguente formato (le virgolette dei blocchi di codice sono solo per la rappresentazione, non le includere nel corpo della richiesta di pull):

   ```text
   whatsnew
   Short description of the change in the [target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html).
   ```

   oppure, se sono presenti più argomenti:

   ```text
   whatsnew
   Short description of the changes in the [first target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/target-topic.html), [second target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-target-topic.html), and [third target topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/third-target-topic.html).
   ```

   è inoltre possibile utilizzare gli elenchi per evidenziare più elementi:

   ```text
   whatsnew
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

   ```text
   whatsnew
   The following changes were made to the documentation:
   - Short description of the first change in the [first topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/first-topic.html).
   - Short description of the second change in the [second topic](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/second-topic.html).
   ```

1. Aggiungi le etichette supportate che indicano il tipo di modifica. Le etichette supportate includono etichette per ogni tipo di modifica, ad esempio:

   - `new-topic` - per nuovi argomenti
   - `major-update` - per aggiornamenti principali che possono includere modifiche significative al contenuto, alla struttura o alle funzionalità
   - `technical` - per modifiche tecniche che non sono considerate aggiornamenti principali ma che richiedono comunque attenzione

   e, facoltativamente, etichette per l&#39;ambito di modifica, quali:

   - `qpt` - per le modifiche relative allo strumento Quality Patch

**Importante:**

1. La parte `whatsnew` deve iniziare dal tag `whatsnew` e trovarsi alla fine del corpo della richiesta di pull.
1. Le descrizioni delle modifiche devono includere collegamenti di lavoro. Verifica che i collegamenti siano corretti e reindirizza agli argomenti previsti. Se l’argomento è nuovo, verifica che i collegamenti funzionino dopo aver unito la richiesta di pull e pubblicato il nuovo argomento. È consentito correggere i collegamenti dopo l’unione della richiesta di pull.

Ad esempio, cerca nelle richieste pull chiuse nell&#39;archivio di per vedere come vengono formattati gli elementi di rilievo esistenti e confrontarli con la [sezione Novità](https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home#whats-new) per vedere come appaiono nella documentazione.
