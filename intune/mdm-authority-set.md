---
title: Ange utfärdare för hantering av mobila enheter
titlesuffix: Microsoft Intune
description: Ange utfärdare för hantering av mobila enheter i Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a783b784f63453ba706e69bbb5078b0c3cda37d8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834525"
---
# <a name="set-the-mobile-device-management-authority"></a>Ange utfärdare för hantering av mobila enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.

Möjliga konfigurationerna är:

- **Fristående Intune** – Endast molnbaserad hantering, som du konfigurerar med hjälp av Azure-portalen. Innehåller den fullständiga uppsättning funktioner som Intune erbjuder. [Ange utfärdare för hantering av mobila enheter i Intune-konsolen](#set-mdm-authority-to-intune).

- **Intune-hybrid** – Integrering av Intunes molnlösning med System Center Configuration Manager. Du kan konfigurera Intune med hjälp av Configuration Manager-konsolen. [Ange utfärdare för hantering av mobila enheter till Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription). 

    > [!Important]
    >Registrering av nya kunder med hybrid MDM kommer att inaktiveras i en kommande version. Mer information finns i blogginlägget [Flytt från hybridhantering av mobilenheter till Intune i Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150).

- **Hantering av mobilenheter i Office 365** – Integrering av Office 365 med Intunes molnlösning. Du kan konfigurera Intune från administrationscentret för Office 365. Innehåller en delmängd av de funktioner som är tillgängliga i Fristående Intune. Ange utfärdare för hantering av mobila enheter i administrationscentret för Office 365.

> [!IMPORTANT]
> I Configuration Manager version 1610 och senare och i Microsoft Intune version 1705 kan du ändra MDM-utfärdaren utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. Mer information finns i [Förbereda ändringen av MDM-utfärdare till Configuration Manager](mdm-authority-set.md#prepare-to-change-the-mdm-authority-to-configuration-manager).

## <a name="set-mdm-authority-to-intune"></a>Ange Intune som utfärdare för hantering av mobila enheter

Följ stegen nedan om du inte har angett MDM-utfärdaren än. Om du vill ändra från en MDM-utfärdaren till en annan går du till avsnittet [Ändra MDM-utfärdare](#prepare-to-change-the-mdm-authority-to-configuration-manager) nedan.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj den orangefärgade banderollen för att öppna inställningen **Utfärdare av Hantering av mobila enheter**. Den orangefärgade banderollen visas bara om du inte har angett MDM-utfärdaren än.
4. Under **Utfärdare av Hantering av mobila enheter** väljer du en utfärdare bland följande alternativ:
   - **Intune-utfärdare av mobilenhetshantering**
   - **Configuration Manager-utfärdare av mobilenhetshantering**
   - **Inga**

   ![Skärmbild av Intune-skärmen Ange utfärdare för hantering av mobila enheter](media/set-mdm-auth.png)

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

## <a name="prepare-to-change-the-mdm-authority-to-configuration-manager"></a>Förbereda ändringen av MDM-utfärdare till Configuration Manager

Läs följande information som beskriver hur du förbereder övergången till MDM-utfärdaren:
- Du måste ha Configuration Manager version 1610 eller senare för att alternativet att byta MDM-utfärdare ska vara tillgängligt.
- Det kan ta upp till åtta timmar innan en enhet ansluter till tjänsten efter att du har bytt till den nya MDM-utfärdaren.
- Skapa en Configuration Manager-användarsamling med alla användare som för närvarande hanteras av fristående Intune, som du sedan ska använda när du konfigurerar Intune-prenumerationen i Configuration Manager-konsolen. Med samlingen kan du vara säker på att användarna och deras enheter har en tilldelad Configuration Manager-licens och att de hanteras i hybridmiljön efter ändringen till MDM-utfärdaren.
- Se till att IT-administratörsanvändaren ingår i den här användarsamlingen.  
- Innan ändringen visas MDM-utfärdaren som **Ställ in på Microsoft Intune** (fristående) i Intune-administrationskonsolen.
- MDM-utfärdaren bör visas som **Ställ in på Microsoft Intune** (fristående klient) i Microsoft Intune-administrationskonsolen före ändringen av MDM-utfärdare.
    > [!NOTE]    
    > Om MDM-utfärdaren visas som **Hanteras av Intune och Office 365** kommer dina Office 365-hanterade MDM-enheter inte längre att hanteras när du ändrar MDM-utfärdaren till **Configuration Manager** (hybrid). Vi rekommenderar att du licensierar dessa användare för Intune eller Enterprise Mobility Suite innan du ändrar MDM-utfärdare.   

- Ta bort rollen Enhetsregistreringshanterare i [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com). Mer information finns i [Ta bort en enhetsregistreringshanterare från Intune](device-enrollment-manager-enroll.md#remove-device-enrollment-manager-permissions).
- Inaktivera alla konfigurerade enhetsgruppmappningar. Mer information finns i avsnittet [Kategorisera enheter med enhetsgruppmappning i Microsoft Intune](device-group-mapping.md).
- Slutanvändarna bör inte påverkas nämnvärt under övergången till den nya MDM-utfärdaren. Det kan dock vara bra att informera användarna om ändringen så att de har sina enheter påslagna och ansluter till tjänsten så snart som möjligt efter ändringen. Detta säkerställer att så många enheter som möjligt ansluter till och registreras med tjänsten via den nya utfärdaren så fort som möjligt.
- Om du använder fristående Intune för att hantera iOS-enheter före ändringen av MDM-utfärdare, måste du se till att samma APNs-certifikat (Apple Push Notification service) som användes tidigare i Intune förnyas och används för att konfigurera klienten igen i Configuration Manager (hybrid).    

    > [!IMPORTANT]  
    > Om ett annat APNs-certifikat används för hybridversionen avregistreras ALLA tidigare registrerade iOS-enheter och du måste registrera dem på nytt. Kontrollera exakt vilket APNs-certifikat som användes för att hantera iOS-enheter i Intune innan du ändrar MDM-utfärdaren. Leta upp samma certifikat på Apple Push Certificates-portalen (https://identity.apple.com)) och kontrollera att den användare vars Apple-ID användes för att skapa det ursprungliga APNs-certifikatet identifieras och är tillgänglig, så att samma APNs-certifikat kan förnyas i samband med att den nya MDM-utfärdaren ändras.

## <a name="change-the-mdm-authority-to-configuration-manager"></a>Ändra MDM-utfärdaren till Configuration Manager

1. Gå till **Administration** &gt; **Översikt** &gt; **Cloud Services** &gt; **Microsoft Intune-prenumeration** i Configuration Manager-konsolen och välj att lägga till en Intune-prenumeration.
2. Logga in på den Intune-klient som du ursprungligen använde när du konfigurerade MDM-utfärdaren i Intune och klicka på **Nästa**.
3. Välj **Ändra utfärdare för hantering av mobila enheter till Configuration Manager** och klicka på **Nästa**.
4. Välj användarsamlingen med alla användare som ska hanteras av den nya hybrid-MDM-utfärdaren.
5. Klicka på **Nästa** och slutför guiden. Nu ändras MDM-utfärdaren till **Configuration Manager**.
6. Logga in på [Microsoft Intune-administrationskonsolen](http://manage.microsoft.com) med samma Intune-klient och kontrollera att MDM-utfärdaren har ändrats till **Ställ in som Configuration Manager**.
7. När du har ändrat MDM-utfärdaren till Configuration Manager kan du konfigurera [iOS-registrering](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac) och [Android-registrering](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-android).
8. Konfigurera och distribuera nya inställningar och appar från den nya MDM-utfärdaren (hybrid) i Configuration Manager-konsolen.

Nästa gång enheterna ansluter till tjänsten synkroniseras de och tar emot de nya inställningarna från den nya MDM-utfärdaren.

## <a name="change-mdm-authority-to-office-365"></a>Ändra MDM-utfärdare till Office 365

Om du vill aktivera Office 365 MDM utöver din befintliga Intune-tjänst går du till [https://protection.office.com](https://protection.office.com) väljer **Skydd mot dataförlust** > **Säkerhetsprinciper för enhet** > **Visa en lista över hanterade enheter** > **Kom igång**.

Mer information finns i [Konfigurera Mobile Device Management (MDM) i Office 365](https://support.office.com/en-us/article/Set-up-Mobile-Device-Management-MDM-in-Office-365-dd892318-bc44-4eb1-af00-9db5430be3cd).

Om du vill att slutanvändarna bara ska hanteras av Office 365 MDM tar bort alla tilldelade Intune- och/eller EMS-licenser efter aktivering av Office 365 MDM.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.

## <a name="remove-mdm-authority"></a>Ta bort MDM-utfärdare

MDM-utfärdaren kan inte ändras tillbaka till Okänd. MDM-utfärdaren används av Microsoft-servrar för att avgöra vilken portal som registrerade enheter rapporterar till (ConfigMGR, Azure Intune, Office 365 MDM).

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

-  Bekräfta att de nya enheterna registreras korrekt med den nya utfärdaren genom att utföra följande steg när du har ändrat MDM-utfärdaren:   
    - Registrera en ny enhet.
    - Kontrollera att den registrerade enheten visas i Configuration Manager-konsolen.
    - Utför en åtgärd på enheten, t.ex. fjärrlåsning, från administrationskonsolen. Om åtgärden lyckas betyder det att enheten hanteras av den nya MDM-utfärdaren.
- Om du har problem med specifika enheter kan du avregistrera och registrera om enheterna så att de börjar använda den nya utfärdaren och hanteras så snart som möjligt.

## <a name="next-steps"></a>Nästa steg

När MDM-utfärdaren har angetts kan du börja [registrera enheter](device-enrollment.md).
