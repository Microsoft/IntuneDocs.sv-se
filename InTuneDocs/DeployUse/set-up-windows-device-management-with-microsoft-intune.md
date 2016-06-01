---
# required metadata

title: Konfigurera Windows-enhetshantering med Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurera Windows-enhetshantering
Med Intune kan du aktivera BYOD (”Bring Your Own Device”) för registrering av Windows PC-enheter för att ge åtkomst till företagets e-post och appar. Tillsammans med Azure Active Directory innebär detta också ett snabbt och automatiskt sätt att integrera nya Windows 10-enheter i hanteringen och få åtkomst till företagsresurser utan att återställa avbildningen på datorn. När användarna har registrerats kan de logga in och principer, appar och inställningar kan tillämpas på deras enheter via Intune-administrationskonsolen. Du kan också [konfigurera Windows Phone-hantering med Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) eller [hantera datorer med Intune-klientprogrammet](manage-windows-pcs-with-microsoft-intune.md) med hjälp av Intune-klienten.

Om du skapar en DNS-CNAME-post blir det lättare för användarna att ansluta och registrera sig i Intune utan att ange ett servernamn.

### Konfigurera Windows-enhetshantering

  1.  Skapa en **CNAME**-DNS-resurspost för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. Om det finns mer än en verifierad domän skapar du en CNAME-post för varje domän. CNAME-resursposterna måste innehålla följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

    DNS record changes might take up to 72 hours to propagate. You cannot verify the DNS change in Intune until the DNS record propagates.

    **EnterpriseEnrollment-s.manage.microsoft.com** – Supports a redirect to the Intune service with domain recognition from the email’s domain name

    **EnterpriseRegistration.windows.net** – Supports Windows 8.1 and Windows 10 Mobile devices that will register with Azure Active Directory using their work or school account

  2.  I [Intune-administrationskonsolen](http://manage.microsoft.com) klickar du på **Administration** &gt; **Hantering av mobila enheter** &gt; **Windows**.
  ![Dialogrutan Windows-enhetshantering](../media/enroll-intune-winenr.png)
  3.  Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och klicka sedan på **Testa automatisk identifiering**

### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


