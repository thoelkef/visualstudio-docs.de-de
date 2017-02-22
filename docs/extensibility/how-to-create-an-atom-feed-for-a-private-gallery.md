---
title: "Gewusst wie: Erstellen Sie einen Atom-Feed f&#252;r einen privaten Galerie | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Atom-feed, private Galerien VSIX"
  - "VSIX-private Galerien Atom-feed"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Erstellen Sie einen Atom-Feed f&#252;r einen privaten Galerie
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können ein Atom \(RSS\-Feeds\) an einem Speicherort im Intranet, die Erweiterungen enthält, und fügen den Feed zu erstellen **Erweiterungen und Updates** als eine private Galerie. Weitere Informationen finden Sie unter [Private Galerien](../extensibility/private-galleries.md).  
  
## Erstellen einen Atom\-Feed  
 Um einen Atom\-feed als eine private Galerie erstellen, erfassen Sie zuerst Ihre Erweiterungen \(VSIX\-Dateien\) in einen Ordner. Sie können diese in Unterordnern organisieren, wenn Sie möchten. Sie benötigen außerdem die folgenden Ressourcen:  
  
-   Eine atom.xml\-Datei, die die Erweiterungen, die als eine private Galerie verfügbar macht. Informationen dazu, wie die Verbindung zu der Datei atom.xml **Erweiterungen und Updates**, finden Sie unter [Private Galerien](../extensibility/private-galleries.md).  
  
-   Ein Ordner, der Bilddateien enthält, die aus der Erweiterung \(z. B. Screenshots\) extrahiert wurden. Die atom.xml\-Datei enthält relativen Links zu dieser Bilder, damit sie in verfügbar sind **Erweiterungen und Updates**.  
  
 Nehmen wir beispielsweise an, dass Sie die folgenden beiden Erweiterungen in einem Ordner gesammelt haben:  
  
-   Template\_Wizard\_239.VSIX, die eine leere VSIX\-Projektvorlage ist.  
  
-   SelectionHighlight.vsix, die ein Tool, das alle Instanzen eines markierten Worts hervorgehoben ist.  
  
 Der Inhalt der Datei atom.xml würde in etwa folgendermaßen aus:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 Beachten Sie, dass die beiden Tags Verknüpfen finden Sie in den Screenshots in den erstellten Ordner Bilder.  
  
## Siehe auch  
 [Private Galerien](../extensibility/private-galleries.md)