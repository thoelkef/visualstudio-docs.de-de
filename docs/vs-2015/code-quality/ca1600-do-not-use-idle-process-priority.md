---
title: 'CA1600: Verwenden Sie nicht im Leerlauf Prozesspriorität | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4002e17e3988ca3b449e141394ce762f95ffc78b
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "58956021"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle".
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel sollte unterdrückt werden, nur, wenn im Leerlauf Prozesspriorität erforderlich ist und Mobilität Überlegungen sicher ignoriert werden können.
