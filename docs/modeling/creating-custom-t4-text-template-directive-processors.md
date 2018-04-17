---
title: Erstellen von benutzerdefinierten T4-Text-Direktivenprozessoren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e55ff7c1c0041e386980b55c9cca7c9263f0b62e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen
Die *Textvorlagen-Transformationsprozess* nimmt eine *Textvorlage* Datei als Eingabe und eine Textdatei als Ausgabe erzeugt. Die *Textvorlagen-Transformationsmodul* Steuerelemente, die der Prozess, und das Modul interagiert mit einem Textvorlagen-Transformationshost und eine oder mehrere Textvorlage *Direktivenprozessoren* um den Vorgang abzuschließen. Weitere Informationen finden Sie unter [der Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md).  
  
 Zum Erstellen eines benutzerdefinierten Direktivenprozessors erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> erbt.  
  
 Der Unterschied zwischen diesen beiden besteht darin, die <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementiert die minimale Schnittstelle ist erforderlich, um Parameter vom Benutzer erhalten und zum Generieren des Codes, der die Vorlagendatei für die Ausgabe erzeugt. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementiert das Entwurfsmuster erfordert/bereitstellt. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> verarbeitet zwei spezielle Parameter `requires` und `provides`.  Z. B. ein benutzerdefinierter Direktivenprozessor möglicherweise akzeptieren einen Dateinamen vom Benutzer, öffnen die Datei nicht lesen und speichern Sie den Text der Datei in einer Variablen mit dem Namen `fileText`. Eine Unterklasse von der <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> Klasse dauern einen Dateinamen vom Benutzer als Wert des der `requires` -Parameter und den Namen der Variablen zum Speichern von Text als Wert für die `provides` Parameter. Dieser Prozessor würde öffnen und Lesen Sie die Datei und klicken Sie dann den Text der Datei in einer angegebenen Variable speichern.  
  
 Bevor Sie einen benutzerdefinierten Direktivenprozessor in einer Textvorlage in Aufrufen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], müssen Sie ihn registrieren.  
  
 Weitere Informationen zur Vorgehensweise beim Hinzufügen des Registrierungsschlüssels finden Sie unter [Bereitstellen einer benutzerdefinierten Direktivenprozessor](../modeling/deploying-a-custom-directive-processor.md).  
  
## <a name="custom-directives"></a>Benutzerdefinierte Richtlinien  
 Eine benutzerdefinierte Direktive sieht folgendermaßen aus:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`  
  
 Sie können einen benutzerdefinierten Direktivenprozessor verwenden, wenn Sie externe Daten oder Ressourcen in einer Textvorlage zugreifen möchten.  
  
 Andere Textvorlagen können die Funktionalität, die ein einzelner Direktivenprozessor bereitstellt, freigeben, sodass Direktivenprozessoren Faktor Code zur Wiederverwendung zu ermöglichen. Die integrierte `include` Richtlinie ist ähnlich, da Sie es, Code verlagern, und teilen Sie diese für andere Textvorlagen verwenden können. Der Unterschied ist, die solche Funktionen verwendet werden, die die `include` Richtlinie bietet, ist unveränderlich und akzeptiert keine Parameter. Wenn die allgemeine Funktionalität zu einer Textvorlage und durch die Vorlage Parameter übergeben werden sollen, müssen Sie einen benutzerdefinierten Direktivenprozessor erstellen.  
  
 Einige Beispiele für benutzerdefinierte Direktivenprozessoren sind möglich:  
  
-   Ein Direktivenprozessor zum Zurückgeben von Daten aus einer Datenbank, das einen Benutzernamen und ein Kennwort als Parameter akzeptiert.  
  
-   Einen Direktivenprozessor öffnen und Lesen einer Datei, die den Namen der Datei als Parameter akzeptiert.  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>Prinzipal Teile eines benutzerdefinierten Direktivenprozessors  
 Um einen Direktivenprozessor zu entwickeln, erstellen Sie eine Klasse, die entweder erbt <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Die wichtigste `DirectiveProcessor` Methoden, die Sie implementieren müssen, sind wie folgt.  
  
-   `bool IsDirectiveSupported(string directiveName)` -Rückgabetyp `true` , wenn der Direktivenprozessor die angegebene Direktive verarbeiten kann.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Das Vorlagenmodul ruft diese Methode für jedes Vorkommen einer Direktive in der Vorlage. Der Prozessor sollte die Ergebnisse zu speichern.  
  
 Nachdem alle Aufrufe an ProcessDirective() wird das Vorlagenmodul diese Methoden aufrufen:  
  
-   `string[] GetReferencesForProcessingRun()` – Gibt die Namen der Assemblys, die der Vorlagencode erfordert zurück.  
  
-   `string[] GetImportsForProcessingRun()` -Geben Sie die Namespaces, die verwendet werden können im Vorlagencode zurück.  
  
-   `string GetClassCodeForProcessingRun()` -Gibt den Code von Methoden, Eigenschaften und anderen Deklarationen, die der Code verwenden können. Die einfachste Möglichkeit hierzu ist eine Zeichenfolge mit c# oder Visual Basic-Code zu erstellen. Stellen Sie den Direktivenprozessor kann aufgerufen werden, aus einer Vorlage, die einer beliebigen CLR-Sprache verwendet, können Sie die Anweisungen als ein CodeDom-Struktur erstellen und dann das Ergebnis der Serialisierung der Struktur in der von der Vorlage verwendeten Sprache zurück.  
  
-   Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen einen benutzerdefinierten Direktivenprozessor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bereitstellen eines benutzerdefinierten Anweisungsprozessors](../modeling/deploying-a-custom-directive-processor.md)  
 Erläutert das Registrieren eines benutzerdefinierten Direktivenprozessors.  
  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Anweisungsprozessors](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Beschreibt Gewusst wie: Erstellen eines benutzerdefiniertes Direktivenprozessors erstellen, registrieren und Testen des Direktivenprozessors komplizierter und wie die Ausgabedatei als HTML formatiert.