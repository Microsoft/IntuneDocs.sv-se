---
title: "Supportavdelningens felsökningsportal"
titleSuffix: Intune on Azure
description: "Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: c932781f988d63395b98452a4f4739e0bce1d9c8
ms.sourcegitcommit: ce8a1f0f4e95444949556600d1837937b6efd769
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/28/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>Använd felsökningsportalen för att hjälpa användare

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I felsökningsportalen kan supportansvariga och Intune-administratörer se användarinformation för att tillgodose användarnas begäran om hjälp. Organisationer med supportansvariga bland personalen kan tilldela rollen **Supportansvarig** till en grupp användare. Användare i gruppen kan då sedan använda felsökningsbladet till att hjälpa användare.

När t.ex. en användare kontaktar supporten om ett tekniskt problem i Intune kan supportansvarig ange användarens namn. Intune visar användbara data som kan hjälpa dig att lösa många nivå 1-problem, inklusive:
- Användarstatus
- Tilldelningar
- Efterlevnadsproblem
- Enheten svarar inte
-   Enheten saknar VPN- eller Wi-Fi-inställningar
-   Appinstallationsfel

## <a name="add-help-desk-operators"></a>Lägga till supportansvariga
I egenskap av Intune-administratör kan du tilldela rollen Supportansvarig till en användargrupp. Medlemmar i gruppen kan använda administrationsportalen för att felsöka användarnas problem. Varje supportansvarig måste ha en Intune-licens för åtkomst till Intune-portalen. Lär dig [tilldela Intune-användarlicenser](licenses-assign.md).

Lägga till supportanvändare:
1. [Lägg till användare i Intune](users-add.md) vid behov.
2. [Skapa en supportgrupp](groups-add.md) och lägg till användare i gruppen.
3. [Tilldela rollen RBAC-supportansvarig](role-based-access-control.md#built-in-roles).

  ![Bild av Intune-portalen med Intune-roller markerat och en lista över inbyggda roller, inklusive Supportansvarig](./media/help-desk-user-add.png) Du kan även [skapa en anpassad roll](role-based-access-control.md#custom-roles) som du kan ändra ytterligare för att ge åtkomst till supportansvariga.  Supportansvariga kräver följande behörigheter för att felsöka användarproblem:
    - MobileApps: Läsbehörighet
    - ManagedApps: Läsbehörighet
    - ManagedDevices: Läsbehörighet
    - Organization: Läsbehörighet
    - DeviceCompliancePolices: Läsbehörighet
    - DeviceConfigurations: Läsbehörighet

4. Om du vill ge supportoperatörer behörighet att visa tjänstens hälsa och öppna supportärenden för Intune ska du [bevilja användarna administratörsbehörighet](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal) som **Tjänstadministratör**. Ge inte behörigheten **Intune-tjänstadministratör** eftersom den här katalogrollen har fler behörigheter än vad som krävs för supportoperatörer.

## <a name="access-the-troubleshooting-portal"></a>Åtkomst till felsökningsportalen

Supportpersonal och Intune-administratörer kan få åtkomst till felsökningsportalen på två sätt:
- Öppna [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) i en webbläsare för att se bara felsökningsportalen.
  ![Skärmbild av felsökningskonsolen](./media/help-desk-console.png)
- Logga in på Azure-portalen, välj **Fler tjänster** > **Övervakning + hantering** > **Intune** och gå sedan till **Hjälp och support** > **Felsök**.

Klicka på **Välj användare** för att visa en användare och dennes användarinformation.

## <a name="use-the-troubleshooting-portal"></a>Använda felsökningsportalen

I felsökningsportalen kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter. Felsökningsportalen visar följande felsökningsinformation:
- **Kontostatus**
- **Användarstatus**
- **Enheter** med enhetsåtgärder
- **Gruppmedlemskap**
- **Appskyddsstatus**
