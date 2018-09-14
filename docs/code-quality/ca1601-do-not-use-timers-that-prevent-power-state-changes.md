---
title: 'CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 033c7a73c404a2bd5146a17a1a7b4f2fa8b9c540
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545712"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern
|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|Kategorie|Microsoft.Mobility|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Einen Zeitgeber wurde ein Intervall festlegen, die mehr als einmal pro Sekunde ausgeführt.

## <a name="rule-description"></a>Regelbeschreibung
 Führen Sie Abrufe nicht öfter als einmal pro Sekunde oder Timer verwenden, die öfter als einmal auftreten pro Sekunde. Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Legen Sie Zeitgeberintervallen kleiner als ein Mal pro Sekunde ausgeführt.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Diese Regel sollte unterdrückt werden, nur, wenn das Auslösen des Timers von mehr als einmal pro Sekunde erforderlich ist und Mobilität Überlegungen ohne weiteres ignoriert werden können.