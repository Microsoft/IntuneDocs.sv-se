---
title: Konfigurera e-postinställningar i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Skapa en e-postprofil i Microsoft Intune och distribuera profilen till Android Enterprise-, iOS- och Windows-enheter. Använd en e-postprofil för att konfigurera vanliga e-postinställningar, inklusive en e-postserver och autentiseringsmetod metod för att ansluta till företagets e-post på enheter som du hanterar.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 41eb282767e6699d9286c6867ff51e4c1a2e00ec
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723963"
---
# <a name="add-email-settings-to-devices-using-intune"></a>Lägg till e-postinställningar på enheter med Intune

Microsoft Intune innehåller olika e-postinställningar som du kan distribuera till enheter i din organisation. En IT-administratör skapar e-postprofiler med specifika inställningar för att ansluta till en e-postserver, till exempel Office 365 och Gmail. Slutanvändare kan sedan ansluta, autentisera och synkronisera sina e-postkonton för organisationen på sina mobila enheter. Genom att skapa och distribuera en e-postprofil kan du bekräfta att inställningarna är gemensamma för många enheter. Och minska antalet supportsamtal från slutanvändare som inte vet de rätta e-postinställningarna.

Du kan använda e-postprofiler för att konfigurera de inbyggda e-postinställningarna för följande enheter:

- Android Samsung Knox Standard 4.0 och senare
- Android enterprise
- iOS 8.0 och senare
- Windows Phone 8.1 och senare
- Windows 10 Desktop och Windows 10 Mobile

Den här artikeln visar hur du skapar en e-postprofil i Microsoft Intune. Den innehåller också länkar till de olika plattformarna för mer specifika inställningar.

## <a name="create-a-device-profile"></a>Skapa en enhetsprofil

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på principen. Namnge dina principer så att du enkelt kan identifiera dem senare. Ett bra principnamn är till exempel **E-postinställningar för alla Windows-enheter**.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj plattform för dina enheter. Alternativen är:

        - **Android** (endast Samsung Android Knox Standard)
        - **Android enterprise**
        - **iOS/iPadOS**
        - **Windows Phone 8.1**
        - **Windows 10 och senare**

    - **Profiltyp**: Välj **E-post**.

4. Vilka inställningar du kan konfigurera varierar beroende på vilken plattform du väljer. Välj din plattform för detaljerade inställningar:

    - [Inställningar för Android Samsung Knox Standard](../email-settings-android.md)
    - [Inställningar för Android Enterprise](../email-settings-android-enterprise.md)
    - [Inställningar för iOS/iPadOS](email-settings-ios.md)
    - [Inställningar för Windows Phone 8.1](email-settings-windows-phone-8-1.md)
    - [Inställningar för Windows 10](email-settings-windows-10.md)

5. När du är klar väljer du **OK** > **Skapa** för att spara dina ändringar.

När du har angett dina inställningar och skapar profilen, visas din profil i profillistan. Härnäst [tilldela profilen till vissa grupper](../device-profile-assign.md).

## <a name="remove-an-email-profile"></a>Ta bort en e-postprofil

E-postprofiler tilldelas till enhetsgrupper, inte till användargrupper. Du kan ta bort en e-postprofil från en enhet på olika sätt, även om det bara finns en e-postprofil på enheten:

- **Alternativ 1**: Öppna e-postprofilen (**Enhetskonfiguration** > **Profiler**) och välj **Tilldelningar**. Fliken **Inkludera** visar de grupper som har tilldelats profilen. Högerklicka på gruppen > **Ta bort**. **Spara** dina ändringar.

- **Alternativ 2**: [Rensa eller dra tillbaka enheten](../remote-actions/devices-wipe.md). Du kan använda de här åtgärderna för att selektivt eller helt ta bort data och inställningar.

## <a name="secure-email-access"></a>Säkra åtkomst till e-post

Du kan skydda e-postprofiler med hjälp av följande alternativ:

- **Certifikat**: När du skapar en e-postprofil väljer du en certifikatprofil som tidigare skapats i Intune. Certifikatet kallas för identitetscertifikat. Det autentiserar mot en betrodd certifikatprofil eller ett rotcertifikat för att bekräfta att en användares enhet får ansluta. Det betrodda certifikatet tilldelas datorn som verifierar e-postanslutningen. Den här datorn är vanligtvis den interna e-postservern.

  Mer information om hur du skapar och använder certifikatprofiler i Intune finns i [Konfigurera certifikat i Intune](../protect/certificates-configure.md).

- **Användarnamn och lösenord**: Slutanvändaren autentiseras mot den interna e-postservern genom att ange ett användarnamn och lösenord. Lösenordet finns inte i e-postprofilen. Slutanvändaren måste därför ange lösenordet när hen ansluter till e-post.

## <a name="how-intune-handles-existing-email-accounts"></a>Hur Intune hanterar befintliga e-postkonton

Om användaren redan konfigurerat ett e-postkonto, tilldelas e-postprofilen på olika sätt, beroende på plattformen.

- **iOS**: En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. E-postprofildubbletten blockerar tilldelningen av en Intune-profil. I det här fallet meddelar företagsportalen användaren om att denne inte uppfyller kraven och uppmanar slutanvändaren att ta bort den manuellt konfigurerade profilen. Om du vill förhindra det här sceneriet bör du be slutanvändarna registrera sig *innan* de installerar någon e-postprofil, så att Intune kan konfigurera profilen.

- **Windows:** En befintlig duplicerad e-postprofil identifieras utifrån värdnamn och e-postadress. Intune skriver över den befintliga e-postprofilen som skapats av slutanvändaren.

- **Android Samsung Knox Standard**: En befintlig duplicerad e-postprofil identifieras utifrån e-postadressen, och den skrivs över med Intune-profilen. Android använder inte värdnamn för att identifiera profilen. Skapa inte flera e-postprofiler på samma e-postadress på olika värdar. Profilerna skriver över varandra.

- **Android-arbetsprofiler**: Intune har två e-postprofiler för arbete för Android, en för Gmail-appen och en för Nine Work-appen. De här apparna är tillgängliga i Google Play Butik och installeras i enhetens arbetsprofil. De här apparna skapar inte dubblettprofiler. Båda apparna stöder anslutningar till Exchange. Om du vill använda e-postanslutningen, distribuerar du en av dessa e-postappar till användarnas enheter. Skapa och distribuera sedan den lämpliga e-postprofilen. E-postappar som Nine Work kanske inte är kostnadsfria. Granska appens licensieringsinformation eller kontakta företaget som skapat appen om du har frågor.

## <a name="changes-to-assigned-email-profiles"></a>Ändringar av tilldelade e-postprofiler

Om du gör ändringar i en e-postprofil som du tidigare tilldelat, kan användarna få ett meddelande som ber dem godkänna omkonfigurationen av deras e-postinställningar.

## <a name="next-steps"></a>Nästa steg

När profilen har skapats gör den ingenting ännu. Härnäst [tilldela profilen till några enheter](../device-profile-assign.md).
