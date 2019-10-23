---
title: Ange utfärdare för hantering av mobila enheter
titleSuffix: Microsoft Intune
description: Ange utfärdare för hantering av mobila enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19d02694ab5e53dc43e0861c6a427a044bf50648
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502632"
---
# <a name="set-the-mobile-device-management-authority"></a>Ange utfärdare för hantering av mobila enheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.

Möjliga konfigurationerna är:

- **Fristående Intune** – Endast molnbaserad hantering, som du konfigurerar med hjälp av Azure-portalen. Innehåller den fullständiga uppsättning funktioner som Intune erbjuder. [Ange utfärdare för hantering av mobila enheter i Intune-konsolen](#set-mdm-authority-to-intune).

- **Intune-samhantering** – Integration av Intunes molnlösning med System Center Configuration Manager för Windows 10-enheter. Du kan konfigurera Intune med hjälp av Configuration Manager-konsolen. [Konfigurera automatisk registrering av enheter i Intune](https://docs.microsoft.com/sccm/comanage/tutorial-co-manage-clients#configure-auto-enrollment-of-devices-to-intune). 

    > [!Important]
    >Registrering av nya hybrid-MDM-kunder är nu inaktuell. Mer information finns i blogginlägget [Flytt från hybridhantering av mobilenheter till Intune i Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

- **Hantering av mobilenheter i Office 365** – Integrering av Office 365 med Intunes molnlösning. Du kan konfigurera Intune från ditt administrationscenter för Microsoft 365. Innehåller en delmängd av de funktioner som är tillgängliga i Fristående Intune. Ange utfärdare av mobilenhetshantering i Administrationscenter för Microsoft 365.

- **Office 365 MDM-samexistens** Du kan aktivera och använda MDM för såväl Office 365 som Intune samtidigt på din klient och konfigurera hanteringsbehörigheten till antingen Intune eller MDM för Office 365 så att varje användare får bestämma vilken tjänst som ska användas för att hantera deras mobilenheter. Användarens hanteringsbehörighet definieras utifrån den licens som tilldelats användaren. Mer information finns i [Microsoft Intune-samexistens med MDM för Office 365](https://blogs.technet.microsoft.com/configmgrdogs/2016/01/04/microsoft-intune-co-existence-with-mdm-for-office-365)

## <a name="set-mdm-authority-to-intune"></a>Ange Intune som utfärdare för hantering av mobila enheter

Följ stegen nedan om du inte har angett MDM-utfärdaren än. Information om att byta från SCCM finns i [Migrera hybrida MDM-användare och -enheter till fristående Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

1. Välj den orangefärgade banderollen för att öppna inställningen **Utfärdare av Hantering av mobila enheter** i [Intune i Azure-portalen](https://aka.ms/intuneportal). Den orangefärgade banderollen visas bara om du inte har angett MDM-utfärdaren än.
2. Under **Utfärdare av Hantering av mobila enheter** väljer du en utfärdare bland följande alternativ:
   - **Intune-utfärdare av mobilenhetshantering**
   - **Inga**

   ![Skärmbild av Intune-skärmen Ange utfärdare för hantering av mobila enheter](./media/mdm-authority-set/set-mdm-auth.png)

   Ett meddelande indikerar att du har angett MDM-utfärdare till Intune.

### <a name="workflow-of-intune-administration-ui"></a>Arbetsflöde i användargränssnitt för Intune-administration
När Android- eller Apple-enhetshantering är aktiverat skickar Intune enhets- och användarinformation för att kunna integrera med dessa tredjepartstjänster och hantera deras respektive enheter.

Scenarier som kräver ett medgivande om att dela data ingår vid följande tillfällen:
- Du aktiverar Android-arbetsprofiler.
- Du aktiverar och laddar upp Apple MDM-pushcertifikat.
- Du aktiverar någon av Apples tjänster som t.ex. programmet för enhetsregistrering, School Manager och volyminköpsprogrammet.

I båda fallen är medgivandet strikt relaterat till att köra en tjänst för hantering av mobilenheter. Till exempel att bekräfta att en IT-administratör har godkänt att Google- eller Apple-enheter får registreras. Dokumentation som visar vilken information som delas när de nya arbetsflödena publiceras finns på följande platser:
- [Data som Intune skickar till Google](https://aka.ms/Data-intune-sends-to-google)
- [Data som Intune skickar till Apple](https://aka.ms/data-intune-sends-to-apple)

## <a name="key-considerations"></a>Viktigt att tänka på
När du har bytt till den nya MDM-utfärdaren kan det ta upp till åtta timmar innan enheten ansluter till och synkroniserar med tjänsten. Du måste konfigurera inställningar i den nya MDM-utfärdaren (hybrid) så att registrerade enheter fortsätter att hanteras och skyddas efter ändringen. 
- Enheter måste ansluta till tjänsten efter ändringen så att inställningarna från den nya MDM-utfärdaren (fristående Intune) ersätter de befintliga inställningarna på enheten.
- När du har ändrat MDM-utfärdaren finns några av de grundläggande inställningarna (t.ex. profiler) från den tidigare MDM-utfärdaren (fristående Intune) kvar på enheten i upp till sju dagar, eller tills enheten ansluter till tjänsten för första gången. Vi rekommenderar att du konfigurerar appar och inställningar (principer, profiler, appar osv.) i den nya MDM-utfärdaren (hybrid) så snart som möjligt och distribuerar inställningen till användargrupperna för användare som har befintliga registrerade enheter. Så fort en enhet ansluter till tjänsten efter ändringen av MDM-utfärdare tar den emot de nya inställningarna från den nya MDM-utfärdaren, vilket förhindrar avbrott i hanteringen och skyddet av enheten.
- När samma enhetskategorier finns i både Intune och Configuration Manager överförs inte enhetskategoritilldelningar för enheter när du växlar till den nya MDM-utfärdaren. Om du vill fortsätta att använda enhetskategorier måste migrerade enheter läggas till manuellt i lämpliga samlingar efter att MDM-utfärdaren har ändrats och enheterna visas i Configuration Manager-konsolen.
- Enheter som inte har associerade användare (vanligt om du har iOS-programmet för enhetsregistrering eller vid massregistreringsscenarier) migreras inte till den nya MDM-utfärdaren. För dessa enheter måste du ringa supporten och få hjälp med att flytta dem till den nya MDM-utfärdaren.

## <a name="change-mdm-authority-to-office-365"></a>Ändra MDM-utfärdare till Office 365

Om du vill aktivera Office 365 MDM (eller aktivera MDM-samexistens) utöver din befintliga Intune-tjänst går du till [https://protection.office.com](https://protection.office.com) väljer **Skydd mot dataförlust** > **Säkerhetsprinciper för enhet** > **Visa en lista över hanterade enheter** > **Kom igång**.

Mer information finns i [Konfigurera Mobile Device Management (MDM) i Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Om du vill att slutanvändarna bara ska hanteras av Office 365 MDM tar bort alla tilldelade Intune- och/eller EMS-licenser efter aktivering av Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.

## <a name="remove-mdm-authority"></a>Ta bort MDM-utfärdare

MDM-utfärdaren kan inte ändras tillbaka till Okänd. MDM-utfärdaren används av tjänsten för att avgöra vilken portal som registrerade enheter rapporterar till (Microsoft Intune eller Office 365 MDM).

## <a name="what-to-expect-after-changing-the-mdm-authority"></a>Vad som händer MDM-utfärdaren har ändrats

- När Intune-tjänsten upptäcker att en klients MDM-utfärdare har ändrats, skickar den ett aviseringsmeddelande till alla registrerade enheter och uppmanar dem att ansluta till samt synkronisera med tjänsten (detta sker utanför den normala schemalagda kontrollen). När MDM-utfärdaren för klienten har ändrats från fristående Intune till hybridversionen kommer därför alla enheter som är påslagna och online att ansluta till tjänsten, ta emot inställningarna från den nya MDM-utfärdaren och börja hanteras av hybridversionen. Det sker inget avbrott i hanteringen och skyddet av dessa enheter.
- Även för enheter som är påslagna och online under (eller strax efter) ändringen av MDM-utfärdaren uppstår det en fördröjning på upp till åtta timmar (beroende på tidpunkten för nästa schemalagda regelbundna incheckning) innan enheterna registreras med tjänsten med den nya MDM-utfärdaren.    

  > [!IMPORTANT]    
  > Under perioden från det att du ändrar MDM-utfärdaren tills det förnyade APNs-certifikatet laddas upp till den nya utfärdaren kommer nya enhetsregistreringar och enhetskontroller på iOS-enheter att misslyckas. Därför är det viktigt att du granskar och laddar upp APNs-certifikatet till den nya utfärdaren så snart som möjligt efter ändringen av MDM-utfärdare.

- Användarna kan snabbt gå över till den nya MDM-utfärdaren genom att manuellt starta en incheckning från enheten till tjänsten. Användarna kan enkelt göra denna ändring genom att initiera en enhetskompatibilitetskontroll från företagsportalappen.
- Du kan kontrollera att allt fungerar korrekt när enheterna har anslutit till och synkroniserat med tjänsten efter ändringen av MDM-utfärdaren genom att granska enheterna i Configuration Manager-konsolen. Enheterna som tidigare hanterades av Intune visas nu som hanterade enheter i Configuration Manager-konsolen.    
- Det uppstår en övergångsperiod om en enhet är frånkopplad under ändringen av MDM-utfärdaren tills dess enheten ansluter till tjänsten. För att säkerställa att enheten fortfarande är skyddad och fungerar under den här övergångsperioden finns följande profiler kvar på enheten i upp till sju dagar (eller tills enheten ansluter till den nya MDM-utfärdaren och tar emot nya inställningar som skriver över de befintliga):
  - E-postprofil
  - VPN-profil
  - Certifikatprofil
  - Wi-Fi-profil
  - Konfigurationsprofiler
- När du har bytt till den nya MDM-utfärdaren kan det ta upp till en vecka innan kompatibilitetsinformationen i Microsoft Intune-administrationskonsolen visar korrekta data. Kompatibilitetsstatusen i Azure Active Directory och på enheten är dock korrekt, så enheten är fortfarande skyddad.
- Kontrollera att de nya inställningarna som ska skriva över befintliga inställningar har samma namn som de tidigare inställningarna för att säkerställa att de gamla inställningarna skrivs över. Annars är risken att de gamla profilerna och principerna ligger kvar på enheterna.    

  > [!TIP]    
  > Vi rekommenderar att du skapar alla hanteringsinställningar och konfigurationer, samt även distributionerna, så snart som möjligt efter ändringen av MDM-utfärdaren. På så sätt kan du vara säker på att enheterna skyddas och hanteras aktivt under övergångsperioden.

- Bekräfta att de nya enheterna registreras korrekt med den nya utfärdaren genom att utföra följande steg när du har ändrat MDM-utfärdaren:   
  - Registrera en ny enhet.
  - Kontrollera att den registrerade enheten visas i Configuration Manager-konsolen.
  - Utför en åtgärd på enheten, t.ex. fjärrlåsning, från administrationskonsolen. Om åtgärden lyckas betyder det att enheten hanteras av den nya MDM-utfärdaren.
- Om du har problem med specifika enheter kan du avregistrera och registrera om enheterna så att de börjar använda den nya utfärdaren och hanteras så snart som möjligt.

## <a name="next-steps"></a>Nästa steg

När MDM-utfärdaren har angetts kan du börja [registrera enheter](../enrollment/device-enrollment.md).
