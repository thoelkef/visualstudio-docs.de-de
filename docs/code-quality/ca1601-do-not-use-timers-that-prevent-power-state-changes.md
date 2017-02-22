---
title: "CA1601: Verwenden Sie keine Timer, um &#196;nderungen am Betriebszustand zu verhindern | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: Verwenden Sie keine Timer, um &#196;nderungen am Betriebszustand zu verhindern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|Kategorie \(Category\)|Microsoft.Mobility|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Für einen Zeitgeber wurde das Intervall so eingestellt, dass mehr als einmal pro Sekunde ein Ereignis ausgelöst wird.  
  
## Regelbeschreibung  
 Führen Sie Abrufe nicht öfter als einmal pro Sekunde durch, und verwenden Sie keine Zeitgeber, die öfter als einmal pro Sekunde ein Ereignis auslösen.  Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlaufzeitgeber, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.  
  
## Behandeln von Verstößen  
 Stellen Sie die Zeitgeberintervalle so ein, dass weniger als einmal pro Sekunde ein Ereignis ausgelöst wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Regel sollte nur unterdrückt werden, wenn der Zeitgeber mehr als einmal pro Sekunde ausgelöst werden muss und Mobilitätsüberlegungen ohne Bedenken ignoriert werden können.