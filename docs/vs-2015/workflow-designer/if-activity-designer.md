---
title: Wenn Aktivitäts-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3ab8c9a7f49302b2308f97855c022d8e8d5126e0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956884"
---
# <a name="if-activity-designer"></a>If-Aktivitätsdesigner
Die <xref:System.Activities.Statements.If>-Aktivität wertet eine Bedingung aus und führt eine Aktivität aus, die von den Ergebnissen dieser Auswertung abhängig ist. Bei Verwendung eines Programmierstils nach Art der Verfahrensmodellierung ist diese Aktivität höchst nützlich. Eine <xref:System.Activities.Statements.If>-Aktivität kann in eine <xref:System.Activities.Statements.Sequence>-Aktivität oder beispielsweise eine <xref:System.Activities.Statements.Parallel>-Aktivität geschachtelt werden. Wenn Sie eine <xref:System.Activities.Statements.Flowchart>-Aktivität verwenden, sollten Sie in Erwägung ziehen, stattdessen eine <xref:System.Activities.Statements.FlowDecision>-Aktivität zu verwenden.  
  
## <a name="if-properties-in-the-workflow-designer"></a>If- Eigenschaften im Workflow-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.If>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Die Bedingung, die die auszuführende untergeordnete Aktivität bestimmt. Festlegen der <xref:System.Activities.Statements.If.Condition%2A>, geben Sie einen [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Ausdruck in der **Bedingung** Feld der **Wenn** -Aktivitätsdesigner oder im Eigenschaftenraster.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Die Aktivität ausgeführt wird, wenn die <xref:System.Activities.Statements.If.Condition%2A> ist **"false"**. Hinzufügen eine Aktivität, die ausgeführt wird, indem die <xref:System.Activities.Statements.If.Else%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in die **Else** Feld der **Wenn** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Die Aktivität ausgeführt wird, wenn die <xref:System.Activities.Statements.If.Condition%2A> ist **"true"**. Hinzufügen eine Aktivität, die ausgeführt wird, indem die <xref:System.Activities.Statements.If.Then%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in die **klicken Sie dann** Feld der **Wenn** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|  
  
## <a name="see-also"></a>Siehe auch  
 [Sequenz](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)