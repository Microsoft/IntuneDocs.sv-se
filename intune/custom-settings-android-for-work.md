---
title: Lägga till anpassade inställningar för Android Enterprise-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Lägga till eller skapa en anpassad profil för Android Enterprise-enheter i Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 494b8011b942026cf932b6f2f1851c5f0ffaadbb
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566479"
---
# <a name="use-custom-settings-for-android-enterprise-devices-in-microsoft-intune"></a>Använda anpassade inställningar för Android Enterprise-enheter i Microsoft Intune

Med Microsoft Intune kan du lägga till eller skapa anpassade inställningar för dina Android Enterprise-enheter med hjälp av en ”anpassad profil”. Anpassade profiler är en funktion i Intune. De gör att du kan lägga till enhetsinställningar och funktioner som inte är inbyggda i Intune.

Anpassade profiler för Android Enterprise använder OMA-URI-inställningar (Open Mobile Alliance Uniform Resource Identifier) för att styra funktioner på Android Enterprise-enheter. De här inställningarna används vanligtvis av tillverkare av mobila enheter för att styra dessa funktioner.

Intune stöder ett begränsat antal anpassade Android-profiler.

Den här artikeln beskriver hur du skapar en anpassad profil för Android Enterprise-enheter. Den innehåller också ett exempel på en anpassad profil som blockerar kopierings- och inklistringsfunktionerna.

## <a name="create-the-profile"></a>Skapa profilen

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `android enterprise custom profile`
    - **Beskrivning:** Ange en beskrivning för profilen
    - **Plattform**: Välj **Android-företag**
    - **Profiltyp**: Välj **Anpassad**

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange ett unikt namn för OMA-URI-inställningen så att du lätt kan hitta den.
    - **Beskrivning**: Ange en beskrivning som ger en översikt över inställningen, samt annan viktig information.
    - **OMA-URI**: Ange den OMA-URI som du vill använda som inställning.
    - **Datatyp**: Välj den datatyp som du vill använda för den här OMA-URI-inställningen. Alternativen är:

      - Sträng
      - Sträng (XML-fil)
      - Datum och tid
      - Heltal
      - Flyttal
      - Boolesk
      - Base64 (fil)

    - **Värde**: Ange det datavärde som du vill associera med den OMA-URI som du har angett. Värdet beror på vilken datatyp du valt. Om du till exempel valde **Datum och tid**, väljer du värdet från en datumväljare.

    När du har lagt till några inställningar kan du välja **Exportera**. **Exportera** skapar en lista över alla värden som du har lagt till i en fil med kommaavgränsade värden (.csv).

5. Klicka på **OK** för att spara ändringarna. Fortsätt att lägga till fler inställningar efter behov.
6. När du är klar väljer du **OK** > **Skapa** för att skapa Intune-profilen. När du är klar visas din profil i listan **Enhetskonfiguration – profiler**.

## <a name="example"></a>Exempel

I det här exemplet skapar du en anpassad profil som begränsar kopierings- och inklistringsåtgärder mellan arbetsappar och personliga appar på Android Enterprise-enheter.

1. I [Azure Portal](https://portal.azure.com) välj **Alla tjänster**, filtrera på **Intune** och välj **Microsoft Intune**.
2. Välj **Enhetskonfiguration** > **Profiler** > **Skapa profil**.
3. Ange följande inställningar:

    - **Namn**: Ange ett namn för profilen, till exempel `android ent block copy paste custom profile`.
    - **Beskrivning:** Ange en beskrivning för profilen.
    - **Plattform**: Välj **Android-företag**.
    - **Profiltyp**: Välj **Anpassad**.

4. I **Anpassade OMA-URI-inställningar** väljer du **Lägg till**. Ange följande inställningar:

    - **Namn**: Ange något som exempelvis `Block copy and paste`.
    - **Beskrivning**: Ange något som exempelvis `Blocks copy/paste between work and personal apps`.
    - **OMA-URI**: Ange `./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste`.
    - **Datatyp**: Välj **Booleskt** så att värdet för den här OMA-URI:n är **Sant** eller **Falskt**.
    - **Värde**: Välj **Sant**.

5. När du har angett inställningarna bör din miljö likna följande bild:

    ![Blockera kopiering och inklistring för Android-arbetsprofil.](./media/custom-policy-afw-copy-paste.png)

När du tilldelar den här profilen till Android Enterprise-enheter som du hanterar blockeras kopierings- och inklistringsfunktionerna mellan appar i arbetsprofiler och personliga profiler.

## <a name="next-steps"></a>Nästa steg

Profilen har skapats, men den gör inte något än. Nu ska du [tilldela profilen](device-profile-assign.md).

Se hur du [skapar profilen på Android-enheter](custom-settings-android.md).
