---
title: Optionen, Text-Editor, Alle Sprachen, Tabstopps | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662382"
---
# <a name="options-text-editor-all-languages-tabs"></a>Optionen, Text-Editor, Alle Sprachen, Tabstopps
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Wählen Sie zum Anzeigen dieser Optionen unter **Tools** den Menüpunkt **Optionen** aus. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Tabstopps** aus.

> [!CAUTION]
> Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die Tabstopp-Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen in „Text-Editor“ für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.

 Wenn auf den Optionsseiten von „Tabstopps“ für bestimmte Programmiersprachen andere Einstellungen ausgewählt sind, wird die Meldung „Die Einzugseinstellungen für einzelne Textformate stehen miteinander im Konflikt“ für abweichende Optionen unter **Einzug** angezeigt. Die Meldung „Die Tabstoppeinstellungen für einzelne Textformate stehen miteinander im Konflikt“ wird für unterschiedliche **Tabstopps**-Optionen angezeigt. Diese Erinnerung wird beispielsweise angezeigt, wenn die Option **Intelligenter Einzug** für Visual Basic und **Block indenting** (Blockeinzug) für Visual C++ ausgewählt ist.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Einzug
 Keine, wenn diese Option ausgewählt ist, werden neue Zeilen nicht eingezogen. Die Einfügemarke wird in der ersten Spalte einer neuen Zeile platziert.

 Wenn diese Option aktiviert ist, werden neue Zeilen automatisch eingezogen. Die Einfügemarke wird am selben Ausgangspunkt wie die vorangehende Zeile platziert.

 Smart: Wenn diese Option aktiviert ist, werden neue Zeilen mithilfe anderer Codeformateinstellungen und IntelliSense-Konventionen für Ihre Entwicklungssprache entsprechend dem Codekontext positioniert. Diese Option ist nicht für alle Programmiersprachen verfügbar.

 Beispielsweise können Zeilen, die zwischen einer öffnenden geschweiften Klammer ( { ) und einer schließenden geschweiften Klammer ( } ) eingeschlossen sind, automatisch um einen zusätzlichen Tabstopp von der Position der ausgerichteten Klammern aus eingezogen werden.

## <a name="tabs"></a>Registerkarten
 Tabulator Größe legt den Abstand zwischen Tabstopps in Leerzeichen fest. Der Standardwert beträgt vier Leerzeichen.

 Einzugs Größe legt die Größe eines automatischen Einzugs in Leerzeichen fest. Der Standardwert beträgt vier Leerzeichen. Es werden Tabstoppzeichen, Leerzeichen oder beides eingefügt, um die angegebene Größe auszufüllen.

 Leerzeichen einfügen wenn diese Option aktiviert ist, werden bei Einzugs Vorgängen nur Leerzeichen und keine Tabstopp Zeichen eingefügt. Wenn beispielsweise die **Indent size** (Größe des Einzugs) auf 5 festgelegt wird, werden jedes Mal fünf Leerzeichen eingefügt, wenn Sie die TAB-TASTE drücken oder auf der Symbolleiste **Format** auf die Schaltfläche **Einzug vergrößern** klicken.

 Wenn Sie Registerkarten beibehalten, werden bei Einzugs Vorgängen so viele Tabstopp Zeichen wie möglich eingefügt. Jedes Tabstoppzeichen füllt die in **Tabstoppgröße** angegebene Anzahl von Leerzeichen auf. Wenn **Indent size** kein ganzzahliges Vielfaches von **Tabstoppgröße** ist, werden Leerzeichen hinzugefügt, um den Unterschied auszugleichen.

## <a name="see-also"></a>Siehe auch
 [Optionen, Text-Editor, alle Sprachen](../../ide/reference/options-text-editor-all-languages.md) [Allgemein, Umgebung, Dialog Feld "Optionen](../../ide/reference/general-environment-options-dialog-box.md) "
