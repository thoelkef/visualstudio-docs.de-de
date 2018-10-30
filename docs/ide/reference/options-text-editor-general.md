---
title: Optionen, Text-Editor, Allgemein
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
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
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4405e50a2bc264c88c073980da77fafbedf49cbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830664"
---
# <a name="options-text-editor-general"></a>Optionen, Text-Editor, Allgemein

Mit diesem Dialogfeld können Sie Einstellungen für den Code- und -Text-Editor von Visual Studio global ändern. Klicken Sie zum Anzeigen dieses Dialogfelds im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Text-Editor**, und klicken Sie dann auf **Allgemein**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="settings"></a>Einstellungen

### <a name="drag-and-drop-text-editing"></a>Textbearbeitung mit Drag & Drop

Bei Auswahl dieser Option können Sie Text verschieben, indem Sie ihn auswählen und mit der Maus auf eine andere Position innerhalb des aktuellen Dokuments oder eines beliebigen anderen geöffneten Dokument ziehen.

### <a name="automatic-delimiter-highlighting"></a>Trennzeichen automatisch hervorheben

Wenn diese Option aktiviert ist, werden die Trennzeichen, die Parameter oder Element-Wert-Paare trennen, sowie übereinstimmende Klammern hervorgehoben.

### <a name="track-changes"></a>Änderungen nachverfolgen

Wenn der Code-Editor ausgewählt ist, erscheint eine vertikale gelbe Linie im Auswahlrand. Diese markiert Code, der seit der letzten Speicherung der Datei geändert wurde. Wenn Sie die Änderungen speichern, wird die vertikale Linie grün.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>UTF-8-Codierung ohne Signatur automatisch erkennen

Standardmäßig erkennt der Editor Codierung durch Suchen nach Bytereihenfolge-Marken oder Charset-Tags. Wenn keines von beidem im aktuellen Dokument gefunden wird, versucht der Code-Editor, UTF-8-Codierung automatisch durch Scannen von Bytefolgen zu erkennen. Deaktivieren Sie diese Option, um die automatische Erkennung der Codierung zu deaktivieren.

## <a name="display"></a>Anzeige

### <a name="selection-margin"></a>Auswahlrahmen

Wenn diese Option aktiviert ist, wird ein vertikaler Rand am linken Rand des Textbereichs des Editors angezeigt. Sie können auf diesen Rand klicken, um eine ganze Textzeile auszuwählen, oder darauf klicken und ziehen, um aufeinander folgende Textzeilen auszuwählen.

|Auswahlrahmen aktiviert|Auswahlrahmen deaktiviert|
| - | - |
|![HTMLpageSelectionMarginOn-Bildschirmabbildung](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff-Bildschirmabbildung](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Indikatorrand

Wenn diese Option aktiviert ist, wird ein vertikaler Rand außerhalb des linken Randes des Textbereichs des Editors angezeigt. Wenn Sie in diesen Rand klicken, erscheint ein Symbol und eine QuickInfo, die sich auf den angezeigten Text beziehen. Beispielsweise werden im Indikatorrand Verknüpfungen zu Haltepunkt- oder Aufgabenlisten angezeigt. Informationen im Indikatorrand werden nicht gedruckt.

### <a name="vertical-scroll-bar"></a>Vertikale Scrollleiste

Wenn diese Option aktiviert ist, wird eine vertikale Scrollleiste angezeigt, mit der Sie hoch und runter scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine vertikalen Scrollleisten verfügbar sind, können Sie die BILD-AUF- oder BILD-AB-Taste oder Cursortasten verwenden.

### <a name="horizontal-scroll-bar"></a>Horizontale Scrollleiste

Wenn diese Option aktiviert ist, wird eine horizontale Scrollleiste angezeigt, mit der Sie von Seite zu Seite scrollen können, um Elemente anzuzeigen, die außerhalb des Anzeigebereichs des Editors liegen. Wenn keine horizontalen Scrollleisten verfügbar sind, können Sie die Cursortasten verwenden.

### <a name="highlight-current-line"></a>Aktuelle Zeile markieren

Wenn diese Option aktiviert ist, wird ein grauer Rahmen um die Codezeile angezeigt, in der sich der Cursor befindet.

## <a name="see-also"></a>Siehe auch

- [Optionen, Text-Editor, Alle Sprachen](../../ide/reference/options-text-editor-all-languages.md)
- [Optionen, Text-Editor, Alle Sprachen, Registerkarten](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Optionen, Text-Editor, Dateierweiterung](../../ide/reference/options-text-editor-file-extension.md)
- [Identifizieren und Anpassen von Tastenkombinationen](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Anpassen des Editors](../../ide/customizing-the-editor.md)
- [Verwenden von IntelliSense](../../ide/using-intellisense.md)