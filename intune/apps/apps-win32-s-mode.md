---
title: Aktivera Win32-appar på S-lägesenheter
titleSuffix: Microsoft Intune
description: Lär dig hur du aktiverar Win32-appar på S-lägesenheter med hjälp av Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a9eb45898102e9d5fcde88f69026467255c513
ms.sourcegitcommit: d2d18eef64bcf16eec1a48fcb67f1362537c0245
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73445270"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Aktivera Win32-appar på S-lägesenheter

[Windows 10 S-läge](https://docs.microsoft.com/windows/deployment/s-mode) är ett låst operativsystem som bara kör Store-appar. Som standard tillåts inte installation och körning av Win32-appar i Windows S-läge. S-lägesenheter har bara en *Win 10 S-basprincip* och den hindrar enheterna från att köra Win32-appar. Men genom att skapa och använda en **tilläggsprincip för S-läge** i Intune kan du installera och köra Win32-appar på hanterade Windows 10 S-lägesenheter. Med PowerShell-verktygen i [Windows Defender-programreglering (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) kan du skapa en eller flera tilläggsprinciper för Windows S-läge. Du måste signera tilläggsprinciperna med [Device Guard-signeringstjänsten (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) eller [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool) och sedan ladda upp och distribuera principerna via Intune. Alternativt kan du signera tilläggsprinciperna med ett kodsigneringscertifikat från din organisation, men den rekommenderade metoden är att använda DGSS. I instansen som kodsigneringscertifikatet från din organisation används i, måste rotcertifikatet som kodsigneringscertifikatet är kopplat till finnas på enheten.

Genom att tilldela tilläggsprincipen för S-läge i Intune kan ett undantag göras för den befintliga principen för S-lägesenheten så att den överförda signerade appkatalogen tillåts. Principen anger en lista med tillåtna appar (appkatalogen) som kan användas på S-lägesenheten.

> [!NOTE]
> Du kan endast använda Win32-appar i S-lägesenheter i november 2019-uppdateringen av Windows 10 (version 18363) eller senare.

<!-- Add WDAC tooling diagram  -->

Följande steg används för att tillåta att Win32-appar körs på en Windows 10-enhet i S-läge:

1. Aktivera S-lägesenheter via Intune som en del av registreringsprocessen för Windows 10 S.
2. Skapa en tilläggsprincip för att tillåta Win32-appar:
   - Du kan använda verktygen för [Windows Defender-programreglering (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) för att skapa en tilläggsprincip. Basprincips-ID:t i principen måste matcha basprincip-ID:t för S-läget (som är hårdkodat på klienten). Kontrollera också att principversionen är högre än den tidigare versionen.
   - Du använder DGSS för att signera tilläggsprincipen. Mer information finns i [Signera kodintegritetsprincip med Device Guard-signering](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Du överför den signerade tilläggsprincipen till Intune genom att skapa en tilläggsprincip för Windows 10 S-läge (se nedan).
3. Du tillåter Win32-appkataloger via Intune:
   - Du skapar katalogfiler (en för varje app) och signerar dem med hjälp av DGSS eller någon annan certifikatinfrastruktur.
   - Du paketerar den signerade katalogen i filen *.intunewin* med hjälp av [Microsofts verktyg för konvertering av Win32-innehåll](https://go.microsoft.com/fwlink/?linkid=2065730). Mer information finns i [Win32-apphantering – Förbereda Win32-appinnehållet för uppladdning](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Intune använder den signerade appkatalogen för att installera Win32-appen på S-lägesenheten med hjälp av [Intune-hanteringstillägget](~/apps/intune-management-extension.md).

> [!NOTE]
> Verksamhetsspecifika appar med filnamnstillägget `.appx` och `.appx`-paket i Windows 10 S-läge stöds via Microsoft Store för företag-signering (MSFB).
>
> **Tilläggsprincipen för S-läge** för appar måste levereras via Intune-hanteringstillägget.
>
> Principer för S-läge tillämpas på enhetsnivå. Flera riktade principer slås samman på enheten. Den sammanslagna principen tillämpas på enheten.

Så här skapar du en tilläggsprincip för Windows 10 S-läge:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I **Intune**-fönstret väljer du **Klientappar** > **Tilläggsprinciper för S-läge** > **Skapa princip**.
3. Innan du kan lägga till **principfilen** måste du skapa och signera den. Mer information finns i:
    - [Skapa en princip för Windows Defender-programreglering med PowerShell-verktyg och omvandla den till binärformat](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Signera med Device Guard-signeringstjänsten](https://go.microsoft.com/fwlink/?linkid=2095629) **(rekommenderas)**

4. På sidan **Grundläggande** lägger du till följande värden:

    | Värde | Beskrivning |
    |--------------|------------------------------------------------|
    | Principfil | Filen som innehåller WDAC-principen. |
    | Namn | Namnet på principen. |
    | Beskrivning | [Valfritt] En beskrivning av principen. |

5. Klicka på **Nästa: Omfångstaggar**.<br>
   På sidan **Omfångstaggar** kan du välja att konfigurera omfångstaggar för att fastställa vem som kan se apprincipen i Intune. Mer information om omfångstaggar finns i [Använda RBAC och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).

6. Klicka på **Nästa: Tilldelningar**.<br>
   På sidan **Tilldelningar** kan du tilldela principen till användare och enheter. Lägg märke till att du kan tilldela en princip till en enhet oavsett om enheten hanteras av Intune eller inte.
7. Klicka på **Nästa: Granska och skapa** för att granska de värden som du har angett för profilen.
8. När du är klar klickar du på **Skapa** för att skapa tilläggsprincipen för S-läge i Intune. 

När principen har skapats läggs den till och visas i listan med tilläggsprinciper för S-läge i Intune. När principen har tilldelats distribueras principen till enheterna. Observera att du måste distribuera appen till samma säkerhetsgrupp som tilläggsprincipen. Du kan börja tilldela appar till dessa enheter. Detta gör att slutanvändarna kan installera och köra apparna på S-lägesenheter.

## <a name="removal-of-s-mode-policy"></a>Borttagning av principen för S-läge

För att kunna ta bort tilläggsprincipen för S-läge från enheten måste du för närvarande tilldela och distribuera en tom princip som skriver över den befintliga tilläggsprincipen för S-läge.

## <a name="policy-reporting"></a>Principrapportering

Tilläggsprincipen för S-läge, som tillämpas på enhetsnivå, har endast rapportering på enhetsnivå. Rapportering på enhetsnivå är tillgängligt för lyckade och misslyckade tillstånd. 

Rapporteringsvärden som visas i Intune-konsolen för rapporteringsprinciper för S-läge:
- **Lyckades**: Tilläggsprincipen för S-läge är aktiv.
- **Okänd**: Status är okänd för tilläggsprincipen för S-läge.
- **TokenError**: Tilläggsprincipen för S-läge är ok strukturellt, men det inträffade ett fel vid auktorisering av token.
- **NotAuthorizedByToken**: Token auktoriserar inte tilläggsprincipen för S-läge.
- **PolicyNotFound**: Det gick inte att hitta tilläggsprincipen för S-läge.

## <a name="next-steps"></a>Nästa steg

- Mer information finns i [Win32-appar på S-lägesenheter](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- Mer information om hur du lägger till appar i Intune finns i [Lägga till appar i Microsoft Intune](apps-add.md).
- Mer information om Win32-appar finns i [Win32-apphantering i Intune](~/apps/apps-win32-app-management.md).
