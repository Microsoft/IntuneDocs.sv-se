---
title: "Hämta ett Apple MDM-pushcertifikat"
titleSuffix: Intune on Azure
description: "Läs om stegen för att hämta ett Apple MDM-pushcertifikat för att hantera iOS-enheter med Intune.”"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 915b432ed32565e820e16a65932fcdeac00d9bc3
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>Hämta ett Apple MDM-pushcertifikat

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och Mac-enheter och ger användarna åtkomst till företagets e-post och appar. Ett MDM Push-certifikat krävs för att Intune ska kunna hantera iOS- och Mac-enheter. När du har lagt till certifikatet i Intune kan dina användare installera företagsportalappen och registrera sina enheter. Du kan också konfigurera hantering av företagsägda iOS-enheter med Apples DEP eller registrera enheter med hjälp av t.ex. Apple Configurator. Mer information om registreringsalternativ för finns [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Steg för att få ditt certifikat
I Intune-portalen väljer du **Enhetsregistrering** > **Apple-registrering** **Apple MDM-pushcertifikat** och följer sedan följande steg i Azure-portalen.

**Steg 1. Hämta Intune certifikatsigneringsförfrågan som krävs för att skapa ett certifikat för Apple MDM-pushcertifikat.**<br>
Välj **Ladda ned CSR** för att hämta och spara begärandefilen lokalt. Filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

  ![Skärmbild som visar skärmen Konfigurera MDM-pushcertifikat där MDM-push inte har ställts in.](./media/create-mdm-push-certificate.png)

**Steg 2. Skapa ett Apple MDM-pushcertifikat**<br>
Välj **Skapa ett MDM-pushcertifikat** för att gå till Apple Push Certificates-portalen. Logga in med företagets Apple-ID för att skapa pushcertifikatet med hjälp av begärandefilen. När du har valt **Överför** på Apple Push-certifikatportalen får du en JSON-fil. Använd den här filen för pushcertifikatet. Slutför hämtningen, gå tillbaka till Apple Push-certifikatportalen, leta upp Certifikat för servrar från tredje part och klicka på **Hämta**. Hämta pushcertifikatet (.pem) och spara filen lokalt.

> [!NOTE]
> Certifikatet associeras med det Apple-ID som användes för att skapa det. Vi rekommenderar att du använder ett Apple-ID för företag för hanteringsaktiviteter. Använd aldrig ett personligt Apple-ID.

**Steg 3. Ange det Apple-ID som används för att skapa ett Apple MDM-pushcertifikat.**

**Steg 4. Bläddra till Apple MDM-pushcertifikatet för att överföra.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera iOS-enheter genom push-överföring av principer till registrerade mobila enheter.

## <a name="renew-apple-mdm-push-certificate"></a>Förnya ett Apple MDM-pushcertifikat
MDM Apple-pushcertifikatet är giltigt i ett år och måste förnyas årligen för iOS- och Mac OS-enhetshantering. Om certifikatet går ut kan inte registrerade Apple-enheter kontaktas.

Certifikatet associeras med det Apple-ID som användes för att skapa det. Förnya MDM-pushcertifikatet med samma Apple-ID som användes för att skapa det.

> [!NOTE]
> Certifikatet associeras med det Apple-ID som användes för att skapa det. Vi rekommenderar att du använder ett Apple-ID för företag för hanteringsaktiviteter. Använd aldrig ett personligt Apple-ID.

1. I Intune-portalen väljer du **Enhetsregistrering** > **Apple-registrering** och därefter **Apple MDM-pushcertifikat**.
2. Välj **Ladda ned CSR** för att hämta och spara begärandefilen lokalt. Filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.
3. Leta upp det certifikat som du vill förnya och välj **Förnya**.
4. På skärmen **Förnya pushcertifikat** lägger du till kommentarer som hjälper dig att identifiera certifikatet i framtiden, väljer **Välj fil** för att bläddra till den nya begärandefilen som du laddade ned och väljer sedan **Ladda upp**.
5. På skärmen **Bekräftelse** väljer du **Ladda ned** och sparar PEM-filen lokalt.
6. På Azure Intune-portalen väljer du bläddringsikonen för **Apple MDM-pushcertifikatet**, väljer den PEM-fil som du laddade ned från Apple och väljer sedan **Ladda upp**.

Ditt Apple MDM-pushcertifikat visas som **Aktivt** och har en giltighetstid på 365 dagar.
