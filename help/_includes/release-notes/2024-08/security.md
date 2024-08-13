---
source-git-commit: 07947c20ef49d1b3ad5df441c0a47982216ff36f
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 0%

---
# Punti salienti delle patch di sicurezza di agosto 2024

Questa versione include i seguenti elementi di rilievo:

* **Limitazione della frequenza per[!DNL one-time passwords]**. Le seguenti nuove opzioni di configurazione del sistema sono ora disponibili per abilitare la limitazione della frequenza nella convalida di [!DNL two-factor authentication (2FA)] [!DNL one-time password (OTP)]:

   * [!UICONTROL **Limite tentativi per autenticazione a due fattori**]
   * [!UICONTROL **Tempo di blocco per autenticazione a due fattori (secondi)**]

  L’Adobe consiglia di impostare una soglia per la convalida OTP 2FA per limitare il numero di tentativi di mitigare gli attacchi di forza bruta. Per ulteriori informazioni, vedere [Sicurezza > 2FA](https://experienceleague.adobe.com/en/docs/commerce-admin/config/security/2fa) nella _Guida di riferimento alla configurazione_. <!-- AC-12095 -->

* **Rotazione chiave di crittografia**: è ora disponibile un nuovo comando CLI per la modifica della chiave di crittografia. Per ulteriori informazioni, vedere l&#39;articolo della Knowledge Base relativo alla risoluzione dei problemi relativi alla rotazione delle chiavi di crittografia: CVE-2024-34102](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102).[

* **Correzione per [CVE-2020-27511](https://nvd.nist.gov/vuln/detail/CVE-2020-27511)**—Risolve una vulnerabilità di sicurezza [!DNL Prototype.js].<!-- AC-11936 -->

* **Correzione per [CVE-2024-39397](https://nvd.nist.gov/vuln/detail/CVE-2024-39397)**—Risolve una vulnerabilità di sicurezza dell&#39;esecuzione di codice remoto. Questa vulnerabilità influisce sui commercianti che utilizzano il server web Apache per distribuzioni locali o con hosting autonomo. Questa correzione è disponibile anche come patch isolata. Per ulteriori informazioni, vedere l&#39;articolo della Knowledge Base [Security update available for Adobe Commerce - APSB24-61](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-61).<!-- ACSD-60551 -->
