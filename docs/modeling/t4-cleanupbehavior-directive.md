---
title: T4 CleanUpBehavior-Anweisung
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 27df15c0b935ff4bae497940c095dba1598bc4c1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970568"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior-Anweisung

Wenn die appDomain nach der Verarbeitung einer Textvorlage gelöscht werden soll, nehmen Sie die folgende Zeile mit auf:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Textvorlagen werden in einer appDomain getrennt vom Hostprozess verarbeitet. In den meisten Fällen wird nach der Verarbeitung einer Textvorlage die jeweilige appDomain erneut verwendet, um die nächste Vorlage zu verarbeiten. Wenn Sie ///CleanupBehavior angeben, wird die appDomain gelöscht und die nächste Vorlage wird in einer neuen appDomain verarbeitet.

Dadurch verlangsamt sich zwar die Textverarbeitung, es wird jedoch sichergestellt, dass Ressourcen verworfen werden.

Diese Direktiven funktionieren nur auf dem Visual Studio-Host.