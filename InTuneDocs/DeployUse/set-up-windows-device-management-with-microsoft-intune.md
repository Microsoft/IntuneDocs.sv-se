---
title: Konfigurera Windows-enhetshantering med Microsoft Intune | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Windows-datorer, till exempel Windows 10-enheter, med Microsoft Intune."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dfc5241376033471a232b059ac07fa4488f05514
ms.openlocfilehash: c405408bd6a1e2b0743566e413436aefbaa7018b


---

# Konfigurera Windows-enhetshantering

Som Intune-administratör kan du aktivera registrering och hantering för Windows-datorer på två sätt:

- **[Automatisk registrering med Azure Active Directory](#azure-active-directory-enrollment)** – Windows 10- och Windows 10 Mobile-användare registrerar sina enheter genom att lägga till ett arbetskonto eller skolkonto till enheten
- **[Registrering med företagsportalen](#company-portal-app-enrollment)** – Användare av Windows 8.1 och senare registrerar sina enheter genom att hämta och installera företagsportalappen och sedan ange autentiseringsuppgifterna för deras arbetskonto eller skolkonto i appen.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Konfigurera registrering via företagsportalappen
Du kan låta användarna installera och registrera sina enheter med hjälp av företagsportalappen. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

1. **Konfigurera Intune**<br>
Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [MAM-auktoritet (hantering av mobilenheter)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) och sedan konfigurera MDM.

2. **Skapa CNAME-poster** (valfritt)<br>Du kan förenkla registreringen genom att skapa **CNAME**-DNS-resursposter för din företagsdomän. Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas uppmanas användarna att manuellt ange MDM-servernamn, `https://manage.microsoft.com`. CNAME-resursposter måste ha följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn.

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras associerade arbets- eller skolkonto

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

3.  **Verifiera CNAME**<br>I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

  ![Dialogrutan Windows-enhetshantering](../media/enroll-intune-winenr.png)

4.  **Valfria steg**<br>Steget **Lägg till nycklar för separat inläsning** behövs inte för Windows 10. Steget **Överför certifikat för kodsignering ** behövs bara om du ska distribuera affärsappar som inte är tillgängliga från Windows Store. [Läs mer](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

6.  **Informera användare**<br>Du måste informera användarna om hur de registrerar sina enheter och vad som händer när de registrerat dem för hantering:
      - [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Vägledning för slutanvändare för Windows-enheter](../enduser/using-your-windows-device-with-intune.md)

### Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->


