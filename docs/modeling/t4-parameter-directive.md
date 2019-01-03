---
title: T4-Parameter-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 42853082ef5de6027bdfb897e85f04d2bc37ad7c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868734"
---
# <a name="t4-parameter-directive"></a>T4-Parameter-Anweisung

In einer Visual Studio-Textvorlage die `parameter` Richtlinie deklariert Eigenschaften im Vorlagencode, die von Werten aus dem externen Kontext übergeben initialisiert werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, die TextTransformation aufruft.

## <a name="using-the-parameter-directive"></a>Mithilfe der Parameterdirektive

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Die `parameter` Richtlinie deklariert Eigenschaften im Vorlagencode, die von Werten aus dem externen Kontext übergeben initialisiert werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, die TextTransformation aufruft. Die Werte können übergeben werden, entweder in der `Session` Wörterbuch vorhanden ist, oder im <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Sie können die Parameter eines remotefähigen Typs deklarieren. D. h. muss der Typ deklariert werden, mit <xref:System.SerializableAttribute>, oder sie muss von abgeleitet <xref:System.MarshalByRefObject>. Dadurch können Parameterwerte in der Anwendungsdomäne übergeben werden, in dem die Vorlage verarbeitet wird.

 Beispielsweise könnten Sie eine Textvorlage mit folgendem Inhalt:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>
```

## <a name="passing-parameter-values-to-a-template"></a>Übergeben von Parameterwerten zu einer Vorlage
 Wenn Sie eine Visual Studio-Erweiterung, z. B. einen Menübefehl oder einen Ereignishandler schreiben, können Sie eine Vorlage mithilfe des Textvorlagendiensts verarbeiten:

```csharp
// Get a service provider - how you do this depends on the context:
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example
// Get the text template service:
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
// Create a Session in which to pass parameters:
host.Session = host.CreateSession();
// Add parameter values to the Session:
session["TimesToRepeat"] = 5;
// Process a text template:
string result = t4.ProcessTemplate("MyTemplateFile.t4",
  System.IO.File.ReadAllText("MyTemplateFile.t4"));
```

## <a name="passing-values-in-the-call-context"></a>Übergeben von Werten in den Kontext aufrufen
 Sie können auch Werte übergeben als logische Daten in <xref:System.Runtime.Remoting.Messaging.CallContext>.

 Das folgende Beispiel übergibt Werte von mithilfe beider Methoden:

```csharp
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;
host.Session = host.CreateSession();
// Pass a value in Session:
host.Session["p1"] = 32;
// Pass another value in CallContext:
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");

// Process a small template inline:
string result = t4.ProcessTemplate("",
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"
 + "Test <#=p1#> <#=p2#>");

// Result value is:
//     Test 32 test
```

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Übergeben von Werten zu einer Textvorlage Run-Time (vorverarbeitete)
 Es ist nicht in der Regel erforderlich ist, verwendet der `<#@parameter#>` -Direktive zusammen mit der Laufzeit (vorverarbeiteten Textvorlagen). Stattdessen können Sie definieren einen zusätzlichen Konstruktor oder eine Eigenschaft für den generierten Code, der über dem Sie Parameterwerte übergeben, die festgelegt werden kann. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Allerdings sollten Sie verwenden `<#@parameter>` in eine Vorlage für die Laufzeit können Sie Werte, übergeben, mit dem Wörterbuch der Sitzung. Ein Beispiel: Angenommen, Sie haben die Datei erstellt, als eine vorverarbeitete Vorlage namens `PreTextTemplate1`. Sie können die Vorlage mit dem folgenden Code in Ihrem Programm aufrufen.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();
```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Abrufen von Argumenten von TextTemplate.exe

> [!IMPORTANT]
>  Die `parameter` Richtlinie ist nicht in festgelegten Werte abgerufen werden die `-a` Parameter, der die `TextTransform.exe` Hilfsprogramm. Um diese Werte zu erhalten, legen Sie `hostSpecific="true"` in die `template` Richtlinie, und verwenden Sie `this.Host.ResolveParameterValue("","","argName")`.