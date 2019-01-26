---
title: T4-Import-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6b7eed6a8280bda3b53dd43633005ebb45e58514
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945423"
---
# <a name="t4-import-directive"></a>T4-Import-Anweisung

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

  Wenn Sie eine benutzerdefinierte Anweisung verwenden, importiert der Anweisungsprozessor unter Umständen automatisch einige Namespaces.

  Wenn Sie z. B. Vorlagen für eine domänenspezifische Sprache (DSL) schreiben, müssen Sie keine Importanweisungen für die folgenden Namespaces schreiben:

- `Microsoft.VisualStudio.Modeling`

- Der Namespace der DSL

## <a name="see-also"></a>Siehe auch

- [T4-Assemblydirektive](../modeling/t4-assembly-directive.md)