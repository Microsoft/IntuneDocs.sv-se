---
title: "Hantera användarenhetslänkar för Windows-datorer"
description: "Länka en användare till en Intune-hanterad Windows-dator."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 9641c40229be52066a97389584e55f2f95bc286d
ms.contentlocale: sv-se
ms.lasthandoff: 06/08/2017


---

# <a name="manage-user-device-linking-for-windows-pcs"></a>Hantera användarenhetslänkar för Windows-datorer

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Informationen i det här avsnittet gäller endast för stationära Windows-datorer som du hanterar som datorer med Intune-klientprogramvaran. 

Innan du kan distribuera programvara till en användare måste du koppla användaren till en dator. Du kan koppla en användare till flera datorer, men varje dator kan bara kopplas till en enda användare. Användarna länkas automatiskt till alla datorer som de registrerar i Intune med hjälp av företagsportalen.

Länka en användare till en dator:

1.  I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator som du vill länka till en användare).

2.  Välj den dator som du vill koppla en användare till och välj sedan **Länka användare**.

    Dialogrutan **Länka användare** visar en lista över tillgängliga användare med deras visningsnamn, användar-ID och hur många datorer som varje användare för närvarande är länkad till. Om en användare redan är länkad till den valda datorn visas användarens namn och användar-ID under **Aktuell användare**. Om datorn inte är länkad till någon användare visas **Ingen användare** under **Aktuella användare**.

3.  Gör något av följande:

    -   Om du vill låta datorn fortsätta att vara kopplad till den aktuella användaren, om det finns en sådan, väljer du **Avbryt**.

    -   Om du vill ta bort länken till den aktuella användaren, om det finns en sådan, väljer du **Ta bort länk**&gt; **OK**.

    -   För att länka datorn till en ny användare väljer du en användare i listan **Alla användare** . Bekräfta att användardatan är korrekt och välj sedan **OK**.

> [!TIP]
> Om du vill begränsa slutanvändarnas möjlighet att länka sig själva till datorer aktiverar du alternativet **Begränsa användarnas möjlighet att länka sig själva till datorer** i principen **Agentinställningar för Microsoft Intune**.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
