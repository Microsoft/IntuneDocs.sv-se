---
title: "Supportavdelningens felsökningsportal"
titleSuffix: Intune on Azure
description: "Supportavdelningen använder felsökningsportalen till att lösa användarnas tekniska problem"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>Hjälpa användarna med felsökningsportalen i Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I felsökningsportalen kan supportansvariga och Intune-administratörer visa användarinformation för att tillgodose användarnas begäran om hjälp. Organisationer med supportansvariga bland personalen kan tilldela rollen **Supportansvarig** till en grupp användare. Användare i gruppen kan då sedan använda felsökningsbladet till att hjälpa användare.

När t.ex. en användare kontaktar supporten om ett tekniskt problem i Intune kan supportansvarig ange användarens namn. Intune visar relevant information som kan hjälpa supportpersonalen att lösa många nivå 1-problem som användarstatus, appinstallationsfel eller efterlevnadsproblem. Bland sådana problem inkluderar följande:
- Enheten svarar inte
-   Enheten saknar VPN- eller Wi-Fi-inställningar
-   Appinstallationsfel


## <a name="add-help-desk-operators"></a>Lägga till supportansvariga
En Intune-administratör kan tilldela supportansvariga behörigheter för användare på två sätt:
- Tilldela den inbyggda rollen **Supportansvarig**
- Skapa och tilldela en anpassad roll

## <a name="assign-help-desk-operator-role"></a>Tilldela rollen Supportansvarig
I egenskap av Intune-administratör kan du tilldela rollen Supportansvarig till en användargrupp. Medlemmar av den gruppen kan använda administrationsportalen. Varje supportansvarig måste ha en Intune-licens för åtkomst till Intune-portalen. Lär dig [tilldela Intune-användarlicenser](licenses-assign.md).

1. Logga in på Intune-portalen som Intune-administratör och välj **Intune-roller**.
2. I arbetsbelastningen **Intune-roller** väljer du **Supportansvarig** > **Tilldelningar** och sedan **Tilldela**.
  ![Bild av Intune-portalen med Intune-roller markerat och en lista över inbyggda roller, inklusive Supportansvarig med Tilldelningar markerat och en röd ram runt Tilldela](./media/help-desk-user-assign.png)
3. Skriv ett **Namn på tilldelning** (obligatoriskt), en **Tilldelningsbeskrivning** (valfritt) och tilldela sedan **Medlemmar (grupper)** och **Omfång (grupper)**.
4. Medlemmar i rollen som supportansvarig kan nu använda felsökningsportalen.

Mer information om Intune-roller finns i [Intune-roller (RBAC)](role-based-access-control.md).

## <a name="create-a-custom-role-for-troubleshooting"></a>Skapa en anpassad roll för felsökning
I egenskap av Intune-administratör kan du skapa en anpassad roll som låter användare använda felsökningsportalen med de behörigheter som passar organisationens behov. Mer information om Intune-roller finns i [Intune-roller (RBAC)](role-based-access-control.md).

![Skärmbild av Intune-portalen med Intune-roller markerat och en lista över inbyggda roller, inklusive Supportansvarig](./media/help-desk-user-add.png)

Om du vill använda Intune-konsolen för en supportvy, ska en anpassad supportroll ha följande behörigheter:
- MobileApps: Läsbehörighet
- ManagedApps: Läsbehörighet
- ManagedDevices: Läsbehörighet
- Organization: Läsbehörighet

## <a name="access-the-troubleshooting-portal"></a>Åtkomst till felsökningsportalen

Supportpersonal och Intune-administratörer kan få åtkomst till felsökningsportalen på två sätt:
- Öppna [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting) i en webbläsare.
- I Intune-portalen går du till **Hjälp och support** > **Felsök**.

![Skärmbild av Intunes arbetsbelastning för felsökning med länken Välj användare](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>Använda felsökningsportalen

I felsökningsportalen kan du välja **Välj användare** för att visa information om en användare. Med hjälp av användarinformation kan du få en bättre förståelse för det aktuella tillståndet för användarna och deras enheter. Felsökningsportalen visar följande felsökningsinformation:
- **Status för klient**
- **Användarstatus**
- **Enheter** och enhetsåtgärder
- **Gruppmedlemskap**
- **Appskyddsstatus**
