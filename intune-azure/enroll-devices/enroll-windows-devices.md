---
title: Registrera Windows-enheter
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Aktivera hantering av mobila enheter (MDM) för Windows-enheter."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 03/21/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: 609656c2831c09c67e911c8150d31f38faad020b
ms.lasthandoff: 03/22/2017


---

# <a name="enroll-windows-devices"></a>Registrera Windows-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd någon av följande metoder för att konfigurera registrering av Windows-enheter:

- [**Windows 10 och Windows 10 Mobile, automatisk registrering med Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Den här metoden gäller endast för Windows 10- och Windows 10 Mobile-enheter.
 -  Du måste ha Azure Active Directory Premium för att kunna använda den här metoden. Annars använder du registreringsmetoden för Windows 8.1 och Windows Phone 8.1.
 -  Om du väljer att inte aktivera automatisk registrering, kan du använda registreringsmetoden för Windows 8.1 och Windows Phone 8.1.

- [**Registrering utan automatisk registrering med Azure AD Premium**](#enable-windows-enrollment-without-azure-ad-premium)
 - Du måste använda den här metoden för att kunna registrera Windows 8.1- och Windows Phone 8.1-enheter.
 - Du kan använda den här metoden för Windows 8.1 och senare enheter om du inte vill använda Azure Active Directory (AD) Premium.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Aktivera Windows-registrering utan Azure AD Premium

Du kan låta användarna installera och registrera sina enheter utan automatisk registrering i Azure AD Premium. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

1. **Skapa CNAME-poster** (valfritt)<br>
 Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.

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

2.  **Verifiera CNAME**<br>På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Windows-registrering** på Intune-bladet. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

3.  **Berätta för dina användare hur de registrerar sina enheter och vad som händer när de har registrerat sina enheter för hantering.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Du kan även hänvisa användarna till [Vad kan min IT-administratör se på min enhet?](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

    Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

Inget ytterligare arbete krävs om du inte ska distribuera företagsportalen till enheter.  Du kan ignorera steg 2 och 3 i administrationskonsolen.

