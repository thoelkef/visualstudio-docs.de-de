---
title: "Zugreifen auf Modelle aus Textvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Textvorlagen, Zugreifen auf Modelle"
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# Zugreifen auf Modelle aus Textvorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe von Textvorlagen können Sie Berichtsdateien, Textdateien und andere Quellcodedateien erstellen, die auf domänenspezifische Sprachen modelle sind.  Eine grundlegende Informationen zu Textvorlagen finden Sie unter [Code Generation and T4 Text Templates](../modeling/code-generation-and-t4-text-templates.md).  Die Textvorlagen arbeiten im Testmodus gestartet, wenn Sie das Debuggen DSL und funktionieren auch auf einem Computer, auf dem das DSL bereitgestellt haben.  
  
> [!NOTE]
>  Wenn Sie eine DSL\-Projektmappe erstellen, wird ein Beispieltext vorlagen\- **\*.tt** Dateien im Projekt Debuggen generiert.  Wenn Sie die Namen der Klassen für Domänen diese Vorlagen ändern, funktionieren nicht mehr.  Trotzdem schließen sie die grundlegenden \- Direktive ein, mit denen Sie Anforderung und Beispiele zur Verfügung stellen, die Sie aktualisieren können, um das DSL übereinstimmt.  
  
 So fügen Sie ein Modell aus einer Textvorlage zugreifen:  
  
-   Legen Sie die erbens der Vorlagendirektive zu <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>fest.  Dies stellt den Zugriff auf den Speicher.  
  
-   Geben Sie Direktivenprozessoren für das DSL, das Sie zugreifen möchten.  Dadurch lädt die Assembly für das DSL, sodass Sie die Domänen Klassen, Eigenschaften und verhältnisse im Code der Textvorlage verwendet werden können.  Laden Sie auch die Modelldatei, die Sie angeben.  
  
 Eine `.tt` Datei mit dem folgenden Beispiel vergleichbar ist, wird Debuggen im Projekt erstellt, wenn Sie eine neue [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projektmappe aus der minimalen Sprachen DSL Vorlage erstellen.  
  
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
  
 Beachten Sie die folgenden Punkte zu dieser Vorlage:  
  
-   Die Vorlage kann die Domänen Klassen, Eigenschaften und verhältnisse verwenden, die Sie in der DSL\-Definition definiert haben.  
  
-   Die Vorlage lädt die Modelldatei, die Sie in der `requires`\-Eigenschaft angeben.  
  
-   Eine Eigenschaft in `this` das Stammelement enthält.  Von dort kann der Code an andere Elemente im Modell navigieren.  Der Name der Eigenschaft ist normalerweise der gleiche wie der Stammdomänen Klasse des DSL.  In diesem Beispiel ist es `this.ExampleModel`.  
  
-   Obwohl die Sprache, in der die Codefragmente C\# geschrieben wurde, können Sie die Art der Text generiert.  Sie können alternativ den Code in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] schreiben, indem Sie die Eigenschaft `language="VB"` auf `template`\-Direktive hinzufügen.  
  
-   Um die Vorlage zu debuggen, fügen Sie den `debug="true"``template`\-Direktive hinzu.  Die Vorlage wird in einer anderen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , wenn eine Ausnahme auftritt.  Wenn Sie den Debugger an einem bestimmten Punkt im Code beeinflussen möchten, fügen Sie die Anweisung ein `System.Diagnostics.Debugger.Break();`  
  
     Weitere Informationen finden Sie unter [Debugging a T4 Text Template](../modeling/debugging-a-t4-text-template.md).  
  
## Neben den Prozessor DSL\-Direktiven  
 Die Vorlage kann die Domänen Klassen verwenden, die Sie in der DSL\-Definition definiert haben.  Dies wird durch Direktive bewerkstelligt, die normalerweise nach dem Start der Vorlage angezeigt wird.  Im vorherigen Beispiel ist dies Folgendes:  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Der Name der Direktive \( `MyLanguage`in diesem Beispiel\) besteht aus dem Namen des DSL abgeleitet.  Er ruft einen Direktivenprozessor *,* der als Teil des DSL generiert wird.  Sie können den Quellcode in **Dsl\\GeneratedCode\\DirectiveProcessor.cs**suchen.  
  
 Der Direktivenprozessor DSL führt zwei Haupttaske aus:  
  
-   Sie fügt Import\-Direktiven Assembly\- und effektiv in der Vorlage ein, die das DSL verweist.  Auf diese Weise können Sie die Domänen Klassen im Vorlagencode verwendet werden.  
  
-   Laden Sie die Datei, die Sie im `requires`\-Parameter angeben, und legt eine Eigenschaft in `this` fest, die das Stammelement des geladenen Modells verweist.  
  
## Das Modell prüfen, bevor die Vorlage ausgeführt wird  
 Sie können bewirken, dass das Modell überprüft werden, bevor die Vorlage ausgeführt wird.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Beachten Sie:  
  
1.  Die `filename` und `validation`\-Parameter werden durch „begrenzt. “ und es muss keine anderen Kommas oder Leerzeichen verwenden.  
  
2.  Die Liste der Kategorien Validierung, die Validierungsmethoden ausgeführt werden.  Verschiedene Kategorien sollten mit getrennten „&#124;“ und es muss keine anderen Kommas oder Leerzeichen verwenden.  
  
 Wenn ein Fehler gefunden wird, wird er im Fehlerfenster angezeigt, und die Ergebnisdatei enthält eine Fehlermeldung angezeigt.  
  
##  <a name="Multiple"></a> Mehrere Modelle in einer Textvorlage zugreifen.  
  
> [!NOTE]
>  Mit dieser Methode können Sie mehrere Modelle in der gleichen Vorlage jedoch nicht unterstützt ModelBus\-Verweise lesen.  Um Modelle zu lesen die von ModelBus\-Verweise verbundenen werden, finden Sie unter [Verwenden von Visual Studio\-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Wenn Sie mehr als ein Modell aus der gleichen Textvorlage zugreifen möchten, müssen Sie den generierten Direktivenprozessor einmal für jedes Modell aufrufen.  Sie müssen den Dateinamen jedes Modells im `requires`\-Parameter angeben.  Sie müssen den Namen angeben, die Sie für die Stammdomänen \- Klasse im `provides`\-Parameter verwenden möchten.  Sie müssen verschiedene Werte für die Parameter `provides` in jedem der Aufrufe angeben.  Angenommen, Sie verfügen über drei Dateien des Modells, die Library.xyz, School.xyz und Work.xyz aufgerufen werden.  Um diese aus der gleichen Textvorlage zuzugreifen, müssen Sie drei richtungweisende Aufrufe schreiben die die folgenden Code ähneln.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Dieser Beispielcode ist für eine Sprache, die auf die minimale Sprachen Vorlage Projektmappe.  
  
 Um die Modelle in der Textvorlage zuzugreifen, können Sie nun den Code schreiben, der mit dem Code im folgenden Beispiel ähnelt.  
  
```c#  
<#  
foreach (ExampleElement element in this.LibraryModel.Elements)  
...  
foreach (ExampleElement element in this.SchoolModel.Elements)  
...  
foreach (ExampleElement element in this.WorkModel.Elements)  
...  
#>  
```  
  
```vb#  
<#  
For Each element As ExampleElement In Me.LibraryModel.Elements  
...  
For Each element As ExampleElement In Me.SchoolModel.Elements  
...  
For Each element As ExampleElement In Me.WorkModel.Elements  
...  
#>  
```  
  
## Dynamisches Laden von Modellen  
 Wenn Sie während der Laufzeit ermitteln möchten, das modelliert, die geladen werden sollen, können Sie eine Modelldatei im Programmcode dynamisch laden, statt die DSL\-Besondere \- Direktive verwenden.  
  
 Dennoch ist eine der Funktionen der DSL\-Besondere Direktive, die DSL\-Namespace zu importieren, für den Vorlagencode die Domänen Klassen verwenden kann, die in diesem DSL definiert sind.  Da Sie nicht die Direktive verwenden, müssen Sie **\<assembly\>** und **\<import\>**\-Direktive für alle Modelle hinzufügen, die Sie möglicherweise lüden.  Dies ist einfach, wenn die verschiedenen Modelle, die Sie lüden, alle Instanzen des gleichen DSL sind.  
  
 So laden Sie die Datei sollte die effektivste Methode, indem sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus verwendet.  In einem typischen Szenario verwendet die Textvorlage DSL\-Besondere \- Direktive, um das erste Modell wie gewöhnliche zu laden.  Dieses Modell ModelBus\-Verweise auf ein anderes Modell enthalten ist.  Sie können ModelBus verwenden, um das Modell zu öffnen und auf ein bestimmtes Element zuzugreifen.  Weitere Informationen finden Sie unter [Verwenden von Visual Studio\-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 In einem weniger üblichen Szenario sollten Sie eine Modelldatei öffnen, für die Sie nur einen Dateinamen und die nicht im aktuellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt sein könnte.  In diesem Fall können Sie die Datei öffnen, indem Sie das Verfahren verwenden, die in [Gewusst wie: Öffnen eines Modells aus einer Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md)beschrieben wird.  
  
## Mehrere Dateien mit einer Vorlage generieren  
 Wenn Sie mehrere Dateien generieren möchten, z. B. eine separate Datei für jedes Element in einem Modell generieren, gibt es einige mögliche Vorgehensweisen.  Standardmäßig wird nur eine Datei aus einer Vorlagendatei generiert.  
  
### Eine lange Datei aufteilen  
 In dieser Methode können Sie eine Vorlage, um eine einzelne Datei zu generieren, getrennt durch ein Trennzeichen.  Dann Sie die Datei in ihre Teile aufgeteilt.  Es gibt zwei Vorlagen, die eine einzelne Datei zu generieren und die andere, um sie zu teilen.  
  
 **LoopTemplate.t4** generiert die lange einzelne Datei.  Beachten Sie, dass die Dateierweiterung „.t4“ ist, da sie nicht direkt verarbeitet werden soll, wenn Sie auf **Alle Vorlagen transformieren**klicken.  Diese Vorlage akzeptiert einen Parameter, der die Trennzeichenfolge angibt, die die Segmente unterteilt:  
  
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
  
 `LoopSplitter.tt` ruft `LoopTemplate.t4`auf und weist dann die resultierende Datei in den zugehörigen Segmenten.  Beachten Sie, dass diese Vorlage Modellierungs keine Vorlage sein muss, da sie nicht das Modell liest.  
  
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