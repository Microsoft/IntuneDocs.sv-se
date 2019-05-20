---
title: Konfigurera Sophos Mobile-integrering med Intune
titleSuffix: Intune on Azure
description: Konfigurera Sophos Mobile-lösningen med Microsoft Intune för att styra mobil enhetsåtkomst till företagets resurser.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/30/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67f3f329cb66716a2126f47eb2984ca26854b6de
ms.sourcegitcommit: b1ad73f5c9fd0ad8026c572aef8d15e258951c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64880762"
---
# <a name="integrate-sophos-mobile-with-intune"></a>Integrera Sophos Mobile med Intune  

Utför följande steg när du ska integrera Sophos Mobile Threat Defense-lösningen med Intune.  

## <a name="before-you-begin"></a>Innan du börjar  

Se till att du har följande innan du börjar integrera Sophos Mobile med Intune:  
- Microsoft Intune-prenumeration  
- Azure Active Directory-administratörsautentiseringsuppgifter som beviljar följande behörigheter:  
  - Logga in och läsa användarprofil  
  - Gå till katalogen som den inloggade användaren  
  - Läs katalogdata  
  - Skicka enhetsinformation till Intune  
- Administratörsinloggning för åtkomst till administratörskonsolen för Sophos Mobile.  


### <a name="sophos-mobile-app-authorization"></a>Behörighetskontroll av Sophos Mobile-appen  
  
Det här är processen för behörighetskontroll av Sophos Mobile-appen:  
- Tillåt att Sophos Mobile-tjänsten förmedlar information om enhetens hälsostatus till Intune.  
- Sophos Mobile fyller enhetens databas genom att synkronisera med registreringsgruppmedlemskapet i Azure AD.  
- Tillåt att Sophos Mobile-administratörskonsolen använder enkel inloggning för Azure AD.  
- Tillåt att Sophos Mobile-appen loggar in med enkel inloggning för Azure AD.  


## <a name="to-set-up-sophos-mobile-integration"></a>Konfigurera Sophos Mobile-integreringen  

1. Logga in på [Azure-portalen]( https://portal.azure.com/), gå till **Intune** > **Enhetsefterlevnad** > **Mobile Threat Defense** > och välj **Lägg till**.  
2. På sidan **Lägg till anslutningsapp** använder du listrutan och väljer **Sophos**. Välj sedan **Skapa**.  
3. Klicka på länken *Open the Sophos admin console* (Öppna Sophos-administratörskonsolen).  
4. Logga in på [Sophos-administratörskonsolen](https://central.sophos.com/) med dina autentiseringsuppgifter för Sophos.  
5. Gå till **Mobile** > **Inställningar** > **Installation** > **Sophos Setup** (Sophos-installation).  
6. På **Sophos-installationssidan** väljer du fliken **Intune MTD**.  
   ![Sophos-installation](./media/sophos-mtd-connector-integration/sophos-setup.png) 
 
7. Välj **Bind** (Binda) och välj sedan **Ja**. Sophos ansluter till Intune och kräver att du loggar in på Intune-prenumerationen. 
8. I fönstret för Microsoft Intune-autentisering anger du dina autentiseringsuppgifter för Intune och **godkänner** behörighetsbegäran för *Sophos Mobile Thread Defense*.  
   ![Intune-autentisering](./media/sophos-mtd-connector-integration/intune-authentication.png)

9. På **Sophos-installationssidan** väljer du **Spara** för att slutföra konfigurationen för Intune:  
   ![Spara Sophos-installation](./media/sophos-mtd-connector-integration/save-sophos-configuration.png)  

1. När meddelandet **Successful Integration** (Integrering klar) visas är integreringen slutförd.  
1. Sophos är nu tillgängligt i Intune-konsolen.  


## <a name="next-steps"></a>Nästa steg  
[Konfigurera klientapparna för Sophos](mtd-apps-ios-app-configuration-policy-add-assign.md)
