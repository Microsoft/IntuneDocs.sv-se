---
title: Registrera en Android-enhet med Intune-företagsportalen | Microsoft Docs
description: Beskriver hur du registrerar en Android-enhet med Intune-företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/31/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: e0a2297509d6077d6508adaab96ae6eb3cf9b28f
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75856742"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrera din enhet med företagsportalen  
Registrera din personliga eller företagsägda Android-enhet för att få säker åtkomst till företagets e-post, appar och data. Företagsportalen har stöd för Android-enheter, däribland Samsung Knox, som kör Android 4.4 och senare.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox är en typ av säkerhet som vissa Samsung-enheter använder för ytterligare skydd utöver vad den interna säkerheten i Android ger. Du kan kontrollera om du har en Samsung Knox-enhet genom att gå till **Inställningar** > **Om enheten**. Om du inte ser **Knox version** där har du en ursprunglig Android-enhet.

## <a name="enroll-device"></a>Registrera enhet  
Se till att [installera den kostnadsfria Intune-företagsportalsappen från Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Under registreringen kan du bli ombedd att välja en kategori som bäst beskriver hur du använder enheten. Företagets support använder ditt svar för att se vilka appar du har åtkomst till.  

1. Öppna företagsportalappen och logga in med ditt arbets- eller skolkonto.  

2. Om du uppmanas att godkänna din organisations villkor trycker du på **GODKÄNN ALLT**.  

   ![Exempel bild på skärmen Företagsportal, villkor, som markerar knappen "acceptera alla".](./media/accept-terms-1911.png)  


3. Granska vad din organisation kan och inte kan se. Tryck sedan på **FORTSÄTT**.


    ![Exempel bild av Företagsportal, vi värnar om din integritets skärm och markerar knappen Fortsätt.](./media/android-privacy-screen-1911.png)  
4. Granska vad du förväntar dig i de kommande stegen. Tryck sedan på **Nästa**.  

    ![Exempel bild av Företagsportal, vad är nästa skärm och markerar knappen Nästa.](./media/android-whats-next-1911.png)  


5. Beroende på din version av Android kan du bli uppmanad att tillåta åtkomst till vissa delar av enheten. Dessa meddelanden krävs av Google och inte styrs av Microsoft.  

    Tryck på **Tillåt** för följande behörigheter:  
    * **Tillåt företagsportal att skapa och hantera telefonsamtal**: med den här behörigheten kan enheten dela sitt internationella IMEI-nummer (Mobile Station Equipment Identity) med Intune, din organisations enhets hanterings leverantör. Det är säkert att tillåta den här behörigheten. Microsoft kommer aldrig att ringa eller hantera telefonsamtal.  
    * **Tillåt företagsportal åtkomst till dina kontakter**: med den här behörigheten kan företagsportal-appen skapa, använda och hantera ditt arbets konto.  Det är säkert att tillåta den här behörigheten. Microsoft kommer aldrig att få åtkomst till dina kontakter. 

    Om du nekar behörighet får du en uppmaning igen nästa gång du loggar in på Företagsportal. Om du vill stänga av de här meddelandena väljer du **Fråga inte igen**. Om du vill hantera app-behörigheter går du till inställningar appen > **appar** > **Företagsportal** > **behörigheter** > **telefon**.  

6. Aktivera appen enhets administratör. 

    Företagsportal behöver enhets administratörs behörighet för att hantera enheten på ett säkert sätt. Genom att aktivera appen kan din organisation identifiera möjliga säkerhets problem, till exempel upprepade misslyckade försök att låsa upp enheten och svara på lämpligt sätt.  

    ![Exempel bild på skärmen Aktivera enhets administratör och markera knappen Aktivera.](./media/activate-device-administrator-1911.png)  

> [!NOTE]
> Microsoft styr inte meddelande tjänsten på den här skärmen. Vi förstår att dess formuleringen kan verka något drastiskt. Företagsportal kan inte ange vilka begränsningar och åtkomst som är relevanta för din organisation. Kontakta din IT-support om du har frågor om hur din organisation använder appen. Gå till [Företagsportal-webbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980) och leta upp din organisations kontaktuppgifter.  


7. Enheten börjar registrera sig. Om du använder en Samsung KNOX-enhet uppmanas du först att granska och godkänna sekretess policyn för den andra.   

    ![Exempel bild av skärmen för Samsung KNOX sekretess policy som visas under registreringen.](./media/and-enroll-7-knox-privacy-policy.png)  

8. På skärmen **konfiguration av företags åtkomst** kontrollerar du att enheten har registrerats. Tryck sedan på **FORTSÄTT**.  

    ![Exempel bild av Företagsportal, skärmen konfiguration av företags åtkomst, som visar Hämta enhets hantering är slutfört.](./media/update-settings-1911.png)  

9. Din organisation kan kräva att du uppdaterar enhets inställningarna. Tryck på **Lös** för att justera en inställning. När du är klar med att uppdatera inställningarna trycker du på **Fortsätt**.  

   ![Exempel bild av Företagsportal, uppdatera enhets inställningar, markera lös och fortsätta knappar.](./media/resolve-settings-1911.png)  

10. När installationen är klar trycker du på **klar**.    

    ![Exempel bild av Företagsportal, skärmen konfiguration av företags åtkomst, som visar slutförd installation och markering klar.](./media/android-enrollment-done-1911.png) 

## <a name="next-steps"></a>Nästa steg  

Innan du försöker installera en skola eller en arbets app går du till **inställningar** > **säkerhet**och aktiverar **okända källor**. Om du inte aktiverar det här alternativet visas följande meddelande när du försöker att installera en app: ”Installationen blockerades. Av säkerhetsskäl är enheten inställd på att blockera installationer av appar från okända källor. Du kan trycka på **Inställningar** i meddelandet för att gå direkt till **okända källor**.  

> [!Note]
> Om din organisation använder kostnad hanteringsprogramvara för telekomtjänster måste ytterligare ett part steg utföras innan enheten har registrerats fullständigt. Läs mer [här](enroll-your-device-with-telecom-expense-management-android.md).

Om du får ett felmeddelande när du försöker registrera enheten i Intune kan du [skicka ett e-postmeddelande till företagets support](send-logs-to-your-it-admin-by-email-android.md).  

Behöver du fortfarande hjälp? Kontakta företagssupporten. Titta efter IT-administratörens kontaktuppgifter på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980).  