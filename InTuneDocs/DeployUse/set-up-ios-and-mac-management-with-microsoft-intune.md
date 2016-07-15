---
title: Konfigurera iOS- och Mac-enhetshantering | Microsoft Intune
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bb44d53c87bec1b6892bf49a65f3df684199ed08
ms.openlocfilehash: 9766b6e64259d809b04e6f6004c25ed88ad72659


---

# Konfigurera iOS- och Mac-enhetshantering
Med Microsoft Intune kan du aktivera BYOD (”Bring Your Own Device”) för registreringen av iOS- och Mac OS X-enheter så att iPhone-, iPad- och Mac-användare får åtkomst till företagets e-post och appar. När den här funktionen har aktiverats kan användarna installera Intunes företagsportalapp så att principer kan tillämpas på deras enheter via Intune-administrationskonsolen.

Innan du kan hantera iOS-enheter med Intune måste enheterna kunna kommunicera med Intune. Apple kräver en förtroenderelation med Intune som upprättas genom att ett certifikat för Apple Push Notification Service (APNs) importeras.

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
    Dina användare behöver information om hur de registrerar sina enheter och om vad som händer när de registrerat dem för hantering. [Vad du ska berätta för slutanvändare om att använda Microsoft Intune](what-to-tell-your-end-users-about-using-microsoft-intune.md)

Om företaget eller organisationen köper iOS-enheter åt användarna kan enheterna även registreras för hantering som [företagsägda iOS-enheter](enroll-corporate-owned-ios-devices-in-microsoft-intune.md).

### Se även
[Dags att registrera enheter i Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Jun16_HO4-->


