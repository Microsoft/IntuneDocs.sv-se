---
title: "Hämta ett Apple DEP-certifikat för Intune"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: anvisningar för hur du konfigurerar och överför ett MDM-pushcertifikat, vilket är en förutsättning för att kunna hantera Apple-enheter i Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>Hämta ett Apple DEP-certifikat

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Innan du kan registrera företagsägda iOS-enheter med Apples program för enhetsregistrering (DEP) behöver du en DEP-token från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till DEP och som ditt företag äger. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

Ett företag som vill hantera företagsägda iOS-enheter med DEP måste gå med i Apples program och skaffa enheter genom det. Information om den här processen finns på https://deploy.apple.com. Exempel på fördelar med programmet är obevakade enhetsinstallationer utan användning av en USB-kabel för att ansluta varje enhet till en dator.

> [!NOTE]
> Det här meddelandet gäller endast för Intune-kunder som har migrerats från Intune-administrationskonsolen till Azure Portal. Om du tar bort en Apple DEP-token från Intune-administrationskonsolen under migreringsperioden kan du upptäcka att DEP-token har återställts till ditt Intune-konto. Om detta inträffar, tar du bort DEP-token från Azure-portalen.

## <a name="steps-to-get-the-apple-dep-certificate"></a>Steg för att hämta ett Apple DEP-certifikat
På Azure-portalen väljer du **Fler tjänster** > **Övervakning + hantering** > **Intune**. Välj **Registrera enheter** > **Apple DEP-token** på Intune-bladet och följ stegen i Azure-portalen enligt nedan.

**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple DEP-token.**<br>
Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

**Steg 2. Ladda ned en Apple DEP-token från en lämplig Apple-webbplats.**<br>
Välj [Skapa en DEP-token via Apples distributionsprogram](https://deploy.apple.com) (https://deploy.apple.com) och logga in med ditt företags Apple-ID. Du måste använda det här Apple-ID:t för att kunna förnya din DEP-token.

   a.  På [DEP-portalen (Device Enrollment Program Portal)](https://deploy.apple.com) går du till **Enhetsregistreringsprogram (DEP)** &gt; **Hantera servrar** och väljer **Lägg till MDM-server**.

   b.  Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

   c.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.

   d.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**Steg 3. Ange det Apple-ID som användes för att skapa din Apple DEP-token. Detta ID kan du använda för att förnya din Apple DEP-token.**

**Steg 4. Bläddra till din Apple DEP-token och ladda upp. Intune synkroniseras automatiskt med ditt DEP-konto.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

