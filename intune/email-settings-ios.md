---
title: E-postinställningarna för iOS-enheter i Microsoft Intune – Azure | Microsoft Docs
description: Skapa en e-postprofil för enhetskonfiguration som använder Exchange-servrar och hämtar attribut från Azure Active Directory. Du kan även aktivera SSL, autentisera användare med certifikat eller användarnamn/lösenord och synkronisera e-post på iOS-enheter med hjälp av Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6fd10ab6a1e9dd7249e2ae1d4bf558d190276ed
ms.sourcegitcommit: b0ee8626191961dc07f9f7f9d8e6a5fb09c63350
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51505886"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>E-postprofilinställningar för iOS-enheter – Intune

Använd e-postprofilinställningarna till att konfigurera dina enheter som kör iOS.

> [!IMPORTANT]
> Vi har gjort några förbättringar av S/MIME-funktionen som beskrivs i den här artikeln. S/MIME-funktionen är därför tillfälligt borttagen i Intune. När funktionen lanseras tar vi bort det här meddelandet.

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

- **E-postadressattribut från AAD**: Välj hur e-postadressen för användaren ska skapas. Välj **User principal name** (`user1@contoso.com` eller `user1`) för att använda det fullständiga huvudnamnet som e-postadress. Välj **Primär SMTP-adress** (`user1@contoso.com`) för att använd den primära SMTP-adressen för att logga in på Exchange.
- **Autentiseringsmetod**: Välj antingen **Användarnamn och lösenord** eller **Certifikat** som den autentiseringsmetod som ska användas av e-postprofilen. Azure-multifaktorautentisering stöds inte.
  - Om du valde **Certifikat**, väljer du en SCEP- eller PKCS-certifikatprofil som du har skapat tidigare och som ska användas för att autentisera Exchange-anslutningen.
- **SSL**: **Aktivera** använder Secure Sockets Layer-kommunikation (SSL) för att skicka e-post, ta emot e-post och kommunicera med Exchange-servern.
- **OAuth**: **Aktivera** använder Open Authorization-kommunikation (OAuth) för att skicka e-post, ta emot e-post och kommunicera med Exchange. Om din OAuth-server använder certifikatautentisering väljer du **Certifikat** som **autentiseringsmetod** och inkluderar certifikatet med profilen. Annars väljer du **Användarnamn och lösenord** som **Autentiseringsmetod**. När du använder OAuth ska du se till att:

  - Bekräfta att din e-postlösning stöder OAuth innan du riktar in den här profilen på dina användare. Office 365 Exchange Online stöder OAuth. Lokalt Exchange och andra partner eller tredjepartslösningar stöder kanske inte OAuth. Lokalt Exchange kan konfigureras för modern autentisering (se blogginlägget [Announcing Hybrid Modern Authentication for Exchange On-Premises](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) (Vi presenterar modern hybridautentisering för lokalt Exchange)).

    Om e-postprofilen använder OAuth och e-posttjänsten inte stöder det förefaller alternativet **Ange nytt lösenord** inte fungera. Till exempel händer ingenting när användaren väljer **Ange lösenordet igen** i Apples enhetsinställningar.

  - När OAuth har aktiverats har slutanvändarna en annan inloggningsfunktion för e-post med ”Modern autentisering” med stöd för multifaktorautentisering (MFA). 

  - Vissa organisationer inaktiverar slutanvändarens möjlighet att utföra [programåtkomst med självbetjäning](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access). I det här scenariot kan inloggningsmetoden Modern autentisering misslyckas tills en administratör skapar företagsappen ”iOS-konton” och ger användarna åtkomst till appen i Azure AD.

    Standardåtgärden är att lägga till ett program med hjälp av den funktion i [Programåtkomstpanelen](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) som heter **Lägg till app** **utan företagsgodkännande**. Mer information finns i [tilldela användare till program](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > När du aktiverar OAuth händer följande:  
  > 1. En ny profil skickas till enheter som redan har konfigurerats som mål.
  > 2. Slutanvändarna uppmanas att ange sina autentiseringsuppgifter igen.

- **S/MIME**: **Aktivera S/MIME** för att skicka utgående e-post med hjälp av S/MIME-signering. När det här är aktiverat kan du även kryptera e-postmeddelande till mottagare som kan ta emot krypterad e-post samt dekryptera e-postmeddelanden från avsändare.
  - Om du väljer **Certifikat** väljer du en befintlig PKCS-certifikatprofil för att autentisera Exchange-anslutningen och/eller kryptera e-postväxlingar.
- **Mängd e-post att synkroniseras**: Välj antalet dagars e-post som du vill synkronisera. Eller välj **Obegränsat** om du vill synkronisera all tillgänglig e-post.
- **Tillåt att meddelanden flyttas till andra e-postkonton**: **Aktivera** ger användarna möjlighet att flytta e-postmeddelanden mellan olika konton som användarna har konfigurerat på sina enheter.
- **Tillåt e-postmeddelande från program från tredje part**: **Aktivera** tillåter användare att välja den här profilen som standardkonto för att skicka e-post. Det tillåter att tredjepartsprogram öppnar e-post i den interna e-postappen, t.ex. bifoga filer till e-post.
- **Synkronisera senast använda e-postadresser**: **Aktivera** låter användarna synkronisera listan över e-postadresser som nyligen har använts på enheten med servern.

## <a name="next-steps"></a>Nästa steg
[Konfigurera e-postinställningar i Intune](email-settings-configure.md)
