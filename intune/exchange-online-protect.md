---
title: Exchange utan enhetshantering
titleSuffix: Microsoft Intune
description: Använd Microsoft Intune för att ge anställda åtkomst till sina e-postkonton för Office 365 Exchange Online utan att behöva installera ett system för enhetshantering.
keywords: E-poståtkomst för Office 365 Exchange
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2017
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.topic: archived
ms.technology: ''
ms.assetid: 88a0d3b9-2622-403b-8374-1396afd8066e
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f61b7e755ea7bfe8d20c3db8c859f148dcf7704
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460435"
---
# <a name="protect-office-365-exchange-online-without-requiring-device-management"></a>Skydda Office 365 Exchange Online utan krav på enhetshantering

Om du vill ge anställda åtkomst till sina e-postkonton för arbetet utan att behöva installera ett system för enhetshantering så kan du göra det nu. Du kan ge åtkomst till Office 365 Exchange Online via Intune. Bekräfta att du har licenser för Microsoft 365 eller Azure Active Directory (premium) och Intune för att slutföra de nödvändiga stegen. Anställda behöver ha en [iOS- eller Android-enhet som stöds](supported-devices-browsers.md). 

Du kan om du vill konfigurera ett system för enhetshantering. Den här typen av appskydd fungerar oberoende av enhetshantering. 

## <a name="action-plan"></a>Åtgärdsplan

1. [Läs om villkorlig åtkomst](conditional-access.md). 
2. [Läs om appbaserad villkorlig åtkomst](app-based-conditional-access-intune.md).
3. [Konfigurera appbaserade principer för villkorlig åtkomst för Exchange Online](app-based-conditional-access-intune-create.md).
4. [Blockera appar som inte kan hanteras](app-modern-authentication-block.md), särskilt appar som inte använder Azure Active Directory Authentication Library (ADAL).
5. (Valfritt) [Konfigurera appbaserade principer för villkorlig åtkomst för SharePoint Online](app-based-conditional-access-intune-create.md). Dessa principer blockerar åtkomst till företagsdata från appar som inte kan hanteras och skyddas. Principerna kan även begränsa åtkomst via SharePoint Mobile. 

## <a name="what-to-tell-employees-and-students"></a>Information till anställda och studenter

* Be dina anställda och studenterna att ladda ned och installera Microsoft Outlook eller Microsoft SharePoint för iOS från Apple App Store eller för Android från Google Play-butiken. 
* Om du blockerar åtkomst till appar som inte använder modern autentisering bör du informera de anställda och studenter om den här begränsningen. 

## <a name="next-steps"></a>Nästa steg

Du har använt appbaserad villkorlig åtkomst för att öka säkerheten för företagets data. Som en del av nästa steg kan du lära dig mer om andra sätt att öka skyddet av företagets data, inklusive: 

* Ställ in [villkorlig tillgång baserad på enhetsefterlevnad, enhetsrisk, plats och användarattribut i Active Directory och Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).  
* Konfigurera appskyddsprinciper som hjälper dig att skydda företagets data mot avsiktligt och oavsiktligt dataläckage. 
* Använd Azure Information Protection för att skydda företagets data utanför nätverket. 

Behöver du hjälp med att aktivera det här eller andra scenarier för EMS eller Office 365? Om du har minst 150 licenser för Microsoft 365, Enterprise Mobility + Security eller Azure Active Directory Premium kan du använda dina [FastTrack-förmåner](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program). 
