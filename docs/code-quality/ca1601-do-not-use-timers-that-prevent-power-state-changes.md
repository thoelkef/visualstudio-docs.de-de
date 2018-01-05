---
title: "CA1601: Verwenden Sie keine Timer, die Änderungen zu verhindern, dass | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4fb8ef82581f60cea3eb121e3d0c68fbffa82d8a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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