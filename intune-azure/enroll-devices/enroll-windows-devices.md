---
title: Registrera Windows-enheter
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Aktivera hantering av mobila enheter (MDM) för Windows-enheter."
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 3c764b269916ae1a9b076617842eb26d7fd13bab
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-windows-devices"></a>Registrera Windows-enheter

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Det här avsnittet hjälper IT-administratörer att förenkla Windows-registrering för sina användare.  Windows-enheter kan registreras utan några ytterligare steg, men du kan göra registreringen enklare för användare.

Enheter som kör Windows 10 Creator-uppdateringen och är domänanslutna till Azure Active Directory, har nu stöd för fleranvändarhantering med Intune. Det innebär att när olika standardanvändare loggar in på enheten med sina autentiseringsuppgifter för Azure AD, får de alla appar och principer som har tilldelats till deras användarnamn. Användarna kan för närvarande inte använda företagsportalen för självbetjäningsscenarier som att installera appar.

Två saker som innebär att du kan förenkla Windows-enhetsregistreringen:

- **Använder du Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) ingår i Enterprise Mobility + Security och andra licensieringsplaner.
- **Vilka versioner av Windows-klienter ska registreras?** <br>Windows 10-enheter kan registreras automatiskt genom att lägga till ett arbets- eller skolkonto. Tidigare versioner måste registreras via företagsportalappen.

||**Azure AD Premium**|**Övriga AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatisk registrering](#enable-windows-10-automatic-enrollment) |[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|
|**Tidigare Windows-versioner**|[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|[Användarregistrering](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Aktivera Windows-registrering utan Azure AD Premium
Du kan låta användarna registrera sina enheter utan automatisk registrering i Azure AD Premium. När du tilldelar licenser kan användarna registrera sig när de har lagt till sina arbetskonton till sina egna enheter, eller anslutit sina företagsägda enheter till din Azure AD. Om du skapar ett DNS-alias (CNAME-posttyp) blir det enklare för användarna att registrera sina enheter. Om du skapar DNS CNAME-resursposter kan användarna ansluta till och registrera enheter i Intune utan att ange Intune-servernamnet.

**Steg 1: Skapa CNAME-poster** (valfritt)<br>
Skapa CNAME-DNS-resursposter för företagsdomänen. Om ditt företags webbplats till exempel är contoso.com så skapar du en CNAME-post i DNS som omdirigerar EnterpriseEnrollment.contoso.com till enterpriseenrollment-s.manage.microsoft.com.

Det är valfritt att skapa CNAME DNS-poster, men det blir enklare för användarna om du gör det. Om ingen CNAME-post hittas, uppmanas användarna att manuellt ange MDM-servernamnet, enrollment.manage.microsoft.com.

|Typ|Värdnamn|Pekar på|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|

Om du har fler än ett UPN-suffix måste du skapa en CNAME-post för varje domännamn och leda var och en till EnterpriseEnrollment-s.manage.microsoft.com. Om användare på Contoso till exempel använder name@contoso.com, men även använder name@us.contoso.com och name@eu.constoso.com som e-post/UPN måste Contoso DNS-administratören skapa följande CNAME-poster.

|Typ|Värdnamn|Pekar på|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 timme|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 timme|

`EnterpriseEnrollment-s.manage.microsoft.com` – Stöder en omdirigering till Intune-tjänsten med domänidentifiering från e-postens domännamn

Distributionen av DNS-poständringarna kan ta upp till 72 timmar. Du kan inte verifiera DNS-ändringen i Intune förrän DNS-posten har spridits.

**Steg 2: Verifiera CNAME** (valfritt)<br>
I Azure Intune-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Windows-registrering** på Intune-bladet. Ange webbadressen till företagswebbplatsens verifierade domän i rutan **Ange ett verifierat domännamn** och välj sedan **Testa automatisk identifiering**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Berätta för användare hur de ska registrera Windows-enheter
Berätta för användarna hur de ska registrera sina Windows-enheter och vad de kan förvänta sig när de har registrerat sig för hantering. Registreringsinstruktioner för slutanvändare finns i [Registrera din Windows-enhet i Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Du kan även berätta för användarna [vad IT-administratören kan se på enheten](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Mer information om slutanvändarnas aktiviteter finns i [Resurser om slutanvändarens upplevelse med Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

