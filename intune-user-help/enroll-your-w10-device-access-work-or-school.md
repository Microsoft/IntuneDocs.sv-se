---
title: Registrera din Windows 10-enhet i Intune | Microsoft Docs
description: Registrera en Windows 10 1607 eller senare enhet i Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/22/2017
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
ms.openlocfilehash: fee90ed055a0d132a4f6304d7b33f67005caf0fc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-your-windows-10-device-in-intune"></a>Registrera din Windows 10-enhet i Intune

> [!NOTE]
> Windows 10 fungerar med alla typer av enheter. Du följer samma steg på datorn, mobiltelefonen eller surfplattan – även om de kan skilja sig något från bilderna på den här sidan.

> [!VIDEO https://channel9.msdn.com/Series/IntuneEnrollment/Windows-Enrollment/player]

1. Gå till **Start**.

   - Om du arbetar på en **Windows 10 Desktop**-enhet går du till **Start-menyn**.
   - Om du arbetar på en **Windows 10 Mobile**-enhet går du till **Startskärmen** och sveper till listan **Alla appar**.

2. Öppna appen **Inställningar** i Windows genom att söka efter ”inställningar” i sökfältet.

3. Välj **Konton** > **Åtkomst till arbete eller skola** > **Anslut**.

    ![Välj kontot för arbete eller skola](./media/w10-enroll-rs1-connect-to-work-or-school.png)

4. Ange e-postadressen för arbetet eller skolan och välj **Nästa**.

   ![Ange ditt arbetskonto eller skolkonto](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

5. Logga in på Intune med ditt arbetskonto eller skolkonto.

    ![Lägg till ett arbetsplats- eller skolkonto](./media/w10-enroll-rs1-enter-your-credentials.png)

    Ett meddelande visas som anger att ditt företag eller din skola registrerar din enhet.

6. När sidan **Allt är klart!** visas väljer du **Stäng**. Klart.

   ![Välj Stäng på sidan Allt är klart! skärmen](./media/w10-enroll-rs1-youre-all-set.png)

7. Om du vill kontrollera att anslutningen är korrekt går du tillbaka till **Inställningar**, där ditt arbets- eller skolkonto nu ska visas.

    ![Verifiera att anslutningen är korrekt konfigurerad](./media/w10-enroll-rs1-validate-successful-enrollment.png)

Om du har följt de föregående stegen, men ändå inte kan komma åt din e-post eller dina filer på arbetet eller i skolan, kan du följa anvisningarna i [Felsökningssteg att följa för Åtkomst för arbete eller skola](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).
