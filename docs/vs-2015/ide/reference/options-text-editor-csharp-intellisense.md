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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662295"
---
# <a name="options-text-editor-c-intellisense"></a>Optionen, Text-Editor, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie die Eigenschaftenseite von **IntelliSense**, um Einstellungen zu ändern, die das Verhalten von IntelliSense für Visual C# beeinflussen. Sie rufen die Eigenschaftenseite von **IntelliSense** durch Klicken auf **Optionen** im Menü **Extras** auf. Klicken Sie danach im Ordner **Text-Editor** auf **C#** und anschließend auf **IntelliSense**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Die Eigenschaftenseite von **IntelliSense** enthält folgende Eigenschaften:

## <a name="completion-lists"></a>Vervollständigungslisten
 **Vervollständigungsliste anzeigen, nachdem ein Zeichen eingegeben** wurde Wenn diese Option ausgewählt ist, zeigt IntelliSense automatisch die Vervollständigungsliste an, wenn Sie mit der Eingabe beginnen. Wenn diese Option nicht aktiviert ist, ist die IntelliSense-Vervollständigung trotzdem über das Menü **IntelliSense** oder durch Drücken von STR+LEERTASTE verfügbar.

 **Schlüsselwörter in Vervollständigungs Listen platzieren** Wenn diese Option ausgewählt ist, fügt IntelliSense C# Schlüsselwörter (z. b. [Klasse](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690)) der Vervollständigungsliste hinzu.

 **Code Ausschnitte in Vervollständigungs Listen platzieren** Wenn diese Option ausgewählt ist, fügt IntelliSense Aliase für C# Code Ausschnitte zur Vervollständigungsliste hinzu. Im Fall, dass das Codausschnitt-Alias mit dem Schlüsselwort, z.B. [class](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690) übereinstimmt, wird das Schlüsselwort durch die Verknüpfung ersetzt. Weitere Informationen finden Sie unter [Visual C#-Codeausschnitte](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Auswahl in Vervollständigungslisten
 Commit **durch Eingabe der folgenden Zeichen:** Gibt alle Zeichen an, die die automatische Vervollständigung von IntelliSense für das ausgewählte Element in der Vervollständigungsliste ausführen, nachdem Sie eingegeben wurden.

 Commit **durch Drücken der Leertaste** Gibt an, dass die Aktion für das Drücken der Leertaste zum Ausführen der automatischen IntelliSense-Vervollständigung für das ausgewählte Element in der Vervollständigungsliste einschließt.

 **Fügen Sie am Ende eines vollständig typisierten Worts eine neue Zeile** ein. Wenn Sie alle Zeichen für einen Eintrag in der Vervollständigungsliste eingeben und dann die EINGABETASTE drücken, wird automatisch eine neue Zeile erstellt, und der Cursor wird in die neue Zeile verschoben.

 Wenn Sie beispielsweise `else` eingeben und anschließend die EINGABETASTE drücken, erscheint folgendes im Editor:

 `else`

 `|` (Cursorplatzierung)

 Wenn Sie allerdings nur `el` eingeben und anschließend die EINGABETASTE drücken, erscheint folgendes im Editor:

 `else|` (Cursorplatzierung)

## <a name="intellisense-member-selection"></a>IntelliSense-Memberauswahl
 **Zuletzt verwendetes Element vorab auswählen** Wenn diese Option ausgewählt ist, wählt IntelliSense die Elemente, die Sie vor kurzem im Feld Member der Popup Liste ausgewählt haben, für die automatische Vervollständigung des Objekt namens während der aktuellen Sitzung in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) aus. Der Verlauf der zuletzt verwendeten Member wird nach jeder Sitzung in der Entwicklungsumgebung (IDE) gelöscht. Weitere Informationen finden Sie unter [IntelliSense für die zuletzt verwendeten Member](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Siehe auch
 [Allgemein, Umgebung, Dialog Feld "Optionen](../../ide/reference/general-environment-options-dialog-box.md) " [XML-Dokumentations Kommentare](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [mit IntelliSense](../../ide/using-intellisense.md)
