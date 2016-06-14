---
# required metadata

title: Hantera iOS-appar som du har köpt via ett volyminköpsprogram | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 1dafc28a-7f8b-4fe0-8619-f977c93d1140

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hantera iOS-appar som du har köpt via ett volyminköpsprogram med Microsoft Intune
En del appbutiker erbjuder möjligheten att köpa flera licenser till en app som du vill köra i företaget. Det hjälper dig att minska det administrativa arbetet med att spåra flera köpta kopior av appar.

Microsoft Intune hjälper dig att hantera appar som du har köpt via ett sådant program genom att importera licensinformationen från App Store, spåra hur många licenser som du har använt och hindra dig från att installera fler kopior av appen än du äger.

> [!Important]
> Intune tilldelar för närvarande applicenser för iOS VPP till användare och inte enheter. Därför måste användare ange sitt Apple-ID-lösenord för att installera appen.

## Hantera appar som köpts genom volyminköpsprogrammet för iOS-enheter
Du kan köpa flera licenser för iOS-appar genom [Apples volymköpsprogram för företag (VPP, Volume Purchase Program)](http://www.apple.com/business/vpp/). När du gör det måste du bland annat skapa ett Apple VPP-konto från Apples webbplats och skicka din Apple VPP-token till Intune.  Sedan kan du synkronisera volyminköpsinformationen med Intune och spåra din användning av appar som du köpt genom volyminköpsprogrammet.

## Innan du börjar
Innan du börjar måste du skaffa en VPP-token från Apple och ladda upp den till ditt Intune-konto. Du bör också känna till följande:

* En organisation kan bara ha ett VPP-konto och en VPP-token.
* När du har kopplat ett Apple VPP-konto till Intune kan du inte koppla ett annat konto senare. Därför är det mycket viktigt att mer än en person har tillgång till informationen om det konto som du använder.
* Om du tidigare har använt en VPP-token med en annan produkt måste du generera en ny som ska användas med Intune.
* Varje token är giltig i ett år.
* Som standard synkroniserar Intune med Apple VPP-tjänsten två gånger om dagen. Du kan dock starta en manuell synkronisering när som helst.
* När du har importerat VPP-token i Intune ska du inte importera samma token till andra enhetshanteringslösningar. Om du gör det kan licenstilldelningen och användarposter gå förlorade.
* Innan du börjar använda iOS VPP med Intune tar du bort alla befintliga VPP-användarkonton som skapats med andra MDM-leverantörer. Intune synkroniserar inte de användarkontona till Intune som en säkerhetsåtgärd. Intune synkroniserar endast data från Apple VPP-tjänsten som har skapats av Intune. 

## Så här skaffar du och laddar upp en Apple VPP-token

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Admin** &gt; **iOS och Mac OS X** &gt; **Volyminköpsprogram**.

2.  Klicka på länken **Apple VPP-konto** och registrera dig för volyminköpsprogrammet för företag om du inte redan gjort det. När du har registrerat dig laddar du ned Apple VPP-token för ditt konto.

3.  På sidan **Hantera Apple VPP (Volume Purchase Program)** i Intune-konsolen klickar du på **Överför VPP-token**.

4.  I dialogrutan **Överför en VPP-token** anger du eller klistrar in namnet på VPP-token och ditt Apple-ID och klickar sedan på **Överför**.

5.  I varningsdialogrutan klickar du på kryssrutan för att bekräfta att du är medveten om att du inte kan byta till ett annat VPP-konto senare och klickar sedan på **Ja**.

På sidan **Volyminköpsprogram** kan du nu visa information om Apple VPP-token, inklusive när den senast uppdaterades, när den upphör att gälla och när den senast synkroniserades med Intune.

Du kan synkronisera data från Apple med Intune när som helst genom att klicka på **Synkronisera nu**.

## Distribuera en volyminköpt app

1.  Gå till [Microsoft Intune-administrationskonsolen](https://manage.microsoft.com) och klicka på **Appar** &gt; **Hanterad programvara** &gt; **Volyminköpta appar**. I listan visas alla appar som har synkroniserats från Apple VPP-tjänsten.

2.  Välj den app som du vill distribuera, klicka på **Hantera distribution**, genomför överföringen, skapa och distribuera appen med hjälp av anvisningarna i avsnittet [Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md).

När du distribuerar appar som en **obligatorisk** installation används en licens av alla användare som installerar appen.

Om du vill frisläppa en licens måste du ändra distributionsåtgärden till **Avinstallera**. Licensen frisläpps när appen avinstalleras.

När användare med kvalificerande enheter försöker installera en VPP-app ombeds de att gå med i Apples volyminköpsprogram. De måste göra detta innan appinstallationen fortsätter.

> [!TIP] Titta på kolumnen **Status för VPP-villkor** om du vill se godkännandestatus för varje användare som appen har distribuerats till.

Distributionen misslyckas om det inte finns fler tillgängliga licenser.

## För att övervaka Apple VPP-appar
Du kan övervaka vilka VPP-appar som har distribuerats och hur många licenser som används från arbetsýtan **Appar** i noden **Hanterad programvara** &gt; **Volyminköpta appar**.

> [!TIP] Du kan också använda appen **Filter** att kontrollera status för varje appinstallation.

### Se även
[Distribuera appar i Microsoft Intune](deploy-apps-in-microsoft-intune.md)



<!--HONumber=May16_HO4-->


