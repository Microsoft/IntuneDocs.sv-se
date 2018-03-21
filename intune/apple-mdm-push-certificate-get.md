---
title: "Hämta ett Apple MDM-pushcertifikat"
titlesuffix: Microsoft Intune
description: "Läs om stegen för att hämta ett Apple MDM-pushcertifikat som kan hantera iOS-enheter med Intune."
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 504f2431754aa88ddf79bef4a201cbf7aa032834
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="get-an-apple-mdm-push-certificate"></a>Hämta ett Apple MDM-pushcertifikat

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

 Intune stöder hantering av mobila enheter (MDM) för iPad-, iPhone- och Mac-enheter och ger användarna åtkomst till företagets e-post och appar. Ett MDM Push-certifikat krävs för att Intune ska kunna hantera iOS- och Mac-enheter. När du har lagt till certifikatet i Intune kan dina användare installera företagsportalappen och registrera sina enheter. Du kan också konfigurera hantering av företagsägda iOS-enheter med Apples DEP eller registrera enheter med hjälp av t.ex. Apple Configurator. Mer information om registreringsalternativ för finns [Välj hur du vill registrera iOS-enheter](enrollment-method-choose-ios.md).

## <a name="steps-to-get-your-certificate"></a>Steg för att få ditt certifikat
I [Azure-portalen](https://portal.azure.com) väljer du **Enhetsregistrering** > **Apple-registrering** > **Apple MDM-pushcertifikat**. Utför sedan nedanstående steg i [Azure-portalen](https://portal.azure.com).

**Steg 1. Hämta Intune certifikatsigneringsförfrågan som krävs för att skapa ett certifikat för Apple MDM-pushcertifikat.**<br>
Välj **Ladda ned CSR** för att hämta och spara begärandefilen lokalt. Filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.

  ![Skärmen Konfigurera MDM-pushcertifikat där MDM-push inte har konfigurerats.](./media/create-mdm-push-certificate.png)

**Steg 2. Skapa ett Apple MDM-pushcertifikat**<br>
Välj **Skapa ett MDM-pushcertifikat** för att gå till Apple Push Certificates-portalen. Logga in med ditt företags Apple-ID och klicka på **Skapa ett certifikat**. Välj **Välj fil** och bläddra till begärandefilen för certifikatsignering och välj sedan **Ladda upp**. Välj **Ladda ned** på bekräftelsesidan för att ladda ned certifikatfilen (.pem) och spara filen lokalt.

> [!NOTE]
> Certifikatet associeras med det Apple-ID som användes för att skapa det. Det bästa är att använda ett företags Apple-ID för hanteringsuppgifter och se till att postlådan övervakas av mer än en person, som en distributionslista. Använd aldrig ett personligt Apple-ID.

**Steg 3. Ange det Apple-ID som används för att skapa ett Apple MDM-pushcertifikat.**<br>
Spara ID:t som en påminnelse när du behöver förnya certifikatet.

**Steg 4. Bläddra till Apple MDM-pushcertifikatet för att överföra.**<br>
Gå till certifikatfilen (.pem), välj **Öppna** och välj **Ladda upp**. Med pushcertifikatet kan Intune registrera och hantera Apple-enheter.

## <a name="renew-apple-mdm-push-certificate"></a>Förnya ett Apple MDM-pushcertifikat
MDM Apple-pushcertifikatet är giltigt i ett år och måste förnyas årligen för iOS- och Mac OS-enhetshantering. Om certifikatet går ut kan inte registrerade Apple-enheter kontaktas.

Certifikatet associeras med det Apple-ID som användes för att skapa det. Förnya MDM-pushcertifikatet med samma Apple-ID som användes för att skapa det.

1. I [Azure-portalen](https://portal.azure.com) väljer du **Enhetsregistrering** > **Apple-registrering** och därefter rutan **Apple MDM-pushcertifikat** i informationsområdet.
2. Välj **Ladda ned CSR** för att hämta och spara begärandefilen lokalt. Filen används för att begära ett förtroendecertifikat från Apple Push-certifikatportalen.
3. Välj **Skapa ett MDM-pushcertifikat** för att gå till Apple Push Certificates-portalen. Leta upp det certifikat som du vill förnya och välj **Förnya**.
4. På skärmen för att **förnya pushcertifikat** lägger du till kommentarer som hjälper dig att identifiera certifikatet i framtiden. Välj sedan **Välj fil** för att bläddra till den nya begärandefil som du laddade ned och därefter **Ladda upp**.
   > [!TIP]
   > Ett certifikat kan identifieras av sitt UID. Granska **Ämnes-ID:t** i certifikatinformationen för att hitta UID:ts GUID-del. På en registrerad iOS-enhet går du till **Inställningar** > **Allmänt** > **Enhet** **Hantering** > **Hanteringsprofil** > **Mer information** > **Hanteringsprofil**. Objektet på den andra raden, **Ämne**, innehåller det unika GUID du kan matcha certifikatet i portalen för Apple Push-certifikat.
 
6. På skärmen **Bekräftelse** väljer du **Ladda ned** och sparar PEM-filen lokalt.
7. I [Azure-portalen](https://portal.azure.com) väljer du först bläddringsikonen för **Apple MDM-pushcertifikat** och sedan den .pem-fil som du laddade ned från Apple. Välj sedan **Ladda upp**.

Ditt Apple MDM-pushcertifikat visas som **Aktivt** och har en giltighetstid på 365 dagar.
