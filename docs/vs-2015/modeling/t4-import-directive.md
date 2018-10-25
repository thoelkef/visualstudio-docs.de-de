---
title: T4 Import-Anweisung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6fa8f027fbb3418fff47b0459628afb691c8a05a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893675"
---
# <a name="t4-import-directive"></a>T4-Import-Anweisung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In den Codeblöcken einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4-Textvorlage ermöglicht die `import`-Anweisung das Erstellen von Verweisen auf Elemente in einem anderen Namespace, ohne einen vollqualifizierten Namen anzugeben. Dies entspricht `using` in C# oder `imports` in [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
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
  
  Wenn Sie eine benutzerdefinierte Anweisung verwenden, importiert der Anweisungsprozessor unter Umständen automatisch einige Namespaces.  
  
  Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Importanweisungen für die folgenden Namespaces schreiben:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Der Namespace der DSL  
  
## <a name="see-also"></a>Siehe auch  
 [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)



