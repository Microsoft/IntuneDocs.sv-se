---
title: Lägg till konfigurationsprinciper för hanterade Android-enheter
titlesuffix: Microsoft Intune
description: Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en Android-arbetsprofilapp.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: db6aed3d87b8a8df55c5c95e52eb3dd9ccc690a7
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386956"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Lägg till konfigurationsprinciper för hanterade Android-enheter

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar till Android-arbetsprofilappar. Apputvecklaren måste exponera Android-hanterade konfigurationsinställningarna för att ange konfigurationsinställningar för appen. Tilldela appkonfigurationsprincipen till den grupp där du vill tillämpa inställningarna.  Principinställningarna används när appen söker efter dem, oftast första gången den körs.

> [!Note]  
> Det är inte alla appar som stöder appkonfiguration. Kontrollera med apputvecklaren om appen har stöd för appkonfigurationsprinciper.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj arbetsbelastningen **Klientappar**.
4. Under gruppen **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
5. Ange följande information:
    - **Namn** – namnet på den profil som visas i Azure-portalen.
    - **Beskrivning** – beskrivning av den profil som visas i Azure-portalen.
    - **Registreringstyp för enhet** – välj **Hanterade enheter**.
6. Välj **Android** för **Plattform**.
7. Välj **Tillhörande app** för att välja den app som du vill definiera en appkonfigurationsprincip för. Välj i listan med Android-arbetsprofilappar som du har godkänt och synkroniserat med Intune.
8. Välj **Behörigheter**. Du kan ange konfigurationer med:
    - [Configuration Designer](#Use-the-configuration-designer)
    - [JSON-redigerare](#Enter-the-JSON-editor)
9. Välj **OK** och sedan **Lägg till**.

## <a name="use-the-configuration-designer"></a>Använd Configuration Designer

Du kan använda Configuration Designer för Android-appar som stöder konfiguration. Konfigurationen tillämpas på enheter som är registrerade i Intune. Med designern kan du konfigurera specifika konfigurationsvärden för de inställningar som en app har tillgängliga.

Välj **Lägg till** för att välja listan med konfigurationsinställningar som du vill ange för appen.  
För varje nyckel och värde i konfigurationen anger du:

  - **Värdetyp**  
    Konfigurationsvärdets datatyp. För värdetyperna Sträng kan du alternativt välja en variabel eller certifikatprofil som värdetyp.
  - **Konfigurationsvärde**  
    Värdet för konfigurationen. Om du väljer variabel eller certifikat som värdetyp måste du välja från en lista med variabler eller certifikatprofiler i listrutan med konfigurationsvärden.  Om du väljer ett certifikat fylls certifikatalias för det certifikat som har distribuerats till enheten vid körning.
    
### <a name="supported-variables-for-configuration-values"></a>Variabler för konfigurationsvärden

Du kan välja följande alternativ om du väljer variabel som värdetyp:

| Alternativ | Exempel |
|----|----|
| E-post | john@contoso.com |
| UPN (User Principal Name) | john@contoso.com |
| Partiellt UPN | john |
| Domain | contoso.com |
| Användarnamn | John Doe |
| Konto-ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| Användar-ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Enhets-ID | b9841cd9-9843-405f-be28-b2265c59ef97 |

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Tillåt endast konfigurerade organisationskonton i appar med flera identiteter 

Använd följande nyckel-/värdepar för Android-enheter:

| **Nyckel** | com.microsoft.intune.mam.AllowedAccountUPNs |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Värden** | <ul><li>Ett eller flera <code>;</code>-avgränsade UPN-namn.</li><li>Endast tillåtna konton är de hanterade användarkonton som anges av den här nyckeln.</li><li> För Intune-registrerade enheter, kan <code>{{userprincipalname}}</code>-token användas för att representera det registrerade användarkontot.</li></ul> |

   > [!NOTE]
   > Du måste använda Outlook för Android 2.2.222 eller senare, när endast konfigurerade organisationskonton med flera identiteter tillåts.<p></p>
   > Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. De stödjande programmen bearbetar appkonfigurationen och tar bort och blockerar icke-godkända konton.<p></p>
   > För Microsoft Word, Microsoft Excel, Microsoft PowerPoint, måste du använda appversion 16.0.9327.1000 och senare. 

## <a name="enter-the-json-editor"></a>Gå in i JSON-redigeraren

Vissa konfigurationsinställningar för appar (till exempel de med pakettyper) kan inte konfigureras med Configuration Designer. Du måste använda JSON-redigeraren för dessa värden. Inställningarna skickas automatiskt till appar när de installeras.

1. I **Format för konfigurationsinställningar** väljer du **Ange JSON-redigerare**.
2. Du kan definiera JSON-värden för konfigurationsinställningar i redigeringsprogrammet. Du kan välja **Ladda ned JSON-mall** för att hämta en exempelfil som du sedan kan konfigurera.
3. Välj **OK** och sedan **Lägg till**.

Principen skapas och visas på bladet med principlistan.

När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Förkonfigurera behörigheterna för att bevilja tillstånd för appar

Du kan också förkonfigurera behörigheter för att appar ska få åtkomst till funktioner i Android-enheten. Som standard kommer Android-appar som kräver enhetsbehörigheter, t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter. Om till exempel en app ska använda enhetens mikrofon, ombeds användaren att bevilja appen behörighet att använda mikrofonen.

1. Logga in på [Azure-portalen](https://portal.azure.com).
2. Välj **Alla tjänster** > **Intune**. Intune finns i avsnittet **Övervakning och hantering**.
3. Välj **Klientappar**.
3. Under **Hantera** väljer du **Appkonfigurationsprinciper** och väljer sedan **Lägg till**.
4. Ange följande information:
    - **Namn**. Namnet på den profil som visas i Azure-portalen.
    - **Beskrivning**. Beskrivning av den profil som visas i Azure-portalen.
    - **Enhetsregistreringstyp**. Välj **Hanterade enheter**.
    - **Plattform**. Välj **Android**.
5. Välj **Tillhörande app** för att välja den app som du vill definiera en konfigurationsprincip för. Välj i listan med Android-arbetsprofilappar som du har godkänt och synkroniserat med Intune.
6. Välj **Behörigheter** och sedan **Lägg till**.
7. Välj i listan med tillgängliga appbehörigheter och välj sedan **OK**.
8. Välj ett alternativ för varje behörighet som kan beviljas med principen:
    - **Fråga**. Uppmana användaren att godkänna eller neka.
    - **Bevilja automatiskt**. Godkänn automatiskt utan att meddela användaren.
    - **Neka automatiskt**. Neka automatiskt utan att meddela användaren.
9. Om du vill tilldela appkonfigurationsprincipen väljer du appkonfigurationsprincipen, **Tilldelning** och sedan **Välj grupper**.
10. Välj först de användargrupper som ska tilldelas och sedan **Välj**.
11. Välj **Spara** för att tilldela principen.

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen.

