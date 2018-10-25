---
title: 'CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 0c1db098a485002d97aaf986fbac95e35519351b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924677"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"

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