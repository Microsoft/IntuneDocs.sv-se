---
title: Använda mallar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd Administrativa mallar i Microsoft Intune för att skapa grupper med inställningar för Windows 10-enheter. Med dessa inställningar i en enhetskonfigurationsprofil kan du styra Office-program, säkra funktioner i Internet Explorer, styra åtkomst till OneDrive, använda fjärrskrivbordsfunktioner, aktivera automatisk uppspelning, ange energisparinställningar, använda HTTP-utskrifter, använda olika alternativ för användarinloggning och styra händelseloggens storlek.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0426b63cb4601a73451ec9509ddea8e39271c29
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204979"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Windows 10-mallar för att konfigurera grupprincipinställningar i Microsoft Intune

När du hanterar enheter i organisationen är det bra att skapa en grupp med inställningar som tillämpas på olika enhetsgrupper. Anta att du har flera enhetsgrupper. För grupp A vill du tilldela en viss uppsättning inställningar. För grupp B vill du tilldela en annan uppsättning inställningar. Du vill även ha en enkel vy över de inställningar du kan konfigurera.

Du kan slutföra den här uppgiften med **Administrativa mallar** i Microsoft Intune. De administrativa mallarna innehåller hundratals inställningar som styr funktionerna i Internet Explorer, Microsoft Office-program, fjärrskrivbord, åtkomst till OneDrive, använda ett bildlösenord eller en PIN-kod för att logga in med mera. Mallarna liknar grupprincipinställningar i Active Directory (AD) och är [ADMX-baserade inställningar](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) som använder XML. Men mallarna i Intune är 100 % molnbaserade. De ger ett enklare och rakare sätt att konfigurera inställningarna på, och hittar de inställningar du vill ha.

**Administrativa mallar** är inbyggda i Intune och kräver inga anpassningar, inklusive användning av OMA-URI. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa mallinställningar som en heltäckande funktion för hantering av dina Windows 10-enheter.

Den här artikeln listar stegen för att skapa en mall för Windows 10-enheter och visar hur du filtrerar alla tillgängliga inställningar i Microsoft Intune. När du skapar mallen skapar den en enhetskonfigurationsprofil. Du kan sedan tilldela eller distribuera profilen till Windows 10-enheter i din organisation.

> [!NOTE]
> Administrativa mallar stöds för fristående enheter. De stöds för närvarande inte för enheter som samhanteras med System Center Configuration Manager (SCCM).

## <a name="create-a-template"></a>Skapar en mall

1. I [Azure-portalen](https://portal.azure.com) väljer du **Alla tjänster** > filtrerar på **Intune** > och väljer **Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett namn på profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Administrativa mallar (förhandsversion)**.

4. Välj **Skapa**. Välj **Inställningar** i det nya fönstret. Varje inställning är listad och du kan använda föregående- och nästa-pilarna om du vill se fler inställningar:

    ![Se en lista exempellista över inställningar och använd föregående- och nästa-knapparna](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Välj en inställning. Du kan till exempel välja **Tillåt hämtning av filer**. En detaljerad beskrivning av inställningen visas. Välj **Aktivera**, **Inaktivera** eller lämna inställningen som **Inte konfigurerad** (standard). Den detaljerade beskrivningen förklarar även vad som händer när du väljer **Aktivera**, **Inaktivera** eller **Inte konfigurerad**.
6. Klicka på **OK** för att spara ändringarna.

Fortsätt gå igenom listan med inställningar och konfigurera de inställningar du vill använda i din miljö. Här följer några exempel:

- Använd inställningen **Meddelandeinställningar för VBA-makro** till att hantera VBA-makron i andra Microsoft Office-program, till exempel Word and Excel.
- Använd inställningen **Tillåt hämtning av filer** för att tillåta eller förhindra nedladdningar från Internet Explorer.
- Använd inställningen **Kräv lösenord när en dator aktiveras (ansluts)** för att be användarna om ett lösenord när enheterna aktiveras från viloläge.
- Använd inställningen **Hämta osignerade ActiveX-kontroller** för att blockera användare från osignerade ActiveX-kontroller från Internet Explorer.
- Använd inställningen **Inaktivera Systemåterställning** för att tillåta eller förhindra användare att köra en systemåterställning på enheten.
- Och mycket annat...

## <a name="find-some-settings"></a>Hitta några inställningar

Det finns hundratals inställningar tillgängliga i dessa mallar. För att göra det enklare att hitta specifika inställningar använder du de inbyggda funktionerna:

- I mallen markerar du kolumnerna **Inställningar**, **Tillstånd** eller **Sökväg** för att sortera listan. Markera till exempel kolumnen **Sökväg** om du vill se alla inställningar i sökvägen `Microsoft Excel`:

  ![Klicka på Sökväg för att sortera alfabetiskt](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Använd rutan **Sök** i mallen för att hitta specifika inställningar. Sök t.ex. efter `copy`. Alla inställningar med `copy` visas:

  ![Klicka på Sökväg för att sortera alfabetiskt](./media/administrative-templates-windows/search-copy-settings.png)

  I ett annat exempel söker du efter `microsoft word`. Du ser alla inställningar du kan ange för Microsoft Word-programmet. Sök efter `explorer` om du vill se alla Internet Explorer-inställningar du kan lägga till i mallen.

## <a name="next-steps"></a>Nästa steg

Mallen har skapats, men den gör inte något än. [Tilldela mallen (kallas även profil)](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
