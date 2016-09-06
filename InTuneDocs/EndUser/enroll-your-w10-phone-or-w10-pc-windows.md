---
title: Registrera din Windows 10-enhet i Intune | Microsoft Intune
description: Beskriver hur du registrerar en Windows 10 Mobile- eller Windows 10-enhet i Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 06/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 02287eb01598c28906045fd8def9e8b4660e3da5
ms.openlocfilehash: 8806231f8d02885a192053a35559694a8984d2f5


---


# Registrera din Windows 10 Mobile- eller Windows 10-enhet i Intune

Om företaget eller skolan använder Microsoft Intune kan du registrera dina enheter så att de får tillgång till företagets e-post, filer och andra resurser. Genom att registrera dina enheter kan organisationen skydda företagsdata. Mer information om registrering finns i [Vad händer om man installerar företagsportalappen och registrerar enheten i Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) och [Vad IT-administratören kan se och inte kan se på enheten](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md).


Registrera din Windows 10 Mobile- eller Windows 10-enhet:

1.  Gå till Windows **Inställningar** och tryck på **Konton**.

    ![settings-accounts](./media/w10-enroll-rs1-settings-accounts.png)

2.  Ta en titt på de två följande skärmarna och se om någon av dem liknar vad du ser på din enhet. Följ de steg som gäller för den skärm som du ser på din enhet.

    Om denna skärm visas följer du stegen i [Steg att följa om du ser Åtkomst för arbete eller skola](#steps-to-follow-if-you-see-access-work-or-school).

    ![connect-to-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Om denna skärm visas följer du stegen i [Steg att följa om du ser Ditt konto](#steps-to-follow-if-you-see-your-account).

    ![your-account](./media/w10-enroll-2-accounts-your-account.png)

## Steg för att följa om du ser Åtkomst för arbete eller skola

1.  Tryck på **Åtkomst för arbete eller skola**.

    ![tap-access-work-school-account](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2.  Ange din e-postadress på arbetet eller i skolan och tryck på **Nästa**.

    ![enter-your-work-or-school-account](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

3. Logga in på Intune med ditt arbets- eller skolkonto.

    ![add-work-school-account](./media/w10-enroll-rs1-enter-your-credentials.png)

    Ett meddelande visas som anger att ditt företag eller din skola registrerar din enhet.

4. När sidan **Allt är klart!** trycker du på **Stäng**. Klart.

  ![tap-close-on-you-are-all-set-screen](./media/w10-enroll-rs1-youre-all-set.png)

5. Om du vill kontrollera att anslutningen är korrekt går du tillbaka till **Inställningar**, och ser att ditt arbets- eller skolkonto listas.

    ![validate-that-connection-was-set-up-correctly](./media/w10-enroll-rs1-validate-successful-enrollment.png)

Om du har följt stegen ovan, men ändå inte får åtkomst till din e-post eller dina filer på arbetet eller i skolan, så följ anvisningarna i [Felsökningssteg att följa för Åtkomst för arbete eller skola](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).


## Steg för att följa för Ditt konto

1.  Gå till Windows **Inställningar** och tryck på **Konton**.

    ![go-to-settings-accounts](./media/W10-enroll-1-settings-accounts.png)

2.  Tryck på **Ditt konto**.

    ![tap-your-account](./media/W10-enroll-2-accounts-your-account.png)

3.  Tryck på **Lägg till ett arbetsplats- eller skolkonto**.

    ![add-work-or-school-account](./media/w10-enroll-3-add-work-school-acct.png)

4.  Logga in med dina uppgifter för arbets- eller skolkontot.

    ![sign-in](./media/W10-enroll-4-sign-in.png)

Om du har följt stegen ovan, men ändå inte får åtkomst till din e-post, dina filer eller annan information på arbetet eller i skolan, så följ anvisningarna i [Felsökningssteg att följa för Ditt konto](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).

Vi rekommenderar också att du installerar appen Företagsportalen som gör att du lätt kan identifiera och ladda ner de företagsappar som är relevanta för dig och din arbetsroll. Företagsportalen kan ha installerats som en del i din registrering, beroende på hur ditt företag har konfigurerat Intune. Du kan kontrollera att du har appen genom att se om **Företagsportalen** finns i din applista. Om du inte ser Företagsportalen i app-listan kan du följa de här stegen för att installera den.

1.  Tryck på **Start** &gt; **Store**.

2.  Tryck på **Sök** och skriv in **Företagsportalen**.

3.  Tryck på **Företagsportal** &gt; **Installera** i listan över resultat.

4.  Tryck på antingen **Installera** eller på **Ledigt**. Vilket alternativ som visas beror på hur ditt företag har konfigurerat appen.

Behöver du fortfarande hjälp? Kontakta IT-administratören. Titta efter kontaktuppgifter på [företagsportalens webbplats](http://portal.manage.microsoft.com).

### Se även
[Att använda din Windowsenhet med Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO3-->


