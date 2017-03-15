---
title: "Optionen, Text-Editor, C#, Formatierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting"
  - "VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing"
  - "VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting"
helpviewer_keywords: 
  - "Formatierung [C#]"
  - "Formatierung [J#]"
  - "Text-Editor-Optionen (Dialogfeld), Formatierung"
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Optionen, Text-Editor, C#, Formatierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie das Dialogfeld mit der Eigenschaftenseite **Formatierung**, um Optionen zur Formatierung von Code im Code\-Editor festzulegen.  Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text\-Editor**, erweitern Sie **C\#**, und klicken Sie dann auf **Formatierung**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Wählen Sie im Menü **Extras** den Eintrag **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Allgemeine Einstellungen  
 Es hängt von den allgemeinen Einstellungen ab, wie Formatierungsoptionen für den Code vom Code\-Editor übernommen werden.  
  
## UIElement-Liste  
  
|Bezeichnung|Beschreibung|  
|-----------------|------------------|  
|**Abgeschlossene Anweisung automatisch formatieren bei ;**|Bei Auswahl dieser Option werden Anweisungen nach der Fertigstellung entsprechend den für den Code\-Editor ausgewählten Formatierungsoptionen formatiert.  Deaktivieren Sie dieses Feld, wenn Anweisungen nicht durch den Code\-Editor geändert werden sollen.|  
|**Abgeschlossenen Block automatisch formatieren bei }**|Bei Auswahl dieser Option werden Codeblöcke entsprechend den für den Code\-Editor ausgewählten Formatierungsoptionen formatiert, sobald der Codeblock abgeschlossen ist.  Deaktivieren Sie dieses Feld, wenn Blöcke nicht durch den Code\-Editor geändert werden sollen.|  
|**Einzug beim Einfügen anpassen**|Bei Auswahl dieser Option wird in den Code\-Editor eingefügter Text entsprechend den für den Code\-Editor ausgewählten Formatierungsoptionen formatiert.  Deaktivieren Sie dieses Feld, wenn eingefügter Text nicht geändert werden soll.|  
  
## Vorschaufenster  
 Die Bereiche, in denen Optionen für **Einzug**, **Neue Zeilen**, **Abstand** und **Umbruch** angezeigt werden, enthalten jeweils ein Vorschaufenster.  Im Vorschaufenster wird die Auswirkung der einzelnen Optionen angezeigt.  Wählen Sie zur Verwendung des Vorschaufensters eine Formatierungsoption aus.  Im Vorschaufenster wird ein Beispiel der ausgewählten Option angezeigt.  Wenn Sie die Einstellung ändern, beispielsweise ein Kontrollkästchen aktivieren oder deaktivieren, wird das Vorschaufenster in Anpassung an die neue Einstellung aktualisiert.  
  
## Hinweise  
 Durch die Einzugsoptionen auf den Seiten **Tabstopps** für die jeweiligen Sprachen wird lediglich festgelegt, an welche Position der Cursor im Code\-Editor gesetzt wird, wenn Sie am Ende einer Zeile die EINGABETASTE drücken.  Die Einzugsoptionen unter **Formatierung** werden bei der automatischen Codeformatierung übernommen, beispielsweise wenn Sie Code bei aktivierter Option **Einzug beim Einfügen anpassen** in die Datei einfügen, und wenn der zu formatierende Block manuell eingegeben wird.  
  
## Siehe auch  
 [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md)