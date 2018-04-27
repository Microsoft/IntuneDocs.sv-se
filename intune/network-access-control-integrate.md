---
title: Integrering av nätverksåtkomstkontroll i Microsoft Intune – Azure | Microsoft Docs
description: Nätverksåtkomstkontroll (NAC, Network Access Control) kontrollerar registrering och kompatibilitet för enheter med Intune. NAC omfattar vissa beteenden och fungerar med villkorlig åtkomst. Se instruktioner om hur du kommer igång och få en lista över partnerlösningar.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cf796afcfc42f2cdf778713f4dceadb2597a12e2
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/26/2018
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integrering av nätverksåtkomstkontroll (NAC) i Intune

Intune kan integreras med en NAC-partner (Network Access Control) som hjälper ditt företag att skydda företagsdata när enheterna söker åtkomst till lokala resurser.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Hur skyddar man företagets resurser med Intune och NAC-lösningar?

NAC-lösningarna kontrollerar enhetens registrering och kompatibilitetstillstånd mot uppgifterna i Intune och fattar sedan ett beslut om att bevilja eller neka åtkomst. Om enheten inte finns registrerad, eller finns registrerad men saknar kompatibilitet med vissa principer, omdirigeras i så fall enheten till Intune för registrering och/eller för en kompatibilitetskontroll.

### <a name="example"></a>Exempel

Om enheten är registrerad och kompatibel med Intune bör NAC-lösningen ge enheten tillgång till företagets resurser. Användare kan beviljas eller nekas åtkomst när de försöker få åtkomst till företagets Wi-Fi eller VPN-resurser.

## <a name="feature-behaviors"></a>Funktionsbeteenden

Enheter som aktivt synkroniseras med Intune kan inte flyttas från **Kompatibel** / **Inte kompatibel** till **Inte synkroniserad** (eller **Okänd**). Tillståndet **Okänd** är reserverat för nyregistrerade enheter som ännu inte har utvärderats för kompatibilitet.

För enheter som har blockerats från åtkomst till resurser, ska blockeringstjänsten omdirigera alla användare till [hanteringsportalen](https://portal.manage.microsoft.com) för att avgöra varför enheten blockerats.  Om användarna besöker den här sidan kommer deras enheter synkront att omvärderas för kompatibilitet.

## <a name="nac-and-conditional-access"></a>NAC och villkorlig åtkomst

NAC kan användas med villkorlig åtkomst om du vill få mer kontroll över besluten om åtkomstkontroll. Du hittar mer information under [Vanliga sätt att använda villkorlig åtkomst med Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Så här fungerar NAC-integrering

Följande lista är en översikt över hur NAC-integrationen fungerar när du har integrerat med Intune. De första tre stegen, 1–3, beskriver registreringsprocessen. När du har integrerat NAC-lösningen med Intune kan du läsa mer om den fortlöpande användningen i steg 4–9.

![Så här fungerar NAC med Intune](./media/ca-intune-common-ways-2.png)

1. Registrera NAC-partnerlösningen i Azure Active Directory (AAD) och ge delegerade behörigheter till Intunes NAC-API.
2. Konfigurera NAC-partnerlösningen och ange lämpliga inställningar, inklusive identifierings-URL för Intune.
3. Konfigurera NAC-partnerlösningen för certifikatautentisering.
4. Användaren ansluter till företagets Wi-Fi-åtkomstpunkt eller skickar en begäran om VPN-anslutning.
5. NAC-partnerlösningen vidarebefordrar enhetsinformationen till Intune och Intune kontrollerar enhetens registrering och kompatibilitetstillstånd.
6. Om enheten inte är kompatibel eller inte finns registrerad uppmanar NAC-partnerlösningen användaren att registrera enheten eller åtgärda enhetskompatibiliteten.
7. Enheten kommer sedan att försöka verifiera sin kompatibilitet och/eller registrering på nytt.
8. Om enheten är registrerad och kompatibel kan NAC-partnerlösningen verifiera tillståndet hos Intune.
9. En anslutning upprättas och enheten får tillgång till företagets resurser.

## <a name="next-steps"></a>Nästa steg

- [Integrera Cisco ISE med Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Integrera Citrix NetScaler med Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Integrera HP Aruba Clear Pass med Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
- [Integrera Squadra security Removable Media Manager (secRMM) med Intune](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)