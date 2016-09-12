---
title: Konfigurera iOS- och Mac-enhetshantering | Microsoft Intune
description: "Aktivera hantering av mobila enheter (MDM) för iOS-enheter, inklusive iPad och iPhone samt Mac OS X-enheter med Microsoft Intune."
keywords: 
author: NathBarn
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
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: e61e764f4761ab83500ff6f0febe253d427729d9


---

# Konfigurera iOS- och Mac-enhetshantering
Om du vill konfigurera din iOS- eller Mac-enhet kan du få hjälp [här](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md).

Ge åtkomst till företagets e-post och appar med Intunes hantering av mobila enheter för iPad, iPhone, och Mac OS X-enheter. Ett APNs-certifikat (Apple Push Notification Service) från Apple krävs för att kunna hantera iOS- och Mac-enheter med Intune. När certifikatet har lagts till i Intune kan användare installera företagsportalappen och registrera sina enheter, eller så kan administratören konfigurera [hantering av företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

1.  **Konfigurera Intune**<br>
    Om du inte redan gjort det förbereder du hanteringen av mobila enheter genom att definiera **Microsoft Intune** som [utfärdare av mobilenhetshantering](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) och genom att konfigurera MDM.

2.  **Hämta en certifikatsigneringsbegäran**<br>
    Öppna [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) som administratör, gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APNs-certifikat** och klicka på **Hämta begäran om APN-certifikat**. Spara begäran om certifikatsignering (.csr) lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

    ![Dialogrutan Överför APN-certifikat](../media/Intune-iOS-enrollment-with-apns.png)

3.  **Hämta ett certifikat för Apple Push Notification Service**<br>
    Gå till [Apple Push Certificates Portal](http://go.microsoft.com/fwlink/?LinkId=269844) , logga in med ditt företags Apple-ID och skapa APN-certifikatet med hjälp av CSR-filen. När du klickar på **Överför** på Apples portal för Push-certifikat får du en JSON-fil som inte kan användas för APNs. Slutför hämtningen och gå tillbaka till Apples portal för Push-certifikat, gå till **Certifikat för servrar från tredje part** och klicka på **Hämta**.

    Hämta APN-certifikatet (.pem) och spara filen lokalt. Detta Apple-ID måste användas i framtiden för att förnya ditt APN-certifikat.

4.  **Lägg till APN-certifikatet i Intune**<br>
    Öppna [Microsoft Intune-administratörskonsolen](http://manage.microsoft.com) och gå till **Administration** &gt; **Hantering av mobila enheter** &gt; **iOS och Mac OS X** &gt; **Överför ett APN-certifikat** och klicka på **Överför APN-certifikatet**. **Bläddra** till certifikatsfil (.pem) och klicka på **Öppna** och ange sedan ditt **Apple ID**. Med APN-certifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

5.  **Förklara för användarna hur de kommer åt företagets resurser med företagsportalen**<br>
    Dina användare behöver information om hur de registrerar sina enheter och om vad som händer när de registrerat dem för hantering.
    - [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Vägledning för slutanvändare för iOS- och Mac-enheter](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

Om företaget eller organisationen köper iOS-enheter åt användarna kan enheterna även registreras för hantering som [företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


