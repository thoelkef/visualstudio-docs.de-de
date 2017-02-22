---
title: "Creating Custom T4 Text Template Directive Processors | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, custom directive processors"
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Creating Custom T4 Text Template Directive Processors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim *Textvorlagen\-Transformationsprozess* wird aus einer *Textvorlagendatei* \(Eingabe\) eine Textdatei \(Ausgabe\) erzeugt.  Das *Textvorlagen\-Transformationsmodul* steuert den Prozess und interagiert mit einem Textvorlagen\-Transformationshost und einem oder mehreren Textvorlagen\-*Direktivenprozessoren*, um den Prozess auszuführen.  Weitere Informationen finden Sie unter [The Text Template Transformation Process](../modeling/the-text-template-transformation-process.md).  
  
 Zum Erstellen eines benutzerdefinierten Direktivenprozessors erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> erbt.  
  
 Der Unterschied zwischen diesen beiden Klassen besteht darin, dass <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> die minimale Schnittstelle implementiert, die notwendig ist, um Parameter vom Benutzer abzurufen und den Code zum Erzeugen der Vorlagenausgabedatei zu generieren.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementiert das requires\/provides\-Entwurfsmuster.  <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> verarbeitet zwei spezielle Parameter, `requires` und `provides`.  Ein benutzerdefinierter Direktivenprozessor könnte z. B. einen Dateinamen vom Benutzer akzeptieren, die Datei öffnen und lesen und den Text der Datei dann in einer Variable namens `fileText` speichern.  Eine Unterklasse der <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>\-Klasse könnte einen Dateinamen vom Benutzer als Wert des `requires`\-Parameters und den Name der Variable, in der der Text gespeichert werden soll, als Wert des `provides`\-Parameters akzeptieren.  Dieser Prozessor würde die Datei öffnen und lesen und den Text der Datei dann in der angegebenen Variable speichern.  
  
 Bevor Sie einen benutzerdefinierten Direktivenprozessor in einer Textvorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aufrufen, müssen Sie ihn registrieren.  
  
 Weitere Informationen zum Hinzufügen des Registrierungsschlüssels finden Sie unter [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md).  
  
## Benutzerdefinierte Direktiven  
 Eine benutzerdefinierte Direktive sieht wie folgt aus:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 Sie können einen benutzerdefinierten Direktivenprozessor verwenden, wenn Sie in einer Textvorlage auf externe Daten oder Ressourcen zugreifen möchten.  
  
 Die von einem Direktivenprozessor bereitgestellte Funktion kann freigegeben und für unterschiedliche Textvorlagen verwendet werden. Direktivenprozessoren bieten daher die Möglichkeit, Code zur Wiederverwendung zu zerlegen.  Die integrierte `include`\-Direktive funktioniert ähnlich, da damit Code zerlegt und für unterschiedliche Textvorlagen verwendet werden kann.  Der Unterschied besteht darin, dass von der `include`\-Direktive bereitgestellte Funktionen korrigiert werden und keine Parameter akzeptieren.  Wenn Sie eine allgemeine Funktion für eine Textvorlage bereitstellen möchten und durch die Vorlage Parameter übergeben werden sollen, müssen Sie einen benutzerdefinierten Direktivenprozessor erstellen.  
  
 Beispiele für die Verwendung von benutzerdefinierten Direktivenprozessoren:  
  
-   Ein Direktivenprozessor zum Zurückgeben von Daten aus einer Datenbank, der einen Benutzernamen und ein Kennwort als Parameter akzeptiert  
  
-   Ein Direktivenprozessor zum Öffnen und Lesen einer Datei, der den Namen der Datei als Parameter akzeptiert  
  
### Hauptbestandteile eines benutzerdefinierten Direktivenprozessors  
 Zum Entwickeln eines benutzerdefinierten Direktivenprozessors müssen Sie eine Klasse erstellen, die von <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> erbt.  
  
 Die beiden folgenden `DirectiveProcessor`\-Methoden sind bei dieser Implementierung am wichtigsten.  
  
-   `bool IsDirectiveSupported(string directiveName)` – Gibt `true` zurück, wenn der Direktivenprozessor die angegebene Direktive verarbeiten kann.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` – Das Vorlagenmodul ruft diese Methode für jedes Vorkommen einer Direktive in der Vorlage auf.  Der Prozessor sollte die Ergebnisse speichern.  
  
 Nach allen Aufrufen von ProcessDirective\(\) ruft das Vorlagenmodul die folgenden Methoden auf:  
  
-   `string[] GetReferencesForProcessingRun()` – Gibt die Namen von Assemblys zurück, die für den Vorlagencode erforderlich sind.  
  
-   `string[] GetImportsForProcessingRun()` – Gibt die Namespaces zurück, die im Vorlagencode verwendet werden können.  
  
-   `string GetClassCodeForProcessingRun()` – Gibt den Code von Methoden, Eigenschaften und anderen Deklarationen zurück, die im Vorlagencode verwendet werden können.  Am einfachsten ist es, eine Zeichenfolge zu erstellen, die den C\#\- oder Visual Basic\-Code enthält.  Damit der Direktivenprozessor in Vorlagen mit beliebigen CLR\-Sprachen aufgerufen werden kann, können Sie die Anweisungen als CodeDOM\-Struktur erstellen und dann das Ergebnis der Serialisierung der Struktur in der von der Vorlage verwendeten Sprache zurückgeben.  
  
-   Weitere Informationen finden Sie unter [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## In diesem Abschnitt  
 [Deploying a Custom Directive Processor](../modeling/deploying-a-custom-directive-processor.md)  
 Erläutert die Registrierung eines benutzerdefinierten Direktivenprozessors.  
  
 [Walkthrough: Creating a Custom Directive Processor](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Beschreibt das Erstellen eines benutzerdefinierten Direktivenprozessors, Registrieren und Testen des Direktivenprozessors und Formatieren der Ausgabedatei als HTML.