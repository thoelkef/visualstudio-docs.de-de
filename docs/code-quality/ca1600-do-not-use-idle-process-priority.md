---
title: 'CA1600: Verwenden Sie nicht im Leerlauf Prozesse mit der Priorität'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e606850298841d1d1c77435d83dbbe12c4e55d64
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921042"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie nicht im Leerlauf Prozesse mit der Priorität

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