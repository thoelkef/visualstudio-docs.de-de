---
title: "T4 Text Template Directives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, import directive"
  - "text templates, include directive"
  - "text templates, assembly directive"
  - "text templates, output directive"
  - "text templates, directives"
  - "text templates, template directive"
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 81
---
# T4 Text Template Directives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Direktiven werden Anweisungen für das Textvorlagen\-Transformationsmodul bereitgestellt.  
  
 Die Syntax von Direktiven lautet wie folgt:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Alle Attributwerte müssen in doppelte Anführungszeichen eingeschlossen werden.  Wenn der Wert selbst Anführungszeichen enthält, müssen diese mit dem Escapezeichen "\\" versehen werden.  
  
 Direktiven sind in der Regel die ersten Elemente in einer Vorlagendatei oder einer eingeschlossenen Datei.  Platzieren Sie sie nicht in einem Codeblock `<#...#>` und nicht nach einem Klassenfunktionsblock `<#+...#>`.  
  
 [T4 Template Directive](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 Parameter Directive](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 Output Directive](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 Import Directive](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 Include Directive](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [T4 CleanUpBehavior\-Direktive](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 Darüber hinaus können Sie eigene Direktiven erstellen.  Weitere Informationen finden Sie unter [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).  Wenn Sie mithilfe des Visualisierungs\- und Modellierungs\-SDKs eine domänenspezifische Sprache \(DSL\) erstellen, wird ein Direktivenprozessor als Teil der DSL generiert.