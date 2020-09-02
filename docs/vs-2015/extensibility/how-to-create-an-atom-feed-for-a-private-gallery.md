---
title: 'Vorgehensweise: Erstellen eines Atom-Feeds für einen privaten Katalog | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204208"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Gewusst wie: Erstellen eines Atom-Feeds für einen privaten Katalog
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können einen Atom (RSS)-Feed an einem Intranetspeicherort erstellen, der Erweiterungen enthält, und den Feed zu **Erweiterungen und Updates** als privaten Katalog hinzufügen. Weitere Informationen finden Sie unter [private Galerien](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Erstellen eines Atom-Feeds  
 Um einen Atom-Feed als privaten Katalog zu erstellen, erfassen Sie zunächst die Erweiterungen (VSIX-Dateien) in einem Ordner. Wenn Sie möchten, können Sie Sie in Unterordnern organisieren. Außerdem benötigen Sie die folgenden Ressourcen:  
  
- Eine atom.xml Datei, die die Erweiterungen als private Galerie verfügbar macht. Informationen dazu, wie Sie die atom.xml Datei mit **Erweiterungen und Updates**verbinden, finden Sie unter [private Galerien](../extensibility/private-galleries.md).  
  
- Ein Ordner, der alle Bilddateien enthält, die aus den Erweiterungen extrahiert wurden (z. b. Bildschirmaufnahmen). Die atom.xml Datei enthält relative Links zu diesen Bildern, sodass Sie in **Erweiterungen und Updates**verfügbar sind.  
  
  Nehmen Sie beispielsweise an, dass Sie die folgenden beiden Erweiterungen in einem Ordner gesammelt haben:  
  
- Template_Wizard_239. VSIX, eine leere VSIX-Projektvorlage.  
  
- Selectionhighlight. VSIX, bei dem es sich um ein Tool zum Hervorheben aller Instanzen eines ausgewählten Worts handelt.  
  
  Der Inhalt der atom.xml Datei ähnelt dem folgenden Beispiel:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Beachten Sie, dass sich die beiden Linktags auf Screenshots im generierten Ordner von Images beziehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Private Kataloge](../extensibility/private-galleries.md)
