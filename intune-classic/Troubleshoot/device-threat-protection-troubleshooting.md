---
title: Felsöka Lookout-integrering
description: I det här avsnittet beskrivs felsökning av problem som ofta uppstår vid Lookout-integrering
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ec20d87da48fb52207d839da0753eb05524569af
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2018
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Felsöka Lookout-integrering med Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Det här avsnittet beskriver några vanliga problem som kan uppstå vid installation av Lookout mobilt skydd (MTP).

**Inloggningsfel**

## <a name="403-errors"></a>403-fel
Ett 403-fel visas när du loggar in i [Lookout MTP-konsolen](https://aad.lookout.com):  **you are not authorized to access the service** (du har inte åtkomsträttigheter till den här tjänsten). Detta kan hända när användarnamnet som du angav inte är medlem i den Azure Active Directory-grupp (Azure AD) som är konfigurerad för att ha åtkomst till Lookout MTP.

Lookout MTP tillåter endast att användare från en konfigurerad Azure AD-grupp får åtkomst till tjänsten. Om du vill fastställa vilken grupp som är konfigurerad att ha åtkomst till Lookout MTP kontaktar du Lookout-supporten:

* E-post: enterprisesupport@lookout.com
* Logga in på [MTP Console](http://aad.lookout.com) (MTP-konsolen), och gå till **support**-modulen.
* Gå till: https://enterprise.support.lookout.com/hc/requests och gör en supportbegäran.

## <a name="unable-to-sign-in"></a>Det går inte att logga in
Du får följande fel när den globala Azure AD-administratöranvändaren inte har godkänt den inledande Lookout-installationen.

![skärmbild av inloggningsskärmen för Lookout som visar inloggningsfelet](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

För att lösa problemet måste en global administratör logga in på https://aad.lookout.com/les?action=consent och godkänna uppmaningen att starta installationen. Mer information finns i avsnittet [Set up your subscription with Lookout MTP](../deploy-use/setup-your-lookout-mtd-subscription.md) (Konfigurera din prenumeration med Lookout MTP)

**Problem med enhetsstatus**

## <a name="device-missing-from-lookout-device-list"></a>Enheten saknas i Lookout-enhetslistan

Detta kan inträffa i något av följande scenarier:
* Enhetsanvändaren finns inte i den **registreringsgrupp** som anges i **Lookout MTP-konsolen**.  I [Lookout-konsolen](http://aad.lookout.com) går du till **System** > **Intune Connector** > **Enrollment Management** (Registreringshantering).  Granska de Azure AD-grupper som har konfigurerats för registrering och verifiera att enhetsanvändaren ingår i en av Azure AD-grupperna.  När en användare har lagts till i registreringsgruppen kan det ta upp till det konfigurerade avsökningsintervallet, standardinställningen är fem minuter, innan enheten visas i **Enheter**-modulen i Lookout MTP-konsolen.
* Om enheten inte stöds av Lookout MTP.  Enheter som inte stöds kommer visas i sektionen **Hanterade enheter** under anslutningsinställningarna i Lookout MTP-konsolen.

### <a name="device-reported-as-pending"></a>Enheten rapporteras som **väntar**

En enhet visas som **väntar** om användaren inte har öppnat Lookout for Work-appen och tryckt på knappen **Aktivera**. Mer information om enhetsaktivering med Lookout for Work-appen finns i [Du uppmanas att installera Lookout for Work på din Android-enhet](http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android) eller [Du uppmanas att installera Lookout for Work på din iOS-enhet](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-ios)

## <a name="device-whos-active-but-has-no-device-id"></a>Enhet som är aktiv, men inte har något enhets-ID
I Lookout MTP-konsolen finns inte enhetsanvändaren i registreringsgruppen om en aktiv enhet inte har ett enhets-ID. En enhet kan hamna i det här tillståndet om användaren tas bort från registreringsgruppen eller om registreringsgruppen har tagits bort.

I [Lookout-konsolen](http://aad.lookout.com) går du till **System** > **Intune Connector** > **Enrollment** (Registrering) och granskar inställningarna.  Granska Azure AD-grupperna och verifiera att enhetsanvändaren ingår i en av Azure AD-grupperna.

När en enhet är i det här tillståndet kan Lookout fortsätter att meddela användaren om eventuella hot som identifieras, men det skickar inte någon information om hotet till Intune.

## <a name="device-reported-as-disconnected"></a>Enheten rapporteras som **frånkopplad**

**Frånkopplad** innebär att enheten inte har synkroniserats med Lookout MTP under det konfigurerade intervallet, 30 dagar som standard med 7 dagar som lägst. Antingen företagsportalappen eller Lookout for Work-appen saknas på enheten. Att installera om apparna bör lösa problemet. När användaren öppnar Lookout for Work och aktiverar appen synkroniseras enheten med Lookout MTP och Intune igen.

### <a name="forcing-a-device-sync"></a>Tvinga en enhetssynkronisering
Administratören kan välja enheten och välja att ta bort den från **Enheter**-modulen i Lookout MTP-konsolen.   Nästa gång ägaren till enheten öppnar Lookout for Work-appen och trycker på **Aktivera** kommer enhetens tillstånd att göra en fullständig synkronisering.

## <a name="device-has-a-new-user"></a>Enheten har en ny användare
Du bör rensa enheten och be den nya användaren att registrera sig.  Markera enheten, högerklicka och välj **Ta bort/Rensa** i [Intune-administratörskonsolen](https://manage.microsoft.com) för att ta bort enheten från hanteringen. När du har tagit bort enheten kan du radera den.

![skärmbild som visar enhetsmodulen i Intune-administratörskonsolen och alternativet Ta bort/Rensa](../media/mtp/mtp-retire-device-intune-console.png)

Du kan även gå till **Enheter**-modulen i [Lookout-konsolen](http://aad.lookout.com) och välja **Ta bort**.

Om den nya användaren finns i en av Lookout MTP-registreringsgrupperna kommer enheten att visas när Azure AD kopplar enheten till den nya användaren.

## <a name="compliance-remediation-workflows"></a>Arbetsflöden för reparation av efterlevnadsproblem
- [Du uppmanas att installera Lookout for Work på din Android-enhet]( http://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)
- [Du måste åtgärda ett hot som Lookout for Work har hittat på din Android-enhet](http://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [Du måste åtgärda ett hot som Lookout for Work har hittat på din iOS-enhet](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>Se även
[Konfigurera din prenumeration med Lookout MTP](/intune-classic/deploy-use/set-up-your-subscription-with-lookout-mtp)
