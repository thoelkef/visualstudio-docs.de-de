---
title: Optionen, Text-Editor, C#, Erweitert | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5d6cf8b655151e9b07111b6ac6fd64b6ad3c845f
ms.sourcegitcommit: 238cd48787391aa0ed1eb684f3f04e80f7958705
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2018
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert

Mithilfe der Optionsseite **Erweitert** können Sie die Einstellungen für Formatierungen mithilfe des Editors, von Coderefactoring und XML-Dokumentationskommentaren für C# ändern. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Extras** > **Optionen** und anschließend auf **Text-Editor** > **C#** > **Erweitert**.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Analyse

- Vollständige Projektmappenanalyse aktivieren

   Aktiviert die Codeanalyse nicht nur für geöffnete Codedateien, sondern für alle Dateien in der Projektmappe. Weitere Informationen finden Sie unter [Full solution analysis (Analyse der gesamten Projektmappe)](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

- Ausführen der Editor-Featureanalyse in einem externen Prozess (experimentell)

## <a name="using-directives"></a>Using-Direktiven

- System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren

- Using-Direktivengruppen trennen

- Using-Direktiven für Typen in Verweisassemblys vorschlagen

- Using-Direktiven für Typen in NuGet-Paketen vorschlagen

## <a name="highlighting"></a>Markieren

- Verweise auf Symbole unter dem Cursor markieren

   Wenn sich der Cursor innerhalb eines Symbols befindet, oder wenn Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.

- Zugehörige Schlüsselwörter unter dem Cursor hervorheben

## <a name="outlining"></a>Gliedern

- Beim Öffnen von Dateien in Gliederungsmodus wechseln

   Wenn diese Option aktiviert ist, wird die Codedatei automatisch gegliedert. Hierdurch werden reduzierbare Codeblöcke erstellt. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.

- Zeilentrennzeichen zwischen Prozeduren anzeigen

- Gliederung für Konstrukte auf Deklarationsebene anzeigen

- Gliederung für Konstrukte auf Codeebene anzeigen

- Gliederung für Kommentare und Präprozessorregionen anzeigen

- #regions beim Reduzieren auf Definitionen zuklappen

## <a name="fading"></a>Ausblenden

- Nicht verwendete Using-Direktiven ausblenden

- Unerreichbaren Code ausblenden

## <a name="block-structure-guides"></a>Führungslinien für Blockstruktur

- Führungslinien für Konstrukte auf Deklarationsebene anzeigen

- Führungslinien für Konstrukte auf Codeebene anzeigen

## <a name="editor-help"></a>Editor-Hilfe

- XML-Dokumentationskommentare generieren für ///

   Bei Auswahl dieser Option werden die XML-Elemente für XML-Dokumentationskommentare eingefügt, wenn Sie die `///`-Kommentareinführung eingegeben haben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Beim Schreiben von Kommentaren /\* \*/ \* am Beginn neuer Zeilen einfügen

- Vorschau für Nachverfolgung beim Umbenennen anzeigen

- Zeichenfolgenliterale bei Eingabe teilen

- Ungültige Platzhalter in string.Format-Aufrufen melden

## <a name="extract-method"></a>Methode extrahieren

- Don't put ref or out on custom struct (Nicht „ref“ oder „out“ auf benutzerdefinierte Struktur anfügen)

## <a name="implement-interface-or-abstract-class"></a>Schnittstelle oder abstrakte Klasse implementieren

- Eigenschaften, Ereignisse und Methoden zusammen mit anderen Members derselben Art oder am Ende einfügen

- Beim Generieren von Eigenschaften vorzugsweise Eigenschaften oder automatische Eigenschaften auslösen

## <a name="see-also"></a>Siehe auch

[Vorgehensweise: Einfügen von XML-Kommentaren für die Generierung der Dokumentation](../../ide/reference/generate-xml-documentation-comments.md)  
[XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[Documenting your code with XML comments (C# Guide) (Dokumentieren von Code mit XML-Kommentaren (C#-Handbuch))](/dotnet/csharp/codedoc)  
[Festlegen von sprachspezifischen Editoroptionen](../../ide/reference/setting-language-specific-editor-options.md)  
[C#-IntelliSense](../../ide/visual-csharp-intellisense.md)