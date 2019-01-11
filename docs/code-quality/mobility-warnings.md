---
title: Mobilitätswarnungen
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2125f8fc674c91d5bbb301c13a3a898b79e174a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889953"
---
# <a name="mobility-warnings"></a>Mobilitätswarnungen
Mobilitätswarnungen zu effizienten Stromverbrauch unterstützen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1600: Verwenden Sie nicht im Leerlauf Prozesse mit der Priorität](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus.|
|[CA1601: Verwenden Sie keine Timer, die Änderungen am Betriebszustand zu verhindern.](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.|