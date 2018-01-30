---
title: "Skicka loggar till företagets support för Windows 10-enheter | Microsoft Docs"
description: Registrera en Windows 10 1511-enhet i Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 038747fb-5b52-47c4-a2b6-f9218da4cfe1
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 6a0f0b566b33d09ba09aee0d479b21f58dedf489
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="send-logs-to-your-company-support-from-the-settings-app-for-windows-10"></a>Skicka loggar till företagets support från inställningsappen för Windows 10

Om du får ett felmeddelande när du använder en Windows 10-enhet som hanteras av företaget kan du hjälpa företagets support att felsöka problemet genom att skicka information via e-post. Den här informationen sparas på din enhet i ett specialdokument som kallas _diagnostiklogg_.

1.  Öppna appen **Inställningar** i Windows genom att välja **Inställningar** på **Start-menyn**. Du kan också söka efter "inställningar" i sökfältet.
2.  Gå till **Konton** > **Åtkomst till arbete eller skola**.
3.  Välj ”Exportera dina hanteringsloggfiler”.

  ![Skärmen ”Åtkomst till arbete eller skola” visar alternativet Exportera under rubriken ”Relaterade inställningar”.](./media/w10-export-logs.png)

4. Loggarna sparas i **C:\Users\Public\Public Documents\MDMDiagnostics**. Två filer skapas: en är själva loggen och den andra är ett särskilt dokument där administratören kan granska loggarna i olika program, till exempel Microsoft Excel. Bifoga båda dessa filer i ett e-postmeddelande och skicka det till administratören. Om du gör detta mer än en gång behöver du bara välja filerna från den dag då du skapade loggarna. 

Du kan också behöva skicka [loggar från företagsportalappen](send-logs-to-your-it-admin-cp-windows.md) för att företagets support ska få mer hjälp med att felsöka eventuella problem. 

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://portal.manage.microsoft.com#HelpDeskDialog).
