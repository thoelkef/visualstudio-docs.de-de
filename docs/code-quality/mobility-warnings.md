---
title: "Mobilit&#228;tswarnungen | Microsoft Docs"
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
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "Analysen für verwalteten Code (Warnungen), Mobilitätswarnungen"
  - "Mobilitätswarnungen"
  - "Warnungen, Mobilität"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Mobilit&#228;tswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mobilitätswarnungen sorgen für einen effizienten Stromverbrauch.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1600: Verwenden Sie keine Prozesse mit der Priorität "idle"](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Legen Sie für Prozesse nicht die Priorität Idle fest.  Prozesse mit System.Diagnostics.ProcessPriorityClass.Idle beanspruchen die CPU, wenn diese sich eigentlich im Leerlauf befindet, und blockieren daher den Standbymodus.|  
|[CA1601: Verwenden Sie keine Timer, um Änderungen am Betriebszustand zu verhindern](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Regelmäßige Aktivitäten mit einer höheren Frequenz belasten die CPU und beeinflussen energiesparende Leerlaufzeitgeber, mit denen die Anzeige sowie die Festplatten ausgeschaltet werden.|