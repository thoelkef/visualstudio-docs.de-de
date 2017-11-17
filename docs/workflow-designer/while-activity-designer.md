---
title: "While-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: b70e0c66813c474d5711538843da93a669df88d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="while-activity-designer"></a>While-Aktivitätsdesigner
Die <xref:System.Activities.Statements.While> -Aktivität führt die Aktivität enthalten sind, dessen <xref:System.Activities.Statements.While.Body%2A> die angegebene <xref:System.Activities.Statements.While.Condition%2A> ergibt **"true"**. Die enthaltene Aktivität wird möglicherweise nie ausgeführt. Wenn die enthaltene Aktivität wenigstens einmal ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.DoWhile>-Aktivität.  
  
## <a name="while-properties-in-workflow-designer"></a>While-Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.While>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.While>Aktivität im Header an. Der Standardwert lautet While. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header Aktivitätsdesigners.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Enthält die auszuführende Aktivität während der <xref:System.Activities.Statements.While.Condition%2A> ergibt **"true"**.|  
|<xref:System.Activities.Statements.While.Condition%2A>|True|Enthält den [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]-Ausdruck, dessen Auswertung bestimmt, ob die Aktivität im <xref:System.Activities.Statements.While.Body%2A> ausgeführt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)