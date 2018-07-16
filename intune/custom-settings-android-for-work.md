---
title: Anpassade profilinställningar i Intune för Android-arbetsprofiler
titlesuffix: Microsoft Intune
description: Läs hur du skapar anpassade profilinställningar i Microsoft Intune för Android-arbetsprofilenheter.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/12/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 109c50acf194598017aa507a0979ad3b9298de9e
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905299"
---
# <a name="create-intune-custom-profile-settings-for-android-work-profile-devices"></a>Skapa anpassade profilinställningar i Intune för Android-arbetsprofilenheter

Använd en anpassad konfigurationsprincip för Android-arbetsprofiler i Intune för att tilldela OMA-URI-inställningar som kan användas till att styra funktioner på Android-arbetsprofilenheter. Detta är standardinställningar som många tillverkare av mobila enheter använder för att styra enhetsfunktioner.

Funktionen är avsedd för att kunna tilldela Android-inställningar som inte går att konfigurera med Intune-principer. Intune har för närvarande stöd för ett begränsat antal anpassade Android-principer. Se exemplen i den här artikeln för att ta reda på vilka principer du kan konfigurera.

## <a name="create-a-custom-profile"></a>Skapa en anpassad profil

1. Kom igång med hjälp av anvisningarna i [Konfigurera anpassade enhetsinställningar](custom-settings-configure.md). I **Plattform** väljer du **Android enterprise** och i **Profiltyp** väljer du **Anpassad**.
2. På bladet **Anpassade OMA-URI-inställningar** väljer du **Lägg till** för att lägga till en ny inställning.
3. På bladet **Lägg till rad** konfigurerar du följande:
    - **Namn** – Ange ett unikt namn för de anpassade inställningarna för Android-arbetsprofiler, som hjälper dig att identifiera den i Azure Portal.
    - **Beskrivning** – Ange en beskrivning med en översikt av den anpassade Android-principen, samt annan information som gör det enkelt att hitta den.
    - **OMA-URI** – Ange den OMA-URI som du vill ange en inställning för.
    - **Datatyp** – Ange den datatyp som du vill specificera den här OMA-URI-inställningen med. Välj mellan **Sträng**, **Sträng (XML-fil)**, **Datum och tid**, **Heltal**, **Flyttal**, **Boolesk** eller **Base64 (fil)**.
    - **Värde** – Ange det värde som ska associeras med den OMA-URI som du tidigare angav. Metoden du använder för att ange värdet varierar beroende på datatypen som du har valt. Om du till exempel har valt **Datum och tid**, väljer du värdet från en datumväljare.
4. När du är klar väljer du OK för att återgå till **Anpassade OMA-URI-inställningar**. Lägg sedan till fler inställningar eller välj **Skapa** för att skapa den anpassade profilen.


## <a name="example"></a>Exempel

I det här exemplet skapar du en anpassad profil som kan användas för att begränsa om åtgärderna för att kopiera och klistra in mellan arbetsappar och personliga appar ska vara tillåtna på Android-arbetsprofilenheter.

1. Använd metoden i den här artikeln för att skapa en anpassad profil för Android-arbetsprofilenheter med följande värden:
    - **Namn** – Ange ”Blockera kopiera och klistra in” eller välj en egen text.
    - **Beskrivning** – Ange ”Blockera kopiera/klistra in mellan arbetsappar och personliga appar” eller välj en egen text.
    - **OMA-URI** – Ange **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**.
    - **Datatyp** – Välj **Boolesk** för att visa att värdet för den här OMA-URI:n är antingen **Sant** eller **Falskt**.
    - **Värde** – Välj **Sant**.
2. Du bör få en inställning som liknar den här bilden.
![Blockera kopiera och klistra in för Android-arbetsprofil.](./media/custom-policy-afw-copy-paste.png)
3. Nu när du tilldelar den här anpassade profilen till Android-arbetsprofilenheter som du hanterar, kommer funktionen för att kopiera och klistra in att blockeras mellan arbetsappar och personliga profiler.