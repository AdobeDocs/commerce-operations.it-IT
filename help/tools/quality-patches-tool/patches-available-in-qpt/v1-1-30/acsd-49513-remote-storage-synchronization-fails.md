---
title: 'ACSD-49513: sincronizzazione dell''archiviazione remota non riuscita'
description: Applicare la patch ACSD-49513 per risolvere il problema Adobe Commerce in cui la sincronizzazione dello storage remoto non riesce a causa di file a 0 byte.
feature: Iaas, Storage
role: Admin
exl-id: 94dacfc4-d2d6-47b9-be0a-5bb55225af9a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: aa037b12-c774-5642-a947-459024feb1a2
    internal-label: Storage
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
subfeature_v2:
  - id: df5e974b-6742-4873-a687-a6bedaafdaa2
    internal-label: IaaS
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%
---
# ACSD-49513: la sincronizzazione dell&#39;archiviazione remota non riesce a causa di file da 0 byte

La patch ACSD-49513 risolve il problema relativo all&#39;errore della sincronizzazione dell&#39;archiviazione remota a causa di file a 0 byte. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-49513. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La sincronizzazione dell&#39;archiviazione remota non riesce a causa di file da 0 byte.

<u>Passaggi da riprodurre</u>:

1. Configura AWS S3 come archiviazione remota.
1. Eseguire `[bin/magento remote-storage:sync]` per assicurarsi che la sincronizzazione funzioni correttamente all&#39;inizio.
1. Creare un file da 0 byte in `[pub/media]`.
1. Eseguire di nuovo `[bin/magento remote-storage:sync]`.

<u>Risultati previsti</u>:

Poiché AWS S3 accetta file a 0 byte sul push diretto S3, non si verifica alcun errore.

<u>Risultati effettivi</u>:

Si verifica il seguente errore:

```PHP
Uploading media files to remote storage.
In File.php line 387:
  The file or directory "pub/media/xxxx.file" cannot be copied to "*.amazonaws.com/media/xxxx.file"
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
