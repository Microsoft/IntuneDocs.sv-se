---
title: Konfigurera hanteringen av Windows 10 Mobile och Windows Phone | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Windows 10 Mobile- eller Windows Phone-enheter med Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: d88405e913fe61cef2c297f9d50408e10674cf3f


---


# Konfigurera hanteringen av Windows Phone och Windows 10 Mobile med Microsoft Intune

Som Intune-administratör kan du aktivera registrering och hantering för Windows 10 Mobile- och Windows Phone-enheter på två sätt:

- **[Automatisk registrering med Azure AD](#azure-active-directory-enrollment)** – Windows 10- och Windows 10 Mobile-användare registrerar sina enheter genom att lägga till ett arbetskonto eller skolkonto till enheten
- **[Registrering med företagsportalen](#company-portal-app-enrollment)** – De som använder Windows Phone 8.1 och senare registrerar sina enheter genom att först hämta och installera företagsportalappen och sedan ange autentiseringsuppgifterna för sitt arbetskonto eller skolkonto i appen.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Registrering med företagsportalappen
Du kan låta användare registrera sina enheter genom att installera och registrera sina enheter med Intune-företagsportalappen. Om du skapar en DNS-CNAME-post blir det lättare för användarna att ansluta och registrera sig i Intune utan att ange ett servernamn. Om du hanterar Windows Phone 8.0-enheter eller behöver distribuera företagsportalen till Windows Phone-enheter måste du också hämta och signera företagsportalappen. Se [Konfigurera hantering av Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Konfigurera Intune**<br>Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#set-mobile-device-management-authority) och genom att konfigurera MDM.

2.  **Skapa CNAME-poster** (valfritt)<br>Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats exempelvis är contoso.com, skulle du skapa en CNAME-post i DNS-servern som omdirigerar EnterpriseEnrollment.contoso.com till manage.microsoft.com. Om det finns fler än en verifierad domän, skapar du en CNAME-post för varje domän. CNAME-resursposten måste innehålla följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|
  Det kan ta upp till 72 timmar för ändringar i DNS-poster att spridas. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

  `EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn.

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1 och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras arbets- eller skolkonton.

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Det kan ta upp till 72 timmar för ändringar i DNS-poster att spridas. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

3.  **Verifiera CNAME**<br>Gå till [Intune-administrationskonsolen](http://manage.microsoft.com) och klicka på **Administration** &gt; **Hantering av mobila enheter** &gt; **Windows Phone**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och klicka sedan på **Testa automatisk identifiering**.

    ![Dialogrutan Ställa in hantering av mobila enheter för Windows](../media/windows-phone-enrollment.png)

4.  **Valfria steg**<br>Steget **Lägg till nycklar för separat inläsning** behövs inte för Windows 10. Steget **Överför certifikat för kodsignering ** behövs bara om du ska distribuera verksamhetsspecifika appar till enheter och apparna inte är tillgängliga från Windows Store. [Läs mer](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

5.  **Informera användare**<br>Dina användare behöver information om hur de registrerar sina enheter och om vad som händer när de registrerat dem för hantering.
    - [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Vägledning för slutanvändare för Windows-enheter](../enduser/using-your-windows-device-with-intune.md)

Inget ytterligare arbete krävs om du inte ska distribuera företagsportalen till enheter.  Du kan ignorera steg 2 och 3 i administrationskonsolen.



<!--HONumber=Sep16_HO4-->


