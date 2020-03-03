---
title: Mobile Threat Defense med Microsoft Intune
titleSuffix: Microsoft Intune
description: Använd Intune Mobile Threat Defense (MTD) med din Mobile Threat Defense-partner för att skydda åtkomsten till företagsresurser baserat på enhetsrisken.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f056f665ebee0d1e2315129a4fe739b2c490ca98
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514854"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Mobile Threat Defense-integrering med Intune

Intune kan integrera data från en Mobile Threat Defense-leverantör som informationskälla för enhetsefterlevnadsprinciper samt enhetsregler för villkorsstyrd åtkomst. Du kan använda den här informationen för att skydda företagsresurser som Exchange och SharePoint genom att blockera åtkomst från komprometterade mobila enheter.

Intune kan använda samma data som källa för oregistrerade enheter som använder Intune-appskyddsprinciper. Administratörer kan därför använda den här informationen för att skydda företagsdata i en [Microsoft Intune-skyddad app](~/apps/apps-supported-intune-apps.md) och utfärda en blockering eller en selektiv rensning.

## <a name="protect-corporate-resources"></a>Skydda företagets resurser

Genom att integrera information från Mobile Threat Defense-leverantörer kan du skydda företagets resurser från hot som påverkar mobila plattformar.  

Vanligtvis är företag förutseende med att skydda datorer mot sårbarheter och angrepp, medan mobila enheter ofta är oövervakade och oskyddade. I då fall då mobila plattformar har ett inbyggt skydd med appisolering och kontrollerade appbutiker för kunder är dessa plattformar fortfarande sårbara för sofistikerade attacker. När alltfler anställda använder sina enheter för arbetsuppgifter och får åtkomst till känslig information, kan informationen från Mobile Threat Defense-leverantörer hjälpa dig att skydda enheter och resurser från mer och mer avancerade attacker.

## <a name="intune-mobile-threat-defense-connectors"></a>Intune Mobile Threat Defense-anslutningsprogram

Intune använder ett Mobile Threat Defense-anslutningsprogram till att skapa en kommunikationskanal mellan Intune och din valda Mobile Threat Defense-leverantör. Intunes Mobile Threat Defense-partners erbjuder intuitiva program som är enkla att distribuera till mobila enheter. De här programmen skannar och analyserar aktivt information om hot som kan delas med Intune. Intune kan använda data antingen för rapporter eller i syfte att framtvinga principer.

Exempel: En ansluten MTD-app rapporterar till MTD-leverantören att en telefon i nätverket för närvarande är ansluten till ett nätverk som är sårbart för man-i-mitten-attacker. Den här informationen kategoriseras till en lämplig risknivå som låg, medel eller hög. Den här risknivån jämförs sedan med de regler för risknivåer som du anger i Intune. Baserat på den här jämförelsen kan åtkomst till vissa resurser som du väljer återkallas medan enheten är komprometterad.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Data som Intune samlar in för Mobile Threat Defense

Om Intune är aktiverat samlar det in information om appinventering från både personliga och företagsägda enheter. Den blir sedan tillgänglig för MTD-leverantörer som kan hämta till exempel Lookout for Work. Du kan samla in en appinventering från användare av iOS-enheter.

Den här tjänsten kräver anmälan; som standard delas ingen information om appinventering. En Intune-administratör måste aktivera **appsynkronisering för iOS-enheter** i inställningarna för Mobile Threat Defense-anslutningsprogrammet innan någon information om appinventering delas.

**Appinventering**  
Om du aktiverar appsynkronisering för iOS/iPadOS-enheter skickas inventeringar från både företagsägda och personligt ägda iOS/iPadOS-enheter till din MTD-tjänstleverantör. Data i appinventeringen omfattar:

- App-ID
- Appversion
- Kort appversion
- Appnamn
- Storlek på appsamling
- Dynamisk appstorlek
- Oavsett om appen har verifierats eller inte
- Oavsett om appen hanteras eller inte

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Exempelscenarier för registrerade enheter med hjälp av principer för enhetsefterlevnad

När en enhet betraktas som infekterad av Mobile Threat Defense-lösningen:

![Bild på en infekterad enhet enligt Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-1.png)

Åtkomst beviljas när enheten åtgärdats:

![Bild på åtkomst beviljad av Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Exempelscenarier för oregistrerade enheter med hjälp av Intune-appskyddsprinciper

När en enhet betraktas som infekterad av Mobile Threat Defense-lösningen:<br>
![Bild på en infekterad enhet enligt Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-3.png)

Åtkomst beviljas när enheten åtgärdats:<br>
![Bild på åtkomst beviljad av Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> Du kan använda flera Mobile Threat Defense-leverantörer med en enda Intune-klient. Men när två eller flera leverantörer har konfigurerats för användning på samma plattform, måste alla enheter som kör plattformen installera varje MTD-app och söka efter hot. Om det inte går att skicka en genomsökning från något av de konfigurerade appresultaten för enheten, resulterar det i att enheten markeras som icke-kompatibel. 

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense-partner

Lär dig hur du skyddar åtkomsten till företagets resurser baserat på enhet, nätverk och programrisk med:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera skydd mot mobila hot](wandera-mtd-connector.md)
