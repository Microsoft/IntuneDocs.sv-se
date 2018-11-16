---
title: Ta bort SCEP- eller PKCS-certifikat i Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Administratörer kan använda rensnings- eller tillbakadragningsåtgärden för att ta bort certifikat från Microsoft Intune. Det finns vissa scenarier då certifikaten tas bort automatiskt, t.ex. om en enhet avregistreras eller om en efterlevnadsprincip tas bort. Det finns vissa scenarier då certifikaten automatiskt bevaras på enheten, t.ex. om Intune-licensen tappas bort eller tas bort. Se hur du gör på Android-, Android Enterprise-, iOS-, macOS- och Windows-enheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a823ea2f04d8e3a8f1ca5a2f1364060840686501
ms.sourcegitcommit: 2e6851a5c1f934dcdb3f854d8462a4d23cc0453b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561949"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Ta bort SCEP- och PKCS-certifikat i Microsoft Intune

I Microsoft Intune kan du lägga till SCEP- och PKCS-certifikat till enheter. Dessa certifikat kan också tas bort när du [rensar](devices-wipe.md#wipe) eller [drar tillbaka](devices-wipe.md#retire) enheten. Det finns några andra scenarier då certifikaten tas bort automatiskt och vissa scenarier då certifikaten bevaras på enheten.

Den här artikeln beskriver några vanliga scenarier och hur de påverkar PKCS- och SCEP-certifikat.

> [!NOTE]
> Om du vill ta bort och återkalla certifikat för en användare som tas bort från Active Directory (AD) eller Azure AD måste du följa stegen i angiven ordning:
>
>    1. Rensa eller dra tillbaka användarens enhet
>    2. Ta bort användaren från AD eller Azure AD

## <a name="windows-devices"></a>Windows-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

- Ett SCEP-certifikat återkallas *och* tas bort när:

  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Enheten tas bort från Azure Active Directory-gruppen (AD)
  - Efterlevnadsprincipen tas bort från grupptilldelningen
  - Konfigurationsprofilen tas bort från grupptilldelningen

- Ett SCEP-certifikat återkallas när:
  - Administratören ändrar eller uppdaterar SCEP-profilen

- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Efterlevnadsprincipen tas bort från grupptilldelningen

- SCEP-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD

#### <a name="pkcs-certificates"></a>PKCS-certifikat

- Ett PKCS-certifikat återkallas *och* tas bort när:

  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- PKCS-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD
  - Administratören ändrar eller uppdaterar PKCS-profilen
  - Konfigurationsprofilen tas bort från grupptilldelningen
  - Efterlevnadsprincipen tas bort från grupptilldelningen 


## <a name="ios-devices"></a>iOS-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

- Ett SCEP-certifikat återkallas *och* tas bort när:

  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Enheten tas bort från Azure Active Directory-gruppen (AD)
  - Efterlevnadsprincipen tas bort från grupptilldelningen
  - Konfigurationsprofilen tas bort från grupptilldelningen

- Ett SCEP-certifikat återkallas när:
  - Administratören ändrar eller uppdaterar SCEP-profilen

- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Efterlevnadsprincipen tas bort från grupptilldelningen

- SCEP-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD

#### <a name="pkcs-certificates"></a>PKCS-certifikat

- Ett PKCS-certifikat återkallas *och* tas bort när:

  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- Ett PKCS-certifikat tas bort när:
  - Efterlevnadsprincipen tas bort från grupptilldelningen
  - Konfigurationsprofilen tas bort från grupptilldelningen
  
- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- PKCS-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD
  - Administratören ändrar eller uppdaterar PKCS-profilen

## <a name="android-knox-devices"></a>Android KNOX-enheter

#### <a name="scep-certificates"></a>SCEP-certifikat

- Ett SCEP-certifikat återkallas *och* tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)

- Ett SCEP-certifikat återkallas när:
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Enheten tas bort från Azure Active Directory-gruppen (AD)
  - Efterlevnadsprincipen tas bort från grupptilldelningen
  - Konfigurationsprofilen tas bort från grupptilldelningen
  - Administratören tar bort användaren eller gruppen från Azure Active Directory (AD)
  - Administratören ändrar eller uppdaterar SCEP-profilen

- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- SCEP-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD

#### <a name="pkcs-certificates"></a>PKCS-certifikat

- Ett PKCS-certifikat återkallas *och* tas bort när:

  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- Rotcertifikat tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [rensningsåtgärden](devices-wipe.md#wipe)
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)

- PKCS-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD
  - Administratören ändrar eller uppdaterar PKCS-profilen
  - Konfigurationsprofilen tas bort från grupptilldelningen
  - Efterlevnadsprincipen tas bort från grupptilldelningen 
  
  
> [!NOTE]
> Android for Work-enheter har inte verifierats för scenarierna ovan. Äldre Android-enheter (alla enheter som inte kommer från Samsung och inte har en arbetsprofil) har inte aktiverats för borttagning av certifikat. 

## <a name="macos-certificates"></a>macOS-certifikat

#### <a name="scep-certificates"></a>SCEP-certifikat

- Ett SCEP-certifikat återkallas *och* tas bort när:
  - En slutanvändare avregistrerar sig
  - Administratören kör [tillbakadragningsåtgärden](devices-wipe.md#retire)
  - Enheten tas bort från Azure Active Directory-gruppen (AD)
  - Efterlevnadsprincipen tas bort från grupptilldelningen
  - Konfigurationsprofilen tas bort från grupptilldelningen

- Ett SCEP-certifikat återkallas när:
  - Administratören ändrar eller uppdaterar SCEP-profilen

- SCEP-certifikat **bevaras** på enheten (certifikaten återkallas inte och tas inte bort) när:
  - En slutanvändare förlorar sin Intune-licens
  - Administratören drar tillbaka Intune-licensen
  - Administratören tar bort användaren eller gruppen från Azure AD

> [!NOTE]
> Det går inte att använda [rensningsåtgärden](devices-wipe.md#wipe) för att fabriksåterställa macOS-enheter.

#### <a name="pkcs-certificates"></a>PKCS-certifikat

PKCS-certifikat stöds inte i macOS.

