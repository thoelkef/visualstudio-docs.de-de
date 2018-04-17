---
title: Wenn Aktivitäts-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 948359e0c6458fb0ad03d0d032676439d8062ca4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
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

- [Sequenz](../workflow-designer/sequence-activity-designer.md)
- [Parallele](../workflow-designer/parallel-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)