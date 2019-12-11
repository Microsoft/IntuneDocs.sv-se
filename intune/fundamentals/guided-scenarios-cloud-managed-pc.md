---
title: Guidat scenario – Molnhanterat modernt skrivbord
titleSuffix: Microsoft Intune
description: Lär dig mer om det guidade scenariot för att upprätta och konfigurera ett grundläggande modernt skrivbord från Microsoft 365-enhetshanteringsportalen.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74164582"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Guidat scenario – Molnhanterat modernt skrivbord

Det moderna skrivbordet är informationsarbetarens förstklassiga produktivitetsplattform. Det moderna skrivbordets huvudkomponenter är Office 365 ProPlus och Windows 10 samt de senaste säkerhetsbaslinjerna för Windows 10 och Microsoft Defender Advanced Threat Protection. 

Hanteringen av det moderna skrivbordet från molnet ger ytterligare fördelar med Internetomspännande fjärråtgärder. Molnhantering använder Windows inbyggda principer för hantering av mobilenheter och eliminerar beroenden av lokal Active Directory-grupprincip. 

Om du vill utvärdera ett molnhanterat modernt skrivbord i din organisation hittar du i det här guidade scenariot en beskrivning av alla nödvändiga konfigurationer för en grundläggande distribution. I det här guidade scenariot skapar du en säker miljö där du kan prova Intune-funktionerna för enhetshantering. 

## <a name="prerequisites"></a>Krav
- [Ange MDM-auktoriteten till Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) – inställningen för hantering av mobilenheter (MDM, Mobile Device Management) avgör hur du hanterar dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.
- Minst M365 E3 (eller M365 E5 för bästa säkerhet)
- Windows 10 1903-enhet (registrerad med Windows Autopilot för bästa slutanvändarupplevelse)
- Intune-administratörsbehörigheter som krävs för slutförande av det här guidade scenariot:
  - Läsa, skriva, ta bort, tilldela och uppdatera för enhetskonfiguration
  - Läsa enhet, läsa profil, skapa profil, tilldela profil och ta bort profil för registreringsprogram
  - Läsa, skapa, ta bort, tilldela och uppdatera för mobilappar
  - Läsa och uppdatera för organisationen
  - Läsa, skapa, ta bort, tilldela och uppdatera för säkerhetsbaslinjer
  - Läsa, skapa, ta bort, tilldela och uppdatera för principuppsättningar

## <a name="step-1---introduction"></a>Steg 1 – Introduktion

Med hjälp av det här guidade scenariot konfigurerar du en testanvändare, registrerar en enhet i Intune och distribuerar enheten med Intune-rekommenderade inställningar samt Windows 10 och Office ProPlus. Enheten kommer även att konfigureras för Microsoft Defender Advanced Threat Protection om du väljer att [aktivera detta skydd i Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). Den användare som du konfigurerar samt den enhet som du registrerar kommer att läggas till i en ny säkerhetsgrupp och konfigureras med de rekommenderade inställningarna för säkerhet och produktivitet. 

### <a name="what-you-will-need-to-continue"></a>Det här behöver du för att fortsätta

I det här guidade scenariot måste du använda din egen testenhet och testanvändare. Slutför följande uppgifter:
- Skapa ett testanvändarkonto i Azure Active Directory.
- Skapa en testenhet som kör Windows 10 version 1903 eller senare.
- (Valfritt) [Registrera testenheten med Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices).
- Valfritt Aktivera [varumärkesanpassning till din organisations Azure Active Directory-inloggningssida](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Steg 2 – Användare

Välj en användare som ska konfigureras på enheten. Den här personen blir enhetens primära användare.

Om du vill lägga till fler användare eller enheter i den här konfigurationen lägger du till användare och enheter i de AAD-säkerhetsgrupper som genereras av guiden. Till skillnad från i andra guidade scenarier behöver du inte köra guiden mer än en gång eftersom konfigurationen inte är anpassningsbar. Lägg bara till fler användare och enheter till de AAD-grupper som skapats. När du har slutfört guiden kommer du att kunna visa den grupp som genererats med de rekommenderade distribuerade principerna. 

## <a name="step-3---device"></a>Steg 3 – Enhet

Se till att testenheten kör Windows 10 version 1903 eller senare.  Den primära användaren måste konfigurera enheten när den tas emot. Användaren har två konfigurationsalternativ. 

### <a name="option-a--windows-autopilot"></a>Alternativ A – Windows Autopilot
Windows Autopilot automatiserar konfigurationen av nya enheter så att användarna kan konfigurera direkt, utan hjälp från IT-avdelningen. Om enheten redan har registrerats med Windows Autopilot väljer du den utefter dess serienummer. Mer information om hur du använder Windows Autopilot finns i [Registrera enheten med Windows Autopilot (valfritt)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Alternativ B – Manuell enhetsregistrering
Användarna kommer att manuellt konfigurera och registrera sina nya enheter i hanteringen av mobilenheter. När du har slutfört det här scenariot återställer du enheten och ger den primära användaren registreringsanvisningarna för Windows-enheter. Mer information finns i [Ansluta en Windows 10-enhet till Azure AD under den första körningsupplevelsen](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Steg 4 – Granska och skapa

I det sista steget kan du granska en sammanfattning av de inställningar som du har konfigurerat. När du har granskat dina val klickar du på **Distribuera** för att slutföra det guidade scenariot. När det guidade scenariot är klart visas en tabell med resurser. Du kan redigera dessa resurser senare, men när du lämnar sammanfattningsvyn sparas inte tabellen.

> [!IMPORTANT]
> När det guidade scenariot är klart visas en sammanfattning. Du kan ändra de resurser som visas i sammanfattningen senare, men den tabell som visar dessa resurser kommer inte att sparas.

### <a name="verification"></a>Verifiering
1. Kontrollera att valet tilldelas MDM-användaromfång
    - Se till att [MDM-användaromfång](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment):
        - Anges till **Alla** för **Microsoft Intune**-app eller
        - Anges till **Vissa**. Lägg även till den användargrupp som skapats av det här guidade scenariot.
2. Kontrollera att den valda användaren kan ansluta enheter till Azure Active Directory.
    - Se till att AAD-anslutningen:
        - Anges till **Alla** eller
        - Anges till **Vissa**. Lägg även till den användargrupp som skapats av det här guidade scenariot.
3. Följ lämpliga steg på enheten för att ansluta den till Azure AD baserat på följande:
    - Med Autopilot. Mer information finns i [Användarstyrt läge för Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Utan Autopilot: Mer information finns i [Ansluta en Windows 10-enhet till Azure AD under den första körningsupplevelsen](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>Vad händer när jag klickar på Distribuera?
Användaren och enheten läggs till i nya säkerhetsgrupper. De konfigureras även med Intune-rekommenderade inställningar för säkerhet och produktivitet i arbetet eller skolan. När användaren har anslutit enheten till Azure AD läggs ytterligare appar och inställningar till på enheten. Mer information om dessa ytterligare konfigurationer finns i [Snabbstart: Registrera din Windows 10-enhet](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Ytterligare information

### <a name="register-device-with-windows-autopilot-optional"></a>Registrera enheten med Windows Autopilot (valfritt)

Du kan välja att använda en registrerad Autopilot-enhet. För Autopilot tilldelar det här guidade scenariot en Autopilot-distributionsprofil och en profil för registreringsstatussida. Autopilot-distributionsprofilen konfigureras enligt följande:
- Användarstyrt läge – det vill säga att slutanvändaren måste ange användarnamn och lösenord under Windows-installationen.
- Azure AD-anslutning.
- Anpassa Windows-installation:
  - Dölj skärmen med licensvillkor för Microsoft-programvara
  - Dölj sekretessinställningar 
  - Skapa användarens lokala profil utan lokal administratörsbehörighet
  - Dölj alternativen för ändring av konto på sidan för företagsinloggning

Sidan för registreringsstatus kommer att konfigureras så att den bara aktiveras för Autopilot-enheter och inte blockerar väntande på att alla appar ska installeras.

Det guidade scenariot tilldelar även användaren till den valda Autopilot-enheten för att ge en anpassad installationsupplevelse.

#### <a name="post-requisites"></a>Efterkrav
När användaren ansluter enheten till Azure Active Directory tillämpas följande konfigurationer på enheten:
1. Office 365 ProPlus installeras automatiskt på den molnhanterade datorn. Den innehåller de program som du är van vid, däribland Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype för företag och Word. Du kan använda dessa program för att ansluta till Office 365-tjänster såsom SharePoint Online, Exchange Online och Skype för företag – Online. Office 365 ProPlus uppdateras regelbundet med nya funktioner, till skillnad från icke-prenumerationsversioner av Office. En lista över nya funktioner finns i Nyheter i Office 365.
2. Windows-säkerhetsbaslinjer kommer att installeras på den molnhanterade datorn. Om du har konfigurerat Microsoft Defender Advanced Threat Protection kommer det guidade scenariot även att konfigurera baslinjeinställningar för Defender. Defender Advanced Threat Protection ger ett nytt skyddslager efter intrång för Windows 10-säkerhetsstacken. Med en kombination av klientteknik som är inbyggd i Windows 10 och en robust molntjänst hjälper det till att identifiera hot som tar sig förbi de andra försvaren. 

## <a name="next-steps"></a>Nästa steg

- Om du använder Microsoft Defender Advanced Threat Detection skapar du en [Intune-efterlevnadsprincip](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) för att kräva att hotanalysen i Defender uppfyller efterlevnad.
- Skapa en [enhetsbaserad princip för villkorsstyrd åtkomst](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) för att blockera åtkomst om enheten inte uppfyller Intune-efterlevnad.
