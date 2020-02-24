---
title: Konfigurationsprinciper för hanterade appar utan enhetsregistrering
titleSuffix: Microsoft Intune
description: Läs om hur du konfigurerar principer för hanterade appar utan enhetsregistrering.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4301afca471d0aa56fa1a0826ad7f88bcdf23de2
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414875"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>Lägg till appkonfigurationsprinciper för hanterade appar utan enhetsregistrering

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Du kan använda appkonfigurationsprinciper med hanterade appar som har stöd för Intune App SDK på enheter som inte har registrerats. 

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Appkonfigurationsprinciper** > **Lägg till** > **Hanterade appar**.
3. Ange följande information på sidan **Grundläggande**:
    - **Namn**: Namnet på den profil som visas i Azure Portal.
    - **Beskrivning**: Beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp**: Hanterade appar har valts.
4. Välj den app du vill konfigurera genom att välja **Välj offentliga appar** eller **Välj anpassade appar**. Välj appen i listan över appar som du har godkänt och synkroniserat med Intune.
5. Visa sidan **Inställningar** genom att klicka på **Nästa**.
6. Ange **Namn** och **Värde** för varje konfigurationsinställning som stöds av appen. 

   Intune App SDK-aktiverade appar har stöd för konfigurationer i nyckel/värde-par. Läs dokumentationen för varje app om du vill lära dig mer om vilka nyckel/värde-konfigurationer som stöds. Observera att du kan använda token som fylls i dynamiskt med data som skapas av programmet. Mer information finns i [Konfigurationsvärden för att använda token](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens). Information om principinställningar för Outlook för iOS/iPadOS-appen finns i [Hantera appkonfiguration för Outlook för iOS/iPadOS med Microsoft Intune](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx).

    Välj ellipsen ( **...** ) och välj **Ta bort** för att ta bort en konfiguration.  

7. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
8. Klicka på **Välj de grupper som ska inkluderas**.
9. Välj en grupp i rutan **Välj grupper att inkludera** och klicka på **Välj**.
10. Klicka på **Välj grupper att utesluta** för att visa det relaterade fönstret.
11. Välj de grupper som du vill exkludera och klicka sedan på **Välj**.

    >[!NOTE]
    >Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir den förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan därför inte användas som en undantagen grupp.

12. Visa sidan **Granska och skapa** genom att klicka på **Nästa**.
13. Lägg till konfigurationsprincipen i Intune genom att klicka på **Skapa**.

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
