---
title: Efterlevnadsprincip för Jamf-enheter
titleSuffix: Microsoft Intune
description: Använd Microsoft Intunes efterlevnadsprinciper med Azure Active Directorys villkorliga åtkomst för att skydda Jamf-hanterade enheter.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3552eca925865eb3278b50490a6b70ee5807e2b
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502447"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>Tvinga fram efterlevnad på Mac-datorer som hanteras med Jamf Pro

När du [integrerar Jamf Pro med Intune](conditional-access-integrate-jamf.md) kan du använda principer för villkorlig åtkomst för att kräva att dina Mac-enheter uppfyller kraven i din organisation.  I den här artikeln lär du dig att:  

- Skapa principer för villkorlig åtkomst.
- Konfigurera Jamf Pro för att distribuera Intune-företagsportalappen till enheter som du hanterar med Jamf.
- Konfigurera enheter så att de registreras i Azure AD när enhetsanvändaren loggar in i företagsportalappen via Jamf Self Service. Vid enhetsregistreringen upprättas en identitet i Azure AD som gör att enheten kan utvärderas av principer för villkorlig åtkomst för åtkomst till företagsresurser.  
 
Procedurerna i den här artikeln kräver åtkomst till både Intune- och Jamf Pro-konsolen.

## <a name="set-up-device-compliance-policies-in-intune"></a>Ställ in efterlevnadsprinciper för enheter i Intune

1. Logga in i [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) och gå till **Enhetsefterlevnad** > **Principer**. 
2. Om du använder en princip som du skapat tidigare väljer du den principen i konsolen och går sedan vidare till nästa steg i proceduren.  
   
   Välj **Skapa princip** och ange sedan information för en princip med *plattformen* **macOS**. Konfigurera *Inställningar* och *Åtgärder vid inkompatibilitet* enligt organisationens krav och spara principen genom att välja **Skapa**.

3. Välj **Tilldelningar** i fönstret *Översikt* för principerna. Använd de tillgängliga alternativen och välj vilka Azure AD-användare (Azure Active Directory) och säkerhetsgrupper som principen ska tillämpas på. Jamf-integreringen med Intune stöder inte efterlevnadsprinciper som tillämpas på enhetsgrupper. 

4. Principen distribueras till användarna när du väljer **Spara**.  

Principer som du distribuerar tillämpas på enheterna som används av de tilldelade användarna. Enheternas kompatibilitet kontrolleras. Kompatibla enheter markeras som kompatibla i inställningen *Kräv att enheten är markerad som kompatibel* i Azure AD.  

> [!NOTE]
> Intune kräver fullständig diskkryptering för att vara kompatibelt.

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>Distribuera företagsportalappen för macOS i Jamf Pro

Skapa en princip i Jamf Pro för att distribuera Intune-företagsportalen. Den här principen distribuerar företagsportalappen så att den är tillgänglig i Jamf Self Service. Skapa den här principen innan du skapar en princip i Jamf Pro som kräver att användare registrerar enheter i Azure AD.  

Stegen nedan kräver åtkomst till en macOS-enhet och till Jamf Pro-portalen. 

### <a name="to-deploy-the-company-portal-app"></a>Så här distribuerar du företagsportalappen  

1. På en macOS-enhet laddar du ned, men installerar inte, den aktuella versionen av [företagsportalappen för macOS](https://go.microsoft.com/fwlink/?linkid=862280). Du behöver bara en kopia av appen så att du kan ladda upp appen till Jamf Pro.  

2. Öppna Jamf Pro och gå till **Datorhantering** > **Paket**.

3. Skapa ett nytt paket med företagsportalappen för macOS och välj **Spara**.

4. Öppna **datorer** > **principer** och välj **ny**.

5. Använd nyttolasten **Allmänt** för att konfigurera inställningar för principen. Inställningarna bör vara:
   - Utlösare: välj **Registreringen är klar** och **Återkommande incheckning**
   - Körningsfrekvens: välj **En gång per dator**

6. Välj nyttolasten **paket** och klicka på **konfigurera**.

7. Klicka på **lägg till** för att välja paketet med företagsportalappen.

8. Välj **Installera** från popup-menyn **Åtgärd**.
9. Konfigurera inställningarna för paketet.

10. Välj fliken **Omfång** för att ange vilka datorer företagsportalappen ska installeras på. Välj **Spara**. Principen körs på enheter inom det angivna omfånget nästa gång den valda utlösaren aktiveras på datorn om villkoren i nyttolasten **Allmänt** är uppfyllda.

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>Skapa en princip i Jamf Pro för att få användarna att registrera sina enheter med Azure Active Directory  

När du har [distribuerat företagsportalappen](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) för macOS via Jamf Pro Self Service kan du skapa Jamf Pro-principen som registrerar en användares enhet i Azure AD. 

Enhetsregistreringen kräver att en enhetsanvändare manuellt väljer Intune-företagsportalappen i JAMF Self Service. [Kontakta slutanvändarna](../fundamentals/end-user-educate.md) via e-post, Jamf Pro-aviseringar eller en annan lämplig metod och be dem att utföra denna åtgärd så att deras enheter registreras. 

> [!WARNING]
> Enheten registreras inte om företagsportalappen startas manuellt (t.ex. från Program eller mappen Nedladdningar). Om en slutanvändare startar företagsportalen manuellt visas varningen **AccountNotOnboarded**.

### <a name="to-create-the-registration-policy"></a>Så här skapar du registreringsprincipen  

1. I Jamf Pro går du till **Datorer** > **Principer** och skapar sedan en ny princip för enhetsregistrering.

2. Konfigurera nyttolasten **Microsoft Intune-integrering**, inklusive utlösare och körningsfrekvens.

3. Välj fliken **Omfång** och välj sedan att principen ska tillämpas på alla målenheter.

4. Välj fliken **Självbetjäning** för att göra principen tillgänglig i Jamf Self Service. Inkludera principen i kategorin **enhetsefterlevnad**. Klicka på **Spara**.

## <a name="validate-intune-and-jamf-integration"></a>Validera Intune- och Jamf-integreringen  

Använd Jamf Pro-konsolen för att bekräfta att kommunikationen mellan Jamf Pro och Microsoft Intune fungerar. 

- I Jamf Pro går du till **Inställningar** > **Global hantering** > **Microsoft Intune-integrering** och väljer **Test**. 

    I konsolen visas ett meddelande som anger om anslutningen lyckades eller misslyckades.  

Kontrollera Jamf-konfigurationen om anslutningstestet från Jamf Pro-konsolen misslyckas. 


## <a name="removing-a-jamf-managed-device-from-intune"></a>Ta bort en Jamf-hanterad enhet från Intune

Du kan ta bort en Jamf-hanterad enhet från Intune-konsolen genom att välja **Ta bort** i vyn **Alla enheter**. Du kan aktivera massborttagning av enheter genom att välja flera enheter och klicka på **Ta bort**.

Få information om hur du [tar bort en Jamf-hanterad enhet i Jamf Pro-dokumenten](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information). Du kan även skicka in ett supportärende med [Jamf-support](https://www.jamf.com/support/) för ytterligare hjälp. 

## <a name="next-steps"></a>Nästa steg

- [Villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [Kom igång med villkorlig åtkomst i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
