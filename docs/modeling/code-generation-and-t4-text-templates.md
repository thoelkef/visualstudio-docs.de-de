---
title: Codegenerierung und T4-Textvorlagen
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3864a1dbf468cbef19b5da4ca95577db59a02e6
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]besteht eine *T4-Textvorlage* aus einer Mischung von Textblöcken und steuernder Logik, über die eine Textdatei generiert werden kann. Die steuernde Logik wird als Programmcodefragmente in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]geschrieben. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art enthalten, z. B. eine Webseite, eine Ressourcendatei oder Programmquellcode in einer beliebigen Sprache.

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

 Ihre Anwendung kann auf einem Computer ausgeführt werden, auf dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nicht installiert ist.

 Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor**festlegen.

 Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

 **T4-Entwurfszeit-Textvorlagen** werden in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt, um einen Teil des Quellcodes sowie andere Ressourcen Ihrer Anwendung zu definieren.
Üblicherweise verwenden Sie mehrere Vorlagen, über die die Daten aus einer einzelnen Eingabedatei oder Datenbank gelesen und einige Ihrer `.cs`-, `.vb`- oder sonstigen Quelldateien generiert werden. Aus jeder Vorlage wird eine Datei generiert. Jede dieser Dateien wird in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]ausgeführt.

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
 [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md) In jeder Anwendung, die Textdateien generiert, sind vorkompilierte Textvorlagen eine einfache und zuverlässige Methode den Text zu definieren. Diese Methode kann jedoch nicht für Textvorlagen verwendet werden, die sich zur Laufzeit ändern.

 [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Generieren von Code und anderen Ressourcen aus einem Modell können Sie Ihre Anwendung durch Aktualisieren des Modells zu aktualisieren.

 [Bei der codegenerierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md) Wenn Ihnen genutztes [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK können Sie sicherstellen, die generierte Software stets aktuell bleibt mit Änderungen im Modell.

 [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md) die Syntax einer Textvorlagendatei.

 [Exemplarische Vorgehensweise: Generieren von Code mithilfe von Textvorlagen](../modeling/walkthrough-generating-code-by-using-text-templates.md) zeigt eine Möglichkeit zum Generieren von Code zu verwenden.

 [Debuggen einer T4-Textvorlage](../modeling/debugging-a-t4-text-template.md) zum Debuggen von Textvorlagen und einige häufige Fehler des Text-Vorlage.

 [Generieren von Dateien mit dem TextTransform-Hilfsprogramm](../modeling/generating-files-with-the-texttransform-utility.md) das Befehlszeilentool, mit dem Sie Textvorlagentransformationen ausführen können.

 [Anpassen der T4-TextTransformation](../modeling/customizing-t4-text-transformation.md) zum Schreiben von Direktivenprozessoren und benutzerdefinierten Vorlagenhosts für Ihre eigenen Datenquellen.

## <a name="see-also"></a>Siehe auch

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)