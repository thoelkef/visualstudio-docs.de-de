---
title: 'Vorgehensweise: Erstellen eines Atom-Feed für einen privaten Katalog | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6053c01908df9f1c2884e81c8610a989ac89294
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55030677"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Vorgehensweise: Erstellen Sie einen Atom-feed für einen privaten Katalog
Sie können ein Atom (RSS-Feeds) zu einem Intranet-Speicherort, der Erweiterungen enthält, und fügen den Feed zu erstellen, **Erweiterungen und Updates** als privater Katalog. Weitere Informationen finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).  
  
## <a name="create-an-atom-feed"></a>Erstellen Sie einen Atom-feed  
 Um einen Atom-feed als privater Katalog zu erstellen, sammeln Sie zunächst Ihre Erweiterungen (*VSIX* Dateien) in einen Ordner. Sie können diese in Unterordnern organisieren, wenn Sie möchten. Sie benötigen außerdem die folgenden Ressourcen:  
  
- Ein *atom.xml* -Datei, die die Erweiterungen als privater Katalog zur Verfügung stellt. Informationen zum Herstellen einer Verbindung die *atom.xml* Datei **Erweiterungen und Updates**, finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).  
  
- Ein Ordner, der Bilddateien enthält, die von den Erweiterungen (z. B. Screenshots) extrahiert wurden. Die *atom.xml* -Datei enthält die relative Links zu diesen Bilder, damit sie in verfügbaren **Erweiterungen und Updates**.  
  
  Nehmen wir beispielsweise an, dass Sie die folgenden zwei Erweiterungen in einem Ordner gesammelt haben:  
  
- *Template_Wizard_239.VSIX*, dies ist eine leere VSIX-Projektvorlage.  
  
- *SelectionHighlight.vsix*, dies ist ein Tool, um alle Instanzen eines markierten Worts zu markieren.  
  
  Den Inhalt der *atom.xml* Datei wird im folgende Beispiel ähneln:  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```  
  
 Beachten Sie, dass die beiden Tags link finden Sie Screenshots im Ordner generierten Bilder.  
  
## <a name="see-also"></a>Siehe auch  
 [Private Kataloge](../extensibility/private-galleries.md)
