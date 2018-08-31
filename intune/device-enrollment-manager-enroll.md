---
title: Registrera enheter med ett konto för enhetsregistreringshanteraren
titlesuffix: Microsoft Intune
description: Använda kontot för enhetsregistreringshanteraren för att registrera flera enheter i Intune. "
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce785ad7898f9e792feeadcd1623bd0989f0d6d0
ms.sourcegitcommit: 40b1d82df99f09a75a17065cdd0e84d8038f460a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40255561"
---
# <a name="enroll-devices-by-using-a-device-enrollment-manager-account"></a>Registrera enheter med ett konto för enhetsregistreringshanteraren

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Organisationer kan använda Intune för att hantera ett stort antal mobila enheter med ett enda användarkonto. Kontot för *enhetsregistreringshanterare* (DEM) är ett särskilt användarkonto som kan registrera upp till 1 000 enheter. Du lägger till befintliga användare i DEM-kontot för att ge dem särskilda DEM-alternativ. Varje registrerad enhet använder en enda licens. Vi rekommenderar att du använder enheter som registrerats via det här kontot som delade enheter snarare än personliga enheter (BYOD).  

Användarna måste finnas i [Azure-portalen](https://portal.azure.com) för att kunna läggas till som enhetsregistreringshanterare. Du får bästa möjliga säkerhet om DEM-användaren inte samtidigt är en Intune-administratör.

>[!NOTE]
>DEM-registreringsmetoden går inte att använda med de här andra registreringsmetoderna: [Apple Configurator med installationsassistenten](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator med direktregistrering](apple-configurator-direct-enroll-ios.md), [Apple School Manager (ASM)](apple-school-manager-set-up-ios.md), eller [programmet för enhetsregistrering (DEP)](device-enrollment-program-enroll-ios.md).

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exempelscenario för enhetsregistreringshanterare

En restaurang vill tillhandahålla 50 surfplattor vid kassan för servitörerna. Kökspersonalen behöver också surfplattor för att se beställningarna. De anställda behöver aldrig ha tillgång till företagets data eller logga in som användare. Intune-administratören skapar ett nytt konto för enhetsregistreringshantering för restaurangchefen.  Det här är ett annat konto än chefens primära konto och används bara till att registrera delade enheter i Intune. Chefen kan nu registrera de 50 surfplattorna med hjälp av DEM-autentiseringsuppgifter.

Det är bara användare i [Azure-portalen](https://portal.azure.com) som kan vara enhetsregistreringshanterare. Den användare som är enhetsregistreringshanterare får inte vara Intune-administratör.

DEM-användaren kan:

-   Registrera upp till 1000 enheter i Intune
-   Logga in på företagsportalen och hämta företagsappar
-   Konfigurera åtkomst till företagets data genom att distribuera rollspecifika appar till surfplattorna

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Begränsningar för enheter som registreras med ett DEM-konto

Enheter som har registrerats med ett konto för enhetsregistreringshantering har följande begränsningar:

  - Ingen åtkomst per användare. Eftersom enheter inte har en tilldelad användare har enheten ingen åtkomst till e-post eller företagsdata. VPN-konfigurationer, till exempel, skulle fortfarande kunna användas för att ge enhetens appar åtkomst till data.
  - DEM-användaren kan inte avregistrera DEM-registrerade enheter på själva enheten genom företagsportalen. Intune-administratören kan avregistrera enheter.
  - Endast den lokala enheten visas i företagsportalappen eller webbplatsen.
  - Användare kan inte använda apparna för Apples volymköpsprogram (VPP) med användarlicenser på grund av Apple-ID-kraven per användare för apphantering.
  - (Endast iOS) Om du använder DEM för att registrera iOS-enheter, kan du inte använda Apple Configurator, Apples program för enhetsregistrering (DEP) eller Apple School Manager (ASM) för att registrera enheter.
  - (Endast Android) Det finns en gräns för hur många Android-arbetsprofilenheter som kan registreras med ett enda DEM-konto. Upp till tio enheter med Android-arbetsprofiler kan registreras per DEM-konto. Den här begränsningen gäller inte för äldre Android-registrering.
  - Enheter kan installera VPP-appar om de har enhetslicenser.
  - Det krävs ingen Intune-enhetslicens för att använda DEM. Läs mer om [användar- och enhetslicenser](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Du kan distribuera företagsappar till enheter som hanteras av enhetsregistreringshanteraren. Distribuera företagsportalappen som **Nödvändig installation** till enhetsregistreringshanterarens användarkonto.
> I syfte att förbättra prestanda visas endast den lokala enheten i företagsportalappen på en DEM-enhet. Fjärrhantering av andra DEM-enheter kan bara utföras från Intune-administratörskonsolen.


## <a name="add-a-device-enrollment-manager"></a>Lägg till en enhetsregistreringshanterare

1.  I [Intune på Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** > **Enhetsregistreringshanterare**.

2.  Välj **Lägg till**.

3.  På bladet **Lägg till användare** anger du ett huvudnamn för DEM-användaren och väljer **Lägg till**. DEM-användaren läggs till i listan över DEM-användare.

## <a name="permissions-for-dem"></a>Behörigheter för DEM

Azure AD-rollerna Global eller Intune-tjänstadministratör krävs för att
- utföra uppgifter relaterade till DEM-registrering i administrationsportalen
- visa alla DEM-användare trots att RBAC-behörigheter visas och är tillgängliga under den anpassade användarrollen.

En användare som inte har tilldelats rollen Global administratör eller Intune-tjänstadministratör, men som har läsbehörigheter för rollen Enhetsregistreringshanterare, kan bara se de DEM-användare som de har skapat. RBAC-rollstöd för dessa funktioner kommer att finnas i framtiden.


## <a name="remove-a-device-enrollment-manager"></a>Ta bort en enhetsregistreringshanterare

När en enhetsregistreringshanterare tas bort:

-   Registrerade enheter påverkas inte och fortsätter att vara fullständigt hanterade.
-   De borttagna autentiseringsuppgifterna för DEM-kontot är fortfarande giltiga.
-   Borttagen DEM kan fortfarande inte rensa eller dra tillbaka enheter.
-   Borttagen DEM kan bara registrera enheter upp till gränsen som Intune-administratören konfigurerat per användare.

**Ta bort en enhetsregistreringshanterare**

1. I [Intune i Azure Portal](https://aka.ms/intuneportal) väljer du **Enhetsregistrering** och sedan **Enhetsregistreringshanterare**.
2. På bladet **Enhetsregistreringshanterare** väljer du enhetsregistreringshanteraren och **Ta bort**.

