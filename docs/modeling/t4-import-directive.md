---
title: T4-Import-Direktive
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a28bedd01e3a4f6a7a87b025ac9a9a6184da9b2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591865"
---
# <a name="t4-import-directive"></a>T4-Import-Direktive

In den Code Blöcken einer Visual Studio T4-Textvorlage können Sie mit der `import`-Direktive auf Elemente in einem anderen Namespace verweisen, ohne einen voll qualifizierten Namen bereitzustellen. Dies entspricht `using` in C# oder `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

- Der Namespace Ihrer DSL

## <a name="see-also"></a>Siehe auch

- [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)
