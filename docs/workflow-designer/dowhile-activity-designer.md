---
title: Workflow-Designer-DoWhile-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85f8d6c442982fff47a679e8fc2ccc04ee515a9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650519"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner

Die <xref:System.Activities.Statements.DoWhile>-Aktivität führt die in der <xref:System.Activities.Statements.DoWhile.Body%2A> enthaltene Aktivität mindestens einmal aus, bis eine angegebene Bedingung als **false**ausgewertet wird. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten <xref:System.Activities.Statements.DoWhile> Aktivitäts Eigenschaften angezeigt, und es wird beschrieben, wie Sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität, die ausgeführt werden soll, während die Bedingung **true**ist. Um die <xref:System.Activities.Statements.DoWhile.Body%2A>-Aktivität hinzuzufügen, legen Sie eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **DoWhile** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Um die <xref:System.Activities.Statements.DoWhile.Condition%2A> festzulegen, geben Sie im Feld **Bedingung** im **DoWhile** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|

## <a name="see-also"></a>Siehe auch

- [While](../workflow-designer/while-activity-designer.md)
- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)