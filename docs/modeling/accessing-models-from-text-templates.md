---
title: Zugreifen auf Modelle aus Textvorlagen
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afb835c883050064d96c32c80de75d58299892f7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040689"
---
# <a name="accessing-models-from-text-templates"></a>Zugreifen auf Modelle aus Textvorlagen
Mithilfe von Textvorlagen können Sie Berichtsdateien Quellcodedateien und anderen Textdateien, die für DSL-Modelle basieren erstellen. Grundlegende Informationen zu Textvorlagen finden Sie [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Die Textvorlagen funktioniert im experimentellen Modus während des Debuggens Ihrer DSL, und es funktioniert auch auf einem Computer, auf dem Sie die DSL bereitgestellt haben.

> [!NOTE]
>  Bei der Erstellung einer DSL-Projektmappe, die Text-Beispielvorlage  **\*TT** -Dateien im Projekt Debuggen generiert werden. Wenn Sie die Namen der Domänenklassen ändern, funktioniert diese Vorlagen nicht mehr. Dennoch, sie enthalten die grundlegenden Anweisungen, die Sie benötigen und Beispiele, die Sie aktualisieren können, um Ihre DSL zu entsprechen.

 So greifen Sie auf ein Modell aus einer Textvorlage

- Legen Sie die Eigenschaft erben von der vorlagenanweisung auf <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Dies ermöglicht den Zugriff auf den Store.

- Geben Sie anweisungsprozessoren, für die DSL, die Sie zugreifen möchten. Dies lädt die Assemblys für Ihre DSL, damit Sie die Domänenklassen, Eigenschaften und Beziehungen im Code der Textvorlage verwenden können. Sie lädt auch die Modelldatei, die Sie angeben.

  Ein `.tt` Datei ähnlich wie im folgenden Beispiel wird im debuggingprojekt erstellt, wenn Sie eine neue Visual Studio-Projektmappe aus der minimale Sprache DSL-Vorlage erstellen.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>
```

 Beachten Sie, dass die folgenden Punkte bezüglich dieser Vorlage:

- Der Domänenklassen, Eigenschaften und Beziehungen, die Sie in der DSL-Definition definiert haben, kann die Vorlage verwenden.

- Lädt die Modelldatei, die Sie, in angeben die Vorlage, die `requires` Eigenschaft.

- Eine Eigenschaft in `this` das Stammelement enthält. Von dort aus kann Ihren Code auf andere Elemente des Modells navigieren. Der Name der Eigenschaft ist in der Regel identisch mit der Domäne Stammklasse der DSL. In diesem Beispiel ist dies `this.ExampleModel`.

- Obwohl die Sprache, in der die Codefragmente geschrieben sind C# -Code ist, können Sie den Text beliebiger Art generieren. Alternativ können Sie den Code schreiben, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] durch Hinzufügen der Eigenschaft `language="VB"` auf die `template` Richtlinie.

- Zum Debuggen der Vorlage hinzufügen `debug="true"` auf die `template` Richtlinie. Die Vorlage wird in einer anderen Instanz von Visual Studio geöffnet, wenn eine Ausnahme auftritt. Wenn Sie in den Debugger zu einem bestimmten Zeitpunkt im Code unterbrechen möchten, fügen Sie die Anweisung `System.Diagnostics.Debugger.Break();`

   Weitere Informationen finden Sie unter [Debuggen einer T4-Textvorlage](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Informationen zu den DSL-anweisungsprozessor
 Die Vorlage kann die Domänenklassen verwenden, die Sie in Ihrer DSL-Definition definiert. Dies wird durch eine Direktive geschaltet zu, die in der Regel am Anfang der Vorlage angezeigt wird. Im vorherigen Beispiel gibt es folgenden Wert.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Der Name der Richtlinie ( `MyLanguage`, in diesem Beispiel) ergibt sich aus den Namen Ihrer DSL. Ruft eine *anweisungsprozessor* , die als Teil der DSL generiert wird. Sie finden den Quellcode in **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Der DSL-anweisungsprozessor führt zwei grundlegenden Aufgaben aus:

- Effektiv in der Vorlage, die Ihre DSL verweist auf Assembly "und" Import-Anweisungen eingefügt. So können Sie Ihre Domänenklassen im Vorlagencode zu verwenden.

- Es lädt die Datei, die Sie, in angeben der `requires` -Parameter und legt eine Eigenschaft `this` , der auf das Stammelement des geladenen Modell verweist.

## <a name="validating-the-model-before-running-the-template"></a>Überprüfen das Modell vor der Ausführung der Vorlage
 Sie können veranlassen, dass das Modell, das überprüft werden, bevor die Vorlage ausgeführt wird.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>
```

 Beachten Sie Folgendes:

1. Die `filename` und `validation` Parameter werden getrennt, mit ";" und keine anderen Trennzeichen oder Leerzeichen vorhanden sein muss.

2. Die Liste der Validierungskategorien bestimmt, welche Überprüfungsmethoden ausgeführt werden. Mehrere Kategorien sollten getrennt werden, mit "&#124;" und keine anderen Trennzeichen oder Leerzeichen vorhanden sein muss.

   Wenn ein Fehler gefunden wird, wird Sie im Fenster "Fehler" gemeldet, und die Ergebnisdatei enthält eine Fehlermeldung angezeigt.

## <a name="Multiple"></a> Zugreifen auf mehrere Modelle aus einer Textvorlage

> [!NOTE]
>  Diese Methode können Sie mehrere Modelle in der gleichen Vorlage zu lesen, aber ModelBus-Verweise nicht unterstützt. Modelle, die von der ModelBus-Verweise angezeigt werden, finden Sie unter [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Wenn Sie mehr als einem Modell mit der gleichen Textvorlage zugreifen möchten, müssen Sie die generierte Direktivenprozessor einmal für jedes Modell aufrufen. Geben Sie den Dateinamen der einzelnen Modelle in der `requires` Parameter. Sie müssen angeben, die Namen, die Sie für die Stammklasse für die Domäne in verwenden möchten die `provides` Parameter. Sie müssen angeben, unterschiedliche Werte für die `provides` Parameter in jedem von der Anweisung aufrufen. Nehmen wir beispielsweise an, dass Sie drei Modelldateien, die aufgerufen wird, Library.xyz School.xyz und Work.xyz verfügen. Um sie mit der gleichen Textvorlage zuzugreifen, müssen Sie drei-Direktive Aufrufe schreiben, die die unten aufgeführten ähneln.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Dieser Beispielcode ist für eine Sprache, die für die Lösungsvorlage für die minimale Sprache basiert.

 Um die Modelle in der Textvorlage zugreifen möchten, können Sie jetzt Code ähnelt dem Code im folgenden Beispiel schreiben.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Dynamisch Laden von Modellen
 Wenn Sie zur Laufzeit zu ladenden welche Modelle bestimmen möchten, können Sie eine Modelldatei im Programmcode, anstatt die DSL-spezifische Richtlinie dynamisch laden.

 Allerdings werden zu den Funktionen der DSL-spezifische Richtlinie den DSL-Namespace zu importieren, damit der Vorlagencode die Domänenklassen in diese DSL definierte verwenden kann. Da Sie die Richtlinie nicht verwenden, müssen Sie hinzufügen  **\<Assembly >** und  **\<Importieren >** Anweisungen für alle Modelle, die Sie laden können. Dies ist einfach, wenn die verschiedenen Modelle, die Sie laden können alle Instanzen der gleichen DSL sind.

 Um die Datei zu laden, ist die effektivste Methode mithilfe von Visual Studio-ModelBus. In einem typischen Szenario werden die Textvorlage eine DSL-spezifische Richtlinie verwenden, um das erste Modell auf die übliche Weise zu laden. Dieses Modell würde ModelBus-Verweise auf ein anderes Modell enthalten. Sie können die ModelBus verwenden, öffnen Sie das Modell auf die verwiesen wird und ein bestimmtes Element zugreifen. Weitere Informationen finden Sie unter [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 In einem Szenario mit weniger üblich, Sie möchten eine Modelldatei zu öffnen, für die, die Sie über nur einen Dateinamen, und die möglicherweise nicht in der aktuellen Visual Studio-Projekt. In diesem Fall können Sie die Datei öffnen, indem Sie mithilfe der beschriebenen Technik [Vorgehensweise: Öffnen Sie ein Modell aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>Generieren mehrerer Dateien aus einer Vorlage
 Wenn Sie separate Dateien - generieren möchten z. B. stehen zum Generieren einer separaten Datei für jedes Element in einem Modell verschiedene Möglichkeiten zur. Standardmäßig wird nur eine Datei aus jeder Vorlagendatei erstellt.

### <a name="splitting-a-long-file"></a>Aufteilen von langen Dateien
 Bei dieser Methode verwenden Sie eine Vorlage, um eine einzelne Datei, die durch ein Trennzeichen getrennt zu generieren. Klicken Sie dann teilen Sie die Datei in seine Bestandteile. Es gibt zwei erste Vorlage zum Generieren der einzelnen Datei, und das andere, um sie aufzuteilen.

 **LoopTemplate.t4** der lange einzelnen Datei generiert. Beachten Sie, dass die Dateierweiterung ".t4", da er nicht verarbeitet werden sollen, direkt beim Klicken auf **alle Vorlagen transformieren**. Diese Vorlage nimmt einen Parameter, der die Trennzeichenfolge gibt an, die die Segmente unterteilt:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>
```

 `LoopSplitter.tt` Ruft `LoopTemplate.t4`, und klicken Sie dann die resultierende Datei in seine Segmente unterteilt. Beachten Sie, dass diese Vorlage nicht unbedingt eine Vorlage für die Modellierung zu werden, da das Modell nicht gelesen werden.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>
```