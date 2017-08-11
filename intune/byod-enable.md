---
title: Aktivera BYOD med Microsoft Intune
description: "Generella steg för att konfigurera Intune för en BYOD-lösning (Bring-Your-Own Device) för din organisation."
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 07/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: vlpetros
ms.suite: ems
ms.openlocfilehash: 8684ea31420edd836038dc9337bd8bdf56e78ba6
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="enable-byod-with-intune"></a>Aktivera BYOD med Intune

Det här avsnittet beskriver de generella steg som du följer för att konfigurera Intune för en BYOD-lösning (Bring-Your-Own Device) för din organisation. Uppgifterna är indelade i tre processer och avsnittet innehåller även länkar till ytterligare instruktionsartiklar.

Arbetsflödet är indelat i följande tre processer. Du kan anpassa olika aspekter av varje process så att de uppfyller organisationens behov.

-   **[Registrera enheter och kontrollera efterlevnad](#enroll-devices-and-check-for-compliance)** beskriver hur användarna kan registrera sina personliga enheter för hantering med Intune. Intune kan hantera iOS-, Mac OS-, Android- och Windows-enheter. Det här avsnittet beskriver också hur du distribuerar principer till enheter och ser till att de uppfyller grundläggande säkerhetskrav.

- **[Ge åtkomst till företagsresurser](#provide-access-to-company-resources)** beskriver hur du enkelt och säkert kan ge användare åtkomst till företagsresurser. Du gör detta genom att distribuera profiler till hanterade enheter. Det här avsnittet beskriver också hur du hanterar volyminköpta appdistributioner med Intune.

-   **[Skydda företagsdata](#protect-company-data)** beskriver hur du ger villkorlig åtkomst till företagsresurser, förhindrar dataförlust och tar bort företagsappar och data från enheter när de inte längre behövs för arbetet eller när de tappats bort eller blivit stulna.

[![Översiktligt arbetsflödesdiagram för BYOD-implementering med Microsoft Intune](./media/workflow-diagram-for-byod.png)](./media/workflow-diagram-for-byod.png)

<!--- > <sup>You can download this infographic at https://gallery.technet.microsoft.com/Infographic-Management-3644ae41.</sup> --->

## <a name="before-you-begin"></a>Innan du börjar
Innan användarna kan registrera enheter måste du förbereda själva Intune-tjänsten. Det gör du genom att [tilldela licenser till användare](licenses-assign.md) och [ange utfärdaren för hantering av mobila enheter](mdm-authority-set.md).

När du ändå håller på bör du även passa på att [anpassa företagsportalen](company-portal-customize.md). Lägg till företagsinformation och ge användarna tillgång till supportinformation. Allt detta gör att dina användare får en bra registrerings- och supportupplevelse. Du kan också skapa [användningsvillkor](terms-and-conditions-create.md) som användarna måste godkänna före registrering, eller [enhetsbegränsningar](enrollment-restrictions-set.md) som anger vilka plattformar som du stöder.

## <a name="enroll-devices-and-check-for-compliance"></a>Registrera enheter och kontrollera kompatibilitet

När du har förberett Intune-tjänsten måste du uppfylla de olika registreringskraven för de olika enhetstyper som du vill hantera. Processen för att registrera enheter för hantering är enkel, men varierar en aning beroende på enhetstyp.

-   **iOS- och Mac-enheter** Du måste [skaffa ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md) för att registrera iPad-, iPhone- eller Mac OS-enheter. När du har överfört MDM-pushcertifikatet till Intune kan användarna [registrera iOS-enheter](/intune-user-help/enroll-your-device-in-intune-ios) med hjälp av företagsportalappen, och använda webbplatsen för företagsportalen för att [registrera Mac OS X-enheter](/intune-user-help/enroll-your-device-in-intune-macos).

-   **Android-enheter** Du behöver inte göra något för att förbereda Intune-tjänsten för registreringen av Android-enheter. Användarna behöver bara [registrera sina Android-enheter](/intune-user-help/enroll-your-device-in-intune-android) i hanteringen med företagsportalappen som är tillgänglig från Google Play.

-   **Windows Phone-enheter och datorer** Windows-enheter kan registreras med ytterligare konfiguration. Förenkla användarnas upplevelse genom att aktivera automatisk registrering för Windows 10-datorer och mobila Windows 10-enheter i Azure Active Directory (AD) Premium. Om du inte har Azure AD Premium eller om du behöver stöd för Windows 8.1 kan du skapa [ett DNS-alias för registreringsservern](windows-enroll.md#enable-windows-enrollment-without-azure-ad-premium) för att göra registreringen enklare.


### <a name="make-sure-that-managed-devices-meet-basic-security-requirements"></a>Kontrollera att hanterade enheter uppfyller grundläggande säkerhetskrav

När användare registrerar sina enheter för hantering måste IT-avdelningen kontrollera att de enheter som används för att komma åt företagsappar och data uppfyller grundläggande säkerhetskrav. Dessa regler kan till exempel kräva att en PIN-kod används för att komma åt enheter samt kryptering av data som lagras på enheter. En uppsättning med sådana regler kallas för en [efterlevnadsprincip](device-compliance.md).

När du [distribuerar en efterlevnadsprincip](device-compliance-get-started.md) till en användare kontrollerar Intune alla enheter som användaren har hanterat med Intune för att se om de uppfyller de grundläggande säkerhetskraven som du har definierat som en del av din BYOD-princip. När en enhets principefterlevnad har utvärderats skickas enhetens status till Intune. I vissa fall kan användare uppmanas att åtgärda inställningar, till exempel deras PIN-kod eller enhetskryptering. Andra gånger meddelar företagsportalappen bara användaren om eventuella inställningar som inte uppfyller principen.

## <a name="provide-access-to-company-resources"></a>Ge åtkomst till företagsresurser

Det första som de flesta anställda vill ha på sina mobila enheter är tillgång till företagets e-post och dokument. Och de förväntar sig att kunna konfigurera detta utan att gå igenom komplexa steg och utan att behöva ringa supportavdelningen. Intune gör det enkelt för dig att [skapa och distribuera e-postinställningar](email-settings-configure.md) för interna e-postappar som är förinstallerade på mobila enheter.


> [!NOTE]
> Intune har stöd för konfiguration av e-postprofiler i Android for Work för e-postapparna Gmail och Nine Work som finns i Google Play Store.

Intune hjälper dig också att styra och skydda åtkomsten till lokala företagsdata när användarna arbetar på en annan plats. Intunes [Wi-Fi-](wi-fi-settings-configure.md), [VPN-](vpn-settings-configure.md) och e-postprofiler fungerar tillsammans för att tillåta åtkomst till filer och resurser som användarna behöver för att utföra sitt arbete, oavsett var de är. Företagets webbprogram och tjänster som finns lokalt går också att komma åt på säkert sätt och skydda med Azure Active Directory-programproxyn och villkorlig åtkomst.

### <a name="manage-volume-purchased-apps"></a>Hantera volyminköpta appar
Med Intune är det enkelt att:
* Importera volymlicensinformation från appbutiker
* Spåra hur många licenser som du har använt
* Förhindra att användare installerar fler kopior av appen än du äger
* [Leverera Store-appar till hanterade enheter](apps-deploy.md)
* Rikta appar till ohanterade enheter via webbplatsen för företagsportalen

Med Intune kan du även hantera och distribuera appar som du har köpt i större volymer från App Store för iOS-enheter och Windows Store för företag. Det här hjälper dig minska den administrativa kostnaden för att spåra volyminköpta appar.

> [!TIP]
> Du kan [konfigurera enkel inloggning (SSO) med Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Med enkel inloggning kan användarna logga in i appar med de domänanvändarnamn och domänlösenord som de använder lokalt. Du kan också [ge Internetbaserad åtkomst till webbappar som finns lokalt](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) med hjälp av Azure Active Directory Application Proxy.

-   [Hantera volyminköpta appar för iOS-enheter](vpp-apps-ios.md). Du kan köpa flera licenser för iOS-appar genom [Apples volyminköpsprogram för företag](http://www.apple.com/business/vpp/). Du måste skapa ett Apple VPP-konto från Apples webbplats och ladda upp Apple VPP-token till Intune. Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

-   [Hantera appar som du har köpt från Windows Store för företag](windows-store-for-business.md). I [Windows Store för företag](https://www.microsoft.com/business-store) kan du söka efter och köpa appar för din organisation, separat eller i volym. Genom att ansluta butiken till Intune kan du hantera volyminköpta appar från Intune-portalen.

## <a name="protect-company-data"></a>Skydda företagsdata

Intune skyddar företagets data via flera tekniklager. I identitetslagret används villkorlig åtkomst för att skydda åtkomsten till tjänster. Villkorlig åtkomst tillåter endast att hanterade och kompatibla enheter kommer åt företagsresurser. I klientprogramlagret används hantering av mobilprogram (MAM) för att skydda mot dataförlust.  Appskyddsprinciper förhindra att data flyttas till appar eller lagringsplatser som inte är skyddade. Med dessa principer kan du även rensa företagsdata om en enhet har tappats bort eller blivit stulen.

### <a name="enforce-conditional-access-to-company-resources"></a>Framtvinga villkorlig åtkomst till företagsresurser

Du kan kombinera efterlevnadsprinciper med [principer för villkorlig åtkomst](device-compliance.md) för att kontrollera om enheterna uppfyller de grundläggande säkerhetskraven som definierats i BYOD-principen. Om en enhet inte uppfyller kraven tillämpas regler och åtkomsten nekas tills enheten uppfyller kraven i principen. Detta säkerställer att endast hanterade och kompatibla enheter kan komma åt företagsdata från tjänster som Exchange ([Exchange On-premises](exchange-connector-install.md) eller [Exchange Online](conditional-access-exchange-create.md)), SharePoint Online, Skype för företag – Online och andra.
<!---first link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)
third link was (https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune). check with Andre--->

> [!IMPORTANT]
> Principer för villkorlig åtkomst fungerar inte om det inte finns en konfigurerad efterlevnadspolicy som kan användas för att verifiera efterlevnad.

### <a name="prevent-data-loss-of-company-data-with-application-protection-policies"></a>Förhindra dataförlust av företagsdata med principer för programskydd

Med Intunes appskyddsprinciper kan du välja hur dina data kan nås: med eller utan enhetsregistrering. Den här flexibiliteten gör att du kan skydda företagsdata så att användare kan komma åt företagsresurser på ett säkert sätt även om de inte registrerar sina enheter i Intune.

Du kan använda [Intunes principer för appskydd](app-protection-policies.md) för att hjälpa att skydda företagsdata som dina användares iOS- och Android-enheter har åtkomst till. När du använder de här principerna på appnivå kan du styra hur företagsdata används och delas av anställda även om själva enheten inte hanteras av Intune

Använd [Windows Information Protection (WIP) principer](app-protection-policies-configure-windows-10.md) för att göra detsamma för hanterade Windows 10 enheter. Dessa principer fungerar utan att påverka de anställdas upplevelse. De kräver inga ändringar i din nätverksmiljö eller andra appar.

### <a name="wipe-company-data-while-leaving-personal-data-intact"></a>Rensa företagsdata och lämna personlig data intakt

Om en enhet inte längre behövs i arbetet, om den ska användas för ett nytt syfte eller om den bara är borttappad, kan du ta bort företagsappar och företagsdata från den. För att göra det kan du använda Intunes funktioner för selektiv rensning och fullständig rensning. Användarna kan också fjärrensa sina egna personligt ägda enheter från Intunes företagsportal om enheterna är registrerade i Intune.

Med en [fullständig rensning](devices-wipe.md) återställs enheten till fabriksinställningarna, och användardata och inställningar tas bort. Med en [selektiv rensning](devices-wipe.md#selective-wipe) tas endast företagsdata bort från enheten, men användarnas personliga data förblir intakta.

När processen påbörjas inleder enheten genast den selektiva rensningen för att tas bort från hanteringen. När processen är klar har alla företagsdata raderats och enhetsnamnet har tagits bort från Intune-portalen. Här upphör enhetens hanteringslivscykel.
