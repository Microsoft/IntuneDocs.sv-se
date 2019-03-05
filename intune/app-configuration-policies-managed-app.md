---
title: Konfigurationsprinciper för hanterade appar utan enhetsregistrering
titlesuffix: Microsoft Intune
description: Läs om hur du konfigurerar principer för hanterade appar utan enhetsregistrering.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cde71d7c4c23aeb91c1e43469e23a4764e62b5b
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238599"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Du kan använda appkonfigurationsprinciper med hanterade appar som har stöd för Intune App SDK på enheter som inte har registrerats. 

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj arbetsbelastningen **Klientappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
5. Ange följande information:
    - **Namn**  
      Namnet på den profil som visas i Azure Portal.
    - **Beskrivning**  
      Beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp**  
      Välj **Hantera appar**.
6. Välj den app som ska konfigureras genom att välja **Associerad app** . Välj appen i listan över appar som du har godkänt och synkroniserat med Intune.
7. För varje konfigurationsinställning som stöds av appen anger du **Namn** och **Värde**, och väljer sedan ellipsen (**...**).  
    Välj ellipsen (**...**) och välj **Ta bort** för att ta bort en konfiguration.  
    
Intune App SDK-aktiverade appar har stöd för konfigurationer i nyckel/värde-par. Läs dokumentationen för varje app om du vill lära dig mer om vilka nyckel/värde-konfigurationer som stöds. Observera att du kan använda token som fylls i dynamiskt med data som skapas av programmet. Information om principinställningar för Outlook för iOS-appen, se [Hantera appkonfiguration för Outlook för iOS med Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

## <a name="configuration-values-for-using-tokens"></a>Konfigurationsvärden för att använda token

Intune kan generera vissa token och skicka dem till det hanterade programmet. Om din appkonfiguration kan använda en e-postinställning så kan du lägga till en dynamisk e-postadress med hjälp av en token. Ange det namn som förväntas av appen i fältet **Namn** och ange sedan `\{\{mail\}\}` i fältet **Värde**.

Intune stöder följande typer av token i konfigurationsinställningarna. Andra anpassade nyckel/värde-par stöds inte.

- \{\{userprincipalname\}\} – till exempel John@contoso.com
- \{\{mail\}\} – till exempel John@contoso.com
- \{\{partialupn\}\} – till exempel John
- \{\{accountid\}\} – till exempel fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\} – till exempel 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\} – till exempel Johan Danielsson
- \{\{PrimarySMTPAddress\}\} – till exempel testuser@ad.domain.com


> [!Note]  
> Tecknen \{\{ och \}\} används endast av tokentyper och får inte användas för andra ändamål.

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen som vanligt.
