---
title: Självstudie – Skydda e-post i Exchange Online på ohanterade enheter
titlesuffix: Microsoft Intune
description: Lär dig att skydda Office 365 Exchange Online med Intunes appskyddsprinciper och Azure AD:s villkorsstyrda åtkomst.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8339f91468abca548b3923df4d4380aabb88c5a8
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848720"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Självstudie: Skydda e-post i Exchange Online på ohanterade enheter

Lär dig att använda appskyddsprinciper med villkorsstyrd åtkomst för att skydda Exchange Online, även om enheterna inte är registrerade i en enhetshanteringslösning som exempelvis Intune. I den här självstudien får du lära dig att: 

> [!div class="checklist"]
> * Skapa en Intune-appskyddsprincip för Outlook-appen. Du kan begränsa hur användaren kan använda appdata genom att förhindra ”Spara som” och begränsa åtgärder för att klippa ut, kopiera och klistra in. 
> * Skapa principer för villkorsstyrd åtkomst i Azure Active Directory (Azure AD) som endast tillåter att Outlook-appen får åtkomst till företagets e-post i Exchange Online. Du kan också kräva multifaktorautentisering (MFA) för moderna autentiseringsklienter, till exempel Outlook för iOS och Android.

## <a name="prerequisites"></a>Krav
  - Du behöver en testklient med följande prenumerationer för den här självstudien:
    - Azure Active Directory Premium ([kostnadsfri utvärderingsversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Intune-prenumeration ([kostnadsfri utvärderingsversion](free-trial-sign-up.md))
    - En Office 365 Business-prenumeration med Exchange ([kostnadsfri utvärderingsversion](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör. Du hittar Intune i Azure Portal genom att välja **Alla tjänster** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Skapa appskyddsprincipen
I den här självstudien ska vi konfigurera en Intune-appskyddsprincip för Outlook-appen som skapar skydd på appnivå. Vi kommer att kräva en PIN-kod för att öppna appen i arbetssammanhang. Vi begränsar också datadelning mellan appar och förhindrar att företagets data sparas på en privat plats.

1.  I Intune väljer du **Klientappar** > **Principer för appskydd** > **Lägg till en princip**.
2.  I **Namn** anger du **Principtest för Outlook-app**.
3.  I **Beskrivning** anger du **Principtest för Outlook-app**.
4.  Välj **Appar**. I applistan väljer du **Outlook** och sedan **Välj**.
5.  Välj **Inställningar**. 
6.  Under **Dataflytt** väljer du i den här självstudien följande inställningar:

    - I **Tillåt att appen överför information till andra appar** väljer du **Ingen**.
    - I **Tillåt att appen tar emot information från andra appar** väljer du **Ingen**.
    - I **Förhindra ”Spara som”** väljer du **Ja**.
    - I **Begränsa klipp ut, kopiera och klistra in med andra appar** väljer du **Blockerad**.
   
     ![Välj dataflyttinställningar för Outlook-appens skyddsprincip](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  Under **Åtkomståtgärder** väljer du i den här självstudien följande inställningar:

    - I **Kräv PIN-kod för åtkomst** väljer du **Ja**.
    - I **Kräv företagets autentiseringsuppgifter för åtkomst** väljer du **Ja**.
    - Låt alla andra inställningar behålla sina standardvärden.
 
     ![Välj åtkomståtgärder för Outlook-appens skyddsprincip](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Välj **OK**.
10. Välj **Skapa**.

Appskyddsprincipen för Outlook skapas. Du kan nu konfigurera villkorsstyrd åtkomst som kräver att enheterna ska använda Outlook-appen.

## <a name="create-conditional-access-policies"></a>Skapa principer för villkorsstyrd åtkomst
Nu ska vi skapa två principer för villkorsstyrd åtkomst som gäller för alla enhetsplattformar. Den första principen kräver moderna autentiseringsklienter, till exempel Outlook för iOS och Outlook för Android, för att den godkända Outlook-appen och MFA ska kunna användas. Den andra principen kräver Exchange ActiveSync-klienter som använder den godkända Outlook-appen. (För närvarande stöder Exchange Active Sync inte andra villkor än enhetsplattform). Du kan konfigurera principer för villkorsstyrd åtkomst i Azure AD-portalen eller i Intune-portalen. Eftersom vi redan är i Intune-portalen, skapar vi principen här.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Skapa en MFA-princip för moderna autentiseringsklienter
1.  I Intune väljer du **Villkorsstyrd åtkomst** > **Principer** > **Ny princip**.
1.  I **Namn** anger du **Testprincip för moderna autentiseringsklienter**. 
3.  Under **Tilldelningar** väljer du **Användare och grupper**. På fliken **Inkludera** väljer du **Alla användare** och sedan **Klar**.

4.  Under **Tilldelningar** väljer du **Molnappar**. Eftersom vi vill skydda e-posten i Office 365 Exchange Online, väljer vi det genom att följa dessa steg:
     
    1. På fliken **Inkludera** väljer du **Välj appar**.
    2. Välj **Välj**. 
    3. I listan med program väljer du **Office 365 Exchange Online** och sedan **Välj**. 
    4. Välj **Klar**.
  
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  Under **Tilldelningar** väljer du **Villkor** > **Enhetsplattformar**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. På fliken **Inkludera** väljer du **Alla plattformar (inklusive de som inte stöds)**. 
    3. Välj **Klar**.
   
6.  Välj **Klientappar** i fönstret **Villkor**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. Välj **Mobilappar och skrivbordsklienter** och **Moderna autentiseringsklienter**.
    3. Avmarkera alla andra kryssrutor.
    4. Välj **Klar** och sedan **Klar** igen.
    
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  Under **Åtkomstkontroller** väljer du **Bevilja**. 
     
    1. I rutan **Bevilja** väljer du **Bevilja åtkomst**.
    2. Välj **Kräv multifaktorautentisering**.
    4. Välj **Kräv godkänd klientapp**.
    5. Under **För flera kontroller** väljer du **Kräv alla valda kontroller**. Den här inställningen garanterar att båda kraven som du har valt tillämpas när en enhet försöker få åtkomst till e-post.
    6. Välj **Välj**.
     
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  Under **Aktivera princip** väljer du **På**.
     
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Välj **Skapa**.

Principen för villkorsstyrd åtkomst för moderna autentiseringsklienter skapas. Nu kan du skapa en princip för Exchange Active Sync-klienter.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Skapa en princip för Exchange Active Sync-klienter
1.  I Intune väljer du **Villkorsstyrd åtkomst** > **Principer** > **Ny princip**.
2.  I **Namn** anger du **Testprincip för EAS-klienter**. 
3.  Under **Tilldelningar** väljer du **Användare och grupper**. På fliken **Inkludera** väljer du **Alla användare** och sedan **Klar**.

4.  Under **Tilldelningar** väljer du **Molnappar**. Välj ett e-postmeddelande i Office 365 Exchange Online med följande steg:
     
    1. På fliken **Inkludera** väljer du **Välj appar**.
    2. Välj **Välj**. 
    3. I listan med program väljer du **Office 365 Exchange Online** och sedan **Välj**. 
    4. Välj **Klar**.

5.  Under **Tilldelningar** väljer du **Villkor** > **Enhetsplattformar**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. På fliken **Inkludera** väljer du **Alla plattformar (inklusive de som inte stöds)** och sedan **Klar**. 
    3. Välj **Klar** igen.

6.  Välj **Klientappar** i fönstret **Villkor**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. Välj **Mobila appar och skrivbordsklienter**.
    3. Välj **Exchange ActiveSync-klienter** och **Tillämpa bara principen på plattformar som stöds**. 
    4. Avmarkera alla andra kryssrutor.
    5. Välj **Klar** och sedan **Klar** igen.
    
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  Under **Åtkomstkontroller** väljer du **Bevilja**. 
     
    1. I rutan **Bevilja** väljer du **Bevilja åtkomst**.
    4. Välj **Kräv godkänd klientapp**. Avmarkera alla andra kryssrutor.
    6. Välj **Välj**.
     
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  Under **Aktivera princip** väljer du **På**.

9.  Välj **Skapa**.

Dina appskyddsprinciper och din villkorsstyrda åtkomst är nu på plats och är redo för att testas. 

## <a name="try-it-out"></a>Prova nu
Med de principer som du har skapat måste enheter registreras i Intune och använda Outlook-mobilappen för att få åtkomst till e-post i Office 365. Försök logga in på Exchange Online med autentiseringsuppgifter för en användare i testklienten för att testa det här scenariot på en iOS-enhet.
1. Om du vill testa på en iPhone går du till **Inställningar** > **Lösenord och konton** > **Lägg till konto** > **Exchange**.
2. Ange e-postadressen för en användare i testklienten och tryck sedan på **Nästa**.
3. Tryck på **Logga in**.
4. Ange testanvändarens lösenord och tryck på **Logga in**.
5. Meddelandet **Mer information krävs** visas, vilket innebär att du uppmanas att konfigurera MFA. Gå vidare och konfigurera en extra verifieringsmetod.
6. Därefter visas ett meddelande om att du försöker öppna den här resursen med en app som inte har godkänts av din IT-avdelning. Det innebär att du är blockerad från att använda den interna e-postappen. Avbryt inloggningen.
7.  Öppna Outlook-appen och välj **Inställningar** > **Lägg till konto** > **Lägg till e-postkonto**.
8. Ange e-postadressen för en användare i testklienten och tryck sedan på **Nästa**.
9. Tryck på **Logga in med Office 365**. Du uppmanas till ytterligare autentisering och registrering. När du har loggat in kan du testa åtgärder som klipp ut, kopiera, klistra in och ”Spara som”.

## <a name="clean-up-resources"></a>Rensa resurser
När testprinciperna inte längre behövs kan du ta bort dem.
1. Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör.
2. Välj **Enhetsefterlevnad** > **Principer**.
3. I listan **Principnamn** väljer du snabbmenyn (**...**) för testprincipen och sedan **Ta bort**. Välj **Ja** för att bekräfta.
4. I Intune väljer du **Villkorsstyrd åtkomst** > **Principer**.
5. I listan **Principnamn** väljer du snabbmenyn (**...**) för varje testprincip och sedan **Ta bort**. Välj **Ja** för att bekräfta.

 ## <a name="next-steps"></a>Nästa steg 
I den här självstudien har du skapat appskyddsprinciper som begränsar vad användaren kan göra med Outlook-appen. Du har även skapat principer för villkorsstyrd åtkomst som kräver att Outlook-appen och MFA för moderna autentiseringsklienter används. Läs om hur du använder Intune med villkorsstyrd åtkomst för att skydda andra appar och tjänster i [Konfigurera villkorsstyrd åtkomst](conditional-access.md).
