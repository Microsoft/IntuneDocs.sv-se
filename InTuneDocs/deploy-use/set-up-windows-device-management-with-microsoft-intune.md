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
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: f66bc5a26f137f62defef4a83a36b22247be4ec1
ms.lasthandoff: 03/22/2017


---

# <a name="set-up-windows-device-management"></a>Konfigurera Windows-enhetshantering

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Använd någon av följande metoder för att konfigurera registrering av Windows-enheter:

- [**Windows 10 och Windows 10 Mobile, automatisk registrering med Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Den här metoden gäller endast för Windows 10- och Windows 10 Mobile-enheter.
 -  Du måste ha Azure Active Directory Premium för att kunna använda den här metoden. Annars använder du registreringsmetoden för Windows 8.1 och Windows Phone 8.1.
 -  Om du väljer att inte aktivera automatisk registrering, kan du använda registreringsmetoden för Windows 8.1 och Windows Phone 8.1.


- [**Windows 8.1- och Windows Phone 8.1-registrering genom att konfigurera CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - Du måste använda den här metoden för att kunna registrera Windows 8.1- och Windows Phone 8.1-enheter.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Konfigurera registrering av Windows 8.1 och Windows Phone 8.1 genom att konfigurera CNAME
Du kan låta användarna installera och registrera sina enheter med hjälp av Intune-företagsportalen. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

### <a name="step-1-set-up-intune"></a>Steg 1: Konfigurera Intune

Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [MAM-auktoritet (hantering av mobilenheter)](prerequisites-for-enrollment.md#step-2-set-mdm-authority) och sedan konfigurera MDM.

### <a name="step-2-create-cnames-optional"></a>Steg 2: Skapa CNAME-poster (valfritt)

Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.


   Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

   CNAME-resursposter måste ha följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras associerade arbets- eller skolkonto

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

### <a name="step-3-verify-cname"></a>Steg 3: Verifiera CNAME

I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>Steg 4: Berätta för dina användare hur de registrerar sina enheter och vad de kan förvänta sig när de registrerat sig för hantering.

   Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows).

   Mer information om slutanvändarnas aktiviteter finns i [Informera slutanvändare om Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) och [End user guidance for Windows devices](https://docs.microsoft.com/intune-user-help/using-your-windows-device-with-intune) (Vägledning om Windows-enheter för slutanvändare).

### <a name="see-also"></a>Se även
[Krav för att registrera enheter i Microsoft Intune](prerequisites-for-enrollment.md)

