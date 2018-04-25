---
title: Mobilitätswarnungen
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1c7c095c6e8c1fe9b1d6d32a997af74450eb09d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="mobility-warnings"></a>Mobilitätswarnungen
Mobilitätswarnungen zu effizienten Stromverbrauch unterstützen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus.|
|[CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlaufzeitgeber, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.|