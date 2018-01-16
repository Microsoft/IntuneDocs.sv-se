---
title: Aktivera registrering av enheter
description: "Ange utfärdare för hantering av mobila enheter och aktivera registrering av iOS-, Windows-, Android- och Mac-enheter."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ab0dfd5abc1cf2f1a0d8576e9072509ba51b4e57
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/12/2018
---
# <a name="enable-enrollment-for-mobile-devices"></a>Aktivera registrering av mobila enheter

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver hur en Intune-administratör kan aktivera registreringen av mobila enheter. Hjälp med att använda Intune på din telefon finns i [Använda hanterade enheter för att få arbetet gjort](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions).

Om du vill konfigurera hantering av mobila enheter med Intune måste du först ange *hanteringsutfärdare för mobila enheter*, som identifierar den tjänst som kan hantera enheter som är kopplade till ditt konto. I den här vägledningen antar vi att du använder tjänsten Intune i stället för System Center Configuration Manager. När utfärdare för Hantering av mobila enheter har angetts kan du aktivera hantering för enhetsplattformar och registrera dina enheter med företagsportalappen.

## <a name="enable-device-enrollment"></a>Aktivera registrering av enheter

1. **Gör Intune till din utfärdare för hantering av mobila enheter**. I [Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Admin** > **Hantering av mobila enheter** och väljer sedan **Ange utfärdare för Hantering av mobila enheter** under **Uppgifter**.  

2. Klicka på **Ja** i dialogrutan Ange utfärdare för Hantering av mobila enheter.

    ![Administrationskonsolen. Ange MDM till Intune](../media/intune-mdm-authority.png)

## <a name="choose-how-to-enroll-devices"></a>Välj hur du vill registrera enheter

Intune kan hantera enheter på en mängd olika sätt beroende på företagets krav. BYOD-enheter (Bring your own device) som ägs av företag, CYOD-enheter (choose your own device) och helskärmsläge är bara några tillgängliga registreringsscenarier.

Följ de här stegen för att [välja hur du registrerar enheter](choose-how-to-enroll-devices1.md).

## <a name="enable-mdm-for-your-device-platform"></a>Aktivera MDM för din enhetsplattform
Registreringen måste aktiveras för iOS, Mac och Android för arbetsenheter som upprättar en relation mellan plattformsprovidern och din Intune-klient. Windows- och Android-enheter kräver inte ytterligare steg, men för Windows-enheter du kan förenkla registrering av enheter för dina användare genom att skapa en särskild DNS-registerpost.

Aktivera registrering av enheter för den enhetsplattform som du vill hantera. Beroende på din plattform behövs olika krav:

- [iOS och macOS](/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [Windows 10 och Windows Phone](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune)
- [Windows-dator](/intune-classic/deploy-use/manage-windows-pcs-with-microsoft-intune) (Intune-programvaruklient)
- [Android for Work](/intune-classic/deploy-use/set-up-android-for-work)

När registreringen är aktiverad kan användare ladda ned företagsportalappen till sin enhet och slutföra registreringen för enheten.

### <a name="enable-company-owned-device-enrollment"></a>Aktivera registrering av företagsägda enheter
Du kan också aktivera olika scenarier för [registrering av företagsägda enheter](/intune-classic/deploy-use/manage-corporate-owned-devices) inklusive:
- [Apples program för enhetsregistrering (Device Enrollment Program)](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
- [Apple Configurator-registrering med installationsassistenten](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
- [Apple Configurator – direkt registrering](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
- [Hanterare av enhetsregistrering](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

### <a name="next-steps"></a>Nästa steg
Gratulerar! Du har slutfört det sista steget i *snabbstartsguiden för Intune*. Nu när den första konfigurationen är klar kan du välja att aktivera ytterligare MDM-funktioner.

>[!div class="step-by-step"]
>[&larr; **Registrera enheter**](.\start-with-a-paid-subscription-to-microsoft-intune-step-8.md) [**Åtgärder efter konfigurering** &rarr;](.\post-configuration-tasks.md)  
