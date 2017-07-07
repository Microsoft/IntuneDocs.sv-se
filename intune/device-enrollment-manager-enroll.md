---
title: "Registrera enheter – enhetsregistreringshanteraren"
titleSuffix: Intune on Azure
description: "Använda kontot för enhetsregistreringshanteraren för att registrera flera enheter i Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1667470154e5d2485e3a372ab25d36eea12109a7
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-devices-using-device-enrollment-manager"></a>Registrera enheter med enhetsregistreringshanteraren

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt användarkonto som kan registrera upp till 1 000 enheter. Du kan lägga till befintliga användare till DEM-kontot för att ge dem speciella DEM-funktioner. Varje registrerad enhet använder en enda licens. Vi rekommenderar att du använder enheter som registrerats via det här kontot som delade enheter snarare än personliga enheter (BYOD).  

Användarna måste finnas i Azure Portal för att kunna läggas till som enhetsregistreringshanterare. För optimal säkerhet bör DEM-användare inte även vara Intune-administratörer.

>[!NOTE]
>DEM-registreringsmetoden går inte att använda med de här andra registreringsmetoderna: [Apple Configurator med installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator med direktregistrering](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md), eller [programmet för enhetsregistrering (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exempelscenario för enhetsregistreringshanterare

En restaurang vill tillhandahålla 50 surfplattor vid kassan för servitörerna. Kökspersonalen behöver också surfplattor för att se beställningarna. De anställda behöver aldrig ha tillgång till företagets data eller logga in som användare. Intune-administratören skapar ett konto för enhetsregistreringshantering (DEM) och lägger till en restaurangchef till DEM-kontot, vilket i praktiken ger chefen DEM-funktioner. Chefen kan nu registrera de 50 surfplattorna med hjälp av DEM-autentiseringsuppgifter.

Endast användare i Intune-konsolen kan vara enhetsregistreringshanterare. Den användare som är enhetsregistreringshanterare får inte vara Intune-administratör.

DEM-användaren kan:

-   Registrera upp till 1000 enheter i Intune.
-   Logga in på företagsportalen och hämta företagsappar.
-   Konfigurera åtkomst till företagets data genom att distribuera rollspecifika appar till surfplattorna.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Begränsningar för enheter som registreras med ett DEM-konto

Enheter som har registrerats med ett konto för enhetsregistreringshantering har följande begränsningar:

  - Ingen åtkomst per användare. Eftersom enheter inte har en tilldelad användare, har enheten ingen åtkomst till e-post eller företagsdata. VPN-konfigurationer, till exempel, skulle fortfarande kunna användas för att ge enhetens appar åtkomst till data.
  - Ingen villkorad åtkomst eftersom de är scenarier per användare
  - DEM-användaren kan inte avregistrera DEM-registrerade enheter på själva enheten genom företagsportalen. Intune-administratören kan göra det här, men inte DEM-användaren.
  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen.
  - Användare kan inte använda apparna för Apples volymköpsprogram (VPP) på grund av Apple-ID-kraven per användare för apphantering.
  - (Endast iOS) Om du använder DEM för att registrera iOS-enheter, kan du inte använda Apple Configurator, Apples program för enhetsregistrering (DEP) eller Apple School Manager (ASM) för att registrera enheter.
  - Varje enhet måste ha en enhetslicens. Läs mer om [användar- och enhetslicenser](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Om du vill distribuera appar till enheter som hanteras med enhetsregistreringshanteraren distribuerar du företagsportalappen som en **obligatorisk installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visas endast den lokala enheten i företagsportalappen på en DEM-enhet. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.


## <a name="add-a-device-enrollment-manager"></a>Lägg till en enhetsregistreringshanterare

1.  På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.

2.  Välj **Registrera enheter** på Intune-bladet och välj sedan **Enhetsregistreringshanterare**.

3.  Välj **Lägg till**.

4.  På bladet **Lägg till användare** anger du ett huvudnamn för DEM-användaren och väljer **Lägg till**. DEM-användaren läggs till i listan över DEM-användare.

## <a name="permissions-for-dem"></a>Behörigheter för DEM

Azure AD-rollerna global eller Intune-tjänstadministratör krävs för att utföra uppgifter för DEM-registrering. De här rollerna krävs också för att se alla DEM-användare trots RBAC behörigheter som listas och är tillgängliga under den anpassade användarrollen. En användare utan rollen global administratör eller Intune-tjänstadministratör tilldelad, men som har läsbehörigheter för rollen enhetsregistreringshanterare, kan bara se de DEM-användare som de skapat. RBAC-rollstöd för dessa funktioner kommer att finnas i framtiden.

Om en användare inte har rollen Global administratör eller Intune-tjänstadministratör tilldelad till sig, men har läsbehörigheter aktiverade för rollen enhetsregistreringshanterare, kan de bara se DEM-användare som de har skapat.

## <a name="remove-a-device-enrollment-manager"></a>Ta bort en enhetsregistreringshanterare

Redan registrerade enheter påverkas inte av att en enhetsregistreringshanterare tas bort. När en enhetsregistreringshanterare tas bort:

-   Registrerade enheter påverkas inte och fortsätter att vara fullständigt hanterade.
-   Den borttagna enhetsregistreringshanterarens kontouppgifterna fortsätter gälla.
-   Den borttagna enhetsregistreringshanteraren kan ändå inte rensa eller dra tillbaka enheter.
-   Borttagna enhetsregistreringshanteraren kan bara registrera ett antal enheter upp till gränsen för per användare som konfigurerats av Intune-administratören.

**Ta bort en enhetsregistreringshanterare**

1. På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**.
2. Välj **Registrera enheter** på Intune-bladet och välj sedan **Enhetsregistreringshanterare**.
3. På bladet **Enhetsregistreringshanterare** högerklickar du på DEM-användaren och väljer **ta bort**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Visa egenskaper för en enhetsregistreringshanterare

1. I Intune-portalen, väljer du **Enhetsregistrering** och sedan **Enhetsregistreringshanterare**.
2. På bladet **Enhetsregistreringshanterare** högerklickar du på DEM-användaren och väljer **Egenskaper**.
