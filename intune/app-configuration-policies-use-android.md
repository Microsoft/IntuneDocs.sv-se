---
title: "Använda Intunes appkonfigurationsprinciper för Android for Work"
titleSuffix: Intune on Azure
description: "Lär dig hur du använder appkonfigurationsprinciper för att ange konfigurationsdata i en Android for Work-app när den körs.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7486a62ed11b83f00414a74b2d816f6048826f73
ms.sourcegitcommit: 4034ac474bfed358270a32459a2cf2fe02f44e45
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/15/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>Så här använder du appkonfigurationsprinciper i Microsoft Intune för Android for Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune om du vill definiera tillgängliga inställningar när användaren kör en Android for Work-app. Det är inte alla appar som stöder appkonfiguration. Kontrollera med apputvecklaren om appen har stöd för appkonfigurationsprinciper.

Med appkonfigurationsprinciperna kan du förkonfigurera tillgängliga appinställningar åt användarna innan de kör appen. Vissa Android-appar har stöd för hanterade konfigurationsalternativ som du kan konfigurera i Intune-konsolen med [Configuration Designer](#use-configuration-designer). Vissa konfigurationsinställningar för appar (till exempel de med pakettyper) kan inte konfigureras med Configuration Designer.  Du måste använda [JSON-redigeraren](#use-json-editor) för dessa värden.   Inställningarna skickas automatiskt till appar när de installeras.

Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem, oftast första gången den körs).

## <a name="use-configuration-designer"></a>Använda Configuration Designer

1. Välj **Mobilappar** i Intune-portalen. Under **Hantera** väljer du **Appkonfigurationsprinciper** och klickar sedan på **Lägg till**.
2. Ange följande information:
    - **Namn** – Namnet på den profil som visas i Intune-konsolen
    - **Beskrivning** – Beskrivning av den profil som visas i Intune-konsolen
    - **Plattform** – Välj **Android**
    - **Registreringstyp för enhet** - **Registrerad med Intune** är förvalt.
3. Välj **Tillhörande app** för att välja den app som du vill definiera en konfigurationsprincip för.  Välj i listan med Android for Work-appar som du har godkänt och synkroniserat med Intune
4. Välj **Konfigurationsinställningar**.
5. I **Format för konfigurationsinställningar** väljer du **Använd Configuration Designer**.
6. Välj **Lägg till**. En lista med tillgängliga konfigurationsinställningar visas. Listan innehåller:
    - **Konfigurationsnycklar** – Namnet på inställningen.
    - **Värdetyp** – Inställning som kan konfigureras, till exempel **Boolesk** eller **Sträng**.
    - **Beskrivning** – En beskrivning av konfigurationsinställningen.
7. Markera kryssrutorna för de inställningar som du vill konfigurera med profilen och klicka sedan på **OK**.
8. En lista med de valda inställningarna visas med det tillgängliga **konfigurationsvärdet**. Ange ett värde för varje inställning och klicka sedan på **OK**.

## <a name="use-json-editor"></a>Använda JSON-redigeraren

1. Välj **Mobilappar** i Intune-portalen. Under **Hantera** väljer du **Appkonfigurationsprinciper** och klickar sedan på **Lägg till**.
2. Ange följande information:
    - **Namn** – Namnet på den profil som visas i Intune-konsolen
    - **Beskrivning** – Beskrivning av den profil som visas i Intune-konsolen
    - **Plattform** – Välj **Android**
    - **Registreringstyp för enhet** - **Registrerad med Intune** är förvalt.
3. Välj **Tillhörande app** för att välja den app som du vill definiera en konfigurationsprincip för.  Välj i listan med Android for Work-appar som du har godkänt och synkroniserat med Intune.
5. Välj **Konfigurationsinställningar**.
6. I **Format för konfigurationsinställningar** väljer du **Ange JSON-redigerare**.
7. Du kan definiera JSON-värden för konfigurationsinställningar i redigeringsprogrammet. Du kan välja **Ladda ned JSON-mall** för att hämta en exempelfil som du sedan kan konfigurera.
8. När du är klar väljer du **OK** och klickar sedan på **Lägg till**.

Principen kommer att skapas och visas på bladet med principlistan.



När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.

## <a name="preconfigure-permissions-grant-state-for-apps"></a>Förkonfigurera behörigheter för att bevilja tillstånd för appar

Du kan också förkonfigurera behörigheter för att appar ska få åtkomst till funktioner i Android-enheten. Som standard kommer Android-appar som kräver enhetsbehörigheter, som t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter. Om till exempel en app använder enhetens mikrofon ombeds slutanvändaren bevilja appen behörighet att använda mikrofonen.

1. Välj **Mobilappar** i Intune-portalen. Under **Hantera** väljer du **Appkonfigurationsprinciper** och klickar sedan på **Lägg till**.
2. Ange följande information:
    - **Namn** – Namnet på den profil som visas i Intune-konsolen
    - **Beskrivning** – Beskrivning av den profil som visas i Intune-konsolen
    - **Plattform** – Välj **Android**
    - **Registreringstyp för enhet** - **Registrerad med Intune** är förvalt.
3. Välj **Tillhörande app** för att välja den app som du vill definiera en konfigurationsprincip för.  Välj i listan med Android for Work-appar som du har godkänt och synkroniserat med Intune.
5. Välj **Behörigheter** och sedan **Lägg till**.
6. Välj i listan med tillgängliga appbehörigheter och välj sedan **OK**.
7. Välj ett alternativ för varje behörighet som kan beviljas med principen:
    - **Fråga** – Uppmana användaren att godkänna eller neka.
    - **Bevilja automatiskt** – Godkänn automatiskt utan att meddela användaren.
    - **Neka automatiskt** – Neka automatiskt utan att meddela användaren.
8. Om du vill tilldela appkonfigurationsprincipen väljer du appkonfigurationsprincipen, **Tilldelning** och sedan **Välj grupper**.
9. Välj först de användargrupper som ska tilldelas och sedan **Välj**.
10. Välj **Spara** för att tilldela principen.

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.

