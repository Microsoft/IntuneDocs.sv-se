---
title: "Åtgärder för inkompatibilitet för Intune"
titleSuffix: Intune on Azure
description: "Lär dig hur du skapar åtgärder för ej kompatibla enheter med Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 01/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e45f5d3836fc33851c650703f713c03204df792
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="automate-actions-for-noncompliance"></a>Automatisera åtgärder för inkompatibilitet

Med **åtgärder för inkompatibilitet** kan du konfigurera en tidsordnad sekvens med åtgärder som tillämpas på enheter som inte uppfyller villkoren för efterlevnadsprinciperna. Som standard när en enhet identifieras som inte uppfyller villkoren för efterlevnadsprinciper markeras Intune omedelbart som icke-kompatibelt och den villkorliga Azure AD-åtkomsten blockerar enheten. Med **åtgärder för inkompatibilitet** har du större flexibilitet när du ska bestämma dig för vad du vill göra när en enhet är inkompatibel. Du kan t.ex. bestämma dig för att inte blockera enheten omedelbart, för att sedan ge användaren en respitperiod att åtgärda problemet.

Det finns två typer av åtgärder:

-   **Meddela slutanvändare via e-post**: Du kan anpassa dina e-postmeddelanden innan du skickar dem till slutanvändaren. Intune tillhandahåller anpassning av mottagare, ämne, brödtext, företagslogotyp och ytterligare kontaktinformation.
-   **Markera enhet som icke-kompatibel**: Du kan fastställa ett schema som anger efter hur många dagar enheten markeras som icke-kompatibel. Du kan konfigurera åtgärden till att börja gälla omedelbart eller ge användare en respitperiod som är kompatibel med efterlevnadsprinciperna för enheten.

## <a name="before-you-begin"></a>Innan du börjar

- Du måste ha skapat minst en princip för enhetsefterlevnad för att kunna vidta åtgärder mot inkompatibilitet. Ta reda på hur du skapar en princip för enhetsefterlevnad för följande plattformar:

    -   [Android](compliance-policy-create-android.md)
    -   [Android for Work](compliance-policy-create-android-for-work.md)
    -   [iOS](compliance-policy-create-ios.md)
    -   [macOS](compliance-policy-create-mac-os.md)
    -   [Windows](compliance-policy-create-windows.md)

- Du måste ha konfigurerat villkorlig Azure AD-åtkomst om du planerar att använda principer för enhetsefterlevnad för att blockera enheter från att använda företagets resurser. Läs om [hur du konfigurerar villkorlig EMS-åtkomst](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access).

- Du måste ha skapat en mall för aviseringsmeddelanden. Mallen för aviseringsmeddelanden används senare under processen när du skapar åtgärder mot inkompatibilitet som ska skickas med e-post till dina användare.

- Du måste konfigurera Exchange Online om du vill acceptera e-post från *IntuneNotificationService@microsoft.com* för att tillåta Intune att skicka e-postmeddelanden. Mer information finns i [Konfigurera begränsningar för meddelandeleverans för en postlåda](https://technet.microsoft.com/library/bb397214(v=exchg.160).aspx).

### <a name="to-create-a-notification-message-template"></a>Skapa en mall för aviseringsmeddelanden

1. Gå till [Intune på Azure Portal](https://portal.azure.com) och logga in med dina Intune-autentiseringsuppgifter.
2. Välj **Fler tjänster** på den vänstra menyn och skriv sedan **Intune** i textrutefiltret.
3. Välj **Intune**
4. Välj **Enhetsefterlevnad** och sedan **Meddelanden** i avsnittet **Hantera**.
5. Välj **Skapa meddelande** och ange följande information:
    - Namn
    - Ärende
    - Meddelande
    - E-postrubrik – Infoga företagslogotyp
    - E-postrubrik – Infoga företagsnamn
    - E-postsidfot – Inkludera kontaktinformation

   ![exempelmall för aviseringsmeddelanden](./media/actionsfornoncompliance-1.PNG)

När du har lagt till informationen väljer du **Skapa**. Mallen för aviseringsmeddelanden är tillgänglig att användas.

> [!NOTE] 
> Du kan också redigera en meddelandemall som du skapat tidigare.

## <a name="to-create-actions-for-non-compliance"></a>Skapa åtgärder avseende inkompatibilitet

> [!TIP]
> Som standard erbjuder Intune en fördefinierad åtgärd bland åtgärderna för avsnittet för inkompatibilitet. Åtgärden markerar att enheten inte följer standard när det har upptäckts att den inte uppfyller dina villkor för enhetens efterlevnadsprincip. Du kan anpassa hur lång tid enheten ska markeras som icke-kompatibel efter identifieringen. Det går inte att ta bort åtgärden.

Du kan lägga till en åtgärd när du skapar en ny efterlevnadsprincip för enheten eller när du redigerar en befintlig efterlevnadsprincip för enheten.

1.  I Intune-arbetsbelastningen går du till **Principer för enhetsefterlevnad** och väljer **Principer** i avsnittet **Hantera**.
2.  Välj en policy för efterlevnad genom att klicka på den och välj sedan **Egenskaper** under avsnittet **Hantera**.
3.  På bladet **egenskaper för efterlevnadsprincip för enheten** väljer du **Åtgärder för inkompatibilitet**.
4.  På bladet **Åtgärder för inkompatibilitet** väljer du åtgärdsparametrar genom att välja **Lägg till**. Du kan välja meddelandemallen som skapades tidigare, ytterligare mottagare och schema för respitperiod. På schemat kan du ange antalet dagar (0 till 365), och sedan kan du tillämpa principen för villkorlig åtkomst. Om du anger **0** dagar,blockerar villkorlig åtkomst **genast** åtkomsten till företagets resurser när enheterna inte uppfyller principerna för enhetsefterlevnad.
5.  När du har lagt till informationen väljer du **Lägg till** och sedan **OK**.

## <a name="next-steps"></a>Nästa steg
Du kan övervaka aktiviteten enhetsefterlevnad genom att köra de tillgängliga rapporterna på bladet med enhetsefterlevnad. Du hittar mer information i [hur du övervakar principer för enhetsefterlevnad med Intune](device-compliance-monitor.md).

