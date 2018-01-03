---
title: "Einstellungswasserfall | Microsoft IntelliTest Test-Tool für Entwickler | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Settings waterfall
ms.assetid: 45777037-9E16-4ABF-BD26-5AF4E740D4E6
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: a56062f68fb0952d2b18726e1edecc26432e3fc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="settings-waterfall"></a>Einstellungswasserfall

Das Konzept des Einstellungswasserfalls bedeutet, dass die Benutzer auf den Ebenen **Assembly**, **Installation** und  **Durchsuchungsvorgang** Einstellungen vornehmen können: 

* Assembly: [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Installation: [PexClass](attribute-glossary.md#pexclass)
* Durchsuchungsvorgang: [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Auf der **Assembly**-Ebene vorgenommene Einstellungen beeinflussen alle Installationen und Durchsuchungsvorgänge unter dieser Assembly. Auf der **Installations**-Ebene vorgenommene Einstellungen beeinflussen alle Durchsuchungsvorgänge unter dieser Installation. Untergeordnete Einstellungen gewinnen: Wenn eine Einstellung in den **Assembly**- und **Installations**-Ebenen definiert wird, werden die **Installations**-Einstellungen verwendet.

Beachten Sie, dass einige Einstellungen spezifisch für die **Assembly**-Ebene oder **Installations**-Ebene sind. 

**Beispiel**

```
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

Posten Sie Ihre Ideen und Clusterfunktion Anforderungen auf **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.
