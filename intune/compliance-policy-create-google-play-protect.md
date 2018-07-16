---
title: Aktivera Google Play-skyddets efterlevnad med Microsoft Intune
titleSuffix: ''
description: Lär dig hur du skapar en efterlevnadsprincip för Android-enheter för att aktivera Google Play-skydd.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 346e69b56d9ee690e2bc3f3970e47d6d25ddcff7
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905180"
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Så här skapar du en princip för enhetsefterlevnad om du vill aktivera Google Play-skydd

Du kan skapa en ny princip för efterlevnad för Android-plattformen att söka efter Google Play-skyddsefterlevnad (GPP).

Efterlevnadsprincipen som kräver de här inställningarna kan sedan riktas mot en grupp Android-användare eller enheter. Om en enhet inte har dessa inställningar aktiverade uppfyller den inte kraven.

## <a name="create-a-compliance-policy"></a>Skapa en efterlevnadsprincip

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
2. Välj **Enhetsefterlevnad** i gruppen **Hantera**. 
3. Välj **Principer** och välj **Skapa princip**.
4. Ange **Namn** och **Beskrivning** för principen.
5. Välj **Android** som plattform.
6. Välj **Inställningar** > **Enhetens hälsotillstånd**.
7. Konfigurera inställningarna för **Google Play-skydd**.
8. När du har angett inställningarna för Google Play-skydd ska du ange inställningarna för **Systemsäkerhet** och **Enhetsegenskaper**. När du är klar väljer du **OK**.

## <a name="configure-the-google-play-protect-settings"></a>Konfigurera inställningarna för Google Play-skydd

 - **Google Play-tjänster har konfigurerats**  
   Kräv att Google Play-tjänstappen är installerad och aktiverad. Google Play-tjänster tillåter säkerhetsuppdateringar, vilket är ett beroende på grundnivå för många säkerhetsfunktioner på certifierade Google-enheter.
 - **Uppdaterad säkerhetsprovider**  
   Kräv att en uppdaterad säkerhetsprovider kan skydda en enhet från kända säkerhetsproblem.
 - **Hotgenomsökning för appar**  
   Kräv att funktionen Android **Verifiera appar** har aktiverats.
    > [!Note]  
    > Den här funktionen är en kompatibilitetsinställning på den äldre Android-plattformen. Intune kan bara kontrollera om den här inställningen är aktiverad på enhetsnivå. På enheter med Android-arbetsprofiler finns den här inställningen som en konfigurationsinställning för principen. På så sätt kan administratörer aktivera inställningen för en enhet.

    Om företaget använder Androids arbetsprofiler kan du aktivera **Hotgenomsökning för appar** för registrerade enheter. Upprätta en enhetsprofil och kräv systemsäkerhetsinställningen. Mer information finns i [Begränsningsinställningar för Android-arbetsprofilenheter i Microsoft Intune](device-restrictions-android-for-work.md).

 - **SafetyNet-enhetsattestering**  
   Ställ in den integritetsnivå för SafetyNet-enhetsattestering som måste uppnås. Nivåerna omfattar **Inte konfigurerad**, **Kontrollera grundläggande integritet** och **Kontrollera grundläggande integritet och certifierade enheter**.




## <a name="next-steps"></a>Nästa steg

Läs mer om hur man arbetar med Intunes principer för enhetsefterlevnad i [Kom igång med Intunes principer för enhetsefterlevnad](device-compliance-get-started.md).