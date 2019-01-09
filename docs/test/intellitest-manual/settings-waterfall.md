---
title: Einstellungswasserfall | Microsoft IntelliTest-Test-Tool für Entwickler
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c15b440845f918c194bad334e118e25dee676431
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936164"
---
# <a name="settings-waterfall"></a>Einstellungswasserfall

Das Konzept des Einstellungswasserfalls bedeutet, dass die Benutzer auf den Ebenen **Assembly**, **Fixture** und  **Durchsuchen** Einstellungen vornehmen können:

* Assembly: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Installation: [PexClass](attribute-glossary.md#pexclass)
* Durchsuchungsvorgang: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Auf der **Assembly**-Ebene vorgenommene Einstellungen beeinflussen alle Fixtures und Durchsuchungsvorgänge unter dieser Assembly. Auf der **Fixture**-Ebene vorgenommene Einstellungen beeinflussen alle Durchsuchungsvorgänge unter dieser Fixture. Untergeordnete Einstellungen gewinnen&mdash;: Wenn eine Einstellung auf den **Assembly**- und **Fixture**-Ebenen definiert wird, werden die **Fixture**-Einstellungen verwendet.

Beachten Sie, dass einige Einstellungen spezifisch für die **Assembly**-Ebene oder **Installations**-Ebene sind.

**Beispiel**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500 
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Sie möchten Feedback geben?

Posten Sie Ihre Ideen und Featureanfragen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).