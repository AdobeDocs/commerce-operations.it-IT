---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---
# Hotfix non inclusi nelle patch di sicurezza di giugno 2024

>[!IMPORTANT]
>
>Questo è un aggiornamento urgente alla nostra ultima comunicazione relativa a [CVE-2024-34102](https://nvd.nist.gov/vuln/detail/CVE-2024-34102). Adobe è consapevole del fatto che CVE-2024-34102 è stato sfruttato in modo selvaggio in attacchi molto limitati rivolti ai commercianti Adobe Commerce. Agisci immediatamente per risolvere la vulnerabilità, se non lo hai fatto.

**Per i clienti che non hanno applicato la patch di sicurezza rilasciata l&#39;11 giugno 2024 o la patch isolata rilasciata il 28 giugno 2024:**

Opzione 1:

1. Applica una delle patch di sicurezza rilasciate l’11 giugno 2024:

   * [2.4.7-p1](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-7-patches#adobe-commerce-247-p1)

   * [2.4.6-p6](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-6-patches#adobe-commerce-246-p6)

   * [2.4.5-p8](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-5-patches#adobe-commerce-245-p8)

   * [2.4.4-p9](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/2-4-4-patches#adobe-commerce-244-p9)

1. Applica l&#39;[hotfix](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) rilasciato il 17 luglio 2024.

1. [Ruota](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) le chiavi di crittografia.

Opzione 2:

1. Applica la [patch isolata](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102).

1. [Ruota](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) le chiavi di crittografia.

**Per i clienti che hanno già applicato una patch di sicurezza rilasciata l&#39;11 giugno 2024 o la patch isolata rilasciata il 28 giugno 2024:**

1. Applica l&#39;[hotfix](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) rilasciato il 17 luglio 2024.

1. [Ruota](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) le chiavi di crittografia.

**Per i clienti che hanno già 1) applicato una patch di sicurezza rilasciata l&#39;11 giugno 2024 o 2) la patch isolata rilasciata il 28 giugno 2024 e 3) ha ruotato le chiavi di crittografia:**
 
1. Applica l&#39;[hotfix](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102) rilasciato il 17 luglio 2024.
