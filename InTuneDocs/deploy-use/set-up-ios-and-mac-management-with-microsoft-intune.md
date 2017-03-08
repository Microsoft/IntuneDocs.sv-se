---
title: Konfigurera iOS- och Mac-enhetshantering | Microsoft Docs
description: "Aktivera hantering av mobila enheter (MDM) för iOS-enheter, inklusive iPad och iPhone samt Mac OS X-enheter med Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: afca2af0b07b939adc66c8804f04a1125e12001b
ms.openlocfilehash: 9c71a83f9514187753360fa9c2085584d1b76711
ms.lasthandoff: 02/18/2017


---

# <a name="set-up-ios-and-mac-device-management"></a>Konfigurera iOS- och Mac-enhetshantering

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och macOS-enheter och ger användarna åtkomst till företagets e-post och appar. Ett APNs-certifikat (Apple Push Notification Service) från Apple krävs för att kunna hantera iOS- och Mac-enheter med Intune. När certifikatet har lagts till i Intune kan användare installera företagsportalappen och registrera sina enheter, eller så kan administratören konfigurera [hantering av företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Konfigurera Intune**<br>
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](prerequisites-for-enrollment.md#step-2-set-mdm-authority) och genom att konfigurera MDM.

2.  **Hämta en certifikatsigneringsbegäran**<br>
    Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APNs-certifikat** och välj **Hämta begäran om APN-certifikat**. Spara begäran om certifikatsignering (.csr) lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

    ![Dialogrutan Överför APN-certifikat](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Hämta ett certifikat för Apple Push Notification Service**<br>
    Gå till [Apple Push-certifikatprofilen](http://go.microsoft.com/fwlink/?LinkId=269844) och logga in med ditt företags Apple-ID för att skapa APN-certifikatet med hjälp av CSR-filen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil som inte kan användas för APN. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp **Certifikat för servrar från tredje part** och klicka på **Hämta**.

    Hämta APN-certifikatet (.pem) och spara filen lokalt.

    > [!NOTE]
    > Varje år måste du förnya (inte ersätta) det här APN-certifikatet. Använd samma Apple-ID för att logga in på Apple Push-certifikatportalen för att förnya certifikatet. Använd sedan samma anvisningar i det här avsnittet för att hämta certifikatet och sedan överföra det till Intune.

4.  **Lägg till APN-certifikatet i Intune**<br>
    Öppna [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) och gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APN-certifikat** och välj **Överför APN-certifikatet**. Gå till certifikatfilen (.pem), välj **Öppna** och ange ditt **Apple-ID**. Med APN-certifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

5.  **Berätta för dina användare hur de registrerar sina enheter för att få åtkomst till företagsresurser.**

    Registreringsinstruktioner för slutanvändare finns i [Registrera din iOS-enhet i Intune](../enduser/enroll-your-device-in-intune-ios.md) och [Registrera din macOS-enhet i Intune](../enduser/enroll-your-device-in-intune-macos.md). Registreringsprocessen förklarar för användarna vad de kan förvänta sig och vad IT-administratörer kan och inte kan se på deras enheter.

    Information om andra slutanvändaraktiviteter finns i de här artiklarna:
    - [Resurser om slutanvändarupplevelsen med Microsoft Intune](how-to-educate-your-end-users-about-microsoft-intune.md)
    - [Vägledning för slutanvändare för iOS- och Mac-enheter](../enduser/using-your-ios-or-macOS-device-with-intune.md)

Om företaget eller organisationen köper iOS-enheter åt användarna kan enheterna även registreras för hantering som [företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Se även
[Krav för registrering i Microsoft Intune](prerequisites-for-enrollment.md)

