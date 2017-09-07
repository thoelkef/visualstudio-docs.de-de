---
title: Wie Sie mithilfe von Textvorlagen... | Microsoft Docs
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 6e6841e77556d9ae8b8ce76bff01537d5f45e855
ms.contentlocale: de-de
ms.lasthandoff: 09/06/2017

---
# <a name="how-to--with-text-templates"></a>Gewusst wie: ... mit Textvorlagen
Textvorlagen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bieten eine gute Möglichkeit Text beliebiger Art zu generieren. Textvorlagen können zum Generieren von Text zur Laufzeit als Teil Ihrer Anwendung und zur Entwurfszeit zu Ihrem Projektcode zu generieren. Dieses Thema fasst zusammen, die am häufigsten gestellten "Wie kann ich...?" Fragen.  
  
 In diesem Thema werden mehrere Antworten, die Nummerierung vorangestellt werden alternative Vorschläge.  
  
 Eine allgemeine Einführung in Textvorlagen werden soll, finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>So wird es gemacht...  
  
### <a name="generate-part-of-my-application-code"></a>Generieren eines Teils meinem Anwendungscode  
 Ich habe eine Konfiguration oder *Modell* in einer Datei oder einer Datenbank. Einem oder mehreren Teilen meines Codes richten sich nach dem Modell.  
  
-   Generieren Sie einige Codedateien über Textvorlagen. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) und [neuerungen die beste Methode zum Schreiben einer Textvorlage?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generieren von Dateien zur Laufzeit übergeben von Daten in die Vorlage  
 Zur Laufzeit generiert meine Anwendung Textdateien, z. B. Berichte, die eine Kombination von standard-Text und Daten enthalten. Ich möchte, um zu vermeiden, Schreiben Hunderte von `write` Anweisungen.  
  
-   Fügen Sie einer Laufzeittextvorlage zu Ihrem Projekt hinzu. Diese Vorlage erstellt eine Klasse in Ihrem Code können Sie instanziieren und verwenden, um Text zu generieren. Sie können Daten in den Konstruktorparametern zu übergeben. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Wenn Sie möchten aus Vorlagen erstellen, die nur zur Laufzeit verfügbar sind, können Sie standard-Text-Vorlagen verwenden. Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung, Sie können den Textvorlagendienst aufrufen. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md). In anderen Kontexten können Sie das Textvorlagenmodul verwenden. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.  
  
     Verwenden der \<#@parameter#>-Direktive zum Übergeben von Parametern zu diesen Vorlagen. Weitere Informationen finden Sie unter [T4-Parameter-Direktive](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Lesen Sie eine andere Projektdatei aus einer Vorlage  
 Zum Lesen einer Datei aus der gleichen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt als Vorlage:  
  
-   Fügen Sie `hostSpecific="true"` in die `<#@template#>`-Direktive ein.  
  
     Verwenden Sie in Ihrem Code `this.Host.ResolvePath(filename)` zum Abrufen des vollständigen Pfads der Datei.  
  
### <a name="invoke-methods-from-a-template"></a>Aufrufen von Methoden aus einer Vorlage  
 Wenn die Methoden, z. B. im Standard vorhanden [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Klassen:  
  
-   Verwenden Sie die \<#@assembly#>-Direktive zum Laden der Assembly, und verwenden \<#@import#> festzulegende Kontext des Namespaces. Weitere Informationen finden Sie unter [T4-Import-Direktive](../modeling/t4-import-directive.md).  
  
     Wenn Sie häufig den gleichen Satz von Assembly verwenden und Richtlinien zu importieren, sollten Sie einen Direktivenprozessor. In jeder Vorlage können Sie des Direktivenprozessors komplizierter, aufrufen, die die Assemblys und die Modelldateien laden und den Namespacekontext festlegen können. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Direktivenprozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Wenn Sie die Methoden selbst schreiben:  
  
-   Wenn Sie eine Laufzeit-Textvorlage schreiben, Schreiben Sie eine partielle Klassendefinition, die den gleichen Namen wie die Laufzeit-Textvorlage verfügt. Fügen Sie die zusätzlichen Methoden in dieser Klasse hinzu.  
  
-   Ein Klassenfunktionskontrollblock schreiben `<#+ ... #>` in dem Sie Methoden, Eigenschaften und private Klassen deklarieren. Wenn die Vorlage "Text" kompiliert wird, wird sie auf eine Klasse umgewandelt. Die Standardkontrollblöcke `<#...#>` Text werden an eine einzelne Methode transformiert und Klassenfunktionsblöcke werden als separate Elemente eingefügt. Weitere Informationen finden Sie unter [Kontrollblöcke für Textvorlagen](../modeling/text-template-control-blocks.md).  
  
     Methoden, die definiert, wie Klassenfunktionen auch eingebettete Textblöcke enthalten können.  
  
     Sie Klassenfunktionen in einer separaten Datei, die Sie ggf. `<#@include#>` in eine oder mehrere Vorlagendateien.  
  
-   Schreiben Sie die Methoden in einer separaten Assembly (Klassenbibliothek), und rufen Sie sie aus der Vorlage. Verwenden der `<#@assembly#>` Direktive, um die Assembly zu laden und `<#@import#>` festzulegende Kontext des Namespaces. Beachten Sie, um die Assembly neu erstellen, während Sie Debuggen, müssen Sie möglicherweise beenden und neu starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Weitere Informationen finden Sie unter [T4-Textvorlagendirektiven](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Viele Dateien aus einem Modellschema generieren  
 Wenn Sie häufig Dateien Modelle, die das gleiche Schema der XML-Index oder Datenbank aufweisen erstellen:  
  
-   Empfiehlt, einen Direktivenprozessor zu schreiben. Dadurch können Sie mehrere Assembly-Anweisungen zu ersetzen, und importieren die Anweisungen in jeder Vorlage mit einer einzigen benutzerdefinierte Direktive. Die Direktivenprozessor kann auch laden und analysieren die Modelldatei. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Direktivenprozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Generieren von Dateien aus einem komplexen Modell  
  
-   Estellen Sie eine domänenspezifische Sprache (DSL), um das Modell darzustellen. Dies erleichtert die Vorlagen zu schreiben, da Sie verwenden, Typen und Eigenschaften, die den Namen der Elemente im Modell widerspiegeln. Sie müssen nicht die Datei zu analysieren, oder navigieren XML-Knoten. Zum Beispiel:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Weitere Informationen finden Sie unter [erste Schritte mit einer domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md) und [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Abrufen von Daten aus[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Bereitgestellten Dienste verwenden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], durch Festlegen der `hostSpecific` Attribut und laden die `EnvDTE` Assembly. Zum Beispiel:  
  
```csharp  
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
  
-   Weitere Informationen finden Sie unter [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Weitere allgemeine Fragen  
  
###  <a name="starting"></a>Was ist die beste Möglichkeit zum Schreiben einer Textvorlage starten?  
  
1.  Schreiben Sie ein bestimmtes Beispiel der generierten Datei.  
  
2.  Wandeln Sie sie in einer Textvorlage durch Einfügen die `<#@template #>` Richtlinie und den Richtlinien und den Code, die erforderlich sind, um die Eingabedatei oder das Modell zu laden.  
  
3.  Ersetzen Sie die Teile der Datei progressiv mit Ausdruck und Codeblöcke.  
  
### <a name="what-is-a-model"></a>Was ist ein "Modell"?  
  
-   Die Eingabe, die von der Vorlage gelesen wird. Es kann in einer Datei oder in einer Datenbank sein. Möglicherweise XML oder eine Visio-Zeichnung oder eine domänenspezifische Sprache (DSL) oder ein UML-Modell, oder es möglicherweise als nur-Text. Sie können auf mehrere Dateien verteilt werden. Mehr als einer Vorlage wird in der Regel ein Modell liest.  
  
     Die Implikation der Begriff "Modell" ist, dass es einige Aspekte Ihres Unternehmens als der generierten Programmcode oder andere Dateien direkt darstellt. Es kann z. B. den Abfrageplan ein Kommunikationsnetzwerk dar, die die generierte Software bereit.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Was ist der Vorteil der Verwendung von Textvorlagen?  
 Generieren Sie in der Regel mehrere Code oder andere Dateien aus einem Modell aus. Das Modell stellt die Anforderungen direkt als des generierten Codes dar. Es lässt Weg Implementierungsdetail beibehalten und im Hinblick auf die Anforderungen, statt den Code geschrieben wird. Wenn die Anforderungen ändern, wie sie in der Regel nicht - - können Sie das Modell einfacher und zuverlässiger als die anderen Teile des Programmcodes aktualisieren.  
  
 Codegenerierung ist daher ein wertvolles Tool aus der Perspektive des agile-Entwicklungsmethoden.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Welche "best Practices" gibt es für Textvorlagen?  
  
-   Weitere Informationen finden Sie unter [Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Was ist "T4"?  
  
-   Einen anderen Namen für die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Text hier beschriebenen Funktionen. Die vorherige Version, die nicht veröffentlicht wurde, wurde eine Abkürzung für "Textvorlagentransformation".

