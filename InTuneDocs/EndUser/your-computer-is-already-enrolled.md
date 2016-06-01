---
# required metadata

title: Din dator är redan registrerad | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Din dator är redan registrerad.
Du ser den här sidan eftersom du körde installationsprogrammet för Intune-klientprogrammet. Men programvaran är redan är installerad på din dator och installationen kan inte fortsätta.

Detta kan bero på att:

-   Klientprogrammet har installerats tidigare och installationsprogrammet kördes igen.

-   Installationsprogrammet kördes på datorn efter att en IT-administratör dragit tillbaka enheten från Intune. Det kan ta flera timmar innan klientprogrammet tas bort från datorn när enheten har dragits tillbaka.

-   Installationsprogrammet har upptäckt en nyligen misslyckad installation eller misslyckad borttagning av klientprogrammet.

## Detta installeras på datorn
Intune-klienten installeras. När installationen är klar fortsätter klientprogrammet att köras i bakgrunden där det konfigurerar din dator för användning med Intune. Den här processen kan ta lite tid att slutföra, och omfattar:

-   Registrering av din dator i Intune

-   Överföring av inventering av maskinvara och installerade program

-   Konfiguration av Intune-princip, inklusive installation av Endpoint Protection (om det är konfigurerat)

-   Intune Center-installation

När Intune Center har installerats kan du använda det för att komma åt företagsportalen där du kan länka datorn till ditt arbetskonto.

## Microsoft Intune Center
Intune Center installeras som en app på datorn när datorn har installerat klientprogrammet och registrerar datorn i Intune. Du kan använda Intune Center för att:

-   **Hämta program från företagsportalen** – Sök efter och installera appar som har distribuerats av IT-administratören. När du loggar in på företagsportalen första gången, på en dator som nyligen registrerats, visas alternativet att länka ditt arbetskonto till datorn.

-   **Sök efter programuppdateringar** – Sök efter programuppdateringar som har distribuerats av Intune-administratören.

-   **Starta en Endpoint Protection-sökning på datorn** – Du kan starta en sökning efter skadlig programvara på din dator.

-   **Begär fjärrhjälp** – Det här alternativet är bara tillgängligt om Fjärrhjälp stöds av operativsystemet.

## Kontrollera att klientprogrammet har installerats eller tagits bort
**Kontrollera att klienten är installerad:**
Intune-klientinstallationen är klar när följande appar är tillgängliga på datorn:

-   **Intune Center**

-   **Intune Endpoint Protection** (om Endpoint Protection har aktiverats av IT-administratören)

Om du föredrar att använda Aktivitetshanteraren kan du söka efter Intune-klienttjänsten, som bör köra:

-   **OmcSvc**

**Kontrollera att klienten har tagits bort:**
När Intune-klienten avinstalleras från en dator tas de appar som installerades tillsammans med klienten bort, inklusive Intune Center.

Intune-klienttjänsten **OmcSvc** tas bort.

## Så här tar du bort klientprogrammet från datorn.
Som standard tar det flera timmar från det att IT-administratören drar tillbaka datorn från Intune-administrationskonsolen tills Intune-klientprogrammet avinstalleras.

Om du vill avinstallera Intune-klientprogrammet manuellt från en dator kan du framtvinga avinstallationen genom att följa dessa steg:

1.  Öppna en kommandotolk i administratörsläge på datorn.

2.  Gå till mappen **%programfiles%\Microsoft\OnlineManagement\Common**

3.  Kör följande kommando: **ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune**

Detta schemalägger borttagningen av klientprogrammet.



<!--HONumber=May16_HO1-->


