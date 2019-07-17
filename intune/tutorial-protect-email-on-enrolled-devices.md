---
title: Självstudie – Skydda e-post i Exchange Online på Intune-hanterade enheter
titleSuffix: Microsoft Intune
description: Lär dig att skydda Exchange Online med iOS-principer för Intune-efterlevnad och villkorlig åtkomst i Azure AD, som kräver att hanterade enheter och Outlook-appen används.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a5a355c82455e135319b7683756eb0ef5c032876
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882369"
---
# <a name="tutorial-protect-exchange-online-email-on-managed-devices"></a>Självstudie: Skydda e-post i Exchange Online på hanterade enheter
Lär dig att använda principer för enhetsefterlevnad med villkorlig åtkomst för att se till att iOS-enheter endast har åtkomst till e-post i Exchange Online om de hanteras med Intune och använder en godkänd e-postapp. 

I den här självstudien får du lära dig att: 
> [!div class="checklist"]
> * Skapa en efterlevnadsprincip för iOS-enheter i Intune som anger de villkor som en enhet måste uppfylla för att anses vara kompatibel.
> * Skapa en villkorlig åtkomstprincip för Azure Active Directory (Azure AD) som kräver att iOS-enheter registreras i Intune, att de är kompatibla med Intune-principer och att de använder den godkända Outlook-mobilappen för att få åtkomst till e-post i Exchange Online.

Om du inte har en Intune-prenumeration [kan du registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
- Du behöver en testklient med följande prenumerationer för den här självstudien:
  - Azure Active Directory Premium ([kostnadsfri utvärderingsversion](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
  - En Office 365 Business-prenumeration med Exchange ([kostnadsfri utvärderingsversion](https://go.microsoft.com/fwlink/p/?LinkID=510938))
- Innan du börjar måste du skapa en testenhetsprofil för iOS-enheter genom att följa stegen i [Snabbstart: Skapa en e-postenhetsprofil för iOS](quickstart-email-profile.md).

## <a name="sign-in-to-intune"></a>Logga in i Intune

Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör. Om du har skapat en prenumeration för en Intune-utvärdering, är det konto som du skapade prenumerationen med den globala administratören.

## <a name="create-the-ios-device-compliance-policy"></a>Skapa en efterlevnadsprincip för iOS-enheter
Konfigurera en efterlevnadsprincip för Intune-enheter som anger de villkor som en enhet måste uppfylla för att anses vara kompatibel. I den här självstudien skapar vi en enhetsefterlevnadsprincip för iOS-enheter. Efterlevnadsprinciper är plattformsspecifika, så du behöver ha en separat efterlevnadsprincip för varje enhetsplattform som du vill utvärdera.

1. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip** i Intune.
2. I **Namn** anger du **Test av iOS-efterlevnadsprincip**. 
3. I **Beskrivning** anger du **Test av iOS-efterlevnadsprincip**.
4. I **Plattform** väljer du **iOS**. 
5. Välj **Inställningar** > **E-post**. 
     
    1. Bredvid **Kräv att mobila enheter har en hanterad e-postprofil** väljer du **Kräv**.
    2. Välj **OK**.

    ![Ange att efterlevnadsprincipen för e-post ska kräva en hanterad e-postprofil](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-email.png)
    
6. Välj **Enhetens hälsotillstånd**. Bredvid **Jailbrokade enheter** väljer du **Blockera** och sedan **OK**.
7. Välj **Systemsäkerhet** och ange inställningar för **Lösenord**. Välj följande rekommenderade inställningar för den här självstudien:
     
    - I **Kräv ett lösenord för att låsa upp mobila enheter** väljer du **Kräv**.
    - I **Enkla lösenord** väljer du **Blockera**.
    - I **Minsta längd på lösenord** anger du **4**.
    - I **Krav på lösenordstyp** väljer du **Alfanumeriskt**.
    - I **Maximalt antal minuter efter skärmlås innan ett lösenord krävs** väljer du **Omedelbart**.
    - I **Lösenordets giltighetstid (dagar)** anger du **41**.
    - I **Antal tidigare lösenord för att förhindra återanvändning** anger du **5**.
 
    ![Ange lösenordsinställningar för e-postens efterlevnadsprincip](media/tutorial-protect-email-on-enrolled-devices/ios-compliance-policy-system-security.png)

8. Välj **OK** och sedan **OK** igen.
9. Välj **Skapa**.

## <a name="create-the-conditional-access-policy"></a>Skapa en princip för villkorlig åtkomst
Nu ska vi skapa en princip för villkorlig åtkomst som kräver att alla enhetsplattformar registreras i Intune och uppfyller vår efterlevnadsprincip för Intune innan de kan få åtkomst till Exchange Online. Vi kommer även kräva Outlook-appen för e-poståtkomst. Principer för villkorlig åtkomst kan konfigureras i Azure AD-portalen eller i Intune-portalen. Eftersom vi redan är i Intune-portalen, skapar vi principen här.
1. I Intune väljer du **Villkorlig åtkomst** > **Principer** > **Ny princip**.
1. I **Namn** anger du **Testprincip för e-post i Office 365**. 
3. Under **Tilldelningar** väljer du **Användare och grupper**. På fliken **Inkludera** väljer du **Alla användare** och sedan **Klar**.

4. Under **Tilldelningar** väljer du **Molnappar**. Eftersom vi vill skydda e-posten i Office 365 Exchange Online, väljer vi det genom att följa dessa steg:
     
    1. På fliken **Inkludera** väljer du **Välj appar**.
    2. Välj **Välj**. 
    3. I listan med program väljer du **Office 365 Exchange Online** och sedan **Välj**. 
    4. Välj **Klar**.
  
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-apps.png)

5. Under **Tilldelningar** väljer du **Villkor** > **Enhetsplattformar**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. På fliken **Inkludera**, väljer du **Alla enheter** och sedan **Klar**. 
    3. Välj **Klar** igen.
   
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-cloud-device-platforms.png)

6. Under **Tilldelningar** väljer du **Villkor** > **Klientappar**.
     
    1. Under **Konfigurera** väljer du **Ja**.
    2. För den här självstudien väljer du **Mobilappar och skrivbordsklienter** och **Moderna autentiseringsklienter** (som avser appar som Outlook för iOS och Outlook för Android). Avmarkera alla andra kryssrutor.
    3. Välj **Klar** och sedan **Klar** igen.
    
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-client-apps.png)

7. Under **Åtkomstkontroller** väljer du **Bevilja**. 
     
    1. I rutan **Bevilja** väljer du **Bevilja åtkomst**.
    2. Välj **Kräv att enheten är markerad som kompatibel**. 
    3. Välj **Kräv godkänd klientapp**.
    4. Under **För flera kontroller** väljer du **Kräv alla valda kontroller**. Den här inställningen garanterar att båda kraven som du har valt tillämpas när en enhet försöker få åtkomst till e-post.
    5. Välj **Välj**.
     
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-grant-access.png)

8. Under **Aktivera princip** väljer du **På**.
     
    ![Välj Office 365 Exchange Online-appen](media/tutorial-protect-email-on-enrolled-devices/ios-ca-policy-enable-policy.png)

9. Välj **Skapa**.

## <a name="try-it-out"></a>Prova nu
Enligt de principer som du har skapat kommer en iOS-enhet som försöker logga in på e-post i Office 365 behöva registreras i Intune och använda Outlook-mobilappen för iOS. Försök logga in på Exchange Online med autentiseringsuppgifter för en användare i testklienten för att testa det här scenariot på en iOS-enhet. Du uppmanas att registrera enheten och installera Outlook-mobilappen.
1. Om du vill testa på en iPhone går du till **Inställningar** > **Lösenord och konton** > **Lägg till konto** > **Exchange**.
2. Ange e-postadressen för en användare i testklienten och tryck sedan på **Nästa**.
3. Tryck på **Logga in**.
4. Ange testanvändarens lösenord och tryck på **Logga in**.
5. Ett meddelande visas om att din enhet måste hanteras för att få åtkomst till resursen, tillsammans med ett alternativ för att registrera den. 

## <a name="clean-up-resources"></a>Rensa resurser
När testprinciperna inte längre behövs kan du ta bort dem.
1. Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör.
2. Välj **Enhetsefterlevnad** > **Principer**.
3. I listan **Principnamn** väljer du snabbmenyn ( **...** ) för testprincipen och sedan **Ta bort**. Välj **Ja** för att bekräfta.
4. I Intune väljer du **Villkorsstyrd åtkomst** > **Principer**.
5. I listan **Principnamn** väljer du snabbmenyn ( **...** ) för testprincipen och sedan **Ta bort**. Välj **Ja** för att bekräfta.

## <a name="next-steps"></a>Nästa steg 
I den här självstudien skapade du principer som kräver att iOS-enheter registreras i Intune och använder Outlook-appen för att få åtkomst till e-post i Exchange Online. Mer information om att använda Intune med villkorlig åtkomst för att skydda andra appar och tjänster, inklusive Exchange ActiveSync-klienter för Office 365 Exchange Online, finns i [Konfigurera villkorlig åtkomst](conditional-access.md).
