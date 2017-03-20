---
title: Registrera din macOS-enhet i Intune | Microsoft Docs
description: Beskriver hur du registrerar en macOS-enhet i Intune
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope:
- User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 10c7bc5461c746ab50e83c2ffc590b89efe75e5f
ms.openlocfilehash: bb4238472277ec579abdde7830a9abc50a7bae97
ms.lasthandoff: 03/13/2017


---

# <a name="enroll-your-macos-device-in-intune"></a>Registrera din macOS-enhet i Intune

Genom att få åtkomst till din organisations appar, data och resurser är det möjligt för dig att göra ditt jobb. Om du använder en macOS-enhet på arbetet, innebär det installation av en __Hanteringsprofil__. Detta är bara en fil som konfigurerats av din IT-administratör och som läser in inställningar och åtkomstinformation till din Mac. Vill du veta mer? Ta reda på [vad som händer om du installerar företagsportalappen och registrerar din enhet i Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

  > [!NOTE]
  > Om du försöker registrera en iOS-enhet, till exempel en iPhone eller iPad, [prova de här instruktionerna i stället](enroll-your-device-in-intune-ios.md).

1. På din __Docka__, går du till __Safari__ och öppnar ett nytt fönster och öppnar sedan [företagsportalens webbplats](http://portal.manage.microsoft.com).
2. Logga in på företagsportalens webbplats med ditt arbets- eller skolkonto.

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. När du loggar in visas alla __Start__-, __Appar__- och __Kategorier__-flikar som är tillgängliga. På den här sidan visas alla appar som du kan installera. Om du inte har några registrerade enheter ännu visas ett meddelande om att **vi inte kan visa några appar**. Du kan fortsätta genom att välja __Mina enheter__.

 ![En skärmbild av webbportalens landningssida och meddelandet om att inga appar kan installeras ännu. Knappen Mina enheter visas nedanför.](./media/macOS_enroll_001_landing_page.png)

4. På sidan __Mina enheter__ visas antingen en lista med registrerade enheter eller bara ett popup-meddelande. Det beror på om du redan har registrerat en enhet, ett macOS eller annat. Om du vill registrera en enhet som inte finns i listan väljer du meddelandet som ser ut ungefär så här: __Identifiera enheten i listan genom att trycka på den. Du kan också trycka här för att registrera din enhet om den inte visas i listan__.

  ![En skärmbild på sidan Min enhet med ett par oidentifierade enheter ovanför popup-meddelandet om att registrera enheter som inte finns i listan eller identifiera oidentifierade enheter.](./media/macOS_enroll_002_tap_here_banner.png)

5. Ett popup-fönster visas med en kort beskrivning av varför du ska __identifiera eller registrera den här enheten__. Granska det och klicka sedan på __Registrera__ för att fortsätta.

 ![Identifiera eller registrera den här macOS-enheten](./media/macOS_enroll_003_IDenroll_popup.png)

6. Ett andra popup-fönster visas med en kort beskrivning av vad som händer när du __registrerar enheten__. Granska det och klicka sedan på __Installera__ för att fortsätta.

 ![Registrera den här macOS-enheten](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > Intune behöver åtkomst till datorn för att se till att enheten är säker nog för att få åtkomst till organisationens resurser. Ta reda på [vad som händer när du registrerar din enhet i Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md).

7. __Systeminställningar__ öppnas och frågar om du vill __Installera "Hanteringsprofil"?__ Klicka på __Installera__ för att fortsätta eller se mer information genom att klicka på __Visa profil__.

 ![Installera Hanteringsprofil](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. Ett macOS popup-fönster visas. Bekräfta att du vill göra ändringar genom att ange datorns __Användarnamn__ och __Lösenord__, klicka på __OK__. Detta installerar hanteringsprofilen på datorn.

 ![Installerings-popup för macOS-profil](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. Du kan se vissa ytterligare meddelanden från din Mac med mer information om profilen eller om du är säker på att du vill __Installera__. Klicka på __Fortsätt__ och __Installera__ för att fortsätta. När installationen är klar, kan du se din nyligen installerade __Hanteringsprofil__ i listan över __Enhetsprofilerna__.

 ![macOS-profilen installerad](./media/macOS_enroll_007_sysprefs_installed_profile.png)

Behöver du fortfarande hjälp? Kontrollera med din IT-administratör. Du hittar kontaktinformationen på [Företagsportalens webbplats](http://portal.manage.microsoft.com).

