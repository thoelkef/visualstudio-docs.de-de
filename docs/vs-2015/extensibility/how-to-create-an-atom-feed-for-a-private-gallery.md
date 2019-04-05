---
title: 'Vorgehensweise: Erstellen eines Atom-Feed für einen privaten Katalog | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961253"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Vorgehensweise: Erstellen eines Atom-Feeds für einen privaten Katalog
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein Atom (RSS-Feeds) zu einem Intranet-Speicherort, der Erweiterungen enthält, und fügen den Feed zu erstellen, **Erweiterungen und Updates** als privater Katalog. Weitere Informationen finden Sie unter [Private Galleries](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Erstellen einen Atom-Feed  
 Um einen Atom-feed als privater Katalog zu erstellen, sammeln Sie zunächst Ihre Erweiterungen (VSIX-Dateien) in einen Ordner. Sie können diese in Unterordnern organisieren, wenn Sie möchten. Sie benötigen außerdem die folgenden Ressourcen:  
  
- Eine atom.xml-Datei, die die Erweiterungen als privater Katalog zur Verfügung stellt. Informationen dazu, wie Sie die Datei atom.xml zum Verbinden **Erweiterungen und Updates**, finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).  
  
- Ein Ordner, der Bilddateien enthält, die von den Erweiterungen (z. B. Screenshots) extrahiert wurden. Die atom.xml-Datei enthält die relative Links zu diesen Bildern, damit sie in verfügbaren **Erweiterungen und Updates**.  
  
  Nehmen wir beispielsweise an, dass Sie die folgenden zwei Erweiterungen in einem Ordner gesammelt haben:  
  
- Template_Wizard_239.VSIX, einer leeren Vorlage des VSIX-Projekt handelt.  
  
- SelectionHighlight.vsix, die ein Tool, um alle Instanzen eines markierten Worts hervorgehoben ist.  
  
  Der Inhalt der Datei atom.xml werden im folgende Beispiel ähneln:  
  
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
  
 Beachten Sie, dass die beiden Tags link finden Sie Screenshots im Ordner generierten Bilder.  
  
## <a name="see-also"></a>Siehe auch  
 [Private Kataloge](../extensibility/private-galleries.md)
