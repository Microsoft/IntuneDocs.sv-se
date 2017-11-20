---
title: "Add app configuration policies for managed apps without device enrollment (Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering) | Microsoft Docs"
titlesuffix: Azure portal
description: "Lär dig hur du använder appkonfigurationsprinciper för hanterade appar utan enhetsregistrering."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c46d7e8f4291345a9da87f7a7a6f3180415b69a4
ms.sourcegitcommit: ce35790090ebe768d5f75c108e8d5934fd19c8c7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2017
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Du kan använda appkonfigurationsprinciper med hanterade appar som har stöd för Intune App SDK på enheter som inte har registrerats. 

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övervakning + hantering** + **Intune**.
3. Välj arbetsbelastningen **mobilappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
5. Ange följande information:
    - **Namn**  
      Namnet på den profil som visas i Azure Portal.
    - **Beskrivning**  
      Beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp**  
      Välj **Hantera appar**.
6. Välj **Associerad app** för att välja den app som du ska konfigurera. Välj appen i listan över appar som du har godkänt och synkroniserat med Intune.
7. För varje konfigurationsinställning som stöds av appen anger du **Namn** och **Värde**, och väljer sedan ellipsen (**...**).  
    Välj ellipsen (**...**) och välj **Ta bort** för att ta bort en konfiguration.  
    Intune App SDK-aktiverade appar har stöd för konfigurationer i nyckel/värde-par. Läs dokumentationen för varje app om du vill lära dig mer om vilka nyckel/värde-konfigurationer som stöds.  
    Du kan dessutom använda token som fylls i dynamiskt med data som genereras av programmet.

## <a name="configuration-values-for-using-tokens"></a>Konfigurationsvärden för att använda token

Intune kan generera vissa token och skicka dem till det hanterade programmet. Om din appkonfiguration kan använda en e-postinställning så kan du lägga till en dynamisk e-postadress med hjälp av en token. Ange det namn som förväntas av appen i fältet **Namn** och ange sedan `\{\{mail\}\}` i fältet **Värde**.

Intune stöder följande typer av token i konfigurationsinställningarna:

- \{\{userprincipalname\}\} – till exempel **John@contoso.com**
- \{\{mail\}\} – till exempel **John@contoso.com**
- \{\{partialupn\}\} – till exempel **John**
- \{\{accountid\}\} – till exempel **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- \{\{deviceid\}\} – till exempel **b9841cd9-9843-405f-be28-b2265c59ef97**
- \{\{userid\}\} – till exempel **3ec2c00f-b125-4519-acf0-302ac3761822**
- \{\{username\}\} – till exempel **Johan Danielsson**
- \{\{PrimarySMTPAddress\}\} – till exempel **testuser@ad.domain.com** 


> [!Note]  
> Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.