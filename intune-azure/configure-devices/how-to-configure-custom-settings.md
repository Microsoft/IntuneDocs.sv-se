---
title: "Så här konfigurerar du Intunes anpassade enhetsinställningar | Förhandsversion av Intune Azure | Microsoft Docs"
description: "Förhandsversion av Intune Azure: Läs om hur använder Intune för att konfigurera anpassade inställningar för enheter som du hanterar."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/23/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 89afae81076d563f4ebba289f8fa82eaea6ab234
ms.openlocfilehash: b404df57e94afe7b80dd39163ed72a24d8b05508


---

# <a name="how-to-configure-custom-device-settings"></a>Konfigurera anpassade enhetsinställningar

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="when-to-use-custom-settings"></a>När anpassade inställningar används

Anpassade enhetsinställningar kan vara användbara när Intune inte har de inställningar som du vill konfigurera inbyggda och tillgängliga från andra enhetsprofiler.
Anpassade inställningar konfigureras på olika sätt för respektive plattform. Med Android- och Windows-enheter kan du till exempel ange OMA-URI-värden (Open Mobile Alliance Uniform Resource Identifier) för att styra funktioner på enheterna. På Apple-enheter kan du importera en fil som du har skapat med [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12).

Använd informationen i det här avsnittet om du vill lära dig grunderna för hur du konfigurerar profiler med anpassade inställningar. Läs sedan de specifika avsnitten om respektive plattform om du vill ha mer detaljerad information.

## <a name="create-a-device-profile-containing-custom-settings"></a>Skapa en enhetsprofil som innehåller anpassade inställningar

1. Logga in på Azure-portalen.
2. Välj **Fler tjänster** > **Övrigt** > **Intune**.
3. Välj **Konfigurera enheter** på **Intune**-bladet.
2. Välj **Hantera** > **Profiler** på bladet **Enhetskonfiguration**.
3. Välj **Skapa profil** på profilbladet.
4. Ange **Namn** och **Beskrivning** för den anpassade profilen på bladet **Skapa profil**.
5. Välj den enhetsplattform på vilken du vill tillämpa anpassade inställningar från listrutan **Plattform**. För närvarande kan du välja någon av följande plattformar för anpassade enhetsinställningar:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 10 och senare**
6. I listrutan **Profil**typ väljer du **Anpassad**.
7. Beroende på vilken plattform du har valt så varierar de inställningar som du kan konfigurera. Gå till något av följande avsnitt om du vill ha detaljerad information om respektive plattform:
    - [Inställningar för Android](custom-for-android.md)
    - [Inställningar för iOS](custom-for-ios.md)
    - [Inställningar för macOS](custom-for-macos.md)
    - [Inställningar för Windows Phone 8.1](custom-for-windows-phone-8-1.md)
    - [Inställningar för Windows 10](custom-for-windows-10.md)
8. När du är klar går du tillbaka till bladet **Skapa profil** och trycker på **Skapa**.

Profilen skapas och visas på bladet med profillistan.
Om du vill gå vidare och tilldela den här profilen till grupper, kan du läsa mer i [Tilldela enhetsprofiler](how-to-assign-device-profiles.md).




<!--HONumber=Feb17_HO1-->


