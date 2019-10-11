---
title: Konfigurera registrering av Windows-enheter med Microsoft Intune
titleSuffix: ''
description: Konfigurera registrering av Windows-enheter.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 24ac01525a0fa1d08187fcb9a96297f2d1094890
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722325"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Konfigurera registrering av Windows-enheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Den här artikeln hjälper IT-administratörer att förenkla Windows-registrering för sina användare. När du har [konfigurerat Intune](../fundamentals/setup-steps.md) kan användarna registrera Windows-enheter genom att [logga in](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) med sina arbets- eller skolkonton.  

I egenskap av Intune-administratör kan du förenkla registreringen på följande sätt:

- [Aktivera automatisk registrering](#enable-windows-10-automatic-enrollment) (Azure AD Premium krävs)
- [CNAME-registrering](#simplify-windows-enrollment-without-azure-ad-premium)
- [Aktivera massregistrering](../windows-bulk-enroll.md) (Azure AD Premium och Windows Configuration Designer krävs)

Två saker som innebär att du kan förenkla Windows-enhetsregistreringen:

- **Använder du Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ingår i Enterprise Mobility + Security och andra licensieringsplaner.
- **Vilka versioner av Windows-klienterna kommer användarna att registrera?** <br>Windows 10-enheter kan registreras automatiskt genom att lägga till ett arbets- eller skolkonto. Tidigare versioner måste registreras via företagsportalappen.

||**Azure AD Premium**|**Övriga AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatisk registrering](#enable-windows-10-automatic-enrollment) |Användarregistrering|
|**Tidigare Windows-versioner**|Användarregistrering|Användarregistrering|

Organisationer som använder automatisk registrering kan också konfigurera [massregistrering av enheter](../windows-bulk-enroll.md) med hjälp av Windows Configuration Designer-appen.

## <a name="device-enrollment-prerequisites"></a>Krav för enhetsregistrering

Innan en administratör kan registrera enheter till Intune för hantering bör licenser redan ha tilldelats till administratörskontot. [Läs om hur du tilldelar licenser för enhetsregistrering](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Stöd för flera användare

Intune stöder flera användare på enheter som båda:

- kör Windows 10 Creators-uppdatering
- är anslutna till en Azure Active Directory domän.

När vanliga användare loggar in med sina autentiseringsuppgifter för Azure AD får de tillgång till de appar och principer som har tilldelats deras användarnamn. Endast enhetens [Primäranvändare](../remote-actions/find-primary-user.md) kan använda företagsportalen för självbetjäningsscenarier, som att installera appar och utföra enhetsåtgärder (ta bort, återställa). För delade Windows 10-enheter som inte har någon primär användare tilldelad kan företagsportalen fortfarande användas för att installera tillgängliga appar.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Förenkla Windows-registreringen utan Azure AD Premium
Du kan förenkla registreringen genom att skapa ett DNS-alias (CNAME-posttyp) som omdirigerar registreringsbegäranden till Intune-servrarna. I annat fall måste användare som försöker ansluta till Intune ange Intune-servernamnet under registreringen.

**Steg 1: Skapa CNAME** (valfritt)<br>
Skapa CNAME-DNS-resursposter för företagsdomänen. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.

Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

|Typ|Värdnamn|Pekar på|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 timme|

Om du har fler än ett UPN-suffix måste du skapa en CNAME-post för varje domännamn och leda var och en till EnterpriseEnrollment-s.manage.microsoft.com. Till exempel, användare på Contoso använder följande format som e-post/UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

Contosos DNS-administratör skapar följande CNAME-poster:

|Typ|Värdnamn|Pekar på|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|

`EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Ytterligare slutpunkter stöds men rekommenderas inte
EnterpriseEnrollment-s.manage.microsoft.com är det föredragna fullständiga domännamnet men det finns två andra slutpunkter som har används av kunder tidigare och stöds. Både EnterpriseEnrollment.manage.microsoft.com (utan -s) och manage.microsoft.com fungerar som mål för servern för automatisk identifiering men användare måste trycka på OK på ett bekräftelsemeddelande. Om du vill peka på EnterpriseEnrollment-s.manage.microsoft.commåste inte användaren göra det ytterligare bekräftelsesteget, så det är den rekommenderade konfigurationen

## <a name="alternate-methods-of-redirection-are-not-supported"></a>Alternativa metoder för omdirigering stöds inte
Det går inte att använda en annan metod än CNAME-konfigurationen. Till exempel stöds inte användning av en proxyserver för att omdirigera enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc till enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc eller manage.microsoft.com/EnrollmentServer/Discovery.svc.

**Steg 2: Verifiera CNAME** (valfritt)<br>
1. I [Intune på Microsoft Azure-portalen](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Windows-registrering** > **CNAME-validering**.
2. I rutan **Domän** skriver du företagets webbplats och väljer **Test**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Berätta för användare hur de ska registrera Windows-enheter
Berätta för användarna hur de ska registrera sina Windows-enheter och vad de kan förvänta sig när de har registrerat sig för hantering.

> [!NOTE]
> Slutanvändare måste ansluta till webbplatsen för företagsportalen via Microsoft Edge för att se Windows-appar som du tilldelat för specifika Windows-versioner. Andra webbläsare, inklusive Google Chrome, Mozilla Firefox och Internet Explorer har inte stöd för den här typen av filtrering.

Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). Du kan även be användarna granska [vad IT-administratören kan se på enheten](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Om du inte har aktiverat automatisk MDM-registrering, men du har Windows 10-enheter som har anslutits till Azure AD, visas två poster i Intune-konsolen efter registreringen. Du kan stoppa detta genom att se till att användare med Azure AD-anslutna enheter går till **Konton** > **Åtkomst för arbete eller skola** och **Anslut** med samma konto. 

Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](../fundamentals/end-user-educate.md).

## <a name="next-steps"></a>Nästa steg

- [Tänk på detta när du hanterar Windows-enheter med Intune i Azure](../fundamentals/intune-legacy-pc-client.md).
