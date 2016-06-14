---
# required metadata

title: Distribuera appar | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Distribuera appar med Microsoft Intune

Det här avsnittet förklarar några av de begrepp som du behöver förstå innan du börjar distribuera appar med Microsoft Intune.

## Intune-programvaruutgivare
**Microsoft Intune programvaruutgivare** startar när du lägger till eller ändrar appar från administratörskonsolen för Microsoft Intune. Från utgivaren väljer du och konfigurerar en typ av installationsprogram som antingen hämtar appar (program för datorer eller appar för mobila enheter) som ska lagras i Intune-molnlagring eller länkar till en onlinebutik eller ett webbprogram.

### Krav
Innan du börjar använda Microsoft Intune programvaruutgivare måste du installera den kompletta versionen av [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Efter att du har installerat .NET Framework måste du starta om innan Intune-programvaruutgivare kan starta korrekt.

## Molnlagringsutrymme
Alla appar som du distribuerar med installationstypen Programinstallation måste paketeras och överföras till Microsoft Intunes molnlagring. En utvärderingsprenumeration på Intune inkluderar 2 GB molnbaserad lagring som används för att lagra hanterade appar och uppdateringar. I en betald prenumeration ingår 20 GB, med alternativet att köpa ytterligare lagringsutrymme.

Du kan se hur mycket utrymme som du använder och köpa mer lagringsutrymme i noden **Lagringsanvändning** i arbetsytan **Admin**.

Följande regler gäller vid köp av ytterligare molnbaserad lagring för Intune:

-   Du måste ha en aktiv betald prenumeration för att kunna köpa ytterligare lagringsutrymme.

-   Endast faktureringsadministratörer eller globala administratörer för din Microsoft Online-tjänst kan köpa ytterligare lagringsutrymme via Intune-kontoportalen. Om du vill lägga till, ta bort eller hantera dessa administratörer måste du vara global administratör och logga in på Intune-kontoportalen.

-   Om du är en volymlicenskund som har köpt Intune eller Microsoft Intune-tilläggsprogrammet kontaktar du din kontoansvariga på Microsoft eller din Microsoft-partner om du vill ha prisinformation och köpa extra lagringsutrymme.

#### Krav för lagringsutrymme i molnet

-   Alla filer som hör till en app måste vara på samma plats och vara tillgängliga för Intune.

-   Den maximala filstorleken för en fil som du överför är 2 GB.

-   Om du vill överföra filer måste du ha en internethastighet på minst 768 kbps.

## Appdistributionsåtgärder
När du distribuerar appar kan du välja någon av följande distributionsåtgärder:

-   **Nödvändig installation** – Appen installeras på enheten utan att det krävs någon åtgärd från slutanvändaren.

    > [!TIP] När det gäller iOS-enheter som inte är i övervakat läge, samt alla Android-enheter, måste användaren godkänna apperbjudandet innan appen kan installeras.
    >
    > Du kan inte längre skapa nya appdistributioner till iOS-enheter som kör ett operativsystem tidigare än iOS 7.1. Alla befintliga appdistributioner till enheter som kör ett tidigare operativsystem än iOS 7.1 fortsätter att fungera och hanteras av Intune.
    > 
    >  Om en slutanvändare avinstallerar en app som du har distribuerat som en nödvändig installation installeras appen automatiskt om av Intune efter nästa inventeringscykel, som vanligtvis sker var sjunde dag.

-   **Tillgänglig installation** – Appen visas i företagsportalen och slutanvändare kan installera den på begäran.

-   **Avinstallera** – Appen avinstalleras från enheten.

-   **Ej tillämpligt** – Appen visas inte i företagsportalen och installeras inte på några enheter.

#### Distributionsåtgärder som är tillgängliga för olika typer av installationsprogram

|Installationstyp|Nödvändig installation|Tillgänglig installation|Avinstallera|Inte tillämpligt|
|------------------|--------------------|---------------------|-------------|------------------|
|Windows-app-paket (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|Windows-appaket (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|App-paket för mobila enheter (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|App-paket för mobila enheter (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|Windows Installer (distribuerad till en användargrupp)|Nej|Ja|Nej|Ja|
|Windows Installer (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
|Extern länk (distribuerad till en användargrupp)|Nej|Ja|Nej|Ja|
|Extern länk (distribuerad till en enhetsgrupp)|Nej|Nej|Nej|Nej|
|Hanterad iOS-app från App Store (distribuerad till en användargrupp)|Ja|Ja|Ja|Ja|
|Hanterad iOS-app från App Store (distribuerad till en enhetsgrupp)|Ja|Nej|Ja|Ja|
> [!TIP] När du distribuerar appar, om du väljer både användar- och enhetsgrupper, kan du bara distribuera appen som en **Tillgänglig installation**.

## Distributionskonflikter
När två distributioner, med samma distributionsåtgärd, tas emot av en enhet gäller följande regler:

-   Distributioner till en enhetsgrupp har företräde framför distributioner till en användargrupp. Men om en app distribueras till en användargrupp med distributionsåtgärden **Tillgänglig** och samma app också distribueras till en enhetsgrupp med distributionåtgärden **Inte tillämplig**görs appen tillgänglig i företagsportalen, varifrån användare kan installera den.

-   IT-administratörens avsikter har företräde framför användaren.

-   En installationsåtgärd har företräde framför en avinstallationsåtgärd.

-   Om både en nödvändig och en tillgänglig installation tas emot av en enhet kombineras åtgärderna (appen är både nödvändig och tillgänglig).


## Nästa steg

Lär dig hur du [distribuerar appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

<!--HONumber=May16_HO4-->


