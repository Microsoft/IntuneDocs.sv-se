---
title: "Registrera enheter – Enhetsregistreringshanterare | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: använda kontot för enhetsregistreringshanterare för att registrera enheter i Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 78eca605a277c1e0fc750900ece028d8f2c7c5b2
ms.lasthandoff: 02/15/2017

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>Registrera enheter med enhetsregistreringshanteraren

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt användarkonto som kan registrera upp till 1 000 enheter. Du kan lägga till befintliga användare till DEM-kontot för att ge dem speciella DEM-funktioner. Varje registrerad enhet använder en enda licens. Vi rekommenderar att du använder enheter som registrerats via det här kontot som delade enheter snarare än personliga enheter (BYOD).  

Användarna måste finnas i Azure Portal för att kunna läggas till som enhetsregistreringshanterare. För optimal säkerhet bör DEM-användare inte även vara Intune-administratörer.

>[!NOTE]
>DEM-registreringsmetoden kan inte användas med följande registreringsmetoder: [Apple Configurator med installationsassistent](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md), [Apple Configurator med direktregistrering](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md) eller [program för enhetsregistrering](enroll-ios-devices-using-device-enrollment-program.md). 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exempelscenario för enhetsregistreringshanterare

En restaurang vill tillhandahålla 50 surfplattor vid kassan för servitörerna. Kökspersonalen behöver också surfplattor för att se beställningarna. De anställda behöver aldrig ha tillgång till företagets data eller logga in som användare. Intune-administratören skapar ett konto för enhetsregistreringshantering (DEM) och lägger till en restaurangchef till DEM-kontot, vilket i praktiken ger chefen DEM-funktioner. Chefen kan nu registrera de 50 surfplattorna med hjälp av DEM-autentiseringsuppgifter.

Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare. Den användare som är enhetsregistreringshanterare får inte vara Intune-administratör.

DEM-användaren kan:

-   Registrera upp till 1000 enheter i Intune.
-   Logga in på företagsportalen och hämta företagsappar.
-   Konfigurera åtkomst till företagets data genom att distribuera rollspecifika appar till surfplattorna.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Begränsningar för enheter som registreras med ett DEM-konto

Enheter som har registrerats med ett konto för enhetsregistreringshantering har följande begränsningar:

  - Det finns ingen specifik "enhetsanvändare". Därför finns det inte någon åtkomst för e-post eller företagsdata. Men VPN kan ändå användas för att t. ex. förse enhetsappar med åtkomst till data.

  - Det finns inte någon villkorlig åtkomst eftersom dessa scenarierna är per användare.

  - DEM-användaren kan inte avregistrera DEM-registrerade enheter på själva enheten genom företagsportalen. Intune-administratörer kan använda den funktionen, men inte DEM-användare.

  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen.
 
  - Användare kan inte använda apparna för Apples volymköpsprogram (VPP) på grund av Apple-ID-kraven per användare för apphantering.
 
  - (Endast iOS) Om du använder DEM för att registrera iOS-enheter kan du inte använda Apple Configurator eller Apples enhetsregistreringsprogram (DEP) för att registrera enheter.


> [!NOTE]
> Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visas endast den lokala enheten i företagsportalappen på en DEM-enhet. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.


## <a name="add-a-device-enrollment-manager"></a>Lägg till en enhetsregistreringshanterare

1.  På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2.  Välj **Registrera enheter** på Intune-bladet och välj sedan **Enhetsregistreringshanterare**.

3.  Välj **Lägg till**.

4.  På bladet **Lägg till användare** anger du ett huvudnamn för DEM-användaren och väljer **Lägg till**. DEM-användaren läggs till i listan över DEM-användare.

## <a name="remove-a-device-enrollment-manager"></a>Ta bort en enhetsregistreringshanterare

Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort. När en enhetsregistreringshanterare tas bort:

-   Borttagning av en användare från listan över DEM-användare påverkar inte registrerade enheter och de registrerade enheterna fortsätter att vara fullständigt hanterade.

-   Den borttagna enhetsregistreringshanterarens kontouppgifterna fortsätter gälla.

-   Den borttagna enhetsregistreringshanteraren kan ändå inte rensa eller dra tillbaka enheter.

-   Den borttagna enhetsregistreringshanteraren kan inte registrera ytterligare enheter om inte per enhet-gränsen, som konfigureras av Intune-administratören, inte har uppnåtts.

**Ta bort en enhetsregistreringshanterare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Enhetsregistreringshanterare**.

3. På bladet **Enhetsregistreringshanterare** högerklickar du på DEM-användaren och väljer **ta bort**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visa egenskaper för en enhetsregistreringshanterare

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Enhetsregistreringshanterare**.

3. På bladet **Enhetsregistreringshanterare** högerklickar du på DEM-användaren och väljer **Egenskaper**.

