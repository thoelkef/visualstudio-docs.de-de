---
title: Codegenerierung und T4-Textvorlagen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2f4fed2cbf00717e4eaf9c1353370dbd96037491
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen

In Visual Studio eine *T4-Textvorlage* ist eine Mischung von Textblöcken und steuernder Logik, die eine Textdatei generieren kann. Die steuernde Logik wird als Programmcodefragmente in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]geschrieben. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art enthalten, z. B. eine Webseite, eine Ressourcendatei oder Programmquellcode in einer beliebigen Sprache.

Es gibt zwei Arten von T4-Textvorlagen: Führen Sie auch zur Entwurfszeit.

## <a name="run-time-t4-text-templates"></a>T4-Entwurfszeittextvorlagen ausführen

Auch bekannt als erfolgen "vorverarbeitete" Vorlagen, Zeit Vorlagen ausführen in Ihrer Anwendung um Textzeichenfolgen, in der Regel als Teil der Ausgabe zu erzeugen. Sie könnten beispielsweise eine Vorlage erstellen, um eine HTML-Seite zu definieren:

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

Ihre Anwendung kann auf einem Computer ausgeführt, das keine Visual Studio installiert.

Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor**festlegen.

Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Entwerfen von T4-Entwurfszeittextvorlagen

Design-Time-gebündelt Teil des Quellcodes sowie andere Ressourcen Ihrer Anwendung zu definieren. In der Regel verwenden Sie mehrere Vorlagen, die Daten in einer einzelnen Eingabedatei oder Datenbank gelesen, und Generieren einiger Ihrer *cs*, *vb*, oder sonstigen Quelldateien. Aus jeder Vorlage wird eine Datei generiert. Sie werden in Visual Studio oder MSBuild ausgeführt.

Ihre Eingabedaten könnten beispielsweise Konfigurationsdaten in einer XML-Datei sein. Wenn Sie während der Entwicklung die XML-Datei bearbeiten, generieren Sie Textvorlagen Teil des Anwendungscodes neu. Eine der Vorlagen könnte so wie im folgenden Beispiel aussehen:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

Abhängig von den Werten in der XML-Datei, die generierte *cs* Datei würde etwa folgendermaßen aussehen:

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
> Der Begriff *Modell* wird manchmal verwendet, um Daten zu beschreiben, die von mindestens einer Vorlage gelesen werden. Das Modell kann in einem beliebigen Format in einer beliebigen Art von Datei oder Datenbank vorliegen. Es muss weder ein UML-Modell noch ein domänenspezifisches Sprachmodell sein. Der Begriff „Modell“ gibt lediglich an, dass die Daten hinsichtlich der Geschäftskonzepte definiert werden können, statt so auszusehen wie Code.

Die Transformationsfunktion für Textvorlagen wird als *T4*bezeichnet.

## <a name="see-also"></a>Siehe auch

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)