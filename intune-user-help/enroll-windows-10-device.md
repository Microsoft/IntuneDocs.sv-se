---
title: Registrera Windows 10-enhet i Intune-företagsportalen| Microsoft Docs
description: Steg för att registrera Windows 10-enheter i Intune-företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/21/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 812e82df-76df-402b-bfe9-29302838f40e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbb6c3b771ae768fe45bea1eecb21f7083003010
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196853"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Registrera Windows 10-enheter med Intune-företagsportalen

Använd Intune-företagsportalen för att registrera den Windows 10-enhet som hanteras av din organisation. I den här artikeln beskrivs hur du registrerar enheter med Windows 10 version 1607 och senare samt Windows 10 version 1511 och tidigare. Innan du börjar bör du [kontrollera versionen på din enhet](windows-enrollment-company-portal.md#find-windows-10-version-number) så att du kan följa rätt steg.  

Windows 10 stöds på olika typer av enheter såsom stationära datorer, telefoner och surfplattor. Registreringsstegen är desamma oavsett vilken enhet du använder. Dock kan skärmen se lite olika ut jämfört med bilderna i den här artikeln.  
</br>
> [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Registrera enhet med Windows 10 version 1607 och senare 
Dessa steg beskriver hur du registrerar en enhet som kör Windows 10 version 1607 och senare.  

1. Gå till **Start**. Om du har en Windows 10 Mobile-enhet fortsätter du till listan **Alla appar**.

2. Öppna appen **Inställningar**. Om appen inte är tillgänglig applistan går du till sökfältet och skriver ”inställningar”.

3. Välj **Konton** > **Åtkomst till arbete eller skola** > **Anslut**.  


    ![Välj kontot för arbete eller skola](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Ange e-postadressen för arbetet eller skolan och välj **Nästa**.  


   ![Ange ditt arbetskonto eller skolkonto](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Logga in på Intune med ditt arbetskonto eller skolkonto.  


    ![Lägg till ett arbetsplats- eller skolkonto](./media/w10-enroll-rs1-enter-your-credentials.png)  

    Så småningom visas ett meddelande om att ditt företag eller din skola registrerar din enhet.

6. Om din organisation kräver att du konfigurerar en PIN-kod för Windows Hello uppmanas du att ange en verifieringskod. Ange koden och fortsätt med stegen på skärmen för att skapa en PIN-kod.  

7. När sidan **Allt är klart!** visas väljer du **Klar**. Enheten har nu registrerats.  

8. Dubbelkolla anslutningen genom att gå tillbaka till **Inställningar** > **Konton** > **Åtkomst till arbete eller skola**.  Ditt konto bör nu visas.  


    ![Verifiera att anslutningen är korrekt konfigurerad](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Kan du fortfarande inte komma åt din e-post, dina filer eller andra data för skolan eller arbetet? Lär dig hur du [felsöker kontoproblem](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Registrera enhet med Windows 10 version 1511 och tidigare  
Dessa steg beskriver hur du registrerar en enhet som kör Windows 10 version 1511 och tidigare.  

1. Gå till **Start**. Om du har en Windows 10 Mobile-enhet fortsätter du till listan **Alla appar**.

2. Öppna appen **Inställningar**. Om appen inte är tillgänglig applistan går du till sökfältet och skriver ”inställningar”.

3. Välj **Konton** > **Ditt konto**.  


    ![Välj ditt konto](./media/W10-enroll-2-accounts-your-account.png)  

5. Välj **Lägg till ett arbetsplats- eller skolkonto**.  


    ![Välj lägga till ett arbetsplats- eller skolkonto](./media/w10-enroll-3-add-work-school-acct.png)  

6. Logga in med dina uppgifter för arbets- eller skolkontot.  


    ![Logga in](./media/W10-enroll-4-sign-in.png)  

Kan du fortfarande inte komma åt din e-post, dina filer eller andra data för skolan eller arbetet? Lär dig hur du [felsöker kontorelaterade problem](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account) under registreringen.  

## <a name="it-administrator-support"></a>IT-administratörssupport   

Om du är IT-administratör och stöter på problem när du registrerar enheter kan du läsa [Felsöka problem med registrering av Windows-enhet i Microsoft Intune](https://support.microsoft.com/help/4469913). Den här artikeln innehåller vanliga fel, deras orsaker och stegen för att lösa dem. 

## <a name="next-steps"></a>Nästa steg  
Om du behöver hjälp med företagsportalen eller registrering kontaktar du din organisations IT-supportteam. Du hittar deras kontaktinformation på [företagsportalens webbplats](https://go.microsoft.com/fwlink/?linkid=2010980). Logga in på sidan med ditt arbets- eller skolkonto.  

 

