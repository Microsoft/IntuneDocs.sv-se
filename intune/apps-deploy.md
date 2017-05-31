---
title: "Så här tilldelar du grupper appar | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Förhandsversion av Intune Azure: När du har lagt till en app till Intune, behöver du tilldela den till grupper av användare eller enheter."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 1246ef539c044b894b4e4a93f449e60e6462600a
ms.contentlocale: sv-se
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Tilldela appar till grupper med Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

När du har lagt till en app till Intune, behöver du dela den till användare och enheter. Det gör du genom att tilldela den.

Appar kan tilldelas till enheter oavsett om de hanteras av Intune eller inte. Använd följande tabell för att förstå de olika alternativen för att tilldela appar till användare och enheter:

||||
|-|-|-|-|
|&nbsp;|Enheter registrerade med Intune|Enheter ej registrerade med Intune|
|Tilldela till användare|Ja|Ja|
|Tilldela till enheter|Ja|Nej|
|Tilldela omslutna appar eller appar med Intune SDK (för appskyddsprinciper)|Ja|Ja|
|Tilldela appar som är tillgängliga|Ja|Ja|
|Tilldela appar vid behov|Ja|Nej|
|Avinstallera appar|Ja|Nej|
|Slutanvändarna installerar tillgängliga appar från företagsportalappen|Ja|Nej|
|Slutanvändarna installerar tillgängliga appar från den webbaserade företagsportalen|Ja|Ja|

> [!NOTE]
> För närvarande kan du tilldela iOS- och Android-appar (både branschspecifika och butiksköpta appar) till enheter som inte har registrerats med Intune.

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>Ändringar för hur du tilldelar appar i grupper i förhandsversionen av Intune

I förhandsversion av Intune Azure kan du inte längre använda Intune-grupper för att tilldela appar. Du använder nu Active Directory Azure (Azure AD)-säkerhetsgrupper istället. På grund av det här behöver du lära dig om några förändringar i hur tilldelning av appar fungerar, särskilt när du har tilldelat appar till underordnade grupper i Intune.
Det viktigaste är att notera att konceptet underordnade grupper inte finns i Azure AD. Men kan vissa grupper kan innehålla samma medlemmar. I det här fallet är funktionerna i klassiska Intune och förhandsversionen av Intune Azure olika. Det här visas i följande tabell:

||||||
|-|-|-|-|-|
|**Klassiska Intune (före migrering av klient)**|-|**Intune Azure (när migreringen av klienten är klar)**|-|**Mer information**|
|**Tilldelningsavsikt för överordnad grupp**|**Tilldelningsavsikt för underordnad grupp**|**Resulterande tilldelningsavsikt för vanliga medlemmar i föregående överordnade och underordnade grupper**|**Resulterande tilldelningsåtgärd för medlemmar i överordnade grupp**|-|
|Tillgänglig|Obligatoriskt|Nödvändig och Tillgänglig|Tillgänglig|Nödvändig och Tillgänglig innebär att appar som har tilldelats som nödvändig också kan visas i företagsportalappen.
|Ej tillämpligt|Tillgänglig|Ej tillämpligt|Ej tillämpligt|Lösning: Ta bort tilldelningsavsikten ”Inte tillämplig” från den överordnade gruppen i Intune.
|Obligatoriskt|Tillgänglig|Nödvändig och Tillgänglig|Obligatoriskt|-|
|Nödvändig och Tillgänglig<sup>1</sup>|Tillgänglig|Nödvändig och Tillgänglig|Nödvändig och Tillgänglig|-|
|Obligatoriskt|Ej tillämpligt|Obligatoriskt|Obligatoriskt|-|
|Nödvändig och Tillgänglig|Ej tillämpligt|Nödvändig och Tillgänglig|Nödvändig och Tillgänglig|-|
|Obligatoriskt|Avinstallera|Obligatoriskt|Obligatoriskt|-|
|Nödvändig och Tillgänglig|Avinstallera|Nödvändig och Tillgänglig|Nödvändig och Tillgänglig|-|
<sup>1</sup> Endast för hanterade iOS store-appar. När du lägger till dem i Intune och tilldelar dem som Nödvändiga skapas de automatiskt med både avsikterna Nödvändig och Tillgänglig.

Du kan utföra följande åtgärder för att undvika tilldelningskonflikter:

1.    Överväg att ta bort de här tilldelningarna innan du påbörjar migreringen om du tidigare har tilldelat appar till relaterade överordnade och underordnade grupper i Intune.
2.    Ta bort underordnade grupper från överordnade grupper och skapa en ny grupp som innehåller medlemmarna i den gamla underordnade gruppen. Du kan sedan skapa en ny apptilldelning till den här gruppen.
Kommentar: Om den tidigare överordnade gruppen var "Alla användare" måste du skapa en dynamisk grupp som inte innehåller medlemmarna i den underordnade gruppen.
Alla ändringar till grupper för användare och enhetsgrupper måste göras i [Azure Portal](https://portal.azure.com/). Den [klassiska Azure-portalen](https://manage.windowsazure.com/) låter dig endast att göra ändringar till användargrupper.


## <a name="how-to-assign-an-app"></a>Så här tilldelar du en app

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** > **Intune**.
3. Välj **Mobilappar** på **Intune**-bladet.
1. Välj **Hantera** > **Appar** i arbetsbelastningen **Mobilappar**.
2. I listan på appbladet klickar du på den app som du vill tilldela.
3. På bladet <*appnamn*>- **Översikt** väljer du **Hantera** > **Tilldelningar**.
4. Välj **Välj grupper**, klicka sedan på bladet **Välj grupper** och välj de Azure AD-grupper som du vill tilldela appen.
5. För varje app som du väljer ska du också välja en av följande **tilldelningstyper** för appen:
    - **Tillgänglig** – Användarna installerar appen från företagsportalappen eller webbplatsen.
    - **Inte tillämpligt** – Appen varken installeras eller visas i företagsportalen.
    - **Obligatoriskt** – Appen installeras på enheter i valda grupper.
    - **Avinstallera** – Appen avinstalleras från enheter i valda grupper.
    - **Tillgänglig med eller utan registrering** – Tilldela den här appen till grupper av användare vars enheter inte har registrerats med Intune. Se tabellen ovan för hjälp.
6. När du är klar väljer du **Spara**.

Appen har nu tilldelats den grupp som du valde.

Du hittar mer information i [Hur du övervakar appar](apps-monitor.md) som hjälper dig att övervaka apptilldelningar.

