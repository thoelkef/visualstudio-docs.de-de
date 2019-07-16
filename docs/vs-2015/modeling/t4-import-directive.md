---
title: T4 Import-Anweisung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 00033640ec7810f97785b38437795906500a7866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163672"
---
# <a name="t4-import-directive"></a>T4-Import-Direktive
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den Codeblöcken einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4-Textvorlage ermöglicht die `import`-Direktive das Erstellen von Verweisen auf Elemente in einem anderen Namespace, ohne einen vollqualifizierten Namen anzugeben. Dies entspricht `using` in C# oder `imports` in [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 Eine allgemeine Übersicht über das Schreiben von T4-Textvorlagen finden Sie unter [Schreiben einer T4-Textvorlage](../modeling/writing-a-t4-text-template.md).  
  
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
  
- `System`  
  
  Wenn Sie eine benutzerdefinierte Direktive verwenden, importiert der Direktivenprozessor unter Umständen automatisch einige Namespaces.  
  
  Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Importanweisungen für die folgenden Namespaces schreiben:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Der Namespace der DSL  
  
## <a name="see-also"></a>Siehe auch  
 [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)
