---
title: T4-Parameter-Direktive | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c1849cbccc1a903716ba94d02f47a339d6ce426
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658571"
---
# <a name="t4-parameter-directive"></a>T4-Parameter-Direktive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Textvorlage deklariert die- `parameter` Direktive Eigenschaften im Vorlagen Code, die aus Werten initialisiert werden, die aus dem externen Kontext übermittelt werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, der die Text Transformation aufruft.

## <a name="using-the-parameter-directive"></a>Verwenden der Parameter-Direktive

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

 Die- `parameter` Direktive deklariert Eigenschaften im Vorlagen Code, die aus Werten initialisiert werden, die aus dem externen Kontext übermittelt werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, der die Text Transformation aufruft. Die Werte können entweder im- `Session` Wörterbuch oder in übermittelt werden <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Sie können Parameter eines beliebigen Remote fähigen Typs deklarieren. Das heißt, der Typ muss mit deklariert werden <xref:System.SerializableAttribute> , oder er muss von abgeleitet sein <xref:System.MarshalByRefObject> . Dadurch können Parameterwerte an die AppDomain übergeben werden, in der die Vorlage verarbeitet wird.

 Beispielsweise können Sie eine Textvorlage mit folgendem Inhalt schreiben:

```
<#@ template language="C#" #>

<#@ parameter type="System.Int32" name="TimesToRepeat" #>

<# for (int i = 0; i < TimesToRepeat; i++) { #>
Line <#= i #>
<# } #>

```

## <a name="passing-parameter-values-to-a-template"></a>Übergeben von Parameterwerten an eine Vorlage
 Wenn Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Erweiterung, z. b. einen Menübefehl oder einen Ereignishandler, schreiben, können Sie eine Vorlage mithilfe des Textvorlagen Dienstanbieter verarbeiten:

```csharp
// Get a service provider – how you do this depends on the context:
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

## <a name="passing-values-in-the-call-context"></a>Übergeben von Werten im Aufrufkontext
 Alternativ können Sie Werte als logische Daten in übergeben <xref:System.Runtime.Remoting.Messaging.CallContext> .

 Im folgenden Beispiel werden Werte mithilfe beider Methoden weitergeleitet:

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

## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Übergeben von Werten an eine Lauf Zeit Vorlage (vorverarbeitete) Text Vorlage
 Es ist normalerweise nicht erforderlich, die- `<#@parameter#>` Direktive mit den Lauf Zeit Vorlagen (vorverarbeitete Textvorlagen) zu verwenden. Stattdessen können Sie einen zusätzlichen Konstruktor oder eine festleg Bare Eigenschaft für den generierten Code definieren, über den Sie Parameterwerte übergeben. Weitere Informationen finden Sie unter [Lauf Zeit Generierung von Text mit T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Wenn Sie jedoch `<#@parameter>` in einer Lauf Zeit Vorlage verwenden möchten, können Sie mithilfe des Sitzungs Wörterbuchs Werte an die Vorlage übergeben. Nehmen Sie beispielsweise an, dass Sie die Datei als vorverarbeitete Vorlage namens erstellt haben `PreTextTemplate1` . Sie können die Vorlage in Ihrem Programm aufrufen, indem Sie den folgenden Code verwenden.

```csharp
PreTextTemplate1 t = new PreTextTemplate1();
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();
t.Session["TimesToRepeat"] = 5;
// Add other parameter values to t.Session here.
t.Initialize(); // Must call this to transfer values.
string resultText = t.TransformText();

```

## <a name="obtaining-arguments-from-texttemplateexe"></a>Abrufen von Argumenten aus TextTemplate.exe

> [!IMPORTANT]
> Die- `parameter` Anweisung ruft keine Werte ab, die im- `–a` Parameter des-Hilfsprogramms festgelegt sind `TextTransform.exe` . Um diese Werte zu erhalten, legen Sie `hostSpecific="true"` in der `template` -Direktive fest, und verwenden Sie `this.Host.ResolveParameterValue("","","argName")` .
