---
title: "Hämta ett Apple MDM-pushcertifikat"
titleSuffix: Intune Azure preview
description: "Förhandsvisning av Intune Azure: Lär dig hur du hämtar ett Apple MDM-pushcertifikat för att hantera iOS-enheter med Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 82585886bb053d5b6b5981f61d0337fc6feffea4
ms.openlocfilehash: b26d66d557e084b5b328aec2222c50c2db254bf7
ms.lasthandoff: 03/14/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Hämta ett Apple MDM-pushcertifikat

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och Mac-enheter och ger användarna åtkomst till företagets e-post och appar. Ett MDM Push-certifikat krävs för att Intune ska kunna hantera iOS- och Mac-enheter. När du har lagt till certifikatet i Intune kan dina användare installera företagsportalappen och registrera sina enheter. Du kan också konfigurera hantering av företagsägda iOS-enheter med Apples DEP eller registrera enheter med hjälp av t.ex. Apple Configurator. Mer information om registreringsalternativ för finns [Välj hur du vill registrera iOS-enheter](https://docs.microsoft.com/intune-azure/enroll-devices/choose-ios-enrollment-method).

## <a name="steps-to-get-your-certificate"></a>Steg för att få ditt certifikat
På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Apple-registrering** **Apple MDM-pushcertifikat** på Intune-bladet och följ sedan stegen i Azure Portal så som visas nedan.

**Steg 1. Hämta Intune certifikatsigneringsförfrågan som krävs för att skapa ett certifikat för Apple MDM-pushcertifikat.**<br>
Välj **hämta din CSR** för att hämta och spara CSR-filen lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

**Steg 2. Skapa ett Apple MDM-pushcertifikat**<br>
Välj **Skapa ett MDM-pushcertifikat** för att gå till Apple Push Certificates-portalen. Logga in med ditt företags Apple-ID för att skapa pushcertifikatet med hjälp av CSR-filen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil. Använd den här filen för pushcertifikatet. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp Certifikat för servrar från tredje part och klicka på **Hämta**. Hämta pushcertifikatet (.pem) och spara filen lokalt.
Obs!

**Steg 3. Ange det Apple-ID som används för att skapa ett Apple MDM-pushcertifikat.**

**Steg 4. Bläddra till Apple MDM-pushcertifikatet för att överföra.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

