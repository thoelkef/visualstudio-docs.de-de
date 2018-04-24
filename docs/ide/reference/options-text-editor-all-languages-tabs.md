---
title: Optionen, Text-Editor, Alle Sprachen, Tabstopps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ded3c11dc1b367489c2a5ff578557b6fb6f6f401
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-all-languages-tabs"></a>Optionen, Text-Editor, Alle Sprachen, Tabstopps
Mit diesem Dialogfeld können Sie das Standardverhalten des Code-Editors ändern. Diese Einstellungen gelten auch für andere Editoren, die auf dem Code-Editor basieren, z.B. die Quellansicht des HTML-Designers. Wählen Sie zum Anzeigen dieser Optionen unter **Tools** den Menüpunkt **Optionen** aus. Erweitern Sie innerhalb des Ordners **Text-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Tabstopps** aus.  
  
> [!CAUTION]
>  Auf dieser Seite werden die Standardoptionen für alle Entwicklungssprachen festgelegt. Denken Sie daran, dass beim Zurücksetzen einer Option in diesem Dialogfeld die Tabstopp-Optionen in allen Sprachen auf die hier ausgewählten Optionen zurückgesetzt werden. Um die Optionen in „Text-Editor“ für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache, und wählen Sie seine Optionsseiten aus.  
  
 Wenn auf den Optionsseiten von „Tabstopps“ für bestimmte Programmiersprachen andere Einstellungen ausgewählt sind, wird die Meldung „Die Einzugseinstellungen für einzelne Textformate stehen miteinander im Konflikt“ für abweichende Optionen unter **Einzug** angezeigt. Die Meldung „Die Tabstoppeinstellungen für einzelne Textformate stehen miteinander im Konflikt“ wird für unterschiedliche **Tabstopps**-Optionen angezeigt. Diese Erinnerung wird beispielsweise angezeigt, wenn die Option **Intelligenter Einzug** für Visual Basic und **Block indenting** (Blockeinzug) für Visual C++ ausgewählt ist.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="indenting"></a>Einzug  
 Keiner  
 Wenn diese Option aktiviert ist, werden neue Zeilen nicht eingezogen. Die Einfügemarke wird in der ersten Spalte einer neuen Zeile platziert.  
  
 Block  
 Wenn diese Option aktiviert ist, werden neue Zeilen automatisch eingezogen. Die Einfügemarke wird am selben Ausgangspunkt wie die vorangehende Zeile platziert.  
  
 Intelligent  
 Wenn diese Option aktiviert ist, werden neue Zeilen mithilfe anderer Codeformateinstellungen und IntelliSense-Konventionen für Ihre Entwicklungssprache entsprechend dem Codekontext positioniert. Diese Option ist nicht für alle Programmiersprachen verfügbar.  
  
 Beispielsweise können Zeilen, die zwischen einer öffnenden geschweiften Klammer ( { ) und einer schließenden geschweiften Klammer ( } ) eingeschlossen sind, automatisch um einen zusätzlichen Tabstopp von der Position der ausgerichteten Klammern aus eingezogen werden.  
  
## <a name="tabs"></a>Registerkarten  
 Tabulatorgröße  
 Legt den Abstand zwischen Tabstopps in Leerzeichen fest. Der Standardwert beträgt vier Leerzeichen.  
  
 Einzugsgröße  
 Legt die Größe eines automatischen Einzugs in Leerzeichen fest. Der Standardwert beträgt vier Leerzeichen. Es werden Tabstoppzeichen, Leerzeichen oder beides eingefügt, um die angegebene Größe auszufüllen.  
  
 Leerzeichen einfügen  
 Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen nur Leerzeichen und keine Tabstoppzeichen eingefügt. Wenn beispielsweise die **Indent size** (Größe des Einzugs) auf 5 festgelegt wird, werden jedes Mal fünf Leerzeichen eingefügt, wenn Sie die TAB-TASTE drücken oder auf der Symbolleiste **Format** auf die Schaltfläche **Einzug vergrößern** klicken.  
  
 Tabstopps beibehalten  
 Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen so viele Tabstoppzeichen wie möglich eingefügt. Jedes Tabstoppzeichen füllt die in **Tabstoppgröße** angegebene Anzahl von Leerzeichen auf. Wenn **Indent size** kein ganzzahliges Vielfaches von **Tabstoppgröße** ist, werden Leerzeichen hinzugefügt, um den Unterschied auszugleichen.  
  
## <a name="see-also"></a>Siehe auch  
 [Optionen, Text-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)   
 [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)