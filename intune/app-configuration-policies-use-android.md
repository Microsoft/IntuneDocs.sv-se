---
title: "Lägg till konfigurationsprinciper för hanterade Android-enheter | Microsoft Docs"
titlesuffix: Azure portal
description: "Lär dig hur du använder appkonfigurationsprinciper för att ange konfigurationsdata i en Android for Work-app när den körs.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e56aff30b353a2c98eb7effbec3e02bde066804f
ms.sourcegitcommit: 67c037af31c1f167ec9b4f4baa754631c817e7d1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2017
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Lägg till konfigurationsprinciper för hanterade Android-enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en Android for Work-app. Du tilldelar inte principerna direkt till användare och enheter. I stället associerar du principen med en app och tilldelar sedan appen. Principinställningarna används när appen söker efter dem, oftast första gången den körs.

> [!Note]  
> Det är inte alla appar som stöder appkonfiguration. Kontrollera med apputvecklaren om appen har stöd för appkonfigurationsprinciper.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj arbetsbelastningen **mobilappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och klickar sedan på **Lägg till**.
5. Ange följande information:
    - **Namn**  
      Namnet på den profil som visas i Azure Portal.
    - **Beskrivning**  
      Beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp**  
      Välj **Hanterade enheter**.
6. Välj **Android** för **Plattformen**.
7. Välj **Tillhörande app** för att välja den app som du vill definiera en appkonfigurationsprincip för.  Välj i listan med Android for Work-appar som du har godkänt och synkroniserat med Intune.
8. Välj **Konfigurationsinställningar**. Du kan ange konfigurationer med:
    - [Configuration Designer](#Use-the-configuration-designer)
    - [Ange JSON-redigerare](#Use-the-JSON-editor)
9. Klicka på **OK** och sedan på **Lägg till**.

## <a name="use-the-configuration-designer"></a>Använd Configuration Designer

Du kan både använda Configuration Designer för appar på enheter som är registrerade och enheter som inte är registrerade i Intune. Designern gör det möjligt att konfigurera specifika konfigurationsnycklar och värden. Du måste även ange datatyp för varje värde.

För varje nyckel och värde i konfigurationen anger du:

  - **Konfigurationsnyckel**  
     Det här används endast för att identifiera den specifika konfigurationsinställningen.
  - **Värdetyp**  
    Konfigurationsvärdets datatyp. Möjliga typer är heltals-, verklig, sträng- eller booleskt värde.
  - **Konfigurationsvärde**  
    Värdet för konfigurationen. 

## <a name="enter-the-json-editor"></a>Gå in i JSON-redigeraren

Vissa konfigurationsinställningar för appar (till exempel de med pakettyper) kan inte konfigureras med Configuration Designer.  Du måste använda JSON-redigeraren för dessa värden. Inställningarna skickas automatiskt till appar när de installeras.

1. I **Format för konfigurationsinställningar** väljer du **Ange JSON-redigerare**.
2. Du kan definiera JSON-värden för konfigurationsinställningar i redigeringsprogrammet. Du kan välja **Ladda ned JSON-mall** för att hämta en exempelfil som du sedan kan konfigurera.
3. När du är klar väljer du **OK** och klickar sedan på **Lägg till**.

Principen skapas och visas på bladet med principlistan.

När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.

## <a name="preconfigure-permissions-grant-state-for-apps"></a>Förkonfigurera behörigheter för att bevilja tillstånd för appar

Du kan också förkonfigurera behörigheter för att appar ska få åtkomst till funktioner i Android-enheten. Som standard kommer Android-appar som kräver enhetsbehörigheter, som t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter. Om till exempel en app använder enhetens mikrofon ombeds slutanvändaren bevilja appen behörighet att använda mikrofonen.

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj **Mobilappar**. Under **Hantera** väljer du Appkonfigurationsprinciper och klickar sedan på **Lägg till**.
4. Ange följande information:
    - **Namn** – Namnet på den profil som visas i Azure-portalen
    - **Beskrivning** – Beskrivning av den profil som visas i Azure-portalen
    - **Plattform** – Välj **Android**
    - **Registreringstyp för enhet** - *Hanterad enhet** är förvalt.
5. Välj **Tillhörande app** för att välja den app som du vill definiera en konfigurationsprincip för.  Välj i listan med Android for Work-appar som du har godkänt och synkroniserat med Intune.
6. Välj **Behörigheter** och sedan **Lägg till**.
7. Välj i listan med tillgängliga appbehörigheter och välj sedan **OK**.
8. Välj ett alternativ för varje behörighet som kan beviljas med principen:
    - **Fråga** – Uppmana användaren att godkänna eller neka.
    - **Bevilja automatiskt** – Godkänn automatiskt utan att meddela användaren.
    - **Neka automatiskt** – Neka automatiskt utan att meddela användaren.
9. Om du vill tilldela appkonfigurationsprincipen väljer du appkonfigurationsprincipen, **Tilldelning** och sedan **Välj grupper**.
10. Välj först de användargrupper som ska tilldelas och sedan **Välj**.
11. Välj **Spara** för att tilldela principen.

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen.

