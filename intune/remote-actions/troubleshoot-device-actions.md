---
title: Felsöka enhetsåtgärder i Microsoft Intune – Azure | Microsoft Docs
description: Få hjälp med att felsöka problem med enhetsåtgärder.
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
ms.openlocfilehash: 7d4517d89e3b7365834e904c815b30a362540906
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755603"
---
# <a name="troubleshoot-device-actions-in-intune"></a>Felsöka enhetsåtgärder i Intune

Microsoft Intune har många åtgärder som hjälper dig att hantera enheter. Den här artikeln innehåller svar på några vanliga frågor som kan hjälpa dig att felsöka enhetsåtgärder.

## <a name="disable-activation-lock-action"></a>Åtgärden Inaktivera aktiveringslås

### <a name="i-clicked-the-disable-activation-lock-action-in-the-portal-but-nothing-happened-on-the-device"></a>Jag klickade på åtgärden ”Inaktivera aktiveringslås” i portalen men inget hände på enheten.
Detta är förväntat. När du har startat åtgärden Inaktivera aktiveringslås begär Intune en uppdaterad kod från Apple. Du anger koden manuellt i fältet för lösenord när enheten finns på Aktiveringslås-skärmen. Den här koden är bara giltig i 15 dagar, så se till att klicka på åtgärden och kopiera koden innan du utfärdar rensningen.

### <a name="why-dont-i-see-the-disable-activation-lock-code-in-the-hardware-overview-blade-of-my-ios-device"></a>Varför ser jag inte koden för Inaktivera aktiveringslås på bladet för maskinvaruöversikt på min iOS-enhet?
De mest sannolika orsakerna är:
- Koden har upphört att gälla och rensats från tjänsten.
- Enheten övervakas inte med enhetsbegränsningsprincipen för att tillåta Aktiveringslås.

Du kan kontrollera koden i Graph Explorer med följande fråga:

```GET - https://graph.microsoft.com/beta/deviceManagement/manageddevices('deviceId')?$select=activationLockBypassCode.```

### <a name="why-is-the-disable-activation-lock-action-greyed-out-for-my-ios-device"></a>Varför är åtgärden Inaktivera aktiveringslås nedtonad för min iOS-enhet?
De mest sannolika orsakerna är: 
- Koden har upphört att gälla och rensats från tjänsten.
- Enheten övervakas inte med enhetsbegränsningsprincipen för att tillåta Aktiveringslås.

### <a name="is-the-disable-activation-lock-code-case-sensitive"></a>Är koden för Inaktivera aktiveringslås skiftlägeskänslig?
Nej. Och du behöver inte ange strecken.

## <a name="remove-devices-action"></a>Åtgärden Ta bort enheter

### <a name="how-do-i-tell-who-started-a-retirewipe"></a>Hur gör jag för att se vem som startade en borttagning/rensning?
I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) går du till **Innehavaradministratör** > **Granskningsloggar** > kontrollera kolumnen **Initierat av**.
Om du inte ser någon post är det mest sannolikt att den person som har initierat åtgärden är enhetens användare. De använde förmodligen Företagsportalappen eller portal.manage.microsoft.com.

### <a name="why-wasnt-my-application-uninstalled-after-using-retire"></a>Varför avinstallerades inte programmet när det hade tagits ur bruk?
Eftersom det inte ansågs vara ett hanterat program. I det här sammanhanget är ett hanterat program ett program som har installerats med hjälp av Intune-tjänsten. Du måste bland annat:
- Appen distribuerades som obligatorisk
- Appen distribuerades som tillgänglig och installerades av slutanvändaren från Företagsportalappen.

### <a name="why-is-wipe-grayed-out-for-android-enterprise-work-profile-devices"></a>Varför är rensningen nedtonad för Android Enterprise-arbetsprofilenheter?
Det här beteendet är förväntat. Google tillåter inte fabriksåterställning av arbetsprofilenheter från MDM-providern.

### <a name="why-can-i-sign-back-into-my-office-apps-after-my-device-was-retired"></a>Varför kan jag logga in i mina Office-appar igen efter det att enheten har dragits tillbaka?
Eftersom ett tillbakadragande av en enhet inte återkallar åtkomsttoken. Du kan använda principer för villkorlig åtkomst för att minimera det här tillståndet.

### <a name="how-can-i-monitor-a-retirewipe-action-after-it-was-issued"></a>Hur kan jag övervaka en borttagnings-/rensningsåtgärd när den har utfärdats?
I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) går du till **Innehavaradministratör** > **Granskningsloggar**.

### <a name="why-do-wipes-sometimes-show-as-pending-indefinitely"></a>Varför visas ibland rensningar som väntande på obestämd tid?
Enheter rapporterar inte alltid tillbaka sin status till Intune-tjänsten innan återställningen startats. Därför visas åtgärden som väntande. Om du har bekräftat att åtgärden lyckades tar du bort enheten från tjänsten.

### <a name="what-happens-if-i-start-a-retirewipe-on-an-offline-device-or-a-device-that-hasnt-communicated-with-the-service-in-a-while"></a>Vad händer om jag startar en borttagning/rensning på en offlineenhet eller en enhet som inte har kommunicerat med tjänsten på ett tag?
Enheten kommer att befinna sig i ett väntande tillstånd för **Ta ur bruk/rensa** tills MDM-certifikatet upphör att gälla. MDM-certifikatet varar i ett år från registreringen och förnyas automatiskt varje år. Om enheten checkar in innan MDM-certifikatet upphör att gälla, kommer den att dras tillbaka/rensas. Om enheten inte checkar in innan MDM-certifikatet upphör att gälla, kommer den inte att kunna checka in till tjänsten. 180 dagar efter att MDM-certifikatet upphör att gälla tas enheten bort automatiskt från Azure Portal.


## <a name="reset-passcode-action"></a>Åtgärden Återställ lösenord

### <a name="why-is-the-reset-passcode-action-greyed-out-on-my-android-device-admin-enrolled-device"></a>Varför är åtgärden Återställ lösenord nedtonad på min Android Device Admin-registrerade enhet?
För att bekämpa utpressningstrojaner har Google tagit bort funktionen för återställning av lösenord i enhetens administrations-API (gäller Android-enheter med version 7.0 eller senare).

### <a name="why-do-i-get-a-not-supported-message-when-i-issue-a-passcode-reset-to-my-android-80-or-later-work-profile-enrolled-device"></a>Varför får jag meddelandet Stöds inte när jag utfärdar en lösenordsåterställning till min enhet med Android 8.0 eller senare som är registrerad med en arbetsprofil?
Eftersom token för återställning inte har aktiverats på enheten. Så här aktiverar du token för återställning:
1. Du måste begära ett lösenord för arbetsprofilen i konfigurationsprincipen.
2. Slutanvändaren måste ange ett lämpligt lösenord för arbetsprofilen.
3. Slutanvändaren måste acceptera den sekundära prompten för att tillåta återställning av lösenord.
När de här stegen har slutförts bör du inte längre få det här svaret.

### <a name="why-am-i-prompted-to-set-a-new-passcode-on-my-ios-device-when-i-issue-the-remove-passcode-action"></a>Varför uppmanas jag att ange ett nytt lösenord på min iOS-enhet när jag utfärdar åtgärden Ta bort lösenord?
Eftersom en av dina efterlevnadsprinciper kräver ett lösenord.

## <a name="next-steps"></a>Nästa steg

Få [support från Microsoft](../fundamentals/get-support.md) eller använd [community-forumen](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
