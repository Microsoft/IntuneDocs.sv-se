---
title: Lägg till konfigurationsprinciper för hanterade Android Enterprise-enheter
titleSuffix: Microsoft Intune
description: Använd appkonfigurationsprinciper i Microsoft Intune för att skicka inställningar när användarna kör en Google Play för företag-app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b30da567d1a25028c51cf8268eab9613a7c3b8af
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755538"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Lägg till konfigurationsprinciper för hanterade Android Enterprise-enheter

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Konfigurationsprinciper för appar i Microsoft Intune tillhandahåller inställningar till Google Play för företag-appar på hanterade Android Enterprise-enheter. Apputvecklaren visar konfigurationsinställningar för Android-hanterade appar. Intune använder dessa exponerade inställningar för att låta administratören konfigurera funktioner för appen. Konfigurationsprincipen för appen tilldelas dina användargrupper. Principinställningarna används när appen söker efter dem, oftast första gången den körs.

> [!NOTE]  
> Det är inte alla appar som stöder appkonfiguration. Kontrollera med apputvecklaren om appen har stöd för appkonfigurationsprinciper.

1. Logga in till [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Välj **Appar** > **Appkonfigurationsprinciper** > **Lägg till** > **Hanterade enheter**. Observera att du kan välja mellan **Hanterade enheter** och **Hanterade appar**. Mer information finns i [Program som stöder appkonfiguration](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. På sidan **Grundläggande** lägger du till följande värden:
    - **Namn** – namnet på den profil som visas i Azure Portal.
    - **Beskrivning** – beskrivning av den profil som visas i Azure Portal.
    - **Enhetsregistreringstyp** – Denna inställning är inställd på **Hanterade enheter**.
4. Välj **Android Enterprise** under **Plattform**.
5. Klicka på **Välj app** bredvid **Målapp**. Fönstret **Associerad app** visas. 
6. I fönstret **Associerad app** väljer du den hanterade app som ska associeras med konfigurationsprincipen och klickar sedan på **OK**.
7. Visa sidan **Inställningar** genom att klicka på **Nästa**.
8. Klicka på **Lägg till** för att visa fönstret **Lägg till behörigheter**.
9. Välj de behörigheter som du vill åsidosätta. De behörigheter som beviljas här åsidosätter principen ”Standardbehörigheter för app” för de valda apparna.
10. Ange **behörighetstillstånd** för varje behörighet. Du kan välja från **Fråga**, **Bevilja automatiskt** eller **Neka automatiskt**. För mer information om behörigheter, se [Android Enterprise-inställningar för att markera enheter som kompatibla eller inkompatibla med hjälp av Intune](~/protect/compliance-policy-create-android-for-work.md).
11. I listrutan väljer du **Konfigurationsinställningsformat**. Välj en av följande metoder för att lägga till konfigurationsinformation:
    - **Använd Configuration Designer**
    - **Ange JSON-data**<br><br>
    Information om hur du använder Configuration Designer finns i [Använda Configuration Designer](#use-the-configuration-designer). Information om hur du anger XML-data finns i [Ange JSON-data](#enter-json-data). 
12. Klicka på **Nästa** för att visa sidan **Tilldelningar**.
13. I listrutan bredvid **Tilldela till** väljer du antingen **Utvalda grupper**, **Alla användare**, **Alla enheter** eller **Alla användare och alla enheter** för att tilldela konfigurationsprincipen för appen.

    ![Skärmbild av fliken Inkludera för principtilldelningar](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. Välj **Alla användare** i listrutan.

    ![Skärmbild av principtilldelningar – listrutealternativet Alla användare](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. Klicka på **Välj grupper att utesluta** för att visa det relaterade fönstret.

    ![Skärmbild av Principtilldelningar – fönstret Välj grupper att undanta](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. Välj de grupper som du vill exkludera och klicka sedan på **Välj**.

    >[!NOTE]
    >Om någon annan grupp redan har inkluderats för en viss tilldelning när du lägger till en grupp så blir den förvald och kan inte ändras för andra tilldelningstyper för inkludering. Gruppen som har använts kan därför inte användas som en undantagen grupp.

17. Visa sidan **Granska och skapa** genom att klicka på **Nästa**.
18. Klicka på **Skapa** för att lägga till konfigurationsprincipen i Intune.

## <a name="use-the-configuration-designer"></a>Använd Configuration Designer

Du kan använda Configuration Designer för Google Play för företag-appar när appen har utformats att ge stöd för konfigurationsinställningar. Konfigurationen gäller för enheter som har registrerats i Intune. Med designern kan du konfigurera specifika konfigurationsvärden för de inställningar som en app har tillgängliga.

1. Välj **Lägg till**. Välj listan med konfigurationsinställningar som du vill ange för appen.

    Om du använder GMail eller Nine Work som e-postapp, se [Android Enterprise-enhetsinställningar för att konfigurera e-post](../email-settings-android-enterprise.md) för mer information om dessa inställningar.

2. För varje nyckel och värde i konfigurationen anger du:

    - **Värdetyp**: Konfigurationsvärdets datatyp. För värdetyperna Sträng kan du alternativt välja en variabel eller certifikatprofil som värdetyp.
    - **Konfigurationsvärde**: Värdet för konfigurationen. Om du väljer variabel eller certifikat som **värdetyp** måste du välja från en lista med variabler eller certifikatprofiler. Om du väljer ett certifikat fylls certifikatalias för det certifikat som har distribuerats till enheten vid körning.

### <a name="supported-variables-for-configuration-values"></a>Variabler för konfigurationsvärden

Du kan välja följande alternativ om du väljer variabel som värdetyp:

| Alternativ | Exempel |
|----|----|
| AAD-enhets-ID | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| Konto-ID | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID för Intune-enhet | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Domain | contoso.com |
| E-post | john@contoso.com |
| Partiellt UPN | john |
| Användar-ID | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Användarnamn | John Doe |
| UPN (User Principal Name) | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Tillåt endast konfigurerade organisationskonton i appar med flera identiteter 

Använd följande nyckel-/värdepar för Android-enheter:

| **Nyckel** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Värden** | <ul><li>Ett eller flera <code>;</code>-avgränsade UPN-namn.</li><li>Endast tillåtna konton är de hanterade användarkonton som anges av den här nyckeln.</li><li> För Intune-registrerade enheter, kan <code>{{userprincipalname}}</code>-token användas för att representera det registrerade användarkontot.</li></ul> |

   > [!NOTE]
   > Du måste använda Outlook för Android 2.2.222 och senare, Word, Excel, PowerPoint för Android 16.0.9327.1000 och senare, eller OneDrive för Android 5.28 och senare när du enbart tillåter konfigurerade organisationskonton med flera identiteter.<p></p>
   > Som Microsoft Intune-administratör kan du styra vilka användarkonton som läggs till i Microsoft Office-program på hanterade enheter. Du kan begränsa åtkomsten till endast tillåtna användarkonton i organisationen och blockera personliga konton på registrerade enheter. De stödjande programmen bearbetar appkonfigurationen och tar bort och blockerar icke-godkända konton.<p></p>

## <a name="enter-json-data"></a>Ange JSON-data

Vissa konfigurationsinställningar för appar (till exempel appar med pakettyper) kan inte konfigureras med Configuration Designer. Använd JSON-redigeraren för dessa värden. Inställningarna skickas automatiskt till appar när de installeras.

1. I **Format för konfigurationsinställningar** väljer du **Ange JSON-redigerare**.
2. Du kan definiera JSON-värden för konfigurationsinställningar i redigeringsprogrammet. Du kan välja **Ladda ned JSON-mall** för att hämta en exempelfil som du sedan kan konfigurera.
3. Välj **OK** och sedan **Lägg till**.

Principen skapas och visas i listan.

När den tilldelade appen körs på en enhet, körs den med de inställningar som du konfigurerade i appkonfigurationsprincipen.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Förkonfigurera behörigheterna för att bevilja tillstånd för appar

Du kan också förkonfigurera behörigheter för att appar ska få åtkomst till funktioner i Android-enheten. Som standard kommer Android-appar som kräver enhetsbehörigheter, t.ex. åtkomst till en plats eller enhetens kamera, att uppmana användarna att godkänna eller neka behörigheter.

En app använder till exempel enhetens mikrofon. Användaren uppmanas att ge appen behörighet att använda mikrofonen.

1. I [administrationscentret för Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) väljer du **Appar** > **Appkonfigurationsprinciper** >  **Lägg till** > **Hanterade enheter**.
2. Lägg till följande egenskaper:

    - **Namn**: Ange ett beskrivande namn på principen. Namnge dina principer så att du enkelt kan identifiera dem senare. Ett bra exempel på ett principnamn är **Android Enterprise fråga apprincip för hela företaget**.
    - **Beskrivning**. Ange en beskrivning av profilen. Denna inställning är valfri, men rekommenderas.
    - **Enhetsregistreringstyp**: Den här inställningen är inställd på **Hanterade enheter**.
    - **Plattform**: Välj **Android**.

3. Välj **Tillhörande app**. Välj den app som du vill definiera en konfigurationsprincip för. Välj i listan med Android-arbetsprofilappar som du har godkänt och synkroniserat med Intune.
4. Välj **Behörigheter** > **Lägg till**. I listan väljer du de tillgängliga appbehörigheterna > **OK**.
5. Välj ett alternativ för varje behörighet som kan beviljas med principen:
    - **Fråga**. Uppmana användaren att godkänna eller neka.
    - **Bevilja automatiskt**. Godkänn automatiskt utan att meddela användaren.
    - **Neka automatiskt**. Neka automatiskt utan att meddela användaren.
6. Om du vill tilldela appkonfigurationsprincipen väljer du appkonfigurationsprincipen > **Tilldelning** > **Välj grupper**. Välj de användargrupper som ska tilldelas > **Välj**.
7. Välj **Spara** för att tilldela principen.

## <a name="additional-information"></a>Ytterligare information

- [Tilldela Managed Google Play-appar till Android enterprise-enheter](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Distribuera appkonfigurationsinställningar för Outlook för iOS och Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Nästa steg

Fortsätt sedan med att [tilldela](apps-deploy.md) och [övervaka](apps-monitor.md) appen.
