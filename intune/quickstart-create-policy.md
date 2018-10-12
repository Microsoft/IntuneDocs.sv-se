---
title: 'Snabbstart: Lägg till en enhetsefterlevnadsprincip för en Windows 10-enhet'
description: Använd den här snabbstarten för att skapa principer som skyddar företagsdata och hanterar de enheter som slutanvändarna använder för att få åtkomst till företagets resurser. Tilldela den principerna till grupper.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/21/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ac74ba5-7441-44ac-98b5-9d8bb8899747
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73e1e0a27d128d567a924e6f2b343026b11f1a44
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581786"
---
# <a name="quickstart-add-a-device-compliance-policy-for-a-windows-10-device"></a>Snabbstart: Lägg till en enhetsefterlevnadsprincip för en Windows 10-enhet
En efterlevnadsprincip i Intune för Windows-enheter anger de regler och inställningar som Windows-enheter måste uppfylla för att anses vara kompatibla. Du kan använda dessa principer med [villkorsstyrd åtkomst](https://docs.microsoft.com/intune/conditional-access) för att tillåta eller blockera åtkomst till företagets resurser. Du kan också få enhetsrapporter och vidta åtgärder för inkompatibilitet.

I den här snabbstarten får du skapa en enhetsefterlevnadsprincip för en Windows 10-enhet och sedan tilldela principen en enhetsgrupp.

Om du inte har en Intune-prenumeration [så registrera dig för ett kostnadsfritt utvärderingskonto](free-trial-sign-up.md).

## <a name="prerequisites"></a>Krav
- För att kunna slutföra den här snabbstarten måste du först [skapa en användare](quickstart-create-user.md) och [skapa en grupp](quickstart-create-group.md).


## <a name="sign-in-to-intune"></a>Logga in i Intune
Logga in på [Intune](https://aka.ms/intuneportal) som global administratör eller Intune-tjänstadministratör.

## <a name="create-a-device-compliance-policy"></a>Skapa en enhetsefterlevnadsprincip
1. Välj **Enhetsefterlevnad** > **Principer** > **Skapa princip**.
2. Ange **Windows 10-efterlevnad** i **Namn** och **Exempelefterlevnadsprincip för Windows 10** som **Beskrivning**.
3. Välj **Windows 10 och senare** som **Plattform**.
4. I **Inställningar** väljer du **Systemsäkerhet** och ställer sedan in **Kräv lösenord för att låsa upp mobila enheter** till **Kräv**. När du har konfigurerat klart principen väljer du **OK**.
   ![Efterlevnadsprincip](/intune/media/quickstart-create-policy/compliance-policy.png)
5. Stäng fönstret **Windows 10-efterlevnadsprincip**. 
6. Välj **Skapa** i fönstret **Skapa princip**. Det här steget skapar principen och listar den i **Efterlevnad för enhet** > **Principer**.
7. Markera den nya principen och välj **Tilldelningar**. Du kan inkludera eller exkludera säkerhetsgrupper i Azure Active Directory (AD).
8. Välj **Valda grupper** om du vill se dina befintliga Azure AD-säkerhetsgrupper. Välj först **Contoso-testare** och sedan **Spara** om du vill distribuera principen till användare i gruppen. Om du inte skapade den här gruppen i [Skapa en grupp](quickstart-create-group.md) kan du välja en grupp. 

## <a name="clean-up-resources"></a>Rensa resurser
Ta bort principen när du inte längre behöver den. Gör det genom att välja principen **Windows 10-efterlevnad** och klicka på **Ta bort**. 

## <a name="next-steps"></a>Nästa steg
I den här snabbstarten har du skapat och tilldelat en enkel enhetsefterlevnadsprincip. Om du vill registrera en Windows 10-enhet som ska ta emot principen fortsätter du till snabbstarten och konfigurerar automatisk registrering. 
 
> [!div class="nextstepaction"]
> [Konfigurera automatisk registrering](quickstart-setup-auto-enrollment.md)