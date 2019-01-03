---
title: 'Gewusst wie: ... mit Textvorlagen'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7a29f9c8813950cda5907b7f0f96141d00d562fe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887762"
---
# <a name="how-to--with-text-templates"></a>Gewusst wie: ... mit Textvorlagen
Textvorlagen in Visual Studio bieten eine gute Möglichkeit für das Generieren von Text beliebiger Art. Sie können Textvorlagen verwenden, um Text zu generieren, zur Laufzeit als Teil Ihrer Anwendung und zur Entwurfszeit aus, um einige der Projektcode zu generieren. Dieses Thema fasst zusammen, die am häufigsten gestellte "Gewusst...?" Fragen.

 In diesem Thema werden mehrere Antworten, die Nummerierung vorangestellt werden alternative Vorschläge.

 Finden Sie eine allgemeine Einführung in den Textvorlagen, [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>So wird es gemacht...

### <a name="generate-part-of-my-application-code"></a>In meiner Anwendungscode generieren
 Ich habe eine Konfiguration oder *Modell* in einer Datei oder einer Datenbank. Eines oder mehrerer Teile von meinem Code hängen von diesem Modell ab.

-   Generieren Sie einige Ihrer Codedateien aus Textvorlagen. Weitere Informationen finden Sie unter [Design-Time Code Generation mithilfe von T4-Textvorlagen](../modeling/design-time-code-generation-by-using-t4-text-templates.md) und [was die beste Möglichkeit zum Schreiben einer Vorlage ist?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generieren von Dateien zur Laufzeit übergeben von Daten in der Vorlage
 Zur Laufzeit generiert meiner Anwendung Textdateien, z. B. Berichte, die eine Kombination von standard-Text und Daten enthalten. Ich möchte, um zu vermeiden, Schreiben Hunderte von `write` Anweisungen.

-   Fügen Sie Ihrem Projekt eine runtimetextvorlage hinzu. Mit dieser Vorlage erstellt eine Klasse in Ihrem Code, die Sie instanziieren und verwenden, um Text zu generieren können. Sie können damit Daten in den Konstruktorparametern übergeben. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

-   Wenn Sie möchten aus Vorlagen zu generieren, die nur zur Laufzeit verfügbar sind, können Sie die standard-Text-Vorlagen verwenden. Wenn Sie Visual Studio-Erweiterung schreiben, können Sie den Textvorlagendienst aufrufen. Weitere Informationen finden Sie unter [Aufrufen von Texttransformation in einer VS-Erweiterung](../modeling/invoking-text-transformation-in-a-vs-extension.md). In anderen Kontexten können Sie die Vorlagen-Engine verwenden. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     Verwenden der \<#@parameter#> Richtlinie zum Übergeben von Parametern an diese Vorlagen. Weitere Informationen finden Sie unter [T4-Parameter-Direktive](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Lesen Sie eine andere Projektdatei aus einer Vorlage
 Um eine Datei aus demselben Visual Studio-Projekt als Vorlage zu lesen:

-   Fügen Sie `hostSpecific="true"` in die `<#@template#>`-Anweisung ein.

     Verwenden Sie in Ihrem Code `this.Host.ResolvePath(filename)` zum Abrufen des vollständigen Pfads der Datei.

### <a name="invoke-methods-from-a-template"></a>Aufrufen von Methoden aus einer Vorlage
 Wenn die Methoden, z. B. im Standard vorhanden [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Klassen:

- Verwenden der \<#@assembly#> Richtlinie zum Laden der Assembly, und verwenden Sie \<#@import#> um den Namespacekontext einzurichten. Weitere Informationen finden Sie unter [T4-Import-Direktive](../modeling/t4-import-directive.md).

   Wenn Sie häufig der gleichen Assembly mithilfe und-Direktiven Import, sollten Sie einen anweisungsprozessor schreiben. In den einzelnen Vorlagen können Sie des anweisungsprozessors komplizierter, aufrufen, die die Assemblys und der Model-Dateien laden und Festlegen des Kontexts des Namespace können. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Richtlinie Prozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md).

  Wenn Sie die Methoden selbst schreiben:

- Wenn Sie eine Laufzeit-Textvorlage schreiben, Schreiben Sie eine partielle Klassendefinition, die den gleichen Namen wie die Laufzeit-Textvorlage. Fügen Sie die zusätzlichen Methoden in dieser Klasse hinzu.

- Schreiben Sie ein Klassenfunktionskontrollblock `<#+ ... #>` in dem Sie Methoden, Eigenschaften und private Klassen deklarieren können. Wenn die Textvorlage kompiliert wird, wird sie auf eine Klasse umgewandelt. Die Standardkontrollblöcke `<#...#>` Text werden an eine einzelne Methode transformiert und Klassenfunktionsblöcke werden als separate Elemente eingefügt. Weitere Informationen finden Sie unter [Kontrollblöcke für Textvorlagen](../modeling/text-template-control-blocks.md).

   Methoden, die definiert, wie Funktionen auch eingebettete Textblöcke enthalten können.

   Sie Klassenfunktionen in einer separaten Datei, die Sie ggf. `<#@include#>` in eine oder mehrere Vorlagendateien.

- Schreiben Sie die Methoden in einer separaten Assembly (Klassenbibliothek), und rufen Sie sie aus Ihrer Vorlage. Verwenden der `<#@assembly#>` Direktive, um die Assembly zu laden und `<#@import#>` um den Namespacekontext einzurichten. Beachten Sie, um die Assembly neu erstellen, während Sie Debuggen, müssen Sie möglicherweise beenden und starten Sie Visual Studio neu. Weitere Informationen finden Sie unter [T4-Textvorlagenanweisungen](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generieren Sie viele Dateien aus einem Modellschema
 Wenn Sie häufig Dateien aus Modellen, die das gleiche XML oder Schema aufweisen generiert:

-   Berücksichtigen Sie beim Schreiben eines anweisungsprozessors. Dadurch können Sie mehrere Assembly-Anweisungen ersetzen, und importieren die Anweisungen in den einzelnen Vorlagen mit einer einzelnen benutzerdefinierten-Direktive. Der anweisungsprozessor kann auch laden und analysieren die Modelldatei. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten T4 Text Vorlage Richtlinie Prozessoren](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generieren von Dateien aus einem komplexen Modell

-   Erwägen Sie eine domänenspezifische Sprache (DSL) zur Darstellung des Modells erstellen. Dadurch viel einfacher schreiben die Vorlagen, da Sie Typen und Eigenschaften, die den Namen der Elemente im Modell widerspiegeln. Sie müssen nicht die Datei analysieren, oder navigieren XML-Knoten. Zum Beispiel:

     `foreach (Book book in this.Library) { ... }`

     Weitere Informationen finden Sie unter [erste Schritte mit domänenspezifischen Sprachen](../modeling/getting-started-with-domain-specific-languages.md) und [Generieren von Code aus einer domänenspezifischen Sprache](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Abrufen von Daten aus Visual Studio
 Dienste, die in Visual Studio, vom Satz verwendet die `hostSpecific` -Attribut, und laden die `EnvDTE` Assembly. Zum Beispiel:

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

### <a name="starting"></a> Was ist die beste Möglichkeit zum Schreiben einer Textvorlage?

1.  Schreiben Sie ein Beispiel der generierten Datei.

2.  Schalten Sie ihn in einer Textvorlage durch Einfügen der `<#@template #>` Richtlinie, und die Anweisungen und den Code, die erforderlich sind, um die Eingabedatei oder ein Modell zu laden.

3.  Ersetzen Sie progressiv Teile der Datei, durch den Ausdruck und Codeblöcken.

### <a name="what-is-a-model"></a>Was ist ein "Modell"?

-   Die Eingabe, die von der Vorlage gelesen. Es kann es sich um in einer Datei oder in einer Datenbank handeln. Möglicherweise XML oder einer Visio-Zeichnung oder eine domänenspezifische Sprache (DSL) oder einem UML-Modell, oder es könnte sein, nur-Text. Sie können in mehrere Dateien verteilt werden. Mehr als eine Vorlage wird in der Regel ein Modell liest.

     Der Begriff "Ansichtsmodell" wird, dass sie einen Aspekt des Unternehmens direkt als der generierten Programmcode oder andere Dateien darstellt. Es kann z. B. den Abfrageplan ein Kommunikationsnetzwerk darstellen, die Ihre generierte Software überwachen wird.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Was ist der Vorteil der Verwendung von Textvorlagen?
 Generieren Sie in der Regel mehrere Code oder andere Dateien aus einem Modell aus. Das Modell repräsentiert die Anforderungen direkt als den generierten Code. Es lässt Implementierungsdetail und im Hinblick auf die Anforderungen, anstatt den Code geschrieben wird. Wenn sich die Anforderungen ändern, wie in der Regel - - können Sie das Modell einfacher und zuverlässiger als die anderen Teile der Programmcode aktualisieren.

 Codegenerierung ist deshalb ein wertvolles Tool aus der Perspektive von flexiblen Entwicklungsmethoden.

### <a name="what-best-practices-are-there-for-text-templates"></a>Welche "best Practices" für Textvorlagen vorhanden sind?

-   Weitere Informationen finden Sie unter [Richtlinien für das Verfassen von T4-Textvorlagen](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Was ist "T4"?

-   Ein anderer Name für die Visual Studio Text hier beschriebenen Funktionen. Die vorherige Version, die nicht veröffentlicht wurde, war eine Abkürzung für "Textvorlagen-Transformationsprozess".
