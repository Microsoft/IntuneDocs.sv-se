---
title: Synkronisera Windows-enheten manuellt | Microsoft Intune
description: 
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2d7630d71505fadc22ab135ff0c8988b314793ad
ms.openlocfilehash: e0f18e4e1077f7843b4f8d8ea6d9e485f715bc3c


---


# Synkronisera Windows-enheten manuellt
Om installationen av appen tar för lång tid kan du testa att synkronisera Windows-enheten manuellt. Manuell synkronisering kan påskynda installationen.

Endast följande versioner stöds. Följ instruktionerna för din typ av enhet.

* [Windows 10 Mobil](#windows-10-mobile)
* [Windows 10 desktop](#windows-10-desktop)
* [Windows Phone 8.1](#windows-phone-8-1)


## Windows 10 Mobil
Så här synkroniserar du en Windows 10 Mobile-enhet manuellt för att påskynda en långsam appinstallation:

1. Gå till **Alla appar** > **Inställningar** > **Konton**.

    ![Välj konton på skärmen Inställningar](./media/win10m-sync-1-settings-accounts.png)

2. Tryck på **Åtkomst till arbetsplats**.

    ![Välj arbetsåtkomst som kontotyp](./media/win10m-sync-2-work-access.png)

3. Välj företagets namn under **Registrera dig för hantering av mobilenheter**.

    ![Välj företagsnamnet för enhetshantering](./media/win10m-sync-3-tap-comp-name.png)

4. Tryck på ikonen **Synkronisera**.

    ![Tryck på ikonen Synkronisera](./media/win10m-sync-4-tap-sync.png)

    Ett meddelande som anger att ditt konto synkroniseras visas längst upp på skärmen. Knappen **Synkronisera** är nedtonad tills synkroniseringen är klar.

## Windows 10 desktop
Det finns mer än en version av Windows 10, vilket innebär att det finns två uppsättningar steg. Om du är osäker på vilka steg du ska följa tittar du på skärmbilderna och följer de steg som liknar vad du ser på din enhet. 

1. Välj **Start**-knappen och sedan **Inställningar**.

    ![Startknappen](./media/win10pc-sync-1-start-button.png)

2. Välj **Konton** på sidan **Inställningar**.

    ![Välj konton på sidan Inställningar](./media/win10pc-sync-2-settings-accounts.png)

3. Ta en titt på följande två skärmar och se om någon av dem liknar den som visas på din enhet. Följ anvisningarna för den skärm som motsvarar den som visas på din enhet.

    Om du ser den här skärmen, som visar ”Åtkomst till arbete eller skola”, följer du anvisningarna i [Steg som du följer om du ser Åtkomst till arbete eller skola](#steps-to-follow-if-you-see-access-work-or-school).

    ![Steg som du följer om du ser Åtkomst till arbete eller skola](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Om du ser den här skärmen, som visar ”Åtkomst till arbete”, följer du stegen i [Steg som du följer om du ser Åtkomst till arbete](#steps-to-follow-if-you-see-your-account).

    ![Välj arbetsåtkomst som kontotyp](./media/win10pc-sync-3-work-access.png) 

### Steg för att följa om du ser Åtkomst för arbete eller skola

1. Välj **Åtkomst till arbete eller skola** på sidan **Konton**.

    ![Välj Åtkomst till arbete eller skola](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. Välj ditt arbets- eller skolkonto. Beroende på hur IT-administratören har konfigurerat inställningarna kanske du ser två konton som liknar de i exemplet nedan. Ett konto visas med en portfölj och det andra med Microsoft-logotypen. 

    - Om du ser kontot med portföljen väljer du det och letar efter knappen **Information** under kontot. 
    - Om du bara ser kontot med Microsoft-logotypen väljer du kontot och letar efter knappen **Information** under kontot.

    ![Välj namnet på ditt konto bredvid portföljikonen eller Microsoft-logotypen](./media/win10pc-rs1-sync-info-button.png)

3. Välj knappen **Information**. En dialogruta öppnas som liknar den i exemplet nedan.

    ![Välj namnet på ditt konto bredvid portföljikonen eller Microsoft-logotypen](./media/win10pc-rs1-sync-button.png)

4. Välj knappen **Synkronisera**. Enheten kommer att synkroniseras med Intune.

### Steg som du följer om du ser Åtkomst till arbete
    
1. Välj **Åtkomst till arbetsplats** på sidan **Konton**.

    ![Välj arbetsåtkomst som kontotyp](./media/win10pc-sync-3-work-access.png)

2. Under avsnittet **Registrera dig för hantering av mobilenheter (MDM)** väljer du namnet på ditt företag.

    ![Välj företagsnamnet för enhetshantering](./media/win10pc-sync-4-tap-com-name.png)

3. Välj knappen **Synkronisera**.

    ![Välj knappen Synkronisera](./media/win10pc-sync-5-tap-sync.png)

   Knappen är nedtonad tills synkroniseringen är färdig.

## Windows Phone 8.1
Så här synkroniserar du en Windows Phone 8.1-enhet manuellt för att påskynda en långsam appinstallation:

1. Gå till **Alla appar** > **Inställningar** > **arbetsplats**.

    ![Lista över inställningar](./media/wp81-1-sync-settings-workplace.png)

2. Välj namnet på ditt företag.

    ![Välj företagsnamnet för arbetsplatskontot](./media/wp81-2-sync-tap-compname.png)

3. Tryck på ikonen **Synkronisera**.

    ![Tryck på ikonen Synkronisera](./media/wp81-3-sync-tap-sync-button.png)

   Ett meddelande som anger att ditt konto synkroniseras visas längst upp på skärmen tills synkroniseringen är klar.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).



<!--HONumber=Oct16_HO3-->


