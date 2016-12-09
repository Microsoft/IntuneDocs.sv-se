---
title: Konfigurera Windows-enhetshantering med Microsoft Intune | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Windows-datorer, till exempel Windows 10-enheter, med Microsoft Intune."
keywords: 
author: staciebarker
manager: stabar
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6adfb7375f9747f64e7037164f48918789bd7ee0
ms.openlocfilehash: 7c518c176e315cbf005b2fceb8d74de09bdcfa98


---

# <a name="set-up-windows-device-management"></a>Konfigurera Windows-enhetshantering

Som Intune-administratör kan du aktivera registrering och hantering för Windows-datorer på två sätt:

- **[Automatisk registrering med Azure Active Directory](#azure-active-directory-enrollment)** – Windows 10- och Windows 10 Mobile-användare registrerar sina enheter genom att lägga till ett arbetskonto eller skolkonto till enheten
- **[Registrering med företagsportalen](#company-portal-app-enrollment)** – Användare av Windows 8.1 och senare registrerar sina enheter genom att hämta och installera företagsportalappen och sedan ange autentiseringsuppgifterna för deras arbetskonto eller skolkonto i appen.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>Konfigurera registrering via företagsportalappen
Du kan låta användarna installera och registrera sina enheter med hjälp av företagsportalappen. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

1. **Konfigurera Intune**<br>
Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [MAM-auktoritet (hantering av mobilenheter)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) och sedan konfigurera MDM.

2. **Skapa CNAME-poster** (valfritt)<br>Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment.manage.microsoft.com.

    Om du har en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till manage.microsoft.com så föreslår vi att du ersätter den med en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com. Den här ändringen rekommenderas eftersom slutpunkten manage.microsoft.com kommer att föråldras för registreringar i en framtida version.

    CNAME-resursposter måste ha följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras associerade arbets- eller skolkonto

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

3.  **Verifiera CNAME**<br>I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

  ![Dialogrutan Windows-enhetshantering](../media/enroll-intune-winenr.png)

4.  **Valfria steg**<br>Steget **Lägg till nycklar för separat inläsning** behövs inte för Windows 10. Steget **Överför certifikat för kodsignering ** behövs bara om du ska distribuera affärsappar som inte är tillgängliga från Windows Store.

6.  **Berätta för dina användare hur de registrerar sina enheter och vad de kan förvänta sig när de registrerat sig för hantering.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](../enduser/enroll-your-device-in-intune-windows.md).

    Information om slutanvändaraktiviteter finns i de här artiklarna:
      - [Resurser om slutanvändarens upplevelse med Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Vägledning för slutanvändare för Windows-enheter](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Dec16_HO2-->


