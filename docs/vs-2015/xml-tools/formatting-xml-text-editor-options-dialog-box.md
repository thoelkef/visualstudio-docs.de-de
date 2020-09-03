---
title: Formatierung, XML, Text-Editor, Dialog Feld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 962321a1ab1a1ca5332300eea0d21781a9e4bbf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670974"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formatierung, XML, Texteditor, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Formatierungseinstellungen für den XML-Editor festlegen. Sie können über das Menü **Extras** auf das Dialogfeld **Optionen** zugreifen.

> [!NOTE]
> Zum Anzeigen dieser Einstellungen wählen Sie zunächst den Ordner **Text-Editor** und anschließend den Ordner **XML** aus. Wählen Sie dann im Dialogfeld **Optionen** die Option **Formatierung** aus.

## <a name="attributes"></a>Attribute
 **Manuelle Attribut Formatierung beibehalten** Attribute werden nicht neu formatiert. Dies ist die Standardoption.

> [!NOTE]
> Wenn die Attribute auf mehrere Zeilen verteilt sind, richtet der Editor jede Attributzeile am Einzug des jeweils übergeordneten Elements aus.

 **Attribute jeweils in einer eigenen Zeile ausrichten** Richtet das zweite und die nachfolgenden Attribute vertikal aus, sodass Sie dem Einzug des ersten Attributs entsprechen. Der folgende XML-Text verkörpert ein Beispiel für die Ausrichtung der Attribute.

```
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatisch neu formatieren
 **Beim Einfügen aus der Zwischenablage** Formatiert den aus der Zwischenablage eingefügten XML-Text neu.

 **Beim Abschluss des Endtags** Formatiert das Element neu, wenn das Endtag abgeschlossen ist.

## <a name="mixed-content"></a>Gemischter Inhalt
 **Gemischten Inhalt standardmäßig beibehalten** Bestimmt, ob der Editor gemischte Inhalte neu formatiert. Der Editor versucht standardmäßig, gemischten Inhalt neu zu formatieren, es sei denn, der Inhalt befindet sich in einem `xml:space="preserve"`-Gültigkeitsbereich.

 Wenn ein Element sowohl Text als auch Markup enthält, wird sein Inhalt wie gemischter Inhalt behandelt. Es folgt als Beispiel ein Element mit gemischtem Inhalt.

```
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumenteigenschaften, Eigenschaften Fenster](../xml-tools/xml-document-properties-properties-window.md) - [XML-Editor-Komponenten](../xml-tools/xml-editor-components.md)
