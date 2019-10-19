---
title: 'CA1600: keine Leerlauf Prozesspriorität verwenden | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d4260db808d9c50f78388cf6ba976f7ace52e6a3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669294"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft. Mobility|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Diese Regel tritt auf, wenn Prozesse auf `ProcessPriorityClass.Idle` festgelegt werden.

## <a name="rule-description"></a>Regelbeschreibung
 Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse, die über `System.Diagnostics.ProcessPriorityClass.Idle` verfügen, belegen die CPU, wenn Sie andernfalls im Leerlauf ist, und blockieren somit den Standbymodus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Legen Sie Prozesse auf `ProcessPriorityClass.BelowNormal` fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel sollte nur unterdrückt werden, wenn die Prozesspriorität für den Leerlauf erforderlich ist und Überlegungen zur Mobilität sicher ignoriert werden können.
