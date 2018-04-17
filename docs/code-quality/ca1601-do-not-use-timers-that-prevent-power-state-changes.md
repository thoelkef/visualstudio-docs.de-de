---
title: 'CA1601: Verwenden Sie keine Timer, die Änderungen zu verhindern, dass | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: 270c030d4d4b829fb1e7d17308a4ae6f0ad17539
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Kategorie|Microsoft.Mobility|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Timer verfügt über ein Intervall Ausführung von mehr als einmal pro Sekunde festgelegt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Führen Sie Abrufe nicht öfter als einmal pro Sekunde oder auf Zeitgeber, verwenden, die öfter als einmal auftreten pro Sekunde. Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlauftimer, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Legen Sie Zeitgeberintervallen kleiner als ein Mal pro Sekunde auftreten.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Diese Regel sollen nur, wenn den Zeitgeber das Auslösen von mehr als einmal pro Sekunde erforderlich ist und Mobility Überlegungen ohne weiteres ignoriert werden können unterdrückt werden.