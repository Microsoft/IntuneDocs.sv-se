---
# required metadata

title: Konfigurera hanteringen av Windows 10 Mobile och Windows Phone med Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Konfigurera hanteringen av Windows Phone och Windows 10 Mobile med Microsoft Intune
Innan du kan hantera Windows 10 Mobile- eller Windows Phone-enheter med Microsoft Intune måste enheterna kunna kommunicera med Intune. För att förenkla detta kan du skapa en DNS-post så att användarna inte behöver ange adressen till servern. Stegen nedan beskriver hur du underlättar registreringen för användarna.  

I de flesta fall kan användarna installera företagsportalappen från Windows Store. Om du hanterar Windows Phone 8.0-enheter eller behöver distribuera företagsportalen till Windows Phone-enheter måste du också hämta och signera företagsportalappen. Läs [Konfigurera hantering av Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Konfigurera Intune**
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) och genom att konfigurera MDM.

2.  **Ange ett DNS-alias för registreringsserverns adress** (valfritt)

    Om du skapar ett DNS-alias (CNAME-posttyp) blir det enklare för användarna att registrera sina enheter. Om du inte skapar ett DNS-alias måste användarna

  1.  Skapa **CNAME**-DNS-resursposter för din företagsdomän. Om ditt företags webbplats exempelvis är contoso.com, skulle du skapa en CNAME-post i DNS-servern som omdirigerar EnterpriseEnrollment.contoso.com till manage.microsoft.com. Om det finns mer än en verifierad domän skapar du en CNAME-post för varje domän. CNAME-resursposterna måste innehålla följande information:

      |TYP|Värdnamn|Pekar på|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 timme|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

      Det kan ta upp till 72 timmar för ändringar i DNS-poster att spridas. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

      **EnterpriseEnrollment-s.manage.microsoft.com** – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postadressens domännamn

      **EnterpriseRegistration.windows.net** – Stöder Windows 8.1- och Windows 10 Mobile-enheter som registreras med Azure Active Directory med ett arbets- eller skolkonto

    2.  I [Intune-administrationskonsolen](http://manage.microsoft.com) klickar du på **Administration** &gt; **Hantering av mobila enheter** &gt; **Windows Phone**.

      ![Dialogrutan Ställa in hantering av mobila enheter för Windows](../media/windows-device-enrollment.png)

    3.  Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och klicka sedan på **Testa automatisk identifiering**.



Inget ytterligare arbete krävs om du inte ska distribuera företagsportalen till enheter.  Du kan ignorera steg 2, 3 och 4 i administrationskonsolen.


<!--HONumber=May16_HO1-->


