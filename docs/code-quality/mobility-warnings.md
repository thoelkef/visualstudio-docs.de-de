---
title: Mobilitätswarnungen
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fecdc2f6e7ab8015bf56f38ee00c9bb43a3b38c
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535750"
---
# <a name="mobility-warnings"></a>Mobilitätswarnungen
Mobilitäts Warnungen unterstützen den effizienten Energieverbrauch.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"](../code-quality/ca1600.md)|Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus.|
|[CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern](../code-quality/ca1601.md)|Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.|
