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
ms.openlocfilehash: 1af8ff6f085d744cb58cb3844fced18d3e484494
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673233"
---
# <a name="options-text-editor-xml-formatting"></a>Optionen, Text-Editor, XML, Formatierung
Verwenden Sie die Eigenschaftenseite **Formatierung**, um anzugeben, wie Elemente und Attribute in Ihren XML-Dokumenten formatiert werden. Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Tools** und anschließend auf **Optionen**. Erweitern Sie für den Zugriff auf die Eigenschaftenseite **Formatierung** den Knoten **Text-Editor** > **XML** > **Formatierung**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="attributes"></a>Attribute  
**Manuelle Attributformatierung beibehalten**  
Formatiert Attribute nicht neu. Dies ist die Standardeinstellung.  
  
> [!NOTE]  
>  Wenn sich die Attribute auf mehreren Zeilen befinden, zieht der Editor jede Attributzeile ein, sodass das Einzugsmuster des übergeordneten Elements festgelegt wird.  
  
**Attribute jeweils in einer eigenen Zeile ausrichten**  
Richtet das zweite und die nachfolgenden Attribute vertikal aus, damit sie dem Einzug des ersten Attributs entsprechen. Der folgende XML-Text veranschaulicht, wie die Attribute ausgerichtet werden.  
  
```xml
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
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
\</dir>  
```  
## <a name="see-also"></a>Siehe auch
- [How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation (Visual Basic))](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Codegenerierung](../code-generation-in-visual-studio.md)
  
