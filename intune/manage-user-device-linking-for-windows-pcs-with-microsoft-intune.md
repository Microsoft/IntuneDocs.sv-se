---
title: Hantera användarenhetslänkar för Windows-datorer
titleSuffix: Microsoft Intune
description: Länka en användare till en Intune-hanterad Windows-dator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4dad2d22b742b62ca35bd7fb98c7f7e8241cbb4
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402907"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Hantera användarenhetslänkar för Windows-datorer

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Informationen i det här avsnittet gäller endast för stationära Windows-datorer som du hanterar som datorer med Intune-klientprogramvaran. 

Innan du kan distribuera programvara till en användare måste du koppla användaren till en dator. Du kan koppla en användare till flera datorer, men varje dator kan bara kopplas till en enda användare. Användarna länkas automatiskt till alla datorer som de registrerar i Intune med hjälp av företagsportalen.

Mer information om primär användare för en enhet finns i [hitta primär användare](find-primary-user.md).

Länka en användare till en dator:

1. I [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com/) väljer du **Grupper** &gt; **Alla enheter** (eller någon annan grupp som innehåller den dator som du vill länka till en användare).

2. Välj den dator som du vill koppla en användare till och välj sedan **Länka användare**.

   Dialogrutan **Länka användare** visar en lista över tillgängliga användare med deras visningsnamn, användar-ID och hur många datorer som varje användare för närvarande är länkad till. Om en användare redan är länkad till den valda datorn visas användarens namn och användar-ID under **Aktuell användare**. Om datorn inte är länkad till någon användare visas **Ingen användare** under **Aktuella användare**.

3. Gör något av följande:

   - Om du vill låta datorn fortsätta att vara kopplad till den aktuella användaren, om det finns en sådan, väljer du **Avbryt**.

   - Om du vill ta bort länken till den aktuella användaren, om det finns en sådan, väljer du <strong>Ta bort länk **&gt;** OK</strong>.

   - För att länka datorn till en ny användare väljer du en användare i listan **Alla användare** . Bekräfta att användardatan är korrekt och välj sedan **OK**.

> [!TIP]
> Om du vill begränsa slutanvändarnas möjlighet att länka sig själva till datorer aktiverar du alternativet **Begränsa användarnas möjlighet att länka sig själva till datorer** i principen **Agentinställningar för Microsoft Intune**.

### <a name="see-also"></a>Se även

[Vanliga hanteringsuppgifter för Windows-datorer med Intune-klientprogrammet](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
