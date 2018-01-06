---
title: "Zugreifen auf Modelle über Textvorlagen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, accessing models
ms.assetid: cf65395a-0ca3-4826-89c7-b1869562685c
caps.latest.revision: "33"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: 768082882c5ed180956b9bac28c20283404bb913
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-models-from-text-templates"></a>Zugreifen auf Modelle aus Textvorlagen
Mithilfe von Textvorlagen können Sie erstellen Berichtsdateien, Quellcodedateien und anderen Textdateien, die auf einer domänenspezifischen sprachenmodelle basieren. Grundlegende Informationen zu den Textvorlagen finden Sie unter [Codegenerierung und T4-Textvorlagen](../modeling/code-generation-and-t4-text-templates.md). Textvorlagen funktionieren in der experimentellen Modus während des Debuggens der DSL und funktioniert auch auf einem Computer, auf dem Sie die DSL bereitgestellt haben.  
  
> [!NOTE]
>  Beim Erstellen einer DSL-Projektmappe, die Vorlage "Sample Text"  **\*TT** Dateien im Projekt Debuggen generiert werden. Wenn Sie den Namen der Domänenklassen ändern, werden diese Vorlagen ohne mehr funktionieren. Trotzdem sie enthalten die grundlegenden Richtlinien, die Sie benötigen und Beispiele, die Sie aktualisieren können, entsprechend der DSL.  
  
 Zugriff auf ein Modell aus einer Textvorlage:  
  
-   Festlegen die Eigenschaft zum erben von der Vorlagendirektive auf <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Dies ermöglicht den Zugriff auf den Speicher.  
  
-   Geben Sie Direktivenprozessoren, für die DSL, die Sie zugreifen möchten. Dadurch werden die Assemblys für der DSL geladen, damit Sie ihre Domänenklassen, Eigenschaften und Beziehungen im Code der Textvorlage verwenden können. Es lädt auch die Modelldatei, die Sie angeben.  
  
 Ein `.tt` Datei wie im folgenden Beispiel wird in der Debugging-Projekt erstellt, beim Erstellen einer neuen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lösung aus der Vorlage für die minimale DSL-Sprache.  
  
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
  
 Beachten Sie die folgenden Punkte bezüglich dieser Vorlage:  
  
-   Die Vorlage können der Domänenklassen, Eigenschaften und Beziehungen, die Sie in der DSL-Definition definiert.  
  
-   Die Vorlage lädt die Modelldatei, die Sie, in angeben der `requires` Eigenschaft.  
  
-   Eine Eigenschaft in `this` des Stammelements enthält. Von dort kann Ihren Code auf andere Elemente des Modells navigieren. Der Name der Eigenschaft ist in der Regel identisch mit der Stammklasse der Domäne von der DSL. In diesem Beispiel ist dies `this.ExampleModel`.  
  
-   Obwohl die Sprache, in der die Codefragmente geschrieben werden c# ist, können Sie den Text beliebiger Art generieren. Alternativ können Sie den Code schreiben, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] durch Hinzufügen der Eigenschaft `language="VB"` auf die `template` Richtlinie.  
  
-   Um die Vorlage zu debuggen, hinzufügen `debug="true"` auf die `template` Richtlinie. Die Vorlage wird geöffnet, in eine andere Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , wenn eine Ausnahme auftritt. Wenn der Debugger zu einem bestimmten Zeitpunkt im Code unterbrochen werden sollen, fügen Sie die Anweisung`System.Diagnostics.Debugger.Break();`  
  
     Weitere Informationen finden Sie unter [Debuggen einer T4-Textvorlage](../modeling/debugging-a-t4-text-template.md).  
  
## <a name="about-the-dsl-directive-processor"></a>Informationen zu den Direktivenprozessor DSL  
 Die Vorlage kann die Domänenklassen verwenden, die Sie in der DSL-Definition definiert. Dies wird durch eine Direktive geschaltet zu, die in der Regel am Anfang der Vorlage angezeigt wird. Im vorherigen Beispiel gibt es folgenden Wert.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>  
```  
  
 Der Name der Richtlinie ( `MyLanguage`, in diesem Beispiel) ist der Name des der DSL abgeleitet. Ruft eine *Direktivenprozessor* , wird als Teil der DSL generiert. Sie finden den Quellcode in **Dsl\GeneratedCode\DirectiveProcessor.cs**.  
  
 Die Direktivenprozessor DSL führt zwei Hauptaufgaben:  
  
-   Effektiv werden die Vorlage, die der DSL verweist auf Assembly "und" Import-Anweisungen eingefügt. Dadurch können Sie Ihre Domänenklassen im Vorlagencode verwenden.  
  
-   Es lädt die Datei, die Sie, in angeben der `requires` Parameter, und Festlegen einer Eigenschaft `this` , das das Stammelement des geladenen Modells bezeichnet.  
  
## <a name="validating-the-model-before-running-the-template"></a>Beim Validieren des Modells vor dem Ausführen der Vorlage  
 Sie können dazu führen, dass das Modell validiert werden, bevor die Vorlage ausgeführt wird.  
  
```  
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>  
  
```  
  
 Beachten Sie Folgendes:  
  
1.  Die `filename` und `validation` Parameter werden getrennt, mit ";" und keine anderen Trennzeichen oder Leerzeichen vorhanden sein muss.  
  
2.  Die Liste der Validierungskategorien bestimmt die Validierungsmethoden ausgeführt werden. Mehrere Kategorien getrennt werden soll, mit "&#124;" und keine anderen Trennzeichen oder Leerzeichen vorhanden sein muss.  
  
 Wenn ein Fehler gefunden wird, werden Sie im Fenster "Debugfehler" gemeldet werden, und die Ergebnisdatei enthält eine Fehlermeldung angezeigt.  
  
##  <a name="Multiple"></a>Zugriff auf mehrere Modelle in einer Textvorlage  
  
> [!NOTE]
>  Diese Methode können Sie mehrere Modelle in der gleichen Vorlage gelesen, jedoch keine ModelBus-Verweise. Modelle, die von ModelBus Verweise miteinander verbunden sind, finden Sie unter [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 Wenn Sie mehr als ein Modell aus der gleichen Textvorlage zugreifen möchten, müssen Sie den generierten Direktivenprozessor einmal für jedes Modell aufrufen. Geben Sie den Namen der einzelnen Modelle in der `requires` Parameter. Sie müssen die Namen angeben, die Sie für die Domäne Stammklasse in verwenden möchten die `provides` Parameter. Geben Sie unterschiedliche Werte für die `provides` Parameter in jeder Richtlinie aufruft. Nehmen wir beispielsweise an, dass Sie drei Modelldateien Library.xyz School.xyz und Work.xyz aufgerufen haben. Um diese von der gleichen Textvorlage zuzugreifen, müssen Sie drei-Direktive Aufrufe schreiben, die dem folgenden ähneln.  
  
```  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>  
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>  
```  
  
> [!NOTE]
>  Dieser Beispielcode ist für eine Sprache, die auf die minimale Sprache Projektmappenvorlage basieren.  
  
 Um die Modelle in der Textvorlage zuzugreifen, können Sie jetzt Code ähnlich dem Code im folgenden Beispiel schreiben.  
  
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
  
## <a name="loading-models-dynamically"></a>Dynamisches Laden von Modellen  
 Wenn Sie zur Laufzeit zu ladenden welche Modelle ermitteln möchten, können Sie eine Modelldatei im Programmcode, statt mit der DSL-spezifische-Direktive dynamisch laden.  
  
 Zu den Funktionen der DSL-spezifische Richtlinie ist jedoch der DSL-Namespace zu importieren, sodass der Vorlagencode in dieser DSL definierten Domänenklassen verwenden kann. Da Sie nicht die Direktive verwenden, müssen Sie hinzufügen  **\<Assembly >** und  **\<Importieren >** Direktiven für alle Modelle, die Sie laden können. Dies ist einfach, wenn die verschiedenen Modelle, die Sie laden können alle Instanzen des gleichen DSL sind.  
  
 Um die Datei zu laden, ist die effizienteste Methode mit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. In einem typischen Szenario wird die Textvorlage DSL-spezifische-Direktive verwenden, um das erste Modell auf die übliche Weise zu laden. Dieses Modell würde ModelBus Verweise auf ein anderes Modell enthalten. ModelBus können Sie das referenzierte Modell zu öffnen und ein bestimmtes Element zugreifen. Weitere Informationen finden Sie unter [mithilfe von Visual Studio-ModelBus in einer Textvorlage](../modeling/using-visual-studio-modelbus-in-a-text-template.md).  
  
 In einem Szenario mit weniger üblich, Sie möchten eine Modelldatei zu öffnen, für die Sie nur einen Dateinamen haben, und die möglicherweise nicht in der aktuellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt. In diesem Fall können Sie die Datei öffnen, indem Sie mithilfe der Technik, die in beschriebenen [Vorgehensweise: Öffnen Sie ein Modell aus der Datei im Programmcode](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
## <a name="generating-multiple-files-from-a-template"></a>Generieren mehrere Dateien aus einer Vorlage  
 Wenn Sie mehrere Dateien - generieren möchten z. B. stehen zum Generieren einer separaten Datei für jedes Element in einem Modell verschiedene Möglichkeiten. Standardmäßig ist nur eine Datei aus jeder Vorlagendatei erstellt.  
  
### <a name="splitting-a-long-file"></a>Teilen eines langen Dateinamens  
 Bei dieser Methode verwenden Sie eine Vorlage, um eine einzelne Datei, die durch ein Trennzeichen getrennt zu generieren. Teilen Sie Sie dann die Datei, in seine Bestandteile. Es gibt zwei Vorlage zum Generieren der einzelnen Datei und das andere, um sie aufgeteilt.  
  
 **LoopTemplate.t4** lang Einzeldatei generiert. Beachten Sie, dass die Dateierweiterung ".t4", da sie nicht verarbeitet werden soll, direkt beim Klicken auf **alle Vorlagen transformieren**. Diese Vorlage nimmt einen Parameter an, das Trennzeichen an, das die Segmente unterteilt:  
  
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
  
 `LoopSplitter.tt`Ruft `LoopTemplate.t4`, und klicken Sie dann die resultierende Datei in seine Segmente unterteilt. Beachten Sie, dass diese Vorlage nicht unbedingt eine Modellierung Vorlage sein, da das Modell nicht gelesen werden.  
  
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