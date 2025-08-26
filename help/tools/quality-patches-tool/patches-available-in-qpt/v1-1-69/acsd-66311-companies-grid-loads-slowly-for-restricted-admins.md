---
title: 'ACSD-66311: la griglia delle società viene caricata lentamente per gli utenti amministratori con restrizioni'
description: Applica la patch ACSD-66311 per risolvere il problema Adobe Commerce, che comporta il caricamento lento della griglia delle aziende per gli utenti amministratori con accesso limitato ai siti web.
role: Admin, Developer
feature: B2B
type: Troubleshooting
exl-id: e470078b-dd10-4b0b-a489-bc88f025fded
source-git-commit: 3337907b1893260d6cb18b1c4fbf45dfa1f3d6d5
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 2%

---

# ACSD-66311: la griglia delle società viene caricata lentamente per gli utenti amministratori con restrizioni

La patch ACSD-66311 risolve il problema relativo al rallentamento del caricamento della griglia aziendale per gli utenti amministratori con accesso limitato al sito Web. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66311. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La griglia delle aziende viene caricata lentamente per gli utenti amministratori con accesso limitato al sito web.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce con **[!UICONTROL B2B features]**.
1. Crea 2 siti Web aggiuntivi (oltre al sito Web principale) con store/visualizzazioni:
   * Sito Web principale (creato durante l&#39;installazione)
   * Sito Web 2 → Store 2 → StoreView 2
   * Sito Web 3 → Store 3 → StoreView 3
1. Crea il ruolo utente **[!UICONTROL Admins in Scope]**:
   * Ambito: solo due archivi: *Sito Web principale* + *Sito Web 3/Archivio 3*.
   * Risorse: solo *Dashboard* + *Aziende*.
1. Creare un utente amministratore con un ruolo **[!UICONTROL Admins in Scope]**, ad esempio **adminscope**.
1. Generare dati specifici distribuiti relativi a clienti e società:
   1. **Clienti assegnati a siti Web**

      | ID sito Web | Numero di clienti |
      |------------|---------------------|
      | 1 | 600.000 |
      | 2 | 1.500 |
      | 3 | 500 |

   1. Esegui la seguente query per verificare la distribuzione:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Clienti assegnati alle aziende**

      | Numero di clienti | Numero di società |
      |---------------------|---------------------|
      | 1 | 4.500 |
      | 2 | ~1.000 |
      | ~595 k | 1 |

   1. Esegui la seguente query per verificare la distribuzione:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
              SELECT company_id, COUNT(customer_id) AS customer_count
              FROM company_advanced_customer_entity
              GROUP BY company_id
            ) AS subquery
            GROUP BY customer_count
            ORDER BY customer_count; 
      ```

1. Reindicizza tutti i dati per generare voci nel **customer_grid_flat**.
1. Accedi come **adminscope**.
1. Vai a **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Risultati previsti</u>:

La pagina viene caricata in meno di 1 secondo.

<u>Risultati effettivi</u>:

Il caricamento della pagina richiede più di 14 minuti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
