---
title: "T4 Import Directive | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# T4 Import Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In den Codeblöcken einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] T4\-Textvorlage ermöglicht die `import`\-Direktive das Erstellen von Verweisen auf Elemente in einem anderen Namespace, ohne einen vollqualifizierten Namen anzugeben.  Dies entspricht `using` in C\# oder `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Eine allgemeine Übersicht über das Schreiben von T4\-Textvorlagen finden Sie unter [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Verwenden der Importdirektive  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 In diesem Beispiel kann Vorlagencode einen expliziten Namespace für Member von System.IO auslassen:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## Standardimporte  
 Der folgende Namespace wird automatisch importiert, damit Sie keine eigene Importdirektive schreiben müssen:  
  
-   `System`  
  
 Wenn Sie eine benutzerdefinierte Direktive verwenden, importiert der Direktivenprozessor unter Umständen automatisch einige Namespaces.  
  
 Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache \(DSL\) schreiben, müssen Sie keine Importdirektiven für die folgenden Namespaces schreiben:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Der Namespace der DSL  
  
## Siehe auch  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)