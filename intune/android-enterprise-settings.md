---
title: Inställningar för helskärmsläge för Android i Microsoft Intune – Azure | Microsoft Docs
description: Konfigurera Android enterprise-kioskenheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e43ab0d088edc87e814ad2c4317d7b7336d34d5
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312904"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Inställningar för Android enterprise kiosk i Intune

Android-kioskprofiler stöder följande konfigurationsinställningar. När du skapar en profil visas dessa inställningar när du väljer **Profiltyp** > **Endast enhetsägare** > **Enhetsbegränsningar**. Om du vill se dessa inställningar väljer du **Egenskaper** från en begränsningsprofil på en Android enterprise-enhet och väljer sedan **Konfigurera**.

## <a name="general-settings"></a>Allmänna inställningar

- **Skärmbild**: Välj **Blockera** för att förhindra användare att ta en bild av enhetens skärm.
- **Kamera**: Välj **Blockera** för att inaktivera enhetens kamera.
- **Standardbehörighetsprincip**: Den här inställningen definierar standardbehörighetsprincipen för begäranden för körningsbehörigheter. Möjliga värden är:
    - **Standard för enheten**: Använd enhetens standardinställning.
    - **Fråga**: Användaren ombeds godkänna behörigheten.
    - **Bevilja automatiskt**: Behörigheter beviljas automatiskt.
    - **Neka automatiskt**: Behörigheter nekas automatiskt.
- **Volymändringar**: Välj **Blockera** för att förhindra användare att ändra enhetens volym.
- **Rensa**: Välj **Blockera** för att hindra användare från att rensa enheten.
- **Säker start**: Välj **Blockera** för att förhindra att användare startar om enheten i felsäkert läge.
- **Statusfält**: Välj **Blockera** för att förhindra användare att komma åt statusfältet, till exempel meddelanden och snabbinställningar.
- **Ändringar i Wi-Fi-inställning**: Välj **Blockera** för att förhindra användare att ändra Wi-Fi-konfigurationer som skapats av enhetsägaren. Användarna kan skapa sina egna Wi-Fi-konfigurationer.
- **Konfiguration av Wi-Fi-åtkomstpunkt**: Välj **Blockera** för att förhindra användare att skapa eller redigera Wi-Fi-konfigurationer.
- **Felsökningsfunktioner**: Välj **Tillåt** för att låta användare använda felsökningsfunktioner.
- **Mikrofonjustering**: Välj **Blockera** för att förhindra användare att justera volymen för eller stänga av mikrofonen.
- **Wipe protection emails** (E-post för skydd mot rensning): Välj **E-postadresser för Google-konto** för att definiera e-postadresser (avgränsa med semikolon) som kan låsa upp enheten efter en rensning. Om ett e-postmeddelande inte har angetts kan vem som helst låsa upp enheten efter en rensning.
- **Nätverkshjälp**: Välj **Aktivera** för att tillåta aktivering av nätverkshjälpfunktionen. Om en nätverksanslutning inte kan upprättas vid start uppmanar hjälpfunktionen användaren att tillfälligt ansluta till ett nätverk för att kunna uppdatera enhetsprincipen. När principen har tillämpats glöms det tillfälliga nätverket och starten av enheten fortsätter. Detta förhindrar att det inte går att ansluta till något nätverk om det inte finns något lämpligt nätverk i den senaste principen och enheten startar i en app i låsläget, eller om användaren på annat sätt inte kan nå enhetsinställningarna.
- **Tillåt installation från okända källor**: Välj **Tillåt** för att tillåta att användare installerar från okända källor.
- **Systemuppdatering**: Välj ett alternativ för att definiera hur enheten hanterar over-the-air-uppdateringar:
    - **Standard för enheten**: Använd enhetens standardinställning.
    - **Automatiskt**: Uppdateringar installeras automatiskt.
    - **Uppskjuten**: Uppdateringar skjuts upp till ett senare datum.
    - **Underhållsfönster**: Användarna uppmanas i ett underhållsfönster att godkänna uppdateringen.

## <a name="kiosk-settings"></a>Kioskinställningar

- **Helskärmsläge**: Definierar om enheten bara kan köra en app eller flera appar. Mer information finns i [Inställningar för helskärmsläge för Android-enheter](android-kiosk-settings.md).
    - **Kioskenhet för enstaka app**: Användare kan bara komma åt en enda app.
    - **Kioskenhet för flera appar**: Användare kan komma åt en obegränsad uppsättning appar.

## <a name="device-password-settings"></a>Inställningar för enhetslösenord

- **Keyguard**: Välj **Inaktivera** för att förhindra att användare använder Keyguard på enheten.
- **Krav på lösenordstyp**: Definiera typen av lösenord som krävs för enheten.
- **Minsta längd på lösenord**: Definiera den minsta lösenorden som krävs för enheten.
- **Antal felaktiga inloggningar innan enheten rensas**: Definiera antalet felaktiga inloggningar som måste förekomma innan enheten rensas.

## <a name="power-settings"></a>Energiinställningar

- **Tid innan skärmen låses**: Ange hur lång väntetid som krävs innan enheten låses.
- **Skärmen är på när enheten är ansluten**: Välj vilka strömkällor som gör så att enhetens skärm är på när den är ansluten.

## <a name="users-and-accounts-settings"></a>Inställningar för användare och konton

- **Lägg till nya användare**: Välj **Blockera** för att förhindra att användare lägger till nya användare.
- **Borttagning av användare**: Välj **Blockera** för att förhindra att användare tar bort användare.
- **Kontoändringar**: Välj **Blockera** för att förhindra att användare ändrar konton.

## <a name="next-steps"></a>Nästa steg
[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).



