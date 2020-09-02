---
title: Code Generierung und T4-Text Vorlagen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667921"
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]besteht eine *T4-Textvorlage* aus einer Mischung von Textblöcken und steuernder Logik, über die eine Textdatei generiert werden kann. Die steuernde Logik wird als Programmcodefragmente in [!INCLUDE[csprcs](../includes/csprcs-md.md)] oder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]geschrieben. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art enthalten, z. B. eine Webseite, eine Ressourcendatei oder Programmquellcode in einer beliebigen Sprache.

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

 Um die Ausgabe zu generieren, ruft die Anwendung eine Funktion auf, die über die Vorlage generiert wurde. Beispiel:

```csharp
string webResponseText = new MyTemplate().TransformText();

```

 Ihre Anwendung kann auf einem Computer ausgeführt werden, auf dem [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nicht installiert ist.

 Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor**festlegen.

 Weitere Informationen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md).

 **T4-Entwurfszeit-Textvorlagen** werden in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt, um einen Teil des Quellcodes sowie andere Ressourcen Ihrer Anwendung zu definieren.
Üblicherweise verwenden Sie mehrere Vorlagen, über die die Daten aus einer einzelnen Eingabedatei oder Datenbank gelesen und einige Ihrer `.cs`-, `.vb`- oder sonstigen Quelldateien generiert werden. Aus jeder Vorlage wird eine Datei generiert. Jede dieser Dateien wird in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]ausgeführt.

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

 Weitere Informationen finden Sie unter [Entwurfszeit Code Generierung mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Der Begriff *Modell* wird manchmal verwendet, um Daten zu beschreiben, die von mindestens einer Vorlage gelesen werden. Das Modell kann in einem beliebigen Format in einer beliebigen Art von Datei oder Datenbank vorliegen. Es muss weder ein UML-Modell noch ein domänenspezifisches Sprachmodell sein. Der Begriff „Modell“ gibt lediglich an, dass die Daten hinsichtlich der Geschäftskonzepte definiert werden können, statt so auszusehen wie Code.

 Die Transformationsfunktion für Textvorlagen wird als *T4*bezeichnet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Lauf Zeit Textgenerierung mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md) In jeder Anwendung, die Textdateien generiert, sind vorkompilierte Textvorlagen eine einfache und zuverlässige Methode, den Text zu definieren. Diese Methode kann jedoch nicht für Textvorlagen verwendet werden, die sich zur Laufzeit ändern.

 [Code Generierung zur Entwurfszeit mithilfe von T4-Text Vorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Das Erstellen von Code und anderen Ressourcen aus einem Modell ermöglicht es Ihnen, Ihre Anwendung durch Aktualisieren des Modells zu aktualisieren.

 [Code Generierung in einem Buildprozess](../modeling/code-generation-in-a-build-process.md) Wenn Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] das Visualisierungs-und Modellierungs-SDK installiert haben, können Sie sicherstellen, dass die generierte Software mit Änderungen im Modell auf dem neuesten Stand gehalten wird.

 [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md) Die Syntax einer Textvorlagen Datei.

 Exemplarische Vorgehensweise [: Erstellen von Code mithilfe von Text Vorlagen](../modeling/walkthrough-generating-code-by-using-text-templates.md) Eine Demonstration einer Möglichkeit zum Verwenden der Codegenerierung.

 [Debuggen einer T4-Text Vorlage](../modeling/debugging-a-t4-text-template.md) Gewusst wie: Debuggen von Textvorlagen und einigen häufigen Textvorlagen Fehlern.

 [Erstellen von Dateien mit dem Hilfsprogramm "textTransform](../modeling/generating-files-with-the-texttransform-utility.md) " Das Befehlszeilen Tool, mit dem Sie Textvorlagen Transformationen ausführen können.

 [Anpassen der T4-Text Transformation](../modeling/customizing-t4-text-transformation.md) Schreiben von direktivenprozessoren und benutzerdefinierten Vorlagen Hosts für Ihre eigenen Datenquellen.

## <a name="see-also"></a>Weitere Informationen
 [Generieren von Dateien aus einem UML-Modell](../modeling/generate-files-from-a-uml-model.md) generieren [von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
