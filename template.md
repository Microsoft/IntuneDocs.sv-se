---
title:
- ARTIKELRUBRIK | TJÄNSTNAMN
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: d05559a46cfd2bf9e092378e7cff779022e21792
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2019
ms.locfileid: "20283577"
---
# <a name="metadata-and-markdown-template"></a>Metadata- och markdownmall

Den här docs.ms-mallen innehåller exempel på markdownsyntax, samt anvisningar för hur du anger metadata. Den finns i rotkatalogen för varje EM Pilot-lagringsplats (t.ex. ~/Azure-RMSDocs-pr /template.md) och är avsedd att läsas som en markdownfil. Du kan gå till [den publicerade versionen](https://stage.docs.microsoft.com/en-us/rights-management/template) om du vill se hur markdownexemplen återges.

När du skapar en markdownfil bör du kopiera mallen till en ny fil, fylla i metadata enligt beskrivningen nedan, ange artikelns rubrik som H1-rubrik och ta bort innehållet. 


## <a name="metadata"></a>Metadata 

Det fullständiga metadatablocket ligger över och det är indelat i obligatoriska och valfria fält. Mer information finns i [Fusklapp för OPS-metadata](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) Kommentarer:

- Du **måste** ha ett blanksteg mellan kolon (:) och värdet för ett metadataelement.
- Om ett valfritt metadataelement saknar ett värde kommenterar du ut elementet med # (lämna det inte tomt eller använd "saknas"). Om du lägger till ett värde till ett element som har kommenterats ut måste du ta bort #.
- Kolon i ett värde (t.ex. en rubrik) bryter metadataparsern. Använd istället HTML-kodningen &#58; (t.ex. "rubrik: Azure Rights Management&#58; Grunderna | "Azure RMS").
- **rubrik**: den här rubriken visas i sökresultat. Rubriken ska avslutas med ett lodstreck (|) följt av namnet på tjänsten (se ovan). Rubriken behöver inte (och bör troligtvis inte) vara identisk med rubriken i H1 rubriken. Den bör innehålla ungefär 65 tecken (inklusive | TJÄNSTENS NAMN)
- **författare**, **ansvarig**, **granskare**: Fältet Författare ska innehålla författarens **Github-användarnamn** och inte hans/hennes alias.  I fälten "ansvarig" och "granskare" ska du däremot ange alias. ms.reviewer anger namnet på projektledaren som är kopplad till artikeln eller tjänsten.
- **ms.assetid**: Det här är artikelns GUID. När du skapar en ny markdownfil kan hämta ett GUID från [ https://www.guidgenerator.com ](https://www.guidgenerator.com). 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: Du hittar möjliga värden för de här elementen [här](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## <a name="basic-markdown-and-gfm"></a>Grundläggande markdown och GFM

Alla grundläggande och GFM-markdown (Github-flavored markdown) stöds. Mer information om dem finns i:

- [Baslinjesyntax för markdown](https://daringfireball.net/projects/markdown/syntax)
- [GFM-dokumentation (Github-flavored markdown)](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Rubriker

Exempel på rubriker på första och andra nivån finns här ovanför. 

Det **får bara** finnas en rubrik på första nivån i ditt ämne och den visas som rubrik på sidan.  

Av rubriker på andra nivån skapas innehållsförteckningen på sidan som visas i avsnittet "I den här artikeln" under rubriken på sidan.

### <a name="third-level-heading"></a>Rubrik på tredje nivån
#### <a name="fourth-level-heading"></a>Rubrik på fjärde nivån
##### <a name="fifth-level-heading"></a>Rubrik på femte nivån
###### <a name="sixth-level-heading"></a>Rubrik på sjätte nivån

## <a name="text-styling"></a>Textformat

*Kursiv* 

**Fet** 

~~Genomstruken~~



## <a name="links"></a>Links

Om du vill länka till en markdownfil på samma lagringsplats använder du [relativa länkar](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Exempel: [Vad är Azure Rights Management](./understand-explore/what-is-azure-rights-management.md)

Du länkar till en rubrik i samma markdownfil genom att visa källan för den publicerade artikeln och leta upp id för huvudet (t.ex. `id="blockquote"`, och länka med # + id (t.ex. `#blockquote`).

- Exempel: [Blockcitat](#blockquote)

Om du vill länka till en rubrik i en markdownfil på samma lagringsplats använder du relativa länkar och hashtaggslänkar.

- Exempel: [Teknisk översikt över registreringsprocessen](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Använd hela webbadressen som länk om du vill länka till en extern fil.

- Exempel: [Github](http://www.github.com)

När en webbadress finns i en markdownfil omvandlas den till en klickbar länk.

- Exempel: http://www.github.com

## <a name="lists"></a>Listor

### <a name="ordered-lists"></a>Sorterade listor

1. Det här 
1. Är
1. En
1. Sorterad
1. List  


#### <a name="ordered-list-with-an-embedded-list"></a>Sorterad lista med en inbäddad lista

1. Här
1. kommer
1. en
1. inbäddad
    1. Fröken Matsson
    1. Professor Persson
1. sorterad
1. lista


### <a name="unordered-lists"></a>Osorterade listor

- Denna
- är
- en
- punkt-
- lista


##### <a name="unordered-list-with-an-embedded-lists"></a>Osorterad lista med en inbäddad lista

- Denna 
- punkt- 
- lista
    - Fru Hansson
    - Herr Berggren
- innehåller  
- andra
    1. Överste Karlsson
    1. Fru Berg
- listor


## <a name="horizontal-rule"></a>Vågrät linje

---

## <a name="tables"></a>Tabeller

| Tabeller        | är           | coola  |
| ------------- |:-------------:| -----:|
| kolumn 3 är      | högerjusterad | $1600 |
| kolumn 2 är      | centrerad      |   $12 |
| kolumn 1 är som standard | vänsterjusterad     |    $1 |


## <a name="code"></a>Kod

### <a name="codeblock"></a>Kodblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Infogad kod

Det här är ett exempel på `in-line code`.

## <a name="blockquotes"></a>Blockcitat

> Torkan hade nu varat i tio miljoner år och skräcködlornas välde var för länge sedan över. Vid ekvatorn, i den kontinent som senare skulle få namnet Afrika, hade kampen om överlevnad nått en ny våldsam kulmen och vinnaren hade ännu inte dykt upp på arenan. I den här sterila och uttorkade världen var det bara de små och snabba och de riktigt vildsinta som kunde klara sig och hoppas på att överleva.

## <a name="images"></a>Avbildningar

### <a name="static-image"></a>Statisk avbildning

![det här är alternativtexten](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Länkad avbildning

[![alternativtext för länkad bild](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>Animerad GIF

![animerad gif](./media/hololens.gif)

## <a name="alerts"></a>Aviseringar

### <a name="note"></a>Obs!

> [!NOTE]
> Det här är Obs!

### <a name="warning"></a>Varning

> [!WARNING]
> Det här är en VARNING

### <a name="tip"></a>Tips

> [!TIP]
> Det här är ett TIPS

### <a name="important"></a>Viktigt

> [!IMPORTANT]
> Det här är VIKTIGT

## <a name="videos"></a>Videor

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms-tillägg

### <a name="button"></a>Knapp

> [!div class="button"]
[knapplänkar](/rights-management)

### <a name="selector"></a>Väljare

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>Steg för steg

>[!div class="step-by-step"]
[Föreg.](https://www.example.com)
[Nästa](https://www.example.com)