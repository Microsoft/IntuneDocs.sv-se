---
title: E-postinställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en e-postprofil för enhetskonfiguration som använder Exchange-servrar och hämtar attribut från Azure Active Directory. Du kan även aktivera SSL, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post på iOS-enheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a231adf4e1f5687bc88c8c9b15241d3f89e711d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905350"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>E-postprofilinställningar för iOS-enheter – Intune

Använd e-postprofilinställningarna till att konfigurera dina enheter som kör iOS.

## <a name="email-settings"></a>E-postinställningar

- **E-postserver**: Ange värdnamnet för din Exchange-server.
- **Kontonamn**: Ange visningsnamnet för e-postkontot. Namnet visas för användare på deras enheter.
- **Användarnamnattribut från AAD**: Namnet är attributet som Intune hämtar från Azure Active Directory (AAD). Intune genererar användarnamnet som används av den här profilen. Alternativen är:
  - **UPN (User Principal Name)**: Hämtar namnet, till exempel `user1` eller `user1@contoso.com`
  - **Primär SMTP-adress**: Hämtar namnet i e-postadressformat, till exempel `user1@contoso.com`
  - **sAM-kontonamn**: Kräver domänen, till exempel `domain\user1`.

    Ange även:  
    - **Källa för användardomännamn**: Välj **AAD** (Azure Active Directory) eller **Anpassat**.

      När du väljer att hämta attributen från **AAD** anger du:
      - **Attribut för användardomännamn från AAD**: Välj att hämta attributet för **Fullständigt domännamn** eller **NetBIOS-namn** för användaren

      När du väljer att använda **anpassade** attribut anger du:
      - **Anpassat domännamn att använda**: Ange ett värde som Intune använder för domännamnet, till exempel `contoso.com` eller `contoso`

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **UPN (User Principal Name)** (`user1@contoso.com` eller `user1`) om du vill använda det fullständiga huvudnamnet som e-postadress eller **Primär SMTP-adress** (`user1@contoso.com`) om du vill använda den primära SMTP-adressen för att logga in på Exchange.
- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen. Azure Multi-Factor Authentication stöds inte.
  - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
- **SSL**: Använd Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **S/MIME**: Skicka utgående e-post med S/MIME-signering.
  - Om du valde **Certifikat** väljer du en PKCS-certifikatprofil som du har skapat tidigare för att autentisera Exchange-anslutningen.
- **Mängd e-post att synkroniseras**: Välj antalet dagars e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Tillåt att meddelanden flyttas till andra e-postkonton**: Ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som de har konfigurerat på sin enhet.
- **Tillåt att e-post skickas från tredjepartsprogram**: Tillåt att användaren väljer den här profilen som standardkonto för att skicka e-post och att appar från andra leverantörer öppnar e-post i den interna e-postappen, till exempel för att bifoga filer i e-postmeddelanden.
- **Synkronisera senast använda e-postadresser**: Låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)
