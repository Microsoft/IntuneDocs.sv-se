---
title: "Skydda verksamhetsspecifika appar på enheter som inte har registrerats | Microsoft Intune"
description: "I det här avsnittet beskrivs hur du kan förbereda dina verksamhetsspecifika appar så att du kan skydda dig mot dataförlust med hjälp av principer för hantering av mobila appar."
keywords: 
author: karthikaraman
manager: arob98
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2038ed6219a94dc4285891d71ce00fd51310f3e3
ms.openlocfilehash: 39908e4b08a7a7b0f058646a776a7c37de14b770


---

# Skydda branschspecifika appar och data på enheter som inte har registrerats i Microsoft Intune

Principer för hantering av mobila appar (MAM, Mobile App Management) bidrar till att skydda företagets data genom att begränsa dataflyttning som att kopiera och klistra in eller genom att hindra användarna från att spara företagsdokument på en egen plats.   Om du vill tillämpa MAM-principer för branschspecifika iOS- och Android-appar måste du först omsluta appen med appomslutningsverktyget för Microsoft Intune.  Appomslutning är en process för tillämpning av ett hanteringslager på en mobil app utan att det krävs några ändringar av det underliggande programmet.  När appen har omslutits kan du tillämpa MAM-principer på den och distribuera den till slutanvändarna.  

I det här avsnittet beskrivs de steg som krävs för att tillämpa MAM-principer för appar som kan nås på **medarbetarenheter som inte hanteras** och enheter som hanteras av en **lösning för hantering av mobila enheter från tredje part**.  Information om hur du förbereder branschspecifika appar som körs på **enheter som är registrerade i Intune** finns i [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).
##  Steg 1: Förbered appen
Innan du kan tillämpa MAM-principer på en app måste du först omsluta appen med verktyget för Microsoft Intune-appomslutning.  Anvisningarna för att installera och använda appomslutningsverktyget ingår i hämtningen.  
>[!IMPORTANT]  
>Den här version av appomslutningsverktyget har stöd för enheter som inte har registrerats i Intune och blir tillgängligt i den privata förhandsgranskningen under de kommande veckorna. Om du vill delta skickar du ett e-postmeddelande till msintuneappsdk@microsoft.com för mer information.

## Steg 2: Lägg till appen

Om du vill associera branschspecifika appar med MAM-principer måste du lägga till appinformationen i din Intune-prenumeration/-klient med hjälp av följande steg:

1. Öppna [Azure Portal](https://portal.azure.com/) och gå till **Intunes hantering av mobila program > Inställningar** och välj **Branschspecifika appar**.

  ![Skärmbild av inställningsbladet med branschspecifikt alternativ](../media/mam-azure-portal-lob-on-settings.png)

2. På bladet **Branschspecifika appar** väljer du **Lägg till en anpassad app**.

  ![Skärmbild av bladet med branschspecifika appar med knappen Lägg till anpassad app överst](../media/mam-azure-portal-add-lob-app-action.png)
3.  Ange ett namn för appen, paket-ID:t i fältet App-ID och plattformen (iOS eller Android).

  ![Skärmbild av bladet Lägg till en anpassad app ](../media/mam-azure-portal-add-app-details.png) Det här steget hjälper dig att skapa en unik lista med din app.  Appen visas även i listan över målappar för en MAM-princip för klienten, enligt beskrivningen i nästa steg.

## Steg 3: Tillämpa MAM-principer
När appmetadata har överförts till tjänsten visas appen i listan över appar.  Du kan nu [skapa en ny princip eller en befintlig princip](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) och tillämpa den på den branschspecifika app som du lade till i steg 2.

>[!IMPORTANT]
>Du måste använda MAM-principen för de användare som ska använda den omslutna appen.  Användare som inte har den här principen distribuerad till sig kommer inte att kunna använda appen.


  ![Skärmbild av bladet Riktad lista över appar där den nya branschspecifika appen visas](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## Steg 4: Distribuera appen
Du kan distribuera appar till slutanvändarna på följande sätt:
* Du kan distribuera appar för enheter som har registreras i en MDM-lösning från tredje part via din MDM-lösning.
* För enheter som inte hanteras av någon MDM-lösning behöver du en anpassad lösning. Slutanvändare måste hämta och installera appen på sin enhet.

## Ändra metadata
Om du behöver ändra informationen om en app, t.ex. namnet på appen eller paket-ID, måste du [ta bort appen](#remove-apps), och [lägga till ](#step-2-add-the-app) den med nya metadata.

##  Ta bort appar
Du kan ta bort en branschspecifik app från applistan.  Den här åtgärden tar bort appen från listan och ta bort kopplingen till MAM-principerna, men inte tar bort eller avinstallerar appen från slutanvändarens enhet.  

1.  I [Azure Portal](https://portal.azure.com/) går du till **Intune-mobilapphantering > Inställningar**.  Välj **Branschspecifik** på bladet **Inställningar** så öppnas listan över befintliga appar.  
2.  Välj den app som du vill ta bort och välj menyn **(...) kontext**.

  ![Skärmbild av det branschspecifika appbladet med ellipsen](../media/mam-azure-portal-lob-context-menu.png)
3.  Ta bort appen genom att välja **Ta bort program**.

  ![Skärmbild av det branschspecifika bladet med alternativet för att ta bort program](../media/mam-azure-portal-delete-app.png)

  Detta tar bort apparna från listan över branschspecifika appar och Riktad lista över appar i MAM-principen.



<!--HONumber=Jul16_HO4-->


