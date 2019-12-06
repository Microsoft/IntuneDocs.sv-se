---
title: Konfigurera S/MIME med Outlook för iOS i Microsoft Intune
description: Förstå S/MIME med Outlook för iOS i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 348d1fe2fd236a2af11f7e58dc11530a5ce397bc
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564189"
---
# <a name="configure-smime-with-outlook-for-ios"></a>Konfigurera S/MIME med Outlook för iOS

Secure/Multipurpose Internet Mail Extensions (S/MIME) ger ett extra säkerhetslager för e-post som skickas till och från ett Exchange ActiveSync-konto (EAS). [Microsoft Outlook](https://aka.ms/omsmime) kan använda S/MIME för att tillåta användare att kryptera både utgående meddelanden och bifogade filer, vilket säkerställer att endast den avsedda mottagaren kan läsa och komma åt meddelandeinnehåll när du använder Office 365-konton. Användare kan också signera ett meddelande digitalt, vilket gör det möjligt för mottagarna att både verifiera avsändarens identitet och bekräfta att meddelandet inte har manipulerats. Den här funktionen är möjlig genom användningen av certifikat. Mer information finns i [Förstå S/MIME](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN).

> [!NOTE]
> I det här avsnittet beskrivs hur du distribuerar betrodda rotcertifikat via [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Microsoft Endpoint Manager är en enkel, integrerad plattform för slutpunktshantering som hanterar alla dina slutpunkter. I det här administrationscentret för Microsoft Endpoint Manager integreras ConfigMgr och Microsoft Intune.

## <a name="about-message-encryption"></a>Om meddelandekryptering
Användare kan skicka krypterade meddelanden till personer i organisationen och personer utanför organisationen om de har den offentliga delen av krypteringscertifikaten. Privata nycklar som är kopplade till krypteringscertifikaten bör alltid skyddas och säkras av mottagaren av det krypterade meddelandet. Den privata nyckeln för krypteringscertifikatet används av mottagaren för att dekryptera meddelandet.

Krypterade meddelanden kan bara läsas av mottagare som har certifikatet som motsvarar det som har krypterat meddelandet. Om du försöker skicka ett krypterat meddelande till mottagare vars krypteringscertifikat inte är tillgängligt uppmanas du av programmet att ta bort dessa mottagare innan du skickar e-postmeddelandet.

## <a name="about-digital-signatures"></a>Om digitala signaturer
Ett meddelande som signerats digitalt ger mottagaren garantin att meddelandet inte har manipulerats och att avsändarens identitet är äkta. Mottagare kan bara verifiera den digitala signaturen om de använder en e-postklient som stöder S/MIME.

## <a name="prerequisites"></a>Krav
- Outlook för iOS stöder endast S/MIME för Office 365-konton.
- S/MIME måste konfigureras för Office 365. Mer information finns i [Så här konfigurerar du S/MIME i Office 365](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516).
- Du måste ha en certifikatutfärdare som kan utfärda certifikat som kan användas för signering och kryptering.
- Distribuera betrodda rotcertifikat via Endpoint Manager. Mer information finns i [Skapa betrodda certifikatprofiler](~/protect/certificates-configure.md#create-trusted-certificate-profiles).
- Krypteringscertifikat måste importeras till Endpoint Manager. Mer information finns i [Konfigurera och använda importerade PKCS-certifikat med Intune](~/protect/certificates-imported-pfx-configure.md).
- Installera och konfigurera PFX-anslutningsprogrammet för Microsoft Intune. Mer information finns i [Ladda ned, installera och konfigurera PFX-certifikatanslutningsprogrammet för Microsoft Intune](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
- Enheter måste vara MDM-registrerade för att automatiskt ta emot betrodda rot- och S/MIME-certifikat från Endpoint Manager.

> [!IMPORTANT]
> Du måste ladda ned och installera det uppdaterade PFX-anslutningsprogrammet (version 6.1911.11.0 eller senare) för att Microsoft Intune ska kunna använda S/MIME-krypteringsnyckeln med Outlook för iOS.

## <a name="smime-support-in-outlook-for-ios"></a>S/MIME-support i Outlook för iOS
Outlook för iOS stöder S/MIME-signering och kryptering av meddelanden med hjälp av certifikat. Många kunder har separata signerings- och krypteringscertifikat i stället för att ha ett enda certifikat som stöder både signering och kryptering. Signeringscertifikat är vanligtvis unika över en enskild användares registrerade enheter, medan krypteringscertifikat delas mellan en enskild användares registrerade enheter. Användare använder ofta S/MIME i flera år och har då använt olika krypteringscertifikat över tid eftersom certifikaten förnyas. Krypteringscertifikatens historik, inklusive deras privata nycklar, måste finnas på användarens enhet så att e-postmeddelanden som kan ha krypterats med något av de tidigare certifikaten kan läsas. Det är också möjligt att ha ett enda certifikat som stöder signering och kryptering.

Outlook för iOS har stöd för två sätt att leverera certifikat till enheter så att de kan användas för S/MIME:

- **Användare** kan skicka e-postmeddelanden med S/MIME-certifikat till sig själva och installera dem från bifogade filer i Outlook för iOS på sina mobila enheter.
- **Administratörer** kan importera krypteringscertifikatens historik från valfri certifikatutfärdare till Endpoint Manager. Endpoint Manager levererar sedan automatiskt certifikaten till de enheter som användaren registrerar. Simple Certificate Enrollment Protocol (SCEP) används vanligen för att signera certifikat. Med SCEP genereras den privata nyckeln och lagras på den registrerade enheten. Ett unikt certifikat levereras till varje enhet som en användare registrerar och kan sedan användas för oavvislighet. Administratörer importerar krypteringscertifikatens historik för sina användare till Endpoint Manager, som sedan levererar användarens alla krypteringscertifikat till enheterna som de registrerar. Slutligen stöder Endpoint Manager härledda autentiseringsuppgifter för kunder som behöver support för standarden NIST 800-157. På iOS används Företagsportal för att hämta signerings- och krypteringscertifikat från Intune.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Konfigurera Outlook för iOS S/MIME i Endpoint Manager
Använd följande steg för att konfigurera Outlook för iOS S/MIME i Endpoint Manager, inklusive automatiskt leverans av S/MIME-certifikat som Outlook för iOS kan använda:

### <a name="add-the-microsoft-outlook-app"></a>Lägg till programmet Microsoft Outlook
1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Lägg till programmet Microsoft Outlook för iOS från App Store till Endpoint Manager eller synkronisera Outlook för iOS från Apples volymköpsprogram. Mer information finns i [Lägg till iOS-butiksprogram i Microsoft Intune](~/apps/store-apps-ios.md) eller [Så här hanterar du iOS- och macOS-program som köpts genom Apples volymköpsprogram med Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>Skapa konfigurationsprincipen för Outlook för iOS S/MIME

Med följande steg kan du skapa och konfigurera Outlook-principen för iOS S/MIME i Endpoint Manager. De här inställningarna gör att signerings- och krypteringscertifikaten levereras automatiskt.

1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och välj **Appar** > **Appkonfigurationsprinciper** > **Lägg till**.<br>
Fönstret **Lägg till konfigurationsprincip** visas.
2. Ange **Namn** och **Beskrivning** för den nya konfigurationsprincipen.
3. Välj **Hanterade enheter** som **Registreringstyp för enhet**.
4. Välj **iOS/iPadOS** som **Plattform**.
5. Klicka på **Välj det program som krävs** för att hitta och associera programmet Microsoft Outlook för iOS som du la till tidigare. 
6. Klicka på **Konfigurationsinställningar** för att lägga till konfigurationsinställningar. 
    - Välj **Använd Configuration Designer** bredvid **Konfigurationsinställningsformat** och godkänn standardinställningarna. Mer information finns i [Konfigurationsinställningar för Microsoft Outlook](~/apps/app-configuration-policies-outlook.md).
7. Klicka på **S/MIME** för att visa **Outlook S/MIME-inställningarna**.

    ![Skärmbild av inställningarna för Outlook för iOS S/MIME](./media/app-configuration-policies-outlook-smime/app-configuration-policies-outlook-smime-01.png)

8. Ställ in **Aktivera S/MIME** på **Ja**.
9. Ställ in **Distribuera S/MIME-certifikat från Intune** på **Ja**.
10. Under **Signeringscertifikat** bredvid **Certifikatprofiltyp** väljer du något av följande alternativ:
    - **SCEP** – skapar ett certifikat som är unikt för den enhet och användare som kan användas av Microsoft Outlook för signering. Relaterad information finns i [Konfigurera infrastrukturen för att stödja SCEP med Intune](~/protect/certificates-scep-configure.md) och [Skapa en SCEP-certifikatprofil](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile). 
    - **PKCS-importerade certifikat** – använder ett certifikat som är unikt för användaren, men som kan delas mellan enheter och har importerats till Endpoint Manager av administratören för användarens räkning. Certifikatet levereras till alla enheter som en användare registrerar. Endpoint Manager väljer automatiskt det importerade certifikatet som stöder signering för att leverera till enheten som motsvarar den registrerade användaren.
    - **Härledda autentiseringsuppgifter** – använder ett certifikat som redan finns på den enhet som kan användas för signering. Certifikatet måste hämtas på enheten som använder flödet för härledda autentiseringsuppgifter i Intune.
11. Under **Krypteringscertifikat** bredvid **Certifikatprofiltyp** väljer du något av följande alternativ:
    - **PKCS-importerade certifikat** – levererar alla krypteringscertifikat som har importerats till Endpoint Manager av administratören för alla enheter en användare registrerar. Endpoint Manager väljer automatiskt det importerade certifikatet eller certifikat som stöder kryptering för att leverera till den enhet som motsvarar den registrerade användaren.
    - **Härledda autentiseringsuppgifter** – använder ett certifikat som redan finns på den enhet som kan användas för signering. Certifikatet måste hämtas på enheten som använder flödet för härledda autentiseringsuppgifter i Intune.
12. Bredvid **Meddelande till slutanvändare** väljer du meddela slutanvändare genom att välja **Företagsportal** eller **E-post** för att hämta S/MIME-certifikat för Outlook för iOS.

    I iOS måste användare använda programmet Företagsportal för att hämta sina S/MIME-certifikat. Endpoint Manager informerar användaren om att de behöver starta Företagsportal för att hämta sina S/MIME-certifikat via meddelandeavsnittet i Företagsportal, ett push-meddelande och/eller ett e-postmeddelande. Om användaren klickar på ett av meddelandena tas de till en landningssida som informerar dem om att de kan hämta certifikaten. När certifikaten har hämtats kan användaren använda S/MIME inifrån Microsoft Outlook för iOS för att signera och kryptera e-post.
    
    Meddelanden för slutanvändare innehåller följande alternativ:
       - **Företagsportal** – om det här alternativet är markerat får användarna ett push-meddelande på sin enhet som tar dem till landningssidan i Företagsportal från vilken S/MIME-certifikat kommer att hämtas.
        - **E-post** – skickar ett e-postmeddelande till slutanvändaren som informerar dem om att de behöver starta Företagsportal för att hämta sina S/MIME-certifikat. Om användaren använder en registrerad iOS-enhet när de klickar på länken i e-postmeddelandet omdirigeras de till Företagsportal för att hämta sina certifikat.
    
13. Välj **Tilldelningar** för att tilldela programmets konfigurationsprincip till Azure Active Directory-grupperna. Mer information finns i [Tilldela appar till grupper med Microsoft Intune](~/apps/apps-deploy.md).

## <a name="next-steps"></a>Nästa steg

- Mer information finns i [Appkonfigurationsprinciper för Microsoft Intune](app-configuration-policies-overview.md).
