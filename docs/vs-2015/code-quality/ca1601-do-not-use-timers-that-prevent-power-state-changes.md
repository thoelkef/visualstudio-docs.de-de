---
title: 'CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 95f13604908ad45c5f33a011fec886bba90d0bd8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669277"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategorie|Microsoft. Mobility|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Für einen Timer ist ein Intervall festgelegt, das mehr als einmal pro Sekunde auftritt.

## <a name="rule-description"></a>Regelbeschreibung
 Rufen Sie nicht öfter als einmal pro Sekunde ab, oder verwenden Sie Zeitgeber, die häufiger als einmal pro Sekunde auftreten. Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Legen Sie Zeit Geber Intervalle so fest, dass Sie weniger als einmal pro Sekunde auftreten.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Regel sollte nur unterdrückt werden, wenn der Timer mehr als einmal pro Sekunde ausgelöst wird und die Überlegungen zur Mobilität sicher ignoriert werden können.
