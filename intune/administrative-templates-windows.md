---
title: Använda mallar för Windows 10-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Använd Administrativa mallar i Microsoft Intune för att skapa grupper med inställningar för Windows 10-enheter. Med dessa inställningar i en enhetskonfigurationsprofil kan du styra Office-program, Microsoft Edge, säkra funktioner i Internet Explorer, styra åtkomst till OneDrive, använda fjärrskrivbordsfunktioner, aktivera automatisk uppspelning, ange energisparinställningar, använda HTTP-utskrifter, använda olika alternativ för användarinloggning samt styra händelseloggens storlek.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c474ac2eccf90e829abe753c82d40bdfae9146ec
ms.sourcegitcommit: 5bb46d3c0bf8c5595132c4200849b1c4bcfe7cdb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70376930"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Använda Windows 10-mallar för att konfigurera grupprincipinställningar i Microsoft Intune

När du hanterar enheter i din organisation är det bra att skapa en grupp med inställningar som tillämpas på olika enhetsgrupper. Anta att du har flera enhetsgrupper. För grupp A vill du tilldela en viss uppsättning inställningar. För grupp B vill du tilldela en annan uppsättning inställningar. Du vill även ha en enkel vy över de inställningar du kan konfigurera.

Du kan slutföra den här uppgiften med **Administrativa mallar** i Microsoft Intune. De administrativa mallarna innehåller hundratals inställningar som styr funktionerna i Microsoft Edge version 77 och senare, Internet Explorer, Microsoft Office-program, fjärrskrivbord, OneDrive, lösenord och PIN-koder med mera. Med de här inställningarna kan gruppadministratörer hantera grupprinciper i molnet.

Windows-inställningarna liknar inställningarna för grupprinciper (GPO) i Active Directory (AD). De här inställningarna är inbyggda i Windows och är [ADMX-baserade inställningar](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) som använder XML. Office- och Microsoft Edge-inställningarna är ADMX-inmatade och använder ADMX-inställningarna i [Offices administrativa mallfiler](https://www.microsoft.com/download/details.aspx?id=49030) samt [Microsoft Edges administrativa mallfiler](https://www.microsoftedgeinsider.com/enterprise). Men Intune-mallarna är 100 % molnbaserade. De ger ett enkelt och rakt sätt att konfigurera inställningarna på, och hittar de inställningar du vill ha.

**Administrativa mallar** är inbyggda i Intune och kräver inga anpassningar, inklusive användning av OMA-URI. Som en del av din MDM-lösning (hantering av mobilenheter) använder du dessa mallinställningar som en heltäckande funktion för hantering av dina Windows 10-enheter.

Den här artikeln listar stegen för att skapa en mall för Windows 10-enheter och visar hur du filtrerar alla tillgängliga inställningar i Intune. När du skapar mallen skapar den en enhetskonfigurationsprofil. Du kan sedan tilldela eller distribuera profilen till Windows 10-enheter i din organisation.

## <a name="before-you-begin"></a>Innan du börjar

- Några av de här inställningarna är tillgängliga från och med Windows 10 version 1703 (RS2). Vi rekommenderar att du använder Windows 10 Enterprise version 1903 (19H1) och senare för bästa möjliga upplevelse.

- I Windows-inställningarna använder du [CSP:er för Windows-princip](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies). CSP:er fungerar i olika utgåvor av Windows, till exempel Home, Professional, Enterprise och så vidare. Om du vill se om en CSP fungerar i en viss version går du till [CSP:er för Windows-princip](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies).

## <a name="create-a-template"></a>Skapa en mall

1. Logga in på [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande egenskaper:

    - **Namn**: Ange ett namn på profilen.
    - **Beskrivning**: Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Plattform**: Välj **Windows 10 och senare**.
    - **Profiltyp**: Välj **Administrativa mallar**.

4. Välj **Skapa**. Välj **Inställningar** i det nya fönstret. Varje inställning är listad och du kan använda föregående- och nästa-pilarna om du vill se fler inställningar:

    ![Se en lista exempellista över inställningar och använd föregående- och nästa-knapparna](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Windows-inställningarna i Intune motsvarar den lokala grupprincipen sökväg som du ser i redigeraren för grupprincipobjekt (`gpedit`).

5. Som standard visas **alla produkter** i listrutan. I listan kan du även filtrera inställningarna så att endast inställningar för **Windows**, **Office** eller **Edge version 77 eller senare** visas:

    ![Filtrera listan för att visa alla Windows- och alla Office-inställningar i administrativa mallar i Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Microsoft Edge-inställningar gäller för:
    >
    > - Microsoft Edge version 77 och senare. Information om hur du konfigurerar Microsoft Edge version 45 och tidigare finns i [inställningarna för Microsoft Edge-webbläsarens enhetsbegränsning](device-restrictions-windows-10.md#microsoft-edge-browser).
    > - Windows 10 RS4 och senare med [KB 4512509](https://support.microsoft.com/kb/4512509) installerat
    > - Windows 10 RS5 och senare med [KB 4512534](https://support.microsoft.com/kb/4512534) installerat
    > - Windows 10 19H1 och senare med [KB 4512941](https://support.microsoft.com/kb/4512941) installerat

6. Välj en inställning. Filtrera exempelvis på **Office** och välj **Aktivera begränsad bläddring**. En detaljerad beskrivning av inställningen visas. Välj **Aktiverad**, **Inaktiverad** eller lämna inställningen som **Inte konfigurerad** (standard). Den detaljerade beskrivningen förklarar även vad som händer när du väljer **Aktiverad**, **Inaktiverad** eller **Inte konfigurerad**.
7. Klicka på **OK** för att spara ändringarna.

Fortsätt gå igenom listan med inställningar och konfigurera de inställningar du vill använda i din miljö. Här följer några exempel:

- Använd inställningen **Meddelandeinställningar för VBA-makro** till att hantera VBA-makron i andra Microsoft Office-program, till exempel Word and Excel.
- Använd inställningen **Tillåt hämtning av filer** för att tillåta eller förhindra nedladdningar från Internet Explorer.
- Använd **Kräv lösenord när en dator aktiveras (ansluts)** för att be användarna om ett lösenord när enheter aktiveras från viloläge.
- Använd inställningen **Hämta osignerade ActiveX-kontroller** för att blockera användare från osignerade ActiveX-kontroller från Internet Explorer.
- Använd inställningen **Inaktivera Systemåterställning** för att tillåta eller förhindra användare att köra en systemåterställning på enheten.
- Använd inställningen **Tillåt import av favoriter** för att tillåta eller blockera användare från att importera favoriter från en annan webbläsare till Microsoft Edge.
- Och mycket annat...

## <a name="find-some-settings"></a>Hitta några inställningar

Det finns hundratals inställningar tillgängliga i dessa mallar. För att göra det enklare att hitta specifika inställningar använder du de inbyggda funktionerna:

- I mallen markerar du kolumnerna **Inställningar**, **Tillstånd**, **Inställningstyp** eller **Sökväg** för att sortera listan. Markera till exempel kolumnen **Sökväg** om du vill se alla inställningar i sökvägen `Microsoft Excel`:

  ![Klicka på sökväg för att visa alla inställningar grupperade efter grupprincip eller ADMX-sökväg i administrativa mallar i Intune](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Använd rutan **Sök** i mallen för att hitta specifika inställningar. Du kan söka genom att ange rubrik eller sökväg. Sök t.ex. efter `copy`. Alla inställningar med `copy` visas:

  ![Sök efter kopia för att visa alla Windows- och Office-inställningar i administrativa mallar i Intune](./media/administrative-templates-windows/search-copy-settings.png) 

  I ett annat exempel söker du efter `microsoft word`. Du ser alla inställningar du kan ange för Microsoft Word-programmet. Sök efter `explorer` om du vill se alla Internet Explorer-inställningar du kan lägga till i mallen.

## <a name="next-steps"></a>Nästa steg

Mallen har skapats, men den gör inte något än. [Tilldela mallen (kallas även profil)](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).
