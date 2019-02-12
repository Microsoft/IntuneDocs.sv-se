---
title: Sidan Klientorganisationsstatus i Microsoft Intune
titleSuffix: Microsoft Intune
description: Använd sidan Klientorganisationsstatus i Intune för att visa viktig klientorganisationsinformation utan att lämna Intune-portalen
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8bdb74c19e6b996bafc9284bfedaf0608fdf8fb
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834627"
---
# <a name="intune-tenant-status-page"></a>Sidan Klientorganisationsstatus i Intune
Använd sidan Klientorganisationsstatus som en centraliserad hubb för att hålla dig uppdaterad om viktig information om klientorganisationen, licenstillgänglighet och -användning, status för anslutningsprogram och viktiga meddelanden om Intune-tjänsten.  

Visa instrumentpanelen genom att gå till **Intune > Klientorganisationsstatus** i Azure-portalen.  Klientorganisationsstatus visas under **gruppen Hjälp och support**.  

Sidan är uppdelad i fyra områden:

## <a name="tenant-details"></a>Information om klientorganisation
Information om klientorganisation innehåller översiktlig information om klientorganisationen. Visa information som klientorganisationens namn och plats, MDM-utfärdare och klientorganisationens tjänstversionsnummer. Tjänstversionsnumret är en länk som öppnar artikeln *Nyheter i Intune* på Microsoft Docs, där du kan läsa om de senaste funktionerna och uppdateringarna för Intune-tjänsten.  

Det här avsnittet innehåller också grundläggande information om dina tillgängliga licenser och hur många som har tilldelats till användare. Licenser för enheter visas inte.

## <a name="connector-status"></a>Kopplingsstatus
Status för anslutningsprogrammet är en plats för att granska statusen för alla tillgängliga anslutningsprogram för Intune.  

Anslutningsprogram är:
- **Anslutningar du konfigurerar till externa tjänster**. Till exempel tjänsten för *Apples volymköpsprogram* eller *Windows Autopilot*-tjänsten.  Status för den här typen av anslutningsprogram baseras på tiden för den senaste genomförda synkroniseringen.
- **Certifikat eller autentiseringsuppgifter som krävs för att ansluta till en extern ohanterad tjänst**, till exempel *Apple Push Notification Service*-certifikat (APNS). Status för den här typen av anslutningsprogram baseras på förfallotidsstämpeln för certifikatet eller autentiseringsuppgiften.  

Som standard visas bara fem anslutningsprogram. Du kan välja **Visa alla anslutningsprogram** om du vill expandera den här listan och visa alla tillgängliga anslutningsprogram, inklusive anslutningsprogram som du inte har konfigurerat för användning.  

När det finns fler än ett enda anslutningsprogram av någon typ är statusen en sammanfattning för alla de anslutningsprogrammen. Den lägsta statusen för ett enskilt anslutningsprogram används som hälsotillstånd för gruppen.  

Ej felfria anslutningsprogram visas alltid överst i listan. Därefter visas anslutningsprogram med varningar och sedan listan över felfria anslutningsprogram. Anslutningsprogram som du inte har konfigurerat ännu visas sist.

**Status för anslutningsprogrammet:**
- **Ej felfri:**
    - Certifikatet eller autentiseringsuppgiften har upphört att gälla
    - Den senaste synkroniseringen genomfördes för minst tre dagar sedan
- **Varning:**
    - Certifikatet eller autentiseringsuppgiften upphör att gälla inom sju dagar
    - Den senaste synkroniseringen genomfördes för mer än en dag sedan
- **Felfri:**
    - Certifikatet eller autentiseringsuppgiften upphör inte att gälla inom sju dagar
    - Den senaste synkroniseringen genomfördes för mindre än en dag sedan  

När du väljer ett anslutningsprogram i listan visas den portalsida som är relevant för att skapa eller konfigurera det anslutningsprogrammet på portalen.  När du väljer anslutningsprogrammet **Förfallodatum för VPP** öppnas till exempel sidan **Volyminköpsprogramtoken för iOS** där du kan visa mer information om det anslutningsprogrammet. Sedan kan du skapa en ny konfiguration eller redigera och åtgärda problem med en befintlig.  

## <a name="intune-service-health"></a>Hälsotillstånd för Intune-tjänsten  
Du kan visa information om aktiva incidenter och rekommendationer utan att behöva gå till instrumentpanelen med hälsotillstånd för Microsoft 365-tjänsten eller meddelandecentret, som båda finns i administrationscentret för Microsoft 365 på https://portal.office.com. Endast incidenter som haft påverkan på din klientorganisation visas.  

När du väljer en incident visas incidentinformationen direkt på sidan Klientorganisationsstatus. Om du vill visa tidigare rekommendationer och incidenter väljer du **Se tidigare incidenter/rekommendationer**. Administrationscentret för Microsoft 365 öppnas och du kan visa rekommendationer och incidenter från de senaste 30 dagarna för din klientorganisation.  

Om du vill visa information för *Hälsotillstånd för Intune-tjänsten* måste ditt konto ha rollen **Global administratör** eller **Tjänstadministratör** i Azure Active Directory eller administrationsportalen för Office. Om du vill tilldela de här behörigheterna loggar du in på [	Administrationscenter för Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) med globala administratörsbehörigheter. Välj **Användare > Aktiva användare** och välj sedan det konto som kräver åtkomst. Välj **Redigera** för Roller, välj *Tjänstadministratör* eller *Global administratör* och **Spara** sedan ändringen för att tilldela behörigheterna.  

Du kan bara konfigurera kommunikationsinställningarna för Hälsotillstånd för Intune-tjänsten via administrationscentret för Microsoft 365.

## <a name="intune-news"></a>Nytt i Intune  
Visa informationskommunikation från Intune-tjänstteamet utan att behöva gå till meddelandecentret för Office. Kommunikationen omfattar meddelanden om ändringar som nyligen har gjorts i Intune-tjänsten eller som är på gång för din klientorganisation.  

Som standard visas de 10 senaste aktiva meddelandena. Om du vill visa äldre meddelanden väljer du **Se tidigare meddelanden** för att öppna *Meddelandecenter* i administrationscentret för Microsoft 365.  

Om du vill visa information för Nytt i Intune måste ditt konto ha rollen **Global administratör** eller **Tjänstadministratör** i Azure Active Directory, eller ha tilldelats rollen **Meddelandecenterläsare** i administrationsportalen för Office.  Om du vill tilldela den här behörigheten loggar du in på [	Administrationscenter för Microsoft 365](https://portal.officeppe.com/AdminPortal/Home#/homepage) med administratörsbehörigheter. Välj **Användare > Aktiva användare** och välj sedan det konto som kräver åtkomst. Välj **Redigera** för *Roller*, välj *	Administratör för Teams-kommunikation* och **Spara** sedan ändringen för att tilldela behörigheterna.  

Du kan bara konfigurera kommunikationsinställningarna för Nytt i Intune via administrationscentret för Microsoft 365.
