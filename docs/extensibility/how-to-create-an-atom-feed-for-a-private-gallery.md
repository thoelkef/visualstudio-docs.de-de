---
title: 'Gewusst wie: Erstellen eines Atomfeeds für eine private Galerie | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711015"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Gewusst wie: Erstellen eines Atom-Feeds für eine private Galerie
Sie können einen Atom-Feed (RSS) an einem Intranetspeicherort erstellen, der Erweiterungen enthält, und den Feed **zu Erweiterungen und Updates** als private Galerie hinzufügen. Weitere Informationen finden Sie unter [Private Kataloge](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Erstellen eines Atom-Feeds
 Um einen Atom-Feed als private Galerie zu erstellen, sammeln Sie zuerst Ihre Erweiterungen (*.vsix-Dateien)* in einem Ordner. Sie können sie in Unterordnern organisieren, wenn Sie möchten. Außerdem benötigen Sie die folgenden Ressourcen:

- Eine *atom.xml-Datei,* die die Erweiterungen als private Galerie verfügbar macht. Informationen zum Verbinden der *datei atom.xml* mit **Erweiterungen und Updates**finden Sie unter Private [Galerien](../extensibility/private-galleries.md).

- Ein Ordner, der alle Bilddateien enthält, die aus den Erweiterungen extrahiert wurden (z. B. Screenshots). Die *Datei atom.xml* enthält relative Links zu diesen Bildern, sodass sie in **Erweiterungen und Updates**verfügbar sind.

  Angenommen, Sie haben die folgenden beiden Erweiterungen in einem Ordner gesammelt:

- *Template_Wizard_239.vsix*, bei dem es sich um eine leere VSIX-Projektvorlage handelt.

- *SelectionHighlight.vsix*, ein Werkzeug zum Hervorheben aller Instanzen eines ausgewählten Wortes.

  Der Inhalt der *Datei atom.xml* würde dem folgenden Beispiel ähneln:

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

 Beachten Sie, dass sich die beiden Link-Tags auf Screenshots im generierten Bildordner beziehen.

## <a name="see-also"></a>Weitere Informationen
- [Private Galerien](../extensibility/private-galleries.md)
