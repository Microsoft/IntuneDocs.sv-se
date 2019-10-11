---
title: Lägg till Android Enterprise-systemappar i Microsoft Intune
titleSuffix: ''
description: Lär dig lägga till Android Enterprise-systemappar i Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c07ce82bbc056e1d76abeb5d31bf57e0973fad6e
ms.sourcegitcommit: bdf948be824cf5390d5166a277f389f3785c81f9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960886"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Lägg till Android Enterprise-systemappar i Microsoft Intune

Innan du tilldelar en app till en enhet eller en grupp av användare måste du först lägga till appen i Microsoft Intune. Systemappar stöds på Android Enterprise-enheter. Du kan aktivera en systemapp för [dedikerade Android Enterprise-enheter](../enrollment/android-kiosk-enroll.md) eller [fullständigt hanterade enheter](../enrollment/android-fully-managed-enroll.md).

## <a name="add-the-app"></a>Lägg till appen

Du kan lägga till en Android Enterprise-systemapp till Intune från Azure Portal genom att göra så här:

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. I fönstret **Intune** väljer du **Klientappar** > **Appar** > **Lägg till**.
3. I fönstret **Lägg till App** väljer du **Android Enterprise-systemapp** under de tillgängliga **Övriga** typerna.
4. Om du vill konfigurera information om appen väljer du **Konfigurera** och anger följande information:
    - **Appnamn**: Ange namnet på appen.
    - **Utgivare**: Ange namnet på appens utgivare.  
    - **Paketnamn**: Ange ett paketnamn. Intune kommer att verifiera att paketnamnet är giltigt.
5. Välj **OK**.
6. Välj **Lägg till**.

> [!NOTE]
> Du måste arbeta med enhetens OEM-enhet för att hitta paketnamnet för den app som du vill aktivera/inaktivera.

Appen som du har skapat visas i applistan där du kan tilldela den till de grupper du väljer. 

Android Enterprise-appar aktiverar eller inaktiverar appar som redan ingår i plattformen. Om du vill aktivera en app tilldelar du systemappen som **Krävs**. Om du vill inaktivera en app tilldelar du systemappen som **Avinstallera**. Systemappar kan inte tilldelas som tillgängliga för en användare.


## <a name="next-steps"></a>Nästa steg

- [Tilldela appar till grupper](apps-deploy.md)
