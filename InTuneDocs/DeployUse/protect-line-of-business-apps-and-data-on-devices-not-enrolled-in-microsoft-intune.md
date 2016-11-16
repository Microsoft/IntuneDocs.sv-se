---
title: "Skydda verksamhetsspecifika appar på enheter som inte har registrerats | Microsoft Intune"
description: "I det här avsnittet beskrivs hur du kan förbereda dina verksamhetsspecifika appar så att du kan skydda dig mot dataförlust med hjälp av principer för hantering av mobila appar."
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: bc5d1b429157e6a6b24f4eb319be50b635466317


---

# <a name="protect-line-of-business-apps-and-data-on-devices-not-enrolled-in-microsoft-intune"></a>Skydda branschspecifika appar och data på enheter som inte har registrerats i Microsoft Intune

Principer för hantering av mobila appar (MAM) skyddar företagsdata genom att begränsa åtgärder som kan läcka företagsdata och tillämpa krav för åtkomst till data, som till exempel PIN-koder för appar. Om du vill tillämpa MAM-principer för branschspecifika iOS- och Android-appar måste du först omsluta appen med programhanteringsverktyget för Microsoft Intune.  Appomslutning är en process för tillämpning av ett hanteringslager på en mobil app utan att det krävs några ändringar av det underliggande programmet.  När appen har omslutits kan du tillämpa MAM-principer på den och distribuera den till slutanvändarna.  

I det här avsnittet beskrivs de steg som krävs för att tillämpa MAM-principer för appar som kan nås på **medarbetarenheter som inte hanteras** och enheter som hanteras av en **lösning för hantering av mobila enheter från tredje part**.  Information om hur du förbereder branschspecifika appar som körs på **enheter som är registrerade i Intune MDM** finns i [Förbereda appar för hantering av mobilprogram med Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).


##  <a name="step-1-prepare-the-app"></a>Steg 1: Förbered appen
Innan du kan tillämpa MAM-principer på en app måste du först omsluta appen med verktyget för Microsoft Intune-appomslutning.  Se följande sidor för anvisningar hur du laddar ned och använder programhanteringsverktyget:

- [Förbereda iOS-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)
- [Förbereda Android-appar för hantering av mobilprogram med Intunes programhanteringsverktyg](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)

>[!IMPORTANT]  
>Den här versionen av programhanteringsverktyget, som har stöd för enheter som inte har registrerats i Intune, har stöd för iOS och är tillgängligt som förhandsversion för Android. Du kan hämta verktyget från [den här GitHub-lagringsplatsen](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) för iOS och [den här GitHub-lagringsplatsen](https://github.com/msintuneappsdk/intune-app-wrapper-android-preview) för Android.

## <a name="step-2-add-the-app"></a>Steg 2: Lägg till appen

Om du vill associera branschspecifika appar med MAM-principer måste du lägga till appinformationen i din Intune-prenumeration/-klient med hjälp av följande steg:

1. Öppna [Azure Portal](https://portal.azure.com/) och gå till **Intunes hantering av mobila program > Inställningar** och välj **Branschspecifika appar**.

  ![Skärmbild av inställningsbladet med branschspecifikt alternativ](../media/mam-azure-portal-lob-on-settings.png)

2. På bladet **Branschspecifika appar** väljer du **Lägg till en anpassad app**.

  ![Skärmbild av bladet med branschspecifika appar med knappen Lägg till anpassad app överst](../media/mam-azure-portal-add-lob-app-action.png)
3.  Ange ett namn för appen, paket-ID:t i fältet App-ID och plattformen (iOS eller Android).

  ![Skärmbild av bladet Lägg till en anpassad app ](../media/mam-azure-portal-add-app-details.png) Det här steget hjälper dig att skapa en unik lista med din app.  Appen visas även i listan över målappar för en MAM-princip för klienten, enligt beskrivningen i nästa steg.

## <a name="step-3-apply-mam-policies"></a>Steg 3: Tillämpa MAM-principer
När appmetadata har överförts till tjänsten visas appen i listan över appar.  Du kan nu [skapa en ny princip eller en befintlig princip](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) och tillämpa den på den branschspecifika app som du lade till i steg 2.

>[!IMPORTANT]
>Du måste använda MAM-principen för de användare som ska använda den omslutna appen.  Användare som inte har den här principen distribuerad till sig kommer inte att kunna använda appen.


  ![Skärmbild av bladet Riktad lista över appar där den nya branschspecifika appen visas](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>Steg 4: Distribuera appen
Du kan distribuera appar till slutanvändarna på följande sätt:
* Du kan distribuera appar för enheter som har registreras i en MDM-lösning från tredje part via din MDM-lösning.
* För enheter som inte hanteras av någon MDM-lösning behöver du en anpassad lösning. Slutanvändare måste hämta och installera appen på sin enhet.

## <a name="changing-the-metadata"></a>Ändra metadata
Om du behöver ändra informationen om en app, t.ex. namnet på appen eller paket-ID, måste du [ta bort appen](#remove-apps), och [lägga till ](#step-2-add-the-app) den med nya metadata.

##  <a name="remove-apps"></a>Ta bort appar
Du kan ta bort en branschspecifik app från applistan.  Den här åtgärden tar bort appen från listan och ta bort kopplingen till MAM-principerna, men inte tar bort eller avinstallerar appen från slutanvändarens enhet.  

1.  I [Azure Portal](https://portal.azure.com/) går du till **Intune-mobilapphantering > Inställningar**.  Välj **Branschspecifik** på bladet **Inställningar** så öppnas listan över befintliga appar.  
2.  Välj den app som du vill ta bort och välj menyn **(...) kontext**.

  ![Skärmbild av det branschspecifika appbladet med ellipsen](../media/mam-azure-portal-lob-context-menu.png)
3.  Ta bort appen genom att välja **Ta bort program**.

  ![Skärmbild av det branschspecifika bladet med alternativet för att ta bort program](../media/mam-azure-portal-delete-app.png)

  Detta tar bort apparna från listan över branschspecifika appar och Riktad lista över appar i MAM-principen.



<!--HONumber=Nov16_HO2-->


