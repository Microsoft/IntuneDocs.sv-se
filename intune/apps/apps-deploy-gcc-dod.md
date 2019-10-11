---
title: Appar för GCC High- och DoD-miljöer
titleSuffix: Microsoft Intune
description: Läs mer om appar som rör GCC High- och DoD-miljöer med hjälp av Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d414899b6146afbe2c5ac119193fe0e59aa719b
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71939982"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>Distribution av appar med hjälp av Intune i GCC High- och DoD-miljöer 

Microsoft Intune kan användas av klientorganisationsadministratörer för att distribuera appar till deras arbetsstyrka. Arbetsstyrkan består av företagets anställda, som är appens användare. Det finns många typer av appar som kan distribueras från Intune på GCC High- eller DoD-miljöer. Om en administratör behöver ladda upp och distribuera en Windows-app som är avsedd för en GCC High- och DoD--målgrupp som är specialanpassad, skapad av tredjepartsleverantörer eller som en offline-app som laddats ned från [Microsoft Store för företag](https://businessstore.microsoft.com/store) kan administratören välja att distribuera den som en [verksamhetsspecifik app](apps-add.md#app-types-in-microsoft-intune).  

> [!NOTE]
> För kommersiella miljöer kan en klientorganisationsadministratör synkronisera sin Store för företag med Intune, men den här tjänsten är inte tillgänglig för GCC High- och DoD-miljöer. I den här situationen måste administratörer distribuera en app genom att ladda upp direkt till Intune.  

## <a name="add-line-of-business-apps-using-intune"></a>Lägga till verksamhetsspecifika appar med hjälp av Intune 

För att lägga till en verksamhetsspecifik app som avses för en GCC High- eller DoD-miljö med hjälp av Intune kan du följa anvisningarna för [verksamhetsspecifika Windows-appar](lob-apps-windows.md). Du kan välja att distribuera företagsportalen först från Microsoft Store för företag. Om du väljer att använda företagsportalen kan du manuellt installera och distribuera företagsportalen. Mer information finns i [Så konfigurerar du Microsoft Intune-företagsportalappen](company-portal-app.md). 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>Distribuera offline-appar från Store för företag med hjälp av Intune  

Om du behöver [ladda ned en offline-licensierad app](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app) från Microsoft Store för företag följer du stegen nedan för att ladda ned programmet: 

1. Logga in på [Store för företag](https://businessstore.microsoft.com/).
2. Välj **Hantera** > **Inställningar**.
3. Under **Shopping Experience** (Shoppingupplevelse) anger du **Show offline apps** (Visa offline-appar) till **På**.

När du köper appar kan du välja att ändra licenstypen till offline om det finns en offline-version tillgänglig. När du har skaffat appen kan du hantera den genom att välja **Hantera** > **Produkter och tjänster** i [Store för företag](https://businessstore.microsoft.com/). Dessutom kan du ladda ned appen och dess beroenden. Du kan sedan distribuera den här nedladdade appen (och dess beroenden) till användare med hjälp av Intune.  

## <a name="syncing-intune-to-the-store-for-business"></a>Synkronisera Intune till Store för företag 

I en kommersiell miljö (inte för myndigheter) kan en administratör synkronisera Intune till Microsoft Store för företag. Den här funktionen är inte tillgänglig i myndighetsmiljöer. Mer information om skillnaderna mellan Intune i kommersiella miljöer och Intune för myndighetsmiljöer finns i [beskrivningen av tjänsten Enterprise Mobility + Security för amerikanska myndigheter](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description).  

Information om hur du synkroniserar ditt Store för företag-konto finns i [Så hanterar du appar som du har köpt från Microsoft Store för företag med Microsoft Intune](windows-store-for-business.md).  

## <a name="compliance"></a>Efterlevnad 

Granska sekretess- och efterlevnadspolicyerna för appar och jämför dem med din organisations krav för efterlevnad, säkerhet och sekretess när du bedömer lämplig användning av dessa tjänster.   

## <a name="next-steps"></a>Nästa steg

Mer information om distribution och tilldelning av appar finns i [Tilldela appar till grupper med Microsoft Intune](apps-deploy.md).

 
