---
# required metadata

title: Lösa konflikter mellan grupprincipobjekt och Intune-principer | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Lösa konflikter mellan grupprincipobjekt och Microsoft Intune-principer
Intune använder principer som hjälper dig att hantera inställningarna på de datorer som du hanterar. Du kan t.ex. använda en princip för att kontrollera datorernas inställningar för Windows-brandväggen. Många av Intunes inställningar påminner om inställningarna som du kan konfigurera med Grupprincip i Windows. Emellanåt kan det dock inträffa att de två metoderna hamnar i konflikt med varandra.

När sådana konflikter uppstår har grupprinciper på domännivå företräde framför Intune-principer, såvida datorn inte kan logga in till domänen. I detta fall tillämpas Intune-principen på klientdatorn.

## Vad som krävs vid användning av grupprinciper
Kontrollera att ingen av de principer som du använder hanteras av någon grupprincip. Om du vill undvika konflikter bör du använda en eller flera av följande metoder:

-   Flytta dina datorer till en Active Directory-organisationsenhet som inte omfattas av några grupprincipinställningar innan du installerar Intune-klienten. Du kan också blockera arv av grupprinciper i organisationsenheter som innehåller datorer som har registrerats i Intune och som du inte vill använda grupprincipinställningar för.

-   Använd ett WMI-filter eller säkerhetsfilter för att begränsa grupprincipobjekt till datorer som inte hanteras av Intune. Mer information och exempel på hur du gör finns i avsnittet [Så här filtrerar du befintliga grupprincipobjekt för att undvika konflikter med Microsoft Intune-principer](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter) nedan.

-   Inaktivera eller ta bort det grupprincipobjekt som står i konflikt med Intune-principerna.

Mer information om Active Directory och grupprinciper i Windows finns i Windows Server-dokumentationen.

## Så här filtrerar du befintliga grupprincipobjekt för att undvika konflikter med Intune-principer
Om du har identifierat grupprincipobjekt med inställningar som är i konflikt med Intune-principer kan du använda någon av följande filtreringsmetoder för att begränsa grupprincipobjekten till datorer som inte hanteras av Intune.

### Använda WMI-filter
WMI-filter tillämpar selektivt grupprincipobjekt på datorer som uppfyller villkoren i en fråga. Om du vill använda ett WMI-filter distribuerar du en WMI-klassinstans till alla datorer på företaget innan du registrerar datorer för Intune-tjänsten.

#### Tillämpa WMI-filter på grupprincipobjekt

1.  Skapa en hanteringsobjektsfil genom att kopiera och klistra in följande i en textfil och sedan spara filen på en lämplig plats som **WIT.mof**. Filen innehåller den WMI-klassinstans som du distribuerar till datorer som du vill registrera i Intune-tjänsten.

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

2.  Använd antingen ett startskript eller en grupprincip för att distribuera filen. Följande distributionskommando används för startskriptet. Du måste distribuera WMI-klassinstansen innan du registrerar klientdatorer i Intune-tjänsten.

    **C:/Windows/System32/Wbem/MOFCOMP &lt;sökväg till MOF-fil&gt;\wit.mof**

3.  Skapa WMI-filtren genom att köra något av följande kommandon, beroende på om det grupprincipobjekt som du vill filtrera gäller för datorer som hanteras i Intune eller för datorer som inte hanteras i Intune.

    -   För grupprincipobjekt som gäller för datorer som inte hanteras i Intune använder du följande:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   För grupprincipobjekt som gäller för datorer som hanteras i Intune använder du följande:

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  Redigera grupprincipobjektet i konsolen Grupprinciphantering så att WMI-filtret som du skapade i förra steget tillämpas.

    -   För grupprincipobjekt som endast ska tillämpas på datorer som du vill hantera med Intune använder du filtret **WindowsIntunePolicyEnabled=1**.

    -   För grupprincipobjekt som endast ska tillämpas på datorer som du inte vill hantera med Intune använder du filtret **WindowsIntunePolicyEnabled=0**.

Mer information om hur du använder WMI-filter i Grupprincip finns i bloggposten [Säkerhetsfiltrering, WMI-filtrering och målinriktning på objektnivå i grupprincipinställningar](http://go.microsoft.com/fwlink/?LinkId=177883)

### Använda säkerhetsgruppfilter
Med en grupprincip kan du tillämpa grupprincipobjekt enbart på de säkerhetsgrupper som du anger i området **Säkerhetsfiltrering** i konsolen Grupprinciphantering för ett utvalt grupprincipobjekt. Grupprincipobjekt gäller som standard för **autentiserade användare**

-   Skapa en ny säkerhetsgrupp i snapin-modulen **Active Directory – användare och datorer** som innehåller datorer och användarkonton som du inte vill hantera med hjälp av Intune. Du kan till exempel ge gruppen namnet **Inte i Microsoft-Intune**

-   Högerklicka på den nya säkerhetsgruppen på fliken **Delegering** i konsolen Grupprinciphantering för det valda grupprincipobjektet och delegera lämpliga **Läs**- och **Tillämpa grupprincip**-behörigheter till både användare och datorer i säkerhetsgruppen. (Behörigheterna för**Tillämpa grupprincip** är tillgängliga i dialogrutan **Avancerat** .)

-   Tillämpa sedan det nya säkerhetsgruppfiltret på ett utvalt grupprincipobjekt och ta bort standardfiltret **Autentiserade användare** .

Den nya säkerhetsgruppen måste underhållas när registreringen i Intune-tjänsten ändras.

### Se även
[Hantera Windows-datorer med Microsoft Intune](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


