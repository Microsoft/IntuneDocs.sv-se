---
title: E-postinställningar för Android Enterprise i Microsoft Intune – Azure | Microsoft Docs
description: Skapa e-postprofiler för enhetskonfigurationer som använder Exchange-servrar och hämta attribut från Azure Active Directory. Aktivera SSL eller SMIME, autentisera användare med certifikat eller användarnamn/lösenord, samt synkronisera e-post och scheman på Android-arbetsprofilenheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8e13c2dce5e8da2ce71b97de496d5234096c3b22
ms.sourcegitcommit: b78793ccbef2a644a759ca3110ea73e7ed6ceb8f
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2019
ms.locfileid: "71301953"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Enhetsinställningar för Android Enterprise-enheter för att konfigurera e-post, autentisering och synkronisering i Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Den här artikeln beskriver de olika e-postinställningar som du kan styra på Android Enterprise-enheter. Som en del av din lösning för hantering av mobilenheter kan du använda dessa inställningar till att konfigurera en e-postserver, använda SSL för att kryptera e-postmeddelanden och mycket mer.

Som en Intune-administratör kan du skapa och tilldela e-postinställningar till följande Android Enterprise-enheter i arbetsprofilen.

Mer information om e-postprofiler i Intune finns i [Konfigurera e-postinställningar](email-settings-configure.md).

## <a name="before-you-begin"></a>Innan du börjar

Skapa en [profil för enhets konfiguration](email-settings-configure.md#create-a-device-profile) (Välj arbets profil) eller skapa en [konfigurations princip för appar](app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android enterprise

- **E-postapp**: Välj antingen **Gmail** eller **Nine Work**
- **E-postserver**: Värdnamnet för din Exchange-server. Ange till exempel `outlook.office365.com`.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (Azure AD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:

  - **UPN (User Principal Name)** : Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Användarnamn**: Hämtar bara namnet, till exempel `user1`

- **E-postadressattribut från AAD**: Namnet är det e-postattribut som Intune hämtar från Azure AD. Intune genererar den e-postadress som används av den här profilen. Alternativen är:
  - **User principal name**: använder det fullständiga huvudnamnet, till exempel `user1@contoso.com` eller `user1`, som e-postadress.
  - **Primär SMTP-adress**: Använder den primära SMTP-adressen, till exempel `user1@contoso.com`, för att logga in på Exchange.

- **Autentiseringsmetod**: Välj **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen.
  - Om du väljer **Certifikat** så väljer du en klients SCEP- eller PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **SSL**: Välj **Aktivera** för att använda Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **Mängd e-post att synkroniseras**: Välj den tidslängd för e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Innehållstyp som ska synkroniseras:** (endast Nine Work): Välj vilka data som du vill synkronisera på enheterna. Alternativen är:
  - **Kontakter**: Välj **Aktivera** för att tillåta slutanvändare att synkronisera kontakter till sina enheter.
  - **Kalender**: Välj **Aktivera** för att tillåta användare att synkronisera kalendern till sina enheter.
  - **Uppgifter**: Välj **Aktivera** för att tillåta användare att synkronisera uppgifter till sina enheter.

## <a name="next-steps"></a>Nästa steg

[Tilldela profilen](device-profile-assign.md) och [övervaka dess status](device-profile-monitor.md).

Du kan också skapa e-postprofiler för [Android Samsung Konx](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 och senare](email-settings-windows-10.md) och [Windows Phone 8.1](email-settings-windows-phone-8-1.md)-enheter.
