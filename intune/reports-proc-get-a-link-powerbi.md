---
title: Ansluta till informationslagret med Power BI
titlesuffix: Microsoft Intune
description: Du kan ladda ned en fil och använda den med Microsoft Power BI för att läsa in interaktiva och dynamiskt skapade rapporter för Microsoft Intune-klientorganisationen.
keywords: Intune-informationslager
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 145b4ba18325d82942eb4ebf5fbfe17ffc8e653b
ms.sourcegitcommit: 279f923b1802445e501324a262d14e8bfdddabde
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/21/2018
ms.locfileid: "53737907"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Ansluta till informationslagret med Power BI

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan ladda ned en fil och använda den med Microsoft Power BI för att läsa in interaktiva, dynamiskt skapade rapporter för Intune-klientorganisationen. Informationslagrets Power BI-fil (pbix) innehåller anslutningsinställningar för klientorganisationen, samt följande exempelrapporter och diagram:  

  -  Egenskaper
  -  Registrering
  -  Appskyddsprincip
  -  Policy för efterlevnad
  -  Enhetens konfigurationsprofiler
  -  Programuppdateringar
  -  Inventeringsloggar för enheten

Här markeras också trenderna för registrering, regelefterlevnad, enhetens konfigurationsprofil och programuppdateringar. För exempeldiagram och rapporter tillämpas användarvänliga filter på arbetsytan. Om du vill använda avancerade filter kan du gå till rutan **Filter** i Power BI Desktop.

I följande anvisningar visas hur du laddar ned Power BI-filen och använder OData-länken med Power BI.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installera Power BI

Installera den senaste versionen av Power BI Desktop. Du kan ladda ned Power BI Desktop från: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Läsa in data och rapporter med Power BI-filen (pbix)

Power BI-filen (pbix) innehåller anslutningsinformation för klientorganisationen och en uppsättning fördefinierade rapporter baserade på informationslagerdatamodellen. Öppna filen i Power BI Desktop och logga in på Azure AD. Rapporten läser in informationen från Intune-klientorganisationen.

> [!Important]  
> Varje Power BI-fil (pbix) kan vara olika beroende på klientens plats. Om du hanterar flera Intune-klienter så måste du använda den fil som hämtats från Azure Portal när du är inloggad i den klienten.  

1.  Logga in på Azure-portalen och välj **Övervakning + hantering** > **Intune**. Du kan också söka efter resurser för  **Intune**.  
2.  Öppna bladet **API för Microsoft Intune-informationslager (förhandsversion)** .
3.  Välj **Ladda ned PowerBI-fil**. Filen med filnamnstillägget pbix laddas ned till den plats du angett.
4.  Öppna filen med Power BI. *Intune Data Warehouse Reports* läses in men det kan ta någon sekund innan klientorganisationens data nås.
5.  Välj **Uppdatera** så att klientorganisationens data läses in, och granska rapporterna.
6.  Om Power BI inte har autentiserat dig med Azure Active Directory-autentiseringsuppgifter uppmanas du i Power BI att ange autentiseringsuppgifter. När du väljer autentiseringsuppgifter väljer du **Organisationskonto** som autentiseringsmetod.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Läsa in data i Power BI med OData-länken

När en klient har autentiserats med Azure AD ansluter OData-webbadressen till RESTful-slutpunkten i informationslager-API:t som gör datamodellen tillgänglig för rapporteringsklienten. Följ de här anvisningarna för att ansluta och skapa egna rapporter med hjälp av Power BI Desktop. Du är inte begränsad till enbart Power BI Desktop utan kan använda ett valfritt analysverktyg med OData-webbadressen så länge klienten har stöd för OAUTH2.0-autentisering och OData v4.0-standarden.

1.  Logga in på Azure-portalen och välj **Övervakning + hantering** > **Intune**. Du kan också söka efter resurser för  **Intune**.  
2.  Öppna bladet **API för Microsoft Intune-informationslager (förhandsversion)** .
3. Hämta webbadressen till anpassad feed på rapportbladet, till exempel `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4. Öppna **Power BI Desktop**.
5. Välj **Hem** > **Hämta data**. Välj**OData-feed**.
6. Välj **Basic**.
7. Skriv eller klistra in **OData-URL** i webbadressrutan.
8. Välj **OK**.
9. Om du inte har autentiserats med Azure AD för klientorganisationen från Power BI-skrivbordsklienten anger du dina autentiseringsuppgifter. För att få åtkomst till dina data måste du auktorisera Azure Active Directory (Azure AD) med hjälp av OAuth 2.0.  
    1.  Välj **Organisationskonto**.  
    2.  Ange användarnamn och lösenord.  
    3.  Välj **Logga in.**  
    4.  Välj **Anslut**.  
10. Välj **Läs in**.

## <a name="next-steps"></a>Nästa steg

Du hittar svar på frågor om miljön, till exempel hur många enheter som har registrerats per dag den senaste veckan. Du får bättre insyn i din Intune-klientorganisation och klientpopulation med hjälp av rapporterna med Intune-informationslager Power BI-filen (pbix) som du hämtat från bladet i Azure. Intune tillhandahåller dock ett antal ytterligare sätt att utöka eller återanvända dessa data. Du kan göra mycket mer med Power BI och API för Intune-informationslagret, till exempel:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  Klientorganisationsdata sammanställs så att de lätt kan tolkas. Mer information om hur data sammanställs finns i [Datamodellen informationslager](reports-ref-data-model.md).
 -  Du kan också komma åt informationen från ett RESTful-gränssnitt och kan lägga till informationen i din egen app. Mer information finns i [Hämta data från API för informationslager med en REST-klient](reports-proc-data-rest.md).
