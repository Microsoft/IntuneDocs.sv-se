---
title: Konfigurera hanteringen av Windows 10 Mobile och Windows Phone | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Windows 10 Mobile- eller Windows Phone-enheter med Microsoft Intune."
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: 66d533d094a12239ca4ed1a30f9ce3a06e5cece1


---


# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>Konfigurera hanteringen av Windows Phone och Windows 10 Mobile med Microsoft Intune

Som Intune-administratör kan du aktivera registrering och hantering för Windows 10 Mobile- och Windows Phone-enheter på två sätt:

- **[Automatisk registrering med Azure Active Directory](#azure-active-directory-enrollment)** – Windows 10- och Windows 10 Mobile-användare registrerar sina enheter genom att lägga till ett arbetskonto eller skolkonto till enheten
- **[Registrering med företagsportalen](#company-portal-app-enrollment)** – Användare av Windows Phone 8.1 och senare registrerar sina enheter genom att hämta och installera företagsportalappen och sedan ange autentiseringsuppgifterna för deras arbetskonto eller skolkonto i appen.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>Registrering med företagsportalappen
Du kan låta användarna installera och registrera sina enheter med hjälp av företagsportalappen. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange ett servernamn.

1.  **Konfigurera Intune**<br>Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [MAM-auktoritet (hantering av mobilenheter)](prerequisites-for-enrollment.md#set-mobile-device-management-authority) och sedan konfigurera MDM.

2.  **Skapa CNAME-poster** (valfritt)<br>Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com. 

    Om du har en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till manage.microsoft.com så föreslår vi att du ersätter den med en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com. Den här ändringen rekommenderas eftersom slutpunkten manage.microsoft.com kommer att föråldras för registreringar i en framtida version.

    Om det finns fler än en verifierad domän, skapar du en CNAME-post för varje domän. CNAME-resursposten måste innehålla följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

  `EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

  `EnterpriseRegistration.windows.net` – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med deras associerade arbets- eller skolkonto

  Om ditt företag använder flera domäner för användarautentiseringsuppgifter kan du skapa CNAME-poster för varje domän.

  Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

3.  **Verifiera CNAME**<br>I [Intune-administrationskonsolen](http://manage.microsoft.com) väljer du **Administration** &gt; **Hantering av mobila enheter** &gt; **Windows Phone**. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

    ![Dialogrutan Ställa in hantering av mobila enheter för Windows](../media/windows-phone-enrollment.png)

4.  **Valfria steg**<br>Steget **Lägg till nycklar för separat inläsning** behövs inte för Windows 10. Steget **Överför certifikat för kodsignering ** behövs bara om du ska distribuera affärsspecifika appar (LOB) som inte är tillgängliga från Windows Store.

5.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](../enduser/enroll-your-device-in-intune-windows.md). Du kan också skicka användarna till [Vad kan din IT-administratör se när du registrerar din enhet i Intune?](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

    Information om andra slutanvändaraktiviteter finns i de här artiklarna:
    - [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Vägledning för slutanvändare för Windows-enheter](../enduser/using-your-windows-device-with-intune.md)

Inget ytterligare arbete krävs om du inte ska distribuera företagsportalen till enheter.  Du kan ignorera steg 2 och 3 i administrationskonsolen.



<!--HONumber=Nov16_HO2-->


