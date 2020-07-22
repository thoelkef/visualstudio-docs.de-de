---
title: Workflow-Designer-DoWhile-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c56a9ab8b46f8f7ee36875dda507cb9f288136cf
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86875604"
---
# <a name="dowhile-activity-designer"></a>DoWhile-Aktivitätsdesigner

Die- <xref:System.Activities.Statements.DoWhile> Aktivität führt die in der enthaltenen Aktivität mindestens <xref:System.Activities.Statements.DoWhile.Body%2A> einmal aus, bis eine angegebene Bedingung als **false**ausgewertet wird. Wenn die in einem Schleifentext enthaltene Anwendung der 0 (null) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>-Aktivität.

## <a name="dowhile-properties-in-the-workflow-designer"></a>DoWhile- Eigenschaften im Workflow-Designer

In der folgenden Tabelle werden die nützlichsten <xref:System.Activities.Statements.DoWhile> Aktivitäts Eigenschaften angezeigt, und es wird beschrieben, wie Sie im Designer verwendet werden:

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität, die ausgeführt werden soll, während die Bedingung **true**ist. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.DoWhile.Body%2A> eine Aktivität aus der Toolbox in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **DoWhile** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll. Um die festzulegen <xref:System.Activities.Statements.DoWhile.Condition%2A> , geben Sie im Feld **Bedingung** im **DoWhile** -Aktivitäts Designer oder im Eigenschaften Raster einen Visual Basic Ausdruck ein.|

## <a name="see-also"></a>Siehe auch

- [While](../workflow-designer/while-activity-designer.md)
- [Ablauf Steuerung](../workflow-designer/control-flow-activity-designers.md)