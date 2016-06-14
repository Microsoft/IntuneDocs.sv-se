---
# required metadata

title: MAM-principinställningar för Android | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5dbb702a-1df5-4637-95c9-77a5f0b1a0e3

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inställningar för hanteringsprincip för Android-mobilappar i Microsoft Intune
Principinställningarna som beskrivs nedan kan [konfigureras](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) för en MAM-princip på bladet **Inställningar** på Azure Portal.
Det finns två kategorier för principinställningar, inställningar för Dataflytt och Åtkomst:

##  Inställningar för dataflytt
Termen **principhanterade appar** används för att hänvisa till appar som är konfigurerade med MAM-principer.
- **Förhindra Android-säkerhetskopieringar:** Välj **Ja** om du vill förhindra eller **Nej** om du vill tillåta säkerhetskopiering av företagsdata från principhanterade appar.

  **Standardvärde = Ja**
- **Tillåt att appen överför data till andra appar:** Välj ett alternativ för att ange de appar som kan ta emot företagsdata från principhanterade appar:
  -   **Principhanterade appar**: Tillåt överföring endast till appar som har MAM-principen
  -   **Alla appar**: Tillåt överföring till alla appar
  -   **Ingen**: Tillåt inte dataöverföring till någon app

  **Standardvärde = Principhanterade appar**
- **Tillåt att appen tar emot data från andra appar:** Ange appar som tillåts att överföra data till principhanterade appar:
  -   **Principhanterade appar**: Tillåt endast dataöverföring från andra principhanterade appar
  -   **Alla appar**: Tillåt dataöverföring från alla appar
  -   **Ingen**: Tillåt inte dataöverföring från någon app

      **Standardvärde = Alla appar**

-   **Förhindra Spara som:** Välj **Ja** om du vill inaktivera alternativet Spara som i appar som använder den här principen. Välj **Nej** om du vill tillåta att Spara som används.

  **Standardvärde = Ja**
- **Begränsa klipp ut, kopiera och klistra in med andra appar:** Ange när åtgärder för klipp ut, kopiera och klistra in ska begränsas. Välj mellan:
  -   **Blockerad**: Tillåt inte åtgärderna Klipp ut, kopiera och klistra in mellan principhanterade appar.
  -   **Principhanterade appar**: Tillåt endast åtgärderna Klipp ut, kopiera och klistra in mellan principhanterade appar.
  -   **Principhanterade appar med inklistring**: Tillåt klipp ut och kopiera mellan principhanterade appar. Tillåt att data som klipps ut eller kopieras från en annan app kan klistras in i den här appen.
  -   **Alla appar**: Inga begränsningar för klipp ut, kopiera och klistra in mellan appar.

    **Standardvärde = Principhanterade appar med inklistring**
-   **Begränsa visning av webbinnehåll i Managed Browser:** När den här inställningen är aktiverad öppnas alla länkar i appen i Managed Browser.

  För enheter som inte är registrerade i Intune öppnas webblänkar i principhanterade appar endast i appen Managed Browser med hanteringsprincipen för mobilappar.

  Om du använder Intune för hanteringen av dina enheter läser du [Hantera Internetåtkomst med hanterade webbläsarprinciper med Microsoft Intune](manage-internet-access-using-managed-browser-policies.md).

    **Standardvärde = Ja**
- **Kryptera appdata:** Välj **Ja** för att aktivera kryptering. När den här inställningen är aktiverad tillhandahålls krypteringen av Microsoft för appar som associeras med en hanteringsprincip för mobilappar. Data krypteras synkront under I/O-åtgärder. Innehållet i enhetens lagringsutrymme krypteras alltid.
  >[!NOTE] Krypteringsmetoden är inte FIPS 140-2-certifierad.

  **Standardvärde = Ja**

- **ContactSyncDisabled:** Välj **Ja** för att förhindra att kontaktinformation synkroniseras till den interna adressboken på enheten. Om du väljer **Nej** sparar appen kontaktinformation till den interna adressboken på enheten.<br/>När du gör en selektiv rensning för att ta bort företagsdata tas kontakter som synkroniserats direkt från appen till den interna adressboken bort. Kontakter som synkroniseras från den interna adressboken till en annan extern källa kan inte rensas. Detta gäller för närvarande endast för **Microsoft Outlook**-appen.

  **Standardvärde = Ja**

##  Principinställningar för Android-åtkomst
Termen **principhanterade appar** används för att hänvisa till appar som är konfigurerade med MAM-principer

- **Kräv PIN-kod för åtkomst:** Välj **Ja** om du vill kräva en PIN-kod vid användning av principhanterade appar. Användarna uppmanas att konfigurera detta första gången de kör appen i en arbetskontext.

 **Standardvärde = Ja**

 -  **Tillåt enkel PIN-kod:** Ange du om du vill tillåta att användarna använder enkla PIN-kodssekvenser, till exempel 1234 eller 1111. **Standardvärde = Ja**.
 - **PIN-kodslängd:** Ange det minsta antalet siffror i en PIN-kod. **Standardvärde = 4**
 - **Antal försök innan PIN-koden återställs:** Ange antalet tillåtna PIN-inmatningsförsök innan användaren måste återställa PIN-koden. **Det finns inget standardvärde för den här inställningen.**
- **Kräv företagets autentiseringsuppgifter för åtkomst:** Välj **Ja** om du vill kräva att företagets autentiseringsuppgifter anges i stället för en PIN-kod för åtkomst till appen.  Om du väljer **Ja** åsidosätts kraven på PIN-kod eller Touch ID.  Användaren uppmanas att ange sina autentiseringsuppgifter för företaget.

  **Standardvärde = Nej**
- **Blockera hanterade appar från att köras på jailbrokade eller rotade enheter:** Välj **Ja** för att blockera appar från att köras på jailbrokade eller rotade enheter. Användaren kan fortfarande använda apparna för personliga uppgifter, men måste använda en annan enhet för arbete.

  **Standardvärde = Ja**
- **Kontrollera åtkomstkraven på nytt efter (minuter)**-   **Tidsgräns:** Tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen.
  -   **Offlinerespittid:** Ange tiden (i minuter) innan åtkomstkraven för appen kontrolleras igen om enheten är offline.

    **Standardvärde = 30 minuters timeout och 720 minuters offlinerespittid**

-   **Intervallet innan appdata rensas efter att enheten varit offline (dagar):** Du kan välja att rensa företagsdata om en enhet har varit offline en viss tid.  Ange hur många dagar en enhet kan vara offline innan företagsdata tas bort från enheten. **Tips!** Om du anger värdet 0 inaktiveras den här inställningen.

  **Standardvärde = 90 dagar**
- **Blockera skärmdump och Android Assistant (Android 6 Marshmallow eller senare):** Välj **Ja** för att blockera funktioner för skärmdump och **Android Assistant** på enheten när den här appen används.


<!--HONumber=May16_HO3-->


