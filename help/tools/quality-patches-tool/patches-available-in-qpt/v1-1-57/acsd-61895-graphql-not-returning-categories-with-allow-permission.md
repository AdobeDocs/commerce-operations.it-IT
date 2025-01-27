---
title: 'ACSD-61895: [!DNL GraphQL] la query delle categorie non riesce per il catalogo condiviso privato con visualizzazione limitata'
description: Applica la patch ACSD-61895 per risolvere il problema di Adobe Commerce per cui [!DNL GraphQL] le risposte per i clienti guest (utilizzando un catalogo condiviso pubblico con tutte le categorie consentite) non restituivano alcuna categoria durante la creazione di un catalogo condiviso privato con restrizioni per le stesse categorie.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
source-git-commit: f929f76dbe79c3764e2c157576b4f6db867673cf
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# ACSD-61895: query [!DNL GraphQL] `categories` non riuscita per catalogo condiviso privato con visualizzazione limitata

La patch ACSD-61895 risolve il problema per cui [!DNL GraphQL] risposte per i clienti guest (utilizzando un catalogo condiviso pubblico con tutte le categorie consentite) non restituivano alcuna categoria quando veniva creato un catalogo condiviso privato con restrizioni per le stesse categorie.

Dopo la correzione, vengono restituite tutte le categorie con autorizzazioni consentite (catalogo condiviso pubblico) per gli utenti guest, anche se la categoria principale non dispone di autorizzazioni consentite nell’ambito di un catalogo condiviso privato.

Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-61895. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL GraphQL] le risposte per i clienti guest (utilizzando un catalogo condiviso pubblico con tutte le categorie consentite) non restituiscono alcuna categoria quando viene creato un catalogo condiviso privato con restrizioni per le stesse categorie.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con B2B e dati di esempio.
1. Assicurati che le funzioni B2B siano abilitate.
1. Crea due cataloghi condivisi: uno pubblico e uno privato.

   * Catalogo condiviso pubblico:

      * Assegna tutte le categorie al catalogo pubblico.

   * Catalogo condiviso privato:

      * Assegnare solo la categoria `Gear` e le relative categorie figlio al catalogo privato.
      * Assegna il catalogo privato a una società di test.

1. Creare un utente aziendale:

   * Crea un utente associato alla società di test collegata al catalogo condiviso privato.
   * Assicurarsi che l&#39;utente sia in grado di accedere solo alla categoria `Gear` e alle relative categorie figlio sul front-end al momento dell&#39;accesso.

1. Query di categorie tramite API:

   * Utilizza il client API per eseguire la seguente query [!DNL GraphQL] senza un token cliente:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Osservare la risposta e verificare se vengono restituite la categoria `Gear` e altre categorie.
1. Ora esegui una query sulle categorie con un token cliente:

   * Accedi come utente della società di test.
   * Eseguire la stessa query di categoria [!DNL GraphQL], ma includere il token cliente per l&#39;utente connesso.
   * Osservare la risposta e verificare se vengono restituite solo la categoria `Gear` e le relative categorie figlio.


<u>Risultati previsti</u>:

Quando si esegue una query come utente della società ospite, devono essere restituite tutte le categorie (come previsto).

<u>Risultati effettivi</u>:

La risposta dalla query `categories` non mostra categorie.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.

