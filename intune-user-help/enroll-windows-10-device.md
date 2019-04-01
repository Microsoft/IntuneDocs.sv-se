---
title: Registrera Windows 10-enhet i Intune-företagsportal | Microsoft Docs
description: Steg för att registrera Windows 10-enheter i Intune-Företagsportalen
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/11/2019
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
ms.openlocfilehash: 4eb5dbb150559de7ad30a598fb78a4fa78033c42
ms.sourcegitcommit: fdc6261f4ed695986e06d18353c10660a4735362
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2019
ms.locfileid: "58069371"
---
# <a name="enroll-windows-10-devices-with-intune-company-portal"></a>Registrera Windows 10-enheter med Intune-Företagsportalen

Använda Intune-Företagsportalen för att registrera Windows 10-enheten hanteras av din organisation. Den här artikeln beskriver hur du registrerar enheter med Windows 10 version 1607 och senare och Windows 10 version 1511 och tidigare. Innan du kan se till att du [Kontrollera versionen på din enhet](windows-enrollment-company-portal.md#find-windows-10-version-number) så att du kan följa rätt steg.  

Windows 10 stöds mellan olika typer av enheter, inklusive desktop, telefoner och surfplattor. Steg för registrering är desamma på den enhet som du använder. Skärmen kan dock se ut skiljer sig något från bilderna som visas i den här artikeln.  

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]  

## <a name="enroll-windows-10-version-1607-and-later-device"></a>Registrera Windows 10 version 1607 och senare enheter 
Dessa steg beskriver hur du registrerar en enhet som kör Windows 10, version 1607 och senare.  

1. Gå till **Start**. Om du har en Windows 10 Mobile-enhet kan fortsätta att den **alla appar** lista.

2. Öppna appen **Inställningar**. Om appen inte är tillgängliga i din applista, går du till sökfältet och Skriv ”inställningar”.

3. Välj **Konton** > **Åtkomst till arbete eller skola** > **Anslut**.  


    ![Välj kontot för arbete eller skola](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

4. Ange e-postadressen för arbetet eller skolan och välj **Nästa**.  


   ![Ange ditt arbetskonto eller skolkonto](./media/w10-enroll-rs1-set-up-work-or-school-account.png)  

5. Logga in på Intune med ditt arbetskonto eller skolkonto.  


    ![Lägg till ett arbetsplats- eller skolkonto](./media/w10-enroll-rs1-enter-your-credentials.png)  

    Så småningom visas ett meddelande om att ditt företag eller din skola registrerar din enhet.

6. Om din organisation kräver att du ställer in en PIN-kod för Windows Hello, uppmanas du att ange en Verifieringskod. Ange koden och fortsätta skapa den på skärmen för att skapa en PIN-kod.  

7. När sidan **Allt är klart!** visas väljer du **Klar**. Enheten har nu registrerats.  

8. Om du vill kontrollera din anslutning går du tillbaka till **inställningar** > **konton** > **åtkomst till arbete eller skola**.  Ditt konto bör nu visas.  


    ![Verifiera att anslutningen är korrekt konfigurerad](./media/w10-enroll-rs1-validate-successful-enrollment.png)  

Kan du fortfarande inte komma åt din e-post, dina filer eller andra data för skolan eller arbetet? Lär dig hur du [felsöka problem med kontot](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).  

## <a name="enroll-windows-10-version-1511-and-earlier-device"></a>Registrera Windows 10 version 1511 och tidigare enhet  
Dessa steg beskriver hur du registrerar en enhet som kör Windows 10, version 1511 och tidigare.  

1. Gå till **Start**. Om du har en Windows 10 Mobile-enhet kan fortsätta att den **alla appar** lista.

2. Öppna appen **Inställningar**. Om appen inte är tillgängliga i din applista, går du till sökfältet och Skriv ”inställningar”.

3. Välj **konton** > **ditt konto**.  


    ![Välj ditt konto](./media/W10-enroll-2-accounts-your-account.png)  

5. Välj **Lägg till ett arbetsplats- eller skolkonto**.  


    ![Välj lägga till ett arbetsplats- eller skolkonto](./media/w10-enroll-3-add-work-school-acct.png)  

6. Logga in med dina uppgifter för arbets- eller skolkontot.  


    ![Logga in](./media/W10-enroll-4-sign-in.png)  

Kan du fortfarande inte komma åt din e-post, dina filer eller andra data för skolan eller arbetet? Lär dig hur du [felsöka problem med kontot](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).   

## <a name="next-steps"></a>Nästa steg  

Kontakta företagets support om du behöver hjälp. Du kan hitta din organisations IT-informationen på den [företagsportalwebbplatsen](https://go.microsoft.com/fwlink/?linkid=2010980). Logga in på sidan med ditt arbets- eller skolkonto.  

 

