---
title: riferimento system.xml
description: Scopri come il file XML di sistema gestisce la configurazione dell’applicazione Commerce.
feature: Configuration, System
badge: label="Contributo di David Lambauer" type="Informative" url="https://github.com/DavidLambauer" tooltip="David Lambauer"
exl-id: a6c5de6c-e8da-4eca-bbfb-592904b2c53f
source-git-commit: e231a27d70e29b01c872b0655168e31f590d4876
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# riferimento system.xml

Il file `system.xml` consente di gestire la configurazione del sistema Commerce. Utilizzare questo argomento come riferimento generale per il file `system.xml`. Il file `system.xml` si trova in `etc/adminhtml/system.xml` in una determinata estensione di Commerce 2.

Il seguente frammento di codice mostra l&#39;ossatura del file:

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <!-- PLACE YOUR MODULE SPECIFIC CONFIGURATION HERE -->
    </system>
</config>
```

>[!TIP]
>
>Se desideri una convalida *XSD immediata nell&#39;IDE, puoi eseguire `bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>`.

## Schede // Sezioni // Gruppi // Campi

Nel file `system.xml` è possibile definire quattro diversi tipi di entità, che sono correlati tra loro. Nella sezione seguente viene descritta la relazione tra schede, sezioni, gruppi e campi. La schermata seguente mostra la configurazione del sistema di Commerce 2 nel backend di amministrazione.
I quadrati rossi contrassegnano i diversi tipi definiti nel file `system.xml`:

![Schermata che mostra una sezione configurata in Admin.](../../assets/configuration/magento2-system-configuration.png)

Le schede vengono utilizzate per dividere semanticamente diverse aree di configurazione. Ogni scheda può contenere una o più sezioni, a cui è possibile fare riferimento come sottomenu. Una sezione contiene uno o più gruppi.
Ogni gruppo elenca uno o più campi. È inoltre possibile utilizzare un gruppo per aggiungere una descrizione generale per i campi seguenti. Come accennato, ogni gruppo può avere uno o più campi. I campi sono l’entità più piccola
nel contesto di configurazione del sistema.

## Schede

Un tag `<tab>` fa riferimento a una scheda esistente o nuova nella configurazione di sistema.

### Riferimento attributo scheda

Un tag `<tab>` può avere i seguenti attributi:

| Attributo | Descrizione | Tipo | Obbligatorio |
|-------------|------------------------------------------------------------------------------------------------------------------------------------------|----------|----------|
| `id` | Definisce l’identificatore utilizzato che fa riferimento alla sezione. | `typeId` | obbligatorio |
| `translate` | Definisce il campo da tradurre. Fornisci `label` per rendere traducibile l&#39;etichetta. | `string` | facoltativo |
| `sortOrder` | Definisce l’ordinamento della sezione. I numeri alti spingono la sezione nella parte inferiore della pagina, mentre i numeri bassi spingono la sezione nella parte superiore. | `float` | facoltativo |
| `class` | Aggiunge una classe CSS definita all&#39;elemento HTML scheda sottoposto a rendering. | `string` | facoltativo |

### Riferimento nodo scheda

Un tag `<tab>` può avere il seguente elemento figlio:

| Nodo | Descrizione | Tipo |
|---------|------------------------------------------------------|----------|
| `label` | Definisce l’etichetta visualizzata nel front-end. | `string` |

### Esempio: creare una scheda

Il seguente frammento di codice illustra la creazione di una nuova scheda con dati di esempio.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>
    </system>
</config>
```

Il frammento precedente crea una nuova scheda con l&#39;identificatore `A_UNIQUE_ID`. Poiché l&#39;attributo `translate` è definito e fa riferimento all&#39;etichetta, il nodo `label` è traducibile. Durante il rendering, la classe CSS `a-custom-css-class-to-style-this-tab` verrà applicata all&#39;elemento HTML creato per questa scheda.
L&#39;attributo `sortOrder` con il valore di `10` definisce la posizione della scheda nell&#39;elenco di tutte le schede sottoposte a rendering.

## Sezioni

Un tag `<section>` fa riferimento a una sezione esistente o nuova nella configurazione di sistema.

### Riferimento attributo sezione

Un tag `<section>` può avere i seguenti attributi:

| Attributo | Descrizione | Tipo | Obbligatorio |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definisce l’identificatore utilizzato che fa riferimento alla sezione. | `typeId` | obbligatorio |
| `translate` | Definisce il campo da tradurre. Fornisci `label` per rendere traducibile l&#39;etichetta. | `string` | facoltativo |
| `type` | Definisce il tipo di input dell&#39;elemento HTML sottoposto a rendering. Impostazione predefinita: `text`. | `string` | facoltativo |
| `sortOrder` | Definisce l’ordinamento della sezione. I numeri alti spingono la sezione nella parte inferiore della pagina, mentre i numeri bassi spingono la sezione nella parte superiore. | `float` | facoltativo |
| `showInDefault` | Definisce se la sezione viene visualizzata nell&#39;ambito di configurazione predefinito. Specificare `1` per visualizzare la sezione e `0` per nasconderla. | `int` | facoltativo |
| `showInStore` | Definisce se la sezione viene visualizzata a livello di punto vendita. Specificare `1` per visualizzare la sezione e `0` per nasconderla. | `int` | facoltativo |
| `showInWebsite` | Definisce se la sezione viene visualizzata a livello di sito Web. Specificare `1` per visualizzare la sezione e `0` per nasconderla. | `int` | facoltativo |
| `canRestore` | Definisce se la sezione può essere ripristinata sul valore predefinito. | `int` | facoltativo |
| `advanced` | Obsoleto dalla versione 100.0.2. | `bool` | facoltativo |
| `extends` | Specificando un identificatore di un’altra sezione, il contenuto di questo nodo estenderà la sezione a cui hai fatto riferimento. | `string` | facoltativo |

### Riferimento nodo sezione

Un tag `<section>` può avere i seguenti figli:

| Nodo | Descrizione | Tipo |
|------------------|-----------------------------------------------------------------------------------------------------------------------|---------------------|
| `label` | Definisce l’etichetta visualizzata nel front-end. | `string` |
| `class` | Aggiunge una classe CSS definita all&#39;elemento HTML della sezione di cui è stato eseguito il rendering. | `string` |
| `tab` | Fa riferimento alla scheda associata. Prevede l’ID della scheda. | `typeTabId` |
| `header_css` | Né utilizzato né valutato al momento di questa scrittura. | `string` |
| `resource` | Fa riferimento a una risorsa ACL per fornire le impostazioni delle autorizzazioni per questa sezione. | `typeAclResourceId` |
| `group` | Definisci uno o più sottogruppi. | `typeGroup` |
| `frontend_model` | Specifica un modello front-end diverso per modificare il rendering e l&#39;output. | `typeModel` |
| `include` | Utilizzato per includere ulteriori file compatibili con `system_include.xsd`. Utilizzato in genere per strutturare file `system.xml` di grandi dimensioni. | `includeType` |

### Esempio: creare una sezione e assegnarla a una scheda

Il seguente frammento di codice illustra l&#39;utilizzo di base della creazione di una nuova sezione.

```xml
<?xml version="1.0" ?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>
        </section>
    </system>
</config>
```

La sezione descritta sopra definisce l&#39;ID `A_UNIQUE_SECTION_ID`, che è visibile nella vista di configurazione predefinita e in un contesto di archivio. Il nodo `label` è traducibile. La sezione è associata alla scheda con ID `A_UNIQUE_ID`. È possibile accedere alla sezione solo da utenti che dispongono delle autorizzazioni definite nell&#39;ACL `VENDOR_MODULE::path_to_the_acl_resource`.

## Gruppi

Il tag `<group>` viene utilizzato per raggruppare i campi.

### Riferimento attributo gruppo

Un tag `<group>` può avere i seguenti attributi:

| Attributo | Descrizione | Tipo | Obbligatorio |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definisce l’identificatore utilizzato che fa riferimento al gruppo. | `typeId` | obbligatorio |
| `translate` | Definisce i campi da tradurre. Fornisci `label` per rendere traducibile l&#39;etichetta. Più campi devono essere separati da uno spazio. | `string` | facoltativo |
| `type` | Definisce il tipo di input dell&#39;elemento HTML sottoposto a rendering. Impostazione predefinita: `text`. | `string` | facoltativo |
| `sortOrder` | Definisce l’ordinamento della sezione. I numeri alti spingono la sezione nella parte inferiore della pagina, mentre i numeri bassi spingono la sezione nella parte superiore. | `float` | facoltativo |
| `showInDefault` | Definisce se il gruppo viene visualizzato nell&#39;ambito di configurazione predefinito. Specificare `1` per mostrare il gruppo e `0` per nasconderlo. | `int` | facoltativo |
| `showInStore` | Definisce se il gruppo viene visualizzato a livello di archivio. Specificare `1` per mostrare il gruppo e `0` per nasconderlo. | `int` | facoltativo |
| `showInWebsite` | Definisce se il gruppo viene visualizzato a livello di sito Web. Specificare `1` per mostrare il gruppo e `0` per nasconderlo. | `int` | facoltativo |
| `canRestore` | Definisce se il gruppo può essere ripristinato al valore predefinito. | `int` | facoltativo |
| `advanced` | Obsoleto dalla versione 100.0.2. | `bool` | facoltativo |
| `extends` | Specificando un identificatore di un altro gruppo, il contenuto di questo nodo estenderà la sezione a cui si fa riferimento. | `string` | facoltativo |

### Riferimento nodo di gruppo

Un tag `<group>` può avere i seguenti figli:

| Nodo | Descrizione | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `label` | Definisce l’etichetta visualizzata nel front-end. | `string` |
| `fieldset_css` | Aggiunge una o più classi CSS a un set di campi gruppo. | `string` |
| `frontend_model` | Specifica un modello front-end diverso per modificare il rendering e l&#39;output. | `typeModel` |
| `clone_model` | Specifica un determinato modello per clonare i campi. | `typeModel` |
| `clone_fields` | È stata abilitata o disabilitata la clonazione dei campi. | `int` |
| `help_url` | Non estensibile. Vedi sotto. | `typeUrl` |
| `more_url` | Non estensibile. Vedi sotto. | `typeUrl` |
| `demo_link` | Non estensibile. Vedi sotto. | `typeUrl` |
| `comment` | Aggiunge un commento sotto l&#39;etichetta del gruppo. Utilizzando `<![CDATA[//]]>` HTML è possibile applicare. | `string` |
| `hide_in_single_store_mode` | Indica se il gruppo deve essere visibile in modalità archivio singolo. `1` nasconde il gruppo; `0` mostra il gruppo. | `int` |
| `field` | Definisci uno o più campi che devono essere disponibili in questo gruppo. | `field` |
| `group` | Definisci uno o più sottogruppi. | `unbounded` |
| `depends` | Può essere utilizzato per dichiarare dipendenze da altri campi. Viene utilizzato per mostrare campi/gruppi specifici solo quando un determinato campo ha un valore di `1`. Questo nodo richiede una stringa `section/group/field`. | `depends` |
| `attribute` | Gli attributi personalizzati possono essere utilizzati dai modelli front-end. Di solito utilizzato per rendere più dinamico un determinato modello di front-end. | `attribute` |
| `include` | Utilizzato per includere ulteriori file compatibili con `system_include.xsd`. Utilizzato in genere per strutturare file `system.xml` di grandi dimensioni. | `includeType` |

>[!WARNING]
>
>I nodi `more_url`, `demo_url` e `help_url` sono definiti da un modello front-end PayPal utilizzato una sola volta. Questi nodi non sono riutilizzabili.

### Esempio: creare un gruppo per una determinata sezione

Il seguente frammento di codice illustra l&#39;utilizzo di base della creazione di un nuovo gruppo.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label comment" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>
                <!-- Add your fields here. -->
            </group>
        </section>
    </system>
</config>
```

Il gruppo descritto sopra definisce l&#39;ID `A_UNIQUE_GROUP_ID`, è visibile nella vista di configurazione predefinita e in un contesto di archivio. Sia `label` che `comment` sono contrassegnati come traducibili.

## Campi

Il tag `<field>` viene utilizzato all&#39;interno dei tag `<group>` per definire valori di configurazione specifici.

### Riferimento attributo campo

Un tag `<field>` può avere i seguenti attributi:

| Attributo | Descrizione | Tipo | Obbligatorio |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| `id` | Definisce l’identificatore utilizzato che fa riferimento al campo. | `typeId` | obbligatorio |
| `translate` | Definisce i campi da tradurre. Fornisci `label` per rendere traducibile l&#39;etichetta. Più campi devono essere separati da uno spazio. | `string` | facoltativo |
| `type` | Definisce il tipo di input dell&#39;elemento HTML sottoposto a rendering. Impostazione predefinita: `text`. | `string` | facoltativo |
| `sortOrder` | Definisce l’ordinamento della sezione. I numeri alti spingono la sezione nella parte inferiore della pagina, mentre i numeri bassi spingono la sezione nella parte superiore. | `float` | facoltativo |
| `showInDefault` | Definisce se il campo viene visualizzato nell&#39;ambito di configurazione predefinito. Specificare `1` per visualizzare il campo e `0` per nascondere il campo. | `int` | facoltativo |
| `showInStore` | Definisce se il campo viene visualizzato a livello di archivio. Specificare `1` per visualizzare il campo e `0` per nascondere il campo. | `int` | facoltativo |
| `showInWebsite` | Definisce se il campo viene visualizzato a livello di sito Web. Specificare `1` per visualizzare il campo e `0` per nascondere il campo. | `int` | facoltativo |
| `canRestore` | Definisce se il campo può essere ripristinato al valore predefinito. | `int` | facoltativo |
| `advanced` | Obsoleto dalla versione 100.0.2. | `bool` | facoltativo |
| `extends` | Specificando un identificatore di un altro campo, il contenuto di questo nodo estenderà la sezione a cui hai fatto riferimento. | `string` | facoltativo |

### Riferimento tipo di campo

Un tag `<field>` può avere i seguenti valori per l&#39;attributo `type=""`:

| Tipo | Descrizione |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `text` | Campo di testo a riga singola standard |
| `textarea` | Blocco di testo |
| `select` | Menu a discesa Normal, potrebbe essere necessario un `source_model` personalizzato. Utilizzato anche per `Yes/No` selezioni. Vedi `Magento\Search\Model\Adminhtml\System\Config\Source\Engine` per un esempio. |
| `multiselect` | Come `select`, ma sono valide più opzioni. |
| `button` | Pulsante che attiva un evento immediato. Richiede un modello front-end personalizzato per definire il testo del pulsante e l’azione. Vedi `Magento\ScheduledImportExport\Block\Adminhtml\System\Config\Clean` per un esempio. |
| `obscure` | Un campo di testo con il valore crittografato e visualizzato come `****`. Se si modifica il tipo utilizzando l’elemento &quot;Inspect&quot; nel browser, il valore non viene visualizzato. |
| `password` | Come `obscure`, tranne per il fatto che il valore nascosto non è crittografato e la modifica forzata del tipo tramite &quot;Inspect Element&quot; nel browser non rivela il valore. |
| `file` | Consente di caricare un file per l’elaborazione. |
| `label` | Visualizza un&#39;etichetta anziché un campo modificabile. Utilizzare questo tipo quando un campo è modificabile solo su ambiti specifici, ad esempio solo a livello di visualizzazione archivio. |
| `time` | Controllo per impostare il tempo utilizzando tre menu a discesa: Ora, minuto e secondo. |
| `allowspecific` | Un elenco a selezione multipla di paesi specifici. Richiede un `source_model` come `Magento\Shipping\Model\Config\Source\Allspecificcountries` |
| `image` | Consente di caricare un’immagine. |
| `note` | Consente di aggiungere una nota informativa alla pagina. Questo tipo richiede `frontend_model` per eseguire il rendering della nota. |

È inoltre possibile creare un tipo di campo personalizzato. Questa operazione viene spesso eseguita quando è necessario un pulsante speciale, con un’azione. A tal fine sono necessari due elementi principali:

- Creazione di un blocco in `adminhtml`
- Impostazione di `type=""` nel percorso di questo blocco

Il blocco stesso richiede almeno un metodo `__construct` e un metodo `getElementHtml()`. [Magento_OfflineShipping](https://github.com/magento/magento2/blob/2.4/app/code/Magento/OfflineShipping) è un semplice esempio di tipo personalizzato.

Nel modulo OfflineShipping, ad esempio, il pulsante Esporta è definito in `Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export` e la definizione del campo è simile alla seguente:

```xml
<field id="export" translate="label" type="Magento\OfflineShipping\Block\Adminhtml\Form\Field\Export" sortOrder="5" showInDefault="0" showInWebsite="1" showInStore="0">
    <label>Export</label>
</field>
```

### Riferimento nodo di campo

Un tag `<field>` può avere i seguenti figli:

| Nodo | Descrizione | Tipo |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| `label` | Definisce l’etichetta visualizzata nel front-end. | `string` |
| `comment` | Aggiunge un commento sotto l&#39;etichetta del campo. Utilizzando `<![CDATA[//]]>` HTML è possibile applicare. | `string` |
| `tooltip` | Un altro possibile elemento front-end che può essere utilizzato per descrivere il significato di questo campo. Viene visualizzata come una piccola icona accanto al campo. | `string` |
| `hint` | Visualizza informazioni aggiuntive. Disponibile solo con `frontend_model` specifico. | `string` |
| `frontend_class` | Aggiunge una classe CSS definita all&#39;elemento HTML della sezione di cui è stato eseguito il rendering. | `string` |
| `frontend_model` | Specifica un modello front-end diverso per modificare il rendering e l&#39;output. | `typeModel` |
| `backend_model` | Specifica un modello di back-end diverso per la modifica dei valori configurati. | `typeModel` |
| `source_model` | Specifica un modello di origine diverso che fornisce un insieme specifico di valori. | `typeModel` |
| `config_path` | Può essere utilizzato per sovrascrivere il percorso di configurazione generico di un campo. | `typeConfigPath` |
| `validate` | Definire regole di convalida diverse (separate da spazi). Di seguito è riportato l’elenco completo dei riferimenti delle regole di convalida disponibili. | `string` |
| `can_be_empty` | Utilizzato quando `type` è `multiselect` per specificare che un campo può essere vuoto. | `int` |
| `if_module_enabled` | Utilizzato per visualizzare un campo solo quando un determinato modulo è abilitato. | `typeModule` |
| `base_url` | Utilizzato in combinazione con `upload_dir` per i caricamenti di file. | `typeUrl` |
| `upload_dir` | Specifica una directory di destinazione per i caricamenti. Questo nodo ha attributi e nodi aggiuntivi. Controllali prima di usare questo. | `typeUploadDir` |
| `button_url` | Visualizza un pulsante se sono specificati `button_url` e `button_label`. Di solito utilizzato in combinazione con un modello front-end personalizzato. | `typeUrl` |
| `button_label` | Visualizza un pulsante se sono specificati `button_label` e `button_url`. Di solito utilizzato in combinazione con un modello front-end personalizzato. | `string` |
| `more_url` | Non estensibile. Vedi sotto. | `typeUrl` |
| `demo_url` | Non estensibile. Vedi sotto. | `typeUrl` |
| `hide_in_single_store_mode` | Indica se il gruppo deve essere visibile in modalità archivio singolo. `1` nasconde il gruppo; `0` mostra il gruppo. | `int` |
| `options` | Non utilizzato. Potenzialmente obsoleto. | `complexType` |
| `depends` | Può essere utilizzato per dichiarare le dipendenze ad altri campi. Viene utilizzato per mostrare campi/gruppi specifici solo quando un determinato campo ha un valore di `1`. Questo nodo richiede una stringa `section/group/field`. | `complexType` |
| `attribute` | Gli attributi personalizzati possono essere utilizzati dai modelli front-end. Di solito utilizzato per rendere più dinamico un determinato modello di front-end. | `complexType` |
| `requires` | Non estensibile. Vedi sotto. | `complexType` |

>[!WARNING]
>
>I nodi `more_url`, `demo_url`, `requires` e `options` sono definiti da un diverso modello di pagamento di base e vengono utilizzati una sola volta. Questi nodi non sono riutilizzabili.

### Esempio: creare due campi in un determinato gruppo

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
    <system>
        <tab id="A_UNIQUE_ID" translate="label" class="a-custom-css-class-to-style-this-tab" sortOrder="10">
            <label>A meaningful label</label>
        </tab>

        <section id="A_UNIQUE_SECTION_ID" showInDefault="1" showInWebsite="0" showInStore="1" sortOrder="10" translate="label">
            <label>A meaningful section label</label>
            <tab>A_UNIQUE_ID</tab>
            <resource>VENDOR_MODULE::path_to_the_acl_resource</resource>

            <group id="A_UNIQUE_GROUP_ID" translate="label" sortOrder="10" showInDefault="1" showInWebsite="0" showInStore="1">
                <label>A meaningful group label</label>
                <comment>An additional comment helping users to understand the effect when configuring the fields defined in this group.</comment>

                <field id="A_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="select">
                    <label>Feature Flag Example</label>
                    <comment>This field is an example for a basic yes or no select.</comment>
                    <tooltip>Usually these kinds of fields are used to enable or disable a given feature. Other fields might be dependent to this and will only appear if this field is set to yes.</tooltip>
                    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
                </field>

                <field id="ANOTHER_UNIQUE_FIELD_ID" translate="label" sortOrder="10" showInDefault="0" showInWebsite="0" showInStore="1" type="text">
                    <label>A meaningful field label</label>
                    <comment>A descriptive text explaining this configuration field.</comment>
                    <tooltip>Another possible frontend element that also can be used to describe the meaning of this field. Will be displayed as a small icon beside the field.</tooltip>
                    <validate>required-entry no-whitespace</validate> <!-- Field is required and must not contain any whitespace. -->
                    <if_module_enabled>VENDOR_MODULE</if_module_enabled>
                    <depends> <!-- This field will only be visible if the field with the id A_UNIQUE_FIELD_ID is set to value 1 -->
                        <field id="A_UNIQUE_FIELD_ID">1</field>
                    </depends>
                </field>
            </group>
        </section>
    </system>
</config>
```

L&#39;esempio precedente crea due campi, entrambi visibili/configurabili nella visualizzazione predefinita e nella visualizzazione punto vendita. Entrambi i campi hanno un commento e una descrizione per descriverne lo scopo per l’utente. Il nodo `label` è traducibile.
Il campo con l&#39;identificatore `ANOTHER_UNIQUE_FIELD_ID` è visibile quando il modulo specificato in `if_module_enabled` è abilitato a livello globale. Il valore del campo viene convalidato anche in base alle regole `required-entry` e `no-whitespace`.
Il campo con identificatore `A_UNIQUE_FIELD_ID` definisce un modello di origine diverso che fornisce i valori `Yes` e `No`.

### Modelli di origine comuni

I seguenti modelli di origine sono forniti da Commerce 2 Core. In generale, ci sono molti più modelli di origine; l&#39;elenco seguente descrive quelli più comuni. Tenere presente che questi modelli di origine richiedono che l&#39;attributo del campo `type` sia impostato su `select` per funzionare correttamente.

| Modello Source | Descrizione |
|-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| `Magento\Config\Model\Config\Source\Yesnocustom` | Fornisce i valori `Yes`, `No` e `Specified`. |
| `Magento\Config\Model\Config\Source\Enabledisable` | Fornisce i valori `Enable`, `Disable`. Salva i valori come `0` e `1` nel database. |
| `Magento\AdminNotification\Model\Config\Source\Frequency` | Fornisce i valori `1 Hour`,`2 Hours`,`6 Hours`,`12 Hours` e `24 Hours`. I valori vengono salvati come numeri interi. |
| `Magento\Catalog\Model\Config\Source\TimeFormat` | Fornisce i valori per il formato ora (12 h/24 h). |
| `Magento\Cron\Model\Config\Source\Frequency` | Fornisce i valori `Daily`, `Weekly` e `Monthly`. I valori vengono salvati nel database come `D`, `W` e `M`. |
| `Magento\GoogleAdwords\Model\Config\Source\Language` | Fornisce i valori per un codice di 2 lettere di una determinata lingua nel formato ISO 639-1 (ad esempio en). |
| `Magento\Config\Model\Config\Source\Locale` | Fornisce valori simili a quelli riportati sopra, ma contiene un codice locale (ad esempio en_US). |

### Convalida campo

A un campo possono essere assegnate una o più classi di convalida per garantire che l’input dell’utente soddisfi i requisiti dell’estensione. Le regole di convalida possono essere applicate con il tag `<validate>`.
Nell&#39;esempio seguente viene convalidato un campo e vengono aggiunte diverse regole di convalida.

```xml
<field id="A_CUSTOM_IDENTIFIER" showInDefault="1" showInWebsite="0" showInStore="1">
    <validate>required-entry validate-clean-url no-whitespace</validate>
</field>
```

Sono disponibili le seguenti regole di convalida:

| Regola | Descrizione |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| `alphanumeric` | Consente solo lettere, numeri, spazi o trattini bassi. |
| `integer` | Consente un numero non decimale positivo o negativo. |
| `ipv4` | Consente un indirizzo IP v4 valido. |
| `ipv6` | Consente un indirizzo IP v6 valido. |
| `letters-only` | Consente solo lettere. Ad esempio, `abcABC`. |
| `letters-with-basic-punc` | Consente solo lettere o punteggiatura.<br>Deve passare la seguente espressione: `/^[a-z\-.,()\u0027\u0022\s]+$/i`. |
| `mobileUK` | Consente un numero di telefono cellulare (Regno Unito). |
| `no-marginal-whitespace` | Non consente spazi vuoti all&#39;inizio o alla fine del valore. |
| `no-whitespace` | Non consente spazi vuoti. |
| `phoneUK` | Consente un numero di telefono (Regno Unito). |
| `phoneUS` | Consente un numero di telefono (Stati Uniti). |
| `required-entry` | Non consente un valore vuoto (convalida equivalente a `validate-no-empty`).<br>Messaggio di errore di convalida: &quot;Questo campo è obbligatorio&quot;. |
| `time` | Consente un orario valido nel formato 24 ore, tra le 00:00 e le 23:59. Ad esempio `15`, `15:05` o `15:05:48`. |
| `time12h` | Consente un orario valido in formato 12 ore, tra le 12:00 e le 11:59:59 pm. Ad esempio `3 am`, `11:30 pm`, `02:15:00 pm`. |
| `validate-admin-password` | Consente 7 o più caratteri, sia numerici che alfabetici. |
| `validate-alphanum-with-spaces` | Consente l&#39;uso di lettere (a-z o A-Z), numeri (0-9) o solo spazi. |
| `validate-clean-url` | Consente un URL valido. Ad esempio, `https://www.example.com` o `www.example.com`. |
| `validate-currency-dollar` | Consente un importo in dollari valido. Ad esempio, $100,00. |
| `validate-data` | Consente solo l&#39;utilizzo di lettere (a-z o A-Z), numeri (0-9) o caratteri di sottolineatura (\_).<br>Il primo carattere deve essere una lettera.<br>(Deve corrispondere all&#39;espressione: `/^[A-Za-z]+[A-Za-z0-9_]+$/`)<br>Messaggio di errore di convalida: &quot;Utilizzare solo lettere (a-z o A-Z), numeri (0-9) o il carattere di sottolineatura (\_) in questo campo e il primo carattere deve essere una lettera.&quot; |
| `validate-date-au` | Applica il seguente formato data: gg/mm/aaaa. Ad esempio, 17/03/2006 per il 17 marzo 2006. |
| `validate-email` | Consente un indirizzo e-mail valido. Ad esempio, johndoe@domain.com. |
| `validate-emailSender` | Consente un indirizzo e-mail valido. Ad esempio, johndoe@domain.com. |
| `validate-fax` | Consente un numero di fax valido. Ad esempio, 123-456-7890. |
| `validate-no-empty` | Non consente un valore vuoto (convalida equivalente a `requried-entry`).<br>Messaggio di errore di convalida: &quot;Valore vuoto&quot;. |
| `validate-no-html-tags` | Non consente l’utilizzo di tag HTML. |
| `validate-password` | Consente 6 o più caratteri. Gli spazi iniziali e finali verranno ignorati. |
| `validate-phoneLax` | Consente un numero di telefono valido. Ad esempio, (123) 456-7890 o 123-456-7890. |
| `validate-phoneStrict` | Consente un numero di telefono valido. Ad esempio, (123) 456-7890 o 123-456-7890. |
| `validate-select` | Impone che l&#39;opzione di selezione scelta non abbia un valore `null`, un valore stringa di `none` o una lunghezza stringa di 0. |
| `validate-ssn` | Consente un numero di previdenza sociale (Stati Uniti) valido. Ad esempio, 123-45-6789. |
| `validate-street` | Consente l&#39;utilizzo solo di lettere (a-z o A-Z), numeri (0-9), spazi e &quot;#&quot;. |
| `validate-url` | Consente un URL valido. Protocollo obbligatorio (http://, https:// o ftp://). |
| `validate-xml-identifier` | Consente un identificatore XML valido. Ad esempio, something_1, block5, id-4. |
| `validate-zip-us` | Consente un CAP valido (Stati Uniti). Ad esempio, 90602 o 90602-1234. |
| `vinUS` | Consente il valore (US) del numero di identificazione del veicolo (VIN). |

### Valori predefiniti

I valori predefiniti per i campi possono essere impostati nel file `etc/config.xml` del modulo specificando il valore predefinito nel nodo `section/group/field_ID`.

#### Esempio: impostazione del valore predefinito per `ANOTHER_UNIQUE_FIELD_ID` (ambito predefinito)

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <default>
        <A_UNIQUE_SECTION_ID>
            <A_UNIQUE_GROUP_ID>
                <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
            </A_UNIQUE_GROUP_ID>
        </A_UNIQUE_SECTION_ID>
    </default>
</config>
```

#### Esempio: impostazione del valore predefinito per `ANOTHER_UNIQUE_FIELD_ID` (ambito sito Web)

Utilizzando il tag `websites`, specifica il valore predefinito per un sito Web specifico.

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Store:etc/config.xsd">
    <websites>
        <WEBSITE_CODE>
            <A_UNIQUE_SECTION_ID>
                <A_UNIQUE_GROUP_ID>
                    <ANOTHER_UNIQUE_FIELD_ID>This is the default value</ANOTHER_UNIQUE_FIELD_ID>
                </A_UNIQUE_GROUP_ID>
            </A_UNIQUE_SECTION_ID>
        </WEBSITE_CODE>
    </websites>
</config>
```
