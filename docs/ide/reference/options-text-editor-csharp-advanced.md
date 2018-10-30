---
title: Optionen, Text-Editor, C#, Erweitert
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 16c92111fc29071447d4af5e736b881fa7c7a769
ms.sourcegitcommit: e680e8ac675f003ebcc8f8c86e27f54ff38da662
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356742"
---
# <a name="options-text-editor-c-advanced"></a>Optionen, Text-Editor, C#, Erweitert

Mithilfe der Optionsseite **Erweitert** können Sie die Einstellungen für Formatierungen mithilfe des Editors, von Coderefactoring und XML-Dokumentationskommentaren für C# ändern. Wenn Sie auf die Optionsseite zugreifen möchten, klicken Sie auf **Extras** > **Optionen** und anschließend auf **Text-Editor** > **C#** > **Erweitert**.

> [!NOTE]
> Möglicherweise sind nicht alle Optionen hier aufgeführt.

## <a name="analysis"></a>Analyse

- Vollständige Projektmappenanalyse aktivieren

   Aktiviert die Codeanalyse nicht nur für geöffnete Codedateien, sondern für alle Dateien in der Projektmappe. Weitere Informationen finden Sie unter [Full solution analysis (Analyse der gesamten Projektmappe)](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Using-Direktiven

- System-Direktiven beim Sortieren von Using-Direktiven an erster Stelle platzieren

   Wenn ausgewählt, sortiert der Befehl **Using-Anweisungen entfernen und sortieren** im Kontextmenü die `using`-Anweisungen und platziert die „System“namespaces ganz oben in der Liste.

   Vor dem Sortieren:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Nach dem Sortieren:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```
   
- Using-Direktivengruppen trennen

   Wenn ausgewählt, trennt der Befehl **Using-Anweisungen entfernen und sortieren** im Kontextmenü die `using`-Anweisungen, indem er eine leere Zeile zwischen Gruppen von Anweisungen einfügt, die den gleichen Stammnamespace aufweisen.

   Vor dem Sortieren:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```
   
   Nach dem Sortieren:
   
   ```csharp
   using AutoMapper;
   
   using FluentValidation;
   
   using Newtonsoft.Json;
   
   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```
   
- Hinzufügen von using-Direktiven für Typen in Referenzassemblys und NuGet-Paketen 

   Bei Auswahl dieser Option ist eine [Schnellaktion](../quick-actions.md) zum Installieren eines NuGet-Pakets und Hinzufügen einer `using`-Anweisung für nicht referenzierte Typen verfügbar.

   ![Schnellaktion zum Installieren eines NuGet-Pakets in Visual Studio](media/nuget-lightbulb.png)
  
## <a name="highlighting"></a>Markieren

- Verweise auf Symbole unter dem Cursor markieren

   Wenn sich der Cursor innerhalb eines Symbols befindet, oder wenn Sie auf ein Symbol klicken, werden alle Instanzen dieses Symbols in der Codedatei hervorgehoben.

## <a name="outlining"></a>Gliedern

- Beim Öffnen von Dateien in Gliederungsmodus wechseln

   Wenn diese Option aktiviert ist, wird die Codedatei automatisch gegliedert. Hierdurch werden reduzierbare Codeblöcke erstellt. Beim ersten Öffnen einer Datei werden #Region-Blöcke und inaktive Codeblöcke reduziert.

## <a name="editor-help"></a>Editor-Hilfe

- XML-Dokumentationskommentare generieren für ///

   Bei Auswahl dieser Option werden die XML-Elemente für XML-Dokumentationskommentare eingefügt, wenn Sie die `///`-Kommentareinführung eingegeben haben. Weitere Informationen über die XML-Dokumentation finden Sie unter [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Einfügen von XML-Kommentaren für die Generierung der Dokumentation](../../ide/reference/generate-xml-documentation-comments.md)
- [XML-Dokumentationskommentare (C#-Programmierhandbuch)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentieren von Code mit XML-Kommentaren (C#-Leitfaden)](/dotnet/csharp/codedoc)
- [Festlegen von sprachspezifischen Editoroptionen](../../ide/reference/setting-language-specific-editor-options.md)
- [C#-IntelliSense](../../ide/visual-csharp-intellisense.md)
