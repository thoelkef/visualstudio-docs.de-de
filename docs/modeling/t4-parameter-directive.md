---
title: "T4 Parameter Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d590387-1d9d-40a5-a72c-65fae7a8bdf3
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Parameter Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Textvorlage deklariert die `parameter`\-Direktive Eigenschaften im Vorlagencode, die von Werten initialisiert werden, die vom externen Kontext übergeben werden.  Sie können diese Werte festlegen, wenn Sie Code schreiben, mit dem Texttransformation aufgerufen wird.  
  
## Verwenden der Parameterdirektive  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Mit der `parameter`\-Direktive werden Eigenschaften im Vorlagencode deklariert, die von Werten initialisiert werden, die vom externen Kontext übergeben werden.  Sie können diese Werte festlegen, wenn Sie Code schreiben, mit dem Texttransformation aufgerufen wird.  Die Werte können entweder im `Session`\-Wörterbuch oder in <xref:System.Runtime.Remoting.Messaging.CallContext> übergeben werden.  
  
 Sie können Parameter eines beliebigen remotefähigen Typs deklarieren.  Das heißt, der Typ muss mit <xref:System.SerializableAttribute> deklariert werden, oder er muss sich von <xref:System.MarshalByRefObject> ableiten.  Somit können Parameterwerte an die AppDomain übergeben werden, in der die Vorlage verarbeitet wird.  
  
 Sie können z. B. eine Textvorlage mit dem folgenden Inhalt schreiben:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## Übergeben von Parameterwerten an eine Vorlage  
 Wenn Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Erweiterung, z. B. einen Menübefehl oder einen Ereignishandler schreiben, können Sie mit dem Textvorlagendienst eine Vorlage verarbeiten:  
  
```c#  
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
  
## Übergeben von Werten im Aufrufkontext  
 Sie können Werte auch als logische Daten in <xref:System.Runtime.Remoting.Messaging.CallContext> übergeben.  
  
 Im folgenden Beispiel werden Werte mit beiden Methoden übergeben:  
  
```c#  
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
  
## Übergeben von Werten an eine Laufzeittextvorlage \(vorverarbeitete Textvorlage\)  
 Es ist normalerweise nicht notwendig, die `<#@parameter#>`\-Direktive mit Laufzeittextvorlagen \(vorverarbeiteten Textvorlagen\) zu verwenden.  Stattdessen können Sie einen zusätzlichen Konstruktor oder eine festlegbare Eigenschaft für den generierten Code definieren, mit dem Sie Parameterwerte übergeben.  Weitere Informationen finden Sie unter [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Wenn Sie jedoch `<#@parameter>` in einer Laufzeitvorlage verwenden möchten, können Sie Werte mit dem Sitzungswörterbuch daran übergeben.  Beispiel: Sie haben die Datei als vorverarbeitete Vorlage mit dem Namen `PreTextTemplate1` erstellt.  Sie können die Vorlage im Programm mit dem folgenden Code aufrufen.  
  
```c#  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## Abrufen von Argumenten von "TextTemplate.exe"  
  
> [!IMPORTANT]
>  Die `parameter`\-Direktive ruft keine Werte ab, die im `–a`\-Parameter des Hilfsprogramms `TextTransform.exe` festgelegt wurden.  Um diese Werte abzurufen, legen Sie `hostSpecific="true"` in der `template`\-Direktive fest, und verwenden Sie `this.Host.ResolveParameterValue("","","argName")`.