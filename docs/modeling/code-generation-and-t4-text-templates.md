---
title: Codegenerierung und T4-Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12dfad3c0a1197161925ca1f59b865975a42b4d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666575"
---
# <a name="code-generation-and-t4-text-templates"></a>Codegenerierung und T4-Textvorlagen

In Visual Studio ist eine *T4-Textvorlage* eine Mischung aus Textblöcken und Steuerelement Logik, mit der eine Textdatei generiert werden kann. Die steuernde Logik wird als Programmcodefragmente in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]geschrieben. In Visual Studio 2015 Update 2 und höher können Sie Funktionen von C# Version 6.0 in T4-template-Direktiven verwenden. Die generierte Datei kann Text beliebiger Art sein, z. b. eine Webseite, eine Ressourcen Datei oder Programm Quellcode in einer beliebigen Sprache.

Es gibt zwei Arten von T4-Textvorlagen: Laufzeit und Entwurfszeit.

## <a name="run-time-t4-text-templates"></a>T4-Textvorlagen zur Laufzeit

Lauf Zeit Vorlagen werden auch als "vorverarbeitete" Vorlagen bezeichnet und werden in Ihrer Anwendung ausgeführt, um Text Zeichenfolgen zu erstellen, in der Regel als Teil der Ausgabe. Sie könnten beispielsweise eine Vorlage erstellen, um eine HTML-Seite zu definieren:

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

Die Anwendung kann auf einem Computer ausgeführt werden, auf dem Visual Studio nicht installiert ist.

Um eine Laufzeitvorlage zu erstellen, fügen Sie Ihrem Projekt eine **Vorverarbeitete Textvorlage** -Datei hinzu. Alternativ können Sie eine Nur-Text-Datei hinzufügen und deren Eigenschaft **Benutzerdefiniertes Tool** auf **TextTemplatingFilePreprocessor**festlegen.

Weitere Informationen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md). Weitere Informationen zur Syntax von Vorlagen finden Sie unter [Schreiben einer T4-Text Vorlage](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Entwurfszeit T4-Textvorlagen

Entwurfszeit Vorlagen definieren einen Teil des Quellcodes und andere Ressourcen Ihrer Anwendung. In der Regel verwenden Sie mehrere Vorlagen, mit denen die Daten in einer einzelnen Eingabedatei oder Datenbank gelesen und einige Ihrer *CS*-, *VB*-oder anderen Quelldateien generiert werden. Aus jeder Vorlage wird eine Datei generiert. Sie werden in Visual Studio oder MSBuild ausgeführt.

Ihre Eingabedaten könnten beispielsweise Konfigurationsdaten in einer XML-Datei sein. Wenn Sie die XML-Datei während der Entwicklung bearbeiten, wird ein Teil des Anwendungs Codes von den Textvorlagen neu generiert. Eine der Vorlagen könnte so wie im folgenden Beispiel aussehen:

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

Abhängig von den Werten in der XML-Datei würde die generierte *CS* -Datei wie folgt aussehen:

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

## <a name="see-also"></a>Siehe auch

- [Generieren von Code für eine domänenspezifische Sprache](../modeling/generating-code-from-a-domain-specific-language.md)
