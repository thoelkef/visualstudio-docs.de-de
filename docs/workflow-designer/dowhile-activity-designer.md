---
title: "DoWhile-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 43a55a8873fa10fb31db89364c50e084cd72fb5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner
Die <xref:System.Activities.Statements.DoWhile> Aktivität ausgeführt wird, die im enthaltene Aktivität seine <xref:System.Activities.Statements.DoWhile.Body%2A> mindestens einmal, bis eine angegebene Bedingung ergibt **"false"**. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.DoWhile>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität ausführen, während die Bedingung **"true"**. Hinzufügen der <xref:System.Activities.Statements.DoWhile.Body%2A> Aktivität, indem Sie eine Aktivität aus der Toolbox in den **Text** Feld der **DoWhile** Aktivitäts-Designer mit dem Hinweistext "Aktivität hier ablegen".|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Festlegen der <xref:System.Activities.Statements.DoWhile.Condition%2A>, geben Sie einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Ausdruck in der **Bedingung** Feld der **DoWhile** -Aktivitätsdesigner oder im Eigenschaftenraster.|  
  
## <a name="see-also"></a>Siehe auch  
 [While](../workflow-designer/while-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)