---
source-git-commit: 4ed23e2a8319ff97f8206f752cf1cbe2e73ea5c5
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---
# 2.4.7 miglioramenti della sicurezza

* **È stato aggiunto il supporto per l&#39;integrità della sottorisorsa (SRI)** per soddisfare i requisiti PCI 4.0 per la verifica dell&#39;integrità dello script nelle pagine di pagamento. Il supporto per l’integrità della sottorisorsa (SRI) fornisce hash di integrità per tutte le risorse JavaScript che risiedono nel file system locale. La funzione SRI predefinita viene implementata solo nelle pagine di pagamento per le aree amministratore e vetrina. Tuttavia, i commercianti possono estendere la configurazione predefinita ad altre pagine. Consulta [Integrità della sottorisorsa](https://developer.adobe.com/commerce/php/development/security/subresource-integrity/) nella _Guida per gli sviluppatori di Commerce PHP_.<!--AC-1153-->

* **Modifiche alle direttive Content Security Policy (CSP)**—Aggiornamenti alla configurazione e miglioramenti alle direttive Adobe Commerce Content Security Policy (CSP) per la conformità ai requisiti PCI 4.0. Per informazioni dettagliate, vedere [Informativa sulla sicurezza dei contenuti](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) nella _Guida per gli sviluppatori di Commerce PHP_. <!--AC-11513-->

   * La configurazione CSP predefinita per le pagine di pagamento per le aree di amministrazione e vetrina di Commerce è ora in modalità `restrict`. Per tutte le altre pagine, la configurazione predefinita è la modalità `report-only`.  Nelle versioni precedenti alla versione 2.4.7, CSP era configurato in modalità `report-only` per tutte le pagine.

   * È stato aggiunto un provider nonce per consentire l’esecuzione di script in linea in un CSP. Il provider di nonce facilita la generazione di stringhe di nonce univoche per ogni richiesta. Le stringhe vengono quindi collegate all’intestazione CSP.

   * Sono state aggiunte opzioni per configurare URI personalizzati in modo da segnalare le violazioni CSP per le pagine Crea ordine in Amministrazione e Pagamento nella vetrina. È possibile aggiungere la configurazione dall&#39;amministratore o aggiungendo l&#39;URI al file `config.xml`.

     >[!NOTE]
     >
     >L&#39;aggiornamento della configurazione CSP alla modalità `restrict` potrebbe bloccare gli script in linea esistenti nelle pagine di pagamento in Admin e storefront, causando il seguente errore del browser al caricamento di una pagina: `Refused to execute inline script because it violates the following Content Security Policy directive: "script-src`. Correggi questi errori aggiornando la configurazione della whitelist per consentire gli script richiesti. Consulta [Risoluzione dei problemi](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#troubleshooting) nella _Guida per gli sviluppatori di Commerce PHP_.
