---
title: T4-Import-Direktive | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3f59641d733e16730d02868c368d53d6cbee0e74
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="t4-import-directive"></a>T4-Import-Anweisung
In den Codeblöcken einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] T4-Textvorlage ermöglicht die `import`-Direktive das Erstellen von Verweisen auf Elemente in einem anderen Namespace, ohne einen vollqualifizierten Namen anzugeben. Dies entspricht `using` in C# oder `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Eine allgemeine Übersicht über das Verfassen von T4-Textvorlagen, finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Verwenden der Importanweisung  
  
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
  
## <a name="standard-imports"></a>Standardimporte  
 Der folgende Namespace wird automatisch importiert, damit Sie keine eigene Importanweisung schreiben müssen:  
  
-   `System`  
  
 Wenn Sie eine benutzerdefinierte Anweisung verwenden, importiert der Anweisungsprozessor unter Umständen automatisch einige Namespaces.  
  
 Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Importanweisungen für die folgenden Namespaces schreiben:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Der Namespace der DSL  
  
## <a name="see-also"></a>Siehe auch  
 [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)