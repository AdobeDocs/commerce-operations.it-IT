---
title: 'ACSD-62355: migliora le prestazioni di modifica dei prodotti configurabili in Adobe Commerce'
description: Applica la patch ACSD-62355 per risolvere il problema di Adobe Commerce, a causa del quale il caricamento della pagina di modifica del prodotto configurabile rallenta quando il prodotto è basato su numerosi attributi con molti valori.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: e8694744c8a2411a8e966148860f43fb56b48772
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: migliora le prestazioni di modifica dei prodotti configurabili in Adobe Commerce

La patch ACSD-62355 risolve il problema dei tempi di caricamento lenti e dell’elevato consumo di memoria nella pagina di modifica del prodotto configurabile quando il prodotto ha molti attributi con numerosi valori. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62355. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il caricamento della pagina di modifica del prodotto configurabile richiede molto tempo se il prodotto configurabile si basa su più attributi con molti valori, causando ritardi e potenziali problemi di timeout o di limite della memoria.

<u>Passaggi da riprodurre</u>:

1. Creare 9 nuovi attributi nel set di attributi predefinito, ciascuno dei quali è [!UICONTROL Filterable] e contiene [!UICONTROL Scope]: [!UICONTROL Global].
   * Attributo 1: 50 opzioni
   * Attributo 2: 20 opzioni
   * Attributo 3: 10 opzioni
   * Attributo 4: 5 opzioni
   * Attributo 5: 5 opzioni
   * Attributo 6: 5 opzioni
   * Attributo 7: 5 opzioni
   * Attributo 8: 3 opzioni
   * Attributo 9: 2 opzioni

1. Crea 9 prodotti semplici con combinazioni di opzioni dagli attributi appena creati.
   * Prodotto 1: prima opzione da ogni attributo
   * Prodotto 2: seconda opzione da ciascun attributo
   * Prodotto 3: terza opzione da ogni attributo
   * Prodotto 4: Quarta opzione da ogni attributo
   * Se un attributo ha un numero di opzioni inferiore al numero di prodotti, assegna i prodotti rimanenti a opzioni casuali all’interno di tale attributo.

1. Crea un prodotto configurabile che utilizza gli attributi appena creati:
   * Aggiungi un prodotto secondario con la seguente configurazione:
      * Utilizzare l&#39;ultima opzione dell&#39;attributo 1 e la prima opzione degli attributi da 2 a 9.
      * Ciò si traduce in 1 prodotto configurabile e 1 prodotto secondario.
1. Passa alla scheda **[!UICONTROL Configurations]** del prodotto configurabile.
1. Fare clic su **[!UICONTROL Add Products]** manualmente e iniziare ad aggiungere uno alla volta i prodotti semplici creati in precedenza.
1. Salva le modifiche dopo ogni aggiunta.
1. Quando aggiungi prodotti, osserva il tempo di caricamento della pagina Modifica prodotto configurabile.
1. Dopo l&#39;aggiunta di 7 prodotti, noterete un aumento significativo del consumo di RAM e del tempo di caricamento delle pagine

<u>Risultati previsti</u>:

Il modulo di modifica del prodotto dovrebbe essere caricato in modo rapido ed efficiente senza un eccessivo consumo di memoria.

<u>Risultati effettivi</u>:

Il caricamento della modifica del prodotto configurabile richiede molto tempo e può causare problemi di memoria o timeout.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
