---
title: Optionen, Text-Editor, Allgemein | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b33fb6408bc9d37d7f0c94af9253a1ce9879235a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441322"
---
# <a name="options-text-editor-general"></a>Optionen, Text-Editor, Allgemein
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit diesem Dialogfeld können Sie Einstellungen für den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Code- und -Text-Editor global ändern. Klicken Sie zum Anzeigen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, und klicken Sie dann auf **Allgemein**.  
  
> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Einstellungen  
 Textbearbeitung mit Drag & Drop  
 Bei Auswahl dieser Option können Sie Text verschieben, indem Sie ihn auswählen und mit der Maus auf eine andere Position innerhalb des aktuellen Dokuments oder eines beliebigen anderen geöffneten Dokument ziehen.  
  
 Trennzeichen automatisch hervorheben  
 Wenn diese Option aktiviert ist, werden die Trennzeichen, die Parameter oder Element-Wert-Paare trennen, sowie übereinstimmende Klammern hervorgehoben.  
  
 Änderungen nachverfolgen  
 Wenn der Code-Editor ausgewählt ist, erscheint eine vertikale gelbe Linie im Auswahlrand. Diese markiert Code, der seit der letzten Speicherung der Datei geändert wurde. Wenn Sie die Änderungen speichern, wird die vertikale Linie grün.  
  
 UTF-8-Codierung ohne Signatur automatisch erkennen  
 Standardmäßig erkennt der Editor Codierung durch Suchen nach Bytereihenfolge-Marken oder Charset-Tags. Wenn keines von beidem im aktuellen Dokument gefunden wird, versucht der Code-Editor, UTF-8-Codierung automatisch durch Scannen von Bytefolgen zu erkennen. Deaktivieren Sie diese Option, um die automatische Erkennung der Codierung zu deaktivieren.  
  
## <a name="display"></a>Anzeige  
 Auswahlrahmen  
 Wenn diese Option aktiviert ist, wird ein vertikaler Rand am linken Rand des Textbereichs des Editors angezeigt. Sie können auf diesen Rand klicken, um eine ganze Textzeile auszuwählen, oder darauf klicken und ziehen, um aufeinander folgende Textzeilen auszuwählen.  
  
|Auswahlrahmen aktiviert|Auswahlrahmen deaktiviert|  
|-------------------------|--------------------------|  
|![HTMLpageSelectionMarginOn-Bildschirmabbildung](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff-Bildschirmabbildung](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Indikatorrand  
 Wenn diese Option aktiviert ist, wird ein vertikaler Rand außerhalb des linken Randes des Textbereichs des Editors angezeigt. Wenn Sie in diesen Rand klicken, erscheint ein Symbol und eine QuickInfo, die sich auf den angezeigten Text beziehen. Beispielsweise werden im Indikatorrand Verknüpfungen zu Haltepunkt- oder Aufgabenlisten angezeigt. Informationen im Indikatorrand werden nicht gedruckt.  
  
 Vertikale Scrollleiste  
 Wenn diese Option aktiviert ist, wird eine vertikale Scrollleiste angezeigt, mit der Sie hoch und runter scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine vertikalen Scrollleisten verfügbar sind, können Sie die BILD-AUF- oder BILD-AB-Taste oder Cursortasten verwenden.  
  
 Horizontale Scrollleiste  
 Wenn diese Option aktiviert ist, wird eine horizontale Scrollleiste angezeigt, mit der Sie von Seite zu Seite scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine horizontalen Scrollleisten verfügbar sind, können Sie die Cursortasten verwenden.  
  
 Aktuelle Zeile markieren  
 Wenn diese Option aktiviert ist, wird ein grauer Rahmen um die Codezeile angezeigt, in der sich der Cursor befindet.  
  
## <a name="see-also"></a>Siehe auch  
 [Optionen, Text-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)   
 [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Optionen, Text-Editor, Dateierweiterung](../../ide/reference/options-text-editor-file-extension.md)   
 [Identifizieren und Anpassen von Tastenkombinationen](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Anpassen des Editors](../../ide/customizing-the-editor.md)   
 [Verwenden von IntelliSense](../../ide/using-intellisense.md)
