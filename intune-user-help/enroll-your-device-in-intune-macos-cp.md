---
title: "Registrera din macOS-enhet i Intune med företagsportalen| Microsoft Docs"
description: "Beskriver hur du registrerar en macOS-enhet i Intune med företagsportalappen"
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope: User help
ROBOTS: 
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 1b177b05f065f66deb8c60be768c123fc7991937
ms.sourcegitcommit: 091f7b34f1fbf73db2bed5b46d92a78ba0dad1e4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2017
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>Registrera din macOS-enhet i Intune på företagsportalappen

[!INCLUDE[macos-preview-1708](./includes/macos-preview-1708.md)]

Med åtkomst till din organisations appar, data och resurser är det enklare för dig att göra ditt jobb. Din organisation använder Intune för att [hantera åtkomst till resurserna](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md), vilket kräver att du kan ladda ned företagsportalappen för macOS. De här instruktionerna fungerar för macOS-enheter på OS X El Capitan 10.11+.

  > [!NOTE]
  > [Prova de här instruktionerna i stället](enroll-your-device-in-intune-ios.md) om du vill registrera en iOS-enhet, till exempel en iPhone eller iPad.

1. På din __Docka__ går du till __Safari__ och öppnar sidan [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=55770) för företagsportalappen på macOS.

2. Ladda ned appen. Mac-enheten kontrollerar att den nedladdade filen **CompanyPortal.dmg** är säker att öppna. När du öppnar den från mappen **Hämtade filer** drar du appen **CompanyPortal** från mappen **Program**.

3. Öppna mappen **Program** eller **Startfönstret** och sedan **Företagsportalen**.

4. Mac-enheten visar ett felmeddelande om att **”CompanyPortal” är ett program som laddats ned från Internet. Vill du öppna det ändå?** Klicka på **Öppna**.

  > [!NOTE]
  > Intune behöver åtkomst till datorn för att se till att enheten är säker nog för att få åtkomst till organisationens resurser. Om datorn vägrar att öppna företagsportalappen kan du försöka att [inaktivera Gatekeeper](https://support.apple.com/HT202491) och sedan öppna appen.

6. På den första skärmen som visas i företagsportalappen uppmanas du att **Logga in** med samma arbets- eller skolkonto som du använde för att logga in på företagsportalens webbplats.

7. Företagsportalen bekräftar kontoinformationen och visar sedan statusen för **Enhetsregistrering** och **Enhetsefterlevnad**. En gul triangel indikerar att det finns åtgärder som du behöver utföra för att kontrollera att Mac-enheten är säker för användning i arbetet. Tryck på **Börja** för att starta [registreringen av din enhet till hantering](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).

8. Mac-enheten börjar registreras för hantering. Du kan uppmanas att ange din dators inloggningsinformation under den här tiden. Det kan ta några minuter att registrera. Du kan göra andra saker på datorn under tiden. När du har slutfört konfigurationen av företagsåtkomst så visas ett meddelande som talar om att du är färdig.

Behöver du fortfarande hjälp? Kontrollera med din IT-administratör. Du hittar kontaktinformationen på [Företagsportalens webbplats](http://portal.manage.microsoft.com).
