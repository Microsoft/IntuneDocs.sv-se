---
title: Konfigurera Windows-enhetshantering med Microsoft Intune | Microsoft Docs
description: "Aktivera hantering av mobila enheter (MDM) för Windows-enheter med Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>Konfigurera Windows-enhetshantering

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd någon av följande metoder för att konfigurera registrering av Windows-enheter:

- [**Windows 10, automatisk registrering med Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Den här metoden är endast tillgänglig för Windows 10-enheter.
 -  Du måste ha Azure Active Directory Premium för att kunna använda den här metoden.
 -  Om du väljer att inte aktivera automatisk registrering, kan du använda registreringsmetoden för Windows 8.1 och Windows Phone 8.1.

- [**Registrering utan automatisk registrering med Azure AD Premium**](#enable-windows-enrollment-without-azure-ad-premium)
 - Du måste använda den här metoden för att kunna registrera Windows 8.1- och Windows Phone 8.1-enheter.
 - Du kan använda den här metoden för Windows 8.1 och senare enheter om du inte vill använda Azure Active Directory (AD) Premium.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Aktivera Windows-registrering utan automatisk registrering
Du kan låta användarna installera och registrera sina enheter utan automatisk registrering i Azure AD Premium. När du tilldelar licenser till användarnas konton kan användarna lägga till kontot i en Windows-enhet och samtycka till att registrera enheten i hantering. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

**Steg 1: Skapa CNAME-poster** (valfritt)<br>
Skapa CNAME-DNS-resursposter för företagsdomänen. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.

Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

Om det finns fler än en verifierad domän, skapar du en CNAME-post för varje domän. CNAME-resursposten måste innehålla följande information:

CNAME-resursposter måste ha följande information:

|TYP|Värdnamn|Pekar på|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

`EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

**Steg 2: Verifiera CNAME** (valfritt)<br>
I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Berätta för användare hur de ska registrera Windows-enheter
Berätta för användarna hur de ska registrera sina Windows-enheter och vad de kan förvänta sig när de har registrerat sig för hantering.
Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Du kan även hänvisa användarna till [Vad kan min IT-administratör se på min enhet](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

### <a name="see-also"></a>Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)

