---
title: Åtgärda konflikter mellan grupprincipobjekt och Intune-principer
titleSuffix: Microsoft Intune
description: Läs om hur du löser konflikter mellan Grupprincip och Intune-konfigurationsprinciper.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ebae39c529571c5f926debcf64b46d6399d770f
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67547942"
---
# <a name="resolve-group-policy-objects-gpo-and-microsoft-intune-policy-conflicts"></a>Lösa konflikter mellan grupprincipobjekt och Microsoft Intune-principer

[!INCLUDE [classic-portal](includes/classic-portal.md)]

> [!NOTE]
> Informationen i det här avsnittet gäller endast för stationära Windows-datorer som du hanterar som datorer med Intune-klientprogramvaran.

Intune använder principer som hjälper dig att hantera inställningarna på Windows PC-datorer. Du använder t.ex. en princip för att kontrollera PC-datorernas inställningar för Windows-brandväggen. Många Intune-inställningar påminner om de inställningar som du kan konfigurera med Grupprincip i Windows. Emellanåt kan det dock hända att de två metoderna hamnar i konflikt med varandra.

När sådana konflikter uppstår har grupprinciper på domännivå företräde framför Intune-principer, såvida PC-datorn inte kan logga in till domänen. I detta fall tillämpas Intune-principen på klientdatorn.

## <a name="what-to-do-if-you-are-using-group-policy"></a>Vad som krävs vid användning av grupprinciper
Kontrollera att de principer som du använder inte hanteras av någon grupprincip. Om du vill undvika konflikter kan du använda en eller flera av följande metoder:

- Flytta dina PC-datorer till en Active Directory-organisationsenhet som inte omfattas av några grupprincipinställningar innan du installerar Intune-klienten. Du kan också blockera arv av grupprinciper i organisationsenheter som innehåller PC-datorer som har registrerats i Intune och som du inte vill använda grupprincipinställningar för.

- Använd säkerhetsgruppfilter för att begränsa grupprincipobjekt till PC-datorer som inte hanteras av Intune.

- Inaktivera eller ta bort det grupprincipobjekt som står i konflikt med Intune-principerna.

Mer information om Active Directory och grupprinciper i Windows finns i Windows Server-dokumentationen.

## <a name="how-to-filter-existing-gpos-to-avoid-conflicts-with-intune-policy"></a>Så här filtrerar du befintliga grupprincipobjekt för att undvika konflikter med Intune-principer
Om du har identifierat grupprincipobjekt vars inställningar är i konflikt med Intune-principer kan du använda säkerhetsgruppfilter för att begränsa grupprincipobjekten till PC-datorer som inte hanteras av Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1. Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2. Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3. Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    - For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    - For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4. Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    - For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    - For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Du kan tillämpa grupprincipobjekt enbart på de säkerhetsgrupper som anges i området **Säkerhetsfiltrering** i konsolen Grupprinciphantering för ett utvalt grupprincipobjekt. Grupprincipobjekt gäller som standard för *autentiserade användare*.

- Skapa en ny säkerhetsgrupp i snapin-modulen **Active Directory - användare och datorer** som innehåller de datorer och användarkonton som du inte vill hantera med Intune. Du kan till exempel ge gruppen namnet *Inte i Microsoft Intune*.

- Högerklicka på den nya säkerhetsgruppen på fliken **Delegering** i konsolen Grupprinciphantering för det valda grupprincipobjektet och delegera lämpliga **Läs**- och **Tillämpa grupprincip**-behörigheter till både användare och datorer i säkerhetsgruppen. (Behörigheterna för**Tillämpa grupprincip** är tillgängliga i dialogrutan **Avancerat** .)

- Tillämpa sedan det nya säkerhetsgruppfiltret på ett utvalt grupprincipobjekt och ta bort standardfiltret **Autentiserade användare**.

Den nya säkerhetsgruppen måste underhållas när registreringen i Intune-tjänsten ändras.

### <a name="see-also"></a>Se även
[Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)
