---
title: "Generieren von Code aus einer domänenspezifischen Sprache | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: e9fc83c57b2e1d0bb9768835b3cccc5be36b9295
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generieren von Code für eine domänenspezifische Sprache
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] bietet eine effiziente Möglichkeit zum Generieren von Code, Dokumente, Konfigurationsdateien und andere Artefakte aus Daten in Modellen dargestellt. Mit [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], können Sie einen Satz von Klassen, die die Daten darstellen erstellen und können schreiben den Textvorlagen in Klassen, deren Namen und Eigenschaften widerspiegeln, die Daten.  
  
 Fabrikam hat beispielsweise eine XML-Datei Kundennamen und e-Mail-Adressen. Entwickler erstellen Sie ein Modell, in dem Kunden eine Klasse mit Namen von Eigenschaften und e-Mail-ist. Sie schreiben mehrere Textvorlagen zum Verarbeiten der Daten, einschließlich dieses Fragment der erzeugt eine Tabelle mit allen Kunden als Teil einer HTML-Seite:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Wenn der Kundendatenbank verarbeitet wird, wird die XML-Datei in den Modellspeicher gelesen. Ein *anweisungsprozessor*erstelltes mit [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], die Customer-Klasse in der Textvorlage an den Code verfügbar macht. Viele Textvorlagen können für den gleichen Speicher ausgeführt werden.  
  
 Textvorlagen sind ein wesentlicher [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Sie dienen zum Generieren von Quellcode für die Elemente der Domänenmodell ebenso wie für das VSPackage und die Steuerelemente, die verwendet werden, um die Tools mit integrieren [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In diesem Abschnitt erläutert einige der Methoden zum Erstellen, ändern und Debuggen von Textvorlagen in verwendet [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Zugreifen auf Modelle aus Textvorlagen](../modeling/accessing-models-from-text-templates.md)  
  
 Enthält grundlegende Informationen zum Verweisen auf einer domänenspezifischen Sprache in Textvorlagen.  
  
 [Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Beschreibt die Vorgehensweise zur Problembehandlung und Debuggen auf einer Textvorlage, die auf eine domänenspezifische Sprache verweist.  
  
 [Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Direktivenprozessor](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Beschreibt, wie die Verbindung einen benutzerdefinierten Host auf einen generierten Direktivenprozessor.  
  
 [Der DslTextTransform-Befehl](../modeling/the-dsltexttransform-command.md)  
  
 Beschreibt die Befehlsdatei, die die TextTransform ausführbare Datei in der Befehlszeile für Textvorlagen ausgeführt wird, die auf domänenspezifische Sprachen verweisen.  
  
## <a name="reference"></a>Verweis  
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)  
  
 Stellt die Syntax von Textvorlagendirektiven und Kontrollblöcken bereit.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Erläutert die Textvorlagen-Transformationsprozess ab.  
  
 [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md)  
  
 Lesen Sie dieses Thema, wenn Sie Dateien aus einem DSL auf einen Build-Server generieren.