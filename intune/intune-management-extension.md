---
title: Lägga till PowerShell-skript i Microsoft Intune för Windows 10-enheter – Azure | Microsoft Docs
description: Lägg till PowerShell-skript, tilldela skriptprincipen till Azure Active Directory-grupper, övervaka skripten med hjälp av rapporter och följ stegvisa anvisningar för att ta bort skript som du lägger till för Windows 10-enheter i Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ad8e874dda47b7c6deeb614b0f893f7c922241ce
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236347"
---
# <a name="manage-powershell-scripts-in-intune-for-windows-10-devices"></a>Hantera PowerShell-skript i Intune för Windows 10-enheter
Intunes hanteringstillägg gör det möjligt att ladda upp PowerShell-skript i Intune för att köra Windows 10-enheter. Hanteringstillägget kompletterar funktioner för hantering av mobilenheter (MDM) i Windows 10 och gör det enklare för dig att flytta till modern hantering.

## <a name="moving-to-modern-management"></a>Flytta till modern hantering
Slutanvändarens databehandling genomgår en digital transformation. Klassisk, traditionell IT fokuserar på en enskild enhetsplattform, företagsägda enheter, användare som arbetar från kontoret och en mängd manuella, reaktiva IT-processer. Men en modern arbetsplats har flera enhetsplattformar som är både användarägda och företagsägda, låter användarna arbeta från valfri plats och tillhandahåller automatiska och proaktiva IT-processer. 

MDM-tjänster som Microsoft Intune kan hantera Windows 10-enheter med hjälp av MDM-protokollet. Den inbyggda Windows 10-hanteringsklienten kan kommunicera med Intune för att utföra hanteringsuppgifter för företag. Den hjälper dig att satsa på modern hantering på Windows 10-enheter. Vissa funktioner som du kan behöva är dock för närvarande inte är tillgängliga i Windows 10 MDM. Till exempel, avancerad enhetskonfiguration, felsökning och äldre Win32-apphantering. För de här funktionerna kan du köra Intune-programvaruklienten på Windows 10-enheter. Därför kan du inte använda de nya funktionerna som Windows 10 MDM tillhandahåller. [Jämför Intune-programvaruklienten och Windows 10 MDM](https://docs.microsoft.com/intune-classic/deploy-use/pc-management-comparison).

Tillägget för Intune -hantering kompletterar de inbyggda funktionerna i Windows 10 MDM. Du kan skapa PowerShell-skript som tillhandahåller de funktioner som du behöver och sedan köra dessa på Windows 10-enheter. Du kan till exempel skapa ett PowerShell-skript som installerar en äldre Win32-app på Windows 10-enheter, ladda upp skriptet till Intune, tilldela det till en grupp i Azure Active Directory (AD) och sedan köra skriptet på Windows 10-enheter. Du kan sedan övervaka körstatusen för skriptet på Windows 10-enheter från början till slut.

## <a name="prerequisites"></a>Krav
Intune-hanteringstillägget har följande krav:
- Enheter måste vara domänanslutna till Azure AD. Intune-hanteringstillägget har stöd för Azure Active Directory-anslutna, hybriddomänanslutna och samhanterade registrerade Windows-enheter.
- Enheter måste köra Windows 10 version 1607 eller senare.
- Automatisk MDM-registrering måste vara [aktiverat i Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) och enheter måste registreras automatiskt i Intune.

## <a name="create-a-powershell-script-policy"></a>Skapa en princip för PowerShell-skript 
1. Logga in på [Azure Portal](https://portal.azure.com).
2. Välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
3. Välj **Enhetskonfiguration** > **PowerShell-skript** > **Lägg till**.
4. Ange ett **namn** och en **beskrivning** för PowerShell-skriptet. Navigera till PowerShell-skriptet för att ange **platsen för skriptet**. Skriptet måste vara mindre än 200 kB (ASCII) eller 100 kB (Unicode).
5. Välj **Konfigurera**. Välj sedan att köra skriptet med användarens autentiseringsuppgifter på enheten (**Ja**), eller i systemkontexten (**Nej**). Som standard körs skriptet i systemkontexten. Välj **Ja** om inte skriptet kräver att det körs i systemkontexten. 
  ![Fönstret Lägg till PowerShell-skript](./media/mgmt-extension-add-script.png)
6. Välj om skriptet måste signeras av en betrodd utgivare (**Ja**). Som standard finns inga krav på att skriptet ska signeras. 
7. Välj **OK** och sedan **Skapa** för att spara skriptet.

## <a name="assign-a-powershell-script-policy"></a>Tilldela en princip för PowerShell-skript
1. Välj det skript som du vill tilldela i fönstret **PowerShell-skript** och välj sedan **Hantera** > **Tilldelningar**.
  ![Fönstret Lägg till PowerShell-skript](./media/mgmt-extension-assignments.png)
 
2. Välj **Välj grupper** för en lista över tillgängliga Azure AD-grupper. 
3. Välj en eller flera grupper som innehåller de användare vars enheter skriptet ska köras på. **Välj** att tilldela principen till de valda grupperna.

> [!NOTE]
> - PowerShell-skript kan inte tillämpas på datorgrupper.
> - Slutanvändare behöver inte vara inloggade på enheten för att köra PowerShell-skript. 
> - PowerShell-skript i Intune kan riktas till säkerhetsgrupper för AAD-enheter.

Intune-hanteringstillägget synkroniserar till Intune en gång i timmen. När du tilldelar principen till Azure AD-grupper körs PowerShell-skriptet och körningsresultaten rapporteras. 
 
## <a name="monitor-run-status-for-powershell-scripts"></a>Övervaka körningsstatus för PowerShell-skript
Du kan övervaka körningsstatusen för PowerShell-skript för användare och enheter i Azure Portal.

Välj det skript som du vill övervaka i fönstret **PowerShell-skript**, välj **Övervaka** och välj sedan någon av följande rapporter:
   - **Enhetstillstånd**
   - **Användarstatus**

## <a name="delete-a-powershell-script"></a>Ta bort ett PowerShell-skript
Högerklicka på skriptet i fönstret **PowerShell-skript** och välj **Ta bort**.
