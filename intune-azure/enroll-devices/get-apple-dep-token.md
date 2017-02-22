---
title: "Hämta ett Apple DEP-certifikat för Intune | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: anvisningar för hur du konfigurerar och överför ett MDM-pushcertifikat, vilket är en förutsättning för att kunna hantera Apple-enheter i Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 65a6b2e22359bdcb9b0c15a84c6b3586dafe4d6c
ms.openlocfilehash: c740dedebdc4afd909a8c38447f698c2724de5a1

---

# <a name="get-an-apple-dep-certificate"></a>Hämta ett Apple DEP-certifikat 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Innan du kan registrera företagsägda iOS-enheter med DEP behöver du en DEP-token från Apple. Med denna token kan Intune synkronisera information om enheter som är anslutna till DEP och som ditt företag äger. Intune kan även utföra överföringar av registreringsprofilen till Apple och tilldela enheter till dessa profiler.

Ett företag som vill hantera företagsägda iOS-enheter med Apples enhetsregistreringsprogram (DEP) måste gå med i Apples program och skaffa enheter genom det. Information om den här processen finns på https://deploy.apple.com. Exempel på fördelar med programmet är obevakade enhetsinstallationer utan användning av en USB-kabel för att ansluta varje enhet till en dator.

> [!NOTE]
> Läs det här meddelandet endast om du är en kund som har migrerats från Intune-administrationskonsolen till Azure-portalen. Om du tar bort en Apple DEP-token från Intune-administrationskonsolen under migreringsperioden kan du upptäcka att DEP-token har återställts till ditt Intune-konto. Om detta inträffar, tar du bort DEP-token från Azure-portalen. 

**Hämta ett Apple DEP-certifikat**</br>
Välj **Fler tjänster** i Azure-portalen, skriv **Intune** i textrutan och välj sedan **Övrigt** > **Intune**. Välj **Registrera enheter** > **Apple DEP-token** på Intune-bladet och följ stegen i Azure-portalen enligt nedan.

**Steg 1. Ladda ned certifikatet för den offentliga Intune-nyckel som krävs för att skapa en Apple DEP-token.**<br>
Välj **Hämta den offentliga nyckeln** om du vill hämta och spara krypteringsnyckelfilen (.pem) lokalt. Filen .pem används för att begära ett förtroendecertifikat från portalen Apples DEP.

**Steg 2. Ladda ned en Apple DEP-token från en lämplig Apple-webbplats.**<br>
Välj [Skapa en DEP-token via Apples distributionsprogram](https://deploy.apple.com) (https://deploy.apple.com) och logga in med ditt företags Apple-ID. Du måste använda det här Apple-ID:t för att kunna förnya din DEP-token.

   1.  På [DEP-portalen (Device Enrollment Program Portal)](https://deploy.apple.com) går du till **Enhetsregistreringsprogram (DEP)** &gt; **Hantera servrar** och väljer **Lägg till MDM-server**.

   2.  Ange **MDM-servernamnet** och välj **Nästa**. Servernamnet är för din egen referens och hjälper dig att identifiera MDM-servern (hantering av mobilenheter). Det är inte namnet eller URL-adressen för Microsoft Intune-servern.

   3.  Dialogrutan **Lägg till &lt;ServerName&gt;** öppnas. Välj **Välj fil** för att överföra PEM-filen och välj sedan **Nästa**.

   4.  Dialogrutan **Lägg till &lt;ServerName&gt;** visar länken **Din servertoken**. Hämta servertokenfilen (.p7m) till datorn och klicka sedan på **Klar**.

    Den här certifikatfilen (.p7m) används för att upprätta en förtroenderelation mellan Intune och Apples DEP-servrar.

**Steg 3. Ange det Apple-ID som användes för att skapa din Apple DEP-token. Detta ID kan du använda för att förnya din Apple DEP-token.**

**Steg 4. Bläddra till din Apple DEP-token och ladda upp. Intune synkroniseras automatiskt med ditt DEP-konto.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.



<!--HONumber=Feb17_HO1-->


