---
title: Konfigurera enhetsbaserad villkorlig åtkomst med Intune
titleSuffix: Microsoft Intune
description: Lär dig att skapa principer för enhetsbaserad villkorlig åtkomst, baserat på Microsoft Intune enhetens efterlevnad och hantering av mobilappar.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed6259c996772817ceaa8ec827c8ac506adfd399
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530464"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Skapa en princip för enhetsbaserad villkorlig åtkomst

Med Intune kan du förbättra villkorlig åtkomst i Azure Active Directory genom att lägga till efterlevnad för mobila enheter i åtkomstkontrollerna. När du har skapat en efterlevnadsprincip i Intune som definierar att kraven för enheterna ska vara kompatibla, kan du använda en enhetsefterlevnadsstatus som antingen tillåter eller blockerar åtkomst till dina appar och tjänster. Du kan göra detta genom att skapa en princip för villkorlig åtkomst som använder inställningen **Kräv att enheten är markerad som kompatibel**.  

En princip för villkorlig åtkomst anger de appar eller tjänster som du vill skydda, de villkor under vilka appar eller tjänster kan nås och vilka användare som principen gäller för. Villkorlig åtkomst är en premiumfunktion som kan konfigureras i Azure Active Directory, men du kan också ange samma principer från Intune-portalen. Den nod för villkorsstyrd åtkomst som nås från *Intune* är samma nod som den som nås från *Azure AD*.  

> [!IMPORTANT]
> Innan du konfigurerar villkorlig åtkomst måste du konfigurera Intunes principer för enhetsefterlevnad till att utvärdera enheter baserat på om de uppfyller specifika krav. Se [Komma igång med efterlevnadsprinciper för enheter i Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Skapa princip för villkorlig åtkomst

1. I Intune-portalen väljer du **Villkorlig åtkomst** > **Principer** > **Ny princip**.
   
    ![Skapa en ny princip för villkorlig åtkomst](media/create-conditional-access-intune/create-ca.png)
 
2. Under **Tilldelningar** väljer du **Användare och grupper**. 
3. På fliken **Inkludera** identifierar du de användare eller grupper som principen för villkorlig åtkomst ska tillämpas för. När du har valt vilka du vill inkludera kan du använda fliken **Undanta**, om det finns några användare, roller eller grupper som du vill undanta från principen.  
    - **Alla användare**: Välj detta alternativ för att tillämpa principen på alla användare och grupper, inklusive interna användare och gästanvändare.
  
    - **Välj användare och grupper**: Välj det här alternativet och ange ett eller flera av följande alternativ:
  
      a. **Alla gästanvändare**: Välj det här alternativet för att inkludera eller exkludera externa gästanvändare (till exempel partners och externa medarbetare)
       
      b. **Katalogroller**: Välj en eller flera Azure AD-roller för att inkludera eller exkludera användare som har tilldelats rollerna.
      
      c. **Användare och grupper**: Välj det här alternativet för att söka efter och välja enskilda användare eller grupper som du vill inkludera eller exkludera.
     
       > [!TIP]  
       > Testa principen på en mindre grupp användare för att se att den fungerar som förväntat.
4. Välj **Klar**.
5. Under **Tilldelningar** väljer du **Molnappar**. 
6. På **fliken Inkludera** identifierar du de appar och tjänster som du vill skydda med principen för villkorlig åtkomst. Du kan sedan använda fliken **Undanta** om det finns några appar eller tjänster som du vill undanta från principen.
    - **Alla molnappar**: Välj det här alternativet om du vill tillämpa principen på alla appar.
      > [!IMPORTANT]  
      > Microsoft Azure Management-appen för åtkomst till Azure-portalen ingår i den här listan. Använd fliken **Undanta** antingen här eller i alternativen för **Användare och grupper** för att se till att du (eller de användare eller grupper som du anger) kommer att kunna logga in på Azure-portalen. 

    - **Välj appar**: Välj det här alternativet, välj **Välj** och använd sedan listan med program för att söka efter och välja de appar eller tjänster som du vill skydda.
    
      ![Skapa en ny princip för villkorlig åtkomst](media/create-conditional-access-intune/create-ca-select-apps.png)

7. Välj **Klar**.
8. Under **Tilldelningar** väljer du **Villkor**.
    - **Inloggningsrisk**: Välj Ja om du vill använda Azure AD Identity Protections inloggningsriskidentifiering med den här principen och välj sedan de inloggningsrisknivåer som principen ska gälla för.
    - **Enhetsplattformar**: På fliken **Inkludera** identifierar du de enhetsplattformar som du vill att principen för villkorlig åtkomst ska tillämpas på. Använd fliken **Undanta** för att undanta plattformar från den här principen.
    - **Platser**: På fliken **Inkludera** anger du om principen gäller för alla platser, betrodda nätverksplatser som kontrolleras av IT-avdelningen eller specifika nätverksplatser. Använd fliken **Undanta** för att undanta nätverksplatser från principen. 
    - **Klientappar**: Välj **Ja** för att ange om principen ska tillämpas på webbläsarappar, mobilappar och skrivbordsklienter. Du kan också välja **Moderna autentiseringsklienter** (till exempel Outlook för iOS eller Outlook för Android) och **Exchange ActiveSync-klienter**.
    - **Enhetstillstånd**: Principen för villkorlig åtkomst gäller alla enhetstillstånd, förutsatt att du väljer Ja och uttryckligen utelämnar de tillstånd som anger Hybrid Azure AD-ansluten enhet eller Enheten är markerad som kompatibel (eller båda).
    
      ![Skapa en ny princip för villkorlig åtkomst](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Om du vill skydda både **Modern autentisering**-klienter och **Exchange ActiveSync-klienter**, skapar du två separata principer för villkorlig åtkomst, en för varje klienttyp. Även om Exchange ActiveSync stöder modern autentisering, är det bara plattformar som stöds av Exchange ActiveSync. Andra villkor, inklusive multifaktorautentisering, stöds inte. Om du effektivt vill skydda åtkomsten till Exchange Online från Exchange ActiveSync, skapar du en princip för villkorlig åtkomst som anger molnappen Office 365 Exchange Online och klientappen Exchange ActiveSync där Tillämpa bara principen på plattformar som stöds är valt.

9. Välj **Klar**.
10. Under **Åtkomstkontroller** väljer du **Bevilja**. Konfigurera vad som händer baserat på de villkor som du har konfigurerat.  Du kan välja bland följande alternativ:
    - **Blockera åtkomst**: De användare som anges i den här principen kommer att nekas åtkomst till appar enligt de villkor som du har angett.
    - **Bevilja åtkomst**: De användare som anges i den här principen kommer att beviljas åtkomst, men du kan kräva någon av följande ytterligare åtgärder:
      - **Kräv multifaktorautentisering**: Användaren måste slutföra ytterligare säkerhetskrav, t.ex. ett telefonsamtal eller SMS.
      - **Kräv att enheten är markerad som kompatibel**: Enheten måste vara kompatibel med Intune. Om enheten inte är kompatibel, kommer användaren ges möjlighet att registrera enheten i Intune. 
      - **Kräv Hybrid Azure AD-kopplad enhet**: Enheterna måste vara Hybrid Azure AD-kopplade.
      - **Kräv godkänd klientapp**: Enheten måste använda godkända klientappar. 
      - **För flera kontroller**: Välj **Kräv alla valda kontroller**. Alla krav ovan tillämpas när en enhet försöker få åtkomst till appen.
    
      ![Bevilja inställningar för åtkomstkontroller](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. Under **Aktivera princip** väljer du **På**.
     
     ![Aktivera principen](media/create-conditional-access-intune/enable-policy.png)

12. Välj **Skapa**.

## <a name="see-also"></a>Se även
[Appbaserad villkorlig åtkomst med Intune](app-based-conditional-access-intune.md)

[Felsöka villkorlig åtkomst för Intune](https://support.microsoft.com/help/4456106)
