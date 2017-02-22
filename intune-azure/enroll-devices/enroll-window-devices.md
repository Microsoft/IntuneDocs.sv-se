---
title: "Registrera Windows-enheter | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Aktivera hantering av mobila enheter (MDM) för Windows-enheter."
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4103a4cef393df585b9b9daa92ab63dd7805e9e
ms.openlocfilehash: a55118e60750616f8b058846148364cbeccb5784


---

# <a name="enroll-windows-devices"></a>Registrera Windows-enheter 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Använd någon av följande metoder för att konfigurera registrering av Windows-enheter:

- [**Windows 10 och Windows 10 Mobile, automatisk registrering med Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Den här metoden gäller endast för Windows 10- och Windows 10 Mobile-enheter.
 -  Du måste ha Azure Active Directory Premium för att kunna använda den här metoden. Annars använder du registreringsmetoden för Windows 8.1 och Windows Phone 8.1.
 -  Om du väljer att inte aktivera automatisk registrering, kan du använda registreringsmetoden för Windows 8.1 och Windows Phone 8.1.

- [**Windows 8.1- och Windows Phone 8.1-registrering genom att konfigurera CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - Du måste använda den här metoden för att kunna registrera Windows 8.1- och Windows Phone 8.1-enheter.


## <a name="prerequisites"></a>Förutsättningar

Om några av följande förutsättningar ännu inte finns i Intune Azure-förhandsversionen behöver du skapa dem från den klassiska Intune-administratörskonsolen.

- [Konfigurera ett eget domännamn](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Ange **Microsoft Intune** som utfärdare ](set-mdm-authority.md) för hantering av mobila enheter
- [Konfigurera företagsportalappen](/intune-azure/manage-apps/company-portal-app.md)
- Tilldela licenser till användare

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Konfigurera registrering av Windows 8.1 och Windows Phone 8.1 genom att konfigurera CNAME

Du kan låta användarna installera och registrera sina enheter med hjälp av Intune-företagsportalen. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

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

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras associerade arbets- eller skolkonto

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

2.  **Verifiera CNAME**<br>I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Administration** &gt; **Hantering av mobila enheter** &gt; **Windows Phone**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

3.  **Valfria steg**<br>Steget **Lägg till nycklar för separat inläsning** behövs inte för Windows 10. <br>Steget **Överför certifikat för kodsignering ** behövs bara om du ska distribuera branschspecifika appar (LOB) som inte är tillgängliga från Windows Store till enheter.

4.  **Berätta för dina användare hur de registrerar sina enheter och vad som händer när de har registrerat sina enheter för hantering.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/en-us/intune/enduser/enroll-your-device-in-intune-windows). Du kan även hänvisa användarna till [Vad kan min IT-administratör se på min enhet?](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

    Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).

Inget ytterligare arbete krävs om du inte ska distribuera företagsportalen till enheter.  Du kan ignorera steg 2 och 3 i administrationskonsolen.



<!--HONumber=Feb17_HO3-->


