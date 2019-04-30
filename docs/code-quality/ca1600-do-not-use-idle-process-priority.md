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
ms.openlocfilehash: a1774b3feb2da4939420bf75506892aac6dedd72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797526"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle".

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft.Mobility|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Mit dieser Regel tritt auf, wenn Prozesse, um festgelegt werden `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Regelbeschreibung
 Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit `System.Diagnostics.ProcessPriorityClass.Idle` belegen die CPU, wenn sie andernfalls im Leerlauf sein würde, und daher den Standbymodus blockieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Legen Sie Prozesse auf `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Diese Regel sollte unterdrückt werden, nur, wenn im Leerlauf Prozesspriorität erforderlich ist und Mobilität Überlegungen sicher ignoriert werden können.