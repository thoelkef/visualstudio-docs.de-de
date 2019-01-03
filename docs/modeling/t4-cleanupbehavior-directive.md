---
title: T4 CleanUpBehavior-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f99cece37b37cdbf4906e9af3939fe824aec0a93
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912820"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior-Anweisung

Wenn die appDomain nach der Verarbeitung einer Textvorlage gelöscht werden soll, nehmen Sie die folgende Zeile mit auf:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Textvorlagen werden in einer appDomain getrennt vom Hostprozess verarbeitet. In den meisten Fällen wird nach der Verarbeitung einer Textvorlage die jeweilige appDomain erneut verwendet, um die nächste Vorlage zu verarbeiten. Wenn Sie ///CleanupBehavior angeben, wird die appDomain gelöscht und die nächste Vorlage wird in einer neuen appDomain verarbeitet.

Dadurch verlangsamt sich zwar die Textverarbeitung, es wird jedoch sichergestellt, dass Ressourcen verworfen werden.

Diese Direktiven funktionieren nur auf dem Visual Studio-Host.