---
title: Workflow-Designer - Wenn-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 716f2b13758864d5eda449967990f9e5be399a9d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822839"
---
# <a name="if-activity-designer"></a>If-Aktivitätsdesigner

Die <xref:System.Activities.Statements.If>-Aktivität wertet eine Bedingung aus und führt eine Aktivität aus, die von den Ergebnissen dieser Auswertung abhängig ist. Bei Verwendung eines Programmierstils nach Art der Verfahrensmodellierung ist diese Aktivität höchst nützlich. Eine <xref:System.Activities.Statements.If>-Aktivität kann in eine <xref:System.Activities.Statements.Sequence>-Aktivität oder beispielsweise eine <xref:System.Activities.Statements.Parallel>-Aktivität geschachtelt werden. Wenn Sie eine <xref:System.Activities.Statements.Flowchart>-Aktivität verwenden, sollten Sie in Erwägung ziehen, stattdessen eine <xref:System.Activities.Statements.FlowDecision>-Aktivität zu verwenden.

## <a name="if-properties-in-the-workflow-designer"></a>If- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.If>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.If.Condition%2A>|True|Die Bedingung, die die auszuführende untergeordnete Aktivität bestimmt. Festlegen der <xref:System.Activities.Statements.If.Condition%2A>, geben Sie einen Visual Basic-Ausdruck in der **Bedingung** Feld der **Wenn** -Aktivitätsdesigner oder im Eigenschaftenraster.|
|<xref:System.Activities.Statements.If.Else%2A>|False|Die Aktivität ausgeführt wird, wenn die <xref:System.Activities.Statements.If.Condition%2A> ist **"false"**. Hinzufügen eine Aktivität, die ausgeführt wird, indem die <xref:System.Activities.Statements.If.Else%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in die **Else** Feld der **Wenn** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|
|<xref:System.Activities.Statements.If.Then%2A>|False|Die Aktivität ausgeführt wird, wenn die <xref:System.Activities.Statements.If.Condition%2A> ist **"true"**. Hinzufügen eine Aktivität, die ausgeführt wird, indem die <xref:System.Activities.Statements.If.Then%2A> verzweigen, legen Sie eine Aktivität aus der **Toolbox** in die **klicken Sie dann** Feld der **Wenn** Aktivitäts-Designer, mit dem Hinweistext " Aktivität hier ablegen".|

## <a name="see-also"></a>Siehe auch

- [Sequence](../workflow-designer/sequence-activity-designer.md)
- [Parallel](../workflow-designer/parallel-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)