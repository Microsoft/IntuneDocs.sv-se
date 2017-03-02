---
title: "Hämta ett Apple MDM-pushcertifikat | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsvisning av Intune Azure: Lär dig hur du hämtar ett Apple MDM-pushcertifikat för att hantera iOS-enheter med Intune."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: a6ac1074055892f5ec42fb4057e47e9349fb5a33
ms.lasthandoff: 02/15/2017


---

# <a name="get-an-apple-mdm-push-certificate"></a>Hämta ett Apple MDM-pushcertifikat 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intunes stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och Mac OS X-enheter och ger användarna åtkomst till företagets e-post och appar. Ett APNs-certifikat (Apple Push Notification Service) från Apple krävs för att kunna hantera iOS- och Mac-enheter med Intune. När du har lagt till certifikatet i Intune kan dina användare installera företagsportalappen och registrera sina enheter, eller så kan du konfigurera hantering av företagsägda iOS-enheter.

**Att hämta MDM-pushcertifikat:**<br>
På Azure Portal väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Apple MDM-pushcertifikat** på Intune-bladet och följ sedan stegen i Azure-portalen enligt nedan.

**Steg 1. Hämta Intune certifikatsigneringsförfrågan som krävs för att skapa ett certifikat för Apple MDM-pushcertifikat.**<br>
Välj **hämta din CSR** för att hämta och spara CSR-filen lokalt. CSR-filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

**Steg 2. Skapa ett Apple MDM-pushcertifikat**<br>
Välj **Skapa ett MDM-pushcertifikat** för att gå till Apple Push Certificates-portalen. Logga in med ditt företags Apple-ID för att skapa pushcertifikatet med hjälp av CSR-filen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil. Använd den här filen för pushcertifikatet. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp Certifikat för servrar från tredje part och klicka på **Hämta**. Hämta pushcertifikatet (.pem) och spara filen lokalt.
Obs!

**Steg 3. Ange det Apple-ID som används för att skapa ett Apple MDM-pushcertifikat.**

**Steg 4. Bläddra till Apple MDM-pushcertifikatet för att överföra.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

