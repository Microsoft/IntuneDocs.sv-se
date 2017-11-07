---
title: "Ange utfärdare för hantering av mobila enheter"
titlesuffix: Azure portal
description: "Lär dig ange hantering av mobila enheter i Intune. \""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cee02cf20416f719771705079beae7bc986f1069
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2017
---
# <a name="set-the-mobile-device-management-authority"></a>Ange utfärdare för hantering av mobila enheter

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Inställningen av hantering av mobil enhet bestämmer hur du ska hantera dina enheter. Som IT-administratör måste du ange en utfärdare för hantering av mobila enheter innan användarna kan registrera enheter för hantering.

Möjliga konfigurationerna är:

- **Fristående Intune** – Endast molnbaserad hantering, som du konfigurerar med hjälp av Azure-portalen. Innehåller den fullständiga uppsättning funktioner som Intune erbjuder. [Ange utfärdare för hantering av mobila enheter i Intune-konsolen](#set-mdm-authority-to-intune).

- **Intune-hybrid** – Integrering av Intunes molnlösning med System Center Configuration Manager. Du kan konfigurera Intune med hjälp av Configuration Manager-konsolen. [Ange utfärdare för hantering av mobila enheter till Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Hantering av mobilenheter i Office 365** – Integrering av Office 365 med Intunes molnlösning. Du kan konfigurera Intune från administrationscentret för Office 365. Innehåller en delmängd av de funktioner som är tillgängliga i Fristående Intune. Ange utfärdare för hantering av mobila enheter i administrationscentret för Office 365.

>[!IMPORTANT]    
I Configuration Manager version 1610 och senare och i Microsoft Intune version 1705 kan du ändra MDM-utfärdaren utan att behöva kontakta Microsoft Support och utan att behöva avregistrera och omregistrera dina befintliga hanterade enheter. Mer information finns i [Vad ska jag göra om jag väljer fel inställning för MDM-utfärdare?](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Ange Intune som utfärdare för hantering av mobila enheter

1. På [Azure Portal](https://portal.azure.com) väljer du **Fler tjänster** > **Övdervakning och hantering** > **Intune**.
2. Välj den orangefärgade banderollen för att öppna inställningen **Utfärdare av Hantering av mobila enheter**.
3. Under **Utfärdare av Hantering av mobila enheter** väljer du en utfärdare bland följande alternativ:
  - **Intune-utfärdare av mobilenhetshantering**
  - **Configuration Manager-utfärdare av mobilenhetshantering**
  - **Inga**

  ![Skärmbild av Intune-skärmen Ange utfärdare för hantering av mobila enheter](media/set-mdm-auth.png)

  Ett meddelande indikerar att du har angett MDM-utfärdare till Intune.

## <a name="enable-device-enrollment"></a>Aktivera registrering av enheter

Med Intune som utfärdare för hantering av mobila enheter kan användare registrera personligt ägda enheter och få åtkomst till resurser, exempelvis e-post, på följande sätt genom att installera företagsportalen (iOS och Android) lägga till autentiseringsuppgifter för arbetet (Windows) eller få åtkomst till företagsportalens webbplats (iOS, Android, macOS).

Flera plattformar har följande krav för att aktivera eller förenkla registrering:
- **iOS** – (obligatoriskt) [Skaffa ett Apple MDM-pushcertifikat](apple-mdm-push-certificate-get.md) och därefter [aktivera registrering för företagsägda iOS-enheter](ios-enroll.md) (valfritt).
- **Android** - (obligatoriskt) [Aktivera Android-arbetsprofiler](android-enroll.md)
- **Windows** – (obligatoriskt) Aktivera [Automatisk registrering](windows-enroll.md) eller [massregistrering](windows-bulk-enroll.md)
- **macOS** – Inga krav


## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Rensa mobila enheter efter att MDM-certifikatet upphört att gälla

MDM-certifikatet förnyas automatiskt när mobila enheter kommunicerar med Intune-tjänsten. Om mobila enheter raderas eller om de inte kan kommunicera med Intune-tjänsten under en viss tidsperiod, kommer MDM-certifikatet inte att förnyas. Enheten tas bort från Azure-portalen 180 dagar efter att MDM-certifikatet har upphört att gälla.
