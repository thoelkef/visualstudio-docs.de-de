---
title: Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Text-Vorlage | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d97b87289be6f6fb685fe9f1b4e5ee4309bd0431
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509381"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Erstellen von benutzerdefinierten T4-Anweisungsprozessoren für Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Richtlinie Prozessoren](https://docs.microsoft.com/visualstudio/modeling/creating-custom-t4-text-template-directive-processors).  
  
Die *Textvorlagen-Transformationsprozess* nimmt eine *Textvorlage* Datei als Eingabe und erzeugt eine Textdatei, die als Ausgabe. Die *Textvorlagen-Transformationsmodul* Steuerelemente, die der Prozess, und die Engine interagiert mit einer Textvorlagen-Transformationshost und mindestens eine Textvorlage *anweisungsprozessoren* zum Abschließen der der Prozess. Weitere Informationen finden Sie unter [das Textvorlagen-Transformationsprozess](../modeling/the-text-template-transformation-process.md).  
  
 Zum Erstellen eines benutzerdefinierten Direktivenprozessors erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> erbt.  
  
 Der Unterschied zwischen diesen beiden besteht darin, die <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementiert die minimale Schnittstelle ist erforderlich, um die Parameter des Benutzers abrufen und zum Generieren des Codes, der die Vorlagendatei für die Ausgabe erzeugt. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementiert das Entwurfsmuster erfordert/bietet. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> verarbeitet zwei spezielle Parameter `requires` und `provides`.  Z. B. ein benutzerdefiniertes anweisungsprozessors akzeptieren einen Dateinamen vom Benutzer, öffnen und Lesen Sie die Datei und klicken Sie dann den Text der Datei in einer Variablen mit dem Namen speichern möglicherweise `fileText`. Eine Unterklasse von der <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> -Klasse kann vom Benutzer einen Dateinamen verwenden, als Wert für die `requires` Parameter und den Namen der Variablen zum Speichern von Text als Wert für die `provides` Parameter. Dieser Prozessor würde öffnen und Lesen Sie die Datei und klicken Sie dann den Text der Datei in der angegebenen Variablen zu speichern.  
  
 Vor dem Aufruf eines benutzerdefinierten anweisungsprozessors in einer Textvorlage in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], müssen Sie ihn registrieren.  
  
 Weitere Informationen dazu, wie Sie den Registrierungsschlüssel hinzuzufügen, finden Sie unter [bereitstellen einen benutzerdefinierten Anweisungsprozessor](../modeling/deploying-a-custom-directive-processor.md).  
  
## <a name="custom-directives"></a>Benutzerdefinierte Richtlinien  
 Eine benutzerdefinierte Anweisung sieht folgendermaßen aus:  
  
 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`  
  
 Sie können einen benutzerdefinierten anweisungsprozessor verwenden, wenn Sie externe Daten oder Ressourcen von einer Textvorlage zugreifen möchten.  
  
 Andere Textvorlagen können die Funktionalität, die ein einzelner anweisungsprozessor bereitstellt, freigeben, sodass anweisungsprozessoren Faktor Code für die Wiederverwendung zu ermöglichen. Die integrierte `include` Richtlinie ist ähnlich, da Sie es, Code zerlegt und teilen Sie sie für unterschiedliche Textvorlagen verwenden können. Der Unterschied ist, alle Funktionen, die die `include` Richtlinie enthält, wurde behoben und akzeptiert keine Parameter. Wenn Sie die allgemeine Funktionalität für eine Textvorlage ermöglichen und die Vorlage zum Übergeben von Parametern möchten, müssen Sie einen benutzerdefinierten anweisungsprozessor erstellen.  
  
 Einige Beispiele für benutzerdefinierte anweisungsprozessoren könnte sein:  
  
-   Ein anweisungsprozessor, Daten aus einer Datenbank zurückzugeben, die einen Benutzernamen und ein Kennwort als Parameter akzeptiert.  
  
-   Einen anweisungsprozessor öffnen und Lesen einer Datei, die den Namen der Datei als Parameter akzeptiert.  
  
### <a name="principal-parts-of-a-custom-directive-processor"></a>Prinzipal Teile eines benutzerdefinierten anweisungsprozessors  
 Um einen anweisungsprozessor entwickeln zu können, müssen Sie eine Klasse, die entweder erbt erstellen <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> oder <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.  
  
 Die wichtigste `DirectiveProcessor` Methoden, die Sie implementieren müssen, sind wie folgt.  
  
-   `bool IsDirectiveSupported(string directiveName)` -Return `true` , wenn die benannte Direktive der anweisungsprozessor behandeln kann.  
  
-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Die Vorlagen-Engine ruft diese Methode für jedes Vorkommen einer Direktive in der Vorlage. Der Prozessor sollten die Ergebnisse zu speichern.  
  
 Die Vorlagen-Engine wird diese Methoden aufrufen, nachdem alle Aufrufe von ProcessDirective():  
  
-   `string[] GetReferencesForProcessingRun()` -Die Namen der Assemblys, die den Code der Vorlage erfordert zurück.  
  
-   `string[] GetImportsForProcessingRun()` -Gibt die Namespaces zurück, die verwendet werden können im Vorlagencode.  
  
-   `string GetClassCodeForProcessingRun()` -Gibt den Code von Methoden, Eigenschaften und anderen Deklarationen, die den Code der Vorlage verwenden können. Die einfachste Möglichkeit hierzu ist eine Zeichenfolge, die mit der C#- oder Visual Basic-Code zu erstellen. Damit den anweisungsprozessor aufgerufen werden, aus einer Vorlage, die einer beliebigen CLR-Sprache verwendet wird, können Sie die Anweisungen als eine CodeDom-Struktur erstellen und dann das Ergebnis der Serialisierung der Struktur in der von der Vorlage verwendeten Sprache zurück.  
  
-   Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: erstellen einen benutzerdefinierten Anweisungsprozessor](../modeling/walkthrough-creating-a-custom-directive-processor.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Bereitstellen eines benutzerdefinierten Anweisungsprozessors](../modeling/deploying-a-custom-directive-processor.md)  
 Erläutert, wie zum Registrieren eines benutzerdefinierten anweisungsprozessors.  
  
 [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Anweisungsprozessors](../modeling/walkthrough-creating-a-custom-directive-processor.md)  
 Beschreibt Vorgehensweise: erstellen ein benutzerdefiniertes anweisungsprozessors, registrieren und Testen des anweisungsprozessors komplizierter, und wie die Ausgabedatei im HTML-Format formatiert.



