---
title: T4-Import-Direktive | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 05891c415e801a7d08a3b168dec854d8566363d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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