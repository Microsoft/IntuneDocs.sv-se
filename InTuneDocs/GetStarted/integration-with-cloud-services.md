---
title: "Intune-integration med Microsofts molntjänster | Microsoft Intune"
description: "Intune-integration med Microsofts molntjänster och andra Microsoft-produkter"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 6523c731e8351b121cba46f6c5d2ef46db656c2c


---

# Intune-integration med Microsofts molntjänster och produkter

Innan du konfigurerar [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] går du igenom det här avsnittet och andra krav som anges i [Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).
##Integrering med andra Microsoft-molntjänster


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] delar en gemensam grund med andra Microsoft-molntjänster. När du använder samma konto för att prenumerera på flera molntjänster, använder tjänsterna samma Microsoft Azure AD-infrastruktur och är innehavare av Azure AD. Azure AD innehåller kärnkatalog- och identitetshanteringsfunktioner för Microsofts molntjänster.

Lär dig mer om att [administrera Azure AD ](http://technet.microsoft.com/library/hh967611.aspx) i TechNet-biblioteket.

## Integrering med andra Microsoft-produkter
Du kan använda [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] som en fristående molntjänst eller som en tjänst i molnet som är integrerad med andra produkter. För närvarande kan endast [!INCLUDE[cmshort](../includes/cmshort_md.md)] integreras direkt med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Beslutet att integrera [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] med [!INCLUDE[cmshort](../includes/cmshort_md.md)] är ett permanent val som kräver att du anger hanteringsplatsen för mobila enheter från [!INCLUDE[cmshort](../includes/cmshort_md.md)]-konsolen och inte inifrån [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]. När du har angett enhetsplatsen för den mobila enheten, kan du inte ändra eller ångra konfigurationen.

När du använder [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] med [!INCLUDE[cmshort](../includes/cmshort_md.md)] använder du inte [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] för att hantera [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] utan använder istället [!INCLUDE[cmshort](../includes/cmshort_md.md)]-konsolen. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] använder fortfarande sin molnlagring i Azure för att vara värd för de program som du distribuerar till enheter som du hanterar med [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

Mer information finns i [Hantera mobila enheter med Configuration Manager och Microsoft Intune](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10) i  [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1-dokumentationen.

### Se även
[Vad du behöver veta innan du startar Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


