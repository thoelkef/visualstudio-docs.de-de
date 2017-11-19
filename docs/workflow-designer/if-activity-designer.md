---
title: "Wenn Aktivitäts-Designer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3d3928330558c3d611decd2a87498d33fd6482ce
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="if-activity-designer"></a>If-Aktivitätsdesigner
Die <xref:System.Activities.Statements.If>-Aktivität wertet eine Bedingung aus und führt eine Aktivität aus, die von den Ergebnissen dieser Auswertung abhängig ist. Bei Verwendung eines Programmierstils nach Art der Verfahrensmodellierung ist diese Aktivität höchst nützlich. Eine <xref:System.Activities.Statements.If>-Aktivität kann in eine <xref:System.Activities.Statements.Sequence>-Aktivität oder beispielsweise eine <xref:System.Activities.Statements.Parallel>-Aktivität geschachtelt werden. Wenn Sie eine <xref:System.Activities.Statements.Flowchart>-Aktivität verwenden, sollten Sie in Erwägung ziehen, stattdessen eine <xref:System.Activities.Statements.FlowDecision>-Aktivität zu verwenden.  
  
## <a name="if-properties-in-the-workflow-designer"></a>If- Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.If>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Die Bedingung, die die auszuführende untergeordnete Aktivität bestimmt. Festlegen der <xref:System.Activities.Statements.If.Condition%2A>, geben Sie einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Ausdruck in der **Bedingung** Feld der **Wenn** -Aktivitätsdesigner oder im Eigenschaftenraster.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Die Aktivität aus, wenn führen Sie die <xref:System.Activities.Statements.If.Condition%2A> ist **"false"**. Um eine Aktivität hinzuzufügen, die ausgeführt wird, indem Sie die <xref:System.Activities.Statements.If.Else%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in der **Else** Feld der **Wenn** Aktivitäts-Designer mit dem Hinweistext " Aktivität hier ablegen".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Die Aktivität aus, wenn führen Sie die <xref:System.Activities.Statements.If.Condition%2A> ist **"true"**. Um eine Aktivität hinzuzufügen, die ausgeführt wird, indem Sie die <xref:System.Activities.Statements.If.Then%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in der **klicken Sie dann** Feld der **Wenn** Aktivitäts-Designer mit dem Hinweistext " Aktivität hier ablegen".|  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenz](../workflow-designer/sequence-activity-designer.md)   
 [Parallele](../workflow-designer/parallel-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)