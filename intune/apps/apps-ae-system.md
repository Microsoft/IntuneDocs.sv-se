---
title: Lägg till Android Enterprise-systemappar i Microsoft Intune
titleSuffix: ''
description: Lär dig lägga till Android Enterprise-systemappar i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755263"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Lägg till Android Enterprise-systemappar i Microsoft Intune

Innan du tilldelar en app till en enhet eller en grupp av användare måste du först lägga till appen i Microsoft Intune. Systemappar stöds på Android Enterprise-enheter. Du kan aktivera en systemapp för [dedikerade Android Enterprise-enheter](../enrollment/android-kiosk-enroll.md) eller [fullständigt hanterade enheter](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Lägg till appen

Du kan lägga till en Android Enterprise-systemapp till Intune från Azure Portal genom att göra så här:

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Alla appar** > **Lägg till**.
3. I fönstret **Välj apptyp** väljer du **Android Enterprise-systemapp** under de tillgängliga **Övriga** typerna.
4. Klicka på **Välj**. Stegen **Lägg till app** visas.
Lägg till information om appen i fönstret **Appinformation**:
    - **Appnamn**: Ange namnet på appen.
    - **Utgivare**: Ange namnet på appens utgivare.  
    - **Paketnamn**: Ange ett paketnamn. Intune kommer att verifiera att paketnamnet är giltigt.
5. Visa sidan **Omfångstaggar** genom att klicka på **Nästa**.
8. Klicka på **Välj omfångstaggar** om du vill lägga till omfångstaggar för appen. Mer information finns i [Använda rollbaserad åtkomstkontroll (RBAC) och omfångstaggar för distribuerad IT](~/fundamentals/scope-tags.md).
9. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
10. Välj grupptilldelningar för appen. Mer information finns i [Lägga till grupper för att organisera användare och enheter](~/fundamentals/groups-add.md). 
11. Visa sidan **Granska och skapa** genom att klicka på **Nästa**. Granska värdena och inställningarna som du har angett för appen.
12. När du är färdig klickar du på **Skapa** för att lägga till appen i Intune.

**Översiktsbladet** för appen som du har skapat visas i applistan.

> [!NOTE]
> Du måste arbeta med enhetens OEM-enhet för att hitta paketnamnet för den app som du vill aktivera/inaktivera.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

Android Enterprise-appar aktiverar eller inaktiverar appar som redan ingår i plattformen. Om du vill aktivera en app tilldelar du systemappen som **Krävs**. Om du vill inaktivera en app tilldelar du systemappen som **Avinstallera**. Systemappar kan inte tilldelas som tillgängliga för en användare.


## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
