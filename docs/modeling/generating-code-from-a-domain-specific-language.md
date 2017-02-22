---
title: "Generieren von Code f&#252;r eine dom&#228;nenspezifische Sprache | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Generieren von Code f&#252;r eine dom&#228;nenspezifische Sprache
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] stellt eine leistungsstarke Möglichkeit, Code, Dokumente, Konfigurationsdateien und andere Artefakte von Daten zu generieren, die sich in den Modellen dargestellt werden.  Verwenden [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]können Sie eine Reihe von Klassen erstellen, die die Daten darstellen, und Sie können die Textvorlagen in Klassen schreiben, deren Namen und Eigenschaften dass Daten widerspiegeln.  
  
 Beispielsweise hat Fabrikam eine XML\-Datei von Kundennamen und E\-Mail\-Adressen.  Die Entwickler erstellen ein Modell, in dem nach Kunde eine Klasse ist, und der E\-Mail\-Nachricht mit Eigenschaft.  Sie schreiben eine Reihe von Textvorlagen, um die Daten, einschließlich dieses Fragment zu verarbeiten, die eine Tabelle mit allen Kunden als Teil einer HTML\-Seite erzeugt:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Wenn die Kunden Zieldatenbank verarbeitet wird, wird die XML\-Datei in den Modellspeicher gelesen.  Ein Direktivenprozessor erstellt, indem er [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]verwendet, werden durch den Code für die Customer\-Klasse in der Textvorlage. Viele Textvorlagen können für den gleichen Arbeitsspeicher ausgeführt werden.  
  
 Textvorlagen sind [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]soll.  Sie werden verwendet, um den Quellcode für die Elemente des Domänenmodells modells zu generieren und VSPackages sowie für die Steuerelemente für die Unterstützung der Tools mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]zu integrieren.  
  
 In diesem Abschnitt werden einige der Methoden, die Textvorlagen zu erstellen, zu ändern und zu debuggen, die in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]verwendet werden.  
  
## In diesem Abschnitt  
 [Zugreifen auf Modelle aus Textvorlagen](../modeling/accessing-models-from-text-templates.md)  
  
 Stellt grundlegende Informationen über das auf einer domänenspezifischen Sprache in Textvorlagen bereit.  
  
 [Exemplarische Vorgehensweise: Debuggen einer Textvorlage, die auf ein Modell zugreift](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Beschreibt, wie Problembehandlung und Debuggen einer Textvorlage, die eine domänenspezifische Sprache verweist.  
  
 [Exemplarische Vorgehensweise: Verbinden eines Hosts mit einem generierten Direktivenprozessor](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Beschreibt, wie Sie einen benutzerdefinierten Host an einen generierten Direktivenprozessor herstellt.  
  
 [Der DslTextTransform\-Befehl](../modeling/the-dsltexttransform-command.md)  
  
 Beschreibt die Befehlsdatei, die die TextTransform\-ausführbare Datei in der Befehlszeile für Textvorlagen ausführt, die domänenspezifische Sprachen verweisen.  
  
## Referenz  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Enthält die Syntax von Textvorlagendirektiven und Kontrollblöcken.  
  
## Verwandte Abschnitte  
 [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Erklärt den Textvorlagen\-Transformationsprozess.  
  
 [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md)  
  
 Lesen Sie dieses Thema, wenn Sie Dateien aus einem DSL in einem Build Server generieren.