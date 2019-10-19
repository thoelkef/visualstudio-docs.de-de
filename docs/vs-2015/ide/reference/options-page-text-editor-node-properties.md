---
title: Optionsseite, Eigenschaften des Knotens „Text-Editor“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62dddacaea1846c8e5d5da404ad7a16fde90f209
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662419"
---
# <a name="options-page-text-editor-node-properties"></a>Optionsseite, Eigenschaften des Knotens "Text-Editor"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In diesem Dokument werden einige Seiten (oder Eigenschaftenauflistungen) beschrieben, die der Kategorie **Text-Editor**, `DTE.Properties("TextEditor", <Property Page>)`, des Dialogfelds **Optionen** zugeordnet sind. Den Titel für jeden Unterabschnitt bildet der Aufruf zum Zugriff auf die `Properties`-Auflistung, und die Tabelle in jedem Unterabschnitt führt die Eigenschaften in der Auflistung auf.

 Die Visual Basic-Makros in [Steuern der Einstellungen im Dialogfeld „Optionen“ (Menü „Extras“)](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) veranschaulichen, wie aktuelle Optionen und ihre Werte für die einzelnen Seiten des Dialogfelds **Optionen** angezeigt werden.

## <a name="general"></a>Allgemein
 `DTE.Properties("TextEditor", "General")`

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (boolesch)|Bei `True` wird die Einfügemarke beim Drücken der ESC-TASTE bei einer vorhandenen Auswahl an die Position verschoben, an der die Aktion ausgelöst wurde, die zur Auswahl führte. `False` verschiebt die Einfügemarke an das andere Ende der Auswahl.|
|DragNDropTextEditing|Get/Set (boolesch)|Bestimmt, ob ein ausgewählter Textbereich im Dokument mit der Maus für Kopier- oder Ausschneide-/Einfügevorgänge von einer Position an eine andere gezogen werden kann.|
|HorizontalScrollBar|Get/Set (boolesch)|Bestimmt, ob in Editor-Fenstern eine horizontale Bildlaufleiste angezeigt wird.|
|VerticalScrollBar|Get/Set (boolesch)|Bestimmt, ob in Editor-Fenstern eine vertikale Bildlaufleiste angezeigt wird.|
|SelectionMargin|Get/Set (boolesch)|Bestimmt, ob links vom Textbereich Raum für besondere Auswahlvorgänge, das Anzeigen von Haltepunktsymbolen usw. vorhanden ist.|
|MarginIndicatorBar|Get/Set (boolesch)|Bestimmt, ob eine vertikale Linie angezeigt wird, die den linken Rand des Textbereichs vom Hauptkörper des Textbereichs trennt.|
|UndoCaretActions|Get/Set (boolesch)|Wenn `True`. Rückgängig-Vorgänge umfassen zusätzlich zu den Bearbeitungsaktionen mit Änderungen des Puffers auch die Verschiebung der Einfügemarke, Auswahlbefehle usw.|
|AutoDelimiterHighlighting|Get/Set (boolesch)|Bestimmt, ob die Eingabe eines schließenden Trennzeichens den Editor zum Hervorheben des öffnenden Trennzeichens veranlasst. Der Editor stellt das öffnende Trennzeichen immer fett dar, unabhängig vom Wert dieser Eigenschaft.|
|EditorEmulation|Get/Set (Enumeration)||
|DetectUTF8WithoutSignature|Get/Set (boolesch)|Erkennt, ob eine Datei UTF-8-Codierung verwendet, wenn sie über keine Codierungssignatur verfügt.|
|TrackChanges|Get/Set (boolesch)||

## <a name="plain-text"></a>Nur-Text
 `DTE.Properties("TextEditor", "PlainText")`

 Die `PlainText`-Editoroptionen wirken sich auf die Editoreinstellungen aus, wenn Textdateien bearbeitet werden. Jede Programmiersprache und jedes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Paket weist eigene spezielle Einstellungen für den **Text-Editor** auf. Um beispielsweise die Editoreinstellungen von [!INCLUDE[csprcs](../../includes/csprcs-md.md)] anzuzeigen oder zu ändern, verwenden Sie `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`. Für die Editoreinstellungen von **SQL-Skript** verwenden Sie `DTE.Properties("TextEditor", "SQL ")`.

|Eigenschaftenelementname|Wert|BESCHREIBUNG|
|------------------------|-----------|-----------------|
|AutoListMembers|Get/Set (boolesch)|Bestimmt, ob bei Eingabe eines Punkts hinter einem Variablenverweis automatisch eine Liste der verfügbaren Member angezeigt wird.|
|AutoListParams|Get/Set (boolesch)|Bestimmt, ob bei Eingabe von "(" hinter einem Funktionsnamen automatisch eine Beschreibung einer Argumentliste angezeigt wird.|
|HideAdvancedMembers|Get/Set (boolesch)|Bestimmt, ob die Anweisungsvervollständigung alle Member oder nur die häufig verwendeten auflistet.|
|VirtualSpace|Get/Set (boolesch)|Bestimmt, ob Leerzeichen als Grafik angezeigt werden. Wird dieses Element auf `true` festgelegt, wird das `WordWrap`-Eigenschaftenelement (in dieser Liste) auf `false` festgelegt.|
|WordWrap|Get/Set (boolesch)|Bestimmt, ob die Ansicht bei langen Zeilen an den Wortgrenzen einen Umbruch durchführt. Wird dieses Element auf `true` festgelegt, wird das `VirtualSpace`-Eigenschaftenelement (in dieser Liste) auf `false` festgelegt.|
|WordWrapGlyphs|Get/Set (boolesch)|Zeigt am Ende einer Zeile ein Symbol an, um anzugeben, dass die Zeile in die nächste Zeile umbrochen wird.|
|EnableLeftClickForURLs|Get/Set (boolesch)|Bestimmt, ob der Editor URLs unterstreicht und einen einfachen Mausklick für den Sprung zur URL in dem im System registrierten Webbrowser aktiviert.|
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|Bestimmt den Einrückungsstil: Standard, Smart oder Kein.|
|TabSize|Get/Set (lange ganze Zahl)|Stellt die Anzahl von Leerzeichen dar, die einer Registerkarte entspricht. Bei Auswahl einer ganzen Zahl außerhalb des Bereichs von 1 bis einschließlich 60 schlägt der Vorgang fehl.|
|InsertTabs|Get/Set (boolesch)|Wenn `True`, werden für Einzüge Tabulatorzeichen verwendet.|
|IndentSize|Get/Set (lange ganze Zahl)|Stellt die Anzahl von Leerzeichen dar, die einer Einzugsebene entspricht. Bei Auswahl eines Ganzzahlwerts außerhalb des Bereichs von 1 bis einschließlich 60 schlägt der Vorgang fehl.|
|ShowLineNumbers|Get/Set (boolesch)|Bestimmt, ob bei der Anzeige eines Haupteditordokuments Zeilenzahlen am linken Rand angezeigt werden.|
|ShowNavigationBar|Get/Set (boolesch)|Bestimmt, ob die Dropdownlisten und Schaltflächen in Editorfenstern oben angezeigt werden.|
|CutCopyBlankLines|Get/Set (boolesch)|Schneidet leere Zeilen aus oder kopiert sie, wenn sie ausgewählt werden.|

## <a name="see-also"></a>Siehe auch
 [Steuern von Options Einstellungen](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) [Festlegen der Namen von Eigenschaften Elementen auf Options Seiten](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [Optionen (Optionsseite), Umgebungs Knoten Eigenschaften](../../ide/reference/options-page-environment-node-properties.md) [Optionen Seite, Eigenschaften des Knotens "Schriftarten und Farben](../../ide/reference/options-page-fonts-and-colors-node-properties.md) "
