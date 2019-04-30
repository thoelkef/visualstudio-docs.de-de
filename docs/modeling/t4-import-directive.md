---
title: T4-Import-Direktive
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49ab8d3462877a28cf40aed519b71615b23f8d4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856350"
---
# <a name="t4-import-directive"></a>T4-Import-Direktive

In den Codeblöcken einer Visual Studio T4-Textvorlage die `import` -Direktive ermöglicht Ihnen, die auf Elemente in einem anderen Namespace zu verweisen, ohne einen vollqualifizierten Namen. Dies entspricht `using` in C# oder `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

- [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)