---
title: 'CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle".'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c37affc585653807912d00c1cfe365853fd6260b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921813"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle".

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft.Mobility|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Diese Regel tritt auf, wenn Prozesse auf `ProcessPriorityClass.Idle`festgelegt sind.

## <a name="rule-description"></a>Regelbeschreibung
Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse, die `System.Diagnostics.ProcessPriorityClass.Idle` über das verfügen, belegen die CPU, wenn Sie andernfalls im Leerlauf ist, und blockieren somit den Standbymodus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Legen Sie Prozesse `ProcessPriorityClass.BelowNormal`auf fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Diese Regel sollte nur unterdrückt werden, wenn die Prozesspriorität für den Leerlauf erforderlich ist und Überlegungen zur Mobilität sicher ignoriert werden können.