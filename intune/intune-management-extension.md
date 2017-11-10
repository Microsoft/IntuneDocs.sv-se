---
title: "Hantera PowerShell-skript i Intune för Windows 10-enheter"
titlesuffix: Azure portal
description: "Lär dig hur du laddar upp PowerShell-skript i Intune för att köra Windows 10-enheter."
keywords: 
author: dougeby
manager: angrobe
ms.date: 10/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b621edad5523f3c77191fb2ef8ca2ea67318dec0
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/02/2017
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Hantera PowerShell-skript i Intune för Windows 10-enheter
Intunes hanteringstillägg gör det möjligt att ladda upp PowerShell-skript i Intune för att köra Windows 10-enheter. Hanteringstillägget kompletterar funktioner för hantering av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att flytta till modern hantering.

## <a name="moving-to-modern-management"></a>Flytta till modern hantering
Slutanvändarens databehandling genomgår en digital transformation. Klassisk, traditionell IT fokuserar på en enskild enhetsplattform, företagsägda enheter, användare som arbetar från kontoret och en mängd manuella, reaktiva IT-processer. Men en modern arbetsplats har flera enhetsplattformar som är både användarägda och företagsägda, låter användarna arbeta från valfri plats och tillhandahåller automatiska och proaktiva IT-processer. 

MDM-tjänster som Microsoft Intune kan hantera Windows 10-enheter med hjälp av MDM-protokollet. Den inbyggda Windows 10-hanteringsklienten kan kommunicera med Intune för att utföra hanteringsuppgifter för företag. Den hjälper dig att satsa på modern hantering på Windows 10-enheter. Vissa funktioner som du kan behöva är dock för närvarande inte är tillgängliga i Windows 10 MDM. Till exempel, avancerad enhetskonfiguration, felsökning och äldre Win32-apphantering. För de här funktionerna kan du köra Intune-programvaruklienten på Windows 10-enheter. Därför kan du inte använda de nya funktionerna som Windows 10 MDM tillhandahåller. [Jämför Intune-programvaruklienten och Windows 10 MDM](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

Tillägget för Intune -hantering kompletterar de inbyggda funktionerna i Windows 10 MDM. Du kan skapa PowerShell-skript som tillhandahåller de funktioner som du behöver och sedan köra dessa på Windows 10-enheter. Du kan till exempel skapa ett PowerShell-skript som installerar en äldre Win32-app på Windows 10-enheter, ladda upp skriptet till Intune, tilldela det till en grupp i Azure Active Directory (AD) och sedan köra skriptet på Windows 10-enheter. Du kan sedan övervaka körstatusen för skriptet på Windows 10-enheter från början till slut.

## <a name="prerequisites"></a>Förutsättningar
Intune-hanteringstillägget har följande krav:
- Enheter måste vara domänanslutna till Azure AD
- Enheter måste köra Windows 10 version 1607 eller senare

## <a name="create-a-powershell-script-policy"></a>Skapa en princip för PowerShell-skript 
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
4. Välj **Hantera** > **PowerShell-skript** på bladet **Enhetskonfiguration**.
5. På bladet **PowerShell-skript** väljer du **Lägg till skript**.
6. Ange ett **Namn** och en **Beskrivning** för PowerShell-skriptet på bladet **Lägg till PowerShell-skript**.
7. Bläddra efter PowerShell-skriptet för att ange en **Skriptplats**. Skriptet måste vara mindre än 10 KB (ASCII) eller 5 KB (Unicode).
8. Välj **Konfigurera** och välj sedan om du vill köra skriptet med användarens autentiseringsuppgifter på enheten (**Ja**) eller i systemkontexten (**Nej**). Som standard körs skriptet i systemkontexten. Välj **Ja** om inte skriptet kräver att det körs i systemkontexten. 
  ![Bladet Lägg till PowerShell-skript](./media/mgmt-extension-add-script.png)
9. Välj om skriptet måste signeras av en betrodd utgivare (**Ja**). Som standard finns inga krav på att skriptet ska signeras. 
10. Klicka på **OK** och sedan på **Skapa** för att spara skriptet.

## <a name="assign-a-powershell-script-policy"></a>Tilldela en princip för PowerShell-skript
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
4. Välj **Hantera** > **PowerShell-skript** på bladet **Enhetskonfiguration**.
5. På bladet **PowerShell-skript** väljer du skriptet du vill tilldela och sedan **Hantera** > **Tilldelningar**.
  ![Bladet lägg till PowerShell-skript](./media/mgmt-extension-assignments.png)
 
6. Välj **Välj grupper** för en lista över tillgängliga Azure AD-grupper. 
7. Välj grupperna och klicka sedan på **Välj** för att tilldela principen till de valda grupperna.

Intune-hanteringstillägget synkroniserar till Intune en gång i timmen. När du tilldelar principen till Azure AD-grupper körs PowerShell-skriptet och körningsresultaten rapporteras. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Övervaka körningsstatus för PowerShell-skript
Du kan övervaka körningsstatusen för PowerShell-skript för användare och enheter i Azure Portal.
1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Enhetskonfiguration** på **Intune**-bladet.
4. Välj **Hantera** > **PowerShell-skript** på bladet **Enhetskonfiguration**.
5. På bladet **PowerShell-skript** väljer du skriptet som du vill övervaka och väljer sedan **Övervaka** och en av följande rapporter:
   - **Enhetstillstånd**
   - **Användarstatus**
