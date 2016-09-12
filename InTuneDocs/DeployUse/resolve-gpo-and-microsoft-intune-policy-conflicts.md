---
title: "Lösa konflikter mellan grupprincipobjekt och Intune-principer | Microsoft Intune"
description: "Läs om hur du löser konflikter mellan Grupprincip och Intune-konfigurationsprinciper."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 70e5920679149791c4856a1db905e564dc1278bd


---

# Lösa konflikter mellan grupprincipobjekt och Microsoft Intune-principer
Intune använder principer som hjälper dig att hantera inställningarna på de Windows PC-datorer som du hanterar. Du kan t.ex. använda en princip för att kontrollera PC-datorernas inställningar för Windows-brandväggen. Många av Intunes inställningar påminner om inställningarna som du kan konfigurera med Grupprincip i Windows. Emellanåt kan det dock inträffa att de två metoderna hamnar i konflikt med varandra.

När sådana konflikter uppstår har grupprinciper på domännivå företräde framför Intune-principer, såvida PC-datorn inte kan logga in till domänen. I detta fall tillämpas Intune-principen på klientdatorn.

## Vad som krävs vid användning av grupprinciper
Kontrollera att ingen av de principer som du använder hanteras av någon grupprincip. Om du vill undvika konflikter bör du använda en eller flera av följande metoder:

-   Flytta dina PC-datorer till en Active Directory-organisationsenhet som inte omfattas av några grupprincipinställningar innan du installerar Intune-klienten. Du kan också blockera arv av grupprinciper i organisationsenheter som innehåller PC-datorer som har registrerats i Intune och som du inte vill använda grupprincipinställningar för.

-   Använd säkerhetsgruppfilter för att begränsa grupprincipobjekt till PC-datorer som inte hanteras av Intune. 

-   Inaktivera eller ta bort det grupprincipobjekt som står i konflikt med Intune-principerna.

Mer information om Active Directory och grupprinciper i Windows finns i Windows Server-dokumentationen.

## Så här filtrerar du befintliga grupprincipobjekt för att undvika konflikter med Intune-principer
Om du har identifierat grupprincipobjekt med inställningar som är i konflikt med Intune-principer kan du använda säkerhetsgruppfilter för att begränsa grupprincipobjekten till PC-datorer som inte hanteras av Intune.

<!--- ### Use WMI filters
WMI filters selectively apply GPOs to computers that satisfy the conditions of a query. To apply a WMI filter, deploy a WMI class instance to all PCs in the enterprise before you enroll any PCs in the Intune service.

#### To apply WMI filters to a GPO

1.  Create a management object file by copying and pasting the following into a text file, and then saving it to a convenient location as **WIT.mof**. The file contains the WMI class instance that you deploy to PCs that you want to enroll in the Intune service.

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

2.  Use either a startup script or Group Policy to deploy the file. The following is the deployment command for the startup script. The WMI class instance must be deployed before you enroll client PCs in the Intune service.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;path to MOF file&gt;\wit.mof**

3.  Run either of the following commands to create the WMI filters, depending on whether the GPO you want to filter applies to PCs that are managed by using Intune or to PCs that are not managed by using Intune.

    -   For GPOs that apply to PCs that are not managed by using Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   For GPOs that apply to PCs that are managed by Intune, use the following:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Edit the GPO in the Group Policy Management console to apply the WMI filter that you created in the previous step.

    -   For GPOs that should apply only to PCs that you want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=1**.

    -   For GPOs that should apply only to PCs that you do not want to manage by using Intune, apply the filter **WindowsIntunePolicyEnabled=0**.

For more information about how to apply WMI filters in Group Policy, see the blog post [Security Filtering, WMI Filtering, and Item-level Targeting in Group Policy Preferences](http://go.microsoft.com/fwlink/?LinkId=177883). --->


Med en grupprincip kan du tillämpa grupprincipobjekt enbart på de säkerhetsgrupper som du anger i området **Säkerhetsfiltrering** i konsolen Grupprinciphantering för ett utvalt grupprincipobjekt. Grupprincipobjekt gäller som standard för **autentiserade användare**.

-   Skapa en ny säkerhetsgrupp i snapin-modulen **Active Directory – användare och datorer** som innehåller datorer och användarkonton som du inte vill hantera med hjälp av Intune. Du kan till exempel ge gruppen namnet **Inte i Microsoft-Intune**.

-   Högerklicka på den nya säkerhetsgruppen på fliken **Delegering** i konsolen Grupprinciphantering för det valda grupprincipobjektet och delegera lämpliga **Läs**- och **Tillämpa grupprincip**-behörigheter till både användare och datorer i säkerhetsgruppen. (Behörigheterna för**Tillämpa grupprincip** är tillgängliga i dialogrutan **Avancerat** .)

-   Tillämpa sedan det nya säkerhetsgruppfiltret på ett utvalt grupprincipobjekt och ta bort standardfiltret **Autentiserade användare** .

Den nya säkerhetsgruppen måste underhållas när registreringen i Intune-tjänsten ändras.

### Se även
[Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


