---
title: Lägga till och tilldela företagsportalappen för Windows 10 för Autopilot-etablerade enheter
titleSuffix: Microsoft Intune
description: Lägg till och tilldela företagsportalappen för Windows 10 i Intune för Autopilot-etablerade enheter.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577291"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>Lägga till och tilldela företagsportalappen för Windows 10 för Autopilot-etablerade enheter

Din användare kan använda företagsportalappen för att hantera enheter och installera appar. Du kan tilldela företagsportalappen för Windows 10 direkt från Intune. 

## <a name="prerequisites"></a>Krav

För Windows 10 Autopilot-etablerade enheter rekommenderar vi att du kopplar ditt Microsoft Store för företag-konto till Intune. Mer information finns i [Så här hanterar du volymköpta appar från Microsoft Store för företag med Microsoft Intune](~/apps/windows-store-for-business.md).

Företagsportal (offline) installeras med hjälp av anvisningarna nedan. Företagsportalappen installeras i enhetskontexten när den tilldelas till gruppen Autopilot och installeras på enheten innan användaren loggar in. 

## <a name="configure-settings-to-show-offline-apps"></a>Konfigurera inställningar för att visa offlineappar
1. Logga in på [Microsoft Store för företag](https://www.microsoft.com/business-store) med ditt administratörskonto.
2. Välj fliken **Hantera** i fönstrets överkant.
3. Välj **Inställningar** i rutan till vänster.
4. Ställ in **Visa offlineappar** i avsnittet om **shoppingupplevelsen** till **På**.  
    Offlinelicensierade appar visas.

## <a name="get-the-offline-company-portal-app"></a>Hämta offlineappen Företagsportal
1. Sök och välj appen **Företagsportal**.
2. Ange **Licenstyp** till **Offline**.
3. Välj **Hämta appen** för att hämta och lägga till offlineappen Företagsportal i inventeringen.

## <a name="assign-the-company-portal-app"></a>Tilldela appen Företagsportal
1. Logga in på  [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) med ditt administratörskonto. 
2. Välj fliken **Appar** i det högra fönstret. 
3. Välj **Windows** under  **Per plattform**. 
4. Välj **Företagsportal (offline)** .   
5. Du måste antingen vänta tills synkroniseringsschemat har slutförts eller göra en manuell synkronisering från administrationscentret för Microsoft Endpoint Manager.
6. Tilldela företagsportalappen som en obligatorisk app till dina valda Autopilot-enhetsgrupper.

## <a name="next-steps"></a>Nästa steg

- Mer information om hur du tilldelar appar finns i [Tilldela appar till grupper](apps-deploy.md).

