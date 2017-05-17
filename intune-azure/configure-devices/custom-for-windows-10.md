---
title: "Anpassade inställningar för Windows 10-enheter i Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: Lär dig om inställningarna du kan använda i en anpassad Windows 10-profil."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: d0fbecbc565d73cad997da1f7b245963144c2d93
ms.contentlocale: sv-se
ms.lasthandoff: 05/10/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Anpassade enhetsinställningar för Windows 10-enheter i Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 Använd Microsoft Intunes **anpassade** profil för Windows 10 och Windows 10 Mobile för att distribuera inställningar för OMA-URI (Open Mobile Alliance Uniform Resource Identifier) som kan användas för att styra funktioner på enheter. I Windows 10 är många CSP-inställningar tillgängliga, t.ex. [Princip-CSP (Configuration Service Provider)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
Kom ihåg att om du letar efter en viss inställning, innehåller [enhetsbegränsningsprofilen i Windows 10](/intune-azure/configure-devices/device-restrictions-for-windows-10) många inställningar som är inbyggda i Intune och som innebär att du inte behöver ange några anpassade värden.

1. Kom igång med hjälp av anvisningarna i [Hur man konfigurerar anpassade enhetsinställningar i Microsoft Intune](how-to-configure-custom-settings.md).
2. På bladet **Skapa profil** väljer du **Inställningar** för att lägga till en eller flera OMA-URI-inställningar.
3. På bladet **Anpassade OMA-URI-inställningar** klickar du på **Lägg till** för att lägga till ett nytt värde. Du kan också klicka på **Exportera** för att skapa en lista över alla värden som du har konfigurerat i en fil med kommaseparerade värden (CSV).
4. Ange följande information för varje OMA-URI-inställning som du vill lägga till. Använd listan i det här avsnittet om du vill veta mer om vilka inställningar du kan använda:
    - **Inställningsnamn** – Ange ett unikt namn för OMA-URI-inställningen som hjälper dig att identifiera den i listan över inställningar.
    - **Inställningsbeskrivning** – Ange en beskrivning för inställningen.
    - **Datatyp** – Välj bland:
        - **Sträng**
        - **Sträng (XML)**
        - **Datum och tid**
        - **Heltal**
        - **Flyttal**
        - **Boolesk**
    - **OMA-URI (skiftlägeskänslig)** – Ange den OMA-URI som du vill tillhandahålla en inställning för.
    - **Värde** – Ange det värde som ska associeras med den OMA-URI som du har angett.
5. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.
Profilen skapas och visas på bladet med profillistan.

## <a name="example"></a>Exempel
I skärmbilden nedan har inställningen **Connectivity/AllowVPNOverCellular** aktiverats. Detta innebär att en Windows 10-enhet öppnar en VPN-anslutning när enheten använder ett mobilnät.

> ![Exempel på en anpassad princip som innehåller VPN-inställningar](./media/custom-policy-example.png)


## <a name="how-to-find-the-policies-you-can-configure"></a>Så här hittar du de principer som du kan konfigurera

Du hittar en lista med alla CSP:er som har stöd för Windows 10 i [Referens till CSP (Configuration Service Provider)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) i dokumentationsbiblioteket för Windows.

Alla inställningar är inte kompatibla med alla versioner av Windows 10. I tabellen i avsnittet om Windows kan du se vilka versioner som stöds för varje CSP.

Dessutom stöder Intune inte alla inställningar som anges i avsnittet. Om du vill veta om Intune har stöd för den inställning som du vill använda, öppnar du avsnittet för den inställningen. Varje inställningssida visar den åtgärd som stöds. Om du vill arbeta med Intune måste inställningen ha stöd för åtgärderna **Lägg till** eller **Ersätt**.



