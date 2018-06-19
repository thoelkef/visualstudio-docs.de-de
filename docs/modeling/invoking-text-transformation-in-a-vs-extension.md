---
title: Aufrufen von Texttransformation in einer VS-Erweiterung
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 20c4c9e9c91fd93a190463bc35fe016be4cdf838
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31949487"
---
# <a name="invoking-text-transformation-in-a-vs-extension"></a>Aufrufen von Texttransformation in einer VS-Erweiterung
Wenn Sie eine Visual Studio-Erweiterung, z. B. einen Menübefehl schreiben oder [einer domänenspezifischen Sprache](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md), Sie können mithilfe des Textvorlagendiensts transformieren von Textvorlagen. Sie benötigen den <xref:Microsoft.VisualStudio.TextTemplating.VSHost.STextTemplating>-Dienst, der in <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating> umgewandelt werden muss.

## <a name="getting-the-text-templating-service"></a>Erhalt des Textvorlagendiensts

```csharp
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = ...; // An instance of EnvDTE, for example

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;

// Process a text template:
string result = t4.ProcessTemplate(filePath, System.IO.File.ReadAllText(filePath));

```

## <a name="passing-parameters-to-the-template"></a>Übergeben von Parametern an die Vorlage
 Sie können Parameter an die Vorlage übergeben. In der Vorlage können Sie die Parameterwerte mit der `<#@parameter#>`-Direktive abrufen.

 Für einen Parameter muss ein Typ verwendet werden, der serialisierbar ist oder gemarshallt werden kann. Das heißt, der Typ muss mit <xref:System.SerializableAttribute> deklariert werden, oder er muss sich von <xref:System.MarshalByRefObject> ableiten. Diese Einschränkung ist notwendig, da die Textvorlage in einer separaten AppDomain ausgeführt wird. Alle integrierten Typen wie z. B. **System.String** und **System. Int32** sind serialisierbar.

 Um Parameterwerte zu übergeben, können vom aufrufenden Code Werte entweder im `Session`-Wörterbuch oder im <xref:System.Runtime.Remoting.Messaging.CallContext> platziert werden.

 Das folgende Beispiel transformiert mithilfe der beiden Methoden eine kurze Testvorlage:

```
using Microsoft.VisualStudio.TextTemplating;
using Microsoft.VisualStudio.TextTemplating.VSHost;
...
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte;

// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost sessionHost = t4 as ITextTemplatingSessionHost;

// Create a Session in which to pass parameters:
sessionHost.Session = sessionHost.CreateSession();
sessionHost.Session["parameter1"] = "Hello";
sessionHost.Session["parameter2"] = DateTime.Now;

// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("parameter3", 42);

// Process a text template:
string result = t4.ProcessTemplate("",
   // This is the test template:
   "<#@parameter type=\"System.String\" name=\"parameter1\"#>"
 + "<#@parameter type=\"System.DateTime\" name=\"parameter2\"#>"
 + "<#@parameter type=\"System.Int32\" name=\"parameter3\"#>"
 + "Test: <#=parameter1#>    <#=parameter2#>    <#=parameter3#>");

// This test code yields a result similar to the following line:
//     Test: Hello    07/06/2010 12:37:45    42

```

## <a name="error-reporting-and-the-output-directive"></a>Fehlerbericht und Ausgabedirektive
 Alle Fehler, die während der Verarbeitung auftreten, werden im Fehlerfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt. Außerdem können Sie über Fehler informiert werden, indem Sie einen Rückruf angeben, der <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplatingCallback> implementiert.

 Wenn Sie die Ergebniszeichenfolge in eine Datei schreiben möchten, sind Sie möglicherweise daran interessiert, welche Dateierweiterung und welche Codierung in der `<#@output#>`-Direktive in der Vorlage angegeben wurden. Diese Informationen werden auch an den Rückruf übergeben. Weitere Informationen finden Sie unter [T4 Output-Direktive](../modeling/t4-output-directive.md).

```csharp
void ProcessMyTemplate(string MyTemplateFile)
{
  string templateContent = File.ReadAllText(MyTemplateFile);
  T4Callback cb = new T4Callback();
  // Process a text template:
  string result = t4.ProcessTemplate(MyTemplateFile, templateContent, cb);
  // If there was an output directive in the MyTemplateFile,
  // then cb.SetFileExtension() will have been called.
  // Determine the output file name:
  string resultFileName =
    Path.Combine(Path.GetDirectoryName(MyTemplateFile),
        Path.GetFileNameWithoutExtension(MyTemplateFile))
      + cb.fileExtension;
  // Write the processed output to file:
  File.WriteAllText(resultFileName, result, cb.outputEncoding);
  // Append any error messages:
  if (cb.errorMessages.Count > 0)
  {
    File.AppendAllLines(resultFileName, cb.errorMessages);
  }
}

class T4Callback : ITextTemplatingCallback
{
  public List<string> errorMessages = new List<string>();
  public string fileExtension = ".txt";
  public Encoding outputEncoding = Encoding.UTF8;

  public void ErrorCallback(bool warning, string message, int line, int column)
  { errorMessages.Add(message); }

  public void SetFileExtension(string extension)
  { fileExtension = extension; }

  public void SetOutputEncoding(Encoding encoding, bool fromOutputDirective)
  { outputEncoding = encoding; }
}

```

 Der Code kann mit einer Vorlagendatei getestet werden, die der folgenden Datei ähnelt:

```
<#@output extension=".htm" encoding="ASCII"#>
<# int unused;  // Compiler warning "unused variable"
#>
Sample text.
```

 Die Compilerwarnung wird im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Fehlerfenster angezeigt, und es wird auch ein Aufruf von `ErrorCallback` generiert.

## <a name="reference-parameters"></a>Verweisparameter
 Sie können Werte aus einer Textvorlage mit einer Parameterklasse übergeben, die von <xref:System.MarshalByRefObject> abgeleitet wird.

## <a name="related-topics"></a>Verwandte Themen
 So generieren Sie Text aus einer vorverarbeiteten Textvorlage: Rufen Sie die `TransformText()` -Methode der generierten Klasse. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

 So generieren Sie Text außerhalb einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterung: Definieren Sie einen benutzerdefinierten Host. Weitere Informationen finden Sie unter [Verarbeiten von Textvorlagen mithilfe eines benutzerdefinierten Hosts](../modeling/processing-text-templates-by-using-a-custom-host.md).

 Um Quellcode zu generieren, der später kompiliert und ausgeführt werden können: Rufen Sie die `t4.PreprocessTemplate()` Methode <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating>.
