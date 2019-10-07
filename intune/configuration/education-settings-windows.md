---
title: Utbildningsinställningar för Windows 10 i Microsoft Intune – Azure | Microsoft Docs
description: Se en lista över alla utbildningsinställningar för Windows 10-enheter. Använd de här inställningarna i en konfigurationsprofil för enheter med appen Gör ett prov, välj hur användare eller elever loggar in, övervaka skärmen under provet och mer i Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: kakyker
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 07d3488d509339fc48eb8449b12725b757775eb5
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734693"
---
# <a name="configure-the-take-a-test-app-on-windows-10-devices-using-intune"></a>Konfigurera appen Gör ett prov på Windows 10-enheter med Intune

Med testa appen kan du på ett säkert sätt administrera online-tester i klass rummets Windows 10-enheter. Om du vill konfigurera en testapp måste du skapa en profil för enhets konfiguration i Intune och konfigurera inställningarna för säker utvärdering. I den här artikeln beskrivs de inställningar som du hittar för appen gör ett prov. 

När du har konfigurerat profilen tilldelar du och distribuerar den till dina studenter. 

[Appen Gör ett prov i Intune](education-settings-configure.md) har mer information om den här funktionen.

## <a name="before-you-begin"></a>Innan du börjar

[Skapa en enhetskonfigurationsprofil](education-settings-configure.md#create-a-device-profile).

## <a name="take-a-test-settings"></a>Inställningar för Gör ett prov
När du har skapat en profil för enhets konfiguration går du till **profil typ** och väljer **säker utvärdering (utbildning)** . Du hittar följande gör ett testprogram-inställningar. 


- **Kontotyp**: Välj hur användare loggar in på provet. Alternativen är:
  - Azure AD-konto
  - Domänkonto
  - Lokalt konto
  - Lokalt gäst konto: endast tillgängligt på enheter som kör Windows 10, version 1903 och senare.    
- **Kontoanvändarnamn**: Ange användarnamnet för det konto som används med appen Gör ett prov. Du kan ange konton i följande format:
  - `user@contoso.com`
  - `domain\username`
  - `user@contoso.com`
  - `computerName\username`
- **Konto namn**: om du vill ställa in en typ av lokalt gäst konto anger du namnet på det konto som används med testappen ta en test. Konto namnet visas som en panel på inloggnings skärmen. Eleverna klickar på panelen för att starta testet.  
- **Utvärderings-URL**: Ange URL:en till det prov som du vill att användarna ska göra. Mer information om hur du hämtar webbadressen finns i [dokumentationen för Gör ett prov](https://docs.microsoft.com/education/windows/take-tests-in-windows-10).
- **Skrivar anslutning**: Välj **Kräv** att endast tillåta åtkomst till ta ett testprogram från enheter som är anslutna till en skrivare. Den här inställningen gör också att appens utskrifts knapp är tillgänglig för test-takers. **Inte konfigurerad** tillåter studenter att komma åt appen från enheter som inte är anslutna till en skrivare.  
- **Skärmövervakning**: Välj **Tillåt** för att övervaka skärmaktiviteten medan användarna gör provet. **Inte konfigurerad** förhindrar dig från att övervaka skärmen under provet.
- **Textförslag**: Välj **Tillåt** så kan provdeltagarna se textförslag. **Inte konfigurerat** blockerar textförslag medan användarna gör ett prov.

## <a name="next-steps"></a>Nästa steg

Kom ihåg att [tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
