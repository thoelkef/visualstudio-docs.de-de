---
title: Optionen, Text-Editor, C#, Formatierung | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18cf7c7ee9c7f40231482b7c0466929bd0290fb1
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2017
---
# <a name="options-text-editor-c-formatting"></a>Optionen, Text-Editor, C#, Formatierung
Verwenden Sie das Dialogfeld mit der Eigenschaftenseite **Formatierung**, um Optionen zur Formatierung von Code im Code-Editor festzulegen. Klicken Sie zum Öffnen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, erweitern Sie **C#**, und klicken Sie dann auf **Formatierung**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-settings"></a>Allgemeine Einstellungen  
 Es hängt von den allgemeinen Einstellungen ab, wie Formatierungsoptionen für den Code vom Code-Editor übernommen werden.  
  
## <a name="uielement-list"></a>UIElement-Liste  
  
|Bezeichnung|Beschreibung|  
|-----------|-----------------|  
|**Abgeschlossene Anweisung automatisch formatieren bei ;**|Bei Auswahl dieser Option werden Anweisungen nach der Fertigstellung entsprechend den für den Code-Editor ausgewählten Formatierungsoptionen formatiert. Deaktivieren Sie dieses Feld, wenn Anweisungen nicht durch den Code-Editor geändert werden sollen.|  
|**Abgeschlossenen Block automatisch formatieren bei }**|Bei Auswahl dieser Option werden Codeblöcke entsprechend den für den Code-Editor ausgewählten Formatierungsoptionen formatiert, sobald der Codeblock abgeschlossen ist. Deaktivieren Sie dieses Feld, wenn Blöcke nicht durch den Code-Editor geändert werden sollen.|  
|**Einzug beim Einfügen anpassen**|Bei Auswahl dieser Option wird in den Code-Editor eingefügter Text entsprechend den für den Code-Editor ausgewählten Formatierungsoptionen formatiert. Deaktivieren Sie dieses Feld, wenn eingefügter Text nicht geändert werden soll.|  
  
## <a name="preview-window"></a>Vorschaufenster  
 Die Bereiche, in denen Optionen für **Einzug**, **Neue Zeilen**, **Abstand** und **Umbruch** angezeigt werden, enthalten jeweils ein Vorschaufenster. Im Vorschaufenster wird die Auswirkung der einzelnen Optionen angezeigt. Wählen Sie zur Verwendung des Vorschaufensters eine Formatierungsoption aus. Im Vorschaufenster wird ein Beispiel der ausgewählten Option angezeigt. Wenn Sie die Einstellung ändern, beispielsweise ein Kontrollkästchen aktivieren oder deaktivieren, wird das Vorschaufenster in Anpassung an die neue Einstellung aktualisiert.  
  
## <a name="remarks"></a>Hinweise  
 Durch die Einzugsoptionen auf den Seiten **Tabstopps** für die jeweiligen Sprachen wird lediglich festgelegt, an welche Position der Cursor im Code-Editor gesetzt wird, wenn Sie am Ende einer Zeile die EINGABETASTE drücken. Die Einzugsoptionen unter **Formatierung** werden bei der automatischen Codeformatierung übernommen, beispielsweise wenn Sie Code bei aktivierter Option **Einzug beim Einfügen anpassen** in die Datei einfügen, und wenn der zu formatierende Block manuell eingegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)