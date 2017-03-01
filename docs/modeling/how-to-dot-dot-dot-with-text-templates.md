---
title: Gewusst wie... mit Textvorlagen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>Gewusst wie: ... mit Textvorlagen
Textvorlagen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bieten eine gute Möglichkeit zum Generieren von Text beliebiger Art. Sie können Textvorlagen verwenden, zum Generieren von Text zur Laufzeit als Teil der Anwendung und zur Entwurfszeit Projektcode zu generieren. In diesem Thema werden die am häufigsten gestellte "Wie kann ich...?" Fragen.  
  
 In diesem Thema werden mehrere Antworten, die mit Aufzählungszeichen werden alternative Vorschläge.  
  
 Eine allgemeine Einführung in Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>So wird es gemacht...  
  
### <a name="generate-part-of-my-application-code"></a>Generieren eines Teils meines Anwendungscodes  
 Ich habe eine Konfiguration oder *Modell* in einer Datei oder einer Datenbank. Ein oder mehrere Teile meines Codes hängt dieses Modell.  
  
-   Generieren Sie einiger Codedateien aus Textvorlagen. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) und [was die beste Methode zum Schreiben einer Textvorlage ist?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generieren von Dateien zur Laufzeit und übergeben von Daten in die Vorlage  
 Zur Laufzeit generiert meiner Anwendung Textdateien, z. B. Berichte, die eine Kombination von standard-Text und Daten enthalten. Ich möchte, um zu vermeiden, Schreiben Hunderte von `write` Anweisungen.  
  
-   Fügen Sie eine Laufzeit-Textvorlage zu Ihrem Projekt. Diese Vorlage erstellt eine Klasse in Ihrem Code können Sie instanziieren und verwenden, um Text zu generieren. Sie können Daten in den Konstruktorparametern zu übergeben. Weitere Informationen finden Sie unter [Textgenerierung mit T4-Textvorlagen zur Laufzeit](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Wenn Sie möchten aus Vorlagen erstellen, die nur zur Laufzeit verfügbar sind, können Sie standard-Text-Vorlagen verwenden. Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Erweiterung können Sie den Textvorlagendienst aufrufen. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md). In anderen Kontexten können Sie das Textvorlagenmodul verwenden. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     Verwenden der \<#@parameter#> Direktive, um Parameter an diese Vorlagen zu übergeben. Weitere Informationen finden Sie unter [T4-Parameter-Direktive](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Lesen einer anderen Projektdatei aus einer Vorlage  
 Zum Lesen einer Datei aus der gleichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Projekt als Vorlage:  
  
-   Fügen Sie `hostSpecific="true"` in die `<#@template#>`-Direktive ein.  
  
     Verwenden Sie in Ihrem Code `this.Host.ResolvePath(filename)` um den vollständigen Pfad der Datei zu erhalten.  
  
### <a name="invoke-methods-from-a-template"></a>Aufrufen von Methoden von einer Vorlage  
 Wenn die Methoden, z. B. im Standard vorhanden [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Klassen:  
  
-   Verwenden Sie die \<#@assembly#> Direktive zum Laden der Assembly, und verwenden Sie \<#@import#> den Namespacekontext festlegen. Weitere Informationen finden Sie unter [T4-Import-Direktive](../modeling/t4-import-directive.md).  
  
     Wenn Sie häufig der gleichen Assembly mithilfe und Importieren von Richtlinien, Schreiben Sie ggf. einen Direktivenprozessor. In jeder Vorlage können Sie den Direktivenprozessor aufrufen, der die Assemblys und die Modelldateien laden und den Namespacekontext festlegen kann. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4-Direktive Direktivenprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Wenn Sie die Methoden selbst schreiben:  
  
-   Wenn Sie eine Laufzeit-Textvorlage schreiben, Schreiben Sie eine partielle Klassendefinition, die den gleichen Namen wie die Laufzeit-Textvorlage verfügt. Fügen Sie die zusätzlichen Methoden in dieser Klasse.  
  
-   Schreiben Sie einen Klassenfunktionskontrollblock `<#+ ... #>` in dem Sie Methoden, Eigenschaften und private Klassen deklarieren können. Wenn die Textvorlage kompiliert wird, wird es in eine Klasse transformiert. Das Standardsteuerelement blockiert `<#...#>` Text wird an eine einzelne Methode transformiert und Klassenfunktionsblöcke werden als separate Elemente eingefügt. Weitere Informationen finden Sie unter [Kontrollblöcke für Textvorlagen](../modeling/text-template-control-blocks.md).  
  
     Methoden, die definiert, wie die Klasse auch eingebettete Textblöcke einschließen können.  
  
     Sie Klassenfunktionen in einer separaten Datei, Sie können ggf. `<#@include#>` in eine oder mehrere Vorlagendateien.  
  
-   Schreiben Sie die Methoden in einer separaten Assembly (Klassenbibliothek), und nennen Sie diese aus der Vorlage. Verwenden der `<#@assembly#>` Richtlinie zum Laden der Assembly und `<#@import#>` den Namespacekontext festlegen. Beachten Sie, um die Assembly neu erstellen, während Sie Debuggen, müssen Sie möglicherweise beenden und neu starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [T4-Textvorlagendirektiven](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Viele Dateien mit einem Modellschema generieren  
 Wenn Sie häufig Dateien anhand von Modellen, die das gleiche XML oder Schema besitzen generieren:  
  
-   Schreiben Sie ggf. einen Direktivenprozessor. Dadurch können Sie mehrere Assembly-Anweisungen ersetzen und Importieren von Anweisungen in jeder Vorlage mit einer einzelnen benutzerdefinierten Direktive. Der Direktivenprozessor kann auch laden und analysieren die Datei. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4-Direktive Direktivenprozessoren für Textvorlagen](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Generieren von Dateien aus einem komplexen Modell  
  
-   Erwägen Sie eine domänenspezifische Sprache (DSL) zur Darstellung des Modells erstellen. Dadurch viel einfacher schreiben Vorlagen an, da Sie Typen und Eigenschaften, die den Namen der Elemente im Modell widerspiegeln. Sie müssen nicht die Datei analysieren oder XML-Knoten navigieren. Zum Beispiel:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Weitere Informationen finden Sie unter [erste Schritte mit domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md) und [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Abrufen von Daten aus[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Dienste, Verwendung [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], durch Festlegen der `hostSpecific` -Attribut und laden die `EnvDTE` Assembly. Zum Beispiel:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>Ausführen von Textvorlagen im Buildprozess  
  
-   Weitere Informationen finden Sie unter [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Allgemeine Fragen  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>Was ist die beste Methode zum Schreiben einer Textvorlage?  
  
1.  Schreiben Sie ein Beispiel der generierten Datei.  
  
2.  Schalten Sie ihn in einer Textvorlage durch Einfügen der `<#@template #>` -Direktive und den Richtlinien und den Code, die erforderlich sind, um die Datei oder das Modell zu laden.  
  
3.  Ersetzen Sie schrittweise Teile der Datei durch Ausdruck und Codeblöcke.  
  
### <a name="what-is-a-model"></a>Was ist ein "Modell"?  
  
-   Die Eingabe von der Vorlage gelesen wird. In einer Datei oder in einer Datenbank zurückzuführen. Möglicherweise XML oder einer Visio-Zeichnung oder eine domänenspezifische Sprache (DSL) oder eines UML-Modells oder nur-Text sein. Es kann auf mehrere Dateien verteilt werden. Mehr als eine Vorlage wird in der Regel ein Modell liest.  
  
     Der Begriff "Modell" wird, dass sie einige Aspekte Ihres Unternehmens direkt als generierten Programmcode oder andere Dateien darstellt. Es kann z. B. den Plan eines darstellen, die die generierten Software bereit.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Was ist der Vorteil der Verwendung von Textvorlagen?  
 Normalerweise generieren Sie mehrere Codeabschnitte oder andere Dateien aus einem Modell. Das Modell repräsentiert die Anforderungen direkt als den generierten Code. Es lässt Implementierungsdetail und im Hinblick auf die Anforderungen, anstatt den Code geschrieben wird. Wenn die Anforderungen ändern wie gewohnt – – können Sie das Modell einfacher und zuverlässiger als die anderen Teile des Programmcodes aktualisieren.  
  
 Generieren von Code ist daher ein wertvolles Tool aus der Perspektive von flexiblen Entwicklungsmethoden.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Welche "best Practices" gibt es für Textvorlagen?  
  
-   Weitere Informationen finden Sie unter [Richtlinien für das Schreiben von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Was ist "T4"?  
  
-   Einen anderen Namen für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Text hier beschriebenen Funktionen. Die vorherige Version, die nicht veröffentlicht wurde, war eine Abkürzung für "Textvorlagentransformation".

