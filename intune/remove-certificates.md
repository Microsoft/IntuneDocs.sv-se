---
title: Ta bort SCEP- eller PKCS-certifikat i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Administratörer kan använda rensnings- eller tillbakadragningsåtgärden för att ta bort certifikat från Microsoft Intune. Det finns vissa scenarier då certifikaten tas bort automatiskt, t.ex. om en enhet avregistreras eller om en efterlevnadsprincip tas bort. Det finns vissa scenarier då certifikaten automatiskt bevaras på enheten, t.ex. om Intune-licensen tappas bort eller tas bort. Se hur du gör på Android-, Android Enterprise-, iOS-, macOS- och Windows-enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: 6a1280ca2a78853ae188ad68620f0b82846a365a
ms.sourcegitcommit: 9daaeba9a960c50efcc951856234fbfec3635737
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2019
ms.locfileid: "59569265"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Ta bort SCEP- och PKCS-certifikat i Microsoft Intune

I Microsoft Intune kan du lägga till SCEP-certifikat (Simple Certificate Enrollment Protocol) och PKCS-certifikat (Public Key Cryptography Standards) i enheter. Dessa certifikat kan också tas bort när du [rensar](devices-wipe.md#wipe) eller [drar tillbaka](devices-wipe.md#retire) enheten. 

Det finns några andra scenarier då certifikaten tas bort automatiskt och vissa scenarier då certifikaten bevaras på enheten. Den här artikeln beskriver några vanliga scenarier och hur de påverkar PKCS- och SCEP-certifikat.

> [!NOTE]
> Om du vill ta bort och återkalla certifikat för en användare som tas bort från lokal Active Directory eller Azure Active Directory (Azure AD) följer du dessa steg i ordning:
>
> 1. Rensa eller dra tillbaka användarens enhet.
> 2. Ta bort användaren från lokal Active Directory eller Azure AD.

## <a name="windows-devices"></a>Windows-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

Ett SCEP-certifikat återkallas *och* tas bort när:

- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).
- Enheten tas bort från en Azure AD-grupp.
- En certifikatprofil tas bort från grupptilldelningen.

Ett SCEP-certifikat återkallas när:
- En administratör ändrar eller uppdaterar SCEP-profilen.

Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

SCEP-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.

#### <a name="pkcs-certificates"></a>PKCS-certifikat

Ett PKCS-certifikat återkallas *och* tas bort när:

- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

PKCS-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.
- En administratör ändrar eller uppdaterar PKCS-profilen.
- En certifikatprofil tas bort från grupptilldelningen.


## <a name="ios-devices"></a>iOS-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

Ett SCEP-certifikat återkallas *och* tas bort när:

- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).
- Enheten tas bort från Azure AD-gruppen.
- En certifikatprofil tas bort från grupptilldelningen.

Ett SCEP-certifikat återkallas när:
- En administratör ändrar eller uppdaterar SCEP-profilen.

Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

SCEP-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.

#### <a name="pkcs-certificates"></a>PKCS-certifikat

Ett PKCS-certifikat återkallas *och* tas bort när:

- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

Ett PKCS-certifikat tas bort när:
- En certifikatprofil tas bort från grupptilldelningen.
  
Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

PKCS-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.
- En administratör ändrar eller uppdaterar PKCS-profilen.

## <a name="android-knox-devices"></a>Android KNOX-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

Ett SCEP-certifikat återkallas *och* tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).

Ett SCEP-certifikat återkallas när:
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).
- Enheten tas bort från en Azure AD-grupp.
- En certifikatprofil tas bort från grupptilldelningen.
- En administratör tar bort användaren eller gruppen från Azure AD.
- En administratör ändrar eller uppdaterar SCEP-profilen.

Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

SCEP-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.

#### <a name="pkcs-certificates"></a>PKCS-certifikat

Ett PKCS-certifikat återkallas *och* tas bort när:

- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

Ett rotcertifikat tas bort när:
- En användare avregistrerar sig.
- En administratör kör [rensningsåtgärden](devices-wipe.md#wipe).
- En administratör kör [tillbakadragningsåtgärden](devices-wipe.md#retire).

PKCS-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.
- En administratör ändrar eller uppdaterar PKCS-profilen.
- En certifikatprofil tas bort från grupptilldelningen.
  
  
> [!NOTE]
> Android for Work-enheter har inte verifierats för scenarierna ovan. Äldre Android-enheter (alla enheter som inte kommer från Samsung och inte har arbetsprofiler) har inte aktiverats för borttagning av certifikat. 

## <a name="macos-certificates"></a>macOS-certifikat

#### <a name="scep-certificates"></a>SCEP-certifikat

Ett SCEP-certifikat återkallas *och* tas bort när:
- En användare avregistrerar sig.
- En administratör kör en [tillbakadragningsåtgärd](devices-wipe.md#retire).
- Enheten tas bort från en Azure AD-grupp.
- En certifikatprofil tas bort från grupptilldelningen.

Ett SCEP-certifikat återkallas när:
- En administratör ändrar eller uppdaterar SCEP-profilen.

SCEP-certifikat *bevaras* på enheten (certifikaten återkallas inte och tas inte bort) när:
- En användare förlorar sin Intune-licens.
- En administratör drar tillbaka Intune-licensen.
- En administratör tar bort användaren eller gruppen från Azure AD.

> [!NOTE]
> Det går inte att använda [rensningsåtgärden](devices-wipe.md#wipe) för att fabriksåterställa macOS-enheter.

#### <a name="pkcs-certificates"></a>PKCS-certifikat

PKCS-certifikat stöds inte i macOS.

