---
title: "Optionen, Text-Editor, Alle Sprachen, Registerkarten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs"
  - "VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs"
helpviewer_keywords: 
  - "Einzüge, Code-Editor"
  - "Code-Editor, Standardverhalten"
  - "Registerkarten, Festlegen im Code-Editor"
  - "Alle Sprachen (Text-Editor im Dialogfeld Optionen)"
  - "Editoren, Code-Editor"
  - "Code-Editor, Einzug"
  - "Code-Editor, Registerkarten"
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Optionen, Text-Editor, Alle Sprachen, Registerkarten
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie das Standardverhalten des Code\-Editors ändern.  Diese Einstellungen betreffen auch andere Editoren, die auf dem Code\-Editor basieren, z. B. die Quellansicht des HTML\-Designers.  Klicken Sie im Menü **Extras** auf **Optionen**, um diese Optionen anzuzeigen.  Erweitern Sie im Ordner **Text\-Editor** den Unterordner **Alle Sprachen**, und wählen Sie dann **Tabstopps** aus.  
  
> [!CAUTION]
>  Auf dieser Seite werden Standardoptionen für alle Entwicklungssprachen festgelegt.  Beachten Sie, dass durch das Zurücksetzen einer Option in diesem Dialogfeld die Optionen unter Tabstopps unabhängig von den dort aktivierten Optionen für alle Programmiersprachen zurückgesetzt werden.  Um Text\-Editor\-Optionen für nur eine Sprache zu ändern, erweitern Sie den Unterordner für diese Sprache und wählen die zugehörigen Optionsseiten aus.  
  
 Wenn auf den Optionsseiten für Tabstopps unterschiedliche Einstellungen für bestimmte Programmiersprachen ausgewählt sind, wird für abweichende Optionen unter **Einzug** die Meldung "Die Einzugseinstellungen für einzelne Textformate stehen miteinander im Konflikt" und für abweichende Optionen unter **Tabstopps** die Meldung "Die Tabstoppeinstellungen für einzelne Textformate stehen miteinander im Konflikt" eingeblendet.  Beispielsweise wird eine solche Erinnerung angezeigt, wenn für Visual Basic die Option **Intelligenter Einzug** und für Visual C\+\+ die Option **Blockeinzug** ausgewählt wurde.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Einzug  
 None  
 Wenn diese Option aktiviert ist, werden neue Zeilen nicht eingezogen.  Die Einfügemarke wird in der ersten Spalte einer neuen Zeile platziert.  
  
 Block  
 Wenn diese Option aktiviert ist, werden neue Zeilen automatisch eingezogen.  Die Einfügemarke wird an demselben Ausgangspunkt wie die vorangehende Zeile platziert.  
  
 Intelligent  
 Wenn diese Option aktiviert ist, werden neue Zeilen in Anpassung an den Codekontext mittels anderer Einstellungen für die Codeformatierung sowie gemäß IntelliSense\-Konventionen für die Entwicklungssprache positioniert.  Diese Option ist nicht für alle Entwicklungssprachen verfügbar.  
  
 Beispielsweise können Zeilen, die zwischen einer öffnenden geschweiften Klammer \( { \) und einer schließenden geschweiften Klammer \( } \) eingeschlossen sind, automatisch um einen zusätzlichen Tabstopp von der Position der ausgerichteten Klammern aus eingezogen werden.  
  
## Tabstopps  
 Tabulatorgröße  
 Legt den Abstand zwischen Tabstopps in Leerzeichen fest.  Vorgegeben sind vier Leerzeichen.  
  
 Einzugsgröße  
 Legt die Größe eines automatischen Einzugs in Leerzeichen fest.  Vorgegeben sind vier Leerzeichen.  Es werden Tabstoppzeichen, Leerzeichen oder beides eingefügt, um die angegebene Größe auszufüllen.  
  
 Leerzeichen einfügen  
 Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen nur Leerzeichen und keine Tabstoppzeichen eingefügt.  Wenn beispielsweise **Einzugsgröße** auf 5 festgelegt wird, werden jedes Mal fünf Leerzeichen eingefügt, sobald Sie die TAB\-TASTE drücken oder auf der Symbolleiste **Format** auf die Schaltfläche **Einzug vergrößern** klicken.  
  
 Tabulatoren beibehalten  
 Wenn diese Option aktiviert ist, werden bei Einzugsvorgängen so viele Tabstoppzeichen wie möglich eingefügt.  Jedes Tabulatorzeichen füllt die in **Tabulatorgröße** angegebene Anzahl von Leerzeichen auf.  Wenn **Einzugsgröße** kein ganzzahliges Vielfaches von **Tabulatorgröße** ist, werden Leerzeichen hinzugefügt, um den Unterschied auszugleichen.  
  
## Siehe auch  
 [Optionen, Text\-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)   
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)