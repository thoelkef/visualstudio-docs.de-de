---
title: "CA1600: Verwenden Sie nicht im Leerlauf Prozesspriorität | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|Kategorie|Microsoft.Mobility|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Mit dieser Regel tritt auf, wenn Prozesse, um festgelegt sind `ProcessPriorityClass.Idle`.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Legen Sie für Prozesse nicht die Priorität Idle fest. Prozesse mit `System.Diagnostics.ProcessPriorityClass.Idle` belegen die CPU, wenn diese andernfalls im Leerlauf werden würde, und daher den Standbymodus blockieren.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Legen Sie Prozesse auf `ProcessPriorityClass.BelowNormal`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Mit dieser Regel sollen nur, wenn im Leerlauf Prozesspriorität erforderlich ist und Mobilität Überlegungen gefahrlos ignoriert werden können unterdrückt werden.