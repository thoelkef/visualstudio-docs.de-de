---
title: Codegenerierung und T4-Textvorlagen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e57349e8c6f969986333eb8b12a9a3cf70ba3ce6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509343"
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Codegenerierung und T4-Textvorlagen](https://docs.microsoft.com/visualstudio/modeling/code-generation-and-t4-text-templates).  
  
In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], *T4-Textvorlage* ist eine Mischung von Textblöcken und steuernder Logik, eine Textdatei generiert werden kann. Die steuernde Logik wird als programmcodefragmente in geschrieben [!INCLUDE[csprcs](../includes/csprcs-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art enthalten, z. B. eine Webseite, eine Ressourcendatei oder Programmquellcode in einer beliebigen Sprache.  
  
 Es gibt zwei Arten von T4-Textvorlagen:  
  
 **T4-Laufzeit-Textvorlagen** („vorverarbeitete“ Vorlagen) werden in Ihrer Anwendung ausgeführt, um Textzeichenfolgen zu erstellen (meist als Teil der Ausgabe der Anwendung).  
 Sie könnten beispielsweise eine Vorlage erstellen, um eine HTML-Seite zu definieren:  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 Sie sehen, dass die Vorlage der generierten Ausgabe ähnelt. Die Ähnlichkeit der Vorlage mit der resultierenden Ausgabe hilft Ihnen dabei, Fehler zu vermeiden, wenn Sie die Vorlage ändern möchten.  
  
 Außerdem enthält die Vorlage Programmcodefragmente. Sie können diese Fragmente verwenden, um Abschnitte des Texts zu wiederholen, bedingte Abschnitte zu erstellen und Daten aus Ihrer Anwendung anzuzeigen.  
  
 Um die Ausgabe zu generieren, ruft die Anwendung eine Funktion auf, die über die Vorlage generiert wurde. Zum Beispiel:  
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 Die Anwendung kann auf einem Computer, die nicht ausgeführt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installiert.  
  
 Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor**festlegen.  
  
 Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).  
  
 **Während der Entwurfszeit T4-Textvorlagen** ausgeführt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Teil des Quellcodes sowie andere Ressourcen Ihrer Anwendung zu definieren.  
 Üblicherweise verwenden Sie mehrere Vorlagen, über die die Daten aus einer einzelnen Eingabedatei oder Datenbank gelesen und einige Ihrer `.cs`-, `.vb`- oder sonstigen Quelldateien generiert werden. Aus jeder Vorlage wird eine Datei generiert. Sie werden ausgeführt, in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Ihre Eingabedaten könnten beispielsweise Konfigurationsdaten in einer XML-Datei sein. Immer dann, wenn Sie die XML-Datei während der Entwicklung bearbeitet haben, würden mit den Textvorlagen Teile des Anwendungscodes neu generiert. Eine der Vorlagen könnte so wie im folgenden Beispiel aussehen:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 Abhängig von den Werten in der XML-Datei würde die generierte `.cs` -Datei in etwa wie folgt aussehen:  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 Ein weiteres Beispiel: Die Eingabe könnte ein Diagramm des Workflows in einer Geschäftsaktivität sein. Wenn die Benutzer ihren Geschäftsworkflow ändern oder wenn Sie beginnen, mit neuen Benutzern zu arbeiten, die einen anderen Workflow haben, kann der Code problemlos neu generiert werden, damit er dem neuen Modell entspricht.  
  
 Entwurfszeitvorlagen ermöglichen es, die Konfiguration schneller und zuverlässiger zu ändern, wenn sich die Anforderungen geändert haben. In der Regel ist die Eingabe hinsichtlich Geschäftsanforderungen definiert (wie im Workflowbeispiel). Dies erleichtert die Erörterung von Änderungen mit den Benutzern. Entwurfszeitvorlagen sind daher ein nützliches Tool in dynamischen Entwicklungsprozessen.  
  
 Um eine Entwurfszeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFileGenerator**festlegen.  
  
 Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Der Begriff *Modell* wird manchmal verwendet, um Daten zu beschreiben, die von mindestens einer Vorlage gelesen werden. Das Modell kann in einem beliebigen Format in einer beliebigen Art von Datei oder Datenbank vorliegen. Es muss weder ein UML-Modell noch ein domänenspezifisches Sprachmodell sein. Der Begriff „Modell“ gibt lediglich an, dass die Daten hinsichtlich der Geschäftskonzepte definiert werden können, statt so auszusehen wie Code.  
  
 Die Transformationsfunktion für Textvorlagen wird als *T4*bezeichnet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Laufzeittextgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 In jeder Anwendung, die Textdateien generiert, sind vorkompilierte Textvorlagen eine einfache und zuverlässige Methode, den Text zu definieren. Diese Methode kann jedoch nicht für Textvorlagen verwendet werden, die sich zur Laufzeit ändern.  
  
 [Generieren von Code zur Entwurfszeit mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 Die Generierung von Code und anderen Ressourcen aus einem Modell ermöglicht es Ihnen, Ihre Anwendung durch Aktualisieren des Modells zu aktualisieren.  
  
 [Codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md)  
 Wenn Sie installiert haben [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualisierungs- und Modellierungs-SDK können Sie sicherstellen, die generierte Software stets aktuell bleibt mit Änderungen im Modell.  
  
 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md)  
 Die Syntax einer Textvorlagendatei.  
  
 [Exemplarische Vorgehensweise: Generieren von Code mithilfe von Textvorlagen](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Veranschaulicht eine Möglichkeit, wie Codegenerierung verwendet werden kann.  
  
 [Debuggen einer T4-Textvorlage](../modeling/debugging-a-t4-text-template.md)  
 Veranschaulicht das Debuggen von Textvorlagen und einigen üblichen Textvorlagenfehlern.  
  
 [Generieren von Dateien mit dem Hilfsprogramm "TextTransform"](../modeling/generating-files-with-the-texttransform-utility.md)  
 Das Befehlszeilentool, mit dem Sie Textvorlagentransformationen ausführen können.  
  
 [Anpassen der T4-Texttransformation](../modeling/customizing-t4-text-transformation.md)  
 Veranschaulicht die Vorgehensweise zum Schreiben von Direktivenprozessoren und benutzerdefinierten Vorlagenhosts für Ihre eigenen Datenquellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md)   
 [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)



