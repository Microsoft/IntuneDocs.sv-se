---
title: Konfigurera Windows-enhetshantering med Microsoft Intune | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för Windows-datorer, till exempel Windows 10-enheter, med Microsoft Intune."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: fae2aa496ec38d9ddc2cb6800bed10ccb32fd154


---

# Konfigurera Windows-enhetshantering
Om du vill konfigurera din Windows-enhet kan du få hjälp [här](../enduser/using-your-windows-device-with-intune.md).

Med Intune kan du aktivera BYOD (”Bring Your Own Device”) för registrering av Windows PC-enheter för att ge åtkomst till företagets e-post och appar. Tillsammans med Azure Active Directory innebär detta också ett snabbt och automatiskt sätt att integrera nya Windows 10-enheter i hanteringen och få åtkomst till företagsresurser utan att återställa avbildningen på datorn. När användarna har registrerats kan de logga in och principer, appar och inställningar kan tillämpas på deras enheter via Intune-administrationskonsolen. Du kan också [konfigurera Windows Phone-hantering med Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) eller [hantera datorer med Intune-klientprogrammet](manage-windows-pcs-with-microsoft-intune.md) med hjälp av Intune-klienten.

Om du skapar en DNS-CNAME-post blir det lättare för användarna att ansluta och registrera sig i Intune utan att ange ett servernamn.

### Konfigurera Windows-enhetshantering

  1.  Skapa en **CNAME**-DNS-resurspost för din företagsdomän. Om ditt företags webbplats till exempel är contoso.com skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till EnterpriseEnrollment-s.manage.microsoft.com. CNAME DNS-posten är valfri för Windows-enhetsregistrering, men vi rekommenderar att du skapar en eller flera poster vid behov. Då blir det enklare att registrera Windows-enheter. Om ingen CNAME-post hittas ombeds användaren att ange namnet på MDM-servern manuellt.

  Om det finns fler än en verifierad domän, skapar du en CNAME-post för varje domän. CNAME-resursposten måste innehålla följande information:

  |TYP|Värdnamn|Pekar på|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

  Det kan ta upp till 72 timmar för ändringar i DNS-poster att spridas. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

  **EnterpriseEnrollment-s.manage.microsoft.com** – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postadressens domännamn

  **EnterpriseRegistration.windows.net** – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med ett arbets- eller skolkonto

  2.  I [Intune-administrationskonsolen](http://manage.microsoft.com) klickar du på **Admin** &gt; **Hantering av mobila enheter** &gt; **Windows**.
  ![Dialogrutan Windows-enhetshantering](../media/enroll-intune-winenr.png)

  3.  Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och klicka sedan på **Testa automatisk identifiering**.

  4.  Dina användare behöver information om hur de registrerar sina enheter och om vad som händer när de registrerat dem för hantering.
      - [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Vägledning för slutanvändare för Windows-enheter](../enduser/using-your-windows-device-with-intune.md)

### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


