---
title: "Förbered konfigurationen av appskyddsprinciper för Windows 10"
titlesuffix: Azure portal
description: Konfigurera MAM-providern i Azure AD
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f4b6a442f83491160f72955d02b8023ee4d949f2
ms.sourcegitcommit: 468480b61110ca81f737582ebbefd4efda6fd667
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Förbered konfigurationen av appskyddsprinciper för Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Aktivera hantering av mobilprogram (MAM) för Windows 10 genom att ange MAM-providern i Microsoft Azure Active Directory. Genom att ställa in MAM-providern i Microsoft Azure Active Directory kan du definiera registreringstillståndet när du skapar en ny Windows Information Protection-princip (WIP) med Intune. Registreringstillståndet kan vara MAM eller hantering av mobila enheter (MDM).

> [!NOTE]
> Enheter med tillståndet MAM-registrering måste vara anslutna till Azure AD.

## <a name="to-configure-the-mam-provider"></a>Konfigurera MAM-providern

1. Logga in på Azure Portal och välj **Azure Active Directory.**

2. Välj **Mobility (MDM och MAM)** i gruppen **Hantera**.

3. Klicka på **Microsoft Intune**.

4. Konfigurera inställningar i gruppen **Återställ standard MAM-URL:er** på bladet **Konfigurera**.

    **MAM-användaromfattning**  
      Använd MA- autoregistrering för att hantera företagsdata på Windows-enheter för dina anställda. MAM-autoregistrering kommer att konfigureras för Bring Your Own Device-scenarier.<ul><li>**Inga**<br>Välj om alla användare kan registreras på MAM.</li><li>**Vissa**<br>Välj Microsoft Azure Active Directory-grupper som innehåller användare som ska registreras på MAM.</li><li>**Alla**<br>Välj om alla användare kan registreras på MAM.</li></ul>

    **Webbadress till MAM-användarvillkor**  
     URL för användarvillkor för MAM-tjänstens slutpunkt. Slutpunkten för användarvillkoren används för att visa användningsvillkoren för slutanvändarna innan de registrerar sina enheter för hantering. Texten för användarvillkor informerar användare om de principer som tillämpas på den mobila enheten.

    **Webbadress till MAM-identifiering**  
    URL till slutpunkten för registrering av MAM-tjänsten. Registrering av slutpunkten används för att registrera enheter för hantering med MAM-tjänsten.

    **MAM kompatibilitets-URL**  
      URL till slutpunkten för efterlevnad av MAM-tjänsten. När en användare nekas åtkomst till en resurs från en icke-kompatibel enhet visas en länk till URL:en för efterlevnad för användaren. För att förstå varför deras enhet betraktas som icke-kompatibel kan användare navigera till den URL som MAM-tjänsten är värd för. Användare kan också initiera hjälpåtgärder i självbetjäningen så att enheten blir kompatibel och de kan fortsätta att komma åt resurser.

5.  Klicka på **Spara**.

## <a name="next-steps"></a>Nästa steg

[Skapa en WIP-appskyddsprincip](windows-information-protection-policy-create.md)
