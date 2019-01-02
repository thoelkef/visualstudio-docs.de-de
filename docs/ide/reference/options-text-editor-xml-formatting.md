---
title: Optionen, Text-Editor, XML, Formatierung
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Formatting
ms.assetid: 203e60b2-7b80-4ff4-9fa1-aa9f4374377b
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 652d9ff3b2178089b4ef35838a4181408aef7f09
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388298"
---
# <a name="options-text-editor-xml-formatting"></a>Optionen, Text-Editor, XML, Formatierung

Verwenden Sie die Eigenschaftenseite **Formatierung**, um anzugeben, wie Elemente und Attribute in Ihren XML-Dokumenten formatiert werden. Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Tools** und anschließend auf **Optionen**. Erweitern Sie für den Zugriff auf die Eigenschaftenseite **Formatierung** den Knoten **Text-Editor** > **XML** > **Formatierung**.

## <a name="attributes"></a>Attribute

**Manuelle Attributformatierung beibehalten**

Formatiert Attribute nicht neu. Dies ist die Standardeinstellung.

> [!NOTE]
> Wenn sich die Attribute auf mehreren Zeilen befinden, zieht der Editor jede Attributzeile ein, sodass das Einzugsmuster des übergeordneten Elements festgelegt wird.

**Attribute jeweils in einer eigenen Zeile ausrichten**

Richtet das zweite und die nachfolgenden Attribute vertikal aus, damit sie dem Einzug des ersten Attributs entsprechen. Der folgende XML-Text veranschaulicht, wie die Attribute ausgerichtet werden.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>Automatisch neu formatieren

**Bei Einfügen aus der Zwischenablage**

Formatiert den aus der Zwischenablage eingefügten XML-Text neu.

**Bei Komplettierung des Endtags**

Formatiert das Element neu, wenn das Endtag vervollständigt wird.

## <a name="mixed-content"></a>	Gemischter Inhalt

**Gemischten Inhalt standardmäßig formatieren**

Es wird versucht, gemischten Inhalt neu zu formatieren, es sei denn, der Inhalt befindet sich in einem `xml:space="preserve"`-Bereich. Dies ist die Standardeinstellung.

Wenn ein Element eine Mischung aus Text und Markup enthält, wird der Inhalt als gemischter Inhalt betrachtet. Es folgt ein Beispiel für ein Element mit gemischtem Inhalt.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>Siehe auch

- [How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation (Visual Basic))](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Codegenerierung](../code-generation-in-visual-studio.md)