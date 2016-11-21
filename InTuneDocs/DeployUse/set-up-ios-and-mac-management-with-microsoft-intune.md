---
title: Konfigurera iOS- och Mac-enhetshantering | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för iOS-enheter, inklusive iPad och iPhone samt Mac OS X-enheter med Microsoft Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d51f34dea3463bec83ea39cdfb79c7bedf9e3926
ms.openlocfilehash: 930419b20b675aa48c2b8bf1c49a1b576bbab414


---

# <a name="set-up-ios-and-mac-device-management"></a>Konfigurera iOS- och Mac-enhetshantering
Intunes stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och Mac OS X-enheter och ger användarna åtkomst till företagets e-post och appar. Ett APNs-certifikat (Apple Push Notification Service) från Apple krävs för att kunna hantera iOS- och Mac-enheter med Intune. När certifikatet har lagts till i Intune kan användare installera företagsportalappen och registrera sina enheter, eller så kan administratören konfigurera [hantering av företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Konfigurera Intune**<br>
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#set-mobile-device-management-authority) och genom att konfigurera MDM.

2.  **Hämta en certifikatsigneringsbegäran**<br>
    Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APNs-certifikat** och välj **Hämta begäran om APN-certifikat**. Spara begäran om certifikatsignering (.csr) lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

    ![Dialogrutan Överför APN-certifikat](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Hämta ett certifikat för Apple Push Notification Service**<br>
    Gå till [Apple Push-certifikatprofilen](http://go.microsoft.com/fwlink/?LinkId=269844) och logga in med ditt företags Apple-ID för att skapa APN-certifikatet med hjälp av CSR-filen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil som inte kan användas för APN. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp **Certifikat för servrar från tredje part** och klicka på **Hämta**.

    Hämta APN-certifikatet (.pem) och spara filen lokalt. Det här Apple-ID:t måste användas senare för att förnya ditt APN-certifikat.

4.  **Lägg till APN-certifikatet i Intune**<br>
    Öppna [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) och gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APN-certifikat** och välj **Överför APN-certifikatet**. Gå till certifikatfilen (.pem), välj **Öppna** och ange ditt **Apple-ID**. Med APN-certifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

5.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din iOS-enhet i Intune](../enduser/enroll-your-device-in-intune-ios.md) och [Registrera din Mac OS X-enhet i Intune](../enduser/enroll-your-device-in-intune-mac-os-x.md). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

    Information om andra slutanvändaraktiviteter finns i de här artiklarna:
    - [Resurser om slutanvändarupplevelsen med Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Vägledning för slutanvändare för iOS- och Mac-enheter](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Om företaget eller organisationen köper iOS-enheter åt användarna kan enheterna även registreras för hantering som [företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Se även
[Krav för registrering i Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO2-->


