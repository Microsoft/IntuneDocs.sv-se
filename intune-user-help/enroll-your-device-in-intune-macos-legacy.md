---
title: "Registrera en äldre macOS-enhet i Intune | Microsoft Docs"
description: Beskriver hur du registrerar en macOS-enhet i Intune
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope: User help
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: f46d9cc4fad54415aeea8deaf1b8daa0c274c1dc
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2017
---
# <a name="enroll-your-legacy-macos-device-in-intune"></a>Registrera en äldre macOS-enhet i Intune

De här instruktionerna fungerar för macOS-enheter på OS X Yosemite 10.10 och äldre versioner. Du hittar anvisningar för att registrera macOS-enheter på nyare versioner av macOS [här](enroll-your-device-in-intune-macos-cp.md).

Genom att få åtkomst till din organisations appar, data och resurser är det möjligt för dig att göra ditt jobb. Om du använder en macOS-enhet på arbetet, innebär det installation av en __Hanteringsprofil__. Detta är bara en fil som har konfigurerats av företagets support och som läser in inställningar och åtkomstinformation till din Mac. Vill du veta mer? Ta reda på [vad som händer om du installerar företagsportalappen och registrerar din enhet i Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

1. På din __Docka__, går du till __Safari__ och öppnar ett nytt fönster och öppnar sedan [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
2. Logga in på företagsportalens webbplats med ditt arbets- eller skolkonto.

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. När du har loggat in klickar du på **menyn** i det övre vänstra hörnet på sidan och väljer **Mina enheter**.

 ![En skärmbild av webbportalens landningssida och meddelandet om att inga appar kan installeras ännu. Knappen Mina enheter visas nedanför.](./media/macOS_enroll_001_landing_page.png)

4. På sidan __Mina enheter__ visas antingen en lista med registrerade enheter eller bara ett popup-meddelande. Det beror på om du redan har registrerat en enhet, ett macOS eller annat. Om du vill registrera en enhet som inte finns i listan väljer du meddelandet som ser ut ungefär så här: __Identifiera enheten i listan genom att trycka på den. Du kan också trycka här för att registrera din enhet om den inte visas i listan__. Om du inte har några registrerade enheter anger banderollen **Du har inga registrerade enheter. Registrera den här genom att trycka här.**

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

Vissa profiler kanske anger att de är **Inte verifierad**. Så länge de kommer från ditt företag är det normalt.

Behöver du fortfarande hjälp? Kontakta företagets support. Du hittar kontaktinformationen på [Företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
