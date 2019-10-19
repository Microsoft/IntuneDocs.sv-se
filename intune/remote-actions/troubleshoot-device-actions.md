---
title: Felsöka enhetsåtgärder i Microsoft Intune – Azure | Microsoft Docs
description: Få hjälp med att felsöka problem med enhets åtgärder.
keywords: ''
author: erikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: ''
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96f6dc3d1a8f8589395cf49b3bb934adadf437a4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508508"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Felsöka enhets åtgärder i Intune

Microsoft Intune har många åtgärder som hjälper dig att hantera enheter. Den här artikeln innehåller svar på några vanliga frågor som kan hjälpa dig att felsöka enhets åtgärder.

## <a name="bypass-activation-lock-action"></a>Åtgärd för att kringgå aktiveringslås

### <a name="i-clicked-the-bypass-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Jag klickade på åtgärden "kringgå Aktiveringslås" i portalen men inget hände på enheten.
Detta är förväntat. När du startar åtgärden kringgå Aktiveringslås begär Intune en uppdaterad kod från Apple. Du anger koden manuellt i fältet lösen ord när enheten finns på Aktiveringslås skärmen. Den här koden är bara giltig i 15 dagar, så se till att klicka på åtgärden och kopiera koden innan du skickar rensningen.

### <a name="why-dont-i-see-the-bypass-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Varför visas inte koden för att kringgå Aktiveringslås i bladet maskin varu översikt på min iOS-enhet?
De mest sannolika orsakerna är:
- Koden har upphört att gälla och rensats från tjänsten.
- Enheten övervakas inte med enhets begränsnings principen för att tillåta Aktiveringslås.

Du kan kontrol lera koden i Graph Explorer med följande fråga:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-bypass-activation-lock-action-greyed-out-for-my-ios-device"></a>Varför är åtgärden kringgå Aktiveringslås nedtonad för min iOS-enhet?
De mest sannolika orsakerna är: 
- Koden har upphört att gälla och rensats från tjänsten.
- Enheten övervakas inte med enhets begränsnings principen för att tillåta Aktiveringslås.

### <a name="is-the-bypass-activation-lock-code-case-sensitive"></a>Är Skift läges känsligt att kringgå Aktiveringslåss kod?
Nej. Och du behöver inte ange bindestrecken.

## <a name="remove-devices-action"></a>Åtgärden ta bort enheter

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Hur gör jag för att se vem som startade en borttagning/rensning?
Gå till **Intune**  > **enheter**  > **enhets åtgärder** > kontrol lera kolumnen **initierad av** .
Om du inte ser någon post är den mest sannolika personen som har initierat åtgärden är användare av enheten. De använde förmodligen Företagsportal app-eller portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Varför avinstallerades inte programmet när det har tagits ur bruk?
Eftersom det inte ansågs något hanterat program. I det här sammanhanget är ett hanterat program ett program som har installerats med hjälp av Intune-tjänsten. Du måste bland annat:
- Appen distribuerades vid behov
- Appen distribuerades som tillgänglig och installerades av slutanvändaren från Företagsportal-appen.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Varför är rensningen av arbets profilen i Android för företag?
Det här beteendet är förväntat. Google tillåter inte att fabriks återställning av arbets profil enheter från MDM-providern.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Varför kan jag logga in i mina Office-appar igen när enheten har dragits tillbaka?
Eftersom en enhet dras tillbaka återkallar inte åtkomsttoken. Du kan använda principer för villkorlig åtkomst för att minimera det här tillståndet.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Hur kan jag övervaka en borttagnings-/rensnings åtgärd när den har utfärdats?
Gå till **Intune** - > **enheter**  > **enhets åtgärder**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Varför visas ibland rensningar som väntar på obestämd tid?
Enheter rapporterar inte alltid statusen tillbaka till Intune-tjänsten innan återställningen startades. Därför visas åtgärden som väntande. Om du har bekräftat att åtgärden lyckades tar du bort enheten från tjänsten.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Vad händer om jag startar en borttagning/rensning på en offline-enhet eller en enhet som inte kommunicerat med tjänsten på ett tag?
Enheten kommer att befinna sig i **vänte läge/rensning** tills MDM-certifikatet upphör att gälla. MDM-certifikatet varar i ett år från registreringen och förnyas automatiskt varje år. Om enheten checkar in innan MDM-certifikatet upphör att gälla, kommer det att dras tillbaka/rensas. Om enheten inte checkar in innan MDM-certifikatet går ut kan den inte checka in till tjänsten. 180 dagar efter att MDM-certifikatet upphör att gälla tas enheten bort automatiskt från Azure Portal.


## <a name="reset-passcode-action"></a>Återställ lösen ords åtgärd

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Varför är åtgärden Återställ lösen ord nedtonad på min Android Device admin-registrerade enhet?
Google har tagit bort funktionen för återställning av lösen ord i enhetens administrations-API (gäller Android version 7,0 eller högre enheter) för att bekämpa utpressnings tro.

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Varför får jag ett meddelande om att det inte stöds när jag utfärdar en återställning av lösen ord till min Android 8,0 eller senare arbets profil som är registrerad som en registrerad enhet?
Eftersom reset-token inte har Aktiver ATS på enheten. Så här aktiverar du RESET-token:
1. Du måste kräva ett lösen ord för arbets profilen i konfigurations principen.
2. Slutanvändaren måste ange ett lämpligt lösen ord för arbets profilen.
3. Slutanvändaren måste acceptera den sekundära prompten för att tillåta återställning av lösen ord.
När de här stegen har slutförts bör du inte längre få det här svaret.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Varför uppmanas jag att ange ett nytt lösen ord på min iOS-enhet när jag utfärdar åtgärden ta bort lösen ord?
Eftersom en av dina efterlevnadsprinciper kräver ett lösen ord.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](../fundamentals/get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
