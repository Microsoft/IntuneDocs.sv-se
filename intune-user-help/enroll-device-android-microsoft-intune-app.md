---
title: Registrera företagsenhet med Microsoft Intune-appen | Microsoft Docs
description: Beskriver hur du registrerar en Android-företagsenhet i Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7e68e404a91927192f1006626d1b865acd5eb589
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197054"
---
# <a name="enroll-your-corporate-device-with-the-microsoft-intune-app"></a>Registrera din företagsenhet med Microsoft Intune-appen

Registrera din företagsägda Android-enhet för att få säker åtkomst till företagets e-post, appar och andra data som organisationen gör tillgängliga. Microsoft Intune-appen har stöd för företagsägda enheter som kör Android 6.0 och senare. Den installeras automatiskt på nya och fabriksåterställda enheter under registreringen. 

Det finns fyra sätt att registrera. Din organisation bör informera dig om vilket alternativ som ska användas.
 
* NFC (Near Field Communication)  
* Token  
* QR-kod   
* Google Zero Touch  

## <a name="enroll-device"></a>Registrera enhet 
Slutför dessa steg för att konfigurera och registrera din enhet.  

> [!NOTE]
> Android-versionen eller enhetstillverkaren kräver kanske att du slututför ytterligare steg som inte omfattas i den här proceduren. De färger och text som visas på skärmbilderna kan också se annorlunda på din enhet.  

1. Aktivera din nya eller fabriksåterställda enhet.  
2. Välj språk på **välkomstskärmen**.   Om du har fått instruktioner om att registrera med en QR-kod eller NFC följer du de nedanstående steg som matchar metoden.  
     * NFC: Vidrör en programmeringsenhet med din NFC-stödda enhet för att ansluta till organisationens nätverk. Följ uppmaningarna på skärmen. När du når skärmen för användningsvillkoren för Chrome fortsätter du till steg 5.  

      * QR-kod: Slutför stegen i [QR-kodsregistrering](#qr-code-enrollment).  

      Om du har fått instruktioner om att använda en annan metod fortsätter du till steg 3.    

1. Anslut till Wi-Fi och tryck på **NÄSTA**. Följ de steg som matchar din registreringsmetod. 

    * Token: När du kommer till inloggningssidan för Google slutför du stegen i [Tokenregistrering](#token-enrollment).    
    * Google Zero Touch: När du har anslutit till Wi-Fi identifieras enheten av din organisation. Fortsätt till steg 4 och följ anvisningarna på skärmen tills installationen är klar.    
 
       ![Exempelbild på skärmen med villkor för Google som visas om du använder Google Zero Touch, med knappen Godkänn och fortsätt markerad.](./media/google-zero-touch-intune-app-01.png)   
   
4. Granska villkoren för Google. Tryck sedan på **GODKÄNN OCH FORTSÄTT**.  

      ![Exempelbild på skärmen för Google-villkor med knappen Godkänn och fortsätt markerad.](./media/fully-managed-intune-app-04.png)   

6. Granska användningsvillkoren för Chrome. Tryck sedan på **GODKÄNN OCH FORTSÄTT**.  

   ![Exempelbild på skärmen för Chrome-användningsvillkor med knappen Godkänn och fortsätt markerad.](./media/fully-managed-intune-app-06.png)   

7. På inloggningsskärmen loggar du in med ditt arbets- eller skolkonto.   

    a. Ange din e-postadress och tryck på **Nästa**.      
    b. Ange lösenordet och tryck på **Logga in**.  

8. Beroende på din organisations krav kan du uppmanas att uppdatera inställningar såsom skärmlås eller kryptering. Om du ser de här uppmaningarna trycker du på **KONFIGURERA** och följer instruktionerna på skärmen.  

   ![Exempelbild på Konfigurera på arbetstelefonskärmen med knappen Konfigurera markerad.](./media/fully-managed-intune-app-10.png)   

9. För att installera arbetsappar på enheten trycker du på **INSTALLERA**. När installationen är klar trycker du på **NÄSTA**.  

   ![Exempelbild på Konfigurera på arbetstelefonskärmen med knappen Installera markerad.](./media/fully-managed-intune-app-11.png)   

10. När du får meddelandet att din enhet är klar trycker du på **KLAR**. 

11. Gå till dina appar och öppna Microsoft Intune-appen. Välj **LOGGA IN**. 

12. På skärmen **Konfigurera åtkomst** visas en lista över väntande uppgifter. Tryck på **FORTSÄTT**.  

       ![Exempelbild på Microsoft Intune-appen med skärmen Konfigurera åtkomst, som visar väntande uppgifter.](./media/fully-managed-intune-app-14.png)   

13. När enhetsregistreringen är klar trycker du på **FORTSÄTT**. Microsoft Intune uppmanar dig kanske att uppdatera ytterligare enhetsinställningar.   

       ![Exempelbild på Microsoft Intune appen med skärmen Uppdatera enhetsinställningar.](./media/fully-managed-intune-app-15-2.png)   

14. Installationen är klar när alla objekt i listan visas med en grön cirkel. Nu kan du komma åt företagsresurser.  

       ![Exempelbild på Microsoft Intune-appen med skärmen Konfigurera åtkomst, som visar slutförda uppgifter.](./media/fully-managed-intune-app-16.png)   


## <a name="qr-code-enrollment"></a>QR-kodsregistrering  
I det här avsnittet skannar du den QR-kod som du fått av företaget.  När du är klar omdirigeras du tillbaka till stegen för enhetsregistrering.     
  
1. På sidan **Välkommen** trycker du på skärmen fem gånger för att starta QR-kodskonfiguration.  

   ![Exempelbild på välkomstskärmen för enhetskonfiguration med instruktioner att trycka på skärmen markerade.](./media/qr-code-intune-app-01.png)  

2. Följ alla anvisningar på skärmen för att ansluta till Wi-Fi.  
3. Om enheten inte har en QR-kodsläsare visar installationsskärmarna förloppet när en skanner installeras. Vänta tills installationen är klar.  
4. När du uppmanas skannar du registreringsprofilens QR-kod som du fått av din organisation.  
5. Gå tillbaka till steg 4 i [Registrera enhet](#enroll-device) för att fortsätta med installationen.  

## <a name="token-enrollment"></a>Tokenregistrering  
I det här avsnittet anger du den token som du fått av företaget. När du är klar omdirigeras du tillbaka till stegen för enhetsregistrering.  

1. På skärmen för Google-inloggning går du till rutan **E-post eller telefon** och skriver **afw#setup**. Tryck på **nästa**. 

   ![Exempelbild på Google-inloggningsskärmen som visar att ”afw#setup” skrivs in i fältet.](./media/token-intune-app-01.png)   

2. Välj **Installera** för appen **Android Device Policy**. Fortsätt att gå igenom installationen. Beroende på din enhet kan du behöva granska och godkänna ytterligare villkor.    

3. På skärmen **Registrera den här enheten** väljer du **Nästa**.  

   ![Exempelbild på skärmen Registrera den här enheten. Visar en bild på en QR-kod med knappen Nästa markerad.](./media/token-intune-app-02.png)  

4. Välj **Ange kod**.

   ![Exempelskärmbild på en aktiv QD-kodsläsare. Markerar knappen Ange kod.](./media/token-intune-app-03.png)  

5. På skärmen **Skanna eller ange kod** skriver du in den kod som du har fått av din organisation.  Klicka sedan på **Nästa**.  

   ![Exempelbild på skärmen Skanna eller ange kod med knappen Nästa markerad.](./media/token-intune-app-04.png)  

6. Gå tillbaka till steg 4 i [Registrera enhet](#enroll-device) för att fortsätta med installationen.  



## <a name="next-steps"></a>Nästa steg   
Behöver du fortfarande hjälp? Kontakta företagets support (du hittar kontaktinformation på [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980)) eller skriv till <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android-teamet</a>.  
