---
title: Optionen, Text-Editor, C#, IntelliSense | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dc4d918f3eae9088e2b36b7bebbb69ce130e26d9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674142"
---
# <a name="options-text-editor-c-intellisense"></a>Optionen, Text-Editor, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Eigenschaftenseite von **IntelliSense**, um Einstellungen zu ändern, die das Verhalten von IntelliSense für Visual C# beeinflussen. Sie rufen die Eigenschaftenseite von **IntelliSense** durch Klicken auf **Optionen** im Menü **Extras** auf. Klicken Sie danach im Ordner **Text-Editor** auf **C#** und anschließend auf **IntelliSense**.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Die Eigenschaftenseite von **IntelliSense** enthält folgende Eigenschaften:  
  
## <a name="completion-lists"></a>Vervollständigungslisten  
 **Vervollständigungsliste nach Eingabe des ersten Zeichens anzeigen**  
 Wenn diese Option aktiviert ist, zeigt IntelliSense automatisch die Vervollständigungsliste an, wenn Sie mit der Eingabe beginnen. Wenn diese Option nicht aktiviert ist, ist die IntelliSense-Vervollständigung trotzdem über das Menü **IntelliSense** oder durch Drücken von STR+LEERTASTE verfügbar.  
  
 **Schlüsselwörter in Vervollständigungslisten platzieren**  
 Wenn diese Option aktiviert ist, fügt IntelliSense C#-Schlüsselwörter zur Vervollständigungsliste hinzu, z.B. [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690).  
  
 **Codeausschnitte in Vervollständigungslisten platzieren**  
 Wenn diese Option aktiviert ist, fügt IntelliSense Aliase für C#-Codeausschnitte zur Vervollständigungsliste hinzu. Im Fall, dass das Codausschnitt-Alias mit dem Schlüsselwort, z.B. [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690) übereinstimmt, wird das Schlüsselwort durch die Verknüpfung ersetzt. Weitere Informationen finden Sie unter [Visual C#-Codeausschnitte](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Auswahl in Vervollständigungslisten  
 **Commit bei Eingabe der folgenden Zeichen:**  
 Gibt alle Zeichen an, die nach der Eingabe die automatische Vervollständigung von IntelliSense für das ausgewählte Element in der Vervollständigungsliste ausführen.  
  
 **Commit beim Drücken der Leertaste**  
 Gibt an, dass durch Drücken der LEERTASTE die automatische Vervollständigung von IntelliSense für das ausgewählte Element in der Vervollständigungsliste ausgeführt werden soll.  
  
 **Mit Eingabe neue Zeile nach jedem ganzen Wort**  
 Gibt an, dass nach Eingabe aller Zeichen für einen Eintrag in der Vervollständigungsliste und Drücken der EINGABETASTE automatisch eine neue Zeile erstellt wird und der Cursor zur neuen Zeile springt.  
  
 Wenn Sie beispielsweise `else` eingeben und anschließend die EINGABETASTE drücken, erscheint folgendes im Editor:  
  
 `else`  
  
 `|` (Cursorplatzierung)  
  
 Wenn Sie allerdings nur `el` eingeben und anschließend die EINGABETASTE drücken, erscheint folgendes im Editor:  
  
 `else|` (Cursorplatzierung)  
  
## <a name="intellisense-member-selection"></a>IntelliSense-Memberauswahl  
 **Pre-selects most recently used member** (Vorauswahl der zuletzt verwendeten Member)  
 Wenn diese Option aktiviert ist, trifft IntelliSense in Ihrer aktuellen Sitzung in der integrierten Entwicklungsumgebung (IDE) eine Vorauswahl der Member, die Sie kürzlich im Popupfeld „Member auflisten“ zur automatischen Vervollständigung des Objektnamen ausgewählt haben. Der Verlauf der zuletzt verwendeten Member wird nach jeder Sitzung in der Entwicklungsumgebung (IDE) gelöscht. Weitere Informationen finden Sie unter [IntelliSense für die zuletzt verwendeten Member](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Allgemein, Umgebung, Dialogfeld „Optionen“](../../ide/reference/general-environment-options-dialog-box.md)   
 [XML-Dokumentationskommentare](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)
