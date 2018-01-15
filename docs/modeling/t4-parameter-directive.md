---
title: T4-Parameter-Richtlinie | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dbb5e31085f4bc7a405722b581c8e424db5b80ca
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="t4-parameter-directive"></a>T4-Parameter-Anweisung
In einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Textvorlage, die `parameter` Richtlinie deklariert Eigenschaften im Vorlagencode, die von Werten, die vom externen Kontext übergeben, initialisiert werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, der TextTransformation aufruft.  
  
## <a name="using-the-parameter-directive"></a>Mithilfe der Parameterdirektive  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Die `parameter` Richtlinie deklariert Eigenschaften im Vorlagencode, die von Werten, die vom externen Kontext übergeben, initialisiert werden. Sie können diese Werte festlegen, wenn Sie Code schreiben, der TextTransformation aufruft. Die Werte können übergeben werden, entweder in der `Session` Wörterbuch vorhanden ist, oder im <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Sie können die Parameter eines beliebigen Typs remotefähige deklarieren. D. h. muss der Typ deklariert werden, mit <xref:System.SerializableAttribute>, oder sie daraus ableiten muss <xref:System.MarshalByRefObject>. Dadurch können Parameterwerte in der Anwendungsdomäne übergeben werden, in dem die Vorlage verarbeitet wird.  
  
 Beispielsweise konnte eine Textvorlage mit folgendem Inhalt geschrieben werden:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Übergeben von Parameterwerten an eine Vorlage  
 Wenn Sie schreiben eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Erweiterungstypen, z. B. einen Menübefehl oder einen Ereignishandler, können Sie eine Vorlage mithilfe des Textvorlagendiensts verarbeiten:  
  
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
  
 Das folgende Beispiel übergibt die Werte mit beiden Methoden:  
  
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
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Übergeben von Werten an einer Textvorlage Run-Time (vorverarbeitete)  
 Es ist nicht in der Regel erforderlich ist, verwendet der `<#@parameter#>` Richtlinie mit einer (vorverarbeiteten) zur Laufzeit-Textvorlagen. Definieren Sie stattdessen einen zusätzlichen Konstruktor oder eine festlegbare Eigenschaft für den generierten Code, über das Sie Parameterwerte übergeben. Weitere Informationen finden Sie unter [Run-Time-Textgenerierung mithilfe von T4-Textvorlagen](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Jedoch, wenn Sie verwenden möchten `<#@parameter>` in einer Laufzeitvorlage können Sie Werte zu übergeben, indem Sie mit dem Wörterbuch der Sitzung. Nehmen Sie beispielsweise an, Sie die Datei erstellt haben, als eine vorverarbeitete Vorlage mit der Bezeichnung `PreTextTemplate1`. Sie können die Vorlage mithilfe des folgenden Codes in Ihrem Programm aufrufen.  
  
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
>  Die `parameter` Richtlinie ist nicht im festgelegten Werte abgerufen werden die `-a` Parameter von der `TextTransform.exe` Hilfsprogramm. Um diese Werte zu erhalten, legen Sie `hostSpecific="true"` in der `template` Richtlinie, und verwenden Sie `this.Host.ResolveParameterValue("","","argName")`.