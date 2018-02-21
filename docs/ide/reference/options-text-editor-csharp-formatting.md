---
title: Optionen, Text-Editor, C#, Formatierung | Microsoft-Dokumentation
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 639082683ad0b65b294307df0740aa4d9c6069d0
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-formatting"></a>Optionen, Text-Editor, C#, Formatierung

Verwenden Sie das Dialogfeld mit der Optionsseite **Formatierung**, um Optionen zur Formatierung von Code im Code-Editor festzulegen. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Extras** > **Optionen** und anschließend auf **Text-Editor** > **C#** > **Codeformat** > **Formatierung**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-settings"></a>Allgemeine Einstellungen

Es hängt von den allgemeinen Einstellungen ab, wie Formatierungsoptionen für den Code vom Code-Editor übernommen werden.

## <a name="uielement-list"></a>UIElement-Liste

|Bezeichnung|description|
|-----------|-----------------|
|**Automatisch während der Eingabe formatieren**|Wenn diese Bezeichnung deaktiviert ist, sind auch die Optionen **Beim Eingeben von ; Anweisung formatieren** und **Bei Eingabe von } Block formatieren** deaktiviert.|
|**Bei Eingabe von ; Anweisung automatisch formatieren**|Bei Auswahl dieser Option werden Anweisungen nach der Fertigstellung entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.|
|**Bei Eingabe von } Block automatisch formatieren**|Bei Auswahl dieser Option werden Codeblöcke entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert, sobald der Codeblock abgeschlossen ist.|
|**Bei Verwendung der EINGABETASTE automatisch formatieren**|Bei Auswahl dieser Option wird Text formatiert, wenn Sie die **EINGABETASTE** drücken, damit dieser den für den Editor aktivierten Formatierungsoptionen entspricht.|
|**Beim Einfügen automatisch formatieren**|Bei Auswahl dieser Option wird in den Editor eingefügter Text entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.|

## <a name="preview-window"></a>Vorschaufenster

Die Bereiche, in denen Optionen für **Einzug**, **Neue Zeilen**, **Abstand** und **Umbruch** angezeigt werden, enthalten jeweils ein Vorschaufenster. Im Vorschaufenster wird die Auswirkung der einzelnen Optionen angezeigt. Wählen Sie zur Verwendung des Vorschaufensters eine Formatierungsoption aus. Im Vorschaufenster wird ein Beispiel der ausgewählten Option angezeigt. Wenn Sie eine Einstellung ändern, indem Sie z.B. ein Optionsfeld oder ein Kontrollkästchen aktivieren oder deaktivieren, wird das Vorschaufenster in Anpassung an diese neue Einstellung aktualisiert.

## <a name="remarks"></a>Hinweise

Durch die Einzugsoptionen auf den Seiten **Tabstopps** für die jeweiligen Sprachen wird lediglich festgelegt, an welche Position der Cursor im Code-Editor gesetzt wird, wenn Sie am Ende einer Zeile die **EINGABETASTE** drücken. Die Einzugsoptionen unter **Formatierung** werden bei der automatischen Codeformatierung übernommen, beispielsweise wenn Sie Code bei aktivierter Option **Beim Einfügen automatisch formatieren** in die Datei einfügen, und wenn der zu formatierende Block manuell eingegeben wird.

## <a name="see-also"></a>Siehe auch

[Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md)
