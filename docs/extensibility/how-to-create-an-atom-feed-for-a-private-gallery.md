---
title: "Vorgehensweise: erstellen ein Atom-Feed für einen privaten Katalog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b41cb3012b937ac5448b129657064cca68a5d725
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Vorgehensweise: erstellen ein Atom-Feed für einen privaten Katalog
Sie erstellen eine Atom (RSS-Feeds) in einem Intranetspeicherort, die Erweiterungen enthält, und fügen den Feed auf **Erweiterungen und Updates** als privater Katalog. Weitere Informationen finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Erstellen einen Atom-Feed  
 Um einen Atom-feed als privater Katalog zu erstellen, erfassen Sie zuerst Ihre Erweiterungen (VSIX-Dateien) in einen Ordner. Sie können diese in Unterordnern organisieren, wenn Sie möchten. Sie benötigen außerdem die folgenden Ressourcen:  
  
-   Eine atom.xml-Datei, die die Erweiterungen als privater Katalog verfügbar macht. Informationen zum Herstellen der Verbindung zu der Datei atom.xml **Erweiterungen und Updates**, finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).  
  
-   Ein Ordner, der alle Dateien des quellstartabbilds enthält, die von den Erweiterungen (z. B. Screenshots) extrahiert wurden. Die Datei atom.xml enthält relative Links zu dieser Bilder, damit sie verfügbar sind **Erweiterungen und Updates**.  
  
 Nehmen wir beispielsweise an, dass Sie die folgenden zwei Erweiterungen in einen Ordner gesammelt haben:  
  
-   Template_Wizard_239.VSIX, also eine leere VSIX-Projektvorlage.  
  
-   SelectionHighlight.vsix, die ein Tool, das alle Instanzen eines markierten Worts hervorgehoben ist.  
  
 Der Inhalt der Datei atom.xml würde das folgende Beispiel ähnelt:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ....</summary>   
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
  ...  
  </entry>  
  </feed>  
  
```  
  
 Beachten Sie, dass die zwei Linktags Screenshots im generierten Ordner "Bilder" verweisen.  
  
## <a name="see-also"></a>Siehe auch  
 [Private Kataloge](../extensibility/private-galleries.md)